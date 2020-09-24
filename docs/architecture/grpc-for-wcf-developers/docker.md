---
title: 適用于 WCF 開發人員的 Docker gRPC
description: 建立 ASP.NET Core gRPC 應用程式的 Docker 映射
ms.date: 09/02/2019
ms.openlocfilehash: 379750edfa1a9fc282e43ffa83e5695425f31a26
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91152711"
---
# <a name="create-docker-images"></a>建立 Docker 映射

本節說明如何建立 ASP.NET Core gRPC 應用程式的 Docker 映射，並準備好在 Docker、Kubernetes 或其他容器環境中執行。 使用 ASP.NET Core MVC web 應用程式和 gRPC 服務的範例應用程式，可在 GitHub 上的 [dotnet 架構/gRPC-適用于 wcf 的開發人員](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) 存放庫中取得。

## <a name="microsoft-base-images-for-aspnet-core-applications"></a>適用于 ASP.NET Core 應用程式的 Microsoft 基礎映射

Microsoft 提供一系列基礎映射來建立和執行 .NET Core 應用程式。 若要建立 ASP.NET Core 3.0 映射，您可以使用兩個基底映射：

- 用來建立和發佈應用程式的 SDK 映射。
- 用於部署的執行時間映射。

| 映像 | 描述 |
| ----- | ----------- |
| [mcr.microsoft.com/dotnet/core/sdk](https://hub.docker.com/_/microsoft-dotnet-core-sdk/) | 用來建立應用程式 `docker build` 。 不要用在生產環境中。 |
| [mcr.microsoft.com/dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) | 包含執行時間和 ASP.NET Core 相依性。 適用于生產環境。 |

每個映射都有四個以不同 Linux 散發套件為基礎的變化，並依標記區分。

| 影像標記 (s)  | Linux | 備註 |
| --------- | ----- | ----- |
| 3.0-buster、3。0 | Debian 10 | 如果未指定作業系統變數，則為預設映射。 |
| 3.0-alpine | Alpine 3。9 | Alpine 基底映射遠小於 Debian 或 Ubuntu。 |
| 3.0-disco | Ubuntu 19.04 | |
| 3.0-bionic | Ubuntu 18.04 | |

Alpine 基底映射大約是 100 MB，相較于 Debian 和 Ubuntu 映射的 200 MB。 某些軟體套件或程式庫可能無法在 Alpine 的套件管理中使用。 如果您不確定要使用哪個映射，您應該選擇預設 Debian。

> [!IMPORTANT]
> 請確定您針對組建和執行時間使用相同的 Linux 變體。 在某個變異上建立併發布的應用程式可能無法在另一個變數上運作。

## <a name="create-a-docker-image"></a>建立 Docker 映像

Docker 映射是由 *Dockerfile*所定義。 這是一個文字檔，其中包含建立應用程式所需的所有命令，並安裝建立或執行應用程式所需的任何相依性。 下列範例顯示 ASP.NET Core 3.0 應用程式的最簡單 Dockerfile：

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

Dockerfile 有兩個部分：第一個是使用 `sdk` 基底映射來建立和發佈應用程式，第二個部分則會從基底建立執行時間映射 `aspnet` 。 這是因為 `sdk` 影像大約是 900 MB，相較于執行時間影像大約 200 mb，而且在執行時間中，大部分的內容都是不必要的。

### <a name="the-build-steps"></a>組建步驟

| 步驟 | 描述 |
| ---- | ----------- |
| `FROM ...` | 宣告基底映射並指派 `builder` 別名。 |
| `WORKDIR /src` | 建立 `/src` 目錄，並將它設定為目前的工作目錄。 |
| `COPY . .` | 將主機上目前目錄下的所有內容複寫到映射的目前目錄中。 |
| `RUN dotnet restore` | 還原任何 (ASP.NET Core 3.0 framework 的外部套件都會隨 SDK) 預先安裝。 |
| `RUN dotnet publish ...` | 建立併發行發行組建。 請注意， `--runtime` 不需要旗標。 |

### <a name="the-runtime-image-steps"></a>執行時間映射步驟

| 步驟 | 描述 |
| ---- | ----------- |
| `FROM ...` | 宣告新的基底映射。 |
| `WORKDIR /app` | 建立 `/app` 目錄，並將它設定為目前的工作目錄。 |
| `COPY --from=builder ...` | 使用第一行的別名，從上一個影像複製已發行的應用程式 `builder` `FROM` 。 |
| `ENTRYPOINT [ ... ]` | 設定要在容器啟動時執行的命令。 `dotnet`執行時間映射中的命令只能執行 DLL 檔案。 |

### <a name="https-in-docker"></a>Docker 中的 HTTPS

適用于 Docker 的 Microsoft 基礎映射 `ASPNETCORE_URLS` 會將環境變數設為 `http://+:80` ，這表示 Kestrel 會在該埠上執行而不需要 HTTPS。 如果您使用 HTTPS 與自訂憑證 (如 [自我裝載 gRPC 應用程式](self-hosted.md)) 中所述，您應該覆寫此項。 在 Dockerfile 的執行時間映射建立部分中設定環境變數。

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a>>.dockerignore 檔案

就像 `.gitignore` 從原始檔控制中排除特定檔案和目錄的檔案一樣，檔案 `.dockerignore` 可以用來排除檔案和目錄，不要在組建期間複製到映射中。 這不僅能節省時間的複製，也可以避免將電腦上的 `obj` 目錄複寫到映射時所發生的一些錯誤。 您至少應該在檔案中加入和的 `bin` 專案 `obj` `.dockerignore` 。

```console
bin/
obj/
```

## <a name="build-the-image"></a>建立映像

針對具有單一應用程式的方案，因此為單一 Dockerfile，最簡單的方式是將 Dockerfile 放在基底目錄中。 換句話說，將它放在與檔案相同的目錄中 `.sln` 。 在此情況下，若要建立映射，請 `docker build` 從包含 Dockerfile 的目錄中使用下列命令。

```console
docker build --tag stockdata .
```

Confusingly 命名的 `--tag` 旗標 (可以縮短為 `-t`) 指定影像的整個名稱，包括實際標記（如果有指定的話）。 `.`結束時，會指定將在其中執行組建的內容; `COPY` Dockerfile 中命令的目前工作目錄。

如果您在單一解決方案中有多個應用程式，您可以將每個應用程式的 Dockerfile 保留在檔案旁的資料夾中 `.csproj` 。 您仍然應該 `docker build` 從基底目錄執行此命令，以確保方案和所有專案都會複製到映射中。 您可以使用 `--file` (或) 旗標，在目前的目錄下指定 Dockerfile `-f` 。

```console
docker build --tag stockdata --file src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a>在您電腦上的容器中執行映射

若要在您的本機 Docker 實例中執行映射，請使用 `docker run` 命令。

```console
docker run -ti -p 5000:80 stockdata
```

旗標會將 `-ti` 您目前的終端機連接到容器的終端機，並在互動模式中執行。 會將 `-p 5000:80` 容器上的埠 80) 的 (連結發佈到 localhost 網路介面上的埠5000。

## <a name="push-the-image-to-a-registry"></a>將映像推送至登錄

確認映射可正常運作之後，請將它推送到 Docker 登錄，使其可在其他系統上使用。 內部網路將需要布建 Docker 登錄。 這可以像是執行 [docker 本身的 `registry` 映射](https://docs.docker.com/registry/deploying/) 一樣簡單 (docker 登錄是在 docker 容器中執行) ，但是有各種更全面的解決方案可用。 針對外部共用和雲端用途，有各種可用的受控登錄，例如 [Azure Container Registry](/azure/container-registry/) 或 [Docker Hub](https://docs.docker.com/docker-hub/repos/)。

若要推送至 Docker Hub，請在映射名稱前加上您的使用者或組織名稱。

```console
docker tag stockdata myorg/stockdata
docker push myorg/stockdata
```

若要推送至私人登錄，請在映射名稱前加上登錄主機名稱和組織名稱。

```console
docker tag stockdata internal-registry:5000/myorg/stockdata
docker push internal-registry:5000/myorg/stockdata
```

映射在登錄中之後，您可以將它部署到個別的 Docker 主機或容器協調流程引擎（例如 Kubernetes）。

>[!div class="step-by-step"]
>[上一個](self-hosted.md) 
>[下一步](kubernetes.md)
