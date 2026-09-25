FROM python:3.13-slim

COPY --from=ghcr.io/astral-sh/uv:latest /uv /bin/


RUN pip install pandas pyarrow

WORKDIR /code

ENV PATH="/code/.venv/bin:$PATH"

COPY pyproject.toml uv.lock .python-version ./

RUN uv sync --locked

COPY pipeline.py .

ENTRYPOINT [ "run", "python", "pipeline.py"]