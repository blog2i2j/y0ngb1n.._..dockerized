# https://github.com/yegle/fava-docker
# https://github.com/swissmanu/docker-fava
# https://github.com/DIYgod/docker-fava

FROM python:bookworm AS build_env

WORKDIR /app

ENV PATH="/app/bin:$PATH"
RUN python3 -mvenv /app

ADD requirements.txt .
RUN pip3 install --no-cache-dir -r requirements.txt

FROM python:slim

COPY --from=build_env /app /app

ENV PATH="/app/bin:$PATH" \
    FAVA_HOST="0.0.0.0" \
    BEANCOUNT_FILE="/ledger/main.beancount"

EXPOSE 5000

ENTRYPOINT ["fava"]