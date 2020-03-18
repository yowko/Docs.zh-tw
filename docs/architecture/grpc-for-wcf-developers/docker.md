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
# <a name="create-docker-images"></a><span data-ttu-id="9c077-103">創建 Docker 映射</span><span class="sxs-lookup"><span data-stu-id="9c077-103">Create Docker images</span></span>

<span data-ttu-id="9c077-104">本節介紹為ASP.NET Core gRPC 應用程式創建 Docker 映射，這些應用程式可在 Docker、Kubernetes 或其他容器環境中運行。</span><span class="sxs-lookup"><span data-stu-id="9c077-104">This section covers the creation of Docker images for ASP.NET Core gRPC applications, ready to run in Docker, Kubernetes, or other container environments.</span></span> <span data-ttu-id="9c077-105">使用的應用程式範例，帶有ASP.NET酷睿 MVC Web 應用和 gRPC 服務，可在 GitHub 上的[dotnet 架構/grpc-for wcf 開發人員](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample)存儲庫中使用。</span><span class="sxs-lookup"><span data-stu-id="9c077-105">The sample application used, with an ASP.NET Core MVC web app and a gRPC service, is available on the [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) repository on GitHub.</span></span>

## <a name="microsoft-base-images-for-aspnet-core-applications"></a><span data-ttu-id="9c077-106">用於ASP.NET核心應用程式的微軟基本映射</span><span class="sxs-lookup"><span data-stu-id="9c077-106">Microsoft base images for ASP.NET Core applications</span></span>

<span data-ttu-id="9c077-107">Microsoft 為構建和運行 .NET Core 應用程式提供了一系列基本映射。</span><span class="sxs-lookup"><span data-stu-id="9c077-107">Microsoft provides a range of base images for building and running .NET Core applications.</span></span> <span data-ttu-id="9c077-108">要創建 ASP.NET酷睿 3.0 圖像，請使用兩個基本映射：</span><span class="sxs-lookup"><span data-stu-id="9c077-108">To create an ASP.NET Core 3.0 image, you use two base images:</span></span>

- <span data-ttu-id="9c077-109">用於生成和發佈應用程式的 SDK 映射。</span><span class="sxs-lookup"><span data-stu-id="9c077-109">An SDK image to build and publish the application.</span></span>
- <span data-ttu-id="9c077-110">用於部署的運行時映射。</span><span class="sxs-lookup"><span data-stu-id="9c077-110">A runtime image for deployment.</span></span>

| <span data-ttu-id="9c077-111">映像</span><span class="sxs-lookup"><span data-stu-id="9c077-111">Image</span></span> | <span data-ttu-id="9c077-112">描述</span><span class="sxs-lookup"><span data-stu-id="9c077-112">Description</span></span> |
| ----- | ----------- |
| [<span data-ttu-id="9c077-113">mcr.microsoft.com/dotnet/core/sdk</span><span class="sxs-lookup"><span data-stu-id="9c077-113">mcr.microsoft.com/dotnet/core/sdk</span></span>](https://hub.docker.com/_/microsoft-dotnet-core-sdk/) | <span data-ttu-id="9c077-114">用於使用`docker build`生成應用程式。</span><span class="sxs-lookup"><span data-stu-id="9c077-114">For building applications with `docker build`.</span></span> <span data-ttu-id="9c077-115">不用於生產。</span><span class="sxs-lookup"><span data-stu-id="9c077-115">Not to be used in production.</span></span> |
| [<span data-ttu-id="9c077-116">mcr.microsoft.com/dotnet/core/aspnet</span><span class="sxs-lookup"><span data-stu-id="9c077-116">mcr.microsoft.com/dotnet/core/aspnet</span></span>](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) | <span data-ttu-id="9c077-117">包含運行時和 ASP.NET核心依賴項。</span><span class="sxs-lookup"><span data-stu-id="9c077-117">Contains the runtime and ASP.NET Core dependencies.</span></span> <span data-ttu-id="9c077-118">用於生產。</span><span class="sxs-lookup"><span data-stu-id="9c077-118">For production.</span></span> |

<span data-ttu-id="9c077-119">對於每個映射，有四種基於不同 Linux 發行版本的變體，按標記區分。</span><span class="sxs-lookup"><span data-stu-id="9c077-119">For each image, there are four variants based on different Linux distributions, distinguished by tags.</span></span>

| <span data-ttu-id="9c077-120">圖像標記</span><span class="sxs-lookup"><span data-stu-id="9c077-120">Image tag(s)</span></span> | <span data-ttu-id="9c077-121">Linux</span><span class="sxs-lookup"><span data-stu-id="9c077-121">Linux</span></span> | <span data-ttu-id="9c077-122">注意</span><span class="sxs-lookup"><span data-stu-id="9c077-122">Notes</span></span> |
| --------- | ----- | ----- |
| <span data-ttu-id="9c077-123">3.0-破壞者，3.0</span><span class="sxs-lookup"><span data-stu-id="9c077-123">3.0-buster, 3.0</span></span> | <span data-ttu-id="9c077-124">Debian 10</span><span class="sxs-lookup"><span data-stu-id="9c077-124">Debian 10</span></span> | <span data-ttu-id="9c077-125">如果未指定作業系統變體，則預設映射。</span><span class="sxs-lookup"><span data-stu-id="9c077-125">The default image if no OS variant is specified.</span></span> |
| <span data-ttu-id="9c077-126">3.0-高山</span><span class="sxs-lookup"><span data-stu-id="9c077-126">3.0-alpine</span></span> | <span data-ttu-id="9c077-127">阿爾卑斯 3.9</span><span class="sxs-lookup"><span data-stu-id="9c077-127">Alpine 3.9</span></span> | <span data-ttu-id="9c077-128">阿爾卑斯基圖圖像比Debian或Ubuntu圖像小得多。</span><span class="sxs-lookup"><span data-stu-id="9c077-128">Alpine base images are much smaller than Debian or Ubuntu ones.</span></span> |
| <span data-ttu-id="9c077-129">3.0-迪斯可</span><span class="sxs-lookup"><span data-stu-id="9c077-129">3.0-disco</span></span> | <span data-ttu-id="9c077-130">Ubuntu 19.04</span><span class="sxs-lookup"><span data-stu-id="9c077-130">Ubuntu 19.04</span></span> | |
| <span data-ttu-id="9c077-131">3.0-仿生</span><span class="sxs-lookup"><span data-stu-id="9c077-131">3.0-bionic</span></span> | <span data-ttu-id="9c077-132">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="9c077-132">Ubuntu 18.04</span></span> | |

<span data-ttu-id="9c077-133">阿爾卑斯基圖約為 100 MB，而 Debian 和 Ubuntu 圖像的映射為 200 MB。</span><span class="sxs-lookup"><span data-stu-id="9c077-133">The Alpine base image is around 100 MB, compared to 200 MB for the Debian and Ubuntu images.</span></span> <span data-ttu-id="9c077-134">某些套裝軟體或庫在 Alpine 的套裝軟體管理中可能不可用。</span><span class="sxs-lookup"><span data-stu-id="9c077-134">Some software packages or libraries might not be available in Alpine's package management.</span></span> <span data-ttu-id="9c077-135">如果您不確定要使用的圖像，則可能需要選擇預設的 Debian。</span><span class="sxs-lookup"><span data-stu-id="9c077-135">If you're not sure which image to use, you should probably choose the default Debian.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9c077-136">請確保在生成和運行時使用相同的 Linux 變體。</span><span class="sxs-lookup"><span data-stu-id="9c077-136">Make sure you use the same variant of Linux for the build and the runtime.</span></span> <span data-ttu-id="9c077-137">在一個變體上構建和發佈的應用程式可能不適用於另一個變體。</span><span class="sxs-lookup"><span data-stu-id="9c077-137">Applications built and published on one variant might not work on another.</span></span>

## <a name="create-a-docker-image"></a><span data-ttu-id="9c077-138">建立 Docker 映像</span><span class="sxs-lookup"><span data-stu-id="9c077-138">Create a Docker image</span></span>

<span data-ttu-id="9c077-139">Docker 映射由 Docker*檔*定義。</span><span class="sxs-lookup"><span data-stu-id="9c077-139">A Docker image is defined by a *Dockerfile*.</span></span> <span data-ttu-id="9c077-140">這是一個文字檔，其中包含生成應用程式和安裝生成或運行應用程式所需的任何依賴項所需的所有命令。</span><span class="sxs-lookup"><span data-stu-id="9c077-140">This is a text file that contains all the commands needed to build the application and install any dependencies that are required for either building or running the application.</span></span> <span data-ttu-id="9c077-141">下面的示例顯示了 ASP.NET Core 3.0 應用程式的最簡單的 Dockerfile：</span><span class="sxs-lookup"><span data-stu-id="9c077-141">The following example shows the simplest Dockerfile for an ASP.NET Core 3.0 application:</span></span>

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

<span data-ttu-id="9c077-142">Dockerfile 有兩個部分：第一部分使用`sdk`基本映射來構建和發佈應用程式;第二部分使用基本映射來構建和發佈應用程式。第二個從基中`aspnet`創建運行時映射。</span><span class="sxs-lookup"><span data-stu-id="9c077-142">The Dockerfile has two parts: the first uses the `sdk` base image to build and publish the application; the second creates a runtime image from the `aspnet` base.</span></span> <span data-ttu-id="9c077-143">這是因為`sdk`映射約為 900 MB，而運行時映射的映射約為 200 MB，並且大多數內容在運行時是不必要的。</span><span class="sxs-lookup"><span data-stu-id="9c077-143">This is because the `sdk` image is around 900 MB, compared to around 200 MB for the runtime image, and most of its contents are unnecessary at runtime.</span></span>

### <a name="the-build-steps"></a><span data-ttu-id="9c077-144">生成步驟</span><span class="sxs-lookup"><span data-stu-id="9c077-144">The build steps</span></span>

| <span data-ttu-id="9c077-145">步驟</span><span class="sxs-lookup"><span data-stu-id="9c077-145">Step</span></span> | <span data-ttu-id="9c077-146">描述</span><span class="sxs-lookup"><span data-stu-id="9c077-146">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="9c077-147">聲明基本映射並分配`builder`別名。</span><span class="sxs-lookup"><span data-stu-id="9c077-147">Declares the base image and assigns the `builder` alias.</span></span> |
| `WORKDIR /src` | <span data-ttu-id="9c077-148">創建`/src`目錄並將其設置為當前工作目錄。</span><span class="sxs-lookup"><span data-stu-id="9c077-148">Creates the `/src` directory and sets it as the current working directory.</span></span> |
| `COPY . .` | <span data-ttu-id="9c077-149">將主機上當前目錄下的所有內容複寫到映射上的目前的目錄中。</span><span class="sxs-lookup"><span data-stu-id="9c077-149">Copies everything below the current directory on the host into the current directory on the image.</span></span> |
| `RUN dotnet restore` | <span data-ttu-id="9c077-150">還原任何外部包（ASP.NET與 SDK 一起預先安裝核心 3.0 框架）。</span><span class="sxs-lookup"><span data-stu-id="9c077-150">Restores any external packages (ASP.NET Core 3.0 framework is pre-installed with the SDK).</span></span> |
| `RUN dotnet publish ...` | <span data-ttu-id="9c077-151">生成和發佈發佈版本。</span><span class="sxs-lookup"><span data-stu-id="9c077-151">Builds and publishes a Release build.</span></span> <span data-ttu-id="9c077-152">請注意，`--runtime`該標誌不是必需的。</span><span class="sxs-lookup"><span data-stu-id="9c077-152">Note that the `--runtime` flag isn't required.</span></span> |

### <a name="the-runtime-image-steps"></a><span data-ttu-id="9c077-153">運行時映射步驟</span><span class="sxs-lookup"><span data-stu-id="9c077-153">The runtime image steps</span></span>

| <span data-ttu-id="9c077-154">步驟</span><span class="sxs-lookup"><span data-stu-id="9c077-154">Step</span></span> | <span data-ttu-id="9c077-155">描述</span><span class="sxs-lookup"><span data-stu-id="9c077-155">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="9c077-156">聲明新的基本映射。</span><span class="sxs-lookup"><span data-stu-id="9c077-156">Declares a new base image.</span></span> |
| `WORKDIR /app` | <span data-ttu-id="9c077-157">創建`/app`目錄並將其設置為當前工作目錄。</span><span class="sxs-lookup"><span data-stu-id="9c077-157">Creates the `/app` directory and sets it as the current working directory.</span></span> |
| `COPY --from=builder ...` | <span data-ttu-id="9c077-158">使用第一`builder``FROM`行中的別名從上一個圖像複製已發佈的應用程式。</span><span class="sxs-lookup"><span data-stu-id="9c077-158">Copies the published application from the previous image, by using the `builder` alias from the first `FROM` line.</span></span> |
| `ENTRYPOINT [ ... ]` | <span data-ttu-id="9c077-159">將命令設置在容器啟動時運行。</span><span class="sxs-lookup"><span data-stu-id="9c077-159">Sets the command to run when the container starts.</span></span> <span data-ttu-id="9c077-160">運行時`dotnet`映射中的命令只能運行 DLL 檔。</span><span class="sxs-lookup"><span data-stu-id="9c077-160">The `dotnet` command in the runtime image can only run DLL files.</span></span> |

### <a name="https-in-docker"></a><span data-ttu-id="9c077-161">Docker 中的 HTTPS</span><span class="sxs-lookup"><span data-stu-id="9c077-161">HTTPS in Docker</span></span>

<span data-ttu-id="9c077-162">Docker 的 Microsoft 基本`ASPNETCORE_URLS`映射將環境`http://+:80`變數設置為 ，這意味著 Kestrel 在該埠上運行沒有 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="9c077-162">Microsoft base images for Docker set the `ASPNETCORE_URLS` environment variable to `http://+:80`, meaning that Kestrel runs without HTTPS on that port.</span></span> <span data-ttu-id="9c077-163">如果將 HTTPS 與自訂證書一起使用（如[自託管 gRPC 應用程式中](self-hosted.md)所述），則應重寫此證書。</span><span class="sxs-lookup"><span data-stu-id="9c077-163">If you're using HTTPS with a custom certificate (as described in [Self-hosted gRPC applications](self-hosted.md)), you should override this.</span></span> <span data-ttu-id="9c077-164">在 Dockerfile 的運行時映射創建部分設置環境變數。</span><span class="sxs-lookup"><span data-stu-id="9c077-164">Set the environment variable in the runtime image creation part of your Dockerfile.</span></span>

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a><span data-ttu-id="9c077-165">.dockerignore 檔</span><span class="sxs-lookup"><span data-stu-id="9c077-165">The .dockerignore file</span></span>

<span data-ttu-id="9c077-166">與從`.gitignore`原始程式碼管理中排除某些檔和目錄的檔類似，`.dockerignore`該檔可用於在生成期間將檔和目錄複寫到映射。</span><span class="sxs-lookup"><span data-stu-id="9c077-166">Much like `.gitignore` files that exclude certain files and directories from source control, the `.dockerignore` file can be used to exclude files and directories from being copied to the image during build.</span></span> <span data-ttu-id="9c077-167">這不僅節省了複製時間，還可以避免將 PC 中的`obj`目錄複寫到映射中出現的一些錯誤。</span><span class="sxs-lookup"><span data-stu-id="9c077-167">This not only saves time copying, but can also avoid some errors that arise from having the `obj` directory from your PC copied into the image.</span></span> <span data-ttu-id="9c077-168">至少，應為`bin`檔添加條目，並`obj`添加到檔中`.dockerignore`。</span><span class="sxs-lookup"><span data-stu-id="9c077-168">At a minimum, you should add entries for `bin` and `obj` to your `.dockerignore` file.</span></span>

```console
bin/
obj/
```

## <a name="build-the-image"></a><span data-ttu-id="9c077-169">建立映像</span><span class="sxs-lookup"><span data-stu-id="9c077-169">Build the image</span></span>

<span data-ttu-id="9c077-170">對於具有單個應用程式的解決方案，以及單個 Dockerfile，將 Dockerfile 放在基本目錄中是最簡單的。</span><span class="sxs-lookup"><span data-stu-id="9c077-170">For a solution with a single application, and thus a single Dockerfile, it's simplest to put the Dockerfile in the base directory.</span></span> <span data-ttu-id="9c077-171">換句話說，將其放在與`.sln`檔相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="9c077-171">In other words, put it in the same directory as the `.sln` file.</span></span> <span data-ttu-id="9c077-172">在這種情況下，要生成映射，請使用包含 Dockerfile`docker build`的目錄中的以下命令。</span><span class="sxs-lookup"><span data-stu-id="9c077-172">In that case, to build the image, use the following `docker build` command from the directory containing the Dockerfile.</span></span>

```console
docker build --tag stockdata .
```

<span data-ttu-id="9c077-173">令人困惑的名稱`--tag`標誌（可以縮短為`-t`）指定圖像的整個名稱，包括指定的實際標記。</span><span class="sxs-lookup"><span data-stu-id="9c077-173">The confusingly named `--tag` flag (which can be shortened to `-t`) specifies the whole name of the image, including the actual tag if specified.</span></span> <span data-ttu-id="9c077-174">`.`末尾指定將在其中運行生成的上下文;Docker 檔中命令的`COPY`當前工作目錄。</span><span class="sxs-lookup"><span data-stu-id="9c077-174">The `.` at the end specifies the context in which the build will be run; the current working directory for the `COPY` commands in the Dockerfile.</span></span>

<span data-ttu-id="9c077-175">如果單個解決方案中有多個應用程式，則可以將每個應用程式的 Dockerfile 保留在檔旁邊的`.csproj`自己的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="9c077-175">If you have multiple applications within a single solution, you can keep the Dockerfile for each application in its own folder, beside the `.csproj` file.</span></span> <span data-ttu-id="9c077-176">您仍應從基`docker build`目錄中運行該命令，以確保將解決方案和所有專案複製到映射中。</span><span class="sxs-lookup"><span data-stu-id="9c077-176">You should still run the `docker build` command from the base directory to ensure that the solution and all the projects are copied into the image.</span></span> <span data-ttu-id="9c077-177">可以使用`--file`（ 或`-f`） 標誌在目前的目錄下方指定 Docker 檔。</span><span class="sxs-lookup"><span data-stu-id="9c077-177">You can specify a Dockerfile below the current directory by using the `--file` (or `-f`) flag.</span></span>

```console
docker build --tag stockdata --file src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a><span data-ttu-id="9c077-178">在電腦上的容器中運行映射</span><span class="sxs-lookup"><span data-stu-id="9c077-178">Run the image in a container on your machine</span></span>

<span data-ttu-id="9c077-179">要在本地 Docker 實例中運行映射，請使用`docker run`命令。</span><span class="sxs-lookup"><span data-stu-id="9c077-179">To run the image in your local Docker instance, use the `docker run` command.</span></span>

```console
docker run -ti -p 5000:80 stockdata
```

<span data-ttu-id="9c077-180">標誌`-ti`將當前終端連接到容器的終端，並在互動式模式下運行。</span><span class="sxs-lookup"><span data-stu-id="9c077-180">The `-ti` flag connects your current terminal to the container's terminal, and runs in interactive mode.</span></span> <span data-ttu-id="9c077-181">容器`-p 5000:80`上的發佈（連結）埠 80 到本地主機網路介面上的埠 5000。</span><span class="sxs-lookup"><span data-stu-id="9c077-181">The `-p 5000:80` publishes (links) port 80 on the container to port 5000 on the localhost network interface.</span></span>

## <a name="push-the-image-to-a-registry"></a><span data-ttu-id="9c077-182">將映像推送至登錄</span><span class="sxs-lookup"><span data-stu-id="9c077-182">Push the image to a registry</span></span>

<span data-ttu-id="9c077-183">驗證映射是否正常工作後，將其推送到 Docker 註冊表，使其在其他系統上可用。</span><span class="sxs-lookup"><span data-stu-id="9c077-183">After you've verified that the image works, push it to a Docker registry to make it available on other systems.</span></span> <span data-ttu-id="9c077-184">內部網路將需要預配 Docker 註冊表。</span><span class="sxs-lookup"><span data-stu-id="9c077-184">Internal networks will need to provision a Docker registry.</span></span> <span data-ttu-id="9c077-185">這可以像運行[Docker 自己的`registry`映射](https://docs.docker.com/registry/deploying/)（Docker 註冊表在 Docker 容器中運行）一樣簡單，但有多種更全面的解決方案可用。</span><span class="sxs-lookup"><span data-stu-id="9c077-185">This can be as simple as running [Docker's own `registry` image](https://docs.docker.com/registry/deploying/) (the Docker registry runs in a Docker container), but there are various more comprehensive solutions available.</span></span> <span data-ttu-id="9c077-186">對於外部共用和雲使用，可以使用各種託管註冊表，例如[Azure 容器註冊表](https://docs.microsoft.com/azure/container-registry/)或[Docker Hub。](https://docs.docker.com/docker-hub/repos/)</span><span class="sxs-lookup"><span data-stu-id="9c077-186">For external sharing and cloud use, there are various managed registries available, such as [Azure Container Registry](https://docs.microsoft.com/azure/container-registry/) or [Docker Hub](https://docs.docker.com/docker-hub/repos/).</span></span>

<span data-ttu-id="9c077-187">要推送到 Docker 中心，請用使用者或組織名稱對圖像名稱進行首碼。</span><span class="sxs-lookup"><span data-stu-id="9c077-187">To push to Docker Hub, prefix the image name with your user or organization name.</span></span>

```console
docker tag stockdata myorg/stockdata
docker push myorg/stockdata
```

<span data-ttu-id="9c077-188">要推送到專用註冊表，使用註冊表主機名稱和組織名稱對映射名稱進行首碼。</span><span class="sxs-lookup"><span data-stu-id="9c077-188">To push to a private registry, prefix the image name with the registry host name and the organization name.</span></span>

```console
docker tag stockdata internal-registry:5000/myorg/stockdata
docker push internal-registry:5000/myorg/stockdata
```

<span data-ttu-id="9c077-189">映射在註冊表中後，您可以將其部署到單獨的 Docker 主機，或部署到容器編排引擎（如 Kubernetes）。</span><span class="sxs-lookup"><span data-stu-id="9c077-189">After the image is in a registry, you can deploy it to individual Docker hosts, or to a container orchestration engine like Kubernetes.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="9c077-190">[上一個](self-hosted.md)
>[下一個](kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="9c077-190">[Previous](self-hosted.md)
[Next](kubernetes.md)</span></span>
