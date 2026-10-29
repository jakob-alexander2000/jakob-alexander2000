# Jakob Alex

Berlin. Tools for asking questions of files you can open, with the source named on every result. CiteBot also marks whether each claim holds.

## Selected work

### [CiteBot](https://github.com/jakob-alexander2000/citebot)

Ask one employee handbook a question, and read the check under the answer.

[Try it](https://citebot-chi.vercel.app). The fixed questions, and what a pass requires, are on [the evaluation page](https://citebot-chi.vercel.app/evals).

![CiteBot verify step. A question goes to at most three handbook tools, then a draft the model writes. Both the draft and the verify step use those same passages. Verify marks each claim pass, fail, or unsupported.](assets/citebot-verify-light.svg#gh-light-mode-only)
![CiteBot verify step. A question goes to at most three handbook tools, then a draft the model writes. Both the draft and the verify step use those same passages. Verify marks each claim pass, fail, or unsupported.](assets/citebot-verify-dark.svg#gh-dark-mode-only)

The model drafts from the passages it just retrieved, with at most three handbook lookups. A second model call marks each claim against those same passages, and a refusal counts as pass when the handbook does not cover the question. `npm run eval` replays the loop offline with no key, using a scripted draft and a word-overlap check in place of the model. Limit: one sample handbook.

### [citebot-evals](https://github.com/jakob-alexander2000/citebot-evals)

Score a fixed set of CiteBot handbook questions, with no model and no network.

Source, runs locally. No key.

```bash
git clone https://github.com/jakob-alexander2000/citebot-evals.git
cd citebot-evals
npm install
npm run eval
```

Each case names the fact an answer must state and the file it must cite. Some must refuse, or correct a false premise. The command scores saved replies, not live model output. A live call to CiteBot is optional and is not the gate.

### [Desk](https://github.com/jakob-alexander2000/desk)

Ask a folder of notes on your machine. The answer names the files it used.

Source, runs locally. Needs a Gemini key.

```bash
git clone https://github.com/jakob-alexander2000/desk.git
cd desk
npm install
export GEMINI_API_KEY=your_key
npm run desk -- ask ./sample-notes "What is Desk?"
```

Passages are picked by word overlap, and each source shows its file and line range. The model writes the answer. A command line and a local page only; no desktop app.

### [desk-index](https://github.com/jakob-alexander2000/desk-index)

Rank the Markdown in a folder. No model on this path.

Source, runs locally. No key.

```bash
git clone https://github.com/jakob-alexander2000/desk-index.git
cd desk-index
go test ./...
go run ./cmd/desk-index search -dir ./sample-notes "core hours"
```

The index lives in memory and ranks a file by how often the query words appear and how rare they are in the folder. Go standard library only.

<!-- Further entries go here after Jakob approves them. Same shape: one line on what it does, one proof link or command, one limit. -->
