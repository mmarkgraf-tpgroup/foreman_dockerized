Foreman, dockerized
===================

This is a meta-role to pull in both

- tp.foreman, to create a foreman-instance in a docker container
- tp.forman_configure, to apply its configuration

In order to have your specific setup, overwrite the "foreman_"-variables you need to change
from your group_vars.  You do not want to create all those variables from scratch.

If you have an existing foreman-instance, you can run tp.foreman_configure with the
"write_resource_info"-tag, to fetch your config and copy the results to your group_vars.

Otherwise, click your config in the foreman-web-frontend and then do the same.
