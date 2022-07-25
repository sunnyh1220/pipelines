

## pipeline installing
```bash
# install
# deep-arena-store:5000/ml-pipeline
# registry.harbor:5000/ml-pipeline
kubectl apply -k manifests/kustomize/cluster-scoped-resources
kubectl wait --for condition=established --timeout=60s crd/applications.app.k8s.io
kubectl apply -k manifests/kustomize/env/platform-agnostic-pns

# uninstall
kubectl delete -k manifests/kustomize/env/platform-agnostic-pns
kubectl delete -k manifests/kustomize/cluster-scoped-resources
```

## pipeline依赖的gcr.io镜像
```bash
# gcr.io/ml-pipeline/argoexec:v3.1.6-patch-license-compliance
docker pull hisunyh/gcr.io.ml-pipeline.argoexec:v3.1.6-patch-license-compliance
docker tag hisunyh/gcr.io.ml-pipeline.argoexec:v3.1.6-patch-license-compliance deep-arena-store:5000/ml-pipeline/argoexec:v3.1.6-patch-license-compliance
docker push deep-arena-store:5000/ml-pipeline/argoexec:v3.1.6-patch-license-compliance

# registry.harbor:5000/ml-pipeline
docker pull hisunyh/gcr.io.google-containers.busybox:latest
docker tag hisunyh/gcr.io.google-containers.busybox:latest deep-arena-store:5000/ml-pipeline/busybox:latest
docker push deep-arena-store:5000/ml-pipeline/busybox:latest
```

```bash
docker pull hisunyh/gcr.io.ml-pipeline.minio:RELEASE.2019-08-14T20-37-41Z-license-compliance
docker tag hisunyh/gcr.io.ml-pipeline.minio:RELEASE.2019-08-14T20-37-41Z-license-compliance deep-arena-store:5000/ml-pipeline/minio:RELEASE.2019-08-14T20-37-41Z-license-compliance

docker pull hisunyh/gcr.io.ml-pipeline.metadata-envoy:1.7.0
docker tag hisunyh/gcr.io.ml-pipeline.metadata-envoy:1.7.0 deep-arena-store:5000/ml-pipeline/metadata-envoy:1.7.0

docker pull hisunyh/gcr.io.ml-pipeline.frontend:1.7.0
docker tag hisunyh/gcr.io.ml-pipeline.frontend:1.7.0 deep-arena-store:5000/ml-pipeline/frontend:1.7.0

docker pull hisunyh/gcr.io.ml-pipeline.metadata-writer:1.7.0
docker tag hisunyh/gcr.io.ml-pipeline.metadata-writer:1.7.0 deep-arena-store:5000/ml-pipeline/metadata-writer:1.7.0

docker pull hisunyh/gcr.io.ml-pipeline.cache-deployer:1.7.0
docker tag hisunyh/gcr.io.ml-pipeline.cache-deployer:1.7.0 deep-arena-store:5000/ml-pipeline/cache-deployer:1.7.0

docker pull hisunyh/gcr.io.ml-pipeline.cache-server:1.7.0
docker tag hisunyh/gcr.io.ml-pipeline.cache-server:1.7.0 deep-arena-store:5000/ml-pipeline/cache-server:1.7.0

docker pull hisunyh/gcr.io.ml-pipeline.visualization-server:1.7.0
docker tag hisunyh/gcr.io.ml-pipeline.visualization-server:1.7.0 deep-arena-store:5000/ml-pipeline/visualization-server:1.7.0

docker pull hisunyh/gcr.io.ml-pipeline.persistenceagent:1.7.0
docker tag hisunyh/gcr.io.ml-pipeline.persistenceagent:1.7.0 deep-arena-store:5000/ml-pipeline/persistenceagent:1.7.0

docker pull hisunyh/gcr.io.ml-pipeline.viewer-crd-controller:1.7.0
docker tag hisunyh/gcr.io.ml-pipeline.viewer-crd-controller:1.7.0 deep-arena-store:5000/ml-pipeline/viewer-crd-controller:1.7.0

docker pull hisunyh/gcr.io.ml-pipeline.scheduledworkflow:1.7.0
docker tag hisunyh/gcr.io.ml-pipeline.scheduledworkflow:1.7.0 deep-arena-store:5000/ml-pipeline/scheduledworkflow:1.7.0

docker pull hisunyh/gcr.io.ml-pipeline.workflow-controller:v3.1.6-patch-license-compliance
docker tag hisunyh/gcr.io.ml-pipeline.workflow-controller:v3.1.6-patch-license-compliance deep-arena-store:5000/ml-pipeline/workflow-controller:v3.1.6-patch-license-compliance

docker pull hisunyh/gcr.io.ml-pipeline.api-server:1.7.0
docker tag hisunyh/gcr.io.ml-pipeline.api-server:1.7.0 deep-arena-store:5000/ml-pipeline/api-server:1.7.0

docker pull hisunyh/gcr.io.ml-pipeline.mysql:5.7
docker tag hisunyh/gcr.io.ml-pipeline.mysql:5.7 deep-arena-store:5000/ml-pipeline/mysql:5.7
```

```bash
docker push deep-arena-store:5000/ml-pipeline/frontend:1.7.0
docker push deep-arena-store:5000/ml-pipeline/visualization-server:1.7.0
docker push deep-arena-store:5000/ml-pipeline/cache-deployer:1.7.0
docker push deep-arena-store:5000/ml-pipeline/cache-server:1.7.0
docker push deep-arena-store:5000/ml-pipeline/metadata-envoy:1.7.0
docker push deep-arena-store:5000/ml-pipeline/metadata-writer:1.7.0
docker push deep-arena-store:5000/ml-pipeline/minio:RELEASE.2019-08-14T20-37-41Z-license-compliance
docker push deep-arena-store:5000/ml-pipeline/api-server:1.7.0
docker push deep-arena-store:5000/ml-pipeline/persistenceagent:1.7.0
docker push deep-arena-store:5000/ml-pipeline/scheduledworkflow:1.7.0
docker push deep-arena-store:5000/ml-pipeline/viewer-crd-controller:1.7.0
docker push deep-arena-store:5000/ml-pipeline/mysql:5.7
docker push deep-arena-store:5000/ml-pipeline/workflow-controller:v3.1.6-patch-license-compliance
```

```bash
docker pull hisunyh/gcr.io.tfx-oss-public.ml_metadata_store_server:1.0.0
docker tag hisunyh/gcr.io.tfx-oss-public.ml_metadata_store_server:1.0.0 registry.harbor:5000/ml-pipeline/tfx-oss-public/ml_metadata_store_server:1.0.0
docker push registry.harbor:5000/ml-pipeline/tfx-oss-public/ml_metadata_store_server:1.0.0
```