# arXiv funding

## Problem 

Information about funding sources associated with scientific outputs (including
arXiv e-prints) is increasingly in demand, e.g. for compliance with 
open access mandates. The core metadata model for arXiv does not support 
funding information. We want to both minimize changes to the 
canonical record, but also allow for a variety of workflows for adding funding
information. This project introduces a new service that can accession and make
available funding information about specific arXiv e-prints.

One big challenge will be thinking about whether/how to leverage taxonomies or
authority lists to ensure that we have normalized data without having to
maintain our own lists of funders. For example, NIH [publishes a list of
funding agencies](https://www.nlm.nih.gov/bsd/grant_acronym.html) used in
PubMed, including agencies outside the US, but it's unclear whether or not this
will be sufficient for arXiv.

## Requirements

1. Author-owners can add/edit funding information about their e-prints. They
   should be able to enter/select an agency, a grant/award number, and 
   possibly other information about the grant.
2. Readers can view funding information for specific e-prints.
3. Provide a RESTful JSON API that allows authorized clients to add/edit
   funding information.

   - Author-owner delegate via OAuth2 workflow.
   - Client owned by the author-owner.
   - Other authorized client, e.g. internal arXiv system client.

4. Provide a RESTful JSON API that supports:

  - Retrieve funding information for a specific e-print.
  - Retrieve e-prints associated with a particular funding agency and/or award.

5. Publishes system notifications (via Kinesis) about new funding information.


## Quick-start

We use [Pipenv](https://github.com/pypa/pipenv) for dependency management.

```bash
pipenv install --dev
```

You can run either the API or the UI using the Flask development server.

```bash
FLASK_APP=ui.py FLASK_DEBUG=1 pipenv run flask run
```

Dockerfiles are also provided in the root of this repository. These use uWSGI and the
corresponding ``wsgi_[xxx].py`` entrypoints.

## Contributing

Please see the [arXiv contributor
guidelines](https://github.com/arXiv/.github/blob/master/CONTRIBUTING.md) for
tips on getting started.

## Code of Conduct

All contributors are expected to adhere to the [arXiv Code of
Conduct](https://arxiv.org/help/policies/code_of_conduct).