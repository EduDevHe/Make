<script lang="ts">
  let text = '';
  let selectionStart: number = 0;
  let selectionEnd: number = 0;

  function handleTab(event: KeyboardEvent<HTMLTextAreaElement>) {

    if(event.key === "Tab"){
      event.preventDefault();
    const textarea = event.target as HTMLTextAreaElement;
    const start = textarea.selectionStart;
    const end = textarea.selectionEnd;
    text = text.substring(0, start) + '\t' + text.substring(end);
    textarea.selectionStart = textarea.selectionEnd = start + 1;
    }
   
  }
</script>

<textarea
  bind:value={text}
  on:keydown={handleTab}

/>

<p>Selection start: {selectionStart}</p>
<p>Selection end: {selectionEnd}</p>
