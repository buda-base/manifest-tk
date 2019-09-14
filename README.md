# BDRC Image Manifest doc and API

This repository contains documentation and API endpoints for BDRC image manifests.

The BDRC Image Manifests are json file present in the s3 directory of the corresponding images. It contains information such as:
- the order of images
- the pagination information
- some basic layout information (physical dimensions, margins, inter line space, etc.)

See the [examples/](examples/) directory for some examples.

## API

The API to access and write the manifest files is rather simple:

```
GET https://iiifpres.bdrc.io/im/{volumeId}
```

for reading (no access restriction), and:

```
PUT https://iiifpres.bdrc.io/im/{volumeId}
```

for writing an image manifest, knowing that:
- the request must have an `Authorization` header with a token valid for BDRC
- the given document must have a `spec-version` field and respect the json schema corresponding to the version (TODO)
- the document must have a `rev` field, and a mechanism similar to [CouchDB's](https://docs.couchdb.org/en/latest/intro/api.html#revisions) will be used to check that no conflict happened