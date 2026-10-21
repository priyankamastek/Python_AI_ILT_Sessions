1. Check your prerequisites.

CMD:
python --version      # should be 3.11 or higher
git --version
claude --version


2. Install uv.

CMD:
pip install uv
uv --version

3. Create the project.

mkdir cg-listings-uk
cd cg-listings-uk
git init
uv init --package --name cglistings
uv add pandas fastapi "uvicorn[standard]" streamlit pydantic
uv add --dev pytest pytest-cov httpx ruff
uv run python -c "import pandas, fastapi, streamlit; print('ok')"
git add .
git commit -m "Initial project setup"
claude

4. Add extension in VSCode 

claude Claude Code for VS Code (Anthropic)
Trust the folder
Open Claude code

5. First Prompt: What files are in this project, and what does pyproject.toml contain?