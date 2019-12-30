[Study kubernetes with Google Cloud Platform](https://cloud.google.com/sdk/downloads)

0. GCP에 프로젝트와 Cluster 생성
  - cloud.google.com 접속
  - project 생성 > Clouster 생성

1. install gcloud SDK
```
$ curl https://sdk.cloud.google.com | bash
```

2. gcp login
```
$ gcloud auth login
```
  - Google 계정 로그인

3. connect project
```
$ gcloud config set project <Project ID>
```
