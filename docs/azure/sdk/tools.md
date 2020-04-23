---
title: 適用於 Azure .NET 和 .NET Core 開發人員的工具
description: 取得工具，開始在 Windows、Linux 和 Mac 環境使用 Azure .NET 程式庫。
ms.date: 10/01/2018
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: 1c6370e4b3e5e6e901ba6ef56c65d794f3da5abe
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2020
ms.locfileid: "82071938"
---
# <a name="tools-for-net-and-net-core-azure-developers"></a><span data-ttu-id="bd945-103">適用於 .NET 和 .NET Core Azure 開發人員的工具</span><span class="sxs-lookup"><span data-stu-id="bd945-103">Tools for .NET and .NET Core Azure developers</span></span>

## <a name="sdk-downloads"></a><span data-ttu-id="bd945-104">SDK 下載</span><span class="sxs-lookup"><span data-stu-id="bd945-104">SDK downloads</span></span>

<span data-ttu-id="bd945-105">.NET 的 Azure 庫作為[NuGet 包](https://www.nuget.org/packages?q=windowsazureofficial)實現。</span><span class="sxs-lookup"><span data-stu-id="bd945-105">Azure libraries for .NET are implemented as [NuGet packages](https://www.nuget.org/packages?q=windowsazureofficial).</span></span> <span data-ttu-id="bd945-106">有關 Azure 服務組織的安裝說明,請參閱[API 參考](/dotnet/api/overview/azure/?view=azure-dotnet)。</span><span class="sxs-lookup"><span data-stu-id="bd945-106">See the [API Reference](/dotnet/api/overview/azure/?view=azure-dotnet) for installation instructions organized by Azure service.</span></span>

## <a name="development-tools"></a><span data-ttu-id="bd945-107">開發工具</span><span class="sxs-lookup"><span data-stu-id="bd945-107">Development tools</span></span>

<span data-ttu-id="bd945-108">Visual Studio 具有用於內置許多 Azure 服務的工具。</span><span class="sxs-lookup"><span data-stu-id="bd945-108">Visual Studio has tooling for many Azure services built-in.</span></span> <span data-ttu-id="bd945-109">某些 Azure 服務具有其他可用工具或模擬器,如[Azure 儲存資源管理員](https://azure.microsoft.com/features/storage-explorer/)。</span><span class="sxs-lookup"><span data-stu-id="bd945-109">Some Azure services have additional tools or emulators available, such as [Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/).</span></span> <span data-ttu-id="bd945-110">如有必要,請參閱 Azure 服務的文檔,瞭解任何其他工具。</span><span class="sxs-lookup"><span data-stu-id="bd945-110">See the documentation for your Azure service for any additional tools, if necessary.</span></span>

<span data-ttu-id="bd945-111">這些說明為您的作業系統安裝建議的啟動開發環境。</span><span class="sxs-lookup"><span data-stu-id="bd945-111">These instructions install the recommended starting development environment for your operating system.</span></span>

## <a name="windows"></a>[<span data-ttu-id="bd945-112">Windows</span><span class="sxs-lookup"><span data-stu-id="bd945-112">Windows</span></span>](#tab/windows)

<span data-ttu-id="bd945-113">Visual Studio 版本 2017 及更高版本已內置支援 Azure 開發。</span><span class="sxs-lookup"><span data-stu-id="bd945-113">Visual Studio versions 2017 and later have built-in support for Azure development.</span></span> <span data-ttu-id="bd945-114">以下步驟描述了在可視化工作室中啟用 Azure 開發支援。</span><span class="sxs-lookup"><span data-stu-id="bd945-114">The below steps describe enabling Azure development support in Visual Studio.</span></span>

<span data-ttu-id="bd945-115">對於 Visual Studio 2015 及更早版本,<a href="vs2015-install.md">請按照以下說明操作</a>。</span><span class="sxs-lookup"><span data-stu-id="bd945-115">For Visual Studio 2015 and earlier, <a href="vs2015-install.md">follow these instructions</a>.</span></span>

### <a name="step-1-download-visual-studio-2019"></a><span data-ttu-id="bd945-116">第 1 步:下載視覺工作室 2019</span><span class="sxs-lookup"><span data-stu-id="bd945-116">Step 1: Download Visual Studio 2019</span></span>

<span data-ttu-id="bd945-117">如果您已經安裝了 Visual Studio 2019,則可以跳過此步驟。</span><span class="sxs-lookup"><span data-stu-id="bd945-117">You can skip this step if you already have Visual Studio 2019 installed.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bd945-118">下載 Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="bd945-118">Download Visual Studio 2019</span></span>](https://www.visualstudio.com/downloads/)

### <a name="step-2-install-the-two-azure-workloads"></a><span data-ttu-id="bd945-119">步驟 2：安裝兩個 Azure 工作負載</span><span class="sxs-lookup"><span data-stu-id="bd945-119">Step 2: Install the two Azure workloads</span></span>

<span data-ttu-id="bd945-120">在可視化工作室安裝程式中,安裝可視化工作室(或修改現有安裝)。</span><span class="sxs-lookup"><span data-stu-id="bd945-120">In the Visual Studio installer, install Visual Studio (or modify an existing installation).</span></span> <span data-ttu-id="bd945-121">確保選擇了*Azure*開發和*ASP.NET 和 Web 開發*工作負荷。</span><span class="sxs-lookup"><span data-stu-id="bd945-121">Make sure the *Azure development* and *ASP.NET and web development* workloads are selected.</span></span>

### <a name="step-3-develop-with-net-on-azure"></a><span data-ttu-id="bd945-122">步驟 3：在 Azure 上利用 .NET 進行開發</span><span class="sxs-lookup"><span data-stu-id="bd945-122">Step 3: Develop with .NET on Azure</span></span>

<span data-ttu-id="bd945-123">從[在 Azure App Service 上部署第一個 ASP.NET Core Web 應用程式](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-dotnet)開始使用。</span><span class="sxs-lookup"><span data-stu-id="bd945-123">Get started by [deploying your first ASP.NET Core web app on Azure App Service](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-dotnet).</span></span>

## <a name="macos"></a>[<span data-ttu-id="bd945-124">macOS</span><span class="sxs-lookup"><span data-stu-id="bd945-124">macOS</span></span>](#tab/macos)

<span data-ttu-id="bd945-125">Visual Studio for Mac 包含您 Azure 開發所需的所有項目。</span><span class="sxs-lookup"><span data-stu-id="bd945-125">Visual Studio for Mac has everything you need for Azure development.</span></span>

### <a name="step-1-download-visual-studio-for-mac"></a><span data-ttu-id="bd945-126">步驟 1：下載 Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="bd945-126">Step 1: Download Visual Studio for Mac</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bd945-127">下載 Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="bd945-127">Download Visual Studio for Mac</span></span>](https://www.visualstudio.com/vs/visual-studio-mac/)

<span data-ttu-id="bd945-128">在安裝過程中,默認情況下選擇 Azure 工具。</span><span class="sxs-lookup"><span data-stu-id="bd945-128">During installation, Azure tools are selected by default.</span></span>

## <a name="linux"></a>[<span data-ttu-id="bd945-129">Linux</span><span class="sxs-lookup"><span data-stu-id="bd945-129">Linux</span></span>](#tab/linux)

<span data-ttu-id="bd945-130">Visual Studio Code 包含您在 Linux 上進行 Azure 開發所需的所有項目。</span><span class="sxs-lookup"><span data-stu-id="bd945-130">Visual Studio Code has everything you need for Azure development on Linux.</span></span>

### <a name="step-1-download-the-net-core-sdk"></a><span data-ttu-id="bd945-131">步驟 1：下載 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="bd945-131">Step 1: Download the .NET Core SDK</span></span>

<span data-ttu-id="bd945-132">適用於 .NET Core 應用程式的 SDK 和命令列工具。</span><span class="sxs-lookup"><span data-stu-id="bd945-132">The SDK and command-line tools for .NET Core apps.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bd945-133">下載 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="bd945-133">Download .NET Core SDK</span></span>](https://dotnet.microsoft.com/download)

### <a name="step-2-visual-studio-code"></a><span data-ttu-id="bd945-134">步驟 2：Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="bd945-134">Step 2: Visual Studio Code</span></span>

<span data-ttu-id="bd945-135">在任何作業系統上編輯 .NET Core 應用程式及進行偵錯：Windows、Mac 和 Linux。</span><span class="sxs-lookup"><span data-stu-id="bd945-135">Edit and debug .NET Core apps on any operating system: Windows, Mac, and Linux.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bd945-136">下載 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="bd945-136">Download Visual Studio Code</span></span>](https://code.visualstudio.com)

---
