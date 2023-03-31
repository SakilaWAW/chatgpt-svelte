<script>
  import { Configuration, OpenAIApi } from 'openai';

  let input, apiKey;

  async function send() {
    const configuration = new Configuration({apiKey});
    const openai = new OpenAIApi(configuration);
    const response = await openai.createCompletion({
      model: "text-davinci-003",
      prompt: input,
      temperature: 0,
      max_tokens: 100,
      top_p: 1,
      frequency_penalty: 0.0,
      presence_penalty: 0.0,
    });
    input = input + response.data.choices[0].text;
  }
</script>

<style>
  textarea {
    padding: 0.5em;
  }
  button {
    padding: 0.5em;
  }
</style>

<textarea type="text" bind:value={input} />
<button on:click={send}>Send</button>
<input type="text" bind:value={apiKey} placeholder="apiKey"/>