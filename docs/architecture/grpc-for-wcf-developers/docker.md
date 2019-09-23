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
# <a name="docker"></a><span data-ttu-id="a1c4a-103">Docker</span><span class="sxs-lookup"><span data-stu-id="a1c4a-103">Docker</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="a1c4a-104">本節將討論如何為 ASP.NET Core gRPC 應用程式建立 Docker 映射，並準備好在 Docker、Kubernetes 或其他容器環境中執行。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-104">This section will cover the creation of Docker images for ASP.NET Core gRPC applications, ready to run in Docker, Kubernetes, or other container environments.</span></span> <span data-ttu-id="a1c4a-105">使用 ASP.NET Core MVC web 應用程式和 gRPC 服務的範例應用程式，可在 GitHub 上的[RendleLabs/gRPC-wcf 開發人員](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample)存放庫中取得。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-105">The sample application used, with an ASP.NET Core MVC web app and a gRPC service, is available on the [RendleLabs/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) repository on GitHub.</span></span>

## <a name="microsoft-base-images-for-aspnet-core-applications"></a><span data-ttu-id="a1c4a-106">適用于 ASP.NET Core 應用程式的 Microsoft 基底映射</span><span class="sxs-lookup"><span data-stu-id="a1c4a-106">Microsoft base images for ASP.NET Core applications</span></span>

<span data-ttu-id="a1c4a-107">Microsoft 提供各種基底映射來建立和執行 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-107">Microsoft provides a range of base images for building and running .NET Core applications.</span></span> <span data-ttu-id="a1c4a-108">若要建立 ASP.NET Core 3.0 映射，會使用兩個基底映射：用來建立及發佈應用程式的 SDK 映射，以及用於部署的執行時間映射。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-108">To create an ASP.NET Core 3.0 image, two base images are used: an SDK image to build and publish the application, and a runtime image for deployment.</span></span>

| <span data-ttu-id="a1c4a-109">Image</span><span class="sxs-lookup"><span data-stu-id="a1c4a-109">Image</span></span> | <span data-ttu-id="a1c4a-110">描述</span><span class="sxs-lookup"><span data-stu-id="a1c4a-110">Description</span></span> |
| ----- | ----------- |
| [<span data-ttu-id="a1c4a-111">mcr.microsoft.com/dotnet/core/sdk</span><span class="sxs-lookup"><span data-stu-id="a1c4a-111">mcr.microsoft.com/dotnet/core/sdk</span></span>](https://hub.docker.com/_/microsoft-dotnet-core-sdk/) | <span data-ttu-id="a1c4a-112">用於建立使用`docker build`的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-112">For building applications with `docker build`.</span></span> <span data-ttu-id="a1c4a-113">不會在生產環境中使用。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-113">Not to be used in production.</span></span> |
| [<span data-ttu-id="a1c4a-114">mcr.microsoft.com/dotnet/core/aspnet</span><span class="sxs-lookup"><span data-stu-id="a1c4a-114">mcr.microsoft.com/dotnet/core/aspnet</span></span>](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) | <span data-ttu-id="a1c4a-115">包含執行時間和 ASP.NET Core 相依性。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-115">Contains the runtime and ASP.NET Core dependencies.</span></span> <span data-ttu-id="a1c4a-116">適用于生產環境。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-116">For production.</span></span> |

<span data-ttu-id="a1c4a-117">針對每個映射，有四個以不同 Linux 散發套件為基礎的變體，以標記區分。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-117">For each image, there are four variants based on different Linux distributions, distinguished by tags.</span></span>

| <span data-ttu-id="a1c4a-118">映射標記</span><span class="sxs-lookup"><span data-stu-id="a1c4a-118">Image tag(s)</span></span> | <span data-ttu-id="a1c4a-119">Linux</span><span class="sxs-lookup"><span data-stu-id="a1c4a-119">Linux</span></span> | <span data-ttu-id="a1c4a-120">注意</span><span class="sxs-lookup"><span data-stu-id="a1c4a-120">Notes</span></span> |
| --------- | ----- | ----- |
| <span data-ttu-id="a1c4a-121">3.0-buster、3。0</span><span class="sxs-lookup"><span data-stu-id="a1c4a-121">3.0-buster, 3.0</span></span> | <span data-ttu-id="a1c4a-122">Debian 10</span><span class="sxs-lookup"><span data-stu-id="a1c4a-122">Debian 10</span></span> | <span data-ttu-id="a1c4a-123">如果未指定 OS variant，則為預設映射。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-123">The default image if no OS variant is specified.</span></span> |
| <span data-ttu-id="a1c4a-124">3.0-alpine</span><span class="sxs-lookup"><span data-stu-id="a1c4a-124">3.0-alpine</span></span> | <span data-ttu-id="a1c4a-125">Alpine 3。9</span><span class="sxs-lookup"><span data-stu-id="a1c4a-125">Alpine 3.9</span></span> | <span data-ttu-id="a1c4a-126">Alpine 基底映射的大小遠低於 Debian 或 Ubuntu。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-126">Alpine base images are much smaller than Debian or Ubuntu ones.</span></span> |
| <span data-ttu-id="a1c4a-127">3.0-disco</span><span class="sxs-lookup"><span data-stu-id="a1c4a-127">3.0-disco</span></span> | <span data-ttu-id="a1c4a-128">Ubuntu 19.04</span><span class="sxs-lookup"><span data-stu-id="a1c4a-128">Ubuntu 19.04</span></span> | |
| <span data-ttu-id="a1c4a-129">3.0-bionic</span><span class="sxs-lookup"><span data-stu-id="a1c4a-129">3.0-bionic</span></span> | <span data-ttu-id="a1c4a-130">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="a1c4a-130">Ubuntu 18.04</span></span> | |

<span data-ttu-id="a1c4a-131">相較于 200 MB，Debian 和 Ubuntu 映射的 Alpine 基底映射大約是 100 MB，但某些軟體套件或程式庫可能無法在 Alpine 的套件管理中使用。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-131">The Alpine base image is around 100 MB, compared to 200 MB for the Debian and Ubuntu images, but some software packages or libraries may not be available in Alpine's package management.</span></span> <span data-ttu-id="a1c4a-132">如果您不確定要使用哪一個影像，最好先使用預設的 Debian，除非您有很大的需求，才能使用不同的散發版本。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-132">If you're not sure which image to use, it's best to stick to the default Debian unless you have a compelling need to use a different distro.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a1c4a-133">請確定您針對組建和執行時間使用相同的 Linux 變體。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-133">Make sure you use the same variant of Linux for the build and the runtime.</span></span> <span data-ttu-id="a1c4a-134">在某個 variant 上建立和發行的應用程式可能無法在另一個變數上使用。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-134">Applications built and published on one variant may not work on another.</span></span>

## <a name="create-a-docker-image"></a><span data-ttu-id="a1c4a-135">建立 Docker 映射</span><span class="sxs-lookup"><span data-stu-id="a1c4a-135">Create a Docker image</span></span>

<span data-ttu-id="a1c4a-136">Docker 映射是由*Dockerfile*所定義，這是一個文字檔，其中包含建立應用程式及安裝建立或執行應用程式所需之任何相依性所需的所有命令。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-136">A Docker image is defined by a *Dockerfile*, a text file that contains all the commands that are needed to build the application and install any dependencies that are required for either building or running the application.</span></span> <span data-ttu-id="a1c4a-137">下列範例顯示 ASP.NET Core 3.0 應用程式的最簡單 Dockerfile：</span><span class="sxs-lookup"><span data-stu-id="a1c4a-137">The following example shows the simplest Dockerfile for an ASP.NET Core 3.0 application:</span></span>

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

<span data-ttu-id="a1c4a-138">Dockerfile 有兩個部分：第一個是使用`sdk`基底映射來建立和發行應用程式; 第二個是`aspnet`從基底建立執行時間映射。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-138">The Dockerfile has two parts: the first uses the `sdk` base image to build and publish the application; the second creates a runtime image from the `aspnet` base.</span></span> <span data-ttu-id="a1c4a-139">這是因為`sdk`相較于執行時間映射約 200 mb，映射大約是 900 mb，而且在執行時間時，大部分的內容都是不必要的。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-139">This is because the `sdk` image is around 900 MB compared to around 200 MB for the runtime image, and most of its contents are unnecessary at runtime.</span></span>

### <a name="the-build-steps"></a><span data-ttu-id="a1c4a-140">組建步驟</span><span class="sxs-lookup"><span data-stu-id="a1c4a-140">The build steps</span></span>

| <span data-ttu-id="a1c4a-141">步驟</span><span class="sxs-lookup"><span data-stu-id="a1c4a-141">Step</span></span> | <span data-ttu-id="a1c4a-142">描述</span><span class="sxs-lookup"><span data-stu-id="a1c4a-142">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="a1c4a-143">宣告基底映射並指派`builder`別名（如需說明，請參閱下一節）。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-143">Declares the base image and assigns the `builder` alias (see next section for explanation).</span></span> |
| `WORKDIR /src` | <span data-ttu-id="a1c4a-144">`/src`建立目錄，並將它設定為目前的工作目錄。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-144">Creates the `/src` directory and sets it as the current working directory.</span></span> |
| `COPY . .` | <span data-ttu-id="a1c4a-145">將主機上目前目錄底下的所有內容複寫到映射上的目前目錄中。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-145">Copies everything below the current directory on the host into the current directory on the image.</span></span> |
| `RUN dotnet restore` | <span data-ttu-id="a1c4a-146">還原任何外部套件（ASP.NET Core 3.0 framework 已預先安裝 SDK）。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-146">Restores any external packages (ASP.NET Core 3.0 framework is pre-installed with the SDK).</span></span> |
| `RUN dotnet publish ...` | <span data-ttu-id="a1c4a-147">建立併發行發行組建。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-147">Builds and publishes a Release build.</span></span> <span data-ttu-id="a1c4a-148">請注意， `--runtime`這不是必要的旗標。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-148">Note that the `--runtime` flag isn't required.</span></span> |

### <a name="the-runtime-image-steps"></a><span data-ttu-id="a1c4a-149">執行時間映射步驟</span><span class="sxs-lookup"><span data-stu-id="a1c4a-149">The runtime image steps</span></span>

| <span data-ttu-id="a1c4a-150">步驟</span><span class="sxs-lookup"><span data-stu-id="a1c4a-150">Step</span></span> | <span data-ttu-id="a1c4a-151">描述</span><span class="sxs-lookup"><span data-stu-id="a1c4a-151">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="a1c4a-152">宣告新的基底映射。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-152">Declares a new base image.</span></span> |
| `WORKDIR /app` | <span data-ttu-id="a1c4a-153">`/app`建立目錄，並將它設定為目前的工作目錄。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-153">Creates the `/app` directory and sets it as the current working directory.</span></span> |
| `COPY --from=builder ...` | <span data-ttu-id="a1c4a-154">使用第`builder` `FROM`一行中的別名，從上一個映射複製已發行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-154">Copies the published application from the previous image, using the `builder` alias from the first `FROM` line.</span></span> |
| `ENTRYPOINT [ ... ]` | <span data-ttu-id="a1c4a-155">設定要在容器啟動時執行的命令。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-155">Sets the command to run when the container starts.</span></span> <span data-ttu-id="a1c4a-156">運行`dotnet`時間映射中的命令只能執行 DLL 檔案。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-156">The `dotnet` command in the runtime image can only run DLL files.</span></span> |

### <a name="https-in-docker"></a><span data-ttu-id="a1c4a-157">Docker 中的 HTTPS</span><span class="sxs-lookup"><span data-stu-id="a1c4a-157">HTTPS in Docker</span></span>

<span data-ttu-id="a1c4a-158">適用于 Docker 的 Microsoft 基底映射`ASPNETCORE_URLS`會將環境`http://+:80`變數設定為，這表示 Kestrel 會在該埠上不搭配 HTTPS 來執行。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-158">Microsoft's base images for Docker set the `ASPNETCORE_URLS` environment variable to `http://+:80`, meaning that Kestrel will run without HTTPS on that port.</span></span> <span data-ttu-id="a1c4a-159">如果您使用 HTTPS 搭配自訂憑證（如上[一節](self-hosted.md)所述），您應該**在 Dockerfile 的執行時間映射建立部分中**設定環境變數來覆寫此項。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-159">If you're using HTTPS with a custom certificate (as described in [the previous section](self-hosted.md)), you should override this by setting the environment variable **in the runtime image creation part** of your Dockerfile.</span></span>

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a><span data-ttu-id="a1c4a-160">.Dockerignore 檔案</span><span class="sxs-lookup"><span data-stu-id="a1c4a-160">The .dockerignore file</span></span>

<span data-ttu-id="a1c4a-161">與從`.gitignore`原始檔控制中排除特定檔案和目錄的檔案很`.dockerignore`類似，檔案可以用來排除檔案和目錄，使其不會在組建期間複製到映射。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-161">Much like `.gitignore` files that exclude certain files and directories from source control, the `.dockerignore` file can be used to exclude files and directories from being copied to the image during build.</span></span> <span data-ttu-id="a1c4a-162">這不僅能節省時間，還可以避免因將電腦上的`obj`目錄複寫到映射而造成的一些困惑錯誤。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-162">This not only saves time copying, but can also avoid some confusing errors that arise from having (particularly) the `obj` directory from your PC copied into the image.</span></span> <span data-ttu-id="a1c4a-163">您至少應為檔案新增和`bin` `obj` `.dockerignore`的專案。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-163">You should add at least entries for `bin` and `obj` to your `.dockerignore` file.</span></span>

```console
bin/
obj/
```

## <a name="build-the-image"></a><span data-ttu-id="a1c4a-164">建立映像</span><span class="sxs-lookup"><span data-stu-id="a1c4a-164">Build the image</span></span>

<span data-ttu-id="a1c4a-165">針對具有單一應用程式的解決方案，因此是單一 Dockerfile，最簡單的方式是將 Dockerfile 放在基底目錄中;也就是與檔案相同的目錄`.sln` 。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-165">For a solution with a single application, and thus a single Dockerfile, it is simplest to put the Dockerfile in the base directory; that is, the same directory as the `.sln` file.</span></span> <span data-ttu-id="a1c4a-166">在此情況下，若要建立映射，請在`docker build`包含 Dockerfile 的目錄中使用下列命令。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-166">In that case, to build the image, use the following `docker build` command from the directory containing the Dockerfile.</span></span>

```console
docker build --tag stockdata .
```

<span data-ttu-id="a1c4a-167">Confusingly 命名`--tag`的旗標（可以縮短為`-t`）會指定影像的完整名稱，*包括*實際的標記（如果有指定的話）。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-167">The confusingly named `--tag` flag (which can be shortened to `-t`) specifies the whole name of the image, *including* the actual tag if specified.</span></span> <span data-ttu-id="a1c4a-168">結尾`.`的會指定要在其中執行組建的*內容*，也就是 Dockerfile 中`COPY`命令的目前工作目錄。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-168">The `.` at the end specifies the *context* in which the build will be run; the current working directory for the `COPY` commands in the Dockerfile.</span></span>

<span data-ttu-id="a1c4a-169">如果您在單一方案中有多個應用程式，您可以將每個應用程式的 Dockerfile 保留在該檔案`.csproj`的資料夾中，但您仍應`docker build`從基底目錄執行命令，以確保解決方案和所有專案都會複製到影像中。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-169">If you have multiple applications within a single solution, you can keep the Dockerfile for each application in its own folder, beside the `.csproj` file, but you should still run the `docker build` command from the base directory to ensure that the solution and all the projects are copied into the image.</span></span> <span data-ttu-id="a1c4a-170">您可以使用`--file` （或`-f`）旗標，在目前目錄底下指定 Dockerfile。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-170">You can specify a Dockerfile below the current directory using the `--file` (or `-f`) flag.</span></span>

```console
docker build --tag stockdata --file src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a><span data-ttu-id="a1c4a-171">在您電腦上的容器中執行映射</span><span class="sxs-lookup"><span data-stu-id="a1c4a-171">Run the image in a container on your machine</span></span>

<span data-ttu-id="a1c4a-172">若要在本機 Docker 實例中執行映射，請使用`docker run`命令。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-172">To run the image in your local Docker instance, use the `docker run` command.</span></span>

```console
docker run -ti -p 5000:80 stockdata
```

<span data-ttu-id="a1c4a-173">`-ti`旗標會將您目前的終端機連接到容器的終端機，並在互動模式中執行。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-173">The `-ti` flag connects your current terminal to the container's terminal and runs in interactive mode.</span></span> <span data-ttu-id="a1c4a-174">會將容器上的埠 80發佈（連結）至localhost網路介面上的埠80。`-p 5000:80`</span><span class="sxs-lookup"><span data-stu-id="a1c4a-174">The `-p 5000:80` publishes (links) port 80 on the container to port 80 on the localhost network interface.</span></span>

## <a name="push-the-image-to-a-registry"></a><span data-ttu-id="a1c4a-175">將映射推送至登錄</span><span class="sxs-lookup"><span data-stu-id="a1c4a-175">Push the image to a registry</span></span>

<span data-ttu-id="a1c4a-176">確認映射運作後，您需要將它推送到 Docker 登錄，讓它可在其他系統上使用。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-176">Once you've verified that the image works, you need to push it to a Docker registry to make it available on other systems.</span></span> <span data-ttu-id="a1c4a-177">內部網路將需要布建 Docker 登錄。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-177">Internal networks will need to provision a Docker registry.</span></span> <span data-ttu-id="a1c4a-178">這可以像執行[docker 本身`registry`的映射](https://docs.docker.com/registry/deploying/)一樣簡單（也就是 docker 登錄會在 docker 容器中執行），但有各種更全面的解決方案可供使用。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-178">This can be as simple as running [Docker's own `registry` image](https://docs.docker.com/registry/deploying/) (that's right, the Docker registry runs in a Docker container), but there are various more comprehensive solutions available.</span></span> <span data-ttu-id="a1c4a-179">針對外部共用和雲端使用，有各種可用的受控登錄，例如[Azure Container Registry](https://docs.microsoft.com/azure/container-registry/)或[Docker Hub](https://docs.docker.com/docker-hub/repos/)。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-179">For external sharing and cloud use, there are various managed registries available, such as [Azure Container Registry](https://docs.microsoft.com/azure/container-registry/) or [Docker Hub](https://docs.docker.com/docker-hub/repos/).</span></span>

<span data-ttu-id="a1c4a-180">若要推送至 Docker Hub，請在映射名稱前面加上您的使用者或組織名稱。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-180">To push to the Docker Hub, prefix the image name with your user or organization name.</span></span>

```console
docker tag stockdata myorg/stockdata
docker push myorg/stockdata
```

<span data-ttu-id="a1c4a-181">若要推送至私用登錄，請在映射名稱前面加上登錄主機名稱和組織名稱。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-181">To push to a private registry, prefix the image name with the registry host name and the organization name.</span></span>

```console
docker tag stockdata internal-registry:5000/myorg/stockdata
docker push internal-registry:5000/myorg/stockdata
```

<span data-ttu-id="a1c4a-182">一旦映射位於登錄中，您就可以將它部署到個別的 Docker 主機或容器協調流程引擎（例如 Kubernetes）。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-182">Once the image is in a registry, you can deploy it to individual Docker hosts or to a container orchestration engine like Kubernetes.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a1c4a-183">[上一頁](self-hosted.md)
>[下一頁](kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="a1c4a-183">[Previous](self-hosted.md)
[Next](kubernetes.md)</span></span>
