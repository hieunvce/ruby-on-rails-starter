FROM ruby:3.1.2
WORKDIR /usr/src/app

COPY Gemfile* ./
RUN bundle install
COPY . .
RUN bundle install

EXPOSE 3000
CMD ["rails", "server", "-b", "0.0.0.0"]
