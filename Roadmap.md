# Roadmap

## 1. Resource framework
Historically ror has been handling internal resources in another way than Kubernetes api-resources. Mainly by storing them in their own collections. From a birds-eyes view this does not make that much sense as it constrains expansion and development. There is also specific code handling the different internal resources making it less maintainable as if we had the same code handling all resources.
Resource framework unifies internal and Kubernetes resources as “rorresources”. This is done by extending the Kubernetes api definition with additional metadata and api-definitions.

Takeaways:
-	Unified way to store, transport and process all resources.
-	Easily extendible with new resource kinds.
-	Easier to query resources across clusters (global reports)

Cons:
-	Project is the new top-level owner but it’s not implemented in the acl-model yet. Some opinionated inheritance rules might get implemented.
-	This might come with an api-version bump for some apis. This might be mitigated in a potentially breaking way, but we are v0.0.500 so it might be acceptable. 

## 2. Finalize the cluster provider framework
Ror is k8s-provider agnostic and we have implemented providers for Vmware Tanzu and Kind. There is some work to be done to finalize this so that any new providers can just plug in to this approach. Additional providers will shed more light on whats missing but its known that some logic round scaling and deletion must be clarified and polished.

## Remove NHN-opinionated code

There will be a continous work to remove NHN opinioneted code.
