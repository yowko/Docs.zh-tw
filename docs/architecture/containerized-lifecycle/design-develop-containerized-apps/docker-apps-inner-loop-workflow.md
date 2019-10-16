---
title: Docker 應用程式的內部迴圈開發工作流程
description: 了解用於開發 Docker 應用程式的「內部迴圈」工作流程。
ms.date: 02/15/2019
ms.openlocfilehash: 565852511f3a837066d5da5cf0e3ab0a902dd7da
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2019
ms.locfileid: "71956504"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a>Docker 應用程式的內部迴圈開發工作流程

在觸發跨越整個 DevOps 循環的外部迴圈工作流程之前，所有項目都從每個開發人員的機器開始，使用其慣用語言或平台對應用程式本身編碼，並在本機進行測試 (圖 4-21)。 但不論何種情況，不論您選擇何種語言、架構或平台，您都會有一個重要的共同點。 在此特定的工作流程中，您將一律開發並測試 Docker 容器，但僅在本機。

![此圖顯示內部迴圈開發環境的概念。](./media/docker-apps-inner-loop-workflow/inner-loop-development-context.png)

**圖 4-21**： 內部迴圈開發內容

Docker 映像的容器或執行個體將包含這些元件：

- 作業系統選取項目 (例如 Linux 發行版本或 Windows)

- 開發人員新增的檔案 (例如應用程式二進位檔)

- 組態 (例如環境設定和相依性)

- 由 Docker 執行哪些程序的指示

您可以設定利用 Docker 作為程序的內部迴圈開發工作流程 (在下一節中描述)。 請考慮不包含設定環境的初始步驟，因為您只需要進行一次。

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a>使用 Visual Studio Code 和 Docker CLI，在 Docker 容器中建置單一應用程式

應用程式是由您自己的服務加上額外程式庫 (相依性) 所組成。

圖 4-22 顯示建置 Docker 應用程式時通常需要執行的基本步驟，後接每個步驟的詳細說明。

![此圖顯示建立容器化應用程式所需的七個步驟。](./media/docker-apps-inner-loop-workflow/life-cycle-containerized-apps-docker-cli.png)

**圖 4-22**。 使用 Docker CLI 之 Docker 容器化應用程式的生命週期工作流程概要

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a>步驟 1:開始在 Visual Studio Code 中編碼，並建立您的初始應用程式/服務基準

開發 Docker 應用程式的方式，與不使用 Docker 開發應用程式的方式類似。 差別在於，在開發時，您要部署並測試放置於本機環境之 Docker 容器 (例如 Linux VM 或 Windows) 中正在執行的應用程式或服務。

**設定您的本機環境**

使用適用於 Mac 和 Windows 的最新版本 Docker，開發 Docker 應用程式比以往更加容易，且設定非常簡單。

> [!TIP]
> 如需設定適用於 Windows 之 Docker 的指示，請瀏覽 <https://docs.docker.com/docker-for-windows/>。
>
>如需設定適用於 Mac 之 Docker 的指示，請瀏覽 <https://docs.docker.com/docker-for-mac/>。

此外，您也需要程式碼編輯器，讓您可在使用 Docker CLI 時實際開發應用程式。

Microsoft 提供 Visual Studio Code，這是 Windows、Linux 和 macOS 上支援的輕量程式碼編輯器，並為 IntelliSense 提供[許多語言的支援](https://code.visualstudio.com/docs/languages/overview)（JavaScript、.Net、Go、JAVA、Ruby、Python 和最新式的語言）。[偵錯](https://code.visualstudio.com/Docs/editor/debugging)與 [使用 Git 的整合功能](https://code.visualstudio.com/Docs/editor/versioncontrol)及[延伸支援](https://code.visualstudio.com/docs/extensions/overview)。 此編輯器非常適合 macOS 和 Linux 開發人員。 在 Windows 中，您也可以使用 Visual Studio。

> [!TIP]
> 如需安裝 Windows、Linux 或 macOS Visual Studio Code 的指示，請移至 <https://code.visualstudio.com/docs/setup/setup-overview/>。
>
> 如需設定適用於 Mac 之 Docker 的指示，請瀏覽 <https://docs.docker.com/docker-for-mac/>。

您可以使用 Docker CLI 並使用任何程式碼編輯器撰寫您的程式碼，但使用包含 Docker 延伸模組的 Visual Studio Code 可以輕鬆撰寫工作區中的 `Dockerfile` 和 `docker-compose.yml` 檔案。 您也可以從 Visual Studio Code IDE 執行工作和指令碼，以使用下面的 Docker CLI 執行 Docker 命令。

適用於 VS Code 的 Docker 延伸模組提供下列功能：

- `Dockerfile` 和 `docker-compose.yml` 檔案的自動產生

- `docker-compose.yml` 和 `Dockerfile` 檔案的語法醒目提示及暫留提示

- `Dockerfile` 和 `docker-compose.yml` 檔案的 IntelliSense (完成)

- `Dockerfile` 檔案的 Linting (錯誤和警告)

- 最常見 Docker 命令的命令選擇區 (F1) 整合

- 用於管理映像和容器的總管整合

- 將映像從 DockerHub 和 Azure Container Registry 部署至 Azure App Service

若要安裝 Docker 延伸模組，請按 Ctrl+Shift+P、鍵入 `ext install`，然後執行安裝延伸模組的命令來顯示 Marketplace 延伸模組清單。 接下來，輸入 **docker** 以篩選結果，然後選取 Docker 支援延伸模組，如圖 4-23 所示。

![適用於 VS Code 的 Docker 延伸模組檢視。](./media/docker-apps-inner-loop-workflow/install-docker-extension-vs-code.png)

**圖 4-23**： 在 Visual Studio Code 中安裝 Docker 延伸模組

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a>步驟 2:建立與現有映像 (純文字 OS 或開發環境，例如 .NET Core、Node.js 和 Ruby) 相關的 DockerFile

針對每個要建置的自訂映像，以及每個要部署的容器，您都需要一個 `DockerFile`。 如果您的應用程式由單一自訂服務所組成，您將需要單一 `DockerFile`。 但如果您的應用程式由多個服務所組成 (如同在微服務架構中)，針對每項服務您將需要一個 `Dockerfile`。

`DockerFile` 通常放在應用程式或服務的根資料夾中，並包含必要的命令，以讓 Docker 知道如何設定並執行該應用程式或服務。 您可以建立您的 `DockerFile`，並將其與您的程式碼 (node.js、.NET Core 等) 一起新增至專案中；如果您還不熟悉環境，請查看下列提示。

> [!TIP]
> 您可以使用 Docker 延伸模組來引導您使用與 Docker 容器相關的 `Dockerfile` 和 `docker-compose.yml` 檔案。 最後，您可能會在沒有此工具的情況下撰寫這類檔案，但使用 Docker 延伸模組是不錯的起點，可加速您的學習曲線。

在圖 4-24 中，您可以看到如何使用適用於 VS Code 的 Docker 延伸模組來新增 docker-compose 檔案。

![適用於 VS Code 的 Docker 延伸模組主控台檢視。](./media/docker-apps-inner-loop-workflow/add-docker-files-to-workspace-command.png)

**圖 4-24**： 使用**將 Docker 檔案新增至工作區命令**新增的 Docker 檔案

新增 DockerFile 時，您將指定您要使用哪些基礎 Docker 映像 (例如使用 `FROM mcr.microsoft.com/dotnet/core/aspnet`)。 您通常會在基底映像之上建置自訂映像，該基底映像可從 [Docker Hub登錄](https://hub.docker.com/)的任何官方存放庫取得 (例如 [.NET Core 的映像](https://hub.docker.com/_/microsoft-dotnet-core/)或 [Node.js](https://hub.docker.com/_/node/) 的映像)。

***使用現有的官方 Docker 映像***

使用具有版本號碼的官方語言堆疊存放庫，可確保所有電腦上都能使用相同的語言功能 (包括開發、測試和生產環境)。

下列是 .NET Core 容器的範例 DockerFile：

```Dockerfile
# Base Docker image to use  
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2
  
# Set the Working Directory and files to be copied to the image  
ARG source  
WORKDIR /app  
COPY ${source:-bin/Release/PublishOutput} .  
  
# Configure the listening port to 80 (Internal/Secured port within Docker host)  
EXPOSE 80  
  
# Application entry point  
ENTRYPOINT ["dotnet", "MyCustomMicroservice.dll"]
```

在此案例中，映像是以 2.2 版的官方 ASP.NET Core Docker 映像為基礎 (適用於 Linux 和 Windows 的多架構)，依據此行 `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`。 (如需本主題的詳細資訊，請參閱 [ASP.NET Core Docker 映像](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/)頁面及 [.NET Core Docker 映像](https://hub.docker.com/_/microsoft-dotnet-core/)頁面)。

在 DockerFile 中，您也可以指示 Docker 接聽您將在執行階段使用的 TCP 連接埠 (例如連接埠 80)。

您可在 Dockerfile 中指定其他的組態設定，視您使用的語言和架構而定。 例如，`ENTRYPOINT` 行中有 `["dotnet", "MySingleContainerWebApp.dll"]` 會指示 Docker 執行 .NET Core 應用程式。 如果您使用 SDK 和 .NET Core CLI (`dotnet CLI`) 建置及執行 .NET 應用程式，此設定會有所不同。 此處的重點，是 ENTRYPOINT 行與其他設定會視您選擇的應用程式語言和平台而定。

> [!TIP]
> 如需如何建置 .NET Core 應用程式之 Docker 映像的詳細資訊，請瀏覽 <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>。
>
> 若要深入了解如何建置您自己的映像，請瀏覽 <https://docs.docker.com/engine/tutorials/dockerimages/>。

**使用多架構映像存放庫**

存放庫中的單一映像名稱可以包含多種平台變化，例如 Linux 映像和 Windows 映像。 這項功能可讓 Microsoft (基底映像建立者) 等廠商建立單一存放庫以涵蓋多個平台 (即 Linux 和 Windows)。 例如，Docker Hub 登錄提供的 [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) 存放庫，會使用相同的映像名稱提供 Linux 和 Windows Nano Server 支援。

從 Windows 主機提取 [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) 映像會提取 Windows 變化，而從 Linux 主機提取相同的映像名稱則會提取 Linux 變化。

***建立全新的基底映像***

您可以從頭建立您自己的 Docker 基底映像，如 Docker 的此[文章](https://docs.docker.com/engine/userguide/eng-image/baseimages/)中所述。 如果您是 Docker 新手，此方案可能不適合您，但如果您想要設定專屬基底映像的特點，您可以這樣做。

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a>步驟 3：建立自訂 Docker 映像並將服務嵌入其中

針對每個包含您應用程式的自訂服務，您需要建立相關映像。 如果您的應用程式組成為單一的服務或 Web 應用程式，則您只需要單一映像。

> [!NOTE]
> 考慮「外部迴圈 DevOps 工作流程」時，每當您將原始程式碼推送至 Git 存放庫 (持續整合)，映像會透過自動建置程序建立，因此映像將於原始程式碼的全域環境中建立。
>
> 但在我們考慮進入該外部迴圈路由之前，我們需要確保 Docker 應用程式實際上正常運作，使其不會將可能無法正常運作的程式碼推送至原始檔控制系統 (Git 等)。
>
> 因此，每位開發人員首先需要執行整個內部迴圈程序，以在本機進行測試並繼續開發，直到他們想要推送完整的功能或變更為原始檔控制系統。

若要在您的本機環境中使用 DockerFile 建立映像，您可以使用 docker build 命令，如圖 4-25 所示 (針對由多個容器/服務所組成的應用程式，您也可以執行 `docker-compose up --build`)。

![螢幕擷取畫面，顯示 docker build 命令的主控台輸出。](./media/docker-apps-inner-loop-workflow/run-docker-build-command.png)

**圖 4-25**： 執行 docker build

(選用) 不直接從專案資料夾執行 `docker build`，而是先使用 run `dotnet publish` 命令產生具有所需 .NET 程式庫的可部署資料夾，然後執行 `docker build`。

此範例使用名稱 `cesardl/netcore-webapi-microservice-docker:first` 來建立 Docker 映像 (`:first` 是標籤，例如特定版本)。 您可以透過數個容器，為組成 Docker 應用程式所需建立的每個自訂映像採用此步驟。

您可以使用 docker images 命令在本機存放庫 (您的部署機器) 中尋找現有的映像，如圖 4-26 所示。

![docker images 命令的主控台輸出，顯示現有的映像。](./media/docker-apps-inner-loop-workflow/view-existing-images-with-docker-images.png)

**圖 4-26**。 使用 docker images 檢視現有的映像

### <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a>步驟 4：建置具有多個服務的組成 Docker 應用程式時，在 docker-compose.yml 中定義您的服務

透過 `docker-compose.yml` 檔案，您可以定義一組相關服務，部署為具有部署命令 (將於下一節解釋) 的組成應用程式。

在主要或根方案資料夾中建立該檔案；其內容應與此 `docker-compose.yml` 檔案中顯示的內容類似：

```yml
version: '3.4'
services:
  web:
    build: .
    ports:
     - "81:80"
    volumes:
     - .:/code
    depends_on:
     - redis
  redis:
    image: redis
```

在此特殊案例中，此檔案定義兩個服務：Web 服務 (您的自訂服務) 和 redis 服務 (熱門的快取服務)。 每項服務都會部署為容器，因此我們需要為每個服務使用具體的 Docker 映像。 針對此特定的 Web 服務，映像必須執行下列作業：

- 從目前目錄中的 DockerFile 建置

- 將容器上公開通訊埠 80 轉送至主機的通訊埠 81

- 將主機上專案目錄裝載至容器內的 /code，可讓您修改程式碼而不需重建映像

- 將 Web 服務連結至 redis 服務

Redis 服務會使用從 Docker Hub 登錄提取的[最新公用 redis 映像](https://hub.docker.com/_/redis/)。 [redis](https://redis.io/) 是伺服器端應用程式的熱門快取系統。

### <a name="step-5-build-and-run-your-docker-app"></a>步驟 5：建置並執行您的 Docker 應用程式

如果您的應用程式只有單一容器，您只需要將其部署至您的 Docker 主機 (VM 或實體伺服器) 來執行。 不過，如果您的應用程式由多個服務組成，您也需要「撰寫」該應用程式。 讓我們看看不同的選項。

@no__t 0Option：執行單一容器或服務***

您可以使用 docker run 命令執行 Docker 映像，如下所示：

```console
docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

針對此特定的部署，我們將會將傳送至連接埠 80 的要求重新導向至內部連接埠 5000。 現在應用程式正在主機層級的外部連接埠 80 上接聽。

***Option B：撰寫並執行多容器應用程式***

在大部分的企業案例中，Docker 應用程式由多個服務組成。 在這些案例中，您可以執行 `docker-compose up` 命令 (圖 4-27)，會使用您先前可能已建立的 docker compose.yml 檔案。 執行此命令會部署組成應用程式及其所有相關容器。

![docker compose up 命令的主控台輸出。](./media/docker-apps-inner-loop-workflow/results-docker-compose-up.png)

**圖 4-27**。 執行 "docker-compose up" 命令的結果

執行 `docker-compose up` 之後，您會將應用程式及其相關容器部署至您的 Docker 主機，如圖 4-28 以 VM 表示。

![執行多容器應用程式的 VM。](./media/docker-apps-inner-loop-workflow/vm-with-docker-containers-deployed.png)

**圖 4-28**。 部署了 Docker 容器的 VM

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a>步驟 6：測試您的 Docker 應用程式 (本機方式，在您的本機 CD VM 中)

此步驟會隨應用程式執行的作業而異。

在部署為單一容器或服務的簡單 .NET Core Web API "Hello World" 中，您只需要提供 DockerFile 中指定的 TCP 連接埠來存取服務。

如果 localhost 未開啟，請使用此命令尋找機器的 IP 位址以巡覽至您的服務：

```console
docker-machine {IP} {YOUR-CONTAINER-NAME}
```

在 Docker 主機上，開啟瀏覽器並巡覽至該網站；您應該會看到您的應用程式/服務正在執行，如圖 4-29 所示。

![從 localhost/API/values 回應的瀏覽器檢視。](./media/docker-apps-inner-loop-workflow/test-docker-app-locally-localhost.png)

**圖 4-29**。 使用 localhost 在本機測試 Docker 應用程式

請注意，其正在使用連接埠 80，但在內部會重新導向至連接埠 5000，因為這是其與 `docker run` 一起部署的方式，如先前所述。

您可以從終端機使用 CURL 來測試。 在 Windows 上的 Docker 安裝中，預設 IP 是 10.0.75.1，如圖 4-30 所示。

![使用 curl 取得 http://10.0.75.1/API/values 的主控台輸出](./media/docker-apps-inner-loop-workflow/test-docker-app-locally-curl.png)

**圖 4-30**。 使用 CURL 在本機測試 Docker 應用程式

**對在 Docker 上執行的容器進行偵錯**

Visual Studio Code 支援對 Docker 的偵錯，如果您使用 Node.js 和像是 .NET Core 容器的其他平台。

在使用適用於 Windows 或 Mac 的 Visual Studio 時，您也可以對 Docker 中的 .NET Core 或 .NET Framework 容器進行偵錯，如下一節中所述。

> [!TIP]
>@no__t 0To 深入瞭解如何對 node.js Docker 容器進行調試，請參閱 <https://blog.docker.com/2016/07/live-debugging-docker/> 和 <https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/>。

>[!div class="step-by-step"]
>[上一頁](docker-apps-development-environment.md)
>[下一頁](visual-studio-tools-for-docker.md)
