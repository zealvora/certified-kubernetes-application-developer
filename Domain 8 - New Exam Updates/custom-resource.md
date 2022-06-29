#### Kubernetes Documentation Referred for Base CRD manifests:

https://kubernetes.io/docs/tasks/extend-kubernetes/custom-resources/custom-resource-definitions/

#### Manifests File (Step 1 and Step 2)

crd.yaml
```sh
apiVersion: apiextensions.k8s.io/v1
kind: CustomResourceDefinition
metadata:
  name: crontabs.kplabs.internal
spec:
  group: kplabs.internal
  versions:
    - name: v1
      served: true
      storage: true
      schema:
        openAPIV3Schema:
          type: object
          properties:
            spec:
              type: object
              properties:
                cronSpec:
                  type: string
                image:
                  type: string
                replicas:
                  type: number
  scope: Namespaced
  names:
    plural: crontabs
    singular: crontab
    kind: CronTab
    shortNames:
    - ct
```

crd-object.yaml
```sh
apiVersion: "kplabs.internal/v1"
kind: CronTab
metadata:
  name: my-new-cron-object
spec:
  cronSpec: "* * * * */5"
  image: my-awesome-cron-image
  replicas: 3
```
AWS Service Operator Manifest File:

https://raw.githubusercontent.com/awslabs/aws-service-operator/master/configs/aws-service-operator.yaml

