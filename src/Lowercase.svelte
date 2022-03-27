<svelte:options tag='lower-case'/> 

<script>
	export let variablename = "Lowercase.svelte";

	let value = "lower test"
	let text = ""

	function changeVariableName() {
		text += `Expected: document.getElementById("lower-case").variablename = index.html\n`;
		let test1 = (document.getElementById("lower-case").variablename === 'index.html')?("OK"):("FAIL")
		text += `[${test1}] Actual: document.getElementById("lower-case").variablename = ${document.getElementById("lower-case").variablename}\n\n`;
		text += `Expected: document.getElementById("lower-case").getAttribute("variablename") = index.html\n`;
		let test2 = (document.getElementById("lower-case").getAttribute("variablename") === 'index.html')?("OK"):("FAIL")
		text += `[${test2}] Actual: document.getElementById("lower-case").getAttribute("variablename") = ${document.getElementById("lower-case").getAttribute("variablename")}\n\n`

		text += `Changing the PROPERTY by executing document.getElementById("lower-case").variablename = P_${value}\n\n`;
		document.getElementById("lower-case").variablename = `P_${value}`;
		
		text += `Expected: document.getElementById("lower-case").variablename = P_${value}\n`;
		let test3 = (document.getElementById("lower-case").variablename === `P_${value}`)?("OK"):("FAIL")
		text += `[${test3}] Actual: document.getElementById("lower-case").variablename = ${document.getElementById("lower-case").variablename}\n\n`;
		
		text += `Expected: document.getElementById("lower-case").getAttribute("variablename") = P_${value}\n`;
		let test4 = (document.getElementById("lower-case").getAttribute("variablename") === `P_${value}`)?("OK"):("FAIL")
		text += `[${test4}] Actual: document.getElementById("lower-case").getAttribute("variablename") = ${document.getElementById("lower-case").getAttribute("variablename")}\n\n`
		
		text += `Changing the ATTRIBUTE by executing document.getElementById("lower-case").setAttribute("variablename", A_${value})\n\n`;
		document.getElementById("lower-case").setAttribute("variablename", `A_${value}`);
		
		text += `Expected: document.getElementById("lower-case").variablename = A_${value}\n`;
		let test5 = (document.getElementById("lower-case").variablename === `A_${value}`)?("OK"):("FAIL")
		text += `[${test5}] Actual: document.getElementById("lower-case").variablename = ${document.getElementById("lower-case").variablename}\n\n`;
		
		text += `Expected: document.getElementById("lower-case").getAttribute("variablename") = A_${value}\n`;
		let test6 = (document.getElementById("lower-case").getAttribute("variablename") === `A_${value}`)?("OK"):("FAIL")
		text += `[${test6}] Actual: document.getElementById("lower-case").getAttribute("variablename") = ${document.getElementById("lower-case").getAttribute("variablename")}\n`
	}
</script>

<main>
	<h1>Lower cased variable test</h1>
	<button on:click|once={changeVariableName}>Change to:</button> <input bind:value={value} />
	<h3>"variablename" used here is [{variablename}]. Initially should have been [index.html] and after clicking should become [A_{value}]</h3>
	<textarea value={text}></textarea>
</main>

<style>
	main {
    position:relative; width:100%; height:100%;
    margin:0 auto
}
	textarea
{
    width:90%;
  height:60%;
}
</style>