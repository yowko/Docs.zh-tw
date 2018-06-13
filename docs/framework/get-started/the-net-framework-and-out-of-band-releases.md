---
title: .NET Framework 和 Out-of-Band 發行版本
ms.date: 03/30/2017
ms.assetid: 721f10fa-3189-4124-a00d-56ddabd889b3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6c0ea6590a53748c9ed85a6d13f67b260ce23af5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33390282"
---
# <a name="the-net-framework-and-out-of-band-releases"></a><span data-ttu-id="d5d34-102">.NET Framework 和 Out-of-Band 發行版本</span><span class="sxs-lookup"><span data-stu-id="d5d34-102">The .NET Framework and Out-of-Band Releases</span></span>
<span data-ttu-id="d5d34-103">.NET Framework 持續朝向容納不同平台 (例如 Windows Phone 和 Windows 市集應用程式以及傳統桌面和 Web 應用程式)，以及獲得最大程式碼重複使用率而不斷進化。</span><span class="sxs-lookup"><span data-stu-id="d5d34-103">The .NET Framework is evolving to accommodate different platforms such as Windows Phone and Windows Store apps as well as traditional desktop and web apps, and to maximize code reuse.</span></span> <span data-ttu-id="d5d34-104">除了定期發行的 .NET Framework 版本之外，我們還會發行非常態 (Out-of-Band，OOB) 新功能，藉此改善跨平台開發工作或引入新功能。</span><span class="sxs-lookup"><span data-stu-id="d5d34-104">In addition to our regular .NET Framework releases, we release new features out of band (OOB) to improve cross-platform development or to introduce new functionality.</span></span> <span data-ttu-id="d5d34-105">本主題將討論 .NET Framework 及其 OOB 版本的未來方向。</span><span class="sxs-lookup"><span data-stu-id="d5d34-105">This topic discusses the future direction of the .NET Framework and its OOB releases.</span></span>  
  
## <a name="advantages-of-oob-releases"></a><span data-ttu-id="d5d34-106">OOB 版本的優點</span><span class="sxs-lookup"><span data-stu-id="d5d34-106">Advantages of OOB releases</span></span>  
 <span data-ttu-id="d5d34-107">以非常態 (OOB) 的方式推出新元件或更新，能夠讓 Microsoft 為 .NET Framework 提供更頻繁的更新。</span><span class="sxs-lookup"><span data-stu-id="d5d34-107">Shipping new components or updates to components out of band enables Microsoft to provide more frequent updates to the .NET Framework.</span></span> <span data-ttu-id="d5d34-108">此外，我們還能更迅速地彙總和回應客戶意見。</span><span class="sxs-lookup"><span data-stu-id="d5d34-108">In addition, we can gather and respond to customer feedback more quickly.</span></span>  
  
 <span data-ttu-id="d5d34-109">當您在應用程式中使用 OOB 功能時，使用者不需要安裝最新版的 .NET Framework 就能執行您的應用程式，因為 OOB 組件會隨您的應用程式套件一併部署。</span><span class="sxs-lookup"><span data-stu-id="d5d34-109">When you use an OOB feature in your app, your users do not have to install the latest version of the .NET Framework to run your app, because the OOB assemblies deploy with your app package.</span></span>  
  
## <a name="how-oob-packages-are-distributed"></a><span data-ttu-id="d5d34-110">OOB 套件散發的方式</span><span class="sxs-lookup"><span data-stu-id="d5d34-110">How OOB packages are distributed</span></span>  
<span data-ttu-id="d5d34-111">核心通用語言執行平台 (CLR) 元件的 OOB 版本是透過 [NuGet](https://www.nuget.org/) 所提供，這是 .NET 的套件管理員。</span><span class="sxs-lookup"><span data-stu-id="d5d34-111">OOB releases for core common language runtime (CLR) components are delivered through the [NuGet](https://www.nuget.org/), which is a package manager for .NET.</span></span> <span data-ttu-id="d5d34-112">NuGet 可讓您從 Visual Studio 的 [方案總管] 中，輕鬆地瀏覽程式庫並加入至 .NET Framework 專案。</span><span class="sxs-lookup"><span data-stu-id="d5d34-112">NuGet enables you to browse and add libraries to your .NET Framework projects easily from the Solution Explorer in Visual Studio.</span></span> <span data-ttu-id="d5d34-113">從 Visual Studio 2012 開始，NuGet 隨附於所有 Visual Studio 版本。</span><span class="sxs-lookup"><span data-stu-id="d5d34-113">NuGet is included with all editions of Visual Studio starting with Visual Studio 2012.</span></span> <span data-ttu-id="d5d34-114">若要查看是否已安裝 NuGet，請在 Visual Studio 的 [工具] 功能表上尋找 [程式庫套件管理員]。</span><span class="sxs-lookup"><span data-stu-id="d5d34-114">To see if NuGet is installed, look for **Library Package Manager** on the Visual Studio **Tools** menu.</span></span> <span data-ttu-id="d5d34-115">如果尚未安裝：</span><span class="sxs-lookup"><span data-stu-id="d5d34-115">If it’s not installed:</span></span>  
  
1.  <span data-ttu-id="d5d34-116">在 Visual Studio 功能表列上，選擇 [工具]、[擴充功能和更新] (在 Visual Studio 2010 中請選擇 [擴充管理員])。</span><span class="sxs-lookup"><span data-stu-id="d5d34-116">On the Visual Studio menu bar, choose **Tools**, **Extensions and Updates** (in Visual Studio 2010, choose **Extension Manager**).</span></span>  
  
     <span data-ttu-id="d5d34-117">[擴充功能和更新] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="d5d34-117">The **Extensions and Updates** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="d5d34-118">選擇 [連線]、[NuGet 套件管理員]，然後選擇 [下載]。</span><span class="sxs-lookup"><span data-stu-id="d5d34-118">Choose **Online**, **NuGet Package Manager**, and then choose **Download**.</span></span>  
  
3.  <span data-ttu-id="d5d34-119">下載完成後，請重新啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="d5d34-119">After the download completes, restart Visual Studio.</span></span>  
  
 <span data-ttu-id="d5d34-120">如需詳細的安裝指示，請參閱 NuGet 文件網站上的[安裝 NuGet](http://docs.nuget.org/docs/start-here/installing-nuget) (英文)。</span><span class="sxs-lookup"><span data-stu-id="d5d34-120">For detailed installation instructions, see [Installing NuGet](http://docs.nuget.org/docs/start-here/installing-nuget) on the NuGet Docs website.</span></span> <span data-ttu-id="d5d34-121">如需 NuGet 的詳細資訊，請參閱 [NuGet 文件](http://docs.nuget.org/) (英文)。</span><span class="sxs-lookup"><span data-stu-id="d5d34-121">For more information about NuGet, see the [NuGet documentation](http://docs.nuget.org/).</span></span>  
  
## <a name="using-a-nuget-oob-package"></a><span data-ttu-id="d5d34-122">使用 NuGet OOB 套件</span><span class="sxs-lookup"><span data-stu-id="d5d34-122">Using a NuGet OOB package</span></span>  
 <span data-ttu-id="d5d34-123">安裝 NuGet 之後，您可以使用 Visual Studio 中的 [方案總管]，瀏覽並加入 NuGet 套件的參考：</span><span class="sxs-lookup"><span data-stu-id="d5d34-123">After you install NuGet, you can browse and add references to NuGet packages by using Solution Explorer in Visual Studio:</span></span>  
  
1.  <span data-ttu-id="d5d34-124">開啟 Visual Studio 中專案的捷徑功能表，然後選擇 [管理 NuGet 套件]。</span><span class="sxs-lookup"><span data-stu-id="d5d34-124">Open the shortcut menu for your project in Visual Studio, and then choose **Manage NuGet Packages**.</span></span> <span data-ttu-id="d5d34-125">(這個選項也可以在 [專案] 功能表中取得)。</span><span class="sxs-lookup"><span data-stu-id="d5d34-125">(This option is also available from the **Project** menu.)</span></span>  
  
2.  <span data-ttu-id="d5d34-126">在左窗格中，選擇 [連線]。</span><span class="sxs-lookup"><span data-stu-id="d5d34-126">In the left pane, choose **Online**.</span></span>  
  
3.  <span data-ttu-id="d5d34-127">如果您想要使用發行前套件，請在中間窗格的下拉式清單方塊中，選擇 [包含發行前版本]，而不要選擇 [僅限穩定版本]。</span><span class="sxs-lookup"><span data-stu-id="d5d34-127">If you want to use prerelease packages, in the drop-down list box in the middle pane, choose **Include Prerelease** instead of **Stable Only**.</span></span>  
  
4.  <span data-ttu-id="d5d34-128">在右窗格中，使用 [搜尋] 方塊尋找您要使用的套件。</span><span class="sxs-lookup"><span data-stu-id="d5d34-128">In the right pane, use the **Search** box to locate the package you would like to use.</span></span> <span data-ttu-id="d5d34-129">某些 Microsoft 套件已獲得 Microsoft .NET Framework 標誌識別，而且所有套件都會將 Microsoft 識別為發行者。</span><span class="sxs-lookup"><span data-stu-id="d5d34-129">Some Microsoft packages are identified by the Microsoft .NET Framework logo, and all identify Microsoft as the publisher.</span></span>  
  
 <span data-ttu-id="d5d34-130">![NuGet 封裝管理員](../../../docs/framework/get-started/media/clrnugetdialog.png "clrNugetDialog")</span><span class="sxs-lookup"><span data-stu-id="d5d34-130">![NuGet Package Manager](../../../docs/framework/get-started/media/clrnugetdialog.png "clrNugetDialog")</span></span>  
  
 <span data-ttu-id="d5d34-131">如前面所述，當您部署使用 OOB 套件的應用程式時，OOB 組件會隨附於應用程式套件。</span><span class="sxs-lookup"><span data-stu-id="d5d34-131">As mentioned previously, when you deploy an app that uses an OOB package, the OOB assemblies will ship with your app package.</span></span>  
  
## <a name="types-of-oob-releases"></a><span data-ttu-id="d5d34-132">OOB 版本的類型</span><span class="sxs-lookup"><span data-stu-id="d5d34-132">Types of OOB releases</span></span>  
 <span data-ttu-id="d5d34-133">通常，OOB 套件會有一個或多個發行前版本和一個穩定版本。</span><span class="sxs-lookup"><span data-stu-id="d5d34-133">Typically, an OOB package has one or more prerelease versions and a stable version.</span></span> <span data-ttu-id="d5d34-134">發行前版本隨附的授權通常不允許轉散發，但是可讓您試用套件並提供意見。</span><span class="sxs-lookup"><span data-stu-id="d5d34-134">The license that accompanies a prerelease doesn't typically allow redistribution, but enables you to try out a package and provide feedback.</span></span> <span data-ttu-id="d5d34-135">意見會納入對套件的任何更新中。</span><span class="sxs-lookup"><span data-stu-id="d5d34-135">Feedback is incorporated in any updates made to the package.</span></span> <span data-ttu-id="d5d34-136">最終版本會做為穩定套件隨 NuGet 一起散發，並且包含可讓您隨應用程式轉散發 NuGet 套件的授權。</span><span class="sxs-lookup"><span data-stu-id="d5d34-136">A final release is distributed as a stable package with NuGet and includes a license that lets you redistribute the NuGet package with your app.</span></span> <span data-ttu-id="d5d34-137">Microsoft 支援穩定套件。</span><span class="sxs-lookup"><span data-stu-id="d5d34-137">Stable packages are supported by Microsoft.</span></span> <span data-ttu-id="d5d34-138">Microsoft 會為所有套件提供 IntelliSense 支援，以及其他類型的文件 (例如，部落格文章和論壇解答)。</span><span class="sxs-lookup"><span data-stu-id="d5d34-138">Microsoft provides IntelliSense support as well as other types of documentation such as blog posts and forum answers for all packages.</span></span> <span data-ttu-id="d5d34-139">此外，部分 (但不是所有) 套件可能會隨附原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="d5d34-139">In addition, source code may be available with some, but not all, packages.</span></span> <span data-ttu-id="d5d34-140">如需有關新套件和更新套件的公告，您可以訂閱 [.NET Framework 部落格](http://blogs.msdn.com/b/dotnet/)。</span><span class="sxs-lookup"><span data-stu-id="d5d34-140">For announcements regarding new and updated packages, you can subscribe to [the .NET Framework Blog](http://blogs.msdn.com/b/dotnet/).</span></span>  
  
 <span data-ttu-id="d5d34-141">若要尋找發行前版本和穩定套件，請在 NuGet 套件管理員中選擇 [包含發行前版本]。</span><span class="sxs-lookup"><span data-stu-id="d5d34-141">To find both prerelease and stable packages, choose **Include Prerelease** in the NuGet Package Manager.</span></span>  
  
 <span data-ttu-id="d5d34-142">如果您想要收到穩定套件的發行通知，請訂閱 [.NET Framework 摘要](https://nuget.org/api/v2/curated-feeds/dotnetframework/Packages/)。</span><span class="sxs-lookup"><span data-stu-id="d5d34-142">If you want to be notified of stable package releases, subscribe to [the .NET Framework feed](https://nuget.org/api/v2/curated-feeds/dotnetframework/Packages/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5d34-143">請參閱</span><span class="sxs-lookup"><span data-stu-id="d5d34-143">See Also</span></span>  
 [<span data-ttu-id="d5d34-144">快速入門</span><span class="sxs-lookup"><span data-stu-id="d5d34-144">Getting Started</span></span>](../../../docs/framework/get-started/index.md)
