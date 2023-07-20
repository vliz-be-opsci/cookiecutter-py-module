FROM python:3.8-buster

COPY ./ /{{cookiecutter.module_name}}
WORKDIR /{{cookiecutter.module_name}}

RUN python -m pip install --upgrade pip && \
    pip install poetry && \
    make init

ENTRYPOINT ["{{cookiecutter.module_name}}"]
