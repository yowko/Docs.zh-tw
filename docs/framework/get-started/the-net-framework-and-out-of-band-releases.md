---
title: .NET 框架和帶外版本
ms.date: 10/10/2018
ms.assetid: 721f10fa-3189-4124-a00d-56ddabd889b3
ms.openlocfilehash: 058bc1a5180060d3c3c6ba4ead1f074a14336b53
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181570"
---
# <a name="net-framework-and-out-of-band-releases"></a><span data-ttu-id="6356e-102">.NET 框架和帶外版本</span><span class="sxs-lookup"><span data-stu-id="6356e-102">.NET Framework and out-of-band releases</span></span>

<span data-ttu-id="6356e-103">.NET Framework 已發展為適應不同的平臺，如 UWP 應用和傳統桌面和 Web 應用，並最大限度地提高代碼重用。</span><span class="sxs-lookup"><span data-stu-id="6356e-103">.NET Framework has evolved to accommodate different platforms, such as UWP apps and traditional desktop and web apps, and to maximize code reuse.</span></span> <span data-ttu-id="6356e-104">除了常規的 .NET 框架版本外，新功能還從頻段 （OOB） 外發佈，以改進跨平臺開發或引入新功能。</span><span class="sxs-lookup"><span data-stu-id="6356e-104">In addition to regular .NET Framework releases, new features are released out of band (OOB) to improve cross-platform development or to introduce new functionality.</span></span>

## <a name="advantages-of-oob-releases"></a><span data-ttu-id="6356e-105">OOB 版本的優點</span><span class="sxs-lookup"><span data-stu-id="6356e-105">Advantages of OOB releases</span></span>

<span data-ttu-id="6356e-106">將新元件或更新傳送到帶外元件使 Microsoft 能夠更頻繁地向 .NET Framework 提供更新。</span><span class="sxs-lookup"><span data-stu-id="6356e-106">Shipping new components or updates to components out of band enables Microsoft to provide more frequent updates to .NET Framework.</span></span> <span data-ttu-id="6356e-107">此外，我們還能更迅速地彙總和回應客戶意見。</span><span class="sxs-lookup"><span data-stu-id="6356e-107">In addition, we can gather and respond to customer feedback more quickly.</span></span>

<span data-ttu-id="6356e-108">在應用中使用 OOB 功能時，使用者不必安裝最新版本的 .NET Framework 來運行應用，因為 OOB 程式集隨應用包一起部署。</span><span class="sxs-lookup"><span data-stu-id="6356e-108">When you use an OOB feature in your app, your users do not have to install the latest version of .NET Framework to run your app, because the OOB assemblies deploy with your app package.</span></span>

## <a name="how-oob-packages-are-distributed"></a><span data-ttu-id="6356e-109">OOB 套件散發的方式</span><span class="sxs-lookup"><span data-stu-id="6356e-109">How OOB packages are distributed</span></span>

<span data-ttu-id="6356e-110">核心通用語言運行時 （CLR） 元件的 OOB 版本通過[NuGet（](https://www.nuget.org/)是 .NET 的包管理器）提供。</span><span class="sxs-lookup"><span data-stu-id="6356e-110">OOB releases for core common language runtime (CLR) components are delivered through [NuGet](https://www.nuget.org/), which is the package manager for .NET.</span></span> <span data-ttu-id="6356e-111">NuGet 使您能夠從 Visual Studio 中輕鬆流覽 .NET 框架專案並將庫添加到專案中。</span><span class="sxs-lookup"><span data-stu-id="6356e-111">NuGet enables you to browse and add libraries to your .NET Framework projects easily from within Visual Studio.</span></span> <span data-ttu-id="6356e-112">從 Visual Studio 2012 開始，所有版本的 Visual Studio 都包含 NuGet 套裝軟體管理器。</span><span class="sxs-lookup"><span data-stu-id="6356e-112">NuGet Package Manager is included with all editions of Visual Studio starting with Visual Studio 2012.</span></span> <span data-ttu-id="6356e-113">在視覺化工作室的 **"工具"** 功能表上查找**NuGet 包管理器**。</span><span class="sxs-lookup"><span data-stu-id="6356e-113">Look for **NuGet Package Manager** on the **Tools** menu in Visual Studio.</span></span> <span data-ttu-id="6356e-114">如果未安裝，請按照安裝[NuGet](/nuget/install-nuget-client-tools)的說明操作。</span><span class="sxs-lookup"><span data-stu-id="6356e-114">If it's not installed, follow the instructions on [Installing NuGet](/nuget/install-nuget-client-tools).</span></span> <span data-ttu-id="6356e-115">有關 NuGet 的詳細資訊，請參閱[NuGet 文檔](/nuget)。</span><span class="sxs-lookup"><span data-stu-id="6356e-115">For more information about NuGet, see the [NuGet docs](/nuget).</span></span>

## <a name="use-a-nuget-oob-package"></a><span data-ttu-id="6356e-116">使用 NuGet OOB 套裝軟體</span><span class="sxs-lookup"><span data-stu-id="6356e-116">Use a NuGet OOB package</span></span>

<span data-ttu-id="6356e-117">如果安裝了 NuGet 包管理器，則可以在 Visual Studio 中使用解決方案資源管理器流覽並添加對 NuGet 包的引用：</span><span class="sxs-lookup"><span data-stu-id="6356e-117">If NuGet Package Manager is installed, you can browse and add references to NuGet packages by using Solution Explorer in Visual Studio:</span></span>

1. <span data-ttu-id="6356e-118">開啟 Visual Studio 中專案的捷徑功能表，然後選擇 [管理 NuGet 套件]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6356e-118">Open the shortcut menu for your project in Visual Studio, and then choose **Manage NuGet Packages**.</span></span> <span data-ttu-id="6356e-119">(這個選項也可以在 [專案]\*\*\*\* 功能表中取得)。</span><span class="sxs-lookup"><span data-stu-id="6356e-119">(This option is also available from the **Project** menu.)</span></span>

2. <span data-ttu-id="6356e-120">在左窗格中，選擇 [連線]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6356e-120">In the left pane, choose **Online**.</span></span>

3. <span data-ttu-id="6356e-121">如果您想要使用發行前套件，請在中間窗格的下拉式清單方塊中，選擇 [包含發行前版本]\*\*\*\*，而不要選擇 [僅限穩定版本]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6356e-121">If you want to use prerelease packages, in the drop-down list box in the middle pane, choose **Include Prerelease** instead of **Stable Only**.</span></span>

4. <span data-ttu-id="6356e-122">在右窗格中，使用 [搜尋]\*\*\*\* 方塊尋找您要使用的套件。</span><span class="sxs-lookup"><span data-stu-id="6356e-122">In the right pane, use the **Search** box to locate the package you would like to use.</span></span> <span data-ttu-id="6356e-123">某些 Microsoft 套件已獲得 Microsoft .NET Framework 標誌識別，而且所有套件都會將 Microsoft 識別為發行者。</span><span class="sxs-lookup"><span data-stu-id="6356e-123">Some Microsoft packages are identified by the Microsoft .NET Framework logo, and all identify Microsoft as the publisher.</span></span>

![NuGet 包管理器。](./media/the-net-framework-and-out-of-band-releases/nuget-package-manager-dialog.png)

<span data-ttu-id="6356e-125">如前面所述，當您部署使用 OOB 套件的應用程式時，OOB 組件會隨附於應用程式套件。</span><span class="sxs-lookup"><span data-stu-id="6356e-125">As mentioned previously, when you deploy an app that uses an OOB package, the OOB assemblies will ship with your app package.</span></span>

## <a name="types-of-oob-releases"></a><span data-ttu-id="6356e-126">OOB 版本的類型</span><span class="sxs-lookup"><span data-stu-id="6356e-126">Types of OOB releases</span></span>

<span data-ttu-id="6356e-127">通常，OOB 套件會有一個或多個發行前版本和一個穩定版本。</span><span class="sxs-lookup"><span data-stu-id="6356e-127">Typically, an OOB package has one or more prerelease versions and a stable version.</span></span> <span data-ttu-id="6356e-128">發行前版本隨附的授權通常不允許轉散發，但是可讓您試用套件並提供意見。</span><span class="sxs-lookup"><span data-stu-id="6356e-128">The license that accompanies a prerelease doesn't typically allow redistribution, but enables you to try out a package and provide feedback.</span></span> <span data-ttu-id="6356e-129">意見會納入對套件的任何更新中。</span><span class="sxs-lookup"><span data-stu-id="6356e-129">Feedback is incorporated in any updates made to the package.</span></span> <span data-ttu-id="6356e-130">最終版本會做為穩定套件隨 NuGet 一起散發，並且包含可讓您隨應用程式轉散發 NuGet 套件的授權。</span><span class="sxs-lookup"><span data-stu-id="6356e-130">A final release is distributed as a stable package with NuGet and includes a license that lets you redistribute the NuGet package with your app.</span></span> <span data-ttu-id="6356e-131">Microsoft 支援穩定套件。</span><span class="sxs-lookup"><span data-stu-id="6356e-131">Stable packages are supported by Microsoft.</span></span> <span data-ttu-id="6356e-132">Microsoft 會為所有套件提供 IntelliSense 支援，以及其他類型的文件 (例如，部落格文章和論壇解答)。</span><span class="sxs-lookup"><span data-stu-id="6356e-132">Microsoft provides IntelliSense support as well as other types of documentation such as blog posts and forum answers for all packages.</span></span> <span data-ttu-id="6356e-133">此外，部分 (但不是所有) 套件可能會隨附原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="6356e-133">In addition, source code may be available with some, but not all, packages.</span></span> <span data-ttu-id="6356e-134">如需有關新套件和更新套件的公告，您可以訂閱 [.NET Framework 部落格](https://devblogs.microsoft.com/dotnet/)。</span><span class="sxs-lookup"><span data-stu-id="6356e-134">For announcements regarding new and updated packages, you can subscribe to [the .NET Framework Blog](https://devblogs.microsoft.com/dotnet/).</span></span>

<span data-ttu-id="6356e-135">要查找預發行包和穩定包，請在 NuGet 套裝軟體管理器中選擇 **"包括預發行**"。</span><span class="sxs-lookup"><span data-stu-id="6356e-135">To find both prerelease and stable packages, choose **Include Prerelease** in NuGet Package Manager.</span></span>

## <a name="see-also"></a><span data-ttu-id="6356e-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6356e-136">See also</span></span>

- [<span data-ttu-id="6356e-137">開始使用</span><span class="sxs-lookup"><span data-stu-id="6356e-137">Getting started</span></span>](index.md)
