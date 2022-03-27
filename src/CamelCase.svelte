<svelte:options tag='camel-case'/> 

<script>
	export let variableName = "CamelCase.svelte";

	let value = "camel test"
	let text = ""

	function changeVariableName() {
		text += `Expected: document.getElementById("camel-case").variableName = index.html\n`;
		let test1 = (document.getElementById("camel-case").variableName === 'index.html')?("OK"):("FAIL")
		text += `[${test1}] Actual: document.getElementById("camel-case").variableName = ${document.getElementById("camel-case").variableName}\n\n`;
		text += `Expected: document.getElementById("camel-case").getAttribute("variableName") = index.html\n`;
		let test2 = (document.getElementById("camel-case").getAttribute("variableName") === 'index.html')?("OK"):("FAIL")
		text += `[${test2}] Actual: document.getElementById("camel-case").getAttribute("variableName") = ${document.getElementById("camel-case").getAttribute("variableName")}\n\n`

		text += `Changing the PROPERTY by executing document.getElementById("camel-case").variableName = P_${value}\n`;
		document.getElementById("camel-case").variableName = `P_${value}`;
		
		text += `Expected: document.getElementById("camel-case").variableName = P_${value}\n`;
		let test3 = (document.getElementById("camel-case").variableName === `P_${value}`)?("OK"):("FAIL")
		text += `[${test3}] Actual: document.getElementById("camel-case").variableName = ${document.getElementById("camel-case").variableName}\n\n`;
		
		text += `Expected: document.getElementById("camel-case").getAttribute("variableName") = P_${value}\n`;
		let test4 = (document.getElementById("camel-case").getAttribute("variableName") === `P_${value}`)?("OK"):("FAIL")
		text += `[${test4}] Actual: document.getElementById("camel-case").getAttribute("variableName") = ${document.getElementById("camel-case").getAttribute("variableName")}\n\n`
		
		text += `Changing the ATTRIBUTE by executing document.getElementById("camel-case").setAttribute("variableName", A_${value})\n\n`;
		document.getElementById("camel-case").setAttribute("variableName", `A_${value}`);
		
		text += `Expected: document.getElementById("camel-case").variableName = A_${value}\n`;
		let test5 = (document.getElementById("camel-case").variableName === `A_${value}`)?("OK"):("FAIL")
		text += `[${test5}] Actual: document.getElementById("camel-case").variableName = ${document.getElementById("camel-case").variableName}\n\n`;
		
		text += `Expected: document.getElementById("camel-case").getAttribute("variableName") = A_${value}\n`;
		let test6 = (document.getElementById("camel-case").getAttribute("variableName") === `A_${value}`)?("OK"):("FAIL")
		text += `[${test6}] Actual: document.getElementById("camel-case").getAttribute("variableName") = ${document.getElementById("camel-case").getAttribute("variableName")}\n`
	}
</script>

<main>
	<h1>Camel cased variable test</h1>
	<button on:click|once={changeVariableName}>Change to:</button> <input bind:value={value} />
	<h3>"variableName" used here is [{variableName}]. Initially should have been [index.html] and
		after clicking should become [A_{value}]</h3>
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