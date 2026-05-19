FROM python:3.9

EXPOSE 8080
USER root

# ENV INSTANA_SERVICE_NAME=payment

WORKDIR /app

COPY requirements.txt /app/

RUN pip install -r requirements.txt

COPY *.py /app/
COPY payment.ini /app/

#CMD ["python", "payment.py"]
# with this cmd the development server will start but it is not recommended for production use as it is not designed to handle high loads or concurrent requests efficiently. Instead, we can use a production-ready WSGI server like uWSGI to serve the application. The uWSGI server is more robust and can handle multiple requests simultaneously, making it suitable for production environments.
CMD ["uwsgi", "--ini", "payment.ini"]

