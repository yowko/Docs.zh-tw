---
title: 安裝 F#
description: '瞭解如何以各種不同的方式安裝 F #。'
ms.date: 12/20/2019
ms.openlocfilehash: 302e04f7cf3271516dff88d9d5f18f620b6ede80
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/20/2020
ms.locfileid: "92224290"
---
# <a name="install-f"></a><span data-ttu-id="f3e1f-103">安裝 F\#</span><span class="sxs-lookup"><span data-stu-id="f3e1f-103">Install F\#</span></span>

<span data-ttu-id="f3e1f-104">您可以用多種方式安裝 F #，視您的環境而定。</span><span class="sxs-lookup"><span data-stu-id="f3e1f-104">You can install F# in multiple ways, depending on your environment.</span></span>

## <a name="install-f-with-visual-studio"></a><span data-ttu-id="f3e1f-105">使用 Visual Studio 安裝 F #</span><span class="sxs-lookup"><span data-stu-id="f3e1f-105">Install F# with Visual Studio</span></span>

1. <span data-ttu-id="f3e1f-106">如果您是第一次下載 [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ，它會先安裝 Visual Studio 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="f3e1f-106">If you're downloading [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) for the first time, it will first install Visual Studio Installer.</span></span> <span data-ttu-id="f3e1f-107">從安裝程式安裝適當的 Visual Studio 版本。</span><span class="sxs-lookup"><span data-stu-id="f3e1f-107">Install the appropriate edition of Visual Studio from the installer.</span></span>

   <span data-ttu-id="f3e1f-108">如果您已經安裝 Visual Studio，請選擇您想要新增 F # 的版本旁的 [ **修改** ]。</span><span class="sxs-lookup"><span data-stu-id="f3e1f-108">If you already have Visual Studio installed, choose **Modify** next to the edition you want to add F# to.</span></span>

2. <span data-ttu-id="f3e1f-109">在 [工作負載] 頁面上，選取 [ **ASP.NET] 和 [網頁程式開發** ] 工作負載，其中包含 ASP.NET Core 專案的 F # 和 .net Core 支援。</span><span class="sxs-lookup"><span data-stu-id="f3e1f-109">On the Workloads page, select the **ASP.NET and web development** workload, which includes F# and .NET Core support for ASP.NET Core projects.</span></span>

3. <span data-ttu-id="f3e1f-110">選擇右下角的 [ **修改** ]，以安裝您所選取的所有專案。</span><span class="sxs-lookup"><span data-stu-id="f3e1f-110">Choose **Modify** in the lower right-hand corner to install everything you've selected.</span></span>

   <span data-ttu-id="f3e1f-111">然後，您可以在 Visual Studio 安裝程式中選擇 [ **啟動** ]，以 F # 開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="f3e1f-111">You can then open Visual Studio with F# by choosing **Launch** in Visual Studio Installer.</span></span>

## <a name="install-f-with-visual-studio-code"></a><span data-ttu-id="f3e1f-112">使用 Visual Studio Code 安裝 F #</span><span class="sxs-lookup"><span data-stu-id="f3e1f-112">Install F# with Visual Studio Code</span></span>

1. <span data-ttu-id="f3e1f-113">確定您已在路徑上安裝並提供 [git](https://git-scm.com/download) 。</span><span class="sxs-lookup"><span data-stu-id="f3e1f-113">Ensure you have [git](https://git-scm.com/download) installed and available on your PATH.</span></span> <span data-ttu-id="f3e1f-114">您可以 `git --version` 在命令提示字元中輸入，然後按 **enter**，確認它是否已正確安裝。</span><span class="sxs-lookup"><span data-stu-id="f3e1f-114">You can verify that it's installed correctly by entering `git --version` at a command prompt and pressing **Enter**.</span></span>

2. <span data-ttu-id="f3e1f-115">安裝 [.NET Core SDK](https://dotnet.microsoft.com/download) 並 [Visual Studio Code](https://code.visualstudio.com)。</span><span class="sxs-lookup"><span data-stu-id="f3e1f-115">Install the [.NET Core SDK](https://dotnet.microsoft.com/download) and [Visual Studio Code](https://code.visualstudio.com).</span></span>

3. <span data-ttu-id="f3e1f-116">選取擴充功能圖示，並搜尋 "Ionide"：</span><span class="sxs-lookup"><span data-stu-id="f3e1f-116">Select the Extensions icon and search for "Ionide":</span></span>

   <span data-ttu-id="f3e1f-117">Visual Studio Code 中 F # 支援所需的唯一外掛程式是 [Ionide-fsharp.core](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)。</span><span class="sxs-lookup"><span data-stu-id="f3e1f-117">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span> <span data-ttu-id="f3e1f-118">不過，您也可以安裝 [Ionide-假](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) 以取得 [假](https://fake.build/) 的支援和 [Ionide Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) ，以取得 [Paket](https://fsprojects.github.io/Paket/) 支援。</span><span class="sxs-lookup"><span data-stu-id="f3e1f-118">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) to get [FAKE](https://fake.build/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span></span> <span data-ttu-id="f3e1f-119">假和 Paket 是其他 F # 的工具，可分別用來建立專案和管理相依性。</span><span class="sxs-lookup"><span data-stu-id="f3e1f-119">FAKE and Paket are additional F# community tools for building projects and managing dependencies, respectively.</span></span>

## <a name="install-f-with-visual-studio-for-mac"></a><span data-ttu-id="f3e1f-120">使用 Visual Studio for Mac 安裝 F #</span><span class="sxs-lookup"><span data-stu-id="f3e1f-120">Install F# with Visual Studio for Mac</span></span>

<span data-ttu-id="f3e1f-121">依預設，F # 會安裝在 [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)中，不論您選擇哪一種設定。</span><span class="sxs-lookup"><span data-stu-id="f3e1f-121">F# is installed by default in [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), no matter which configuration you choose.</span></span>

<span data-ttu-id="f3e1f-122">安裝完成之後，請選擇 [ **開始 Visual Studio**]。</span><span class="sxs-lookup"><span data-stu-id="f3e1f-122">After the install completes, choose **Start Visual Studio**.</span></span> <span data-ttu-id="f3e1f-123">您也可以透過 macOS 上的搜尋工具開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="f3e1f-123">You can also open Visual Studio through Finder on macOS.</span></span>

## <a name="install-f-on-a-build-server"></a><span data-ttu-id="f3e1f-124">在組建伺服器上安裝 F #</span><span class="sxs-lookup"><span data-stu-id="f3e1f-124">Install F# on a build server</span></span>

<span data-ttu-id="f3e1f-125">如果您是透過 .NET SDK 使用 .NET Core 或 .NET Framework，則只需要在您的組建伺服器上安裝 .NET SDK。</span><span class="sxs-lookup"><span data-stu-id="f3e1f-125">If you're using .NET Core or .NET Framework via the .NET SDK, you simply need to install the .NET SDK on your build server.</span></span> <span data-ttu-id="f3e1f-126">它具有您所需的一切。</span><span class="sxs-lookup"><span data-stu-id="f3e1f-126">It has everything you need.</span></span>

<span data-ttu-id="f3e1f-127">如果您使用 .NET Framework 而 **不** 是使用 .net SDK，則您必須在 Windows Server 上安裝 [Visual Studio Build Tools SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) 。</span><span class="sxs-lookup"><span data-stu-id="f3e1f-127">If you're using .NET Framework and you are **not** using the .NET SDK, then you'll need to install the [Visual Studio Build Tools SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) onto your Windows Server.</span></span> <span data-ttu-id="f3e1f-128">在安裝程式中，選取 [ **.net 桌面 build tools**]，然後選取安裝程式功能表右邊的 **F # 編譯器** 元件。</span><span class="sxs-lookup"><span data-stu-id="f3e1f-128">In the installer, select **.NET desktop build tools**, and then select the **F# compiler** component on the right-hand side of the installer menu.</span></span>
