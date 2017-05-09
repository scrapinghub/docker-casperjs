# scrapinghub-image-casperjs

Recommended base Docker image for CasperJS spiders at Scrapinghub.

## env2options

`env2options` is a utility that merges job arguments and Scrapinghub spider/project settings and converts them to the
[CasperJS command line options](http://docs.casperjs.org/en/latest/cli.html):


```
usage: env2options [-h] {all,arguments,settings}

Utility to convert job arguments and/or job settings to the CasperJS command line options

positional arguments:
  {all,arguments,settings}
                        Select what should be converted to command line options

optional arguments:
  -h, --help            show this help message and exit
```

For example you can use it in `start-crawl` script:

```
#!/usr/bin/env bash

casperjs /app/$SHUB_SPIDER $(env2options arguments)
```
