---
title: 在 Linux 或 Windows Nano Server 主機上部署單一容器 .NET Core Web 應用程式
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 在 Linux 或 Windows Nano Server 主機上部署單一容器 .NET Core Web 應用程式
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: f429bc0c6e76c2be2e4f491768a15ab36ecb0d34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="deploying-single-container-based-net-core-web-applications-on-linux-or-windows-nano-server-hosts"></a>在 Linux 或 Windows Nano Server 主機上部署單一容器 .NET Core Web 應用程式

您可以使用 Docker 容器進行更簡單 Web 應用程式的整合型部署。如此可改善持續整合與持續部署管線，並協助完成部署到生產的過程。不再有「它在我的電腦中可行，為何在生產環境中不可行」的疑問。

微服務架構有許多好處，但這些好處的代價是複雜度會增加。 在某些情況下，這些代價會遠大於所獲得的好處，因此您最好在單一容器或幾個容器中執行整合型部署應用程式。 

整合型應用程式可能不容易分解成多個適當分離的微服務。 您已了解這應該透過函式來分割：微服務應該彼此獨立運作，才能提供復原能力更高的應用程式。 如果您無法切割應用程式的功能，將它分離只會增加複雜度。

應用程式可能還不需要獨立擴充功能。 假設在 eShopOnContainers 參考應用程式生命週期初期，流量並不需要將功能分成不同的微服務。 流量很小，因此將資源新增至一個服務通常相當於將資源新增至所有服務。 執行額外工作以將應用程式分成不同服務的好處有限。

此外，在開發應用程式初期，您可能不清楚自然功能邊界止於何處。 當您開發最低可行性產品 (Minimum Viable Product) 時，自然分離的情況可能尚不明顯。

有些情況可能是暫時性的。 您可以先建立一個整合型應用程式，稍後再將某些功能分成微服務來開發和部署。 其他情況可能對應用程式的問題空間很重要，這表示應用程式可能永遠不會分成多個微服務。

將應用程式分成許多不同的處理序也會引進額外負荷。 將功能分成不同處理序的複雜度更高。 通訊協定變得更複雜。 您必須在服務之間使用非同步通訊，而不是方法呼叫。 當您移至微服務架構時，您需要新增在 eShopOnContainers 應用程式的微服務版本中實作的許多建置組塊：事件匯流排處理、訊息復原與重試、最終一致性等等。

eShopOnContainers 的大幅簡化版本 (名為 [eShopWeb](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebMonolithic) 並包含在相同的 GitHub 存放庫中) 會以整合型 MVC 應用程式執行，且如剛才所述，該設計選擇提供一些優點。 您可以從 GitHub 下載此應用程式的來源並在本機執行。 即使是此整合型應用程式也可以透過部署至容器環境獲利。

其中一個優點是，容器化部署表示每個應用程式執行個體都會在相同的環境中執行。 這包括進行早期測試和開發的開發人員環境。 開發小組可以在與生產環境相符的容器化環境中執行應用程式。

此外，擴充容器化應用程式的成本較低。 如稍早所見，容器環境可共用的資源比傳統 VM 環境更多。

最後，容器化應用程式會強制分離商務邏輯與存放區伺服器。 當應用程式擴充時，多個容器全部都會依賴單一實體儲存媒體。 這通常是執行 SQL Server 資料庫的高可用性伺服器。

## <a name="application-tour"></a>應用程式導覽

[eShopWeb](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebMonolithic) 應用程式，代表當作整合型應用程式執行的部分 eShopOnContainers 應用程式，也就是在 .NET Core 上執行的 ASP.NET Core MVC 應用程式。 它主要提供稍早章節中所述的目錄瀏覽功能。

該應用程式使用 SQL Server 資料庫來存放目錄。 在容器部署中，此整合型應用程式可以存取與微服務應用程式相同的資料存放區。 該應用程式會在整合型應用程式所在的容器中執行 SQL Server。 在生產環境中，SQL Server 會在 Docker 主機外部的高可用性電腦上執行。 為了開發或測試環境方便起見，建議在專屬的容器中執行 SQL Server。

初始功能集只會啟用目錄瀏覽。 更新後即會啟用容器化應用程式的完整功能集。 如需更進階整合型 Web 應用程式架構的描述，請參閱 [ASP.NET Web 應用程式架構實務](https://aka.ms/webappebook)電子書和相關 [eShopOnWeb 範例應用程式](http://aka.ms/WebAppArchitecture)。不過在此情況下，它不會在 Docker 容器上執行，因為該情節主要是 ASP.NET Core 的一般網頁程式開發。

不過，eShopOnContainers (eShopWeb) 中可用的簡化版本會在 Docker 容器中執行。

## <a name="docker-support"></a>Docker 支援

eShopOnWeb 專案是在 .NET Core 上執行。 因此，它可以在 Linux 或 Windows 容器中執行。 請注意，若是 Docker 部署，您想要針對 SQL Server 使用相同的主機類型。 Linux 容器允許較小的使用量，而且是偏好選項。

Visual Studio 提供專案範本，以將 Docker 支援新增至方案。 以滑鼠右鍵按一下專案，然後依序按一下 [新增] 和 [Docker 支援]。 此範本會將 Dockerfile 新增至您的專案，以及提供起始 docker-compose.yml 檔案的新 **docker-compose** 專案。 此步驟在從 GitHub 下載的 eShopOnWeb 專案中已完成。 您將會看到此方案包含 **eShopOnWeb** 專案和 **docker-compose** 專案，如圖 6-1 中所示。

![](./media/image1.png)

**圖 6-1**. 單一容器 Web 應用程式中的 **docker-compose** 專案

這些檔案是標準 docker-compose 檔案，與任何 Docker 專案一致。 您可以透過 Visual Studio 或從命令列使用這些檔案。 此應用程式是在 .NET Core 上執行並使用 Linux 容器，因此您也可以在 Mac 或 Linux 電腦上撰寫、建置及執行程式碼。

docker-compose.yml 檔案包含要建置哪些映像及要啟動哪些容器的相關資訊。 這些範本會指定如何建置 eshopweb 映像及啟動應用程式的容器。 您需要在 SQL Server 上藉由加入其映像 (例如 mssql-server-linux) 來新增相依性，並新增 sql.data 映像的服務，Docker 才能建置及啟動該容器。 下列範例將顯示這些設定：

```yml
version: '2'

services:
  eshopweb:
    image: eshop/web
    build:
    context: ./eShopWeb
    dockerfile: Dockerfile
    depends_on:
      - sql.data

  sql.data:
    image: microsoft/mssql-server-linux
```

depends\_on 指示詞會告訴 Docker eShopWeb 映像相依於 sql.data 映像。 下列程式碼行是使用 microsoft/mssql-server-linux 映像建置映像標記之 sql.data 的指示。

**docker-compose** 專案會在主要 docker-compose.yml 節點下顯示其他 docker-compose 檔案，以提供與這些檔案相關的視覺化提示。 docker-compose-override.yml 檔案包含這兩項服務的設定，例如連接字串和其他應用程式設定。

下列範例會顯示 docker-compose.vs.debug.yml 檔案，其中包含用來在 Visual Studio 中偵錯的設定。 在該檔案中，eshopweb 映像前面會加上 dev 標記。 這有助於將偵錯與發行映像分開，因此您不會意外地將偵錯資訊部署至生產環境：

```yml
version: '2'
  
services:
  eshopweb:
    image: eshop/web:dev
    build:
    args:
    source: ${DOCKER_BUILD_SOURCE}
    environment:
      - DOTNET_USE_POLLING_FILE_WATCHER=1
    volumes:
      - ./eShopWeb:/app
      - ~/.nuget/packages:/root/.nuget/packages:ro
      - ~/clrdbg:/clrdbg:ro
    entrypoint: tail -f /dev/null
    labels:
      - "com.microsoft.visualstudio.targetoperatingsystem=linux"
```

最後一個新增的檔案是 docker-compose.ci.build.yml。 您可以從命令列使用此檔案，以從 CI 伺服器建置專案。 此 Compose 檔案會啟動 Docker 容器，以建置應用程式所需的映像。 下列範例顯示 docker-compose.ci.build.yml 檔案的內容。

```yml
version: '2'
  
services:
  ci-build:
    image: microsoft/aspnetcore-build:latest
    volumes:
      - .:/src
    working_dir: /src
  command: /bin/bash -c "dotnet restore ./eShopWeb.sln && dotnet publish  ./eShopWeb.sln -c Release -o ./obj/Docker/publish"
```

**注意**：從 .NET Core 2.0 開始，執行 dotnet publish 時會自動執行 dotnet restore 命令。

請注意，此映像是 ASP.NET Core 組建映像。 該映像包含 SDK 和建置工具，可建置您的應用程式並建立所需的映像。 使用此檔案執行 **docker-compose** 專案會從映像啟動組建容器，然後在該容器中建置應用程式的映像。 您可以將 docker-compose 檔案指定為命令列的一部分，在 Docker 容器中建置您的應用程式，然後將它啟動。

在 Visual Studio 中，您可以選取 **docker-compose** 專案作為啟始專案，然後按 Ctrl+F5 (F5 以偵錯)，以便在 Docker 容器中執行您的應用程式，就像是任何其他應用程式一樣。 當您啟動 **docker-compose** 專案時，Visual Studio 會使用 docker-compose.yml 檔案、docker-compose.override.yml 檔案及其中一個 docker-compose.vs.\* 檔案來執行 **docker-compose**。 一旦啟動應用程式，Visual Studio 會為您啟動瀏覽器。

如果您在偵錯工具中啟動應用程式，Visual Studio 將會附加至 Docker 中執行的應用程式。

## <a name="troubleshooting"></a>疑難排解

本節描述當您在本機執行容器時可能發生的一些問題，並建議一些修正。

### <a name="stopping-docker-containers"></a>停止 Docker 容器 

啟動容器化應用程式之後，容器會繼續執行，即使在停止偵錯之後亦然。 您可以從命令列執行 docker ps 命令，以查看哪些容器正在執行。 docker stop 命令會停止執行中的容器，如圖 6-2 所示。

![](./media/image2.png)

**圖 6-2**. 使用 docker ps 和 docker stop CLI 命令來列出及停止容器

當您在不同的設定之間切換時，您可能需要停止執行中的處理序。 否則，執行 Web 應用程式的容器會使用適用於您應用程式的連接埠 (在此範例中為 5106)。

### <a name="adding-docker-to-your-projects"></a>將 Docker 新增至您的專案

新增 Docker 支援的精靈會與執行中的 Docker 處理序通訊。 如果當您啟動精靈時，Docker 不在執行中，精靈將無法正確執行。 此外，精靈會檢查您目前的容器選擇，以新增正確的 Docker 支援。 如果您想要新增 Windows 容器的支援，您需要在有執行中 Docker 並已設定 Windows 容器的同時執行精靈。 如果您想要新增 Linux 容器的支援，請在有執行中 Docker 並已設定 Linux 容器的同時執行精靈。

>[!div class="step-by-step"]
[上一個] (../docker-application-development-process/docker-app-development-workflow.md) [下一個] (../containerize-net-framework-applications/index.md)
