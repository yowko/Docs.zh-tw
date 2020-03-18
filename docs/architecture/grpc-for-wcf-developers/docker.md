---
title: 為 WCF 開發人員提供 Docker - gRPC
description: 為ASP.NET核心 gRPC 應用程式創建 Docker 映射
ms.date: 09/02/2019
ms.openlocfilehash: e67c43f9486fbfe9a5d3e84e3b74770eb621f604
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148110"
---
# <a name="create-docker-images"></a>創建 Docker 映射

本節介紹為ASP.NET Core gRPC 應用程式創建 Docker 映射，這些應用程式可在 Docker、Kubernetes 或其他容器環境中運行。 使用的應用程式範例，帶有ASP.NET酷睿 MVC Web 應用和 gRPC 服務，可在 GitHub 上的[dotnet 架構/grpc-for wcf 開發人員](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample)存儲庫中使用。

## <a name="microsoft-base-images-for-aspnet-core-applications"></a>用於ASP.NET核心應用程式的微軟基本映射

Microsoft 為構建和運行 .NET Core 應用程式提供了一系列基本映射。 要創建 ASP.NET酷睿 3.0 圖像，請使用兩個基本映射：

- 用於生成和發佈應用程式的 SDK 映射。
- 用於部署的運行時映射。

| 映像 | 描述 |
| ----- | ----------- |
| [mcr.microsoft.com/dotnet/core/sdk](https://hub.docker.com/_/microsoft-dotnet-core-sdk/) | 用於使用`docker build`生成應用程式。 不用於生產。 |
| [mcr.microsoft.com/dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) | 包含運行時和 ASP.NET核心依賴項。 用於生產。 |

對於每個映射，有四種基於不同 Linux 發行版本的變體，按標記區分。

| 圖像標記 | Linux | 注意 |
| --------- | ----- | ----- |
| 3.0-破壞者，3.0 | Debian 10 | 如果未指定作業系統變體，則預設映射。 |
| 3.0-高山 | 阿爾卑斯 3.9 | 阿爾卑斯基圖圖像比Debian或Ubuntu圖像小得多。 |
| 3.0-迪斯可 | Ubuntu 19.04 | |
| 3.0-仿生 | Ubuntu 18.04 | |

阿爾卑斯基圖約為 100 MB，而 Debian 和 Ubuntu 圖像的映射為 200 MB。 某些套裝軟體或庫在 Alpine 的套裝軟體管理中可能不可用。 如果您不確定要使用的圖像，則可能需要選擇預設的 Debian。

> [!IMPORTANT]
> 請確保在生成和運行時使用相同的 Linux 變體。 在一個變體上構建和發佈的應用程式可能不適用於另一個變體。

## <a name="create-a-docker-image"></a>建立 Docker 映像

Docker 映射由 Docker*檔*定義。 這是一個文字檔，其中包含生成應用程式和安裝生成或運行應用程式所需的任何依賴項所需的所有命令。 下面的示例顯示了 ASP.NET Core 3.0 應用程式的最簡單的 Dockerfile：

```dockerfile
# Application build steps
FROM mcr.microsoft.com/dotnet/core/sdk:3.0 as builder

WORKDIR /src

COPY . .

RUN dotnet restore

RUN dotnet publish -c Release -o /published src/StockData/StockData.csproj

# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

# Uncomment the line below if running with HTTPS
# ENV ASPNETCORE_URLS=https://+:443

WORKDIR /app

COPY --from=builder /published .

ENTRYPOINT [ "dotnet", "StockData.dll" ]
```

Dockerfile 有兩個部分：第一部分使用`sdk`基本映射來構建和發佈應用程式;第二部分使用基本映射來構建和發佈應用程式。第二個從基中`aspnet`創建運行時映射。 這是因為`sdk`映射約為 900 MB，而運行時映射的映射約為 200 MB，並且大多數內容在運行時是不必要的。

### <a name="the-build-steps"></a>生成步驟

| 步驟 | 描述 |
| ---- | ----------- |
| `FROM ...` | 聲明基本映射並分配`builder`別名。 |
| `WORKDIR /src` | 創建`/src`目錄並將其設置為當前工作目錄。 |
| `COPY . .` | 將主機上當前目錄下的所有內容複寫到映射上的目前的目錄中。 |
| `RUN dotnet restore` | 還原任何外部包（ASP.NET與 SDK 一起預先安裝核心 3.0 框架）。 |
| `RUN dotnet publish ...` | 生成和發佈發佈版本。 請注意，`--runtime`該標誌不是必需的。 |

### <a name="the-runtime-image-steps"></a>運行時映射步驟

| 步驟 | 描述 |
| ---- | ----------- |
| `FROM ...` | 聲明新的基本映射。 |
| `WORKDIR /app` | 創建`/app`目錄並將其設置為當前工作目錄。 |
| `COPY --from=builder ...` | 使用第一`builder``FROM`行中的別名從上一個圖像複製已發佈的應用程式。 |
| `ENTRYPOINT [ ... ]` | 將命令設置在容器啟動時運行。 運行時`dotnet`映射中的命令只能運行 DLL 檔。 |

### <a name="https-in-docker"></a>Docker 中的 HTTPS

Docker 的 Microsoft 基本`ASPNETCORE_URLS`映射將環境`http://+:80`變數設置為 ，這意味著 Kestrel 在該埠上運行沒有 HTTPS。 如果將 HTTPS 與自訂證書一起使用（如[自託管 gRPC 應用程式中](self-hosted.md)所述），則應重寫此證書。 在 Dockerfile 的運行時映射創建部分設置環境變數。

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a>.dockerignore 檔

與從`.gitignore`原始程式碼管理中排除某些檔和目錄的檔類似，`.dockerignore`該檔可用於在生成期間將檔和目錄複寫到映射。 這不僅節省了複製時間，還可以避免將 PC 中的`obj`目錄複寫到映射中出現的一些錯誤。 至少，應為`bin`檔添加條目，並`obj`添加到檔中`.dockerignore`。

```console
bin/
obj/
```

## <a name="build-the-image"></a>建立映像

對於具有單個應用程式的解決方案，以及單個 Dockerfile，將 Dockerfile 放在基本目錄中是最簡單的。 換句話說，將其放在與`.sln`檔相同的目錄中。 在這種情況下，要生成映射，請使用包含 Dockerfile`docker build`的目錄中的以下命令。

```console
docker build --tag stockdata .
```

令人困惑的名稱`--tag`標誌（可以縮短為`-t`）指定圖像的整個名稱，包括指定的實際標記。 `.`末尾指定將在其中運行生成的上下文;Docker 檔中命令的`COPY`當前工作目錄。

如果單個解決方案中有多個應用程式，則可以將每個應用程式的 Dockerfile 保留在檔旁邊的`.csproj`自己的資料夾中。 您仍應從基`docker build`目錄中運行該命令，以確保將解決方案和所有專案複製到映射中。 可以使用`--file`（ 或`-f`） 標誌在目前的目錄下方指定 Docker 檔。

```console
docker build --tag stockdata --file src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a>在電腦上的容器中運行映射

要在本地 Docker 實例中運行映射，請使用`docker run`命令。

```console
docker run -ti -p 5000:80 stockdata
```

標誌`-ti`將當前終端連接到容器的終端，並在互動式模式下運行。 容器`-p 5000:80`上的發佈（連結）埠 80 到本地主機網路介面上的埠 5000。

## <a name="push-the-image-to-a-registry"></a>將映像推送至登錄

驗證映射是否正常工作後，將其推送到 Docker 註冊表，使其在其他系統上可用。 內部網路將需要預配 Docker 註冊表。 這可以像運行[Docker 自己的`registry`映射](https://docs.docker.com/registry/deploying/)（Docker 註冊表在 Docker 容器中運行）一樣簡單，但有多種更全面的解決方案可用。 對於外部共用和雲使用，可以使用各種託管註冊表，例如[Azure 容器註冊表](https://docs.microsoft.com/azure/container-registry/)或[Docker Hub。](https://docs.docker.com/docker-hub/repos/)

要推送到 Docker 中心，請用使用者或組織名稱對圖像名稱進行首碼。

```console
docker tag stockdata myorg/stockdata
docker push myorg/stockdata
```

要推送到專用註冊表，使用註冊表主機名稱和組織名稱對映射名稱進行首碼。

```console
docker tag stockdata internal-registry:5000/myorg/stockdata
docker push internal-registry:5000/myorg/stockdata
```

映射在註冊表中後，您可以將其部署到單獨的 Docker 主機，或部署到容器編排引擎（如 Kubernetes）。

>[!div class="step-by-step"]
>[上一個](self-hosted.md)
>[下一個](kubernetes.md)
