FROM mcr.microsoft.com/vscode/devcontainers/python:0-{{ cookiecutter.python_version }}

{% if cookiecutter.use_docker_inside_container == "y" -%}
# Install Docker
RUN curl -fsSL https://get.docker.com -o get-docker.sh \
    && apt-get install -y wget \
    && sh get-docker.sh \
    && usermod -aG docker root \
    && apt autoremove

# Install Docker Compose
RUN LATEST_COMPOSE_VERSION=$(curl -sSL "https://api.github.com/repos/docker/compose/releases/latest" | grep -o -P '(?<="tag_name": ").+(?=")') \
    && curl -sSL "https://github.com/docker/compose/releases/download/${LATEST_COMPOSE_VERSION}/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose \
    && chmod +x /usr/local/bin/docker-compose

{% endif -%}
# Install SQLite 3
#RUN apt-get update && apt-get install -y sqlite3 && apt autoremove

RUN pip install --no-cache-dir -U pip \
    && pip install --no-cache-dir poetry ipython \
    && poetry config virtualenvs.create false