---
title: 安裝F#
description: 了解如何安裝F#根據您的環境。
ms.date: 08/28/2018
ms.openlocfilehash: 792c61c0522cd4d0c68a64572f2892ce33f71ea6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59331971"
---
# <a name="install-f"></a><span data-ttu-id="f0a49-103">安裝 F\#</span><span class="sxs-lookup"><span data-stu-id="f0a49-103">Install F\#</span></span>

<span data-ttu-id="f0a49-104">您可以安裝F#以多種方式，根據您的環境。</span><span class="sxs-lookup"><span data-stu-id="f0a49-104">You can install F# in multiple ways, depending on your environment.</span></span>

## <a name="install-f-with-visual-studio"></a><span data-ttu-id="f0a49-105">安裝F#使用 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f0a49-105">Install F# with Visual Studio</span></span>

<span data-ttu-id="f0a49-106">如果您正在下載[Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)第一次，它會先安裝 Visual Studio 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="f0a49-106">If you're downloading [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) for the first time, it will first install the Visual Studio installer.</span></span> <span data-ttu-id="f0a49-107">安裝適當的 SKU 的 Visual Studio 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="f0a49-107">Install the appropriate SKU of Visual Studio from the installer.</span></span> <span data-ttu-id="f0a49-108">如果您已經安裝，請按一下**修改**。</span><span class="sxs-lookup"><span data-stu-id="f0a49-108">If you already have it installed, click **Modify**.</span></span>

<span data-ttu-id="f0a49-109">接下來，您會看到一份工作負載。</span><span class="sxs-lookup"><span data-stu-id="f0a49-109">You'll next see a list of Workloads.</span></span> <span data-ttu-id="f0a49-110">選取  **ASP.NET 和 web 開發**安裝F#支援和.NET Core 支援 ASP.NET Core 專案。</span><span class="sxs-lookup"><span data-stu-id="f0a49-110">Select **ASP.NET and web development** which will install F# support and .NET Core support for ASP.NET Core projects.</span></span>

<span data-ttu-id="f0a49-111">接下來，按一下**修改**右手邊角。</span><span class="sxs-lookup"><span data-stu-id="f0a49-111">Next, click **Modify** in the lower right-hand side.</span></span>  <span data-ttu-id="f0a49-112">這會安裝您所選取的所有項目。</span><span class="sxs-lookup"><span data-stu-id="f0a49-112">This will install everything you have selected.</span></span> <span data-ttu-id="f0a49-113">接著，您就可以開啟 Visual Studio 2017F#語言支援，即可**啟動**。</span><span class="sxs-lookup"><span data-stu-id="f0a49-113">You can then open Visual Studio 2017 with F# language support by clicking **Launch**.</span></span>

## <a name="install-f-with-visual-studio-for-mac"></a><span data-ttu-id="f0a49-114">安裝F#使用 Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="f0a49-114">Install F# with Visual Studio for Mac</span></span>

<span data-ttu-id="f0a49-115">F#根據預設，在已安裝[Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)，無論哪種設定您選擇。</span><span class="sxs-lookup"><span data-stu-id="f0a49-115">F# is installed by default in [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), no matter which configuration you choose.</span></span>

<span data-ttu-id="f0a49-116">安裝完成後，選擇 [啟動 Visual Studio]。</span><span class="sxs-lookup"><span data-stu-id="f0a49-116">After the install completes, choose "Start Visual Studio".</span></span> <span data-ttu-id="f0a49-117">您也可以啟動它透過搜尋工具在 macOS 上。</span><span class="sxs-lookup"><span data-stu-id="f0a49-117">You can also launch it through Finder on macOS.</span></span>

## <a name="install-f-with-visual-studio-code"></a><span data-ttu-id="f0a49-118">安裝F#使用 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="f0a49-118">Install F# with Visual Studio Code</span></span>

<span data-ttu-id="f0a49-119">您必須擁有[安裝 git](https://git-scm.com/download) ，可在您的路徑，請使用專案範本。</span><span class="sxs-lookup"><span data-stu-id="f0a49-119">You must have [git installed](https://git-scm.com/download) and available on your PATH to make use of project templates.</span></span> <span data-ttu-id="f0a49-120">您可以確認它已正確安裝輸入`git --version`在命令提示字元並按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="f0a49-120">You can verify that it is installed correctly by typing `git --version` at a command prompt and pressing **Enter**.</span></span>

### <a name="macostabmacos"></a>[<span data-ttu-id="f0a49-121">macOS</span><span class="sxs-lookup"><span data-stu-id="f0a49-121">macOS</span></span>](#tab/macos)

<span data-ttu-id="f0a49-122">[Mono](https://www.mono-project.com)使用於[F#互動式](../tutorials/fsharp-interactive/index.md)支援。</span><span class="sxs-lookup"><span data-stu-id="f0a49-122">[Mono](https://www.mono-project.com) is used for [F# Interactive](../tutorials/fsharp-interactive/index.md) support.</span></span> <span data-ttu-id="f0a49-123">在 macOS 上安裝 Mono 的最簡單方式是透過 Homebrew。</span><span class="sxs-lookup"><span data-stu-id="f0a49-123">The easiest way to install Mono on macOS is via Homebrew.</span></span> <span data-ttu-id="f0a49-124">只要您的終端機中輸入下列：</span><span class="sxs-lookup"><span data-stu-id="f0a49-124">Simply type the following into your terminal:</span></span>

```console
brew install mono
```

<span data-ttu-id="f0a49-125">也會安裝[.NET Core SDK](https://www.microsoft.com/net/download)。</span><span class="sxs-lookup"><span data-stu-id="f0a49-125">Also install the [.NET Core SDK](https://www.microsoft.com/net/download).</span></span>

### <a name="linuxtablinux"></a>[<span data-ttu-id="f0a49-126">Linux</span><span class="sxs-lookup"><span data-stu-id="f0a49-126">Linux</span></span>](#tab/linux)

<span data-ttu-id="f0a49-127">[Mono](https://www.mono-project.com)使用於[F#互動式](../tutorials/fsharp-interactive/index.md)支援。</span><span class="sxs-lookup"><span data-stu-id="f0a49-127">[Mono](https://www.mono-project.com) is used for [F# Interactive](../tutorials/fsharp-interactive/index.md) support.</span></span> <span data-ttu-id="f0a49-128">如果您是在 Debian 或 Ubuntu 上，您可以使用下列項目：</span><span class="sxs-lookup"><span data-stu-id="f0a49-128">If you're on Debian or Ubuntu, you can use the following:</span></span>

```console
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

<span data-ttu-id="f0a49-129">也會安裝[.NET Core SDK](https://www.microsoft.com/net/download)。</span><span class="sxs-lookup"><span data-stu-id="f0a49-129">Also install the [.NET Core SDK](https://www.microsoft.com/net/download).</span></span>

### <a name="windowstabwindows"></a>[<span data-ttu-id="f0a49-130">Windows</span><span class="sxs-lookup"><span data-stu-id="f0a49-130">Windows</span></span>](#tab/windows)

<span data-ttu-id="f0a49-131">安裝[Visual Studio 中使用F#支援](#install-f-with-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="f0a49-131">Install [Visual Studio with F# support](#install-f-with-visual-studio).</span></span> <span data-ttu-id="f0a49-132">這會安裝所有必要的元件，來撰寫、 編譯及執行F#程式碼。</span><span class="sxs-lookup"><span data-stu-id="f0a49-132">This installs all the necessary components to write, compile, and execute F# code.</span></span>

<span data-ttu-id="f0a49-133">也會安裝[.NET Core SDK](https://www.microsoft.com/net/download/)。</span><span class="sxs-lookup"><span data-stu-id="f0a49-133">Also install the [.NET Core SDK](https://www.microsoft.com/net/download/).</span></span>

---

<span data-ttu-id="f0a49-134">然後您必須[Visual Studio Code](https://code.visualstudio.com)安裝。</span><span class="sxs-lookup"><span data-stu-id="f0a49-134">You will then need [Visual Studio Code](https://code.visualstudio.com) installed.</span></span>

<span data-ttu-id="f0a49-135">接下來，按一下 擴充功能圖示並搜尋"Ionide 」:</span><span class="sxs-lookup"><span data-stu-id="f0a49-135">Next, click the Extensions icon and search for "Ionide":</span></span>

<span data-ttu-id="f0a49-136">唯一的外掛程式所需的F#支援在 Visual Studio Code [Ionide fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)。</span><span class="sxs-lookup"><span data-stu-id="f0a49-136">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span> <span data-ttu-id="f0a49-137">不過，您也可以安裝[Ionide FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE)若要取得[假](https://fsharp.github.io/FAKE/)支援並[Ionide Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket)取得[Paket](https://fsprojects.github.io/Paket/)支援。</span><span class="sxs-lookup"><span data-stu-id="f0a49-137">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) to get [FAKE](https://fsharp.github.io/FAKE/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span></span> <span data-ttu-id="f0a49-138">假和 Paket 是其他F#建置專案，並分別管理相依性的社群工具。</span><span class="sxs-lookup"><span data-stu-id="f0a49-138">FAKE and Paket are additional F# community tools for building projects and managing dependencies, respectively.</span></span>
