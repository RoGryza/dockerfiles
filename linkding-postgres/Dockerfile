ARG UPSTREAM_TAG=1.8.5
FROM sissbruecker/linkding:$UPSTREAM_TAG

LABEL description="linkding configured with postgresql"

RUN /opt/venv/bin/pip install -U psycopg2-binary

# TODO this is a hacky placeholder while upstream doesn't support postgres
RUN apt-get install -y patch
COPY queries.patch .
RUN patch bookmarks/queries.py queries.patch

RUN mv siteroot/settings/base.py siteroot/settings/original_base.py
COPY override_base.py siteroot/settings/base.py
