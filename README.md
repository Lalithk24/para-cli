![Logo](https://s3-eu-west-1.amazonaws.com/org.paraio/para.png)

# Para CLI

[![NPM version][npm-image]][npm-url] [![Build Status][travis-image]][travis-url]
[![Join the chat at https://gitter.im/Erudika/para](https://badges.gitter.im/Erudika/para.svg)](https://gitter.im/Erudika/para?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

## What is this?

**Para** was designed as a simple and modular backend framework for object persistence and retrieval.
It helps you build applications faster by taking care of the backend. It works on three levels -
objects are stored in a NoSQL data store or any old relational database, then automatically indexed
by a search engine and finally, cached.

This is the command-line tool for talking to a Para server.

## Installation

```sh
$ npm install -g para-cli
```

## Usage

```
                                 ________    ____
      ____  ____ __________ _   / ____/ /   /  _/
     / __ \/ __ `/ ___/ __ `/  / /   / /    / /  
    / /_/ / /_/ / /  / /_/ /  / /___/ /____/ /   
   / .___/\__,_/_/   \__,_/   \____/_____/___/   
  /_/                                            

  Command-line tool for Para backend servers

  Usage:
    $ para-cli [command] [file]

  Commands:
    create <file|glob> [--id] [--type]   Persists files as Para objects and makes them searchable
    read --id 123 [--id 345 ...]         Fetches objects with the given ids
    update <file.json|glob> ...          Updates Para objects with the data from a JSON file (must contain id field)
    delete [glob] --id 123 ...           Deletes one or more objects from Para
    new-key                              Generates a new secret key and saves it to config.json
    new-jwt                              Generates a new JWT super token to be used for app authentication
    ping                                 Tests the connection to the Para API and returns the auth. object

  Options:
    --type          Sets the "type" field of an object
    --id            Sets the "id" field of an object
    --sanitize      Strips all symbols from input files
    --accessKey     Sets the Para access key
    --secretKey     Sets the Para secret key
    --endpoint      Sets the URL of the Para server
    --help          Prints the list of commands
    --version       Prints the version of the program

  Examples:
    $ para-cli create my-blog-post.md
    $ para-cli read --id my-blog-post.md
    $ para-cli create index.html --type webpage --id "My new article" --sanitize
    $ para-cli delete --id 123 --id "my-blog-post.md"
    $ para-cli new-key

```

The tool supports basic CRUD operations on files and can also generate JWT 'super tokens' or new secret keys for your app.
You can use the CLI to upload multiple files, like blog posts, for example. The files can be HTML, text or JSON.

The plan is to add more functionality in the near future.

## Configuration

The configuration file is located in `~/.config/configstore/para-cli.json` and contains the keys used to authenticate with a Para server.
The properties `accessKey`, `secretKey` and `endpoint` can be passed as arguments or loaded from the config file.
Also you can choose to set the environment variables `PARA_ACCESS_KEY`, `PARA_SECRET_KEY` and `PARA_ENDPOINT`.

Once configured you can test your connection to the server:

```
$ para-cli ping
``` 

## Para Docs

### [Read the Docs](https://paraio.org/docs)

## Contributing

1. Fork this repository and clone the fork to your machine
2. Create a branch (`git checkout -b my-new-feature`)
3. Implement a new feature or fix a bug and add some tests
4. Commit your changes (`git commit -am 'Added a new feature'`)
5. Push the branch to **your fork** on GitHub (`git push origin my-new-feature`)
6. Create new Pull Request from your fork

For more information see [CONTRIBUTING.md](https://github.com/Erudika/para/blob/master/CONTRIBUTING.md)

## License
[Apache 2.0](LICENSE)


[npm-image]: https://badge.fury.io/js/para-cli.svg
[npm-url]: https://npmjs.org/package/para-cli
[travis-image]: https://travis-ci.org/Erudika/para-cli.svg?branch=master
[travis-url]: https://travis-ci.org/Erudika/para-cli
[daviddm-image]: https://david-dm.org/Erudika/para-cli.svg?theme=shields.io
[daviddm-url]: https://david-dm.org/Erudika/para-cli