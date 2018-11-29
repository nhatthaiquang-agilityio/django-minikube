FROM nhatthai/python3.6_django

COPY mysite /mysite
WORKDIR /mysite

COPY ./entrypoint.sh /
ENTRYPOINT ["/entrypoint.sh"]