---
title: 建置 ASP.NET Core 2.1 應用程式與 Linux 容器部署到 AKS/Kubernetes 叢集
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/25/2019
ms.openlocfilehash: c6d778d345466b1b852d06bc01ce40ccfdebf964
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2019
ms.locfileid: "57676651"
---
# <a name="build-aspnet-core-21-applications-deployed-as-linux-containers-into-an-akskubernetes-orchestrator"></a>建置 ASP.NET Core 2.1 應用程式與 Linux 容器部署至 AKS/Kubernetes orchestrator

Azure Kubernetes Service (AKS) 是簡化容器部署和管理的 Azure 的受管理的 Kubernetes 協調流程服務 」。

AKS 主要功能如下：

- Azure 託管的控制平面
- 自動化的升級
- 自我修復
- 使用者可設定調整
- 開發人員和叢集操作員更簡單的使用者經驗。

下列範例會探索建立的 ASP.NET Core 2.1 應用程式在 Linux 上執行，且開發完成時，會部署到 AKS 叢集在 Azure 中，使用 Visual Studio 2017。

## <a name="creating-the-aspnet-core-21-project-using-visual-studio-2017"></a>建立 ASP.NET Core 2.1 專案使用 Visual Studio 2017

ASP.NET Core 是由 Microsoft 與 GitHub 上的.NET 社群維護的一般用途開發平台。 它是跨平台，支援 Windows、 macOS 和 Linux，而且可以用於裝置、 雲端和內嵌 /iot 情節。

此範例會使用簡單的專案，因此您不需要任何額外的知識，來建立範例，根據 Visual Studio Web API 範本。 您只需要使用標準的範本，其中包含透過 REST API，使用 ASP.NET Core 2.1 技術執行小型專案的所有項目建立專案。

![在 Visual Studio 中，選取 ASP.NET Core Web 應用程式中加入新的 專案 視窗。](media/create-aspnet-core-application.png)

**圖 4-36**。 建立 ASP.NET Core 應用程式

若要建立範例專案在 Visual Studio 中，選取**檔案** > **新增** > **專案**，選取**Web**專案類型的左窗格中，後面接著**ASP.NET Core Web 應用程式**。

Visual Studio 會列出 web 專案範本。 我們的範例中，選取**API**建立 ASP.NET Web API 應用程式。

確認您已選取 ASP.NET Core 2.1 作為架構。 .NET core 2.1 包含 Visual Studio 2017 的最後一個版本中是自動安裝及設定和為您安裝 Visual Studio 2017 時。

![針對選取的 API 選項，選取 [ASP.NET Core Web 應用程式類型的 visual Studio] 對話方塊。](media/create-web-api-application.png)

**圖 4-37**。 選取 ASP.NET CORE 2.1 和 Web API 專案類型

如果您有任何舊版的.NET Core 時，您可以下載並安裝從 2.1 版<https://www.microsoft.com/net/download/core#/sdk>。

建立專案時，您可以新增 Docker 支援，或之後，因此您可以 「 docker 化 」 您的專案在任何時間。 若要在專案建立之後新增 Docker 支援，以滑鼠右鍵按一下方案總管 中的專案節點，然後選取**新增** > **Docker 支援**的操作功能表上。

![若要將 Docker 支援新增至現有的專案快顯功能表選項：以滑鼠右鍵按一下 （專案） > 新增 > Docker 支援。](media/add-docker-support-to-project.png)

**圖 4-38**。 將 Docker 支援新增至現有的專案

若要完成新增 Docker 支援，您可以選擇 Windows 或 Linux。 在此案例中，選取**Linux**，因為 AKS 不支援 Windows 容器 （如晚期 2018)。

![選項對話方塊以選取目標作業系統的 Dockerfile。](media/select-linux-docker-support.png)

**圖 4-39**。 選取 Linux 容器。

透過這些簡單的步驟，您會有 Linux 容器上執行的 ASP.NET Core 2.1 應用程式。

如您所見，Visual Studio 2017 與 Docker 之間的整合是完全導向的開發人員生產力。

現在，您可以執行您的應用程式**F5**鍵，或使用**播放** 按鈕。

執行專案之後, 您可以列出使用的映像`docker images`命令。 您應該會看到`mssampleapplication`我們使用 Visual Studio 2017 的專案自動部署所建立的映像。

```console
docker images
```

![主控台輸出 docker 映像的命令，從顯示的清單：存放庫、 標記、 映像識別碼、 建立 （日期） 和大小。](media/docker-images-command.png)

**圖 4-40**。 Docker 映像的檢視

## <a name="register-the-solution-in-the-azure-container-registry"></a>在 Azure 容器登錄中註冊方案

例如，任何 Docker 登錄，來上傳映像[Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/)或 Docker Hub，讓映像可以從登錄部署至 AKS 叢集。 在此情況下，我們在影像上傳到 Azure Container Registry。

### <a name="create-the-image-in-release-mode"></a>在發行模式中建立映像

我們現在將建立中的映像**發行**變更為 （可用於生產環境） 的模式**版本**，如下圖 4-41，並執行應用程式，如同我們先前所示。

![工具列選項在 VS 中以發行模式建置。](media/select-release-mode.png)

**圖 4-41**。 選取 [發行] 模式

如果您執行`docker image`命令，您會看到這兩個建立的映像，一個用於`debug`和另一個則用於`release`模式。

### <a name="create-a-new-tag-for-the-image"></a>映像建立新標記

每個容器映像必須加上`loginServer`登錄的名稱。 此標記用於路由時將容器映像推送到映像登錄。

您可以檢視`loginServer`名稱從 Azure 入口網站中，從 Azure Container Registry 中取得資訊

![Azure 容器登錄名稱的瀏覽器檢視右上方。](media/loginServer-name.png)

**圖 4-42**。 登錄名稱的檢視

或藉由執行下列命令：

```console
az acr list --resource-group MSSampleResourceGroup --query "[].{acrLoginServer:loginServer}" --output table
```

![上述命令輸出的主控台。](media/az-cli-loginServer-name.png)

**圖 4-43**。 取得使用 PowerShell 的登錄名稱

在這兩種情況下，您會取得名稱。 在我們的範例， `mssampleacr.azurecr.io`。

現在您可以標記映像，採用最新的映像 （版本映像），使用命令：

```console
docker tag mssampleaksapplication:latest mssampleacr.azurecr.io/mssampleaksapplication:v1
```

執行後`docker tag`命令，列出與映像`docker images`命令，然後您應該會看到具有新標記的映像。

![從 docker images 命令輸出的主控台。](media/tagged-docker-images-list.png)

**圖 4-44**。 已加上標記的映像的檢視

### <a name="push-the-image-into-the-azure-acr"></a>將映像推送到 Azure ACR

將映像推送到 Azure 的 ACR，使用下列命令：

```console
docker push mssampleacr.azurecr.io/mssampleaksapplication:v1
```

此命令需要一些時間上傳影像，但可讓您在程序的意見反應。

![主控台從 docker push 命令的輸出： 顯示每個圖層的字元為基礎的進度列。](media/uploading-image-to-acr.png)

**圖 4-45**。 映像上傳至 ACR

您可以看到下列結果的程序完成時，您應該取得：

![主控台輸出 docker push 命令，完成之後，顯示所有的圖層或節點。](media/uploading-docker-images-complete.png)

**圖 4-46**。 節點檢視

下一個步驟是將您的容器部署到 AKS 的 Kubernetes 叢集。 為此，您需要的檔案 (**.yml 檔案部署**) 包含下列：

```yml
apiVersion: apps/v1beta1
kind: Deployment
metadata:
  name: mssamplesbook
spec:
  replicas: 1
  template:
    metadata:
      labels:
        app: mssample-kub-app
    spec:
      containers:
        - mane: mssample-services-app
          image: mssampleacr.azurecr.io/mssampleaksapplication:v1
          ports:
            - containerPort: 80
---
apiVersion: v1
kind: Service
metadata:
    name: mssample-kub-app
spec:
  ports:
    - name: http-port
      port: 80
      targetPort: 80
  selector:
    app: mssample-kub-app
  type: LoadBalancer
```

> [!NOTE]
> 如需使用 Kubernetes 的部署詳細資訊，請參閱： <https://kubernetes.io/docs/reference/kubectl/cheatsheet/>

現在，您可以幾乎準備好要部署使用**Kubectl**，但首先您必須取得 AKS 叢集使用此命令的認證：

```console
az aks get-credentials --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

![上述命令輸出的主控台：合併"MSSampleK8Cluster 做為目前的內容中 /root/.kube/config](media/getting-aks-credentials.png)

**圖 4-47**。 取得認證

然後，使用`kubectl create`命令，以啟動部署。

```console
kubectl create -f mssample-deploy.yml
```

![主控台上述命令的輸出： 部署 「 mssamplesbook 」 建立。 「 mssample kub-應用程式 」 建立的服務。](media/kubectl-create-command.png)

**圖 4-48**。 部署至 Kubernetes

完成部署之後，您可以使用本機 proxy，您可以使用此命令暫時存取來存取 Kubernetes 主控台：

```console
az aks browse --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

存取的 url 和`http://127.0.0.1:8001`。

![瀏覽器檢視 Kubernetes 儀表板，顯示部署、 Pod，複本集和服務。](media/kubernetes-cluster-information.png)

**圖 4-49**。 檢視 Kubernetes 叢集資訊

現在您已在 Azure 上使用 Linux 容器和 AKS 的 Kubernetes 叢集中部署的應用程式。 您可以存取您的應用程式瀏覽至您的服務，您可以從 Azure 入口網站取得的公用 IP。

> [!NOTE]
> 您可以了解如何建立 AKS 叢集，此範例一節[**部署到 Azure Kubernetes Service (AKS)** ](deploy-azure-kubernetes-service.md)有關本指南。

>[!div class="step-by-step"]
>[上一頁](set-up-windows-containers-with-powershell.md)
>[下一頁](../docker-devops-workflow/index.md)
