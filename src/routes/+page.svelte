<script>
	let result = 0;
	let currentInput = '';
	let operator = '';

	function handleButtonClick(value) {
		if (value === '=') {
			result = calculateResult();
			currentInput = '';
			operator = '';
		} else if (value === 'C') {
			currentInput = ''; // Only clear the current input, not the result and operator
		} else {
			currentInput += value;
		}
	}

	function calculateResult() {
		const num1 = parseFloat(result);
		const num2 = parseFloat(currentInput);

		switch (operator) {
			case '+':
				return num1 + num2;
			case '-':
				return num1 - num2;
			case '*':
				return num1 * num2;
			case '/':
				return num1 / num2;
			default:
				return num2;
		}
	}

	function setOperator(value) {
		if (currentInput !== '') {
			operator = value;
			result = currentInput;
			currentInput = '';
		}
	}

	function handleDecimal() {
		if (!currentInput.includes('.')) {
			currentInput += '.';
		}
	}

	function handlePercentage() {
		currentInput = (parseFloat(currentInput) / 100).toString();
	}
</script>

<main>
	<div class="calculator card p-3">
		<div class="display bg-light text-end">{currentInput || result}</div>
		<div class="buttons">
			<button on:click={() => handleButtonClick('7')} class="btn btn-primary">7</button>
			<button on:click={() => handleButtonClick('8')} class="btn btn-primary">8</button>
			<button on:click={() => handleButtonClick('9')} class="btn btn-primary">9</button>
			<button on:click={() => setOperator('/')} class="btn btn-warning">/</button>

			<button on:click={() => handleButtonClick('4')} class="btn btn-primary">4</button>
			<button on:click={() => handleButtonClick('5')} class="btn btn-primary">5</button>
			<button on:click={() => handleButtonClick('6')} class="btn btn-primary">6</button>
			<button on:click={() => setOperator('*')} class="btn btn-warning">*</button>

			<button on:click={() => handleButtonClick('1')} class="btn btn-primary">1</button>
			<button on:click={() => handleButtonClick('2')} class="btn btn-primary">2</button>
			<button on:click={() => handleButtonClick('3')} class="btn btn-primary">3</button>
			<button on:click={() => setOperator('-')} class="btn btn-warning">-</button>

			<button on:click={() => handleButtonClick('0')} class="btn btn-primary">0</button>
			<button on:click={handleDecimal} class="btn btn-primary">.</button>
			<button on:click={handlePercentage} class="btn btn-primary">%</button>
			<button on:click={() => setOperator('+')} class="btn btn-warning">+</button>

			<button on:click={() => handleButtonClick('C')} class="btn btn-danger">C</button>
			<button on:click={() => handleButtonClick('=')} class="btn btn-success">=</button>
		</div>
	</div>
</main>

<style>
	@import url('https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css');

	main {
		display: flex;
		justify-content: center;
		align-items: center;
		height: 100vh;
	}

	.calculator {
		width: 300px;
	}

	.display {
		font-size: 1.5em;
		padding: 10px;
	}

	.buttons {
		display: grid;
		grid-template-columns: repeat(4, 1fr);
		gap: 10px;
	}

	button {
		font-size: 1.2em;
	}
</style>
