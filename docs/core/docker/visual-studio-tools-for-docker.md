---
title: Visual Studio Tools for Docker
description: "使用 Visual Studio Tools for Docker"
keywords: .NET, .NET Core, Docker, ASP.NET Core, Visual Studio
author: spboyer
ms.author: shboyer
ms.date: 04/27/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: dotnet
ms.assetid: 1f3b9a68-4dea-4b60-8cb3-f46164eedbbf
ms.translationtype: HT
ms.sourcegitcommit: 9bb17207ba72bb22f5d6db55e9d1bd77e3013445
ms.openlocfilehash: 113d470a55fd92704de0e6def392a6e0a1a3a118
ms.contentlocale: zh-tw
ms.lasthandoff: 08/25/2017

---

# <a name="visual-studio-tools-for-docker"></a>Visual Studio Tools for Docker

[Microsoft Visual Studio 2017](https://www.visualstudio.com/) (含 [Docker for Windows](https://docs.docker.com/docker-for-windows/install/)) 支援使用 Windows 和 Linux 容器來建置、偵錯與執行 .NET Framework 及 .NET Core Web 和主控台應用程式。

## <a name="prerequisites"></a>必要條件

- 含 .NET Core 工作負載的 [Microsoft Visual Studio 2017](https://www.visualstudio.com/)
- [Docker for Windows](https://docs.docker.com/docker-for-windows/install/)

## <a name="installation-and-setup"></a>安裝和設定

安裝含 .NET Core 工作負載的 [Microsoft Visual Studio 2017](https://docs.microsoft.com/en-us/visualstudio/install/install-visual-studio)。

若要安裝 Docker，請檢閱 [Docker for Windows: What to know before you install](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install) (Docker for Windows：安裝須知) 的資訊，並安裝 [Docker For Windows](https://docs.docker.com/docker-for-windows/install/)。

必要的設定是在 Docker for Windows 中安裝**[共用磁碟機](https://docs.docker.com/docker-for-windows/#shared-drives)**。 這對磁碟區對應及偵錯支援是必要的設定。

以滑鼠右鍵按一下系統匣中的 Docker 圖示，按一下 [設定] 並選取 [共用磁碟機]。 選取 Docker 儲存檔案所在的磁碟機，並套用變更。

![共用磁碟機](./media/visual-studio-tools-for-docker/settings-shared-drives-win.png)

## <a name="create-an-aspnet-web-application-and-add-docker-support"></a>建立 ASP.NET Web 應用程式並新增 Docker 支援

使用 Visual Studio 建立新的 ASP.NET Core Web 應用程式。 載入應用程式時，從 [專案] 功能表選取 「Add Docker Support」 (新增 Docker 支援)，或在方案總管中的專案上按一下滑鼠右鍵，選取 [新增] > [Docker Support] 「Docker 支援」。

[專案] 功能表

![[專案] 「Add Docker Support」 (新增 Docker 支援)](./media/visual-studio-tools-for-docker/project-add-docker-support.png)

[專案] 內容功能表

![以滑鼠右鍵按一下 「Add Docker Support」 (新增 Docker 支援)](./media/visual-studio-tools-for-docker/right-click-add-docker-support.png)

將 Docker 支援加入您的專案時，可以選擇 Windows 或 Linux 容器。 (Docker 主機必須執行相同的容器類型。 如果您需要變更執行中 Docker 執行個體內的容器類型，請以滑鼠右鍵按一下系統匣中的 [Docker] 圖示，選擇 [切換到 Windows 容器] 或 [切換至 Linux 容器])。 

下列檔案即會加入專案中。

- **Dockerfile**：ASP.NET Core 應用程式的 Docker 檔案是以 [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore) 映像為基礎。 此映像包含 ASP.NET Core NuGet 封裝，已經過預先 JIT 編譯改善啟動效能。 建置 .NET Core 主控台應用程式時，Dockerfile FROM 會參考最新的 [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet) 映像。   
- **docker-compose.yml**︰基礎 Docker Compose 檔案，用於定義要使用 docker-compose build/run 建置及執行的映像集合。   
- **docker-compose.dev.debug.yml**︰當組態設定為偵錯時，其他具有反覆變更的 docker-compose 檔案。 Visual Studio 會呼叫 -f docker-compose.yml -f docker-compose.dev.debug.yml 將這些合併到一起。 這是 Visual Studio 開發工具使用的 compose 檔案。   
- **docker-compose.dev.release.yml**：偵錯版本定義的其他 Docker Compose 檔案。 它會以磁碟區掛接方式掛接偵錯工具，這樣就不會變更生產環境映像的內容。  

docker-compose.yml 檔案包含執行專案時所建立的映像名稱。 

```
version '2'

services:
  hellodockertools:
    image:  user/hellodockertools${TAG}
    build:
      context: .
      dockerfile: Dockerfile
    ports:
      - "80"
``` 

在本例中，當應用程式在 **偵錯**模式中執行，而 `user/hellodockertools:latest` 在**發行**模式中執行時，`image: user/hellodockertools${TAG}` 會產生映像 `user/hellodockertools:dev`。 

如果您打算將映像推送至登錄，您會想要將 `user` 變更為您的 Docker Hub 使用者名稱。 例如，`spboyer/hellodockertools`，或變更為私用登錄 URL `privateregistry.domain.com/`，視您的設定而定。

### <a name="debugging"></a>偵錯

從工具列的 [偵錯] 下拉式清單中選取 [Docker]，再使用 F5 開始偵錯應用程式。 

- 即取得 microsoft/aspnetcore 映像 (快取中若無)
- ASPNETCORE_ENVIRONMENT 在容器內設為 [開發]
- PORT 80 為 EXPOSED，且對應至本機主機的動態指派連接埠。 連接埠是由銜接站主機決定，可以使用 docker ps 進行查詢。 
- 您的應用程式會複製到容器
- 預設瀏覽器會和附加至容器的偵錯工具一起啟動，使用動態指派的連接埠。 

產生的 Docker 映像組建是應用程式的 `dev` 映像，以 `microsoft/aspnetcore` 映像為基礎映像。
注意︰應用程式內容的 dev 映像是空的，因為 [偵錯] 設定使用磁碟區掛接提供反覆的體驗。 若要推送映像，請使用 [發行] 設定。

```console
REPOSITORY                  TAG         IMAGE ID            CREATED         SIZE
spboyer/hellodockertools    dev         0b6e2e44b3df        4 minutes ago   268.9 MB
microsoft/aspnetcore        1.0.1       189ad4312ce7        5 days ago      268.9 MB
```

應用程式正在執行，執行 `docker ps` 命令可以查看使用的容器。

```console
CONTAINER ID        IMAGE                          COMMAND               CREATED             STATUS              PORTS                   NAMES
3f240cf686c9        spboyer/hellodockertools:dev   "tail -f /dev/null"   4 minutes ago       Up 4 minutes        0.0.0.0:32769->80/tcp   hellodockertools_hellodockertools_1
```

### <a name="edit-and-continue"></a>編輯後繼續

靜態檔案和/或 Razor 範本檔案 (.cshtml) 的變更會自動更新，不需要編譯步驟。 進行變更，儲存並點選瀏覽器的 [重新整理] 檢視更新。  

程式碼檔案的修改需要編譯以及重新啟動容器內的 Kestrel。 完成變更之後，使用 CTRL + F5 執行程序，並啟動容器內的應用程式。 Docker 容器不會重建或停止，使用命令列的 `docker ps` 就會看見原始容器仍在執行，和 10 分鐘前一樣。 

```console
CONTAINER ID        IMAGE                          COMMAND               CREATED             STATUS              PORTS                   NAMES
3f240cf686c9        spboyer/hellodockertools:dev   "tail -f /dev/null"   10 minutes ago      Up 10 minutes       0.0.0.0:32769->80/tcp   hellodockertools_hellodockertools_1
```

### <a name="publishing-docker-images"></a>發佈 Docker 映像

只要完成應用程式的開發和偵錯循環，Visual Studio Tools for Docker 就會協助您建立應用程式的生產環境映像。 將 [偵錯] 下拉式清單變更為 [發行] 並建置應用程式。 這項工具會產生附有 `:latest` 標記的映像，這個標記可以推送至您的私用登錄或 Docker Hub。 

使用 `docker images` 可以查看映像清單。

```console
REPOSITORY                 TAG                 IMAGE ID            CREATED             SIZE
spboyer/hellodockertools   latest              8184ae38ba91        5 seconds ago       278.4 MB
spboyer/hellodockertools   dev                 0b6e2e44b3df        About an hour ago   268.9 MB
microsoft/aspnetcore       1.0.1               189ad4312ce7        5 days ago          268.9 MB
```

不過，使用磁碟區對應，生產環境或發行映像的大小預期會比 **dev** 映像更小；偵錯工具和應用程式過去確實是從本機電腦執行，不是在容器內執行。 **最新的**映像已封裝在執行主機電腦應用程式所需的整個應用程式程式碼中，所以此差異是應用程式程式碼的大小。

