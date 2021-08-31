# Contour/Linkerd/Websockets/GRPC

## Running

Modify `ingress.yaml` with a dns-address and an issuer

```bash
kubectl apply -f namespace.yaml
kubectl apply -f configmap.yaml
kubectl apply -f envoy.yaml
kubectl apply -f ingress.yaml
kubectl apply -f websocket.yaml
kubectl apply -f yages.yaml
```

Test Websocket

```bash
npm install -g wscat
wscat --connect wss://<dns-address>/websocket
```

Test GRPC (using [grpcurl](https://github.com/fullstorydev/grpcurl))

```bash
grpcurl <dns-address>:443 list
```

Everything should work.

Modify `namespace.yaml` and uncomment out the linkerd annotation

```bash
kubectl apply -f namespace.yaml
kubectl rollout restart deployment
```
