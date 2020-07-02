---
title: .NET Framework 和頻外發行
description: 瞭解 .NET 和頻外發行。 新功能會以頻外（OOB）發行，以改善跨平臺開發或引進新功能。
ms.date: 10/10/2018
ms.assetid: 721f10fa-3189-4124-a00d-56ddabd889b3
ms.openlocfilehash: 9653696f46279e0c23418f92030d64839cc20518
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618762"
---
# <a name="net-framework-and-out-of-band-releases"></a><span data-ttu-id="ad461-104">.NET Framework 與不定期發行</span><span class="sxs-lookup"><span data-stu-id="ad461-104">.NET Framework and out-of-band releases</span></span>

<span data-ttu-id="ad461-105">.NET Framework 已演進以配合不同的平臺（例如 UWP 應用程式和傳統桌面和 web 應用程式），並可讓程式碼重複使用。</span><span class="sxs-lookup"><span data-stu-id="ad461-105">.NET Framework has evolved to accommodate different platforms, such as UWP apps and traditional desktop and web apps, and to maximize code reuse.</span></span> <span data-ttu-id="ad461-106">除了一般 .NET Framework 版本外，新功能會以頻外（OOB）發行，以改善跨平臺開發或引進新功能。</span><span class="sxs-lookup"><span data-stu-id="ad461-106">In addition to regular .NET Framework releases, new features are released out of band (OOB) to improve cross-platform development or to introduce new functionality.</span></span>

## <a name="advantages-of-oob-releases"></a><span data-ttu-id="ad461-107">OOB 版本的優點</span><span class="sxs-lookup"><span data-stu-id="ad461-107">Advantages of OOB releases</span></span>

<span data-ttu-id="ad461-108">將新元件或元件的更新傳送至頻外，可讓 Microsoft 為 .NET Framework 提供更頻繁的更新。</span><span class="sxs-lookup"><span data-stu-id="ad461-108">Shipping new components or updates to components out of band enables Microsoft to provide more frequent updates to .NET Framework.</span></span> <span data-ttu-id="ad461-109">此外，我們還能更迅速地彙總和回應客戶意見。</span><span class="sxs-lookup"><span data-stu-id="ad461-109">In addition, we can gather and respond to customer feedback more quickly.</span></span>

<span data-ttu-id="ad461-110">當您在應用程式中使用 OOB 功能時，您的使用者不需要安裝最新版本的 .NET Framework 來執行您的應用程式，因為 OOB 元件會隨您的應用程式套件一起部署。</span><span class="sxs-lookup"><span data-stu-id="ad461-110">When you use an OOB feature in your app, your users do not have to install the latest version of .NET Framework to run your app, because the OOB assemblies deploy with your app package.</span></span>

## <a name="how-oob-packages-are-distributed"></a><span data-ttu-id="ad461-111">OOB 套件散發的方式</span><span class="sxs-lookup"><span data-stu-id="ad461-111">How OOB packages are distributed</span></span>

<span data-ttu-id="ad461-112">核心通用語言執行平臺（CLR）元件的 OOB 版本是透過[NuGet](https://www.nuget.org/)傳遞，這是 .net 的套件管理員。</span><span class="sxs-lookup"><span data-stu-id="ad461-112">OOB releases for core common language runtime (CLR) components are delivered through [NuGet](https://www.nuget.org/), which is the package manager for .NET.</span></span> <span data-ttu-id="ad461-113">NuGet 可讓您從 Visual Studio 內輕鬆流覽並將程式庫新增至您的 .NET Framework 專案。</span><span class="sxs-lookup"><span data-stu-id="ad461-113">NuGet enables you to browse and add libraries to your .NET Framework projects easily from within Visual Studio.</span></span> <span data-ttu-id="ad461-114">從 Visual Studio 2012 開始，NuGet 套件管理員隨附于所有版本的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="ad461-114">NuGet Package Manager is included with all editions of Visual Studio starting with Visual Studio 2012.</span></span> <span data-ttu-id="ad461-115">在 Visual Studio 的 [**工具**] 功能表上尋找 [ **NuGet 套件管理員**]。</span><span class="sxs-lookup"><span data-stu-id="ad461-115">Look for **NuGet Package Manager** on the **Tools** menu in Visual Studio.</span></span> <span data-ttu-id="ad461-116">如果未安裝，請依照[安裝 NuGet](/nuget/install-nuget-client-tools)上的指示進行。</span><span class="sxs-lookup"><span data-stu-id="ad461-116">If it's not installed, follow the instructions on [Installing NuGet](/nuget/install-nuget-client-tools).</span></span> <span data-ttu-id="ad461-117">如需 NuGet 的詳細資訊，請參閱[nuget](/nuget)檔。</span><span class="sxs-lookup"><span data-stu-id="ad461-117">For more information about NuGet, see the [NuGet docs](/nuget).</span></span>

## <a name="use-a-nuget-oob-package"></a><span data-ttu-id="ad461-118">使用 NuGet OOB 套件</span><span class="sxs-lookup"><span data-stu-id="ad461-118">Use a NuGet OOB package</span></span>

<span data-ttu-id="ad461-119">如果已安裝 NuGet 套件管理員，您可以使用 Visual Studio 中的方案總管，流覽並新增 NuGet 套件的參考：</span><span class="sxs-lookup"><span data-stu-id="ad461-119">If NuGet Package Manager is installed, you can browse and add references to NuGet packages by using Solution Explorer in Visual Studio:</span></span>

1. <span data-ttu-id="ad461-120">開啟 Visual Studio 中專案的捷徑功能表，然後選擇 [管理 NuGet 套件]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ad461-120">Open the shortcut menu for your project in Visual Studio, and then choose **Manage NuGet Packages**.</span></span> <span data-ttu-id="ad461-121">(這個選項也可以在 [專案]\*\*\*\* 功能表中取得)。</span><span class="sxs-lookup"><span data-stu-id="ad461-121">(This option is also available from the **Project** menu.)</span></span>

2. <span data-ttu-id="ad461-122">在左窗格中，選擇 [連線]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ad461-122">In the left pane, choose **Online**.</span></span>

3. <span data-ttu-id="ad461-123">如果您想要使用發行前套件，請在中間窗格的下拉式清單方塊中，選擇 [包含發行前版本]\*\*\*\*，而不要選擇 [僅限穩定版本]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ad461-123">If you want to use prerelease packages, in the drop-down list box in the middle pane, choose **Include Prerelease** instead of **Stable Only**.</span></span>

4. <span data-ttu-id="ad461-124">在右窗格中，使用 [搜尋]\*\*\*\* 方塊尋找您要使用的套件。</span><span class="sxs-lookup"><span data-stu-id="ad461-124">In the right pane, use the **Search** box to locate the package you would like to use.</span></span> <span data-ttu-id="ad461-125">某些 Microsoft 套件已獲得 Microsoft .NET Framework 標誌識別，而且所有套件都會將 Microsoft 識別為發行者。</span><span class="sxs-lookup"><span data-stu-id="ad461-125">Some Microsoft packages are identified by the Microsoft .NET Framework logo, and all identify Microsoft as the publisher.</span></span>

![NuGet 套件管理員。](./media/the-net-framework-and-out-of-band-releases/nuget-package-manager-dialog.png)

<span data-ttu-id="ad461-127">如前面所述，當您部署使用 OOB 套件的應用程式時，OOB 組件會隨附於應用程式套件。</span><span class="sxs-lookup"><span data-stu-id="ad461-127">As mentioned previously, when you deploy an app that uses an OOB package, the OOB assemblies will ship with your app package.</span></span>

## <a name="types-of-oob-releases"></a><span data-ttu-id="ad461-128">OOB 版本的類型</span><span class="sxs-lookup"><span data-stu-id="ad461-128">Types of OOB releases</span></span>

<span data-ttu-id="ad461-129">通常，OOB 套件會有一個或多個發行前版本和一個穩定版本。</span><span class="sxs-lookup"><span data-stu-id="ad461-129">Typically, an OOB package has one or more prerelease versions and a stable version.</span></span> <span data-ttu-id="ad461-130">發行前版本隨附的授權通常不允許轉散發，但是可讓您試用套件並提供意見。</span><span class="sxs-lookup"><span data-stu-id="ad461-130">The license that accompanies a prerelease doesn't typically allow redistribution, but enables you to try out a package and provide feedback.</span></span> <span data-ttu-id="ad461-131">意見會納入對套件的任何更新中。</span><span class="sxs-lookup"><span data-stu-id="ad461-131">Feedback is incorporated in any updates made to the package.</span></span> <span data-ttu-id="ad461-132">最終版本會做為穩定套件隨 NuGet 一起散發，並且包含可讓您隨應用程式轉散發 NuGet 套件的授權。</span><span class="sxs-lookup"><span data-stu-id="ad461-132">A final release is distributed as a stable package with NuGet and includes a license that lets you redistribute the NuGet package with your app.</span></span> <span data-ttu-id="ad461-133">Microsoft 支援穩定套件。</span><span class="sxs-lookup"><span data-stu-id="ad461-133">Stable packages are supported by Microsoft.</span></span> <span data-ttu-id="ad461-134">Microsoft 會為所有套件提供 IntelliSense 支援，以及其他類型的文件 (例如，部落格文章和論壇解答)。</span><span class="sxs-lookup"><span data-stu-id="ad461-134">Microsoft provides IntelliSense support as well as other types of documentation such as blog posts and forum answers for all packages.</span></span> <span data-ttu-id="ad461-135">此外，部分 (但不是所有) 套件可能會隨附原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="ad461-135">In addition, source code may be available with some, but not all, packages.</span></span> <span data-ttu-id="ad461-136">如需有關新套件和更新套件的公告，您可以訂閱 [.NET Framework 部落格](https://devblogs.microsoft.com/dotnet/)。</span><span class="sxs-lookup"><span data-stu-id="ad461-136">For announcements regarding new and updated packages, you can subscribe to [the .NET Framework Blog](https://devblogs.microsoft.com/dotnet/).</span></span>

<span data-ttu-id="ad461-137">若要尋找發行前版本和穩定套件，請在 NuGet 套件管理員中選擇 [**包含發行**前版本]。</span><span class="sxs-lookup"><span data-stu-id="ad461-137">To find both prerelease and stable packages, choose **Include Prerelease** in NuGet Package Manager.</span></span>

## <a name="see-also"></a><span data-ttu-id="ad461-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad461-138">See also</span></span>

- [<span data-ttu-id="ad461-139">快速入門</span><span class="sxs-lookup"><span data-stu-id="ad461-139">Getting started</span></span>](index.md)
