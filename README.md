# validate-pull-secret

Checks that a pull secret can access all required resources for an OpenShift installation.

If your bootstrap node keeps failing at pulling images, then you probably want to check that you passed `openshift-install` the required credentials in the pull-secret.

This tool takes the pull secret filename as an argument and uses it to fetch the image manifests for all the openshift pods.

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
