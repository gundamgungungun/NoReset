# Repository working conventions

- Read [README.md](README.md) for the current product entry and local startup. Architecture is documented in `docs/ARCHITECTURE.md`; HTTP contracts are in `docs/API.md` and `contracts/api.ts`.
- Preserve the current framework and storage boundaries unless a change explicitly requires an architectural decision. Runtime implementation lives in `backend/` and `frontend/`.
- Test backend behavior through HTTP and the public storage interfaces. Mock only external model providers; keep online acceptance separate from offline tests.
- Run from the repository root with Python 3.12: `python -m pytest -q`, `python -m scripts.demo`. Use temporary databases in tests.
- Never commit `.env`, tokens, recovery passphrases, runtime databases, backups, private health records, personal media, or dependency directories. Use only explicitly synthetic fixtures or licensed public-case adaptations.
- Public case adaptations must retain provenance and licensing. Synthetic cases must stay explicitly synthetic. Preserve third-party attribution and do not present public cases as project-user trials.
- A successful record confirmation only confirms record accuracy; it never clears medical danger or authorizes medication changes.
- A `422` organize response can contain a saved original and an emergency notice. Clients must retain and display them.
- Keep real ASR/OCR, Mock behavior, software checks and clinical validation distinct. Do not turn historical notes into a current verification claim.
