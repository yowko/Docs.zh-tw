---
title: "建置 .NET Core Docker 映像"
description: "了解 Docker 映像和 .NET Core"
keywords: ".NET、.NET Core、Docker"
author: spboyer
manager: wpickett
ms.date: 08/29/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 03c28597-7e73-46d6-a9c3-f9cb55642739
translationtype: Human Translation
ms.sourcegitcommit: 1cb9e19ec9c9c0764244aeec5f62b812cbd91aef
ms.openlocfilehash: 8cc784c267e9ca85ae110f8c92e0191f6fee6596

---
 

#<a name="building-docker-images-for-net-core-applications"></a>建置 .NET Core 應用程式的 Docker 映像

為了解如何同時使用 .NET Core 和 Docker，我們必須先了解取得的不同 Docker 映像，以及正確的使用時機。 在此，我們會逐步解說所獲得的變化、建置 ASP.NET Core Web API、使用 Yeoman Docker 工具建立可偵錯的容器，以及預覽 Visual Studio Code 如何在程序中提供協助。 

## <a name="docker-image-optimizations"></a>Docker 映像最佳化

在建置開發人員的 Docker 映像時，我們會著重在三個主要案例︰

- 用來開發 .NET Core 應用程式的映像
- 用來建置 .NET Core 應用程式的映像
- 用來執行 .NET Core 應用程式的映像

為何是三個映像？
在開發、建置及執行放入容器的應用程式時，我們有不同的優先考量。
- **開發︰**逐一查看變更的速度以及偵錯變更的能力。 映像大小不那麼重要，而是變更及查看程式碼的速度。 我們有些工具，像是用於 VS Code 的 [yo docker](https://aka.ms/yodocker)，會在開發期間使用此映像。 
- **建置︰**編譯應用程式需要的內容。 這包括編譯器和任何其他可最佳化二進位檔的相依性。 此映像不是您部署的映像，而是您用來建置實際執行映像內容的映像。 此映像可用於連續整合或建置環境。 例如，不是直接在組建代理程式上安裝所有相依性，組建代理程式會引證建置映像，使用有建置映像內含應用程式所需的全部相依性，來編譯應用程式。 組建代理程式只需要知道如何執行此 Docker 映像。 
- **生產環境︰**多快可以部署及啟動映像。 此映像很小，因此它可以快速地從 Docker 登錄到 Docker 主機在網路上傳輸。 準備好執行的內容可用最短的時間完成 Docker 執行到處理結果。 在不可變的 Docker 模型中，沒必要動態編譯程式碼。 您放置在此映像中的內容會限於執行應用程式所需的二進位檔和內容。 例如，已發行輸出使用的 `dotnet publish` 包含已編譯的二進位檔、映像、.js 和 .css 檔案。 經過一段時間，您會看到包含預先 JIT 編譯封裝的映像。  

雖然有多種版本的 .NET Core 映像，但它們全都共用一或多個圖層。 儲存所需的磁碟空間量，或從登錄提取的差異，遠小於整體，因為所有的映像共用相同的基底層，可能還有其他層。  

## <a name="docker-image-variations"></a>Docker 映像變化

為達成上述目標，我們在 [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) 下提供映像變體。

- `microsoft/dotnet:<version>-sdk`：也就是 **microsoft/dotnet:1.0.0-preview2-sdk**，此映像包含具有 .NET Core 及命令列工具 (CLI) 的 .NET Core SDK。 此映像會對應至**開發案例**。 您可以使用此映像處理本機開發、偵錯和單元測試。 例如，所有的開發都要先於簽入程式碼。 此映像也可用於**建置**案例。

- `microsoft/dotnet:<version>-core`︰也就是 **microsoft/dotnet:1.0.0-core**，此映像會執行[可攜式 .NET Core 應用程式](../deploying/index.md)，並為了在**生產環境**中執行應用程式而經過最佳化。 它不包含 SDK，且表示要採用最佳化的 `dotnet publish` 輸出。 可攜式執行階段非常適合 Docker 容器案例，因為執行多個容器可從共用的映像圖層中得益。  

## <a name="alternative-images"></a>替代的映像

除了開發、建置和生產環境的最佳化案例，我們還提供其他映像︰

- `microsoft/dotnet:<version>-onbuild`︰也就是 **microsoft/dotnet:1.0.0-preview2-onbuild**，包含 [ONBUILD](https://docs.docker.com/engine/reference/builder/#/onbuild) 觸發程序。 組建會[複製](https://docs.docker.com/engine/reference/builder/#/copy)應用程式，執行 `dotnet restore` 並建立 [進入點](https://docs.docker.com/engine/reference/builder/#/entrypoint) `dotnet run` 指示，在執行 Docker 映像時執行應用程式。 至於未最佳化的生產環境映像，有些人可能會覺得它很有用，因為只要將原始程式碼複製到映像並執行即可。 

- `microsoft/dotnet:<version>-core-deps`︰也就是 **microsoft/dotnet:1.0.0-core-deps**，如果想要執行自封式應用程式，請使用此映像。 它包含作業系統及 .NET Core 所需的所有原生相依性。 此映像也可用為您自己自訂的 CoreFX 或 CoreCLR 組建的基礎映像。 雖然 **onbuild** 變體經過最佳化後，只需將程式碼放入映像並執行即可，但此映像經過最佳化後，只讓所需的作業系統相依性執行將 .NET 執行階段和應用程式封裝在一起的 .NET Core 應用程式。 此映像通常不會為在相同的主機上執行多個 .NET Core 容器而最佳化，因為每個映像在應用程式內都會攜帶 .NET Core 執行階段，而您不會得益於映像圖層。   

每個變體的最新版本︰

- `microsoft/dotnet:latest` 或 `microsoft/dotnet` (包括 SDK)
- `microsoft/dotnet:onbuild`
- `microsoft/dotnet:core`
- `microsoft/dotnet:core-deps`

以下是開發電腦上的 `docker pull <imagename>` 顯示各種大小後的映像清單。 請注意，開發/建置變體 `microsoft/dotnet:1.0.0-preview2-sdk` 較大，因為它包含開發和建置應用程式的 SDK。 生產環境變體 `microsoft/dotnet:core` 較小，因為它只包含 .NET Core 執行階段。 能夠在 Linux 上使用的最小映像 `core-deps` 相當小，但您的應用程式需要用它複製 .NET 執行階段的私用複本。 因為容器已經是私人的隔離障礙，所以在執行多個 dotnet 型的容器時會遺失最佳化。 

```
REPOSITORY          TAG                     IMAGE ID            SIZE
microsoft/dotnet    1.0.0-preview2-onbuild  19b6a6c4b1db        540.4 MB
microsoft/dotnet    onbuild                 19b6a6c4b1db        540.4 MB
microsoft/dotnet    1.0.0-preview2-sdk      a92c3d9ad0e7        540.4 MB
microsoft/dotnet    core                    5224a9f2a2aa        253.2 MB
microsoft/dotnet    1.0.0-core-deps         c981a2eebe0e        166.2 MB
microsoft/dotnet    core-deps               c981a2eebe0e        166.2 MB
microsoft/dotnet    latest                  03c10abbd08a        540.4 MB
microsoft/dotnet    1.0.0-core              b8da4a1fd280        253.2 MB
```

## <a name="prerequisites"></a>必要條件

若要建置並執行，您需要安裝幾個項目︰

- [.NET Core](http://dot.net)
- [Docker](https://www.docker.com/products/docker)：在本機執行 Docker 容器 
- [ASP.NET Yeoman 產生器](https://github.com/omnisharp/generator-aspnet)：建立 Web API 應用程式
- [Docker Yeoman 產生器](http://aka.ms/yodocker)：來自 Microsoft

使用 npm 安裝 ASP.NET Core 和 Docker 的 Yeoman 產生器 

```
npm install -g yo generator-aspnet generator-docker
```

> [!NOTE]
> 這個範例會使用 [Visual Studio Code](http://code.visualstudio.com) 當作編輯器。

## <a name="creating-the-web-api-application"></a>建立 Web API 應用程式

針對參考點，在將應用程式放入容器前，要先在本機執行應用程式。 

完成的應用程式位於 [GitHub 上的 dotnet/core-docs 儲存機制](https://github.com/dotnet/docs/tree/master/samples/core/docker/building-net-docker-images)。

建立應用程式的目錄。

在該目錄中開啟命令或終端機工作階段，並輸入下列內容使用 ASP.NET Yeoman 產生器︰
```
yo aspnet
```

選取 [Web API 應用程式] 並在應用程式名稱輸入 **api**，然後點選 Enter。  應用程式建立結構後，請變更至 `/api` 目錄，並使用 `dotnet restore` 還原 NuGet 相依性。

```
cd api
dotnet restore
```

使用 `dotnet run` 並瀏覽至 **http://localhost:5000/api/values** 測試應用程式

```javascript
[
    "value1",
    "value2"
]
```

使用 `Ctrl+C` 停止應用程式。

## <a name="adding-docker-support"></a>新增 Docker 支援

使用來自 Microsoft 的 Yeoman 產生器可將 Docker 支援加入專案。 目前，它透過建立協助在容器內建置和執行專案的 Dockerfile 和指令碼，支援 .NET Core、Node.js 和 Go 專案。 也會加入 Visual Studio Code 特定檔案 (launch.json、tasks.json) 供編輯器偵錯和命令調色盤支援。

```console
$ yo docker

     _-----_     ╭──────────────────────────╮
    |       |    │   Welcome to the Docker  │
    |--(o)--|    │        generator!        │
   `---------´   │     Let's add Docker     │
    ( _´U`_ )    │  container magic to your │
    /___A___\   /│           app!           │
     |  ~  |     ╰──────────────────────────╯
   __'.___.'__
 ´   `  |° ´ Y `

? What language is your project using? (Use arrow keys)
❯ .NET Core
  Golang
  Node.js

```

- 選取 `.NET Core` 作為專案類型
- `rtm` 為 .NET Core 版本
- `Y` 是使用網頁伺服器的專案
- `5000` 是 Web API 應用程式接聽中的連接埠 (http://localhost:5000/)
- `api` 為映像名稱
- `api` 為服務名稱
- `api` 為撰寫專案 
- `Y` 會覆寫目前的 Dockerfile

產生器完成時，下列檔案會加入專案中

- .vscode/launch.json
- Dockerfile.debug
- Dockerfile
- docker-compose.debug.yml
- docker-compose.yml
- dockerTask.ps1
- dockerTask.sh
- .vscode/tasks.json

產生器會建立兩個 Dockerfile。

**Dockerfile.debug**：這個檔案是以 **microsoft/dotnet:1.0.0-preview2-sdk** 映像為基礎，如果您注意到，它是出自映像變體清單，包括 SDK、CLI 和 .NET Core，而且會是開發和偵錯 (F5) 所用的映像。 包括所有這些元件會產生較大的映像，大小約為 540 MB。

**Dockerfile**：此映像是以 **microsoft/dotnet:1.0.0-core** 為基礎的發行映像，應該用於生產環境。 此映像在建置時約為 253 MB。

### <a name="creating-the-docker-images"></a>建立 Docker 映像
使用 `dockerTask.sh` 或 `dockerTask.ps1` 指令碼，我們可以針對特定的環境建置或撰寫 **api** 應用程式的映像和容器。 執行下列命令以建置**偵錯**映像。

```bash
./dockerTask.sh build debug
```

此映像會建置 ASP.NET 應用程式、執行 `dotnet restore`、將偵錯工具加入映像、設定 `ENTRYPOINT`，最後將應用程式複製到映像。 結果是名為 *api* 的 Docker 映像，附帶「偵錯」的 `TAG`。  請使用 `docker images` 查看電腦上的映像。

```bash
docker images

REPOSITORY          TAG                  IMAGE ID            CREATED             SIZE
api                 debug                70e89fbc5dbe        a few seconds ago   779.8 MB
```

產生映像並在 Docker 容器內執行應用程式的另一個方法，是在 Visual Studio Code 中開啟應用程式，並使用偵錯工具。 

在 VS Code 左側的 [檢視] 列中選取偵錯圖示。

![vscode 偵錯圖示](./media/building-net-docker-images/debugging_debugicon.png)

然後點選播放圖示或 F5 產生映像，在容器內啟動應用程式。 Web API 會使用您在 http://localhost:5000 的預設網頁瀏覽器啟動。

![VSCode Docker 工具偵錯](./media/building-net-docker-images/docker-tools-vscode-f5.png)

您可在應用程式、逐步執行等等設定中斷點，就像在開發電腦本機執行應用程式，而不是在容器內。 在容器內偵錯的優點是，這是會部署到生產環境的同一映像。

建立發行或生產環境映像，只需要從終端機執行命令，傳遞 `release` 環境名稱。

```bash
./dockerTask build release
```

此命令會根據較小的 **microsoft/dotnet:core** 基礎映像建立映像、[EXPOSE](https://docs.docker.com/engine/reference/builder/#/expose) 連接埠 5000、設定 `dotnet api.dll` 的 [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint)，再將它複製到 `/app` 目錄。 不會有任何偵錯工具、SDK 或 `dotnet restore` 產生更小的映像。 此映像名為 **api**，附帶**最新的**的 `TAG`。

```
REPOSITORY          TAG                  IMAGE ID            CREATED             SIZE
api                 debug                70e89fbc5dbe        1 hour ago        779.8 MB
api                 latest               ef17184c8de6        1 hour ago        260.7 MB
```

## <a name="summary"></a>總結

使用 Docker 產生器將必要的檔案新增至 Web API 應用程式，曾經讓建立開發和生產環境版本映像的程序變得簡單。  這項工具之所以能夠跨平台，是因為它也提供 PowerShell 指令碼來達成，在提供於容器內逐步偵錯應用程式的 Windows 和 Visual Studio 整合中達到相同的結果。 透過了解映像變體和目標案例，您可以最佳化內部迴圈開發程序，同時達到最佳化生產環境部署的映像。  





<!--HONumber=Nov16_HO3-->


