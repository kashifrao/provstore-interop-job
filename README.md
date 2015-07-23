# ProvStore Interoperability Tests

[ProvStore](https://provenance.ecs.soton.ac.uk/store/) interoperability test job.

[![Build Status](https://travis-ci.org/prov-suite/provstore-interop-job.svg)](https://travis-ci.org/prov-suite/provstore-interop-job)

The Travis CI test job:

* Gets [ProvPy](https://github.com/trungdong/prov) via 'pip' (most recent release).
* Configures interoperability test harness.
* Runs interoperability tests to validate ProvStore conversions. Conversions are validated using ProvPy's prov-compare script.

The job assumes you have 

* Created a ProvStore API Key:
  - Log in to [ProvStore](https://provenance.ecs.soton.ac.uk/
store)
  - Select Account => Developer Area
  - You will see your API key

* Defined a Travis CI variable, `PROVSTORE_API_KEY` holding your ProvStore user name and API key:

* Visit your job's settings page in Travis CI
* Select settings
* Click Environment Variables
* Click Add a new variable
* Name: `PROVSTORE_API_KEY`
* Value: `user:qwert12345`
* Ensure Display value in build logs is *not* selected

See [define variables in repository settings](http://docs.travis-ci.com/user/environment-variables/#Defining-Variables-in-Repository-Settings).

## Author

Developed by [The Software Sustainability Institute](http://www.software.ac.uk>) and the [Provenance Tool Suite](http://provenance.ecs.soton.ac.uk/) team at [Electronics and Computer Science](http://www.ecs.soton.ac.uk) at the [University of Southampton](http://www.soton.ac.uk).

For more information, see our [document repository](https://github.com/prov-suite/ssi-consultancy/).

## License

These tests are released under the MIT license.
