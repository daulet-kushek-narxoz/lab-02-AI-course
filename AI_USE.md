# AI-use declaration — Lab 02

**Tool used:** Claude Code (Anthropic, Claude Opus model), run in my terminal on my own laptop.

**What I used it for:**

- Running the notebook `lab02_inside_the_model.ipynb` locally (GPT-2 small through Hugging Face `transformers`)
  instead of in Colab, so that every cell has its outputs saved in the file.
- Drafting the text in the ✏️ cells: the four predictions, the explanations of temperature and top-p,
  the attention-head answers and the Part 3 answer. All the measured numbers were copied from the real output
  of the cells, not written from memory.
- Finding the per-head scores for layer 4 (to answer "does every head in that layer do the same thing?").
- Committing the finished notebook to my GitHub repository.

**What I did myself:** I read the lab instructions and the README, checked that the answers match the numbers
in the outputs (Part 0: 19 tokens; Part 1: ` Ast` 22.87% vs ` Paris` 22.08%, top-10 hold 64%; temperature: the #1
token never changes; previous-token head = layer 4, head 11; most extreme token-0 head = layer 7, head 10;
Part 3: Kazakh 1.10 vs Russian 1.11 tokens per character), and I am responsible for the submitted answers.

**Honest note on the "predict first" rule:** the predictions were written with the AI's help and not by me
alone before running each cell, so they do not fully follow the lab's rule. Where a prediction turned out wrong
(top-10 mass, #1 token, Kazakh vs Russian), the notebook says so next to the measured value.

**Not used:** no AI tool was used to change the lab's code, except replacing the three example prompts in
`MY_PROMPTS` and setting `LAYER, HEAD = 4, 11`, as the ✏️ TODOs ask.
