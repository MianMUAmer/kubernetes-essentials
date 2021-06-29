```bash
kubectl create ns bluegreen
kubectl apply -f app-v1.yaml
kubectl run --restart=Never --image=raesene/alpine-nettools nettools
kubectl exec -it nettools -- /bin/sh
while true; do curl http://my-app.bluegreen; done

kubectl apply -f app-v2.yaml
kubectl get pods -n bluegreen

kubectl delete ns bluegreen
kubectl delete pod nettools

```
