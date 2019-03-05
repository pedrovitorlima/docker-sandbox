FROM nginx:latest
LABEL mantainer 'Pedro Rodrigues'

RUN echo '<h1>No content</h1>' > /usr/share/nginx/html/conteudo.html
COPY *.html /usr/share/nginx/html

#>>docker image build -t ex-build-copy .