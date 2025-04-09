цель: обеспечить атомарность коммита / роллбека транзакций
могут быть грязные чтения
4 участника закоммитили, пятый не смог
однако вероятность грязных чтений намного меньше

![[Pasted image 20250220134957.png]]

labels:

app: ms-team

app.kubernetes.io/managed-by: Helm

app.kubernetes.io/name: ms-team

app.kubernetes.io/part-of: backend

app.kubernetes.io/version: stable

app.openshift.io/runtime: rh-openjdk

deploymentconfig: ms-team

helm.sh/chart: backend-1.0.0

annotations:

meta.helm.sh/release-name: ms-team

meta.helm.sh/release-namespace: spectr


labels:

app: ms-team-release

app.kubernetes.io/managed-by: Helm

app.kubernetes.io/name: ms-team

app.kubernetes.io/part-of: backend

app.kubernetes.io/version: stable

app.openshift.io/runtime: rh-openjdk

deploymentconfig: ms-team-release

helm.sh/chart: backend-1.0.0