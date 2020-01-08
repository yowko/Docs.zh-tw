---
title: 安裝 F#
description: 瞭解如何以各種F#不同的方式安裝。
ms.date: 12/20/2019
ms.openlocfilehash: 302e04f7cf3271516dff88d9d5f18f620b6ede80
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346557"
---
# <a name="install-f"></a><span data-ttu-id="8f4d6-103">安裝 F\#</span><span class="sxs-lookup"><span data-stu-id="8f4d6-103">Install F\#</span></span>

<span data-ttu-id="8f4d6-104">您可以透過F#多種方式安裝，視您的環境而定。</span><span class="sxs-lookup"><span data-stu-id="8f4d6-104">You can install F# in multiple ways, depending on your environment.</span></span>

## <a name="install-f-with-visual-studio"></a><span data-ttu-id="8f4d6-105">使用F# Visual Studio 安裝</span><span class="sxs-lookup"><span data-stu-id="8f4d6-105">Install F# with Visual Studio</span></span>

1. <span data-ttu-id="8f4d6-106">如果您是第一次下載[Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ，它會先安裝 Visual Studio 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="8f4d6-106">If you're downloading [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) for the first time, it will first install Visual Studio Installer.</span></span> <span data-ttu-id="8f4d6-107">從安裝程式安裝適當版本的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="8f4d6-107">Install the appropriate edition of Visual Studio from the installer.</span></span>

   <span data-ttu-id="8f4d6-108">如果您已安裝 Visual Studio，請選擇您想要新增F#至的版本旁邊的 [修改]。</span><span class="sxs-lookup"><span data-stu-id="8f4d6-108">If you already have Visual Studio installed, choose **Modify** next to the edition you want to add F# to.</span></span>

2. <span data-ttu-id="8f4d6-109">在 [工作負載] 頁面上，選取 [ **ASP.NET 和 網頁程式開發**] F#工作負載，其中包含 ASP.NET CORE 專案的和 .net Core 支援。</span><span class="sxs-lookup"><span data-stu-id="8f4d6-109">On the Workloads page, select the **ASP.NET and web development** workload, which includes F# and .NET Core support for ASP.NET Core projects.</span></span>

3. <span data-ttu-id="8f4d6-110">選擇右下角的 [**修改**]，以安裝您所選取的所有專案。</span><span class="sxs-lookup"><span data-stu-id="8f4d6-110">Choose **Modify** in the lower right-hand corner to install everything you've selected.</span></span>

   <span data-ttu-id="8f4d6-111">然後在 Visual Studio 安裝程式中選擇 [ F# **啟動**]，即可開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="8f4d6-111">You can then open Visual Studio with F# by choosing **Launch** in Visual Studio Installer.</span></span>

## <a name="install-f-with-visual-studio-code"></a><span data-ttu-id="8f4d6-112">使用F# Visual Studio Code 安裝</span><span class="sxs-lookup"><span data-stu-id="8f4d6-112">Install F# with Visual Studio Code</span></span>

1. <span data-ttu-id="8f4d6-113">請確定您已在您的路徑上安裝並使用[git](https://git-scm.com/download) 。</span><span class="sxs-lookup"><span data-stu-id="8f4d6-113">Ensure you have [git](https://git-scm.com/download) installed and available on your PATH.</span></span> <span data-ttu-id="8f4d6-114">您可以在命令提示字元中輸入 `git --version`，然後按**enter**鍵，確認它已正確安裝。</span><span class="sxs-lookup"><span data-stu-id="8f4d6-114">You can verify that it's installed correctly by entering `git --version` at a command prompt and pressing **Enter**.</span></span>

2. <span data-ttu-id="8f4d6-115">安裝[.NET Core SDK](https://dotnet.microsoft.com/download)和[Visual Studio Code](https://code.visualstudio.com)。</span><span class="sxs-lookup"><span data-stu-id="8f4d6-115">Install the [.NET Core SDK](https://dotnet.microsoft.com/download) and [Visual Studio Code](https://code.visualstudio.com).</span></span>

3. <span data-ttu-id="8f4d6-116">選取 [延伸模組] 圖示，並搜尋 "Ionide"：</span><span class="sxs-lookup"><span data-stu-id="8f4d6-116">Select the Extensions icon and search for "Ionide":</span></span>

   <span data-ttu-id="8f4d6-117">Visual Studio Code 中F#支援的唯一外掛程式是[Ionide-fsharp.core](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)。</span><span class="sxs-lookup"><span data-stu-id="8f4d6-117">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span> <span data-ttu-id="8f4d6-118">不過，您也可以安裝[Ionide-假](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE)以取得[假](https://fake.build/)的支援和[Ionide Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) ，以取得[Paket](https://fsprojects.github.io/Paket/)支援。</span><span class="sxs-lookup"><span data-stu-id="8f4d6-118">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) to get [FAKE](https://fake.build/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span></span> <span data-ttu-id="8f4d6-119">假和 Paket 是用F#來分別建立專案和管理相依性的額外社區工具。</span><span class="sxs-lookup"><span data-stu-id="8f4d6-119">FAKE and Paket are additional F# community tools for building projects and managing dependencies, respectively.</span></span>

## <a name="install-f-with-visual-studio-for-mac"></a><span data-ttu-id="8f4d6-120">使用F# Visual Studio for Mac 安裝</span><span class="sxs-lookup"><span data-stu-id="8f4d6-120">Install F# with Visual Studio for Mac</span></span>

<span data-ttu-id="8f4d6-121">F#預設會安裝在[Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)中，不論您選擇哪一種設定。</span><span class="sxs-lookup"><span data-stu-id="8f4d6-121">F# is installed by default in [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), no matter which configuration you choose.</span></span>

<span data-ttu-id="8f4d6-122">安裝完成之後，請選擇 [**開始 Visual Studio**]。</span><span class="sxs-lookup"><span data-stu-id="8f4d6-122">After the install completes, choose **Start Visual Studio**.</span></span> <span data-ttu-id="8f4d6-123">您也可以透過 macOS 上的搜尋工具開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="8f4d6-123">You can also open Visual Studio through Finder on macOS.</span></span>

## <a name="install-f-on-a-build-server"></a><span data-ttu-id="8f4d6-124">在F#組建伺服器上安裝</span><span class="sxs-lookup"><span data-stu-id="8f4d6-124">Install F# on a build server</span></span>

<span data-ttu-id="8f4d6-125">如果您是透過 .NET SDK 使用 .NET Core 或 .NET Framework，您只需要在組建伺服器上安裝 .NET SDK。</span><span class="sxs-lookup"><span data-stu-id="8f4d6-125">If you're using .NET Core or .NET Framework via the .NET SDK, you simply need to install the .NET SDK on your build server.</span></span> <span data-ttu-id="8f4d6-126">它包含您所需的所有專案。</span><span class="sxs-lookup"><span data-stu-id="8f4d6-126">It has everything you need.</span></span>

<span data-ttu-id="8f4d6-127">如果您使用 .NET Framework，而您**未**使用 .net SDK，則必須將[Visual Studio Build Tools SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16)安裝到您的 Windows 伺服器上。</span><span class="sxs-lookup"><span data-stu-id="8f4d6-127">If you're using .NET Framework and you are **not** using the .NET SDK, then you'll need to install the [Visual Studio Build Tools SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) onto your Windows Server.</span></span> <span data-ttu-id="8f4d6-128">在安裝程式中，選取 [ **.net 桌面組建工具**]，然後選取 [安裝程式] 功能表右側的 [  **F#編譯器**] 元件。</span><span class="sxs-lookup"><span data-stu-id="8f4d6-128">In the installer, select **.NET desktop build tools**, and then select the **F# compiler** component on the right-hand side of the installer menu.</span></span>
