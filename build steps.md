build steps
1. export DOCKER_BUILDKIT=1 && docker build --no-cache -t 373353083651.dkr.ecr.us-east-1.amazonaws.com/openemr --ssh default -f Dockerfile . && docker push 373353083651.dkr.ecr.us-east-1.amazonaws.com/openemr
2. docker push 373353083651.dkr.ecr.us-east-1.amazonaws.com/openemr
3. get the digest from the push ecr or docker
`latest: digest: sha256:7ea9880b4b2bcfe9c7c781be5f737d7b0af391bec5af330d6785bdf991db27c9 size: 3659`
4. change the digest in the helm repo here: https://github.com/BridgeCr/bridge-infrastructure/tree/develop/kubernetes/openemr
5. helm upgrade --install demo-openemr --namespace demo-emr --set 'ingress.enabled=True' --set 'ingress.hosts[0]=openemr.bcrdemo.us'  .


1. we are only running one version of openemr in demo
2. we were running it in dev but i didn't want to risk data issues with two services and one db
