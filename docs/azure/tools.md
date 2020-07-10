---
title: Azure .NET 開發人員工具
description: 取得工具，開始在 Windows、Linux 和 Mac 環境使用 Azure .NET 程式庫。
ms.date: 06/19/2020
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: fa645b152f15550b25a3542ba0cdbb43799536b9
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174906"
---
# <a name="azure-tools-for-developing-with-net"></a><span data-ttu-id="b2717-103">使用 .NET 進行開發的 Azure 工具</span><span class="sxs-lookup"><span data-stu-id="b2717-103">Azure tools for developing with .NET</span></span>

## <a name="sdk-downloads"></a><span data-ttu-id="b2717-104">SDK 下載</span><span class="sxs-lookup"><span data-stu-id="b2717-104">SDK downloads</span></span>

<span data-ttu-id="b2717-105">適用于 .NET 的 Azure 程式庫會實作為[NuGet 套件](https://www.nuget.org/packages?q=windowsazureofficial)。</span><span class="sxs-lookup"><span data-stu-id="b2717-105">Azure libraries for .NET are implemented as [NuGet packages](https://www.nuget.org/packages?q=windowsazureofficial).</span></span> <span data-ttu-id="b2717-106">如需 Azure 服務所組織的參考檔，請參閱[API 參考](/dotnet/api/overview/azure/?view=azure-dotnet)。</span><span class="sxs-lookup"><span data-stu-id="b2717-106">See the [API Reference](/dotnet/api/overview/azure/?view=azure-dotnet) for reference documentation organized by Azure service.</span></span>

## <a name="development-tools"></a><span data-ttu-id="b2717-107">開發工具</span><span class="sxs-lookup"><span data-stu-id="b2717-107">Development tools</span></span>

<span data-ttu-id="b2717-108">Visual Studio 有許多內建 Azure 服務的工具。</span><span class="sxs-lookup"><span data-stu-id="b2717-108">Visual Studio has tooling for many Azure services built-in.</span></span> <span data-ttu-id="b2717-109">某些 Azure 服務有其他可用的工具或模擬器，例如[Azure 儲存體總管](https://azure.microsoft.com/features/storage-explorer/)。</span><span class="sxs-lookup"><span data-stu-id="b2717-109">Some Azure services have additional tools or emulators available, such as [Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/).</span></span> <span data-ttu-id="b2717-110">如有必要，請參閱 Azure 服務的檔，以取得任何其他工具。</span><span class="sxs-lookup"><span data-stu-id="b2717-110">See the documentation for your Azure service for any additional tools, if necessary.</span></span>

<span data-ttu-id="b2717-111">請在下方選取您慣用的開發環境。</span><span class="sxs-lookup"><span data-stu-id="b2717-111">Select your preferred development environment below.</span></span>

## <a name="visual-studio-on-windows"></a>[<span data-ttu-id="b2717-112">Windows 上的 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b2717-112">Visual Studio on Windows</span></span>](#tab/vs)

<span data-ttu-id="b2717-113">Visual Studio 2017 版和更新版本具有 Azure 開發的內建支援。</span><span class="sxs-lookup"><span data-stu-id="b2717-113">Visual Studio version 2017 and later have built-in support for Azure development.</span></span> <span data-ttu-id="b2717-114">下列步驟說明如何在 Visual Studio 中啟用 Azure 開發支援。</span><span class="sxs-lookup"><span data-stu-id="b2717-114">The below steps describe enabling Azure development support in Visual Studio.</span></span>

<span data-ttu-id="b2717-115">針對 Visual Studio 2015 和更早版本，請<a href="vs2015-install.md">遵循這些指示</a>。</span><span class="sxs-lookup"><span data-stu-id="b2717-115">For Visual Studio 2015 and earlier, <a href="vs2015-install.md">follow these instructions</a>.</span></span>

### <a name="step-1-download-visual-studio-2019"></a><span data-ttu-id="b2717-116">步驟1：下載 Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="b2717-116">Step 1: Download Visual Studio 2019</span></span>

<span data-ttu-id="b2717-117">如果您已安裝 Visual Studio 2019，可以略過此步驟。</span><span class="sxs-lookup"><span data-stu-id="b2717-117">You can skip this step if you already have Visual Studio 2019 installed.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b2717-118">下載 Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="b2717-118">Download Visual Studio 2019</span></span>](https://www.visualstudio.com/downloads/)

### <a name="step-2-install-the-two-azure-workloads"></a><span data-ttu-id="b2717-119">步驟 2：安裝兩個 Azure 工作負載</span><span class="sxs-lookup"><span data-stu-id="b2717-119">Step 2: Install the two Azure workloads</span></span>

<span data-ttu-id="b2717-120">在 Visual Studio 安裝程式中，安裝 Visual Studio (或修改現有的安裝) 。</span><span class="sxs-lookup"><span data-stu-id="b2717-120">In the Visual Studio installer, install Visual Studio (or modify an existing installation).</span></span> <span data-ttu-id="b2717-121">請確定已選取 [ *Azure 開發*] 和 [ *ASP.NET] 和 [網頁程式開發*] 工作負載。</span><span class="sxs-lookup"><span data-stu-id="b2717-121">Make sure the *Azure development* and *ASP.NET and web development* workloads are selected.</span></span>

### <a name="step-3-develop-with-net-on-azure"></a><span data-ttu-id="b2717-122">步驟 3：在 Azure 上利用 .NET 進行開發</span><span class="sxs-lookup"><span data-stu-id="b2717-122">Step 3: Develop with .NET on Azure</span></span>

<span data-ttu-id="b2717-123">從[在 Azure App Service 上部署第一個 ASP.NET Core Web 應用程式](/azure/app-service-web/app-service-web-get-started-dotnet)開始使用。</span><span class="sxs-lookup"><span data-stu-id="b2717-123">Get started by [deploying your first ASP.NET Core web app on Azure App Service](/azure/app-service-web/app-service-web-get-started-dotnet).</span></span>

## <a name="visual-studio-code-cross-platform"></a>[<span data-ttu-id="b2717-124">跨平臺 Visual Studio Code () </span><span class="sxs-lookup"><span data-stu-id="b2717-124">Visual Studio Code (cross-platform)</span></span>](#tab/vscode)

<span data-ttu-id="b2717-125">Visual Studio Code 具備跨平臺 Azure 開發所需的所有專案。</span><span class="sxs-lookup"><span data-stu-id="b2717-125">Visual Studio Code has everything you need for cross-platform Azure development.</span></span>

### <a name="step-1-download-the-net-core-sdk"></a><span data-ttu-id="b2717-126">步驟 1：下載 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="b2717-126">Step 1: Download the .NET Core SDK</span></span>

<span data-ttu-id="b2717-127">適用於 .NET Core 應用程式的 SDK 和命令列工具。</span><span class="sxs-lookup"><span data-stu-id="b2717-127">The SDK and command-line tools for .NET Core apps.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b2717-128">下載 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="b2717-128">Download .NET Core SDK</span></span>](https://dotnet.microsoft.com/download)

### <a name="step-2-visual-studio-code"></a><span data-ttu-id="b2717-129">步驟 2：Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="b2717-129">Step 2: Visual Studio Code</span></span>

<span data-ttu-id="b2717-130">在任何作業系統上編輯 .NET Core 應用程式及進行偵錯：Windows、Mac 和 Linux。</span><span class="sxs-lookup"><span data-stu-id="b2717-130">Edit and debug .NET Core apps on any operating system: Windows, Mac, and Linux.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b2717-131">下載 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="b2717-131">Download Visual Studio Code</span></span>](https://code.visualstudio.com)

### <a name="step-3-azure-tools-extension"></a><span data-ttu-id="b2717-132">步驟3： Azure Tools 擴充功能</span><span class="sxs-lookup"><span data-stu-id="b2717-132">Step 3: Azure Tools extension</span></span>

<span data-ttu-id="b2717-133">在 Visual Studio Code 中安裝 Azure Tools 擴充功能。</span><span class="sxs-lookup"><span data-stu-id="b2717-133">Install the Azure Tools extension in Visual Studio Code.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b2717-134">安裝 Azure Tools 擴充功能</span><span class="sxs-lookup"><span data-stu-id="b2717-134">Install Azure Tools extension</span></span>](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-node-azure-pack)

### <a name="step-4-develop-with-net-on-azure"></a><span data-ttu-id="b2717-135">步驟4：在 Azure 上使用 .NET 進行開發</span><span class="sxs-lookup"><span data-stu-id="b2717-135">Step 4: Develop with .NET on Azure</span></span>

<span data-ttu-id="b2717-136">開始[在 Linux 上的 Azure App Service 上部署您的第一個 ASP.NET Core web 應用程式](/azure/app-service/containers/quickstart-dotnetcore)。</span><span class="sxs-lookup"><span data-stu-id="b2717-136">Get started by [deploying your first ASP.NET Core web app on Azure App Service on Linux](/azure/app-service/containers/quickstart-dotnetcore).</span></span>

---
