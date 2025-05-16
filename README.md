repo with test with tactical-frontend
that is minimal code with lot of hardcodding. but for test it enought.

Requirements:
A working Dockerfile ✅
Kubernetes manifests for:
Deployment ✅
Service ✅
optional Ingress ✅
Proper use of ConfigMaps and Secrets ✅
(Optional) readiness/liveness probes ✅
Local setup instructions:
1. setup any k8s cluster and get config:
   eks: https://github.com/terraform-aws-modules/terraform-aws-eks
   onprem: https://www.cherryservers.com/blog/install-kubernetes-on-ubuntu
   minikube https://minikube.sigs.k8s.io/docs/start/?arch=%2Fwindows%2Fx86-64%2Fstable%2F.exe+download
2. put credentials to github cicd envs:  
   secrets.DOCKERHUB_USERNAME
   secrets.DOCKERHUB_TOKEN
   secrets.KUBE_CONFIG_DATA
3. create ns tactical-frontend in k8s
4. you also need to setup infra for acces to cluster from internet:
   aws: eks-lb(tls)-route53
   opnrem: k8s-metalb(letsencrypt)-any dns
5. install by helm ongress-nginx, letsencrypt(obprem), metallb(onprem) and any of secret provider like external-secrets (i dont like use native k8s secrets)
6. put docker config to regcred.yaml
7. run pipeline, any push to pipeline will redeploy code to k8s

logging: prometeus-grafana-loki stack, service monitor yaml for autodiscovery.
hpa for autoscalling bu cpu

