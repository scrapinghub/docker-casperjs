# scrapinghub-image-casperjs

Recommended base Docker image for CasperJS spiders at Scrapinghub.

## shub-exec

`shub-exec` is a utility that converts project and spider settings to environment variables and
job arguments to [CasperJS command line options](http://docs.casperjs.org/en/latest/cli.html).

This tool can be used in [start-crawl](http://shub.readthedocs.io/en/latest/custom-images-contract.html#contract-statements)
script as last command that exec the real spider script, but before it setups environment from settings
in `SHUB_SETTINGS` environment variable and arguments according to `SHUB_JOB_DATA` environment variable.

An example start-crawl for CasperJS is:

```
#/bin/sh
exec shub-exec -- casperjs --debug /app/$SHUB_SPIDER
```

For a job whose spider name is simple.js and job arguments are url=http://scrapinghub.com it will run:

    casperjs --debug /app/simple.js --url=http://scrapinghub.com

It's important to have `--` before the positional arguments, it helps to distinguish shub-exec options
from script options.

If the job has some setting set, i.e. LOGLEVEL=DEBUG, it will be available in CasperJS
process environment as 'LOGLEVEL' with value 'DEBUG'.
