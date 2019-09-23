---
title: 適用于 WCF 開發人員的 Docker gRPC
description: 建立 ASP.NET Core gRPC 應用程式的 Docker 映射
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 6e9d4956077286d133d09ab8e681ba5e82ab1aa4
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184474"
---
# <a name="docker"></a>Docker

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

本節將討論如何為 ASP.NET Core gRPC 應用程式建立 Docker 映射，並準備好在 Docker、Kubernetes 或其他容器環境中執行。 使用 ASP.NET Core MVC web 應用程式和 gRPC 服務的範例應用程式，可在 GitHub 上的[RendleLabs/gRPC-wcf 開發人員](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample)存放庫中取得。

## <a name="microsoft-base-images-for-aspnet-core-applications"></a>適用于 ASP.NET Core 應用程式的 Microsoft 基底映射

Microsoft 提供各種基底映射來建立和執行 .NET Core 應用程式。 若要建立 ASP.NET Core 3.0 映射，會使用兩個基底映射：用來建立及發佈應用程式的 SDK 映射，以及用於部署的執行時間映射。

| Image | 描述 |
| ----- | ----------- |
| [mcr.microsoft.com/dotnet/core/sdk](https://hub.docker.com/_/microsoft-dotnet-core-sdk/) | 用於建立使用`docker build`的應用程式。 不會在生產環境中使用。 |
| [mcr.microsoft.com/dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) | 包含執行時間和 ASP.NET Core 相依性。 適用于生產環境。 |

針對每個映射，有四個以不同 Linux 散發套件為基礎的變體，以標記區分。

| 映射標記 | Linux | 注意 |
| --------- | ----- | ----- |
| 3.0-buster、3。0 | Debian 10 | 如果未指定 OS variant，則為預設映射。 |
| 3.0-alpine | Alpine 3。9 | Alpine 基底映射的大小遠低於 Debian 或 Ubuntu。 |
| 3.0-disco | Ubuntu 19.04 | |
| 3.0-bionic | Ubuntu 18.04 | |

相較于 200 MB，Debian 和 Ubuntu 映射的 Alpine 基底映射大約是 100 MB，但某些軟體套件或程式庫可能無法在 Alpine 的套件管理中使用。 如果您不確定要使用哪一個影像，最好先使用預設的 Debian，除非您有很大的需求，才能使用不同的散發版本。

> [!IMPORTANT]
> 請確定您針對組建和執行時間使用相同的 Linux 變體。 在某個 variant 上建立和發行的應用程式可能無法在另一個變數上使用。

## <a name="create-a-docker-image"></a>建立 Docker 映射

Docker 映射是由*Dockerfile*所定義，這是一個文字檔，其中包含建立應用程式及安裝建立或執行應用程式所需之任何相依性所需的所有命令。 下列範例顯示 ASP.NET Core 3.0 應用程式的最簡單 Dockerfile：

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

Dockerfile 有兩個部分：第一個是使用`sdk`基底映射來建立和發行應用程式; 第二個是`aspnet`從基底建立執行時間映射。 這是因為`sdk`相較于執行時間映射約 200 mb，映射大約是 900 mb，而且在執行時間時，大部分的內容都是不必要的。

### <a name="the-build-steps"></a>組建步驟

| 步驟 | 描述 |
| ---- | ----------- |
| `FROM ...` | 宣告基底映射並指派`builder`別名（如需說明，請參閱下一節）。 |
| `WORKDIR /src` | `/src`建立目錄，並將它設定為目前的工作目錄。 |
| `COPY . .` | 將主機上目前目錄底下的所有內容複寫到映射上的目前目錄中。 |
| `RUN dotnet restore` | 還原任何外部套件（ASP.NET Core 3.0 framework 已預先安裝 SDK）。 |
| `RUN dotnet publish ...` | 建立併發行發行組建。 請注意， `--runtime`這不是必要的旗標。 |

### <a name="the-runtime-image-steps"></a>執行時間映射步驟

| 步驟 | 描述 |
| ---- | ----------- |
| `FROM ...` | 宣告新的基底映射。 |
| `WORKDIR /app` | `/app`建立目錄，並將它設定為目前的工作目錄。 |
| `COPY --from=builder ...` | 使用第`builder` `FROM`一行中的別名，從上一個映射複製已發行的應用程式。 |
| `ENTRYPOINT [ ... ]` | 設定要在容器啟動時執行的命令。 運行`dotnet`時間映射中的命令只能執行 DLL 檔案。 |

### <a name="https-in-docker"></a>Docker 中的 HTTPS

適用于 Docker 的 Microsoft 基底映射`ASPNETCORE_URLS`會將環境`http://+:80`變數設定為，這表示 Kestrel 會在該埠上不搭配 HTTPS 來執行。 如果您使用 HTTPS 搭配自訂憑證（如上[一節](self-hosted.md)所述），您應該**在 Dockerfile 的執行時間映射建立部分中**設定環境變數來覆寫此項。

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a>.Dockerignore 檔案

與從`.gitignore`原始檔控制中排除特定檔案和目錄的檔案很`.dockerignore`類似，檔案可以用來排除檔案和目錄，使其不會在組建期間複製到映射。 這不僅能節省時間，還可以避免因將電腦上的`obj`目錄複寫到映射而造成的一些困惑錯誤。 您至少應為檔案新增和`bin` `obj` `.dockerignore`的專案。

```console
bin/
obj/
```

## <a name="build-the-image"></a>建立映像

針對具有單一應用程式的解決方案，因此是單一 Dockerfile，最簡單的方式是將 Dockerfile 放在基底目錄中;也就是與檔案相同的目錄`.sln` 。 在此情況下，若要建立映射，請在`docker build`包含 Dockerfile 的目錄中使用下列命令。

```console
docker build --tag stockdata .
```

Confusingly 命名`--tag`的旗標（可以縮短為`-t`）會指定影像的完整名稱，*包括*實際的標記（如果有指定的話）。 結尾`.`的會指定要在其中執行組建的*內容*，也就是 Dockerfile 中`COPY`命令的目前工作目錄。

如果您在單一方案中有多個應用程式，您可以將每個應用程式的 Dockerfile 保留在該檔案`.csproj`的資料夾中，但您仍應`docker build`從基底目錄執行命令，以確保解決方案和所有專案都會複製到影像中。 您可以使用`--file` （或`-f`）旗標，在目前目錄底下指定 Dockerfile。

```console
docker build --tag stockdata --file src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a>在您電腦上的容器中執行映射

若要在本機 Docker 實例中執行映射，請使用`docker run`命令。

```console
docker run -ti -p 5000:80 stockdata
```

`-ti`旗標會將您目前的終端機連接到容器的終端機，並在互動模式中執行。 會將容器上的埠 80發佈（連結）至localhost網路介面上的埠80。`-p 5000:80`

## <a name="push-the-image-to-a-registry"></a>將映射推送至登錄

確認映射運作後，您需要將它推送到 Docker 登錄，讓它可在其他系統上使用。 內部網路將需要布建 Docker 登錄。 這可以像執行[docker 本身`registry`的映射](https://docs.docker.com/registry/deploying/)一樣簡單（也就是 docker 登錄會在 docker 容器中執行），但有各種更全面的解決方案可供使用。 針對外部共用和雲端使用，有各種可用的受控登錄，例如[Azure Container Registry](https://docs.microsoft.com/azure/container-registry/)或[Docker Hub](https://docs.docker.com/docker-hub/repos/)。

若要推送至 Docker Hub，請在映射名稱前面加上您的使用者或組織名稱。

```console
docker tag stockdata myorg/stockdata
docker push myorg/stockdata
```

若要推送至私用登錄，請在映射名稱前面加上登錄主機名稱和組織名稱。

```console
docker tag stockdata internal-registry:5000/myorg/stockdata
docker push internal-registry:5000/myorg/stockdata
```

一旦映射位於登錄中，您就可以將它部署到個別的 Docker 主機或容器協調流程引擎（例如 Kubernetes）。

>[!div class="step-by-step"]
>[上一頁](self-hosted.md)
>[下一頁](kubernetes.md)
