---
title: 將部署為 Linux 容器 ASP.NET Core 應用程式組建到 AKS/Kubernetes 叢集
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
ms.date: 08/06/2020
ms.openlocfilehash: 4b04e5d56c73918c665ad6e2825205870aac9606
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916301"
---
# <a name="build-aspnet-core-applications-deployed-as-linux-containers-into-an-akskubernetes-orchestrator"></a>將部署為 Linux 容器 ASP.NET Core 應用程式組建到 AKS/Kubernetes orchestrator

Azure Kubernetes Service (AKS) 是 Azure 的受控 Kubernetes 協調流程服務，可簡化容器部署和管理。

AKS 的主要功能包括：

- Azure 裝載的控制平面
- 自動升級
- 自我修復
- 使用者可設定的調整
- 為開發人員和叢集操作員提供更簡單的使用者體驗。

下列範例會探索如何建立在 Linux 上執行的 ASP.NET Core 3.1 應用程式，並部署至 Azure 中的 AKS 叢集，而使用 Visual Studio 2019 進行開發。

## <a name="creating-the-aspnet-core-project-using-visual-studio-2019"></a>使用 Visual Studio 2019 建立 ASP.NET Core 專案

ASP.NET Core 是一般用途的開發平台，由 Microsoft 和 GitHub 上的 .NET 社群共同維護。 它可以跨平台支援 Windows、macOS 及 Linux，並可用於裝置、雲端和內嵌式系統/IoT 等應用情節。

這個範例會使用以 Visual Studio 範本為基礎的幾個簡單專案，因此您不需要額外的知識來建立範例。 您只需要使用包含所有元素的標準範本來建立專案，即可使用 REST API 和使用 Razor 頁面的 Web 應用程式來執行小型專案，並使用 ASP.NET Core 3.1 技術。

![在 Visual Studio 中新增專案視窗，並選取 ASP.NET Core Web 應用程式。](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/create-aspnet-core-application.png)

**圖 4-35**. 在 Visual Studio 2019 中建立 ASP.NET Core Web 應用程式。

若要在 Visual Studio 中建立範例專案，**請選取**  >  [檔案] [**新增**  >  **專案**]，選取 [ **web** ] 專案類型，然後選取 [ **ASP.NET Core web 應用程式**] 範本。 您也可以在需要時搜尋範本。

然後輸入 [應用程式名稱] 和 [位置]，如下圖所示。

![輸入專案名稱和位置。](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/enter-project-name-and-location.png)

**圖 4-36**. 輸入 Visual Studio 2019 中的專案名稱和位置。

確認您已選取 ASP.NET Core 3.1 做為架構。 .NET Core 3.1 隨附于最新版的 Visual Studio 2019，當您安裝 Visual Studio 時，系統會自動為您安裝並設定此版本。

![用於選取 ASP.NET Core Web 應用程式類型並已選取 API 選項的 Visual Studio 對話方塊。](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/create-web-api-application.png)

**圖 4-37**. 選取 ASP.NET CORE 3.1 和 Web API 專案類型

請注意，目前未啟用 Docker 支援，只是為了顯示它可以在專案建立之後完成。

如果您有任何舊版的 .NET Core，您可以從下載並安裝3.1 版 <https://dotnet.microsoft.com/download> 。

若要顯示您可以隨時「Docker 化」您的專案，請立即新增 Docker 支援。 因此，以滑鼠右鍵按一下方案總管中的專案節點， **Add**然後選取  >  內容功能表上的 [新增**Docker 支援**]。

![將 Docker 支援新增至現有專案的內容功能表選項：以滑鼠右鍵按一下專案) 上的 [ (] > 新增 > Docker 支援]。](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/add-docker-support-to-project.png)

**圖 4-38**. 將 Docker 支援新增至現有的專案

若要完成新增 Docker 支援，您可以選擇 [Windows] 或 [Linux]。 在此情況下，請選取 [ **Linux**]。

![用於選取 Dockerfile 目標 OS 的選項對話方塊。](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/select-linux-docker-support.png)

**圖 4-39**. 選取 Linux 容器。

有了這些簡單的步驟，您就可以在 Linux 容器上執行 ASP.NET Core 3.1 應用程式。

同樣地，您也可以將非常簡單的**WebApp**專案加入 (圖 4-40) 以取用 Web API 端點，不過這裡不會討論詳細資料。

之後，您可以為**WebApi**專案新增協調器支援，如下圖4-40 所示。

![將協調器支援新增至 WebApi 專案](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/add-orchestrator-support.png)

**圖 4-40**. 將協調器支援新增至*WebApi*專案。

當您選擇 `Docker Compose` 適用于本機開發的選項時，Visual Studio 會新增 docker 撰寫專案，並以 docker 撰寫檔案的形式顯示，如映射4-41 所示。

![Docker 撰寫已新增至解決方案](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/docker-compose-project-in-visual-studio.png)

**圖 4-41**. 將協調器支援新增至*WebApi*專案。

新增的初始檔案如下所示：

`docker-compose.yml`

```yml
version: "3.4"

services:
  webapi:
    image: ${DOCKER_REGISTRY-}webapi
    build:
      context: .
      dockerfile: WebApi/Dockerfile

  webapp:
    image: ${DOCKER_REGISTRY-}webapp
    build:
      context: .
      dockerfile: WebApp/Dockerfile
```

`docker-compose.override.yml`

```yml
version: "3.4"

services:
  webapi:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=https://+:443;http://+:80
    ports:
      - "80"
      - "443"
    volumes:
      - ${APPDATA}/Microsoft/UserSecrets:/root/.microsoft/usersecrets:ro
      - ${APPDATA}/ASP.NET/Https:/root/.aspnet/https:ro
  webapp:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=https://+:443;http://+:80
    ports:
      - "80"
      - "443"
    volumes:
      - ${APPDATA}/Microsoft/UserSecrets:/root/.microsoft/usersecrets:ro
      - ${APPDATA}/ASP.NET/Https:/root/.aspnet/https:ro
```

若要讓應用程式以 Docker Compose 執行，您只需要對`docker-compose.override.yml`

```yml
services:
  webapi:
    #...
    ports:
      - "51080:80"
      - "51443:443"
    #...
  webapp:
    environment:
      #...
      - WebApiBaseAddress=http://webapi
    ports:
      - "50080:80"
      - "50443:443"
    #...
```

現在您可以使用**F5**鍵來執行應用程式，或使用 [**播放**] 按鈕，或按**Ctrl + F5**鍵，選取 [docker 撰寫] 專案，如影像4-42 所示。

![使用 Visual Studio 執行 docker 撰寫專案](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/running-docker-compose-with-visual-studio.png)

**圖 4-42**. 將協調器支援新增至*WebApi*專案。

如所述，執行 docker 撰寫應用程式時，您會得到：

1. 建立映射和根據 docker 撰寫檔案建立的容器。
2. 瀏覽器會在專案的 [屬性] 對話方塊中設定的位址中開啟 `docker-compose` 。
3. [**容器**] 視窗會在 Visual Studio 2019 16.4 版和更新版本的) 中開啟 (。
4. 方案中所有專案的偵錯工具支援，如下列影像所示。

瀏覽器已開啟：

![Web 應用程式正在執行的瀏覽器視圖](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/browser-opened.png)

**圖 4-43**. 具有在多個容器上執行之應用程式的瀏覽器視窗。

[容器] 視窗：

![Visual Studio [容器] 視窗](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/visual-studio-containers-window.png)

**圖 4-44**. Visual Studio [容器] 視窗

[**容器**] 視窗可讓您查看執行中的容器、流覽可用的映射、查看環境變數、記錄和埠對應、檢查檔案系統、附加偵錯工具，或在容器環境中開啟終端機視窗。

如您所見，Visual Studio 2019 與 Docker 之間的整合，完全是以開發人員的生產力為導向。

當然，您也可以使用命令來列出映射 `docker images` 。 您應該會看到 `webapi` 和 `webapp` 影像，其中包含 `dev` 自動部署具有 Visual Studio 2019 之專案的標記所建立的標籤。

```console
docker images
```

![來自 docker images 命令的主控台輸出會顯示包含下列清單：存放庫、標記、映射識別碼、建立 (日期) 和大小。](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/docker-images-command.png)

**圖 4-45**. Docker 映像檢視

## <a name="register-the-solution-in-an-azure-container-registry-acr"></a>在 Azure Container Registry (ACR 中註冊解決方案) 

您可以將映射上傳至[Azure Container Registry (ACR) ](https://azure.microsoft.com/services/container-registry/)，但您也可以使用 Docker Hub 或任何其他登錄，讓映射可以從該登錄部署到 AKS 叢集。

### <a name="create-an-acr-instance"></a>建立 ACR 實例

從**az cli**執行下列命令：

```powershell
az acr create --name exploredocker --resource-group explore-docker-aks-rg --sku basic --admin-enabled
```

### <a name="create-the-image-in-release-mode"></a>在 [發行] 模式中建立映像

您現在會藉由變更為 [**發行**]，在 [**發行**] 模式中建立映射 (準備好用於生產) ，如圖4-46 所示，然後像之前一樣執行應用程式。

![在 [發行] 模式中建置的 VS 工具列選項。](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/select-release-mode.png)

**圖 4-46**. 選取 [發行] 模式

如果您執行 `docker images` 命令，您會看到兩個映射建立，一個用於 `debug` (**dev**) ，另一個用於 `release` (**最新**的) 模式。

### <a name="create-a-new-tag-for-the-image"></a>為映像建立新的標記

每個容器映像都必須標記登錄的 `loginServer` 名稱。 將容器映像推送到映像登錄時，此標籤可用於路由傳送。

您可以從 Azure 入口網站檢視 `loginServer` 名稱，然後從 Azure Container Registry 擷取資訊

![Azure Container Registry 名稱的瀏覽器檢視，位於右上方。](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/loginServer-name.png)

**圖 4-47**. Registry 名稱檢視

或執行下列命令：

```console
az acr list --resource-group <resource-group-name> --query "[].{acrLoginServer:loginServer}" --output table
```

![上述命令的主控台輸出。](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/az-cli-loginServer-name.png)

**圖 4-48**. 使用**az cli**取得登錄的名稱

在這兩種情況下，您都會取得名稱。 在我們的範例中為 `exploredocker.azurecr.io`。

現在您可以使用命令來標記映像，然後擷取最新的映像 (發行映像)：

```console
docker tag <image-name>:latest <login-server-name>/<image-name>:v1
```

執行 `docker tag` 命令之後，請使用 `docker images` 命令列出映像，您應該會看到具有新標記的映像。

![docker images 命令的主控台輸出。](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/tagged-docker-images-list.png)

**圖 4-49**. 已標記的映像檢視

### <a name="push-the-image-into-the-azure-acr"></a>將映像推送到 Azure ACR

登入 Azure Container Registry

```console
az acr login --name exploredocker
```

使用下列命令將映像推送到 Azure ACR：

```console
docker push <login-server-name>/<image-name>:v1
```

此命令需要一些時間上傳映像，但會在程序中提供回饋給您。 在下圖中，您可以看到已完成的一個映射的輸出，另一個則是進行中。

![來自 docker push 命令的主控台輸出。](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/uploading-docker-images-complete.png)

**圖 4-50**。 推播命令的主控台輸出。

若要將多容器應用程式部署到 AKS 叢集中，您需要一些具有的資訊清單檔案 `.yaml` ，這些都是從和檔案取得的屬性 `docker-compose.yml` `docker-compose.override.yml` 。

#### `deploy-webapi.yml`

```yml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: webapi
  labels:
    app: weather-forecast
spec:
  replicas: 1
  selector:
    matchLabels:
      service: webapi
  template:
    metadata:
      labels:
        app: weather-forecast
        service: webapi
    spec:
      containers:
        - name: webapi
          image: exploredocker.azurecr.io/webapi:v1
          imagePullPolicy: IfNotPresent
          ports:
            - containerPort: 80
              protocol: TCP
          env:
            - name: ASPNETCORE_URLS
              value: http://+:80
---
apiVersion: v1
kind: Service
metadata:
  name: webapi
  labels:
    app: weather-forecast
    service: webapi
spec:
  ports:
    - port: 80
      targetPort: 80
      protocol: TCP
  selector:
    service: webapi
```

#### `deploy-webapp.yml`

```yml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: webapp
  labels:
    app: weather-forecast
spec:
  replicas: 1
  selector:
    matchLabels:
      service: webapp
  template:
    metadata:
      labels:
        app: weather-forecast
        service: webapp
    spec:
      containers:
        - name: webapp
          image: exploredocker.azurecr.io/webapp:v1
          imagePullPolicy: IfNotPresent
          ports:
            - containerPort: 80
              protocol: TCP
          env:
            - name: ASPNETCORE_URLS
              value: http://+:80
            - name: WebApiBaseAddress
              value: http://webapi
---
apiVersion: v1
kind: Service
metadata:
  name: webapp
  labels:
    app: weather-forecast
    service: webapp
spec:
  type: LoadBalancer
  ports:
    - port: 80
      targetPort: 80
      protocol: TCP
  selector:
    service: webapp
```

> [!NOTE]
> 先前的檔案 `.yml` 只會 `HTTP` 使用參數來啟用埠， `ASPNETCORE_URLS` 以避免範例應用程式中遺失的憑證發生問題。

> [!TIP]
> 您可以在本指南的[**部署到 Azure Kubernetes Service (AKS)**](deploy-azure-kubernetes-service.md) 一節中，了解如何為此範例建立 AKS 叢集。

現在您已經準備好使用**kubectl**進行部署，但您必須先使用下列命令從 AKS 叢集取得認證：

```console
az aks get-credentials --resource-group explore-docker-aks-rg --name explore-docker-aks
```

![上述命令的主控台輸出：合併「探索-docker-aks」作為 C:\Users\Miguel.kube\config 中的目前內容](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/getting-aks-credentials.png)

**圖 4-51**。 將認證從 AKS 取得至 kubectl 環境。

您也必須允許 AKS 叢集使用下列命令，從 ACR 提取映射：

```console
az aks update --name explore-docker-aks --resource-group explore-docker-aks-rg --attach-acr exploredocker
```

上一個命令可能需要幾分鐘的時間才能完成。 然後，使用 `kubectl apply` 命令來啟動部署，然後 `kubectl get all` 取得叢集物件清單。

```console
kubectl apply -f deploy-webapi.yml
kubectl apply -f deploy-webapp.yml

kubectl get all
```

![上述命令的主控台輸出：已套用部署。 已建立服務。](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/kubectl-apply-command.png)

**圖 4-52**。 部署至 Kubernetes

您必須等候一段時間，直到負載平衡器取得外部 IP，檢查 `kubectl get services` ，然後應用程式應該可在該位址上使用，如下圖所示：

![已部署至 AKS 之應用程式的瀏覽器視圖](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/aks-deployed-application.png)

**圖 4-53**。 部署至 Kubernetes

當部署完成時，您可以使用 ssh 通道，透過本機 proxy 來存取[Kubernetes WEB UI](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/) 。

首先，您必須使用下列命令建立 ClusterRoleBinding：

```console
kubectl create clusterrolebinding kubernetes-dashboard --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard
```

然後，執行下列命令以啟動 proxy：

```console
az aks browse --resource-group exploredocker-aks-rg --name explore-docker-aks
```

瀏覽器視窗應該會在 `http://127.0.0.1:8001` 與下列類似的視圖中開啟：

![Kubernetes 儀表板的瀏覽器檢視，其中顯示 [部署]、[Pod]、[複本集] 和 [服務]。](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/kubernetes-cluster-information.png)

**圖 4-54**。 檢視 Kubernetes 叢集資訊

現在您已有 ASP.NET Core 應用程式，在 Linux 容器中執行，並已部署至 Azure 上的 AKS 叢集。

> [!NOTE]
> 如需使用 Kubernetes 部署的詳細資訊，請參閱：<https://kubernetes.io/docs/reference/kubectl/cheatsheet/>

> [!div class="step-by-step"]
> [上一個](set-up-windows-containers-with-powershell.md) 
> [下一步](../docker-devops-workflow/index.md)
