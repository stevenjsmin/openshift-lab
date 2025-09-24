This is the Labs repository for the Practical OpenShift for Developers course. 


oc new-app quay.io/practicalopenshift/hello-world --as-deployment-config
oc new-app quay.io/practicalopenshift/hello-world --name demo-app --as-deployment-config

oc new-app https://github.com/stevenjsmin/openshift-lab2.git --name demo-app --as-deployment-config

oc new-app trialqdcy13.jfrog.io/stevenlab-docker-local/hello:0.1 --as-deployment-config 

oc delete all -l app=hello-world

# BuildConfig 이름이 demo-app 인 빌드(Build) 작업의 로그를 실시간으로 따라가면서(follow) 출력하라는 뜻입니다.
#   -f는 follow 옵션. 로그를 tail 모드로 계속 이어서 표시 (리눅스 tail -f와 동일)
oc logs -f bc/demo-app

oc describe dc/demo-app
oc logs dc/demo-app

oc get dc/demo-app -o yaml

kubectl get replicationcontrollers  
oc get replicationcontrollers
oc get rc


oc rollout latest dc/demo-app

oc explain svc

oc explain service.spec

# 내부 Pod/Service를 클러스터 내부뿐 아니라 다른 리소스나 외부에서 접근할 수 있게 “공개”하는 작업을 합니다.
oc expose pod/hello-world-pod
   --> error: couldn't find port via --port flag or introspection

oc expose --port 8080 pod/hello-world-pod

# 이 서비스에서 제공되는 IP는 K8s 클러스터 내에서 제공되는 IP이므로 테스트를 위해서는 동일한 클러스터내의 다른 Pod에서 접근해야만 아래 테스트를 진행할수있다.
wget -qO- 172.30.37.211:808

# 아래는 K8s내부 클러스터IP에서 서비스되고있는 service/hello-world-pod를 K8s 외부에서 접근이 가능하도록 노출해주는 명령이다. 즉 Rout를 생성해준다.
# 즉, 외부에서 서비스로 접근할수 있도록 DNS를 설정해준다.
oc expose service/hello-world-pod

















