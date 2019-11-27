---
title: 安裝 F#
description: 瞭解如何根據您F#的環境安裝。
ms.date: 09/05/2019
ms.openlocfilehash: 592a4c7763266cee68809fca84f9604d7e96b8f1
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204879"
---
# <a name="install-f"></a><span data-ttu-id="d93ff-103">安裝 F\#</span><span class="sxs-lookup"><span data-stu-id="d93ff-103">Install F\#</span></span>

<span data-ttu-id="d93ff-104">您可以透過F#多種方式安裝，視您的環境而定。</span><span class="sxs-lookup"><span data-stu-id="d93ff-104">You can install F# in multiple ways, depending on your environment.</span></span>

## <a name="install-f-with-visual-studio"></a><span data-ttu-id="d93ff-105">使用F# Visual Studio 安裝</span><span class="sxs-lookup"><span data-stu-id="d93ff-105">Install F# with Visual Studio</span></span>

<span data-ttu-id="d93ff-106">如果您是第一次下載[Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) ，它會先安裝 Visual Studio 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="d93ff-106">If you're downloading [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) for the first time, it will first install the Visual Studio installer.</span></span> <span data-ttu-id="d93ff-107">從安裝程式安裝適當的 Visual Studio SKU。</span><span class="sxs-lookup"><span data-stu-id="d93ff-107">Install the appropriate SKU of Visual Studio from the installer.</span></span> <span data-ttu-id="d93ff-108">如果您已經安裝它，請按一下 [**修改**]。</span><span class="sxs-lookup"><span data-stu-id="d93ff-108">If you already have it installed, click **Modify**.</span></span>

<span data-ttu-id="d93ff-109">接下來，您會看到工作負載清單。</span><span class="sxs-lookup"><span data-stu-id="d93ff-109">You'll next see a list of Workloads.</span></span> <span data-ttu-id="d93ff-110">選取 [ **ASP.NET 和 網頁程式開發**]， F#這將會安裝 ASP.NET Core 專案的支援和 .net Core 支援。</span><span class="sxs-lookup"><span data-stu-id="d93ff-110">Select **ASP.NET and web development** which will install F# support and .NET Core support for ASP.NET Core projects.</span></span>

<span data-ttu-id="d93ff-111">接下來，按一下右下方的 [**修改**]。</span><span class="sxs-lookup"><span data-stu-id="d93ff-111">Next, click **Modify** in the lower right-hand side.</span></span>  <span data-ttu-id="d93ff-112">這會安裝您所選取的所有專案。</span><span class="sxs-lookup"><span data-stu-id="d93ff-112">This will install everything you have selected.</span></span> <span data-ttu-id="d93ff-113">接著，您可以按一下 [ F# **啟動**]，開啟具有語言支援的 Visual Studio 2017。</span><span class="sxs-lookup"><span data-stu-id="d93ff-113">You can then open Visual Studio 2017 with F# language support by clicking **Launch**.</span></span>

## <a name="install-f-with-visual-studio-code"></a><span data-ttu-id="d93ff-114">使用F# Visual Studio Code 安裝</span><span class="sxs-lookup"><span data-stu-id="d93ff-114">Install F# with Visual Studio Code</span></span>

<span data-ttu-id="d93ff-115">首先，請確定您已在您的路徑上安裝並使用[git](https://git-scm.com/download) 。</span><span class="sxs-lookup"><span data-stu-id="d93ff-115">First, ensure you have [git installed](https://git-scm.com/download) and available on your PATH.</span></span> <span data-ttu-id="d93ff-116">您可以在命令提示字元中輸入 `git --version`，然後按**enter**鍵，確認是否已正確安裝。</span><span class="sxs-lookup"><span data-stu-id="d93ff-116">You can verify that it is installed correctly by typing `git --version` at a command prompt and pressing **Enter**.</span></span>

<span data-ttu-id="d93ff-117">接下來，安裝[.NET Core SDK](https://dotnet.microsoft.com/download)。</span><span class="sxs-lookup"><span data-stu-id="d93ff-117">Next, install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>

<span data-ttu-id="d93ff-118">接著，您將需要安裝[Visual Studio Code](https://code.visualstudio.com) 。</span><span class="sxs-lookup"><span data-stu-id="d93ff-118">You will then need [Visual Studio Code](https://code.visualstudio.com) installed.</span></span>

<span data-ttu-id="d93ff-119">接下來，按一下 [延伸模組] 圖示，然後搜尋 "Ionide"：</span><span class="sxs-lookup"><span data-stu-id="d93ff-119">Next, click the Extensions icon and search for "Ionide":</span></span>

<span data-ttu-id="d93ff-120">Visual Studio Code 中F#支援的唯一外掛程式是[Ionide-fsharp.core](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)。</span><span class="sxs-lookup"><span data-stu-id="d93ff-120">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span> <span data-ttu-id="d93ff-121">不過，您也可以安裝[Ionide-假](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE)以取得[假](https://fake.build/)的支援和[Ionide Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) ，以取得[Paket](https://fsprojects.github.io/Paket/)支援。</span><span class="sxs-lookup"><span data-stu-id="d93ff-121">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) to get [FAKE](https://fake.build/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span></span> <span data-ttu-id="d93ff-122">假和 Paket 是用F#來分別建立專案和管理相依性的額外社區工具。</span><span class="sxs-lookup"><span data-stu-id="d93ff-122">FAKE and Paket are additional F# community tools for building projects and managing dependencies, respectively.</span></span>

## <a name="install-f-with-visual-studio-for-mac"></a><span data-ttu-id="d93ff-123">使用F# Visual Studio for Mac 安裝</span><span class="sxs-lookup"><span data-stu-id="d93ff-123">Install F# with Visual Studio for Mac</span></span>

<span data-ttu-id="d93ff-124">F#預設會安裝在[Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)中，不論您選擇哪一種設定。</span><span class="sxs-lookup"><span data-stu-id="d93ff-124">F# is installed by default in [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), no matter which configuration you choose.</span></span>

<span data-ttu-id="d93ff-125">安裝完成之後，請選擇 [開始 Visual Studio]。</span><span class="sxs-lookup"><span data-stu-id="d93ff-125">After the install completes, choose "Start Visual Studio".</span></span> <span data-ttu-id="d93ff-126">您也可以透過 macOS 上的搜尋工具來啟動它。</span><span class="sxs-lookup"><span data-stu-id="d93ff-126">You can also launch it through Finder on macOS.</span></span>

## <a name="install-f-on-a-build-server"></a><span data-ttu-id="d93ff-127">在F#組建伺服器上安裝</span><span class="sxs-lookup"><span data-stu-id="d93ff-127">Install F# on a Build Server</span></span>

<span data-ttu-id="d93ff-128">如果您是透過 .NET SDK 使用 .NET Core 或 .NET Framework，您只需要在組建伺服器上安裝 .NET SDK。</span><span class="sxs-lookup"><span data-stu-id="d93ff-128">If you are using .NET Core or .NET Framework via the .NET SDK, you simply need to install the .NET SDK on your build server.</span></span> <span data-ttu-id="d93ff-129">它包含您所需的所有專案。</span><span class="sxs-lookup"><span data-stu-id="d93ff-129">It has everything you need.</span></span>

<span data-ttu-id="d93ff-130">如果您使用 .NET Framework，而您**未**使用 .net SDK，則必須將[Visual Studio Build Tools SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16)安裝到您的 Windows 伺服器上。</span><span class="sxs-lookup"><span data-stu-id="d93ff-130">If you are using .NET Framework and you are **not** using the .NET SDK, then you will need to install the [Visual Studio Build Tools SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) onto your Windows Server.</span></span> <span data-ttu-id="d93ff-131">在安裝程式中，選取 [ **.net 桌面組建工具**]，然後選取 [安裝程式] 功能表右側的 [  **F#編譯器**] 元件。</span><span class="sxs-lookup"><span data-stu-id="d93ff-131">In the installer, select **.NET desktop build tools** and then select the **F# compiler** component on the right side of the installer menu.</span></span>
