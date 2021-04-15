# kub-data-01-starting-setup
## Learn k8s Volumes & Data
[deployment.yaml](https://github.com/sovernut/kub-data-01-starting-setup/commit/d471eb7926288c7ddd544938fe61bba417c8b1da#diff-3e3d094b07e9e7ff2eb410ec3f28180795c2fbbe33c8b61a1c13e3a8b53f87d7)
* add _metadata_ to define name of deployment
* add _replicas_ to define number of pods
* template of Deployment are always `Pods`
* _selector_ show what deployments can control so in this case it match `Pods` labels

[service.yaml](https://github.com/sovernut/kub-data-01-starting-setup/commit/d471eb7926288c7ddd544938fe61bba417c8b1da#diff-7b032461847f02192bb99ad5d10d6142580e260a8d9a036bda55d1537c57d4da)
* use type `LoadBalancer` to expose service to public network
* selector set to label name of `Pods`
* `port` is expose port, `targetPort` is inside container port (port that app listen to)

### Type of Volumes
* `emptyDir` will create empty dir when Pods is created, when Pods destroyed its also gone.
* `hostPath` set 2 parameter `path` and `type`
  * good for one pod environment (such as minikube)
  * `path` is path in WorkerNode
  * `type` can set to DirectoryOrCreate to create directory if it not exists.
* `persistentVolume` is volume that remain persist even Pods destroy ([commit](https://github.com/sovernut/kub-data-01-starting-setup/commit/30e48348b18ef2111ceb7c5efcac41e521a93942))
  * CSI volume is interface that any Cloud Provider can integrate to k8s
  * use `persistentVolumeClaim` to use persistentVolume


**note if anything incorrect feel free to inform me thanks 😸**
