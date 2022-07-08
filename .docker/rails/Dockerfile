FROM ruby:3.1.2

# Install node 16-LTS and yarn
RUN curl -fsSL https://deb.nodesource.com/setup_16.x | bash -
RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -
RUN apt-get update -qq && apt-get install -qq --no-install-recommends \
    nodejs \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*
RUN npm install -g yarn@1.22.19

WORKDIR /usr/src/app

COPY ./rails/Gemfile* ./
RUN bundle install
COPY ./rails .

EXPOSE 3000

ARG SECRET_KEY_BASE=123458bb7ef6402f6a8bcf5d3be54321
ARG RAILS_ENV=production
RUN SECRET_KEY_BASE=${SECRET_KEY_BASE} RAILS_ENV=${RAILS_ENV} bundle exec rake assets:precompile

CMD ["bundle", "exec", "puma", "-C", "config/puma.rb"]
