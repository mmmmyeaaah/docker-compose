FROM python:3.9-alpine

WORKDIR /usr/src/stocks_products

RUN apk update && apk add postgresql-dev gcc python3-dev musl-dev

RUN pip install --upgrade pip

COPY ./requirements.txt .

RUN pip install -r requirements.txt

COPY ./entrypoint.sh .
RUN sed -i 's/\r$//g' /usr/src/stocks_products/entrypoint.sh
RUN chmod +x /usr/src/stocks_products/entrypoint.sh

COPY . .

RUN mkdir /usr/src/stocks_products/staticfiles

ENTRYPOINT ["/usr/src/stocks_products/entrypoint.sh"]
