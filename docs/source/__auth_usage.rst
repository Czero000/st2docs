To acquire a new token via the CLI, run the ``st2 auth`` command.  If password is not provided,
then ``st2 auth`` will prompt for the password. If successful, a token is returned in the
response. ::

    # with password
    st2 auth yourusername -p yourpassword

    # without password
    st2 auth yourusename
    Password:

The following is a sample API call via curl using the token. ::

    curl -H "X-Auth-Token: 4d76e023841a4a91a9c66aa4541156fe" https://myhost.example.com/api/v1/actions

The following is the equivalent for CLI. ::

    # Include the token as command line argument.
    st2 action list -t 4d76e023841a4a91a9c66aa4541156fe

    # Or set the token as an environment variable.
    export ST2_AUTH_TOKEN=4d76e023841a4a91a9c66aa4541156fe
    st2 action list

Note that there can be use cases when you want the TTL to be different from default.
You can specify a TTL (in seconds) when you request a token. To get a token that is valid
for 10 minutes, use the following:

::

    # with TTL and password
    st2 auth yourusername -p yourpassword -l 600

Note that if the TTL requested is greater than maximum allowed TTL in st2 configuration, you'd get an error.

If you don't want to retrieve a new token and configure the environment variable
every time you start a new shell session, you can put your StackStorm
credentials in the CLI configuration file and the CLI will automatically authenticate,
retrieve and cache the auth token for you.

For information on how to do that, see the :ref:`CLI configuration
<cli-configuration>` page.
