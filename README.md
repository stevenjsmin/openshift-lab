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














