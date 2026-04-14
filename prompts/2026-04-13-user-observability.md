# Prompts

<!--

cd ~/code/aipipe/
dev.sh
codex --yolo --model gpt-5.4 --config model_reasoning_effort=xhigh

-->

Add user observability, i.e. include the email address of the user in the requests to the providers in providers.js.

For example,

- [OpenRouter accepts a `"user"` key](https://openrouter.ai/docs/guides/administration/user-tracking) in the request body.
- [OpenAI chat completions API](https://developers.openai.com/api/reference/resources/chat/subresources/completions/methods/create#(resource)%20chat.completions%20%3E%20(method)%20create%20%3E%20(params)%200.non_streaming%20%3E%20(param)%20metadata%20%3E%20(schema)) accepts a `metadata` key in the request body.
- [OpenAI responses API](https://developers.openai.com/api/reference/resources/responses/methods/create#(resource)%20responses%20%3E%20(method)%20create%20%3E%20(params)%200.non_streaming%20%3E%20(param)%20metadata%20%3E%20(schema)) also accepts a `metadata` key in the request body.

I'm not sure if Gemini has something similar, but explore this.

For each provider, add the email address of the user making the request in the appropriate field. This will allow us to have better observability into which users are making requests to which providers, and how much they are using, in the server logs of the providers.

Add tests to see if this is sent correctly using mocking - not actual requests. Run and test.

Make minimal code changes.

In README.md, document the URL at which we can check this in the server logs of the providers.

---

For OpenAI make sure to add `store: true` along with the metadata.

Find any other opportunities to simplify this code so that the diffs are minimal - while ensuring that the code is highly readable and maintainable.

<!-- codex resume 019d86b5-271f-7d20-b604-4d47cd0e2650 -->
