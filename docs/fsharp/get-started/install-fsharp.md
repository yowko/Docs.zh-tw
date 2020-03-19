---
title: 安裝 F#
description: 瞭解如何以各種不同方式安裝 F#。
ms.date: 12/20/2019
ms.openlocfilehash: 302e04f7cf3271516dff88d9d5f18f620b6ede80
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400243"
---
# <a name="install-f"></a><span data-ttu-id="8b8fc-103">安裝 F\#</span><span class="sxs-lookup"><span data-stu-id="8b8fc-103">Install F\#</span></span>

<span data-ttu-id="8b8fc-104">您可以根據環境以多種方式安裝 F#。</span><span class="sxs-lookup"><span data-stu-id="8b8fc-104">You can install F# in multiple ways, depending on your environment.</span></span>

## <a name="install-f-with-visual-studio"></a><span data-ttu-id="8b8fc-105">使用視覺化工作室安裝 F#</span><span class="sxs-lookup"><span data-stu-id="8b8fc-105">Install F# with Visual Studio</span></span>

1. <span data-ttu-id="8b8fc-106">如果您是首次下載[視覺化工作室](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)，它將首先安裝視覺化工作室安裝程式。</span><span class="sxs-lookup"><span data-stu-id="8b8fc-106">If you're downloading [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) for the first time, it will first install Visual Studio Installer.</span></span> <span data-ttu-id="8b8fc-107">從安裝程式安裝相應的視覺工作室版本。</span><span class="sxs-lookup"><span data-stu-id="8b8fc-107">Install the appropriate edition of Visual Studio from the installer.</span></span>

   <span data-ttu-id="8b8fc-108">如果已安裝 Visual Studio，請選擇要向其添加 F# 的版本旁邊的 **"修改**"。</span><span class="sxs-lookup"><span data-stu-id="8b8fc-108">If you already have Visual Studio installed, choose **Modify** next to the edition you want to add F# to.</span></span>

2. <span data-ttu-id="8b8fc-109">在"工作負載"頁上，選擇**ASP.NET和 Web 開發**工作負載，其中包括 ASP.NET核心專案的 F# 和 .NET Core 支援。</span><span class="sxs-lookup"><span data-stu-id="8b8fc-109">On the Workloads page, select the **ASP.NET and web development** workload, which includes F# and .NET Core support for ASP.NET Core projects.</span></span>

3. <span data-ttu-id="8b8fc-110">在右下角選擇 **"修改"** 以安裝您選擇的所有內容。</span><span class="sxs-lookup"><span data-stu-id="8b8fc-110">Choose **Modify** in the lower right-hand corner to install everything you've selected.</span></span>

   <span data-ttu-id="8b8fc-111">然後，您可以通過選擇"在視覺化工作室安裝程式中**啟動"** 來打開帶有 F# 的視覺化工作室。</span><span class="sxs-lookup"><span data-stu-id="8b8fc-111">You can then open Visual Studio with F# by choosing **Launch** in Visual Studio Installer.</span></span>

## <a name="install-f-with-visual-studio-code"></a><span data-ttu-id="8b8fc-112">使用視覺化工作室代碼安裝 F#</span><span class="sxs-lookup"><span data-stu-id="8b8fc-112">Install F# with Visual Studio Code</span></span>

1. <span data-ttu-id="8b8fc-113">確保您已安裝[git](https://git-scm.com/download)並在您的 PATH 上可用。</span><span class="sxs-lookup"><span data-stu-id="8b8fc-113">Ensure you have [git](https://git-scm.com/download) installed and available on your PATH.</span></span> <span data-ttu-id="8b8fc-114">您可以通過在命令提示符處輸入`git --version`並按**Enter**來驗證其安裝是否正確。</span><span class="sxs-lookup"><span data-stu-id="8b8fc-114">You can verify that it's installed correctly by entering `git --version` at a command prompt and pressing **Enter**.</span></span>

2. <span data-ttu-id="8b8fc-115">安裝[.NET 核心 SDK](https://dotnet.microsoft.com/download)和[視覺化工作室代碼](https://code.visualstudio.com)。</span><span class="sxs-lookup"><span data-stu-id="8b8fc-115">Install the [.NET Core SDK](https://dotnet.microsoft.com/download) and [Visual Studio Code](https://code.visualstudio.com).</span></span>

3. <span data-ttu-id="8b8fc-116">選擇"擴展"圖示並搜索"Ionide"：</span><span class="sxs-lookup"><span data-stu-id="8b8fc-116">Select the Extensions icon and search for "Ionide":</span></span>

   <span data-ttu-id="8b8fc-117">在視覺工作室代碼中 F# 支援的唯一外掛程式是[Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)。</span><span class="sxs-lookup"><span data-stu-id="8b8fc-117">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span> <span data-ttu-id="8b8fc-118">但是，您也可以安裝[Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE)以獲得[FAKE](https://fake.build/)支援和[Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket)以獲得[Paket](https://fsprojects.github.io/Paket/)支援。</span><span class="sxs-lookup"><span data-stu-id="8b8fc-118">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) to get [FAKE](https://fake.build/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span></span> <span data-ttu-id="8b8fc-119">FAKE 和 Paket 是用於構建專案和管理依賴項的其他 F# 社區工具。</span><span class="sxs-lookup"><span data-stu-id="8b8fc-119">FAKE and Paket are additional F# community tools for building projects and managing dependencies, respectively.</span></span>

## <a name="install-f-with-visual-studio-for-mac"></a><span data-ttu-id="8b8fc-120">安裝 F# 與 Mac 的視覺工作室</span><span class="sxs-lookup"><span data-stu-id="8b8fc-120">Install F# with Visual Studio for Mac</span></span>

<span data-ttu-id="8b8fc-121">F# 預設安裝在[Mac 的 Visual Studio](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)中，無論您選擇哪種配置。</span><span class="sxs-lookup"><span data-stu-id="8b8fc-121">F# is installed by default in [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), no matter which configuration you choose.</span></span>

<span data-ttu-id="8b8fc-122">安裝完成後，選擇 **"開始視覺化工作室**"。</span><span class="sxs-lookup"><span data-stu-id="8b8fc-122">After the install completes, choose **Start Visual Studio**.</span></span> <span data-ttu-id="8b8fc-123">您還可以在 macOS 上通過 Finder 打開視覺工作室。</span><span class="sxs-lookup"><span data-stu-id="8b8fc-123">You can also open Visual Studio through Finder on macOS.</span></span>

## <a name="install-f-on-a-build-server"></a><span data-ttu-id="8b8fc-124">在生成伺服器上安裝 F#</span><span class="sxs-lookup"><span data-stu-id="8b8fc-124">Install F# on a build server</span></span>

<span data-ttu-id="8b8fc-125">如果您通過 .NET SDK 使用 .NET Core 或 .NET 框架，只需在生成伺服器上安裝 .NET SDK 即可。</span><span class="sxs-lookup"><span data-stu-id="8b8fc-125">If you're using .NET Core or .NET Framework via the .NET SDK, you simply need to install the .NET SDK on your build server.</span></span> <span data-ttu-id="8b8fc-126">它有你需要的一切。</span><span class="sxs-lookup"><span data-stu-id="8b8fc-126">It has everything you need.</span></span>

<span data-ttu-id="8b8fc-127">如果您使用的是 .NET 框架，**並且沒有**使用 .NET SDK，則需要將[視覺化工作室構建工具 SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16)安裝到 Windows 伺服器上。</span><span class="sxs-lookup"><span data-stu-id="8b8fc-127">If you're using .NET Framework and you are **not** using the .NET SDK, then you'll need to install the [Visual Studio Build Tools SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) onto your Windows Server.</span></span> <span data-ttu-id="8b8fc-128">在安裝程式中，選擇 **.NET 桌面生成工具**，然後在安裝程式功能表右側選擇**F# 編譯器**元件。</span><span class="sxs-lookup"><span data-stu-id="8b8fc-128">In the installer, select **.NET desktop build tools**, and then select the **F# compiler** component on the right-hand side of the installer menu.</span></span>
