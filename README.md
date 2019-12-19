# Wine in Docker
ikus060/docker-wine are Docker image with pre-installed wine prefix

# Tags

* `:buster` base on Debian buster with wine version `wine-4.0 (Debian 4.0-2)`
* `:stretch` make use of Debian stretch as a base image `wine-1.8.7 (Debian 1.8.7-2)`
* `:staging` base on Debian buster with wine-staging branch installed from PPA
* `:stable` base on Debian buster with wine-stable branch installed from PPA

# Usages

These images are particularly useful in a CICD pipeline to test stuff in a Windows like environment.

To execute command in wine prefix, you must call `wine` command line. e.g.:


    docker run --rm -it ikus060/docker-wine:stretch wine cmd /c echo coucou

# Troubleshooting

While executing a wine command line, if you see error like this:

    0009:err:winediag:nodrv_CreateWindow Application tried to create a window, but no driver could be loaded.
    0009:err:winediag:nodrv_CreateWindow Make sure that your X server is running and that $DISPLAY is set correctly
    
You must allocate a virtual X server using `(Xvfb :99 &) && export DISPLAY=:99`

# See Also

You could also take a look at `ikus060/docker-wine-maven` which is base on this one providing maven and java pre-installed in a wine prefix.

