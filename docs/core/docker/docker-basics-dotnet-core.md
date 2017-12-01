---
title: "了解 Docker 與.NET Core 的基本概念"
description: "Docker 和.NET Core 的基本教學課程"
keywords: ".NET、.NET core、 Docker、 教學課程"
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: tutorial
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: dotnet
ms.assetid: 03c28597-7e73-46d6-a9c3-f9cb55642739
ms.custom: mvc
manager: wpickett
ms.openlocfilehash: 5935f67d7e4ca9c9e8768373e2bcaa9febccfdc5
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/08/2017
---
# <a name="learn-docker-basics-with-net-core"></a>了解 Docker 與.NET Core 的基本概念

本教學課程將教導的 Docker 容器建置和部署.NET Core 應用程式的工作。 本教學課程的過程中，您了解：

> [!div class="checklist"]
> * 如何建立 Dockerfile。
> * 如何建立.NET Core 應用程式。
> * 如何將您的應用程式部署至 Docker 容器。

[Docker 平台](https://docs.docker.com/engine/docker-overview/#the-docker-platform)使用[Docker 引擎](https://docs.docker.com/engine/docker-overview/#docker-engine)快速建置並封裝為應用程式[Docker images](https://docs.docker.com/glossary/?term=image)。 這些映像以撰寫[Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile)部署和執行中的格式[分層容器](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers)。

## <a name="net-core-easiest-way-to-get-started"></a>若要開始使用.NET core： 最簡單的方式

之前建立 Docker 映像，您必須以化應用程式。 您可以在 Linux、 MacOS、 或 Windows 上建立它。 最快速而且簡單的方法是使用.NET 核心。

如果您不熟悉 .NET Core CLI 工具組，請參閱 [.NET Core SDK 概觀](../tools/index.md)。

您可以建立具有 Windows 和 Linux 容器[多 arch 基礎標記](https://github.com/dotnet/announcements/issues/14)。

## <a name="your-first-net-core-docker-app"></a>第一個.NET Core Docker 應用程式

### <a name="prerequisites"></a>必要條件

若要完成本教學課程：

#### <a name="net-core-20-sdk"></a>.NET 核心 2.0 SDK

* 安裝[.NET Core SDK 2.0](https://www.microsoft.com/net/core)。

如需 .NET Core 2.x 支援的作業系統完整清單、不支援的作業系統版本，以及週期原則連結，請參閱 [.NET Core 2.x 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md)。

* 如果您還沒有這麼做，請安裝您最愛的程式碼編輯器 中。

> [!TIP]
> 需要安裝的程式碼編輯器？ 再試一次[Visual Studio](https://visualstudio.com/downloads)！

#### <a name="installing-docker-client"></a>安裝 Docker 用戶端

安裝[Docker 17.06](https://docs.docker.com/release-notes/docker-ce/)或更新版本的 Docker 用戶端。

Docker 用戶端可以安裝在：

* Linux 散發套件

   * [CentOS](https://www.docker.com/docker-centos-distribution)

   * [Debian](https://www.docker.com/docker-debian)

   * [Fedora](https://www.docker.com/docker-fedora)

   * [Ubuntu](https://www.docker.com/docker-ubuntu)

* [macOS](https://docs.docker.com/docker-for-mac/)

* [Windows](https://docs.docker.com/docker-for-windows/)。

### <a name="create-a-net-core-20-console-app-for-dockerization"></a>建立.NET Core 2.0 主控台應用程式，Dockerization

開啟命令提示字元，並建立名為 *Hello* 的資料夾。 導覽至您所建立的資料夾，並輸入下列命令：

```console
dotnet new console
dotnet run
```

讓我們快速逐步解說︰

1. `$ dotnet new console`

   [`dotnet new`](../tools/dotnet-new.md) 使用建置主控台應用程式時所需的相依性，來建立最新的 `Hello.csproj` 專案檔。  它也會建立 `Program.cs`，這個基本檔案包含了應用程式的進入點。
   
   `Hello.csproj`:

   專案檔會指定還原相依性和建置程式所需的所有內容。

   * `OutputType` 標記會指定我們正在建置可執行檔，亦即主控台應用程式。
   * `TargetFramework` 標記會指定做為目標的 .NET 實作。 在進階案例中，您可以指定多個目標架構，並在單一作業中指定的架構來建置。 在本教學課程中，我們會建置.NET Core 2.0。

   `Program.cs`：

   藉由啟動程式`using System`。 這個聲明意指，"的所有項目納入`System`進入範圍內，此檔案的命名空間。 」 `System` 命名空間會包含像是 `string` 的基本結構或數字類型。

   然後，我們會定義稱為 `Hello` 的命名空間。 您可以變更您想要的任何項目命名空間。 名為 `Program` 的類別是定義於該命名空間內，其中含有可接受字串陣列作為其引數的 `Main` 方法。 這個陣列包含呼叫已編譯的程式時傳入的引數清單。 在本例中，程式只會寫入"Hello World ！" 到主控台。

2. `$ dotnet restore`

   在.NET Core 2.x， **dotnet 新**執行[ `dotnet restore` ](../tools/dotnet-restore.md)命令。 **Dotnet 還原**還原樹狀目錄中的相依性與[NuGet](https://www.nuget.org/)（.NET 封裝管理員） 呼叫。
   NuGet 會執行下列工作：
   * 分析*Hello.csproj*檔案 
   * 會將檔案下載相依性 （或從您的電腦快取 grabs）
   * 寫入*obj/project.assets.json*檔案

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
   
   *Project.assets.json*檔案是一組完整的 NuGet 相依性圖形、 繫結解析度，以及其他應用程式中繼資料。 需要這個檔案由其他工具，例如[ `dotnet build` ](../tools/dotnet-build.md)和[ `dotnet run` ](../tools/dotnet-run.md)，才能正確地處理的原始程式碼。
   
3. `$ dotnet run`

   [`dotnet run`](../tools/dotnet-run.md)呼叫[ `dotnet build` ](../tools/dotnet-build.md)確認建置成功，然後呼叫`dotnet <assembly.dll>`執行應用程式。
   
    ```console
    $ dotnet run
    
    Hello World!
    ```

    進階案例中，請參閱[.NET Core 應用程式部署](../deploying/index.md)如需詳細資訊。

## <a name="dockerize-the-net-core-application"></a>Dockerize.NET Core 應用程式

Hello.NET Core 主控台應用程式成功地在本機執行。 現在讓我們更步驟進一步和建置和執行應用程式在 Docker 中。

### <a name="your-first-dockerfile"></a>您的第一個 Dockerfile

開啟文字編輯器，讓我們開始吧 ！ 我們仍然使用我們建立了應用程式中的 Hello 目錄。

加入下列任一 Linux Docker 指示或[Windows 容器](https://docs.microsoft.com/virtualization/windowscontainers/about/)到新的檔案。 完成後，請將它儲存為 Hello 目錄的根目錄中**Dockerfile**，不含副檔名 (您可能需要將檔案類型設定為`All types (*.*)`或類似)。

```Dockerfile
FROM microsoft/dotnet:2.0-sdk
WORKDIR /app

# copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# copy and build everything else
COPY . ./
RUN dotnet publish -c Release -o out
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

Dockerfile 包含 Docker 建置的指示，以循序方式執行。

必須是第一個指令[ **FROM**](https://docs.docker.com/engine/reference/builder/#from)。 這個指令會初始化新的組建階段，並設定基底映像的其餘指示進行。 多重 arch 標記提取 Windows 或 Linux 容器 Docker for Windows 根據[容器模式](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers)。 基底映像，我們的範例是 microsoft/dotnet 儲存機制中，從 2.0 sdk 映像

```Dockerfile
FROM microsoft/dotnet:2.0-sdk
```

[ **WORKDIR** ](https://docs.docker.com/engine/reference/builder/#workdir)指令集的工作目錄的任何其餘執行、 CMD、 進入點、 複製和新增 Dockerfile 指示。 如果此目錄不存在，它會建立它。 在此情況下，WORKDIR 設定應用程式目錄。

```Dockerfile
WORKDIR /app
```

[**複製**](https://docs.docker.com/engine/reference/builder/#copy)指令會從來源路徑複製到新的檔案或目錄，並將它們加入到目的地容器檔案系統。 使用此指示中，我們會將 C# 專案檔複製到容器。

```Dockerfile
COPY *.csproj ./
```

[**執行**](https://docs.docker.com/engine/reference/builder/#run)指令執行任何命令，在目前的映像之上一個新圖層中，並認可結果。 產生的認可映像用於 Dockerfile 的下一個步驟。 目前我們正在執行**dotnet 還原**取得所需的相依性的 C# 專案檔。 

```Dockerfile
RUN dotnet restore
```

這**複製**指令將複製的其他檔案插入到我們容器新[層](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers)。

```Dockerfile
COPY . ./
```

我們會發佈應用程式與這個**執行**指令。 [ **Dotnet 發行**](../tools/dotnet-publish.md)命令編譯應用程式、 讀取整個專案檔中指定其相依性和目錄發佈設定檔的結果。 我們的應用程式一起發佈**發行**組態，以及輸出至預設的目錄。

```Dockerfile
RUN dotnet publish -c Release -o out
```

[ **ENTRYPOINT** ](https://docs.docker.com/engine/reference/builder/#entrypoint)指示可讓容器執行可執行檔。

```Dockerfile
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

現在有了 Dockerfile 的：

* 將您的應用程式複製到映像
* 您的應用程式映像的相依性
* 建置可執行檔，以執行應用程式

### <a name="build-and-run-the-hello-net-core-20-app"></a>建置並執行 Hello.NET Core 2.0 應用程式

#### <a name="essential-docker-commands"></a>必要的 Docker 命令

這些 Docker 命令是不可或缺：

* [docker 建置](https://docs.docker.com/engine/reference/commandline/build/)
* [執行的 docker](https://docs.docker.com/engine/reference/commandline/run/)
* [docker ps](https://docs.docker.com/engine/reference/commandline/ps/)
* [docker 停止](https://docs.docker.com/engine/reference/commandline/stop/)
* [docker rm](https://docs.docker.com/engine/reference/commandline/rm/)
* [docker rmi](https://docs.docker.com/engine/reference/commandline/rmi/)
* [docker 映像](https://docs.docker.com/engine/reference/commandline/image/)

#### <a name="build-and-run"></a>建置並執行

您已撰寫 dockerfile。現在 Docker 建置您的應用程式，並執行容器。

```console
docker build -t dotnetapp-dev .
docker run --rm dotnetapp-dev Hello from Docker
```

從輸出`docker build`命令應該類似下列的主控台輸出：

```console
Sending build context to Docker daemon   72.7kB
Step 1/7 : FROM microsoft/dotnet:2.0-sdk
 ---> d84f64b126a6
Step 2/7 : WORKDIR /app
 ---> Using cache
 ---> 9af1fbdc7972
Step 3/7 : COPY *.csproj ./
 ---> Using cache
 ---> 86c8c332d4b3
Step 4/7 : RUN dotnet restore
 ---> Using cache
 ---> 86fcd7dd0ea4
Step 5/7 : COPY . ./
 ---> Using cache
 ---> 6faf0a53607f
Step 6/7 : RUN dotnet publish -c Release -o out
 ---> Using cache
 ---> f972328318c8
Step 7/7 : ENTRYPOINT dotnet out/Hello.dll
 ---> Using cache
 ---> 53c337887e18
Successfully built 53c337887e18
Successfully tagged dotnetapp-dev:latest
```

您可以從輸出中看到，Docker 引擎會使用 Dockerfile 建立我們的容器。

從輸出`docker run`命令應該類似下列的主控台輸出：

```console
Hello World!
```

恭喜您！ 只要有：
> [!div class="checklist"]
> * 建立本機的.NET Core 應用程式
> * 建立 Dockerfile，以建置您的第一個容器
> * 建置及執行 Dockerized 應用程式



## <a name="next-steps"></a>後續步驟

以下是一些您可以採取的後續步驟：

* [.NET Docker 映像的影片簡介](https://channel9.msdn.com/Shows/Code-Conversations/Introduction-to-NET-Docker-Images-with-Kendra-Havens?term=docker)
* [Visual Studio、 Docker 和 Azure 容器執行個體一起提供更好 ！](https://blogs.msdn.microsoft.com/alimaz/2017/08/17/visual-studio-docker-azure-container-instances-better-together/)
* [Docker for Azure 快速入門](https://docs.docker.com/docker-for-azure/#docker-community-edition-ce-for-azure)
* [部署您的應用程式，azure docker](https://docs.docker.com/docker-for-azure/deploy/)

> [!Note]
> 如果您沒有 Azure 訂用帳戶，[立即註冊](https://azure.microsoft.com/free/?b=16.48)免費 30 天的帳戶和 Azure 信用額度試用 Azure 服務的任何組合中的 get 美金 200。

## <a name="docker-images-used-in-this-sample"></a>此範例中使用的 docker 映像

在此範例中使用下列的 Docker 映像

* [`microsoft/dotnet:2.0-sdk`](https://hub.docker.com/r/microsoft/dotnet)

## <a name="related-resources"></a>相關資源

* [.NET core Docker 範例](https://github.com/dotnet/dotnet-docker-samples/README.md)
* [Windows 容器上的 Dockerfile](https://docs.microsoft.com/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [.NET framework Docker 範例](https://github.com/Microsoft/dotnet-framework-docker-samples)
* [ASP.NET Core DockerHub 上](https://hub.docker.com/r/microsoft/aspnetcore/)
* [Dockerize.NET Core 應用程式-Docker 教學課程](https://docs.docker.com/engine/examples/dotnetcore/)
* [使用 Visual Studio Docker 工具](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [將從 Azure 容器登錄至 Azure 容器執行個體的 Docker 映像部署](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)