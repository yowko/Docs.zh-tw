---
title: '安裝 F #'
description: '了解如何安裝 F # 根據您的環境。'
ms.date: 08/28/2018
ms.openlocfilehash: 909e1c07ff7f6d52db77a987639d1c749146fdca
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49120930"
---
# <a name="install-f"></a><span data-ttu-id="baebd-103">安裝 F #</span><span class="sxs-lookup"><span data-stu-id="baebd-103">Install F#</span></span> #

<span data-ttu-id="baebd-104">您可以安裝 F # 以多種方式，根據您的環境。</span><span class="sxs-lookup"><span data-stu-id="baebd-104">You can install F# in multiple ways, depending on your environment.</span></span>

## <a name="install-f-with-visual-studio"></a><span data-ttu-id="baebd-105">安裝 F # 與 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="baebd-105">Install F# with Visual Studio</span></span>

<span data-ttu-id="baebd-106">如果您正在下載[Visual Studio](https://visualstudio.microsoft.com/)第一次，它會先安裝 Visual Studio 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="baebd-106">If you're downloading [Visual Studio](https://visualstudio.microsoft.com/) for the first time, it will first install the Visual Studio installer.</span></span> <span data-ttu-id="baebd-107">安裝適當的 SKU 的 Visual Studio 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="baebd-107">Install the appropriate SKU of Visual Studio from the installer.</span></span> <span data-ttu-id="baebd-108">如果您已經安裝，請按一下**修改**。</span><span class="sxs-lookup"><span data-stu-id="baebd-108">If you already have it installed, click **Modify**.</span></span>

<span data-ttu-id="baebd-109">接下來，您會看到一份工作負載。</span><span class="sxs-lookup"><span data-stu-id="baebd-109">You'll next see a list of Workloads.</span></span> <span data-ttu-id="baebd-110">選取  **ASP.NET 和 web 開發**安裝 F # 支援和 ASP.NET Core 專案的.NET Core 支援。</span><span class="sxs-lookup"><span data-stu-id="baebd-110">Select **ASP.NET and web development** which will install F# support and .NET Core support for ASP.NET Core projects.</span></span>

<span data-ttu-id="baebd-111">接下來，按一下**修改**右手邊角。</span><span class="sxs-lookup"><span data-stu-id="baebd-111">Next, click **Modify** in the lower right-hand side.</span></span>  <span data-ttu-id="baebd-112">這會安裝您所選取的所有項目。</span><span class="sxs-lookup"><span data-stu-id="baebd-112">This will install everything you have selected.</span></span> <span data-ttu-id="baebd-113">您接著可以開啟使用 F # 語言支援 Visual Studio 2017，依序按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="baebd-113">You can then open Visual Studio 2017 with F# language support by clicking **Launch**.</span></span>

## <a name="install-f-with-visual-studio-for-mac"></a><span data-ttu-id="baebd-114">安裝 F # 與 Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="baebd-114">Install F# with Visual Studio for Mac</span></span>

<span data-ttu-id="baebd-115">F # 預設會安裝在[Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/)，無論哪種設定您選擇。</span><span class="sxs-lookup"><span data-stu-id="baebd-115">F# is installed by default in [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/), no matter which configuration you choose.</span></span>

<span data-ttu-id="baebd-116">安裝完成後，選擇 [啟動 Visual Studio]。</span><span class="sxs-lookup"><span data-stu-id="baebd-116">After the install completes, choose "Start Visual Studio".</span></span> <span data-ttu-id="baebd-117">您也可以啟動它透過搜尋工具在 macOS 上。</span><span class="sxs-lookup"><span data-stu-id="baebd-117">You can also launch it through Finder on macOS.</span></span>

## <a name="install-f-with-visual-studio-code"></a><span data-ttu-id="baebd-118">安裝 F # 與 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="baebd-118">Install F# with Visual Studio Code</span></span>

<span data-ttu-id="baebd-119">您必須擁有[安裝 git](https://git-scm.com/download) ，可在您的路徑，請使用專案範本。</span><span class="sxs-lookup"><span data-stu-id="baebd-119">You must have [git installed](https://git-scm.com/download) and available on your PATH to make use of project templates.</span></span> <span data-ttu-id="baebd-120">您可以確認它已正確安裝輸入`git --version`在命令提示字元並按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="baebd-120">You can verify that it is installed correctly by typing `git --version` at a command prompt and pressing **Enter**.</span></span>

### <a name="macostabmacos"></a>[<span data-ttu-id="baebd-121">macOS</span><span class="sxs-lookup"><span data-stu-id="baebd-121">macOS</span></span>](#tab/macos)

<span data-ttu-id="baebd-122">[Mono](http://www.mono-project.com)使用於[F # Interactive](../tutorials/fsharp-interactive/index.md)支援。</span><span class="sxs-lookup"><span data-stu-id="baebd-122">[Mono](http://www.mono-project.com) is used for [F# Interactive](../tutorials/fsharp-interactive/index.md) support.</span></span> <span data-ttu-id="baebd-123">在 macOS 上安裝 Mono 的最簡單方式是透過 Homebrew。</span><span class="sxs-lookup"><span data-stu-id="baebd-123">The easiest way to install Mono on macOS is via Homebrew.</span></span> <span data-ttu-id="baebd-124">只要您的終端機中輸入下列：</span><span class="sxs-lookup"><span data-stu-id="baebd-124">Simply type the following into your terminal:</span></span>

```console
brew install mono
```

<span data-ttu-id="baebd-125">也會安裝[.NET Core SDK](https://www.microsoft.com/net/download)。</span><span class="sxs-lookup"><span data-stu-id="baebd-125">Also install the [.NET Core SDK](https://www.microsoft.com/net/download).</span></span>

### <a name="linuxtablinux"></a>[<span data-ttu-id="baebd-126">Linux</span><span class="sxs-lookup"><span data-stu-id="baebd-126">Linux</span></span>](#tab/linux)

<span data-ttu-id="baebd-127">[Mono](https://www.mono-project.com)使用於[F # Interactive](../tutorials/fsharp-interactive/index.md)支援。</span><span class="sxs-lookup"><span data-stu-id="baebd-127">[Mono](https://www.mono-project.com) is used for [F# Interactive](../tutorials/fsharp-interactive/index.md) support.</span></span> <span data-ttu-id="baebd-128">如果您是在 Debian 或 Ubuntu 上，您可以使用下列項目：</span><span class="sxs-lookup"><span data-stu-id="baebd-128">If you're on Debian or Ubuntu, you can use the following:</span></span>

```console
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

<span data-ttu-id="baebd-129">也會安裝[.NET Core SDK](https://www.microsoft.com/net/download)。</span><span class="sxs-lookup"><span data-stu-id="baebd-129">Also install the [.NET Core SDK](https://www.microsoft.com/net/download).</span></span>

### <a name="windowstabwindows"></a>[<span data-ttu-id="baebd-130">Windows</span><span class="sxs-lookup"><span data-stu-id="baebd-130">Windows</span></span>](#tab/windows)

<span data-ttu-id="baebd-131">安裝[Visual Studio 中使用 F # 支援](#install-f-with-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="baebd-131">Install [Visual Studio with F# support](#install-f-with-visual-studio).</span></span> <span data-ttu-id="baebd-132">這會安裝所有必要的元件，來撰寫、 編譯及執行 F # 程式碼。</span><span class="sxs-lookup"><span data-stu-id="baebd-132">This installs all the necessary components to write, compile, and execute F# code.</span></span>

<span data-ttu-id="baebd-133">也會安裝[.NET Core SDK](https://www.microsoft.com/net/download/)。</span><span class="sxs-lookup"><span data-stu-id="baebd-133">Also install the [.NET Core SDK](https://www.microsoft.com/net/download/).</span></span>

---

<span data-ttu-id="baebd-134">然後您必須[Visual Studio Code](https://code.visualstudio.com)安裝。</span><span class="sxs-lookup"><span data-stu-id="baebd-134">You will then need [Visual Studio Code](https://code.visualstudio.com) installed.</span></span>

<span data-ttu-id="baebd-135">接下來，按一下 擴充功能圖示並搜尋"Ionide 」:</span><span class="sxs-lookup"><span data-stu-id="baebd-135">Next, click the Extensions icon and search for "Ionide":</span></span>

<span data-ttu-id="baebd-136">在 Visual Studio Code 中的 F # 支援所需的唯一外掛程式[Ionide fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)。</span><span class="sxs-lookup"><span data-stu-id="baebd-136">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span> <span data-ttu-id="baebd-137">不過，您也可以安裝[Ionide FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE)若要取得[假](https://fsharp.github.io/FAKE/)支援並[Ionide Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket)取得[Paket](https://fsprojects.github.io/Paket/)支援。</span><span class="sxs-lookup"><span data-stu-id="baebd-137">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) to get [FAKE](https://fsharp.github.io/FAKE/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span></span> <span data-ttu-id="baebd-138">假 Paket，而 其他 F # 社群的工具建置專案，並分別管理相依性。</span><span class="sxs-lookup"><span data-stu-id="baebd-138">FAKE and Paket are additional F# community tools for building projects and managing dependencies, respectively.</span></span>
