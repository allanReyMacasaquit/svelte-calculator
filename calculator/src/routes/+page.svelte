<script>
  let firstNumber = '';
  let secondNumber = '';
  let result = 0;

  function isInvalidInput(value) {
    return isNaN(value) || value.trim() === '' || parseFloat(value) === -1;
  }

  function calculate(operation) {
    // Validate that the input is not -1
    if (isInvalidInput(firstNumber) || isInvalidInput(secondNumber)) {
      result = 'Invalid input';
      return;
    }

    // Convert input values to numbers for calculations
    const num1 = parseFloat(firstNumber);
    const num2 = parseFloat(secondNumber);

    switch (operation) {
      case 'add':
        result = num1 + num2;
        break;
      case 'subtract':
        result = num1 - num2;
        break;
      case 'multiply':
        result = num1 * num2;
        break;
      case 'divide':
        result = num2 !== 0 ? num1 / num2 : 'Error';
        break;
      default:
        result = 0;
    }

    // Clear input fields after calculation
    firstNumber = '';
    secondNumber = '';
  }
</script>

<main class="text-center p-4 h-screen flex flex-col justify-center items-center max-w-md mx-auto">
  <section class="h-[400px] w-[600px]  rounded-lg bg-slate-100 p-6">
    <h1 class="text-3xl font-bold mb-4">Calculator</h1>

    <div class="mb-4">
      <label for="firstNumber" class="block mb-2">First Number:</label>
      <input type="text" bind:value={firstNumber} id="firstNumber" class=" border border-gray-300 px-3 py-2 rounded" />
    </div>

    <div class="mb-4">
      <label for="secondNumber" class="block mb-2">Second Number:</label>
      <input type="text" bind:value={secondNumber} id="secondNumber" class=" border border-gray-300 px-3 py-2 rounded" />
    </div>

    <div class="mb-4">
      <button on:click={() => calculate('add')} class="mr-2 bg-blue-500 text-white px-4 py-2 rounded">
        <i class="fas fa-plus"></i> Add
      </button>
      <button on:click={() => calculate('subtract')} class="mr-2 bg-red-500 text-white px-4 py-2 rounded">
        <i class="fas fa-minus"></i> Subtract
      </button>
      <button on:click={() => calculate('multiply')} class="mr-2 bg-green-500 text-white px-4 py-2 rounded">
        <i class="fas fa-times"></i> Multiply
      </button>
      <button on:click={() => calculate('divide')} class="bg-yellow-500 text-white px-4 py-2 rounded">
        <i class="fas fa-divide"></i> Divide
      </button>
    </div>

    <p class="text-xl font-semibold border rounded-lg p-4 bg-slate-200">Result: {result}</p>
  </section>
</main>
