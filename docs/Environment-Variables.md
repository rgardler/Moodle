# Environment Variables

In order to configure our deployment and tools we'll set up some
environment variables to ensure consistency. If you are running these
scripts through SimDem you can customize these values by copying and
editing `env.json` into `env.local.json`.

We'll need a unique name for our Resource Group in Azure, but when
running in an automated mode it is useful to have a (mostly) unique
name for your deployment and related resources. We'll use a timestamp.
If the environmnt variable `MOODLE_RG_NAME` is not set we will
create a new value using a timestamp:


``` shell
if [ -z "$MOODLE_RG_NAME" ]; then MOODLE_RG_NAME=moodle_$(date +%Y-%m-%d-%H); fi
echo "Resource Group Name : $MOODLE_RG_NAME"
```

Other configurable values for our Azure deployment include the
location and depoloyment name. We'll standardize these, but you can
use different values if you like.

``` shell
MOODLE_RG_LOCATION=southcentralus
MOODLE_DEPLOYMENT_NAME=MasterDeploy
```

We also need to provide an SSH key. Later we'll generate this if it
doesn't already exist but to enable us to reuse an existing key we'll
store it's filename in an Environment Variable.

``` shell
MOODLE_SSH_KEY_FILENAME=~/.ssh/moodle_id_rsa
```

We need a workspace for storing configuration files and other
per-deployment artifacts:

``` shell
MOODLE_AZURE_WORKSPACE=~/.moodle
```

