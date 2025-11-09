FROM public.ecr.aws/lambda/python:3.13

# install uv
COPY --from=ghcr.io/astral-sh/uv:latest /uv /uvx /bin/

# copy pyproject.toml
COPY pyproject.toml .

# install dependencies with uv
RUN uv sync

# copy handler.py
COPY handler.py ${LAMBDA_TASK_ROOT}/

# set PYTHONPATH
ENV PYTHONPATH="${LAMBDA_TASK_ROOT}/.venv/lib/python3.13/site-packages"

# set CMD
CMD ["handler.resize_handler"]
