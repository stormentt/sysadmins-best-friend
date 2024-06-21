<svelte:head>
  <link rel="stylesheet" href="./node_modules/@xterm/xterm/css/xterm.css" />
</svelte:head>
<script>
 import { onMount } from 'svelte'; //imports the needed onMount handler
 let terminal;                     //creates a var to bind the dom element

 onMount(async () => {
   let xterm = await import("@xterm/xterm")
   let term = new xterm.Terminal({ fontFamily: "Roboto Mono", fontSize: 16})
   term.open(terminal)                // open the element bound to the var
   term.write('Hello from \x1B[1;3;31mxterm.js\x1B[0m $ ')
 });
</script>

<div id="terminal" bind:this={terminal}/> <!-- bind the element to the 'terminal' var -->

