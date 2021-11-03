FROM python:3.9

EXPOSE 8000

ENV USER compiler

RUN useradd --create-home --shell /bin/bash $USER && \
    chown -R $USER /home/$USER && \
    mkdir -p /workspace/best-practices && \
    chown -R $USER /workspace/best-practices

WORKDIR /workspace/best-practices

COPY . .

USER $USER

ENV PATH "$PATH:/home/$USER/.local/bin"

RUN pip install -r .devcontainer/requirements.txt && \
    pip install -r docs/requirements.txt

ENTRYPOINT ["python"]
CMD ["-m", "mkdocs", "serve", "--dev-addr=0.0.0.0:8000"]
