---
title: 了解 .NET Core 的 Docker 基本概念
description: Docker 和 .NET Core 基本教學課程
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 543b9454e826022a72752d9a24bc43b77d2501f5
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44201383"
---
# <a name="learn-docker-basics-with-net-core"></a>了解 .NET Core 的 Docker 基本概念

本教學課程會教導 .NET Core 應用程式的 Docker 容器建置和部署作業。 [Docker 平台](https://docs.docker.com/engine/docker-overview/#the-docker-platform)使用 [Docker 引擎](https://docs.docker.com/engine/docker-overview/#docker-engine)快速建置應用程式並將其封裝為 [Docker 映像](https://docs.docker.com/glossary/?term=image)。 這些映像是使用 [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) 格式所撰寫，以在[分層式容器](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers)中部署和執行。

您會在本教學課程中了解︰

> [!div class="checklist"]
> * 如何：建立 Dockerfile
> * 如何建立 .NET Core 應用程式。
> * 如何將您的應用程式部署至 Docker 容器。

## <a name="net-core-easiest-way-to-get-started"></a>.NET Core：最簡單的入門方式

建立 Docker 映像之前，您需要將應用程式容器化。 您可以在 Linux、MacOS 或 Windows 上建立它。 執行這項作業的最快速且最簡單方法是使用 .NET Core。

如果您不熟悉 .NET Core CLI 工具組，請參閱 [.NET Core SDK 概觀](../tools/index.md)。

您可以使用[多架構標記](https://github.com/dotnet/announcements/issues/14)建置 Windows 和 Linux 容器。

## <a name="your-first-net-core-docker-app"></a>第一個 .NET Core Docker 應用程式

### <a name="prerequisites"></a>必要條件

完成本教學課程：

#### <a name="net-core-20-sdk"></a>.NET Core 2.0 SDK

* 安裝 [.NET Core SDK 2.0](https://www.microsoft.com/net/core)。

如需 .NET Core 2.x 支援的作業系統完整清單、不支援的作業系統版本，以及週期原則連結，請參閱 [.NET Core 2.x 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md)。

* 如果您還沒有這麼做，請安裝您慣用的程式碼編輯器。

> [!TIP]
> 需要安裝程式碼編輯器嗎？ 試用 [Visual Studio](https://visualstudio.com/downloads)！

#### <a name="installing-docker-client"></a>安裝 Docker 用戶端

安裝 [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) 或更新版本的 Docker 用戶端。

Docker 用戶端可以安裝於：

* Linux 散發

   * [CentOS](https://www.docker.com/docker-centos-distribution)

   * [Debian](https://www.docker.com/docker-debian)

   * [Fedora](https://www.docker.com/docker-fedora)

   * [Ubuntu](https://www.docker.com/docker-ubuntu)

* [macOS](https://docs.docker.com/docker-for-mac/)

* [Windows](https://docs.docker.com/docker-for-windows/).

### <a name="create-a-net-core-20-console-app-for-dockerization"></a>建立 .NET Core 2.0 主控台應用程式以進行 Docker 化

開啟命令提示字元，並建立名為 *Hello* 的資料夾。 巡覽至您已建立的資料夾，並鍵入下列命令：

```console
dotnet new console
dotnet run
```

讓我們快速逐步解說︰

1. `$ dotnet new console`

   [`dotnet new`](../tools/dotnet-new.md) 使用建置主控台應用程式時所需的相依性，來建立最新的 `Hello.csproj` 專案檔。  它也會建立 `Program.cs`，這個基本檔案包含了應用程式的進入點。
   
   `Hello.csproj`：

   專案檔會指定還原相依性和建置程式所需的所有內容。

   * `OutputType` 標記會指定我們正在建置可執行檔，亦即主控台應用程式。
   * `TargetFramework` 標記會指定做為目標的 .NET 實作。 在進階案例中，您可以指定多個目標架構，並透過單一作業建置所指定的架構。 在本教學課程中，我們會建置 .NET Core 2.0。

   `Program.cs`：

   程式是從 `using System` 開始。 此陳述式表示「將 `System` 命名空間中的所有內容帶入這個檔案的範圍內」。 `System` 命名空間會包含像是 `string` 的基本結構或數字類型。

   然後，我們會定義稱為 `Hello` 的命名空間。 您可以將命名空間變更為任何所需的內容。 名為 `Program` 的類別是定義於該命名空間內，其中含有可接受字串陣列作為其引數的 `Main` 方法。 這個陣列包含呼叫已編譯的程式時傳入的引數清單。 在本例中，程式只會撰寫 "Hello World"！ 到主控台。

2. `$ dotnet restore`

   在 .NET Core 2.x 中，**dotnet new** 會執行 [`dotnet restore`](../tools/dotnet-restore.md) 命令。 **Dotnet restore** 會還原與 [NuGet](https://www.nuget.org/) (.NET 套件管理員) 呼叫之相依性的樹狀結構。
   NuGet 會執行下列工作：
   * 分析 *Hello.csproj* 檔案 
   * 下載檔案相依性 (或從您的電腦快取捕捉)
   * 寫入 *obj/project.assets.json* 檔案

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
   
   *project.assets.json* 檔案是一組完整 NuGet 相依性圖形、繫結解析和其他應用程式中繼資料。 [`dotnet build`](../tools/dotnet-build.md) 和 [`dotnet run`](../tools/dotnet-run.md) 這類其他工具會使用此必要檔案來正確處理原始程式碼。
   
3. `$ dotnet run`

   [`dotnet run`](../tools/dotnet-run.md) 會呼叫 [`dotnet build`](../tools/dotnet-build.md) 以確認建置成功，然後呼叫 `dotnet <assembly.dll>` 以執行應用程式。
   
    ```console
    $ dotnet run
    
    Hello World!
    ```

    針對進階案例，如需詳細資訊，請參閱 [.NET Core 應用程式部署](../deploying/index.md)。

## <a name="dockerize-the-net-core-application"></a>將 .NET Core 應用程式 Docker 化

Hello .NET Core 主控台應用程式會在本機成功地執行。 現在讓我們進行下一步，以及在 Docker 中建置並執行應用程式。

### <a name="your-first-dockerfile"></a>您的第一個 Dockerfile

開啟文字編輯器，並讓我們開始吧！ 我們仍然從在其中建置應用程式的 Hello 目錄中工作。

將 Linux 或 [Windows 容器](https://docs.microsoft.com/virtualization/windowscontainers/about/)的下列 Docker 指示新增至新檔案。 完成時，會以無副檔名的 **Dockerfile** 形式將它儲存至 Hello 目錄的根目錄 (您可能需要將檔案類型設定為 `All types (*.*)` 或類似項目)。

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

Dockerfile 包含循序執行的 Docker 建置指示。

第一個指令必須是 [**FROM**](https://docs.docker.com/engine/reference/builder/#from)。 此指令會初始化新的建置階段，並設定其餘指令的基底映像。 多架構標記會根據 Docker for Windows [容器模式](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers)來提取 Windows 或 Linux 容器。 我們範例的基底映像是 microsoft/dotnet 存放庫中的 2.0-sdk 映像。

```Dockerfile
FROM microsoft/dotnet:2.0-sdk
```

[**WORKDIR**](https://docs.docker.com/engine/reference/builder/#workdir) 指令會設定任何其餘 RUN、CMD、ENTRYPOINT、COPY 和 ADD Dockerfile 指令的工作目錄。 如果目錄不存在，則會建立它。 在此情況下，WORKDIR 會設定為應用程式目錄。

```Dockerfile
WORKDIR /app
```

[**COPY**](https://docs.docker.com/engine/reference/builder/#copy) 指令會從來源路徑中複製新檔案或目錄，並將它們新增至目的地容器檔案系統。 使用此指令，我們會將 C# 專案檔複製至容器。

```Dockerfile
COPY *.csproj ./
```

[**RUN**](https://docs.docker.com/engine/reference/builder/#run) 指令會在目前映像的新層中執行任何命令，並認可結果。 產生的已認可映像用於 Dockerfile 中的下一步。 我們將執行 **dotnet restore** 來取得 C# 專案檔所需的相依性。 

```Dockerfile
RUN dotnet restore
```

這個 **COPY** 指令會將其餘的檔案複製至容器的新[層](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers)。

```Dockerfile
COPY . ./
```

我們會使用此 **RUN** 指令來發行應用程式。 [**dotnet publish**](../tools/dotnet-publish.md) 命令會編譯應用程式，並讀取在其專案檔中指定的相依性，然後將產生的一組檔案發行到目錄中。 我們的應用程式是使用**發行**組態所發行，並輸出至預設目錄。

```Dockerfile
RUN dotnet publish -c Release -o out
```

[**ENTRYPOINT**](https://docs.docker.com/engine/reference/builder/#entrypoint) 指令可讓容器執行為可執行檔。

```Dockerfile
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

現在，您已經有 Dockerfile：

* 將您的應用程式複製至映像
* 您應用程式與映像的相依性
* 建置要執行為可執行檔的應用程式

### <a name="build-and-run-the-hello-net-core-20-app"></a>建置並執行 Hello .NET Core 2.0 應用程式

#### <a name="essential-docker-commands"></a>必要 Docker 命令

這些 Docker 命令不可或缺：

* [docker build](https://docs.docker.com/engine/reference/commandline/build/)
* [docker run](https://docs.docker.com/engine/reference/commandline/run/)
* [docker ps](https://docs.docker.com/engine/reference/commandline/ps/)
* [docker stop](https://docs.docker.com/engine/reference/commandline/stop/)
* [docker rm](https://docs.docker.com/engine/reference/commandline/rm/)
* [docker rmi](https://docs.docker.com/engine/reference/commandline/rmi/)
* [docker image](https://docs.docker.com/engine/reference/commandline/image/)

#### <a name="build-and-run"></a>建置並執行

您已撰寫 dockerfile；現在 Docker 會建置您的應用程式，然後執行容器。

```console
docker build -t dotnetapp-dev .
docker run --rm dotnetapp-dev Hello from Docker
```

`docker build` 命令的輸出應該類似下列主控台輸出：

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

如您從輸出中所見，Docker 引擎已使用 Dockerfile 來建置我們的容器。

`docker run` 命令的輸出應該類似下列主控台輸出：

```console
Hello World!
```

恭喜您！ 您已：
> [!div class="checklist"]
> * 建立本機 .NET Core 應用程式
> * 建立 Dockerfile 來建置您的第一個容器
> * 建置並執行 Docker 化應用程式



## <a name="next-steps"></a>後續步驟

以下是一些您可以採取的後續步驟：

* [.NET Docker 映像簡介影片](https://channel9.msdn.com/Shows/Code-Conversations/Introduction-to-NET-Docker-Images-with-Kendra-Havens?term=docker)
* [Visual Studio、Docker 和 Azure 容器執行個體更適合一起使用！](https://blogs.msdn.microsoft.com/alimaz/2017/08/17/visual-studio-docker-azure-container-instances-better-together/)
* [Docker for Azure 快速入門](https://docs.docker.com/docker-for-azure/#docker-community-edition-ce-for-azure)
* [在 Docker for Azure 上部署應用程式](https://docs.docker.com/docker-for-azure/deploy/)

> [!Note]
> 如果您沒有 Azure 訂用帳戶，請[立即註冊](https://azure.microsoft.com/free/?b=16.48)可免費使用 30 天的帳戶，並獲得 $200 美元的 Azure 點數來試用其他的 Azure 服務組合。

## <a name="docker-images-used-in-this-sample"></a>此範例中所使用的 Docker 映像

在此範例中，使用下列 Docker 映像

* [`microsoft/dotnet:2.0-sdk`](https://hub.docker.com/r/microsoft/dotnet)

## <a name="related-resources"></a>相關資源

* [.NET Core Docker 範例](https://github.com/dotnet/dotnet-docker/tree/master/samples)
* [Windows 容器上的 Dockerfile](https://docs.microsoft.com/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [.NET Framework Docker 範例](https://github.com/Microsoft/dotnet-framework-docker-samples)
* [DockerHub 上的 ASP.NET Core](https://hub.docker.com/r/microsoft/aspnetcore/)
* [將 .NET Core 應用程式 Docker 化 - Docker 教學課程](https://docs.docker.com/engine/examples/dotnetcore/)
* [使用 Visual Studio Docker 工具](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [將 Docker 映像從 Azure Container Registry 部署到 Azure 容器執行個體](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/) \(英文\)
