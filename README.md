# Interoperability Test Harness ProvStore Extension

[Southampton Provenance Tool Suite](https://provenance.ecs.soton.ac.uk) interoperability test harness ProvStore extension. This package consists of classes that extend the [interoperability test harness framework](https://github.com/prov-suite/interop-test-harness/tree/package) to allow interoperability testing of [ProvStore](https://provenance.ecs.soton.ac.uk/store/).

The test harness runs under Python 2.7+ and Python 3.

[![Build Status](https://travis-ci.org/prov-suite/provstore-interop-job.svg)](https://travis-ci.org/prov-suite/provstore-interop-job)

---

## Installation

The instructions have been written with reference to the 64-bit [Ubuntu](http://www.ubuntu.com/) 14.04.2 operating system.

Other operating systems, or versions of these, may differ in how packages are istalled, the versions of these packages available from package managers etc. Consult the relevant documentation for your operating system and the products concerned.

Some dependencies require you to have sudo access to install and configure software (or a local system administrator can do this for you).

This page assumes that [pyenv](https://github.com/yyuu/pyenv) is used to manage Python versions.

Install the interoperability test harness framework

* See [interoperability test harness framework](https://github.com/prov-suite/interop-test-harness/blob/package/README.md)

Install package

```
$ pip install -r requirements.txt
$ python setup.py install
```

Run unit tests

```
$ nosetests prov_interop_provstore.tests
```

---

## Running ProvStore interoperability tests

Get the interoperability test cases

```
$ git clone https://github.com/prov-suite/testcases
```

Get a ProvStore API Key:

* Log in to [ProvStore](https://provenance.ecs.soton.ac.uk/store)
* Select Account => Developer Area
* You will see your API key

Define a `PROVSTORE_API_KEY` with your API key:

```
$ export PROVSTORE_API_KEY=user:qwert12345
```

Run interoperability tests:

```
$ nosetests -v prov_interop_provstore.interop_tests
```

If you are running on a multi-processor machine then the tests can run in parallel, using nosetests' support for [parallel testing](http://nose.readthedocs.org/en/latest/doc_tests/test_multiprocess/multiprocess.html). Specify the number of processes you want to use using a `--processes` flag e.g.

```
$ nosetests --processes=4 -v prov_interop_provstore.interop_tests
```

---

## Running ProvStore interoperability tests under Travis CI

[.travis.yml](./.travis.yml) provides an example Travis CI configuration file

You will need to define a Travis CI variable, `PROVSTORE_API_KEY` holding your ProvStore user name and API key:

* Visit your job's settings page in Travis CI
* Select settings
* Click Environment Variables
* Click Add a new variable
  - Name: `PROVSTORE_API_KEY`
  - Value: `user:qwert12345`
  - Ensure Display value in build logs is *not* selected
  - See [define variables in repository settings](http://docs.travis-ci.com/user/environment-variables/#Defining-Variables-in-Repository-Settings).

---

## Changing the ProvStore URL

Either:

* Edit:

```
prov_interop_provstore/interop_tests/provstore.yaml
```

* Change the following to specify the URL you wish to use.

```
url: https://provenance.ecs.soton.ac.uk/store/api/v0/documents/
```

* Reinstall the package, as above.
* Run the interoperability tests, as above.

Or:

* Copy the interoperability test configuration file:

```
$ cp prov_interop_provstore/interop_tests/provstore.yaml myprovstore.yaml
```

* Edit `myprovstore.yaml` as above.
* Set an environment variable, `PROVSTORE_TEST_CONFIGURATION`, with the path to this file:

```
$ export PROVSTORE_TEST_CONFIGURATION=$PWD/myprovstore.yaml
```

* Reinstall the package, as above.
* Run the interoperability tests, as above.

---

## API documentation

To create API documentation in `apidocs/_build/html`:

```
$ pip install sphinx
$ make apidocs
```

---

## Author

Developed by [The Software Sustainability Institute](http://www.software.ac.uk>) and the [Provenance Tool Suite](http://provenance.ecs.soton.ac.uk/) team at [Electronics and Computer Science](http://www.ecs.soton.ac.uk) at the [University of Southampton](http://www.soton.ac.uk).

For more information, see our [document repository](https://github.com/prov-suite/ssi-consultancy/).

---

## License

The code is released under the MIT license.
