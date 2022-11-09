# pycircleci

[![PyPI version](https://badge.fury.io/py/pycircleci-async.svg)](https://badge.fury.io/py/pycircleci-async)
[![Build Status](https://github.com/theY4Kman/pycircleci-async/actions/workflows/test.yml/badge.svg?branch=master)](https://github.com/theY4Kman/pycircleci-async/actions/workflows/test.yml?query=branch%3Amaster)

Asynchronous Python client for [CircleCI API](https://circleci.com/docs/2.0/api-intro/).

Ported from [pycircleci](https://github.com/alpinweis/pycircleci), a fork of the discontinued [circleci.py](https://github.com/levlaz/circleci.py) project.

## Features

- Supports [API v1.1](https://circleci.com/docs/api/#api-overview) and [API v2](https://circleci.com/docs/api/v2/)
- Supports both `circleci.com` and self-hosted [Enterprise CircleCI](https://circleci.com/enterprise/)

## Installation

    $ pip install pycircleci-async

## Usage

Create a personal [API token](https://circleci.com/docs/2.0/managing-api-tokens/#creating-a-personal-api-token).

Set up the expected env vars:

    CIRCLE_TOKEN           # CircleCI API access token
    CIRCLE_API_URL         # CircleCI API base url. Defaults to https://circleci.com/api

```python
import asyncio
from pycircleci_async import CircleCIClient


async def main():
    async with CircleCIClient(token='<access-token-uuid>') as circle_client:
        # get current user info
        await circle_client.get_user_info()

        # get list of projects
        results = await circle_client.get_projects()


asyncio.run(main())
```


### Contributing

1. Fork it
2. Install poetry (`pip install poetry`)
3. Install dependencies (`poetry install`)
4. Create your feature branch (`git checkout -b my-new-feature`)
5. Make sure `flake8` and the `pytest` test suite successfully run locally
6. Commit your changes (`git commit -am 'Add some feature'`)
7. Push to the branch (`git push origin my-new-feature`)
8. Create new Pull Request
