# SCOPE Prompt

[`prompt.txt`](prompt.txt) provides the probe generation prompt used in SCOPE.

## Usage

Use the contents of the `SYSTEM_PROMPT` string as the system message. Send one request per target utterance, with the following user message:

```text
Context:
<speaker>: <utterance text>
<speaker>: <utterance text>
...

Target Utterance:
{"utt_id": "<original ID>", "speaker": "<speaker>", "text": "<original text>"}
```

`Context` contains the entire dialogue in its original order, including utterances before and after the target. The target JSON contains only `utt_id`, `speaker`, and `text`, without emotion labels or cause annotations. Preserve the original IDs and text.

The response follows the JSON schema in `prompt.txt`. The two descriptions under `probes`—`emo_sociocognitive_context` and `cau_relational_claim_context`—are used as auxiliary input for the downstream model. The `thought_process` field is excluded from that input.
