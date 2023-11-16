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
			currentInput = '';
			operator = '';
			result = 0;
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
	<div class="calculator card">
		<div class="display">{currentInput || result}</div>
		<div class="buttons">
			<button on:click={() => handleButtonClick('7')}>7</button>
			<button on:click={() => handleButtonClick('8')}>8</button>
			<button on:click={() => handleButtonClick('9')}>9</button>
			<button on:click={() => setOperator('/')}>/</button>

			<button on:click={() => handleButtonClick('4')}>4</button>
			<button on:click={() => handleButtonClick('5')}>5</button>
			<button on:click={() => handleButtonClick('6')}>6</button>
			<button on:click={() => setOperator('*')}>*</button>

			<button on:click={() => handleButtonClick('1')}>1</button>
			<button on:click={() => handleButtonClick('2')}>2</button>
			<button on:click={() => handleButtonClick('3')}>3</button>
			<button on:click={() => setOperator('-')}>-</button>

			<button on:click={() => handleButtonClick('0')}>0</button>
			<button on:click={handleDecimal}>.</button>
			<button on:click={handlePercentage}>%</button>
			<button on:click={() => setOperator('+')}>+</button>

			<button on:click={handleButtonClick}>C</button>
			<button on:click={() => handleButtonClick('=')}>=</button>
		</div>
	</div>
</main>

<!-- Include Bootstrap's JavaScript -->

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
		text-align: right;
		margin-bottom: 10px;
		padding: 10px;
		background-color: #f8f9fa;
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
