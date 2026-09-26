# How I used AI

**Tool:** Claude Code (Anthropic), an AI assistant in the terminal on my laptop.

## What AI did
- **Running** – set up the environment and ran the notebook locally instead of Colab, so all outputs are saved in the file.
- **Formatting** – formatted my answers in the ✏️ cells and made `output.md` (terminal output of all cells).
- **Writing texts** – helped turn my answers into clear English: predictions, temperature / top-p sentences, attention heads, Part 3.

## What I did
- Directed the whole process: what to run, what to change (my own `MY_PROMPTS`, `LAYER, HEAD = 4, 11`) and how the answers should sound.
- Made the rough estimates behind the predictions myself, e.g. a smaller tokenizer table → more tokens for Kazakh than o200k; dividing all logits by the same T keeps their order.
- Checked the answers against the real outputs:
  - `бөлімшеңізде` = 19 tokens
  - ` Ast` 22.87% vs ` Paris` 22.08%, top-10 hold 64%
  - #1 token never changes with temperature
  - previous-token head (4, 11), most extreme token-0 head (7, 10)
  - Kazakh 1.10 vs Russian 1.11 tokens per character

## Note
The predictions were not written strictly before running each cell. Where a prediction was wrong, the notebook says so next to the measured value.
