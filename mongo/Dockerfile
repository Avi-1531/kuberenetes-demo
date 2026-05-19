

# If it’s the first run
# It starts mongod in a special way and then executes all scripts in:
# /docker-entrypoint-initdb.d/*.js
# /docker-entrypoint-initdb.d/*.sh
# Your user.js, catalogue.js run at this stage and:
# Create DBs/collections.
# Insert initial data.
# Create users, indexes, etc.
# On later container starts
# The data directory already has Mongo files.
# The entrypoint detects “DB already initialized.”
# It skips running /docker-entrypoint-initdb.d/*.
# It just starts mongod with the existing data.

# Uses the official MongoDB image, version 5, as the base.
# That image already includes:
# mongod
# An entrypoint script that knows how to run init scripts on first startup.
# dockerfile

# Collapse
# Save
# Copy
# 1
# COPY *.js /docker-entrypoint-initdb.d/
# Copies all *.js files from your build context (e.g., user.js, catalogue.js) into /docker-entrypoint-initdb.d/ inside the image.
# In the mongo official image, any .js or .sh placed in /docker-entrypoint-initdb.d/ is executed once, automatically, when:
# The container starts, and
# The data directory is empty (i.e., first initialization of the database).
# So, behind the scenes:

# You build this image.
# When you run a container from it:
# The Mongo entrypoint starts mongod.
# Detects that the DB is uninitialized (first run).
# Executes each *.js file in /docker-entrypoint-initdb.d/ in alphabetical order.
# Your user.js and catalogue.js typically:
# Create databases/collections.
# Insert seed data.
# Set up indexes, users, etc.

FROM mongo:5

COPY *.js /docker-entrypoint-initdb.d/

