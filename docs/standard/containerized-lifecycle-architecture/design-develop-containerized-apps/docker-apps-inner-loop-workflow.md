---
title: Docker 應用程式的內部迴圈開發工作流程
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: be9c3fe165be32df43073919904b85120c52d595
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50034453"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a>Docker 應用程式的內部迴圈開發工作流程

之前觸發外部迴圈工作流程跨越整個 DevOps 循環，所有開始每位開發人員在電腦上，應用程式本身程式碼撰寫、 使用其慣用的語言或平台，以及在本機進行測試 (圖 4-14)。 但在每個案例中，您會有非常重要的一點共通點，無論選擇何種語言、 架構或平台。 在此特定的工作流程，您一律開發和測試 Docker 容器，但只能在本機。

![](./media/image18.png)

圖 4-14： 內部迴圈開發內容

Docker 映像的執行個體的容器將會包含這些元件：

-   作業系統選取項目 （例如，對 Linux 散發套件或 Windows）

-   加入開發人員 （例如，應用程式二進位檔） 的檔案

-   設定 （例如，環境設定和相依性）

-   指示的哪些處理程序來執行 docker

您可以設定內部迴圈開發工作流程，利用 Docker 處理序 （下一節中所述）。 考慮設定環境的初始步驟不包含在內，因為您需要這樣做，就可以一次。

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a>建置使用 Visual Studio Code 和 Docker CLI 的 Docker 容器內的單一應用程式

應用程式是由您自己的服務加上額外的程式庫 （相依性） 所組成。

圖 4-15 示範您通常需要執行時建置的 Docker 應用程式，後面接著每個步驟的詳細描述的基本步驟。

![](./media/image19.png)

圖 4-15： 使用 Docker CLI 的容器化 Docker 應用程式的生命週期的高階工作流程

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a>步驟 1： 開始在 Visual Studio Code 中撰寫程式碼，並建立初始應用程式/服務基準

開發您的應用程式的方式是未 Docker 的方式十分類似。 差別在於，在開發時，您部署和測試您的應用程式或服務放在您的本機環境 （例如 Linux VM 或 Windows） 中的 Docker 容器內執行。

**設定您的本機環境**

使用適用於 Mac 和 Windows 的 Docker 的最新版本，這遠比以往若要開發 Docker 應用程式，而且安裝程式是直接的。

**進一歩** 如需有關設定 Docker for Windows 的指示，請移至[ https://docs.docker.com/docker-for-windows/ ](https://docs.docker.com/docker-for-windows/)。

如需 Docker for Mac 設定指示，請移至<https://docs.docker.com/docker-for-mac/>。

此外，您需要的程式碼編輯器，讓您實際上可以開發應用程式時使用 Docker CLI。

Microsoft 提供的 Visual Studio Code 中，也就是支援 Mac、 Windows、 和 Linux 上，並提供 IntelliSense 的輕量型程式碼編輯器[支援用於多種語言](https://code.visualstudio.com/docs/languages/overview)(JavaScript、.NET、 Go、 Java、 Ruby、 Python 和大部分現代程式語言），[偵錯](https://code.visualstudio.com/Docs/editor/debugging)，[與 Git 整合](https://code.visualstudio.com/Docs/editor/versioncontrol)並[延伸模組支援](https://code.visualstudio.com/docs/extensions/overview)。 此編輯器是適用於 Mac 和 Linux 的開發人員的絕佳選擇。 在 Windows 中，您也可以使用完整的 Visual Studio 應用程式。

**進一歩** 如需安裝 Visual Studio for Windows、 Mac 或 Linux 的指示，請移至<https://code.visualstudio.com/docs/setup/setup-overview/>。

您可以使用 Docker CLI，並撰寫程式碼，使用任何程式碼編輯器中，但如果您使用 Visual Studio Code，它可讓您輕鬆地撰寫 Dockerfile 和 docker-compose.yml 檔案在您的工作區中。 此外，您可以從 IDE，以提示所能執行使用 Docker CLI 底下的複雜的作業的指令碼執行 Visual Studio 程式碼工作。

Visual Studio Code 會提供的擴充功能，您必須安裝。 若要這樣做，請按 Ctrl + Shift + P，鍵入**ext 安裝**，然後執行 延伸模組： 安裝延伸模組命令來啟動 Marketplace 延伸模組清單。 接下來，輸入**docker**來篩選結果，然後按 Dockerfile 和 Docker Compose 檔案 (yml) 支援擴充功能，如上圖中圖 4-16。

![](./media/image20.png)

圖 4-16： 安裝 Visual Studio Code 中的 Docker 擴充功能

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a>步驟 2： 建立 DockerFile，現有的映像 （純文字的 OS 或開發環境，例如.NET Core、 Node.js 和 Ruby） 相關

您需要 DockerFile，每個要建置的自訂映像，以及每個要部署的容器，因此，如果您的應用程式組成單一的自訂服務，您將需要單一的 DockerFile。 但是，如果您的應用程式所組成 （就像在微服務架構） 的多個服務，您將需要一個 Dockerfile，每個服務。

DockerFile 通常會放在您的應用程式或服務的根資料夾內，並包含必要的命令，因此 Docker 知道如何設定及執行該應用程式或服務。 您可以建立您的 DockerFile，並將它新增至您的專案中，以及您的程式碼 (.NET Core、 node.js 等)，或如果您不熟悉的環境，看看以下的提示。

> [!TIP]
> 您可以使用命令列工具，稱為[yo docker](https://github.com/Microsoft/generator-docker)，這則來自您的專案，在您選擇的語言加入所需的 Docker 組態檔中的檔案。 基本上，協助開發人員開始使用，它會建立適當的 DockerFile 中，docker compose.yml 和其他相關聯的指令碼，以建置並執行 Docker 容器。 這個的 yeoman 產生器會提示您幾個問題，詢問您所選的開發語言和目的地容器主機。

![yo docker](./media/image21.png)

在 Windows 和 Mac 上，在這兩種情況下，執行 yo docker，但這會產生的範例程式碼專案 （目前.NET Core、 Golang、 和 Node.js 作為支援的語言） 已設定為搭配使用上圖 4-17 比方說，顯示來自終端機的兩個螢幕擷取畫面Docker 的頂端。

![](./media/image22.PNG)  ![](./media/image23.png)

圖 4-17: yo docker 命令在 Windows （左） 和 Mac 上的工具

圖 4-18 提供範例使用 yo docker 之後，您有現有的.NET Core 專案中會包含 scaffold 的地方。

![](./media/image24.PNG)

圖 4-18: yo docker 使用現有的.NET Core 專案就緒

您可以從 DockerFile 中，指定哪些基底的 Docker 映像，選擇您要使用 （例如，使用"FROM microsoft/dotnet:1.0.0-core"）。 您通常會建置您自訂的映像，您可以從在任何官方存放庫取得基底映像[Docker Hub 登錄](https://hub.docker.com/)(像是[適用於.NET Core 的映像](https://hub.docker.com/r/microsoft/dotnet/)或一個[適用於 Node.js](https://hub.docker.com/_/node/)).

***選項 a： 使用現有的正式 Docker 映像***

使用版本號碼的語言在堆疊的官方存放庫可確保可以相同的語言功能 （包括開發、 測試和生產環境） 的所有電腦上。

以下是.NET Core 容器的範例 DockerFile:

```
# Base Docker image to use
FROM microsoft/aspnetcore:1.0.1\

# Set the Working Directory and files to be copied to the image
ARG source
WORKDIR /app
COPY ${source:-bin/Release/PublishOutput} .

# Configure the listening port to 80 (Internal/Secured port within Docker host)
EXPOSE 80

# Application entry point
ENTRYPOINT ["dotnet", "MyCustomMicroservice.dll"]
```

在此情況下，它使用官方 ASP.NET Core Docker 映像的 1.0.1 版適用於名為 microsoft/aspnetcore:1.0.1 Linux。 如需詳細資訊，請參閱[ASP.NET Core Docker 映像頁面](https://hub.docker.com/r/microsoft/aspnetcore/)並[.NET Core Docker 映像頁面](https://hub.docker.com/r/microsoft/dotnet/)。 您也可以使用另一個可比較像的映像節點： 4-Node.js 或許多其他預先設定映像開發語言，可在 onbuild [Docker Hub](https://hub.docker.com/explore/)。

在 DockerFile 中，您也需要指示 Docker 接聽您在執行階段 （例如連接埠 80） 會使用 TCP 連接埠。

有其他線讓 Docker 知道如何執行應用程式，您可以加入根據您使用的語言/架構 DockerFile 中的設定。 比方說，您需要 ENTRYPOINT 行中的有\["dotnet"，"MyCustomMicroservice.dll"\]執行.NET Core 應用程式，雖然您可以根據以建置並執行您的服務方法的多個變異。 如果您使用的 SDK 和 dotnet CLI 來建置和執行.NET 應用程式，它會稍有不同。 重點是 ENTRYPOINT 行，加上額外的線條將會根據您選擇您的應用程式的語言/平台而不同。

**進一歩** 建置.NET Core 應用程式的 Docker 映像的相關資訊，請移至<https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>。

若要深入了解如何建置自己的映像，請移至[https://docs.docker.com/engine/\教學課程/dockerimages/](https://docs.docker.com/engine/tutorials/dockerimages/)。

**多平台映像存放庫**

由於 Windows 容器變得更普遍的單一的存放庫可以包含多種平台變化，例如 Linux 和 Windows 的映像。 這是可讓廠商能夠涵蓋多個平台，例如使用單一儲存機制的 Docker 中的新功能[microsoft/aspdotnetcore](https://hub.docker.com/r/microsoft/aspnetcore/)存放庫中，會使用可在 DockerHub 登錄。 功能過來運作時，從 Windows 主機提取此映像會提取 Windows variant，而從 Linux 主機提取相同的映像名稱將會提取 Linux variant。

***選項 b： 建立您從頭建立基底映像***

在此所述，您可以從頭建立您自己的 Docker 基礎映像[文章](https://docs.docker.com/engine/userguide/eng-image/baseimages/)從 Docker。 這是可能不是最適合您如果您剛開始使用 Docker 的案例，但如果您想要設定您自己的基底映像的特定位元，您可以執行。

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a>步驟 3： 建立自訂 Docker 映像嵌入您的服務

針對每個包含您的應用程式的自訂服務，您必須建立相關的映像。 如果您的應用程式組成的單一服務或 web 應用程式，您將需要一張圖片。

> [!NOTE]
> 考慮 「 外部迴圈 DevOps 工作流程 」，映像將會建立自動化的建置程序時您將來源程式碼推送至 Git 存放庫 （連續整合），因此會在全域環境中建立的映像從您原始程式碼。

但是，我們考慮移到該外部迴圈路由之前，我們需要確保 Docker 應用程式實際運作正常，讓它們不會推送程式碼，可能無法正常運作 （Git 等等），才會進行來源控制系統。

因此，每位開發人員第一次需要整個 「 內部迴圈 」 程序，在本機測試，並繼續開發，直到他們想要推送完整的功能或變更原始檔控制系統。

在您的本機環境中和使用 DockerFile 建立映像，您可以使用 docker build 命令，在圖 4-19 示 (您也可以執行 docker compose up--建置由數個容器/服務所組成的應用程式)。

![](./media/image25.png)

圖 4-19： 執行 docker 建置

（選擇性） 而不是直接執行 docker 建置的專案資料夾中，您第一次可以產生可部署的資料夾使用執行的 dotnet 發行命令，並執行 docker 建置所需的.NET 程式庫。

在此範例中，這會建立 Docker 映像名稱 cesardl/netcore webapi-微服務-docker： 第一個 (: 首先是標記，例如特定的版本)。 您可以採取此步驟中的每個您需要建立數個容器組成 Docker 應用程式的自訂映像。

您可以找到現有的映像在本機存放庫 （您的開發電腦） 使用 docker images 命令所示的 圖 4 到 20。

![](./media/image26.png)

圖 4 到 20： 檢視現有的映像使用 docker 映像

### <a name="step-4-optional-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a>步驟 4: （選擇性） 定義您的服務，在 docker-compose.yml 建置具有多個服務的組成的 Docker 應用程式時

使用 docker-compose.yml 檔案中，您可以定義一組相關的服務一起部署為組成的應用程式的下一個步驟一節所述的部署命令。

您必須建立該檔案在您的 main 或根解決方案資料夾;下列 docker compose.yml 檔案應該類似的內容：

```yml
version: '2'
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

-   建立從目前的目錄中的 DockerFile

-   轉送公開的連接埠 80 上的容器在主機電腦上的連接埠 81

-   讓您修改程式碼，而不需要重建映像的容器內的 /code 主機上掛接專案目錄

-   連結至 redis 服務的 web 服務

Redis 服務會使用[最新的公用 redis 映像](https://hub.docker.com/_/redis/)從 Docker Hub 登錄提取。 [redis](https://redis.io/)是伺服器端應用程式的非常受歡迎的快取系統。

### <a name="step-5-build-and-run-your-docker-app"></a>步驟 5： 建置並執行您的 Docker 應用程式

如果您的應用程式有單一容器，您只需要藉由將它部署至您的 Docker 主機 （VM 或實體伺服器） 執行它。 不過，如果您的應用程式多個服務組成，您需要*組合*也。 讓我們看到不同的選項。

***選項 a： 執行單一容器或服務***

您可以執行的 Docker 映像使用 docker run 命令，如下所示：

```
docker run -t -d -p 80:5000
cesardl/netcore-webapi-microservice-docker:first
```

請注意，針對此特定的部署，我們將會將要求重新導向傳送至連接埠 80 的內部連接埠 5000。 現在，應用程式正在接聽的外部連接埠 80，在主機層級。

***選項 b： 撰寫和執行多容器應用程式***

在大部分的企業案例中，將多個服務組成 Docker 應用程式。 在這些情況下，您可以執行命令 docker compose 設定 (圖 4-21)，它會使用您可能會有先前建立的 docker-compose.yml 檔案。 執行此命令會部署所有及其相關容器組成的應用程式。

![](./media/image27.png)

圖 4-21： 結果的執行 」 啟動 docker compose 」 命令

執行 docker 之後-docker-compose up，您將部署應用程式和其相關的容器到您的 Docker 主機中所示在圖 4-22，呈現的 VM。

![](./media/image28.png)

圖 4-22: VM 部署了 Docker 容器

附註啟動 docker compose 和 docker 執行可能不足以在您的開發環境中測試您的容器，但您可能完全不使用它們，如果您預期地使用 Docker 叢集和協調器，像是 Docker Swarm、 Mesosphere DC/OS 或 Kubernetes為了能夠相應增加。 如果您使用類似的叢集[Docker Swarm 模式](https://docs.docker.com/engine/swarm/)（可在 Docker for Windows 和 Mac 1.12 版之後），您需要部署及測試與其他命令，例如 docker 服務建立單一服務，或當您準備部署數個容器所組成的應用程式，搭配使用 docker compose bundle 及 docker 部署 myBundleFile，作為堆疊，部署組成的應用程式，如本文所述[分散式應用程式套件組合](https://blog.docker.com/2016/06/docker-app-bundle/)從 Docker。

針對[DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/)並[Kubernetes](https://kubernetes.io/docs/user-guide/deployments/#creating-a-deployment)您可以使用不同的部署命令和指令碼，以及。

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a>步驟 6： 測試您的 Docker 應用程式 （在本機，在您本機的 CD VM)

此步驟會因應用程式的執行。

非常簡單.NET Core Web API 中"Hello World"部署為單一容器或服務，您只需要提供 DockerFile 中指定的 TCP 連接埠來存取服務。

如果 localhost 未開啟，以瀏覽至您的服務，尋找電腦的 IP 位址，使用下列命令：

docker 機器 ip*您的容器名稱*

在 Docker 主機上，開啟瀏覽器並瀏覽至該網站;圖 4-23 示，應該會看到執行中，您的應用程式/服務。

![](./media/image29.png)

圖 4-23： 測試使用 localhost 在本機的 Docker 應用程式

請注意，它使用連接埠 80，但在內部它已被重新導向至連接埠 5000，因為這是它的部署方式使用 docker 執行時，如先前所述。

您可以從終端機使用 CURL 來測試。 在 Docker 安裝在 Windows 中，預設值是 IP 10.0.75.1，如上圖中圖 4-24。

![](./media/image30.png)

圖 4-24： 由使用 CURL 在本機測試 Docker 應用程式

**偵錯在 Docker 上執行的容器**

Visual Studio Code 支援偵錯的 Docker，如果您使用 Node.js 和.NET Core 容器等其他平台。

您也可以偵錯在 Docker 中的.NET Core 容器時使用 Visual Studio 中下, 一節中所述。

**更多資訊：** 若要深入了解偵錯 Node.js Docker 容器，請前往<https://blog.docker.com/2016/07/live-debugging-docker/>並[https://blogs.msdn.microsoft.com/\使用者\_ed/2016年/02/27 /visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/](https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/)。


>[!div class="step-by-step"]
[上一頁](docker-apps-development-environment.md)
[下一頁](visual-studio-tools-for-docker.md)
