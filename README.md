docker-RVM-Rubinius
===================

Docker image to run Rubinius applications

Usage Dockerfile example
------------------------

    FROM davidgaya/rvm-rubinius

    # Gem dependencies
    ADD ./Gemfile /app/
    ADD ./Gemfile.lock /app/
    RUN /bin/bash -l -c "bundle"

    # NPM dependencies
    ADD ./package.json /app/
    RUN npm install

    # Add rest of source code
    ADD . /app/

    # Compile assets
    #RUN /bin/bash -l -c "bundle exec rake assets:clean"
    #RUN /bin/bash -l -c "rake assets:precompile"
    WORKDIR /app
    CMD /bin/bash -l -c "puma"
