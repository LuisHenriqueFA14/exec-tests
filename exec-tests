#!/usr/bin/env zx

$.verbose = false;

const continueInError = argv.continueInError;

async function checkRun(index) {
	console.log(chalk.gray(`Running test ${index+1}...`));

	const testOut = await Promise.resolve($`./${argv.exe} < __tests__/in${index+1}`);
	const fileOut = fs.readFileSync(`__tests__/out${index+1}`);
	
	if(String(testOut).trim() == String(fileOut).trim()) {
		console.log(chalk.green(`✓ Test ${index+1} ran successfully!`));
	} else {
		console.log(chalk.red(`✕ Test ${index+1} failed to run!`));
		console.log(`\n  Expected: \n${fileOut}`);
		console.log(`  Result: \n${testOut}`);

		if(!continueInError) {
			process.exit(0);
		}
	}
}

// Check "__tests__" folder
if(!fs.readdirSync("./").includes("__tests__")) {
	console.log(chalk.red(`[ERROR] Directory "__tests__" is missing!`));
	process.exit(0);
}

// Check executable file set
if(!argv.exe || argv.exe == true) {
	console.log(chalk.red(`[ERROR] Use the flag "--exe [EXECUTABLE]" to set the executable.`));
	process.exit(0);
}

// Check if executable exists
if(!fs.existsSync(`${argv.exe}`)) {
	console.log(chalk.red(`[ERROR] Executable file not found.`));
	process.exit(0);
}

const list = fs.readdirSync("./__tests__");

for(let j = 0; j < list.length/2; j += 1) {
	console.log();
	await checkRun(j);
}

console.log(chalk.white("All tests have been run!"));
