# How to run locally

The lab is made for Colab, but it also runs on a normal laptop CPU, no GPU and no API key needed.
Tested on Windows 11, Python 3.12.

## 1. What you need

- **Python 3.10–3.12** (torch 2.5.1 has no wheels for 3.13 yet)
- **git**
- ~3 GB free disk (torch ~1–2 GB + GPT-2 model ~0.5 GB)
- internet for the first run (the model is downloaded once and cached)

Check:

```
python --version
git --version
```

On macOS / Linux the command may be `python3` instead of `python`.

## 2. Get the code

```
git clone https://github.com/daulet-kushek-narxoz/lab-02-AI-course.git
cd lab-02-AI-course
```

## 3. Create venv and install

### Windows (PowerShell)

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
pip install -r requirements.txt
```

If PowerShell says *"running scripts is disabled"*, run once:

```powershell
Set-ExecutionPolicy -Scope CurrentUser RemoteSigned
```

In `cmd.exe` activate with `.venv\Scripts\activate.bat` instead.

### Linux

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
# CPU-only torch, much smaller than the default CUDA build
pip install torch==2.5.1 --index-url https://download.pytorch.org/whl/cpu
pip install -r requirements.txt
```

If `venv` is missing on Ubuntu/Debian: `sudo apt install python3-venv`.

### macOS

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
pip install -r requirements.txt
```

Works on both Apple Silicon and Intel. No Python yet? `brew install python@3.12`.

After activation the prompt starts with `(.venv)`, so you know the venv is on.

## 4. Run the notebook

### Option A — run everything from the terminal (full run)

Same command on all three systems:

```
python -m nbconvert --to notebook --execute --inplace --ExecutePreprocessor.timeout=900 lab02_inside_the_model.ipynb
```

This runs all cells and saves the outputs into the notebook. First run takes a few minutes
(model download), after that ~1 minute.

> Note: this is like *Run all* — you see every answer at once. To follow the lab's
> "predict first" rule, use Option B.

### Option B — cell by cell (interactive)

```
pip install notebook
jupyter notebook lab02_inside_the_model.ipynb
```

The browser opens, run cells one by one with **Shift+Enter**.

Or open the `.ipynb` in **VS Code** (Python + Jupyter extensions) and pick `.venv` as the kernel
in the top right corner.

### Option C — Colab

No install at all: open the notebook in Colab from the README badge.

## 5. After the run

- Outputs are saved in `lab02_inside_the_model.ipynb` (open it in Jupyter / VS Code / GitHub).
- Check the key numbers: `бөлімшеңізде` = 19 tokens, ` Ast` 22.87% vs ` Paris` 22.08%,
  previous-token head (4, 11), token-0 head (7, 10).
- Leave the venv:

  ```
  deactivate
  ```

- Next time just activate again (step 3, the `activate` line only) and run.

## 6. Cleanup (optional)

Delete the venv:

- Windows: `Remove-Item -Recurse -Force .venv`
- Linux / macOS: `rm -rf .venv`

The model cache stays in `~/.cache/huggingface` (Windows: `C:\Users\<you>\.cache\huggingface`),
delete it too if you need the space.

## Common problems

| Problem | Fix |
|---|---|
| `No matching distribution found for torch==2.5.1` | Python is 3.13+ — install 3.12 and recreate the venv |
| `ModuleNotFoundError` | venv is not activated — activate it and run again |
| `HF_TOKEN` warning | ignore it, the model is public |
| symlinks warning on Windows | harmless; hide it with `$env:HF_HUB_DISABLE_SYMLINKS_WARNING=1` |
| `Kernel died` / out of memory | close other apps, the model needs ~1 GB RAM |
