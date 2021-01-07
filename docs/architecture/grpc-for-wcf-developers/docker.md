---
title: 適用于 WCF 開發人員的 Docker gRPC
description: 建立 ASP.NET Core gRPC 應用程式的 Docker 映射
ms.date: 01/06/2021
ms.openlocfilehash: f59518a28b0a1dee75c792ba03bd4af826638502
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970085"
---
# <a name="create-docker-images"></a><span data-ttu-id="56add-103">建立 Docker 映射</span><span class="sxs-lookup"><span data-stu-id="56add-103">Create Docker images</span></span>

<span data-ttu-id="56add-104">本節說明如何建立 ASP.NET Core gRPC 應用程式的 Docker 映射，並準備好在 Docker、Kubernetes 或其他容器環境中執行。</span><span class="sxs-lookup"><span data-stu-id="56add-104">This section covers the creation of Docker images for ASP.NET Core gRPC applications, ready to run in Docker, Kubernetes, or other container environments.</span></span> <span data-ttu-id="56add-105">使用 ASP.NET Core MVC web 應用程式和 gRPC 服務的範例應用程式，可在 GitHub 上的 [dotnet 架構/gRPC-適用于 wcf 的開發人員](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) 存放庫中取得。</span><span class="sxs-lookup"><span data-stu-id="56add-105">The sample application used, with an ASP.NET Core MVC web app and a gRPC service, is available on the [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) repository on GitHub.</span></span>

## <a name="microsoft-base-images-for-aspnet-core-applications"></a><span data-ttu-id="56add-106">適用于 ASP.NET Core 應用程式的 Microsoft 基礎映射</span><span class="sxs-lookup"><span data-stu-id="56add-106">Microsoft base images for ASP.NET Core applications</span></span>

<span data-ttu-id="56add-107">Microsoft 提供一系列基礎映射來建立和執行 .NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="56add-107">Microsoft provides a range of base images for building and running .NET applications.</span></span> <span data-ttu-id="56add-108">若要建立 ASP.NET Core 5.0 映射，您可以使用兩個基底映射：</span><span class="sxs-lookup"><span data-stu-id="56add-108">To create an ASP.NET Core 5.0 image, you use two base images:</span></span>

- <span data-ttu-id="56add-109">用來建立和發佈應用程式的 SDK 映射。</span><span class="sxs-lookup"><span data-stu-id="56add-109">An SDK image to build and publish the application.</span></span>
- <span data-ttu-id="56add-110">用於部署的執行時間映射。</span><span class="sxs-lookup"><span data-stu-id="56add-110">A runtime image for deployment.</span></span>

| <span data-ttu-id="56add-111">映像</span><span class="sxs-lookup"><span data-stu-id="56add-111">Image</span></span> | <span data-ttu-id="56add-112">描述</span><span class="sxs-lookup"><span data-stu-id="56add-112">Description</span></span> |
| ----- | ----------- |
| [<span data-ttu-id="56add-113">mcr.microsoft.com/dotnet/sdk</span><span class="sxs-lookup"><span data-stu-id="56add-113">mcr.microsoft.com/dotnet/sdk</span></span>](https://hub.docker.com/_/microsoft-dotnet-sdk/) | <span data-ttu-id="56add-114">用來建立應用程式 `docker build` 。</span><span class="sxs-lookup"><span data-stu-id="56add-114">For building applications with `docker build`.</span></span> <span data-ttu-id="56add-115">不要用在生產環境中。</span><span class="sxs-lookup"><span data-stu-id="56add-115">Not to be used in production.</span></span> |
| [<span data-ttu-id="56add-116">mcr.microsoft.com/dotnet/aspnet</span><span class="sxs-lookup"><span data-stu-id="56add-116">mcr.microsoft.com/dotnet/aspnet</span></span>](https://hub.docker.com/_/microsoft-dotnet-aspnet/) | <span data-ttu-id="56add-117">包含執行時間和 ASP.NET Core 相依性。</span><span class="sxs-lookup"><span data-stu-id="56add-117">Contains the runtime and ASP.NET Core dependencies.</span></span> <span data-ttu-id="56add-118">適用于生產環境。</span><span class="sxs-lookup"><span data-stu-id="56add-118">For production.</span></span> |

<span data-ttu-id="56add-119">每個映射都有四個以不同 Linux 散發套件為基礎的變化，並依標記區分。</span><span class="sxs-lookup"><span data-stu-id="56add-119">For each image, there are four variants based on different Linux distributions, distinguished by tags.</span></span>

| <span data-ttu-id="56add-120">影像標記 (s) </span><span class="sxs-lookup"><span data-stu-id="56add-120">Image tag(s)</span></span> | <span data-ttu-id="56add-121">Linux</span><span class="sxs-lookup"><span data-stu-id="56add-121">Linux</span></span> | <span data-ttu-id="56add-122">附註</span><span class="sxs-lookup"><span data-stu-id="56add-122">Notes</span></span> |
| --------- | ----- | ----- |
| <span data-ttu-id="56add-123">5.0-buster-超薄、5。0</span><span class="sxs-lookup"><span data-stu-id="56add-123">5.0-buster-slim, 5.0</span></span> | <span data-ttu-id="56add-124">Debian 10</span><span class="sxs-lookup"><span data-stu-id="56add-124">Debian 10</span></span> | <span data-ttu-id="56add-125">如果未指定作業系統變數，則為預設映射。</span><span class="sxs-lookup"><span data-stu-id="56add-125">The default image if no OS variant is specified.</span></span> |
| <span data-ttu-id="56add-126">5.0-alpine</span><span class="sxs-lookup"><span data-stu-id="56add-126">5.0-alpine</span></span> | <span data-ttu-id="56add-127">Alpine 3.12</span><span class="sxs-lookup"><span data-stu-id="56add-127">Alpine 3.12</span></span> | <span data-ttu-id="56add-128">Alpine 基底映射遠小於 Debian 或 Ubuntu。</span><span class="sxs-lookup"><span data-stu-id="56add-128">Alpine base images are much smaller than Debian or Ubuntu ones.</span></span> |
| <span data-ttu-id="56add-129">5.0-焦點</span><span class="sxs-lookup"><span data-stu-id="56add-129">5.0-focal</span></span>| <span data-ttu-id="56add-130">Ubuntu 20.04</span><span class="sxs-lookup"><span data-stu-id="56add-130">Ubuntu 20.04</span></span> | |

<span data-ttu-id="56add-131">Alpine 基底映射大約是 100 MB，相較于 Debian 和 Ubuntu 映射的 200 MB。</span><span class="sxs-lookup"><span data-stu-id="56add-131">The Alpine base image is around 100 MB, compared to 200 MB for the Debian and Ubuntu images.</span></span> <span data-ttu-id="56add-132">某些軟體套件或程式庫可能無法在 Alpine 的套件管理中使用。</span><span class="sxs-lookup"><span data-stu-id="56add-132">Some software packages or libraries might not be available in Alpine's package management.</span></span> <span data-ttu-id="56add-133">如果您不確定要使用哪個映射，您應該選擇預設 Debian。</span><span class="sxs-lookup"><span data-stu-id="56add-133">If you're not sure which image to use, you should probably choose the default Debian.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="56add-134">請確定您針對組建和執行時間使用相同的 Linux 變體。</span><span class="sxs-lookup"><span data-stu-id="56add-134">Make sure you use the same variant of Linux for the build and the runtime.</span></span> <span data-ttu-id="56add-135">在某個變異上建立併發布的應用程式可能無法在另一個變數上運作。</span><span class="sxs-lookup"><span data-stu-id="56add-135">Applications built and published on one variant might not work on another.</span></span>

## <a name="create-a-docker-image"></a><span data-ttu-id="56add-136">建立 Docker 映像</span><span class="sxs-lookup"><span data-stu-id="56add-136">Create a Docker image</span></span>

<span data-ttu-id="56add-137">Docker 映射是由 *Dockerfile* 所定義。</span><span class="sxs-lookup"><span data-stu-id="56add-137">A Docker image is defined by a *Dockerfile*.</span></span> <span data-ttu-id="56add-138">此 *Dockerfile* 是一個文字檔，其中包含建立應用程式所需的所有命令，並安裝建立或執行應用程式所需的任何相依性。</span><span class="sxs-lookup"><span data-stu-id="56add-138">This *Dockerfile* is a text file that contains all the commands needed to build the application and install any dependencies that are required for either building or running the application.</span></span> <span data-ttu-id="56add-139">下列範例顯示 ASP.NET Core 5.0 應用程式的最簡單 Dockerfile：</span><span class="sxs-lookup"><span data-stu-id="56add-139">The following example shows the simplest Dockerfile for an ASP.NET Core 5.0 application:</span></span>

```dockerfile
FROM mcr.microsoft.com/dotnet/sdk:5.0 as build

WORKDIR /src

COPY ./StockKube.sln .
COPY ./src/StockData/StockData.csproj ./src/StockData/
COPY ./src/StockWeb/StockWeb.csproj ./src/StockWeb/

RUN dotnet restore

COPY . .

RUN dotnet publish --no-restore -c Release -o /published src/StockData/StockData.csproj

FROM mcr.microsoft.com/dotnet/aspnet:5.0 as runtime

# Uncomment the line below if running with HTTPS
# ENV ASPNETCORE_URLS=https://+:443

WORKDIR /app

COPY --from=build /published .

ENTRYPOINT [ "dotnet", "StockData.dll" ]
```

<span data-ttu-id="56add-140">Dockerfile 有兩個部分：第一個是使用 `sdk` 基底映射來建立和發佈應用程式，第二個部分則會從基底建立執行時間映射 `aspnet` 。</span><span class="sxs-lookup"><span data-stu-id="56add-140">The Dockerfile has two parts: the first uses the `sdk` base image to build and publish the application; the second creates a runtime image from the `aspnet` base.</span></span> <span data-ttu-id="56add-141">這是因為 `sdk` 影像大約是 900 MB，相較于執行時間影像大約 200 mb，而且在執行時間中，大部分的內容都是不必要的。</span><span class="sxs-lookup"><span data-stu-id="56add-141">This is because the `sdk` image is around 900 MB, compared to around 200 MB for the runtime image, and most of its contents are unnecessary at runtime.</span></span>

### <a name="the-build-steps"></a><span data-ttu-id="56add-142">組建步驟</span><span class="sxs-lookup"><span data-stu-id="56add-142">The build steps</span></span>

| <span data-ttu-id="56add-143">步驟</span><span class="sxs-lookup"><span data-stu-id="56add-143">Step</span></span> | <span data-ttu-id="56add-144">描述</span><span class="sxs-lookup"><span data-stu-id="56add-144">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="56add-145">宣告基底映射並指派 `builder` 別名。</span><span class="sxs-lookup"><span data-stu-id="56add-145">Declares the base image and assigns the `builder` alias.</span></span> |
| `WORKDIR /src` | <span data-ttu-id="56add-146">建立 `/src` 目錄，並將它設定為目前的工作目錄。</span><span class="sxs-lookup"><span data-stu-id="56add-146">Creates the `/src` directory and sets it as the current working directory.</span></span> |
| `COPY . .` | <span data-ttu-id="56add-147">將主機上目前目錄下的所有內容複寫到映射的目前目錄中。</span><span class="sxs-lookup"><span data-stu-id="56add-147">Copies everything below the current directory on the host into the current directory on the image.</span></span> |
| `RUN dotnet restore` | <span data-ttu-id="56add-148">還原任何 (ASP.NET Core 3.0 framework 的外部套件都會隨 SDK) 預先安裝。</span><span class="sxs-lookup"><span data-stu-id="56add-148">Restores any external packages (ASP.NET Core 3.0 framework is pre-installed with the SDK).</span></span> |
| `RUN dotnet publish ...` | <span data-ttu-id="56add-149">建立併發行發行組建。</span><span class="sxs-lookup"><span data-stu-id="56add-149">Builds and publishes a Release build.</span></span> <span data-ttu-id="56add-150">請注意， `--runtime` 不需要旗標。</span><span class="sxs-lookup"><span data-stu-id="56add-150">Note that the `--runtime` flag isn't required.</span></span> |

### <a name="the-runtime-image-steps"></a><span data-ttu-id="56add-151">執行時間映射步驟</span><span class="sxs-lookup"><span data-stu-id="56add-151">The runtime image steps</span></span>

| <span data-ttu-id="56add-152">步驟</span><span class="sxs-lookup"><span data-stu-id="56add-152">Step</span></span> | <span data-ttu-id="56add-153">描述</span><span class="sxs-lookup"><span data-stu-id="56add-153">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="56add-154">宣告新的基底映射。</span><span class="sxs-lookup"><span data-stu-id="56add-154">Declares a new base image.</span></span> |
| `WORKDIR /app` | <span data-ttu-id="56add-155">建立 `/app` 目錄，並將它設定為目前的工作目錄。</span><span class="sxs-lookup"><span data-stu-id="56add-155">Creates the `/app` directory and sets it as the current working directory.</span></span> |
| `COPY --from=builder ...` | <span data-ttu-id="56add-156">使用第一行的別名，從上一個影像複製已發行的應用程式 `builder` `FROM` 。</span><span class="sxs-lookup"><span data-stu-id="56add-156">Copies the published application from the previous image, by using the `builder` alias from the first `FROM` line.</span></span> |
| `ENTRYPOINT [ ... ]` | <span data-ttu-id="56add-157">設定要在容器啟動時執行的命令。</span><span class="sxs-lookup"><span data-stu-id="56add-157">Sets the command to run when the container starts.</span></span> <span data-ttu-id="56add-158">`dotnet`執行時間映射中的命令只能執行 DLL 檔案。</span><span class="sxs-lookup"><span data-stu-id="56add-158">The `dotnet` command in the runtime image can only run DLL files.</span></span> |

### <a name="https-in-docker"></a><span data-ttu-id="56add-159">Docker 中的 HTTPS</span><span class="sxs-lookup"><span data-stu-id="56add-159">HTTPS in Docker</span></span>

<span data-ttu-id="56add-160">適用于 Docker 的 Microsoft 基礎映射 `ASPNETCORE_URLS` 會將環境變數設為 `http://+:80` ，這表示 Kestrel 會在該埠上執行而不需要 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="56add-160">Microsoft base images for Docker set the `ASPNETCORE_URLS` environment variable to `http://+:80`, meaning that Kestrel runs without HTTPS on that port.</span></span> <span data-ttu-id="56add-161">如果您使用 HTTPS 與自訂憑證 (如 [自我裝載 gRPC 應用程式](self-hosted.md)) 中所述，您應覆寫此設定。</span><span class="sxs-lookup"><span data-stu-id="56add-161">If you're using HTTPS with a custom certificate (as described in [Self-hosted gRPC applications](self-hosted.md)), you should override this configuration.</span></span> <span data-ttu-id="56add-162">在 Dockerfile 的執行時間映射建立部分中設定環境變數。</span><span class="sxs-lookup"><span data-stu-id="56add-162">Set the environment variable in the runtime image creation part of your Dockerfile.</span></span>

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/aspnet:5.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a><span data-ttu-id="56add-163">>.dockerignore 檔案</span><span class="sxs-lookup"><span data-stu-id="56add-163">The .dockerignore file</span></span>

<span data-ttu-id="56add-164">就像 `.gitignore` 從原始檔控制中排除特定檔案和目錄的檔案一樣，檔案 `.dockerignore` 可以用來排除檔案和目錄，不要在組建期間複製到映射中。</span><span class="sxs-lookup"><span data-stu-id="56add-164">Much like `.gitignore` files that exclude certain files and directories from source control, the `.dockerignore` file can be used to exclude files and directories from being copied to the image during build.</span></span> <span data-ttu-id="56add-165">這個檔案不僅能節省時間的複製，也可以避免將電腦上的 `obj` 目錄複寫到映射時所發生的一些錯誤。</span><span class="sxs-lookup"><span data-stu-id="56add-165">This file not only saves time copying, but can also avoid some errors that arise from having the `obj` directory from your PC copied into the image.</span></span> <span data-ttu-id="56add-166">您至少應該在檔案中加入和的 `bin` 專案 `obj` `.dockerignore` 。</span><span class="sxs-lookup"><span data-stu-id="56add-166">At a minimum, you should add entries for `bin` and `obj` to your `.dockerignore` file.</span></span>

```console
bin/
obj/
```

## <a name="build-the-image"></a><span data-ttu-id="56add-167">建立映像</span><span class="sxs-lookup"><span data-stu-id="56add-167">Build the image</span></span>

<span data-ttu-id="56add-168">針對 `StockKube.sln` 包含兩個不同應用程式 `StockData` 和的方案 `StockWeb` ，最簡單的方式是將每個應用程式的 Dockerfile 放在基底目錄中。</span><span class="sxs-lookup"><span data-stu-id="56add-168">For a `StockKube.sln` solution containing two different applications `StockData` and `StockWeb`, it's simplest to put the Dockerfile for each one of them in the base directory.</span></span> <span data-ttu-id="56add-169">在此情況下，若要建立映射，請 `docker build` 從檔案所在的相同目錄中使用下列命令 `.sln` 。</span><span class="sxs-lookup"><span data-stu-id="56add-169">In that case, to build the image, use the following `docker build` command from the same directory where `.sln` file resides.</span></span>

```console
docker build -t stockdata:1.0.0 -f ./src/StockData/Dockerfile .
```

<span data-ttu-id="56add-170">Confusingly 命名的 `--tag` 旗標 (可以縮短為 `-t`) 指定影像的整個名稱，包括實際標記（如果有指定的話）。</span><span class="sxs-lookup"><span data-stu-id="56add-170">The confusingly named `--tag` flag (which can be shortened to `-t`) specifies the whole name of the image, including the actual tag if specified.</span></span> <span data-ttu-id="56add-171">`.`結束時，會指定將在其中執行組建的內容; `COPY` Dockerfile 中命令的目前工作目錄。</span><span class="sxs-lookup"><span data-stu-id="56add-171">The `.` at the end specifies the context in which the build will be run; the current working directory for the `COPY` commands in the Dockerfile.</span></span>

<span data-ttu-id="56add-172">如果您在單一解決方案中有多個應用程式，您可以將每個應用程式的 Dockerfile 保留在檔案旁的資料夾中 `.csproj` 。</span><span class="sxs-lookup"><span data-stu-id="56add-172">If you have multiple applications within a single solution, you can keep the Dockerfile for each application in its own folder, beside the `.csproj` file.</span></span> <span data-ttu-id="56add-173">您仍然應該 `docker build` 從基底目錄執行此命令，以確保方案和所有專案都會複製到映射中。</span><span class="sxs-lookup"><span data-stu-id="56add-173">You should still run the `docker build` command from the base directory to ensure that the solution and all the projects are copied into the image.</span></span> <span data-ttu-id="56add-174">您可以使用 `--file` (或) 旗標，在目前的目錄下指定 Dockerfile `-f` 。</span><span class="sxs-lookup"><span data-stu-id="56add-174">You can specify a Dockerfile below the current directory by using the `--file` (or `-f`) flag.</span></span>

```console
docker build -t stockdata:1.0.0 -f ./src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a><span data-ttu-id="56add-175">在您電腦上的容器中執行映射</span><span class="sxs-lookup"><span data-stu-id="56add-175">Run the image in a container on your machine</span></span>

<span data-ttu-id="56add-176">若要在您的本機 Docker 實例中執行映射，請使用 `docker run` 命令。</span><span class="sxs-lookup"><span data-stu-id="56add-176">To run the image in your local Docker instance, use the `docker run` command.</span></span>

```console
docker run -ti -p 5000:80 stockdata:1.0.0
```

<span data-ttu-id="56add-177">旗標會將 `-ti` 您目前的終端機連接到容器的終端機，並在互動模式中執行。</span><span class="sxs-lookup"><span data-stu-id="56add-177">The `-ti` flag connects your current terminal to the container's terminal, and runs in interactive mode.</span></span> <span data-ttu-id="56add-178">會將 `-p 5000:80` 容器上的埠 80) 的 (連結發佈到 localhost 網路介面上的埠5000。</span><span class="sxs-lookup"><span data-stu-id="56add-178">The `-p 5000:80` publishes (links) port 80 on the container to port 5000 on the localhost network interface.</span></span>

## <a name="push-the-image-to-a-registry"></a><span data-ttu-id="56add-179">將映像推送至登錄</span><span class="sxs-lookup"><span data-stu-id="56add-179">Push the image to a registry</span></span>

<span data-ttu-id="56add-180">確認映射可正常運作之後，請將它推送到 Docker 登錄，使其可在其他系統上使用。</span><span class="sxs-lookup"><span data-stu-id="56add-180">After you've verified that the image works, push it to a Docker registry to make it available on other systems.</span></span> <span data-ttu-id="56add-181">內部網路將需要布建 Docker 登錄。</span><span class="sxs-lookup"><span data-stu-id="56add-181">Internal networks will need to provision a Docker registry.</span></span> <span data-ttu-id="56add-182">此活動可以像是執行 [docker 本身的 `registry` 映射](https://docs.docker.com/registry/deploying/) 一樣簡單 (docker 登錄是在 docker 容器) 中執行，但是有各種更全面的解決方案可供使用。</span><span class="sxs-lookup"><span data-stu-id="56add-182">This activity can be as simple as running [Docker's own `registry` image](https://docs.docker.com/registry/deploying/) (the Docker registry runs in a Docker container), but there are various more comprehensive solutions available.</span></span> <span data-ttu-id="56add-183">針對外部共用和雲端用途，有各種可用的受控登錄，例如 [Azure Container Registry](/azure/container-registry/) 或 [Docker Hub](https://docs.docker.com/docker-hub/repos/)。</span><span class="sxs-lookup"><span data-stu-id="56add-183">For external sharing and cloud use, there are various managed registries available, such as [Azure Container Registry](/azure/container-registry/) or [Docker Hub](https://docs.docker.com/docker-hub/repos/).</span></span>

<span data-ttu-id="56add-184">若要推送至 Docker Hub，請在映射名稱前加上您的使用者或組織名稱。</span><span class="sxs-lookup"><span data-stu-id="56add-184">To push to Docker Hub, prefix the image name with your user or organization name.</span></span>

```console
docker tag stockdata:1.0.0 <myorg>/stockdata:1.0.0
docker push <myorg>/stockdata:1.0.0
```

<span data-ttu-id="56add-185">若要推送至私人登錄，請在映射名稱前加上登錄主機名稱和組織名稱。</span><span class="sxs-lookup"><span data-stu-id="56add-185">To push to a private registry, prefix the image name with the registry host name and the organization name.</span></span>

```console
docker tag stockdata <internal-registry:5000>/<myorg>/stockdata:1.0.0
docker push <internal-registry:5000>/<myorg>/stockdata:1.0.0
```

<span data-ttu-id="56add-186">映射在登錄中之後，您可以將它部署到個別的 Docker 主機或容器協調流程引擎（例如 Kubernetes）。</span><span class="sxs-lookup"><span data-stu-id="56add-186">After the image is in a registry, you can deploy it to individual Docker hosts, or to a container orchestration engine like Kubernetes.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="56add-187">[上一個](self-hosted.md) 
>[下一步](kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="56add-187">[Previous](self-hosted.md)
[Next](kubernetes.md)</span></span>
