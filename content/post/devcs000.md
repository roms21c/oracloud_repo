+++
date = "2018-08-03T13:58:54+09:00"
description = "2018년 Developer Cloud Service 신기능 소개 입니다."
title = "Oracle Developer Cloud - 신기능 자세히 알아보기"
thumbnailInList = "https://oracloud-kr-teamrepo.github.io/2018/05/devcs/dev01.png"
thumbnailInPost = "https://oracloud-kr-teamrepo.github.io/2018/05/devcs/dev02.png"
tags = ["ORACLE", "Oracle Cloud", "Developer Cloud", "CI", "CD", "devops", "오라클 클라우드"]
categories = ["Oracle-Cloud"]
author = "mee-nam.lee"
language = ""  

+++

Oracle Developer Cloud Service는 자동화된 CI/CD를 위한 빌드 파이프라인 관리를 제공하는 클라우드 서비스입니다. <br/>
이 문서에서는 [Oracle Developer Cloud](https://cloud.oracle.com/en_US/developer-service)의 2018년 4월과 5월 릴리즈에서 추가된 새로운 기능들에 대해서 설명하려고 합니다.

## 빌드 파이프라인 정의 및 가시화
 이 버전의 Developer Cloud Service에서는 구성된 빌드들을 조합하여 일련의 파이프라인을 구성하는 기능이 추가되었습니다. <br/>각 빌드 작업들은 작업의 연관성과 흐름을 가지며 연속적으로 수행되도록 구성될 수 있습니다.
 일련의 빌드 작업의 수행에서 선행 빌드 작업의 성공 여부에 따라 후행 작업의 시작 유무를 조건에 다라 결정 지을 수도 있습니다.
 
- 그림 1. 빌드 파이프라인 
 ![](https://oracloud-kr-teamrepo.github.io/2018/05/devcs/dev03_pipeline.jpg)
 
- [빌드 파이프라인에 대해 더 알아보기](https://docs.oracle.com/en/cloud/paas/developer-cloud/csdcs/managing-project-jobs-and-builds-oracle-developer-cloud-service.html#GUID-8A6787EF-2D7E-4322-A7C9-00509920FC1C)

## 새로운 Build Executor
기존에 제공되던 빌더 이외에 신규 릴리즈에서 Docker, Kubernetes, Terraform 등의 빌더가 추가되었습니다. 이런 기능들을 통해서 단순히 애플리케이션 소스만을 빌드하는 것에 그치지 않고, 빌드된 애플리케이션이 포함된 컨테이너 이미지를 빌드하고 이를 Kubernetes Cluster로 배포하거나 Terraform을 이용해 다른 컴퓨트 환경으로 배포하거나 OCIcli를 통해 오라클 클라우드 환경으로 프로비저닝 하는 과정을 연결하는 빌드 파이프라인 구성이 용이하게 되었습니다.  

- 그림 2. 빌드 구성시 추가할 Executor 선택 메뉴
![](https://oracloud-kr-teamrepo.github.io/2018/05/devcs/build_executor.jpg)

- [Build Executor로 사용되는 소프트웨어 상세](https://docs.oracle.com/en/cloud/paas/developer-cloud/csdcs/managing-project-jobs-and-builds-oracle-developer-cloud-service.html#GUID-D03F85B7-EE9C-435F-BCE3-7F728222CFDF)

## 독립된 빌드 환경 - Compute VM
새롭게 릴리즈된 Developer Cloud Service는 이전 버전처럼 공유되는 환경을 사용한 서비스가 아닌, 별도의 독립된 클라우드 환경을 가진 인스턴스로 생성됩니다. 따라서 빌드 환경도 독립된 컴퓨트 VM을 사용하는 형식으로 변경되었습니다. <br/>
제공되는 소프트웨어 탬플릿들 중 원하는 소프트웨어들만 선택하여 맞춤형 빌드 환경을 구성할 수 있게 되었습니다. 이 빌드 VM은 빌드 구성에 따라 다른 VM을 사용할 수 있도록 여러개를 생성할 수 있으며, 빌드 시에만 구동되고 빌드가 완료되면 자동으로 정지됩니다.

- 그림 3. 빌드 VM 구성에 사용되는 소프트웨어 탬플릿 
 ![](https://oracloud-kr-teamrepo.github.io/2018/05/devcs/Software_template.jpg)

- 그림 4. 구성된 빌드 VM 정보와 상태 모니터링 
 ![](https://oracloud-kr-teamrepo.github.io/2018/05/devcs/BuildVM.jpg)

- [Build VM 구성에 대해 더 알아보기](https://docs.oracle.com/en/cloud/paas/developer-cloud/csdcs/organization-virtual-machines-page.html#GUID-0B9A93E2-7231-4E83-A893-2DC9C6FE1F42)

## Software Configuration
Developer Cloud Service에서 빌드 구성 시에 사용할 Build VM Template를 선택하게 되고, Build VM 구성된 소프트웨어들을 이용하여 빌드가 이루어지게 되는데, 이때 동일 소프트웨어의 여러 버전들이 해당 빌드 VM에 구성되어 있다면, 빌드 구성시 여러 버전 중에 어떤 버전을 사용할 것인지를 소프트웨어 구성에서 명시함으로써 정확한 버전의 소프트웨어를 사용하여 빌드가 이루어지게 할 수 있습니다.

- 그림 5. 가용한 소프트웨어 확인 및 버전 명시 
 ![](https://oracloud-kr-teamrepo.github.io/2018/05/devcs/software_config.jpg)

## 새로운 Agile Report
오라클 Developer Cloud Service을 이용하여 프로젝트 관리 기능의 수행이 가능한데, 이를 위해서 Agile Dashboard 라는 기능을 제공하고 있으며, Scrum Board와 Kanban Board가 포함되어 있습니다. 액티브 데시보드를 통한 작업 진행 상황과 진척율 모니터링 기능 외에 보고서 기능을 제공하고 있으며, 기존 제공하던 보고서들에 새로운 보고서 형태가 추가되었습니다. <br/>

- 그림 6. Agile Report 예시 
 ![](https://oracloud-kr-teamrepo.github.io/2018/05/devcs/agile_report.png)

- [Agile Report 및 Chart에 대해 더 알아보기](https://docs.oracle.com/en/cloud/paas/developer-cloud/csdcs/using-agile-methodology-oracle-developer-cloud-service.html#GUID-6A02C756-954D-4955-BB56-0FFF8277D847)


## 참고 자료
- [Oracle Developer Cloud - New Continuous Integration Engine Deep Dive](https://blogs.oracle.com/developers/oracle-developer-cloud-new-continuous-integration-engine-deep-dive)
- [Oracle Developer Cloud Service Adds Docker, Pipelines, and More](https://blogs.oracle.com/cloud-platform/oracle-developer-cloud-service-adds-docker,-pipelines,-and-more)