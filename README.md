# Getting Started with Claude Opus 5.5 Distillation on the CC Channel via Vitas AI (www.aiwts.com)

Distillation needs a teacher you can actually call at scale. Claude Opus 5.5 is Anthropic's flagship teacher model, and Vitas AI (www.aiwts.com) lets you reach it through the Claude Code (CC) compatible channel with full distillation support â no content filtering of teacher outputs, no throttling of training batches, no separate approval to request.

## 1. Get your key and base URL

1. Register or log in at https://www.aiwts.com
2. Create an API key from the dashboard.
3. Use the base URL `https://www.aiwts.com/v1` (OpenAI-compatible) or the native Anthropic-compatible endpoint for Claude models.
4. In your Claude Code / CC channel configuration, point `ANTHROPIC_BASE_URL` (or the equivalent setting in your client) at Vitas AI and set the model to `claude-opus-5-5`.

## 2. Pull teacher outputs for distillation

The CC channel returns normal, official-grade responses you can feed into your fine-tuning stack. A minimal request looks like:

```bash
curl https://www.aiwts.com/v1/messages \
  -H "x-api-key: YOUR_KEY" \
  -H "anthropic-version: 2023-06-01" \
  -H "content-type: application/json" \
  -d '{
    "model": "claude-opus-5-5",
    "max_tokens": 4096,
    "messages": [{"role": "user", "content": "Explain this codebase and propose a refactor plan."}]
  }'
```

Collect the outputs, clean them, and use them to train your student model with your preferred distillation framework (e.g., fine-tuning on teacher completions).

## 3. Scale without hitting API walls

- **No synthetic blocking** of legitimate distillation traffic on the CC channel.
- **Production relay** keeps long training batches stable, with low latency and no 5xx bursts.
- **Usage dashboard** shows exactly how many tokens you pulled and what they cost.

## Reference: Claude Opus 5.5 official pricing

| Item | Official price (per 1M tokens) |
|---|---|
| Input | $4 |
| Output | $20 |
| Cache read | $0.2 |

On Vitas AI, billing is RMB-denominated with no surprise currency conversion â check live rates at https://www.aiwts.com/pricing.

## Start now

Point your client at https://www.aiwts.com, choose the CC channel, pick `claude-opus-5-5`, and send a test request. Documentation: https://docs.aiwts.com/
