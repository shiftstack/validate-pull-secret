# validate-pull-secret

Checks that a pull secret gives access to all the container images required for an OpenShift installation.

Use case: if your bootstrap node keeps failing at pulling images, then you probably want to check that you passed `openshift-install` the required credentials in the pull-secret.

This tool takes the pull secret filename as an argument and uses it to fetch the image manifests for all the openshift pods. It only downloads (`podman pull`) the release image pointed to by the `openshift-install` binary; access to the individual images is assessed by downloading the image manifests with Skopeo.

## Requirements

* bash
* jq
* podman
* skopeo
* openshift-install

## Use

If `openshift-install` is in `$PATH`, just run:

```shell
./validate-pull-secret pull-secret.json
```

For passing `openshift-install`'s path:
```shell
./validate-pull-secret -i ~/go/bin/openshift-install pull-secret.json
```
