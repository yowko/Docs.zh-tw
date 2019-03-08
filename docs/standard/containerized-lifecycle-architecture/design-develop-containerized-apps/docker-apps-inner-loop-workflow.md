---
title: Docker 應用程式的內部迴圈開發工作流程
description: 了解開發 Docker 應用程式的 「 內部迴圈 」 工作流程。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 1ed0feeec682f5a79bc38db6a101b751ea4dbc3a
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2019
ms.locfileid: "57676664"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a>Docker 應用程式的內部迴圈開發工作流程

之前觸發外部迴圈工作流程跨越整個 DevOps 循環，所有開始每位開發人員在電腦上，應用程式本身程式碼撰寫、 使用其慣用的語言或平台，以及在本機進行測試 (圖 4-21)。 但在每個案例中，您有很重要的一點共通點，無論選擇何種語言、 架構或平台。 在此特定的工作流程，您一律開發並測試 Docker 容器，但只能在本機。

![步驟 1-程式碼/執行/偵錯](./media/image18.png)

**圖 4-21**： 內部迴圈開發內容

Docker 映像的執行個體的容器將會包含這些元件：

-   作業系統選取項目 （例如，對 Linux 散發套件或 Windows）

- 加入開發人員 （例如，應用程式二進位檔） 的檔案

-   設定 （例如，環境設定和相依性）

- 指示的哪些處理程序來執行 docker

您可以設定內部迴圈開發工作流程，利用 Docker 處理序 （下一節中所述）。 請考慮設定環境的初始步驟不包含在內，因為您只需要進行一次。

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a>建置使用 Visual Studio Code 和 Docker CLI 的 Docker 容器內的單一應用程式

應用程式是由您自己的服務加上額外的程式庫 （相依性） 所組成。

圖 4-22 顯示您通常需要執行時建置的 Docker 應用程式，後面接著每個步驟的詳細描述的基本步驟。

![工作流程概觀：步驟 1-程式碼中，步驟 2-撰寫 Dockerfile，步驟 3-建立 Dockerfile，步驟 4 中所定義的映像-定義服務使用 docker-compose 檔案，步驟 5-執行容器或組成的應用程式，步驟 6-測試應用程式，步驟 7-推播開始外部迴圈 （CI/CD 管線），或繼續 developing。](./media/image19.png)

**圖 4-22**。 使用 Docker CLI 的容器化 Docker 應用程式的生命週期的高階工作流程

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a>步驟 1：開始在 Visual Studio Code 中撰寫程式碼，並建立初始應用程式/服務基準

開發您的應用程式的方式是類似於未 Docker 的方式。 差別在於，在開發時，您要部署與測試您的應用程式或服務放在您的本機環境 （例如 Linux VM 或 Windows） 中的 Docker 容器內執行。

**設定您的本機環境**

使用適用於 Mac 和 Windows 的 Docker 的最新版本，這遠比以往若要開發 Docker 應用程式，而且安裝程式是直接的。

> [!INFORMATION]
>
> 如需有關設定 Docker for Windows 的指示，請移至<https://docs.docker.com/docker-for-windows/>。
>
>如需 Docker for Mac 設定指示，請移至<https://docs.docker.com/docker-for-mac/>。

此外，您需要的程式碼編輯器，讓您實際上可以開發應用程式時使用 Docker CLI。

Microsoft 提供的 Visual Studio Code 中，也就是支援 Mac、 Windows、 和 Linux 上，並提供 IntelliSense 的輕量型程式碼編輯器[支援用於多種語言](https://code.visualstudio.com/docs/languages/overview)(JavaScript、.NET、 Go、 Java、 Ruby、 Python 和大部分現代程式語言），[偵錯](https://code.visualstudio.com/Docs/editor/debugging)，[與 Git 整合](https://code.visualstudio.com/Docs/editor/versioncontrol)並[延伸模組支援](https://code.visualstudio.com/docs/extensions/overview)。 此編輯器是適用於 Mac 和 Linux 的開發人員的絕佳選擇。 在 Windows 中，您也可以使用完整的 Visual Studio 應用程式。

> [!INFORMATION]
>
> 如需安裝 Visual Studio 程式碼的 Windows、 Mac 或 Linux 的指示，請移至<https://code.visualstudio.com/docs/setup/setup-overview/>。
>
> 如需 Docker for Mac 設定指示，請移至<https://docs.docker.com/docker-for-mac/>。

您可以使用 Docker CLI，並撰寫程式碼，使用任何程式碼編輯器中，但使用 Visual Studio Code 的 Docker 擴充功能可輕鬆為作者`Dockerfile`和`docker-compose.yml`工作區中的檔案。 您也可以從 Visual Studio 程式碼 IDE，來執行 Docker 命令使用 Docker CLI 之下執行工作和指令碼。

適用於 VS Code Docker 擴充功能提供下列功能：

- 自動`Dockerfile`和`docker-compose.yml`檔案產生

- 語法反白顯示並暫留秘訣`docker-compose.yml`和`Dockerfile`檔案

- （完成） 適用於 IntelliSense`Dockerfile`和`docker-compose.yml`檔案

- Linting （錯誤和警告）`Dockerfile`檔案

- 最常見的 Docker 命令的命令選擇區 (F1) 整合

- 總管的整合來管理映像和容器

- 部署至 Azure App Service 從 DockerHub 和 Azure Container Registry 的映像

若要安裝 Docker 擴充功能中，按下 Ctrl + Shift + P，輸入`ext install`，然後執行安裝的延伸模組命令，以顯示 Marketplace 延伸模組清單。 接下來，輸入**docker**來篩選結果，並如上圖中 圖 4 月 23 日，然後選取支援 Docker 延伸模組。

![適用於 VS Code 的 Docker 擴充功能檢視。](./media/image20.png)

**圖 4-23**： Visual Studio Code 中安裝 Docker 擴充功能

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a>步驟 2：建立 DockerFile，現有的映像 （純文字的 OS 或開發環境，例如.NET Core、 Node.js 和 Ruby） 相關

您將需要`DockerFile`每個要建置的自訂映像，以及每個要部署的容器。 如果您的應用程式組成單一的自訂服務，您將需要單一`DockerFile`。 但如果您的應用程式所組成 （就像在微服務架構） 的多個服務，您將需要一個`Dockerfile`每項服務。

`DockerFile`常放在您的應用程式或服務的根資料夾，而包含必要的命令，因此 Docker 知道如何設定及執行該應用程式或服務。 您可以建立您`DockerFile`並將它新增至您的專案，以及您的程式碼 (.NET Core、 node.js 等)，或如果您還不熟悉的環境，看看以下的提示。

> [!TIP]
>
> 您可以使用 Docker 擴充功能來引導您使用`Dockerfile`和`docker-compose.yml`Docker 容器的相關檔案。 最後，您可能會撰寫這類檔案，而這項工具，但使用 Docker 擴充功能是不錯的起點，將可加速您的學習曲線。

在 圖 4-24，您可以看到如何 docker-compose 檔案會加入適用於 VS Code 中使用 Docker 擴充功能。

![主控台檢視的 Docker 擴充功能適用於 VS Code。](./media/image24.png)

**圖 4-24**： Docker 檔案已新增使用**新增 Docker 檔案至工作區命令**

當您新增 DockerFile 時，您會指定您要使用哪些基礎 Docker 映像 (例如使用`FROM microsoft/aspnetcore`)。 您通常會建置您自訂的映像，在您從在任何官方存放庫取得的基底映像之上[Docker Hub 登錄](https://hub.docker.com/)(像是[適用於.NET Core 的映像](https://hub.docker.com/r/microsoft/dotnet/)或[適用於 Node.js](https://hub.docker.com/_/node/)).

***使用現有的正式 Docker 映像***

使用版本號碼的語言在堆疊的官方存放庫可確保可以相同的語言功能 （包括開發、 測試和生產環境） 的所有電腦上。

以下是.NET Core 容器的範例 DockerFile:

```Dockerfile
# Base Docker image to use  
FROM microsoft/dotnet:2.1-aspnetcore-runtime
  
# Set the Working Directory and files to be copied to the image  
ARG source  
WORKDIR /app  
COPY ${source:-bin/Release/PublishOutput} .  
  
# Configure the listening port to 80 (Internal/Secured port within Docker host)  
EXPOSE 80  
  
# Application entry point  
ENTRYPOINT ["dotnet", "MyCustomMicroservice.dll"]
```

在此情況下，映像為基礎的官方 ASP.NET Core Docker 映像 （適用於 Linux 和 Windows 的多架構），根據列 2.1 版`FROM microsoft/dotnet:2.1-aspnetcore-runtime`。 (如需有關本主題的詳細資訊，請參閱 < [ASP.NET Core Docker 映像](https://hub.docker.com/r/microsoft/aspnetcore/)頁面並[.NET Core Docker 映像](https://hub.docker.com/r/microsoft/dotnet/)頁面)。

在 DockerFile 中，您也可以指示 Docker 接聽 TCP 連接埠，您將使用在執行階段 （例如連接埠 80）。

您可在 Dockerfile 中指定其他的組態設定，視您使用的語言和架構而定。 比方說，`ENTRYPOINT`使用直線`["dotnet", "MySingleContainerWebApp.dll"]`會指示 Docker 執行.NET Core 應用程式。 如果您使用 SDK 和.NET Core CLI (`dotnet CLI`) 若要建置及執行.NET 應用程式，此設定會有所不同。 此處的重點是 ENTRYPOINT 行與其他設定，取決於您為您的應用程式選擇的語言及平台。

> [!INFORMATION]
>
> 如需有關如何建置.NET Core 應用程式的 Docker 映像的詳細資訊，請移至<https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>。
>
> 若要深入了解如何建置自己的映像，請移至<https://docs.docker.com/engine/tutorials/dockerimages/>。

**使用多架構映像儲存機制**

存放庫中的單一映像名稱可以包含多種平台變化，例如 Linux 映像和 Windows 映像。 這項功能可讓像 Microsoft （基底映像建立者） 的廠商建立單一的存放庫，以涵蓋多個平台 （也就是 Linux 和 Windows）。 例如， [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/)在 Docker Hub 登錄存放庫會提供適用於 Linux 和 Windows Nano Server 支援使用相同的映像名稱。

提取[microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/)從 Windows 主機的映像會提取 Windows variant，而從 Linux 主機提取相同的映像名稱會提取 Linux variant。

***從頭開始建立您的基底映像***

在此所述，您可以從頭建立您自己的 Docker 基礎映像[文章](https://docs.docker.com/engine/userguide/eng-image/baseimages/)從 Docker。 這種情況下可能不是最適合您，如果您剛開始使用 Docker，但如果您想要設定您自己的基底映像的特定位元，您可以執行它。

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a>步驟 3：建立自訂 Docker 映像嵌入您的服務

針對每個包含您的應用程式的自訂服務，您必須建立相關的映像。 如果您的應用程式組成的單一服務或 web 應用程式，您將需要一張圖片。

> [!NOTE]
>
> 當考慮 「 外部迴圈 DevOps 工作流程 」，每當您您的程式碼從推送至 Git 存放庫 （持續整合），因此會在全域環境中建立映像時，就會自動化的建置程序建立映像您原始程式碼。
>
> 但我們考慮移到該外部迴圈路由之前，我們需要確保 Docker 應用程式實際運作正常，讓它們不會推送程式碼，可能無法正常運作 （Git 等等），才會進行來源控制系統。
>
> 因此，每位開發人員第一次需要整個 「 內部迴圈 」 程序，在本機測試，並繼續開發，直到他們想要推送完整的功能或變更原始檔控制系統。

在您的本機環境中和使用 DockerFile 建立映像，您可以使用 docker build 命令，在圖 4-25 示 (您也可以執行`docker-compose up --build`由數個容器/服務所組成的應用程式)。

![Docker-compose build，顯示下載進度的映像的主控台輸出。](./media/image25.png)

**圖 4-25**： 執行 docker 建置

（選擇性） 而不是直接執行`docker build`從 [專案] 資料夾中，您第一次可以產生可部署資料夾使用執行所需的.NET 程式庫`dotnet publish`命令，然後再執行`docker build`。

此範例會使用名稱來建立 Docker 映像`cesardl/netcore-webapi-microservice-docker:first`(`:first`是標記，例如特定的版本)。 您可以採取此步驟中的每個您需要建立數個容器組成 Docker 應用程式的自訂映像。

您可以找到現有的映像在本機存放庫 （您的開發電腦） 中使用 docker images 命令所示的圖 4-26。

![主控台輸出命令 docker 映像，顯示現有的映像。](./media/image26.png)

**圖 4-26**。 檢視現有的映像使用 docker 映像

### <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a>步驟 4：建置具有多個服務的組成的 Docker 應用程式時，在 docker-compose.yml 中定義您的服務

使用`docker-compose.yml`檔案中，您可以定義一組相關的服務一起部署為組成的應用程式的下一個步驟一節所述的部署命令。

建立該檔案在您的 main 或根解決方案資料夾;它應該類似於此所示的內容`docker-compose.yml`檔案：

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

在此案例中，此檔案會定義兩個服務： web 服務 （您自訂的服務） 和 redis 服務 （受歡迎的快取服務）。 每個服務會部署為容器，，因此我們要用於每個具體的 Docker 映像。 此特定的 web 服務，影像必須執行下列作業：

- 建立從目前的目錄中的 DockerFile

- 轉送公開的連接埠 80 上的容器在主機電腦上的連接埠 81

- 讓您修改程式碼，而不需要重建映像的容器內的 /code 主機上掛接專案目錄

- 連結至 redis 服務的 web 服務

Redis 服務會使用[最新的公用 redis 映像](https://hub.docker.com/_/redis/)從 Docker Hub 登錄提取。 [redis](https://redis.io/)是伺服器端應用程式的受歡迎的快取系統。

### <a name="step-5-build-and-run-your-docker-app"></a>步驟 5：建置並執行您的 Docker 應用程式

如果您的應用程式有單一容器，您只需要藉由將它部署至您的 Docker 主機 （VM 或實體伺服器） 執行它。 不過，如果您的應用程式多個服務組成，您需要*組合*也。 讓我們看到不同的選項。

***選項 a:執行單一容器或服務***

您可以執行的 Docker 映像使用 docker run 命令，如下所示：

```console
docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

針對此特定的部署，我們將會將要求重新導向傳送至連接埠 80 的內部連接埠 5000。 現在應用程式正在接聽的外部連接埠 80，在主機層級。

***選項 b:撰寫和執行多容器應用程式***

在大部分的企業案例中，將多個服務組成 Docker 應用程式。 在這些情況下，您可以執行`docker-compose up`命令 (圖 4-27)，將使用您可能會有先前建立的 docker compose.yml 檔案。 執行此命令會部署所有及其相關容器組成的應用程式。

![主控台輸出 docker compose up 命令。](./media/image27.png)

**圖 4-27**。 執行 「 啟動 docker compose"命令的結果

執行之後`docker-compose up`，您將部署應用程式和其相關的容器到您的 Docker 主機中所示的圖 4-28，呈現的 VM。

![執行多容器應用程式的 VM。](./media/image28.png)

**圖 4-28**。 部署了 Docker 容器的 VM

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a>步驟 6：測試 Docker 應用程式 （在本機，在您本機的 CD VM)

此步驟會因應用程式的執行。

中的簡單.NET Core Web API"Hello World"部署為單一容器或服務，您只需要提供 DockerFile 中指定的 TCP 連接埠來存取服務。

如果 localhost 未開啟，以瀏覽至您的服務，尋找電腦的 IP 位址，使用下列命令：

```console
docker-machine {IP} {YOUR-CONTAINER-NAME}
```

在 Docker 主機上，開啟瀏覽器並瀏覽至該網站;示範在圖 4-29，應該會看到執行中，您的應用程式/服務。

![從 localhost/API/values 回應的瀏覽器檢視。](./media/image29.png)

**圖 4-29**。 測試使用 localhost 在本機的 Docker 應用程式

請注意，它使用連接埠 80，但在內部會被重新導向至連接埠 5000，因為這是如何部署與`docker run`，如先前所述。

您可以從終端機使用 CURL 來測試。 在 Docker 安裝在 Windows 中，預設值是 IP 10.0.75.1，如上圖中圖 4-30。

![主控台輸出取得 http://10.0.75.1/API/values與 curl](./media/image30.png)

**圖 4-30**。 由使用 CURL 在本機測試 Docker 應用程式

**偵錯在 Docker 上執行的容器**

Visual Studio Code 支援偵錯的 Docker，如果您使用 Node.js 和.NET Core 容器等其他平台。

您也可以偵錯在 Docker 中的.NET Core 或.NET Framework 的容器時使用 Visual Studio for Windows 或 Mac 下, 一節中所述。

> [!INFORMATION]
>
> 若要深入了解偵錯 Node.js Docker 容器，請前往<https://blog.docker.com/2016/07/live-debugging-docker/>和<https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/>。

>[!div class="step-by-step"]
>[上一頁](docker-apps-development-environment.md)
>[下一頁](visual-studio-tools-for-docker.md)
