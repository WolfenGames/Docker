FROM ruby:latest

RUN apt update -y && apt upgrade -y && apt install yarn git -y && gem install rails && mkdir -p /opt/eish

ONBUILD WORKDIR /opt/eish

ONBUILD ADD . /opt/eish

ONBUILD EXPOSE 3000

ONBUILD RUN bundle install --without production && rails db:migrate && rails db:seed && rails test

# docker build -t ft-rails:on-build .
# git clone https://github.com/mhartl/hello_app_original.git FUCK
# echo "FROM\tft-rails:on-build\n\nEXPOSE\t3000\n\nCMD\t[\"rails\", \"s\", \"-b\", \"0.0.0.0\", \"-p\", \"3000\"]" > FUCK/Dockerfile
# docker build -t rails ./FUCK
# docker run --rm -p 3000:3000 rails 