# Azure DevOps Hands-on

## 환경

* Azure Kubernetes Service(incl. Container Registry)
* Azure DevOps
* Azure KeyVault
* Azure PostgreSQL
* Spring Boot 프로젝트
* SonarQube
* GitHub Action or Azure Pipeline for CI/CD Pipeline
  * Azure Pipeline은 Code 방식 사용 (Classic X)
* Code Repository (GitHub or Azure Git Repo)

## 구성 시나리오 요약

1. Azure DevOps 보드 생성
2. DevOps Starter로 원클릭 구성
   * 한번에 K8S, Repo, Pipeline, 샘플 PJT, 모니터링 등 기본환경 구성
3. CI파이프라인 강화
    * SonarQube로 테스트 결과, 정점점검 결과 수집
4. CD파이프라인 강화
   * 개발계, 테스트계, 운영계 파아프라인 구성
   * 단계 별 승인과정 추가

## Azure DevOps 조직 구성

1. `https://dev.azure.com/` 로그인
2. `New Organization` 으로 새 조직 생성
    * Region은 `East asia` 선택
3. 프로젝트 생성
    * Version control은 `Git` 
4. (옵션) GitHub 리파지토리 연결 필요 시 
    * 생성된 프로젝트의 Project settings - GitHub Connections에서 GitHub 계정 연결
    * 리파티토리 선택 (복수개 선택 가능)

## Azure Board 구성

1. Delivery Plan 생성
2. 사용자스토리 워크샵 실시 - 백로그 생성 
3. 스프린트 플래닝
    * 이터레이션 생성
    * 백로그 (사용자스토리) 스프린트 할당
4. 스프린트 착수
    * 스토리 포인트 산정
    * 코드 링킹 

## Step by Step - DevOps Starter with Azure DevOps

> 참고문서: https://docs.microsoft.com/ko-kr/azure/devops-project/overview

1. DevOps Starter에서 `create`로 신규 프로젝트를 생성
    * 랭귀지 선택 전 아래 그림과 같이 나오는 `here`링크를 통해 `Azure DevOps`와 `GitHub Action`중 하나를 선택할 수 있음. 
    <img title="선택지" alt="선택지 " src="img/img1.png">

    > GitHub Action vs Azure DevOps?
    > <https://docs.microsoft.com/ko-kr/dotnet/architecture/devops-for-aspnet-developers/actions-vs-pipelines>

    * `Azure DevOps`선택
    * Language: `JAVA`, Framework: `Spring`, Service: `Kubernetes Service` 선택
    * Project name, Azure DevOps 조직, Kubernetes 신규 생성, 로케이션 Korea Central로 선택하여 생성.

2. Git 설정
    * 샘플 어플리케이션 Clone

    ```bash
        git clone https://github.com/HakjunMIN/azure-petclinic.git
    ```

    * 기본 설정

    ```bash
    rm -rf .git
    git add . 
    git commit -am "first commit"
    git remote add origin <신규생성 repo>
    git pull 
    git push
    ```

    [<img title="배포" src="img/deploy-to-azure.png">](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fopenhackpublic.blob.core.windows.net%2Flob-migration%2Fsept-2021%2FSmartHotelFull.json
)
