---
title: 安裝 F#
description: 瞭解如何根據您F#的環境安裝。
ms.date: 09/05/2019
ms.openlocfilehash: dffa30eac0bdb59c85a66dca6cafd62b25daa572
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855798"
---
# <a name="install-f"></a><span data-ttu-id="189e5-103">安裝 F\#</span><span class="sxs-lookup"><span data-stu-id="189e5-103">Install F\#</span></span>

<span data-ttu-id="189e5-104">您可以透過F#多種方式安裝，視您的環境而定。</span><span class="sxs-lookup"><span data-stu-id="189e5-104">You can install F# in multiple ways, depending on your environment.</span></span>

## <a name="install-f-with-visual-studio"></a><span data-ttu-id="189e5-105">使用F# Visual Studio 安裝</span><span class="sxs-lookup"><span data-stu-id="189e5-105">Install F# with Visual Studio</span></span>

<span data-ttu-id="189e5-106">如果您是第一次下載[Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) ，它會先安裝 Visual Studio 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="189e5-106">If you're downloading [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) for the first time, it will first install the Visual Studio installer.</span></span> <span data-ttu-id="189e5-107">從安裝程式安裝適當的 Visual Studio SKU。</span><span class="sxs-lookup"><span data-stu-id="189e5-107">Install the appropriate SKU of Visual Studio from the installer.</span></span> <span data-ttu-id="189e5-108">如果您已經安裝它，請按一下 [**修改**]。</span><span class="sxs-lookup"><span data-stu-id="189e5-108">If you already have it installed, click **Modify**.</span></span>

<span data-ttu-id="189e5-109">接下來，您會看到工作負載清單。</span><span class="sxs-lookup"><span data-stu-id="189e5-109">You'll next see a list of Workloads.</span></span> <span data-ttu-id="189e5-110">選取 [ **ASP.NET 和 網頁程式開發**]， F#這將會安裝 ASP.NET Core 專案的支援和 .net Core 支援。</span><span class="sxs-lookup"><span data-stu-id="189e5-110">Select **ASP.NET and web development** which will install F# support and .NET Core support for ASP.NET Core projects.</span></span>

<span data-ttu-id="189e5-111">接下來，按一下右下方的 [**修改**]。</span><span class="sxs-lookup"><span data-stu-id="189e5-111">Next, click **Modify** in the lower right-hand side.</span></span>  <span data-ttu-id="189e5-112">這會安裝您所選取的所有專案。</span><span class="sxs-lookup"><span data-stu-id="189e5-112">This will install everything you have selected.</span></span> <span data-ttu-id="189e5-113">接著，您可以按一下 [ F# **啟動**]，開啟具有語言支援的 Visual Studio 2017。</span><span class="sxs-lookup"><span data-stu-id="189e5-113">You can then open Visual Studio 2017 with F# language support by clicking **Launch**.</span></span>

## <a name="install-f-with-visual-studio-for-mac"></a><span data-ttu-id="189e5-114">使用F# Visual Studio for Mac 安裝</span><span class="sxs-lookup"><span data-stu-id="189e5-114">Install F# with Visual Studio for Mac</span></span>

<span data-ttu-id="189e5-115">F#預設會安裝在[Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)中，不論您選擇哪一種設定。</span><span class="sxs-lookup"><span data-stu-id="189e5-115">F# is installed by default in [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), no matter which configuration you choose.</span></span>

<span data-ttu-id="189e5-116">安裝完成之後，請選擇 [開始 Visual Studio]。</span><span class="sxs-lookup"><span data-stu-id="189e5-116">After the install completes, choose "Start Visual Studio".</span></span> <span data-ttu-id="189e5-117">您也可以透過 macOS 上的搜尋工具來啟動它。</span><span class="sxs-lookup"><span data-stu-id="189e5-117">You can also launch it through Finder on macOS.</span></span>

## <a name="install-f-with-visual-studio-code"></a><span data-ttu-id="189e5-118">使用F# Visual Studio Code 安裝</span><span class="sxs-lookup"><span data-stu-id="189e5-118">Install F# with Visual Studio Code</span></span>

<span data-ttu-id="189e5-119">您必須在路徑上安裝並使用[git](https://git-scm.com/download) ，才能利用專案範本。</span><span class="sxs-lookup"><span data-stu-id="189e5-119">You must have [git installed](https://git-scm.com/download) and available on your PATH to make use of project templates.</span></span> <span data-ttu-id="189e5-120">您可以在命令提示字元中輸入`git --version`並按**enter**，確認它是否已正確安裝。</span><span class="sxs-lookup"><span data-stu-id="189e5-120">You can verify that it is installed correctly by typing `git --version` at a command prompt and pressing **Enter**.</span></span>

### <a name="macostabmacos"></a>[<span data-ttu-id="189e5-121">macOS</span><span class="sxs-lookup"><span data-stu-id="189e5-121">macOS</span></span>](#tab/macos)

<span data-ttu-id="189e5-122">[Mono](https://www.mono-project.com)用於[ F#互動式](../tutorials/fsharp-interactive/index.md)支援。</span><span class="sxs-lookup"><span data-stu-id="189e5-122">[Mono](https://www.mono-project.com) is used for [F# Interactive](../tutorials/fsharp-interactive/index.md) support.</span></span> <span data-ttu-id="189e5-123">在 macOS 上安裝 Mono 最簡單的方式是透過 Homebrew。</span><span class="sxs-lookup"><span data-stu-id="189e5-123">The easiest way to install Mono on macOS is via Homebrew.</span></span> <span data-ttu-id="189e5-124">只要在您的終端機中輸入下列內容：</span><span class="sxs-lookup"><span data-stu-id="189e5-124">Simply type the following into your terminal:</span></span>

```console
brew install mono
```

<span data-ttu-id="189e5-125">也請安裝[.NET Core SDK](https://dotnet.microsoft.com/download)。</span><span class="sxs-lookup"><span data-stu-id="189e5-125">Also install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>

### <a name="linuxtablinux"></a>[<span data-ttu-id="189e5-126">Linux</span><span class="sxs-lookup"><span data-stu-id="189e5-126">Linux</span></span>](#tab/linux)

<span data-ttu-id="189e5-127">[Mono](https://www.mono-project.com)用於[ F#互動式](../tutorials/fsharp-interactive/index.md)支援。</span><span class="sxs-lookup"><span data-stu-id="189e5-127">[Mono](https://www.mono-project.com) is used for [F# Interactive](../tutorials/fsharp-interactive/index.md) support.</span></span> <span data-ttu-id="189e5-128">如果您是在 Debian 或 Ubuntu 上，您可以使用下列各項：</span><span class="sxs-lookup"><span data-stu-id="189e5-128">If you're on Debian or Ubuntu, you can use the following:</span></span>

```console
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

<span data-ttu-id="189e5-129">也請安裝[.NET Core SDK](https://dotnet.microsoft.com/download)。</span><span class="sxs-lookup"><span data-stu-id="189e5-129">Also install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>

### <a name="windowstabwindows"></a>[<span data-ttu-id="189e5-130">Windows</span><span class="sxs-lookup"><span data-stu-id="189e5-130">Windows</span></span>](#tab/windows)

<span data-ttu-id="189e5-131">安裝[支援的F# Visual Studio](#install-f-with-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="189e5-131">Install [Visual Studio with F# support](#install-f-with-visual-studio).</span></span> <span data-ttu-id="189e5-132">這會安裝所有必要的元件來撰寫、編譯和執行F#程式碼。</span><span class="sxs-lookup"><span data-stu-id="189e5-132">This installs all the necessary components to write, compile, and execute F# code.</span></span>

<span data-ttu-id="189e5-133">也請安裝[.NET Core SDK](https://dotnet.microsoft.com/download)。</span><span class="sxs-lookup"><span data-stu-id="189e5-133">Also install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>

---

<span data-ttu-id="189e5-134">接著，您將需要安裝[Visual Studio Code](https://code.visualstudio.com) 。</span><span class="sxs-lookup"><span data-stu-id="189e5-134">You will then need [Visual Studio Code](https://code.visualstudio.com) installed.</span></span>

<span data-ttu-id="189e5-135">接下來，按一下 [延伸模組] 圖示，然後搜尋 "Ionide"：</span><span class="sxs-lookup"><span data-stu-id="189e5-135">Next, click the Extensions icon and search for "Ionide":</span></span>

<span data-ttu-id="189e5-136">Visual Studio Code 中F#支援的唯一外掛程式是[Ionide-fsharp.core](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)。</span><span class="sxs-lookup"><span data-stu-id="189e5-136">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span> <span data-ttu-id="189e5-137">不過，您也可以安裝[Ionide-假](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE)以取得[假](https://fsharp.github.io/FAKE/)的支援和[Ionide Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) ，以取得[Paket](https://fsprojects.github.io/Paket/)支援。</span><span class="sxs-lookup"><span data-stu-id="189e5-137">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) to get [FAKE](https://fsharp.github.io/FAKE/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span></span> <span data-ttu-id="189e5-138">假和 Paket 是用F#來分別建立專案和管理相依性的額外社區工具。</span><span class="sxs-lookup"><span data-stu-id="189e5-138">FAKE and Paket are additional F# community tools for building projects and managing dependencies, respectively.</span></span>

## <a name="install-f-on-a-build-server"></a><span data-ttu-id="189e5-139">在F#組建伺服器上安裝</span><span class="sxs-lookup"><span data-stu-id="189e5-139">Install F# on a Build Server</span></span>

<span data-ttu-id="189e5-140">如果您是透過 .NET SDK 使用 .NET Core 或 .NET Framework，您只需要在組建伺服器上安裝 .NET SDK。</span><span class="sxs-lookup"><span data-stu-id="189e5-140">If you are using .NET Core or .NET Framework via the .NET SDK, you simply need to install the .NET SDK on your build server.</span></span> <span data-ttu-id="189e5-141">它包含您所需的所有專案。</span><span class="sxs-lookup"><span data-stu-id="189e5-141">It has everything you need.</span></span>

<span data-ttu-id="189e5-142">如果您使用 .NET Framework，而您**未**使用 .net SDK，則必須將[Visual Studio Build Tools SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16)安裝到您的 Windows 伺服器上。</span><span class="sxs-lookup"><span data-stu-id="189e5-142">If you are using .NET Framework and you are **not** using the .NET SDK, then you will need to install the [Visual Studio Build Tools SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) onto your Windows Server.</span></span> <span data-ttu-id="189e5-143">在安裝程式中，選取 [ **.net 桌面組建工具**]，然後選取 [安裝程式] 功能表右側的 [  **F#編譯器**] 元件。</span><span class="sxs-lookup"><span data-stu-id="189e5-143">In the installer, select **.NET desktop build tools** and then select the **F# compiler** component on the right side of the installer menu.</span></span>
