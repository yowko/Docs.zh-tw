---
title: Docker 應用程式的內部迴圈開發工作流程
description: 瞭解 Docker 應用程式的「內部迴圈」開發工作流程。
ms.date: 08/06/2020
ms.openlocfilehash: d66274a64591f79f242c1e8a63951b51d94a9ecd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676526"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a>Docker 應用程式的內部迴圈開發工作流程

在觸發跨越整個 DevOps 循環的外部迴圈工作流程之前，所有項目都從每個開發人員的機器開始，使用其慣用語言或平台對應用程式本身編碼，並在本機進行測試 (圖 4-21)。 但不論何種情況，不論您選擇何種語言、架構或平台，您都會有一個重要的共同點。 在此特定的工作流程中，您永遠都不需要在其他環境中開發和測試 Docker 容器，而是在本機。

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

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a>步驟1：在 Visual Studio Code 中開始撰寫程式碼，並建立您的初始應用程式/服務基準

開發 Docker 應用程式的方式，與不使用 Docker 開發應用程式的方式類似。 差別在於，在開發時，您要部署並測試放置於本機環境之 Docker 容器 (例如 Linux VM 或 Windows) 中正在執行的應用程式或服務。

**設定您的本機環境**

使用適用于 Mac 和 Windows 的最新 Docker Desktop 版本，開發 Docker 應用程式比以往更容易，而且安裝程式很簡單。

> [!TIP]
> 如需設定適用于 Windows 的 Docker Desktop 的指示，請移至 <https://docs.docker.com/docker-for-windows/> 。
>
> 如需設定適用于 Mac 的 Docker Desktop 的指示，請移至 <https://docs.docker.com/docker-for-mac/> 。

此外，您也需要程式碼編輯器，讓您可在使用 Docker CLI 時實際開發應用程式。

Microsoft 提供的 Visual Studio Code 是 Windows、Linux 和 macOS 上所支援的輕量程式碼編輯器，並提供 IntelliSense [支援多種語言](https://code.visualstudio.com/docs/languages/overview) (JavaScript、.Net、Go、JAVA、Ruby、Python 和大部分新式語言) 、 [調試](https://code.visualstudio.com/Docs/editor/debugging)程式、 [與 Git](https://code.visualstudio.com/Docs/editor/versioncontrol) 和 [延伸模組支援](https://code.visualstudio.com/docs/extensions/overview)的整合。 此編輯器非常適合 macOS 和 Linux 開發人員。 在 Windows 中，您也可以使用 Visual Studio。

> [!TIP]
> 如需安裝適用于 Windows、Linux 或 macOS 之 Visual Studio Code 的指示，請移至 <https://code.visualstudio.com/docs/setup/setup-overview/> 。
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

![適用於 VS Code 的 Docker 延伸模組檢視。](media/docker-apps-inner-loop-workflow/install-docker-extension-vs-code.png)

**圖 4-23**： 在 Visual Studio Code 中安裝 Docker 延伸模組

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a>步驟2：建立與現有映射相關的 DockerFile， (一般 OS 或開發環境（例如 .NET Core、Node.js 和 Ruby）) 

針對每個要建置的自訂映像，以及每個要部署的容器，您都需要一個 `DockerFile`。 如果您的應用程式是由單一自訂服務所組成，您將需要一個 `DockerFile` 。 但如果您的應用程式由多個服務所組成 (如同在微服務架構中)，針對每項服務您將需要一個 `Dockerfile`。

`DockerFile` 通常放在應用程式或服務的根資料夾中，並包含必要的命令，以讓 Docker 知道如何設定並執行該應用程式或服務。 您可以建立您的 `DockerFile`，並將其與您的程式碼 (node.js、.NET Core 等) 一起新增至專案中；如果您還不熟悉環境，請查看下列提示。

> [!TIP]
> 您可以使用 Docker 延伸模組來引導您使用與 Docker 容器相關的 `Dockerfile` 和 `docker-compose.yml` 檔案。 最後，您可能會在沒有此工具的情況下撰寫這類檔案，但使用 Docker 延伸模組是不錯的起點，可加速您的學習曲線。

在圖4-24 中，您可以使用適用于 VS Code 的 Docker 擴充功能，查看將 docker 檔案新增至專案的步驟：

1. 開啟命令選擇區，輸入 "**docker**"，然後選取 [**將 docker 檔案新增至工作區**]。
2. 選取應用程式平臺 (ASP.NET Core) 
3. 選取作業系統 (Linux) 
4. 包含選用的 Docker Compose 檔案
5. 輸入要發佈的埠 (80、443) 
6. 選取專案

![使用 docker 擴充功能新增 docker 檔案的步驟](media/docker-apps-inner-loop-workflow/add-docker-files-to-workspace-command.png)

**圖 4-24**： 使用 [ **將 docker 檔案新增至工作區** ] 命令新增的 docker 檔案

當您新增 DockerFile 時，您會指定要使用的基底 Docker 映射 (例如使用 `FROM mcr.microsoft.com/dotnet/aspnet`) 。 您通常會在基底映像之上建置自訂映像，該基底映像可從 [Docker Hub登錄](https://hub.docker.com/)的任何官方存放庫取得 (例如 [.NET Core 的映像](https://hub.docker.com/_/microsoft-dotnet/)或 [Node.js](https://hub.docker.com/_/node/) 的映像)。

> [!TIP]
> 您必須針對應用程式中的每個專案重複此程式。 不過，此延伸模組會要求您在第一次之後覆寫產生的 docker 撰寫檔案。 您應回復不覆寫它，讓擴充功能建立個別的 docker 組成檔案，您可以在執行 docker 撰寫之前，手動合併這些檔案。

**_使用現有的官方 Docker 映射_**

使用具有版本號碼的官方語言堆疊存放庫，可確保所有電腦上都能使用相同的語言功能 (包括開發、測試和生產環境)。

下列是 .NET Core 容器的範例 DockerFile：

```dockerfile
FROM mcr.microsoft.com/dotnet/aspnet:3.1 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/sdk:3.1 AS build
WORKDIR /src
COPY ["src/WebApi/WebApi.csproj", "src/WebApi/"]
RUN dotnet restore "src/WebApi/WebApi.csproj"
COPY . .
WORKDIR "/src/src/WebApi"
RUN dotnet build "WebApi.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "WebApi.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "WebApi.dll"]
```

在此情況下，映射是以正式 ASP.NET Core Docker 映射的3.1 版為基礎， (多架構的 Linux 和 Windows) （依據這一行） `FROM mcr.microsoft.com/dotnet/aspnet:3.1` 。 (如需本主題的詳細資訊，請參閱 [ASP.NET Core Docker 映像](https://hub.docker.com/_/microsoft-dotnet-aspnet/)頁面及 [.NET Core Docker 映像](https://hub.docker.com/_/microsoft-dotnet/)頁面)。

在 DockerFile 中，您也可以指示 Docker 接聽您將在執行時間使用的 TCP 埠 (例如埠80或 443) 。

您可在 Dockerfile 中指定其他的組態設定，視您使用的語言和架構而定。 例如，`ENTRYPOINT` 行中有 `["dotnet", "WebMvcApplication.dll"]` 會指示 Docker 執行 .NET Core 應用程式。 如果您使用 SDK 和 .NET Core CLI (`dotnet CLI`) 建置及執行 .NET 應用程式，此設定會有所不同。 此處的重點，是 ENTRYPOINT 行與其他設定會視您選擇的應用程式語言和平台而定。

> [!TIP]
> 如需如何建置 .NET Core 應用程式之 Docker 映像的詳細資訊，請瀏覽 <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>。
>
> 若要深入了解如何建置您自己的映像，請瀏覽 <https://docs.docker.com/engine/tutorials/dockerimages/>。

**使用多架構映像存放庫**

存放庫中的單一映像名稱可以包含多種平台變化，例如 Linux 映像和 Windows 映像。 這項功能可讓 Microsoft (基底映像建立者) 等廠商建立單一存放庫以涵蓋多個平台 (即 Linux 和 Windows)。 例如，Docker Hub 登錄提供的 [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-aspnet/) 存放庫，會使用相同的映像名稱提供 Linux 和 Windows Nano Server 支援。

從 Windows 主機提取 [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-aspnet/) 映像會提取 Windows 變化，而從 Linux 主機提取相同的映像名稱則會提取 Linux 變化。

**_從頭開始建立您的基底映射_**

您可以從頭建立您自己的 Docker 基底映像，如 Docker 的此[文章](https://docs.docker.com/engine/userguide/eng-image/baseimages/)中所述。 如果您是 Docker 新手，此方案可能不適合您，但如果您想要設定專屬基底映像的特點，您可以這樣做。

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a>步驟3：建立您的自訂 Docker 映射，在其中內嵌您的服務

針對每個包含您應用程式的自訂服務，您需要建立相關映像。 如果您的應用程式組成為單一的服務或 Web 應用程式，則您只需要單一映像。

> [!NOTE]
> 考慮「外部迴圈 DevOps 工作流程」時，每當您將原始程式碼推送至 Git 存放庫 (持續整合)，映像會透過自動建置程序建立，因此映像將於原始程式碼的全域環境中建立。
>
> 但在考慮前往該外部迴圈路由之前，您必須確定 Docker 應用程式實際運作正常，使其不會將可能無法正常運作的程式碼推送至原始檔控制系統 (Git 等 ) 。
>
> 因此，每位開發人員首先需要執行整個內部迴圈程序，以在本機進行測試並繼續開發，直到他們想要推送完整的功能或變更為原始檔控制系統。

若要在您的本機環境中建立映射並使用 DockerFile，您可以使用 docker build 命令，如圖4-25 所示，因為它已經為您標記映射，並使用簡單的命令來建立應用程式中所有服務的映射。

![顯示 docker 撰寫組建命令之主控台輸出的螢幕擷取畫面。](media/docker-apps-inner-loop-workflow/run-docker-build-command.png)

**圖 4-25**： 執行 docker build

(選用) 不直接從專案資料夾執行 `docker build`，而是先使用 run `dotnet publish` 命令產生具有所需 .NET 程式庫的可部署資料夾，然後執行 `docker build`。

此範例使用名稱 `explore-docker-vscode/webapi:latest` 來建立 Docker 映像 (`:latest` 是標籤，例如特定版本)。 您可以透過數個容器，為組成 Docker 應用程式所需建立的每個自訂映像採用此步驟。 不過，我們會在下一節中看到使用來進行這項作業比較容易 `docker-compose` 。

您可以使用命令，在您的開發電腦)  (您的本機存放庫中找到現有的映射 `docker images` ，如圖4-26 所示。

![docker images 命令的主控台輸出，顯示現有的映像。](media/docker-apps-inner-loop-workflow/view-existing-images-with-docker-images.png)

**圖 4-26**。 使用 docker images 檢視現有的映像

### <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a>步驟4：建立具有多個服務的組成 Docker 應用程式時，在 >docker-compose.yml. yml 中定義您的服務

透過 `docker-compose.yml` 檔案，您可以定義一組相關服務，部署為具有部署命令 (將於下一節解釋) 的組成應用程式。

在主要或根方案資料夾中建立該檔案；其內容應與此 `docker-compose.yml` 檔案中顯示的內容類似：

```yml
version: "3.4"

services:
  webapi:
    image: webapi
    build:
      context: .
      dockerfile: src/WebApi/Dockerfile
    ports:
      - 51080:80
    depends_on:
      - redis
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://+:80

  webapp:
    image: webapp
    build:
      context: .
      dockerfile: src/WebApp/Dockerfile
    ports:
      - 50080:80
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://+:80
      - WebApiBaseAddress=http://webapi

  redis:
    image: redis
```

在此特定案例中，此檔案會定義三個服務： web API 服務 (您的自訂服務) 、web 應用程式和 Redis 服務 (常用的快取服務) 。 每個服務都會部署為容器，因此您必須為每個服務使用具體的 Docker 映射。 針對這個特定的應用程式：

- Web API 服務是由目錄中的 DockerFile 所建立 `src/WebApi/Dockerfile` 。

- 主機埠51080會轉送至容器上公開的埠 80 `webapi` 。

- Web API 服務相依于 Redis 服務

- Web 應用程式會使用內部位址存取 web API 服務： `http://webapi` 。

- Redis 服務會使用從 Docker Hub 登錄中提取的 [最新公用 Redis 映射](https://hub.docker.com/_/redis/) 。 [Redis](https://redis.io/) 是伺服器端應用程式的熱門快取系統。

### <a name="step-5-build-and-run-your-docker-app"></a>步驟5：建立並執行您的 Docker 應用程式

如果您的應用程式只有單一容器，您只需要將其部署至您的 Docker 主機 (VM 或實體伺服器) 來執行。 不過，如果您的應用程式由多個服務組成，您也需要「撰寫」該應用程式。 讓我們看看不同的選項。

**_選項 A：執行單一容器或服務_**

您可以使用 docker run 命令執行 Docker 映像，如下所示：

```console
docker run -t -d -p 50080:80 explore-docker-vscode/webapp:latest
```

針對此特定部署，我們會將傳送至主機上端口50080的要求重新導向至內部埠80。

**_選項 B：撰寫和執行多容器應用程式_**

在大部分的企業案例中，Docker 應用程式由多個服務組成。 在這些情況下，您可以執行 `docker-compose up` 命令 (圖 4-27) ，它將使用您先前建立的 >docker-compose.yml. yml 檔案。 執行此命令會建立所有自訂映射，並使用其所有相關容器來部署組成的應用程式。

![docker compose up 命令的主控台輸出。](media/docker-apps-inner-loop-workflow/results-docker-compose-up.png)

**圖 4-27**。 執行 "docker-compose up" 命令的結果

執行 `docker-compose up` 之後，您會將應用程式及其相關容器部署至您的 Docker 主機，如圖 4-28 以 VM 表示。

![執行多容器應用程式的 VM。](./media/docker-apps-inner-loop-workflow/vm-with-docker-containers-deployed.png)

**圖 4-28**。 部署了 Docker 容器的 VM

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a>步驟6：在本機 CD VM (本機測試您的 Docker 應用程式) 

此步驟會隨應用程式執行的作業而異。

在部署為單一容器或服務的簡單 .NET Core Web API "Hello World" 中，您只需要提供 DockerFile 中指定的 TCP 連接埠來存取服務。

在 Docker 主機上，開啟瀏覽器並巡覽至該網站；您應該會看到您的應用程式/服務正在執行，如圖 4-29 所示。

![從 localhost/API/values 回應的瀏覽器檢視。](media/docker-apps-inner-loop-workflow/test-docker-app-locally-localhost.png)

**圖 4-29**。 使用瀏覽器在本機測試您的 Docker 應用程式

請注意，它會使用埠50080，但會在內部重新導向至埠80，因為這是與先前所述的部署方式 `docker compose` 。

您可以使用來自終端機的捲曲瀏覽器進行測試，如圖4-30 所示。

![從中取得的捲曲結果 http://localhost:51080/WeatherForecast](media/docker-apps-inner-loop-workflow/test-docker-app-locally-curl.png)

**圖 4-30**。 使用 CURL 在本機測試 Docker 應用程式

**對在 Docker 上執行的容器進行偵錯**

Visual Studio Code 支援對 Docker 的偵錯，如果您使用 Node.js 和像是 .NET Core 容器的其他平台。

在使用適用於 Windows 或 Mac 的 Visual Studio 時，您也可以對 Docker 中的 .NET Core 或 .NET Framework 容器進行偵錯，如下一節中所述。

> [!TIP]
> 若要深入瞭解 Node.js Docker 容器的調試，請參閱 <https://blog.docker.com/2016/07/live-debugging-docker/> 和 <https://docs.microsoft.com/archive/blogs/user_ed/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more> 。

> [!div class="step-by-step"]
> [上一個](docker-apps-development-environment.md) 
> [下一步](visual-studio-tools-for-docker.md)
