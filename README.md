# Installing Open Data Hub on Azure Red Hat OpenShift

The purpose of this repo is to provide sample instructions for installing Open Data Hub (ODH) in Azure Red Hat OpenShift (ARO).  We'll do a smoke test of the components to ensure Open Data Hub components operate as expected.

## Prerequisites

* Azure Red Hat OpenShift 4
* Admin access to OpenShift

## Prep

Login to the cluster using `oc login` and admin credentials.

Create a new project for ODH:

```bash
oc new-project odh
```

## Open Data Hub

We will deploy ODH using the Operator.

Login to the cluster using the console and admin credentials.

Navigate to OperatorHub and search for `Open Data Hub Operator`.  Install using the `beta` channel.  The version installed in this guide is `0.9`.

![ODH Install](images/odh_install.png)



## Troubleshooting

1.  If you delete the ODH operator and need to reinstall again, you have to make sure the operator group has been deleted.  Otherwise the next install will move into a stuck `Pending` state.

```
oc delete operatorgroup opendatahub -n openshift-operators
```