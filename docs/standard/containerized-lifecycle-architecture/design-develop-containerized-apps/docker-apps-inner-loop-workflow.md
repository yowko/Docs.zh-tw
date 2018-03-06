---
title: "Docker 應用程式的內部迴圈的開發工作流程"
description: "Microsoft 平台和工具的容器化 Docker 應用程式生命週期"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 632c04507c1478238a5dc2573542f8c88bae2a51
ms.sourcegitcommit: c3957fdb990060559d73cca44ab3e2c7b4d049c0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2018
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a>Docker 應用程式的內部迴圈的開發工作流程

觸發跨越整個 DevOps 外部迴圈工作流程之前循環，所有開始每位開發人員在電腦上，撰寫程式碼應用程式本身、 使用其偏好的語言或平台，以及在本機測試它 (圖 4-14)。 但在每個案例中，您會有一點很重要共通點，無論您選擇何種語言、 架構或平台。 在此特定的工作流程，您一律開發和測試 Docker 容器，但只能在本機。

![](./media/image18.png)

圖 4-14： 內部迴圈開發內容

容器或 Docker 映像的執行個體將會包含這些元件：

-   作業系統的選取範圍 （例如 Linux 散發套件或 Windows）

-   加入的開發人員 （例如，應用程式二進位檔） 檔案

-   設定 （例如，環境設定和相依性）

-   若要執行 Docker 哪些處理程序指示

您可以設定為 （下一節中所述） 的程序會利用 Docker 內部迴圈開發工作流程。 考慮設定環境的初始步驟不包含在內，因為您需要這樣做，就可以一次。

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a>建置 Visual Studio 程式碼和 Docker CLI 使用 Docker 容器內的單一應用程式

應用程式會啟動從您的服務，再加上額外的程式庫 （相依性）。

圖 4-15 會顯示您通常需要時建置 Docker 應用程式，後面接著每個步驟的詳細描述執行的基本步驟。

![](./media/image19.png)

圖 4-15： 使用 Docker CLI Docker 容器化應用程式生命週期的高層級工作流程

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a>步驟 1： 開始撰寫程式碼在 Visual Studio 程式碼中，並建立初始應用程式/服務基準

開發應用程式的方式是不 Docker 的方式很類似。 差別在於，在開發時，會在部署並測試您的應用程式或放在本機環境 （例如 Linux VM 或 Windows） 的 Docker 容器內執行的服務。

**設定您的本機環境**

Docker for Mac 和 Windows 的最新版本，比以往若要開發 Docker 應用程式，更輕鬆與安裝程式將更為簡單。

**進一歩** 如需有關設定 Docker for Windows 的指示，請移至[https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/)。

如需 Docker for Mac 設定指示，請移至<https://docs.docker.com/docker-for-mac/>。

此外，您必須在程式碼編輯器，讓您實際上可以開發的應用程式使用 Docker CLI。

Microsoft 提供 Visual Studio 程式碼，其中是輕量型的程式碼編輯器支援 Mac、 Windows 和 Linux 上並提供 IntelliSense[多語言支援](https://code.visualstudio.com/docs/languages/overview)(JavaScript、.NET、 Go、 Java、 Ruby、 Python 和大部分現代的語言），[偵錯](https://code.visualstudio.com/Docs/editor/debugging)，[與 Git 整合](https://code.visualstudio.com/Docs/editor/versioncontrol)和[延伸模組支援](https://code.visualstudio.com/docs/extensions/overview)。 此編輯器是適用於 Mac 和 Linux 的開發人員的絕佳符合。 在 Windows 中，您也可以使用完整的 Visual Studio 應用程式。

**進一歩** 如需安裝 Visual Studio for Windows、 Mac 或 Linux 的指示，請移至[http://code.visualstudio.com/docs/setup/setup-overview/https://docs.docker.com/docker-for-mac/](http://code.visualstudio.com/docs/setup/setup-overview/https:/docs.docker.com/docker-for-mac/)。

您可以使用 Docker CLI，並撰寫程式碼，使用任何程式碼編輯器 中，但如果您使用 Visual Studio 程式碼，它可以輕鬆地撰寫 Dockerfile 和 docker compose.yml 檔案工作區中。 此外，您可以從 IDE，以提示可以執行複雜的作業使用 Docker CLI 底下的指令碼執行 Visual Studio 程式碼工作。

Visual Studio 程式碼係由延伸模組，您必須安裝。 若要這樣做，請按 Ctrl + Shift + P，輸入**ext 安裝**，然後執行 延伸模組： 安裝延伸模組命令，以顯示 Marketplace 擴充功能清單。 接著，輸入**docker**來篩選結果，然後選取 Dockerfile 和 Docker 撰寫檔案 (yml) 支援擴充功能，如圖 4-16。

![](./media/image20.png)

圖 4-16： 安裝 Visual Studio 程式碼中的 Docker 擴充功能

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a>步驟 2： 建立 DockerFile，現有的映像 （純文字的 OS 或開發環境，例如.NET Core、 Node.js 和 Ruby） 相關

您需要 DockerFile 每個要建置自訂的影像和每個要部署的容器，因此，如果您的應用程式由單一的自訂服務所組成，您將需要單一 DockerFile。 但是，如果您的應用程式所組成 （如同 microservices 架構） 的多個服務，您將需要每個服務的一個 Dockerfile。

DockerFile 通常會放在應用程式或服務的根資料夾內，並包含所需的命令，讓該 Docker 知道如何設定及執行該應用程式或服務。 您可以建立 DockerFile，並將它加入至您的專案中，以及您的程式碼 (.NET Core node.js 等等)，或如果您不熟悉的環境，看看下列提示。

> [!TIP]
> 您可以使用命令列工具，稱為[yo docker](https://github.com/Microsoft/generator-docker)，其中 scaffold 從您的專案，在您選擇的語言新增必要的 Docker 組態檔中的檔案。 基本上，來協助開發人員快速入門，它會建立適當的 DockerFile 中，docker compose.yml 和其他相關聯的指令碼，以建置並執行 Docker 容器。 此 yeoman 產生器會提示您要求您選取的開發語言和目的地容器主機的幾個問題。

![yo docker](./media/image21.png)

比方說，圖 4-17 顯示兩個螢幕擷取畫面，將終端機視窗中，以及在 Mac 上，在這兩種情況下，執行 yo docker，將會產生的範例程式碼專案 （目前.NET Core、 Golang 和支援的語言為 Node.js） 已設定成使用Docker 的頂端。

![](./media/image22.PNG)  ![](./media/image23.png)

圖 4-17: yo docker 命令在 Windows 中 （左），並在 Mac 上的工具

圖 4-18 顯示 yo docker 後使用您已有現有的.NET Core 專案會建立結構的範例。

![](./media/image24.PNG)

圖 4-18: yo docker 與現有的.NET Core 專案中的位置

DockerFile 中，從您指定哪些基底的 Docker 映像，選擇您要使用 （例如使用 從 microsoft/dotnet:1.0.0-core"）。 您通常會建置您自訂的映像，您可以從任何正式儲存機制取得基底映像之上[Docker Hub 登錄](https://hub.docker.com/)(像是[適用於.NET Core 的映像](https://hub.docker.com/r/microsoft/dotnet/)或一個[for Node.js](https://hub.docker.com/_/node/)).

***選項 a： 使用現有的官方 Docker 映像***

使用版本號碼為語言堆疊官方儲存機制可確保可以相同的語言功能 （包括開發、 測試和生產環境） 的所有電腦上。

以下是範例 DockerFile.NET Core 容器：

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

在此情況下，它適用於 Linux 名為 microsoft/aspnetcore:1.0.1 使用 1.0.1 版的官方 ASP.NET Core Docker 映像。 如需詳細資訊，請參閱[ASP.NET Core Docker 映像頁面](https://hub.docker.com/r/microsoft/aspnetcore/)和[.NET Core Docker 映像頁面](https://hub.docker.com/r/microsoft/dotnet/)。 您也可以使用另一個可比較像的映像節點： 4-Node.js 或開發語言，可從許多其他預先設定的影像 onbuild [Docker Hub](https://hub.docker.com/explore/)。

在 DockerFile 中，您也需要會指示 Docker 以接聽 TCP 通訊埠，您將使用在執行階段 （例如連接埠 80）。

有其他您可以根據您使用的語言/架構 DockerFile 中新增讓 Docker 知道如何執行應用程式的組態中的行。 例如，您需要的進入點線條\["dotnet"，"MyCustomMicroservice.dll"\]執行是.NET Core 應用程式中，雖然您可以根據要建置並執行您的服務方法的多個變異。 如果您使用的 SDK 和 dotnet CLI 建置並執行.NET 應用程式，它會稍有不同。 營收是進入點的行，加上額外的線條將會根據您選擇您的應用程式的語言/平台而不同。

**進一歩** 建置.NET Core 應用程式的 Docker 映像的相關資訊，請移至<https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>。

若要了解如何建置自己的映像，請前往[https://docs.docker.com/engine/ \ 教學課程/dockerimages/](https://docs.docker.com/engine/tutorials/dockerimages/)。

**多平台映像儲存機制**

由於 Windows 容器變得更普遍的單一的存放庫可包含平台的變異，例如的 Linux 和 Windows 映像。 這是一項新功能，可讓廠商使用單一的儲存機制以涵蓋多個平台，例如 Docker 的未來[microsoft/aspdotnetcore](https://hub.docker.com/r/microsoft/aspnetcore/)儲存機制，會使用可在 DockerHub 登錄。 功能都運作時，從 Windows 主機提取此映像將會提取 Windows 的變體，而在 Linux 主機從提取相同的映像名稱將會提取 Linux variant。

***選項 b： 建立您從頭的基底映像***

您可以從頭開始建立您自己的 Docker 基底映像中所述[文章](https://docs.docker.com/engine/userguide/eng-image/baseimages/)從 Docker。 這是不可能最適合您如果您剛開始使用 Docker 的案例，但如果您想要設定特定的位元基底映像，您可以這麼做。

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a>步驟 3： 建立您自訂的 Docker 映像嵌入您的服務

針對每個包含您的應用程式的自訂服務，您必須建立相關的映像。 如果您的應用程式所組成的單一服務或 web 應用程式，您必須只以單一影像。

> [!NOTE]
> 不顧及 「 外部迴圈 DevOps workflow"，影像將會建立由自動化的建置處理序時就是您推送您的程式碼至 Git 儲存機制 （連續整合） 因此會在全域環境中建立映像從您原始程式碼。

但是，我們認為該外部迴圈路由時，將之前，我們需要確定 Docker 應用程式實際上運作正常，讓它們不發送可能無法正常運作 （Git 等等） 時，原始檔控制系統的程式碼。

因此，每位開發人員第一次需要進行整個內部迴圈處理序，在本機測試，並繼續開發，直到他們想要推送的完整功能，或變更原始檔控制系統。

若要在本機環境和使用 DockerFile 建立映像，您可以使用 docker 建置命令中，示圖 4-19 (您也可以執行 docker 撰寫向上-由數個的容器服務組成的應用程式的組建)。

![](./media/image25.png)

圖 4-19： 執行 docker 建置

（選擇性） 而不是直接執行 docker 來建立專案的資料夾，則第一次可以產生可部署的資料夾與使用執行的 dotnet 發行命令，然後再執行 docker 建置所需的.NET 程式庫。

在此範例中，這會建立 Docker 映像名稱 cesardl/netcore-webapi-微服務-docker： 第一個 (: 第一個是標記，例如特定的版本)。 您可以採取此步驟，您必須建立數個容器與 Docker 組成應用程式的每個自訂映像。

您可以找到現有的映像在本機儲存機制 （在開發電腦） 中使用 docker 映像命令的說明圖 4-20。

![](./media/image26.png)

圖 4-20： 檢視現有的映像使用 docker 映像

### <a name="step-4-optional-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a>步驟 4: （選擇性） 定義 docker compose.yml 時建置含有多個服務組成的 Docker 應用程式中的服務

使用 docker compose.yml 檔案中，您可以定義一組相關的服務一起部署為組成的應用程式的下一個步驟中說明的部署命令。

您必須建立該檔案在您的 main 或根方案資料夾。下列 docker compose.yml 檔案應該類似的內容：

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

在此特定情況下，此檔案會定義兩個服務： web 服務 （您自訂的服務） 和 redis 服務 （熱門的快取服務）。 將當做容器時，部署每個服務，因此我們必須針對每個使用具體的 Docker 映像。 此特定 web 服務、 映像必須執行下列作業：

-   從目前目錄中 DockerFile 建置

-   轉送公開的連接埠 80 上的容器主機上的連接埠 81

-   讓您修改程式碼，而不必重建映像容器內的 /code 在主機上裝載專案目錄

-   連結至 redis 服務的 web 服務

Redis 服務會使用[最新的公用 redis 映像](https://hub.docker.com/_/redis/)提取從 Docker Hub 登錄。 [redis](http://redis.io/)是非常普遍的快取系統的伺服器端應用程式。

### <a name="step-5-build-and-run-your-docker-app"></a>步驟 5： 建置並執行您的 Docker 應用程式

如果您的應用程式具有單一容器，您只需要執行，請將它部署至您的 Docker 主機 （VM 或實體伺服器）。 不過，如果您的應用程式由多個服務所組成，您需要*撰寫*、 太。 我們來看看不同的選項。

***選項 a： 執行單一容器或服務***

您可以執行的 Docker 映像使用 docker run 命令，如下所示：

```
docker run -t -d -p 80:5000
cesardl/netcore-webapi-microservice-docker:first
```

請注意，針對此特定的部署，我們會重新導向要求傳送至連接埠 80 的內部連接埠為 5000。 現在，應用程式正在接聽的外部連接埠 80，主機層級。

***選項 b： 撰寫和執行多個容器應用程式***

在大部分的企業案例中，Docker 應用程式將由多個服務。 這些情況下，您可以執行命令，docker 撰寫向上 (圖 4-21)，就會使用您可能會有先前建立的 docker compose.yml 檔案。 執行此命令會將部署組成的應用程式與它的所有相關容器。

![](./media/image27.png)

圖 4-21： 執行"docker-撰寫"命令的結果

在執行 docker 之後-向上撰寫，您將應用程式和其相關的容器到您的 Docker 主機中所示在圖 4-22，VM 表示法。

![](./media/image28.png)

圖 4-22: VM 部署的 Docker 容器

注意 docker-撰寫向上 docker 執行可能不足以在您的開發環境中測試您的容器，但您可能不會使用它們完全如果您想要使用 Docker 群集，而且 orchestrators 像 Docker Swarm、 Mesosphere DC/作業系統或 Kubernetes若要能夠向上延展。 如果您使用類似的叢集[Docker Swarm 模式](https://docs.docker.com/engine/swarm/)（適用於 Docker for Windows 和 Mac 版本 1.12 之後），您需要部署和測試與其他命令，例如，docker 服務建立單一服務，或當您準備部署數個容器所組成的應用程式，使用 docker 撰寫組合和 docker 來組成的應用程式部署為堆疊，發行項中所述部署 myBundleFile，[分散式應用程式套件組合](https://blog.docker.com/2016/06/docker-app-bundle/)從 Docker。

如[DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/)和[Kubernetes](http://kubernetes.io/docs/user-guide/deployments/#creating-a-deployment)您會使用不同的部署命令和指令碼，以及。

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a>步驟 6： 測試您的 Docker 應用程式 （在本機，在您本機的 CD VM)

此步驟會因您的應用程式正在執行。

在非常簡單.NET Core Web 應用程式開發介面"Hello World"部署為單一容器或服務，您只需要提供 DockerFile 中指定的 TCP 連接埠來存取服務。

如果 localhost 未開啟，瀏覽至您的服務，尋找電腦的 IP 位址，使用這個命令：

docker 機器 ip*您的容器名稱*

Docker 主機上，開啟瀏覽器並瀏覽至該網站。您應該會看到您的應用程式/服務執行，如圖 4-23 所示範。

![](./media/image29.png)

圖 4-23： 測試 Docker 應用程式在本機使用 localhost

請注意，它會使用通訊埠 80，內部它已被重新導向到 5000 之間，因為它的部署方式執行時，docker 稍早所述。

您可以使用 CURL 從終端機來測試。 在 Windows 上的 Docker 安裝，預設是 IP 10.0.75.1，如上圖 4-24。

![](./media/image30.png)

圖 4-24： 由使用 CURL 在本機測試 Docker 應用程式

**偵錯執行 docker 容器**

如果您使用 Node.js 和.NET Core 容器等其他平台，visual Studio 程式碼支援偵錯的 Docker。

您也可以偵錯.NET Core 容器在 Docker 中的使用 Visual Studio 中下, 一節中所述。

**更多資訊：** 若要了解有關偵錯 Node.js Docker 容器的詳細資訊，請移至<https://blog.docker.com/2016/07/live-debugging-docker/>和[https://blogs.msdn.microsoft.com/ \ 使用者\_ed/2016年/02/27 /visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/](https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/)。


>[!div class="step-by-step"]
[Previous] (docker-apps-development-environment.md) [Next] (visual-studio-tools-for-docker.md)
