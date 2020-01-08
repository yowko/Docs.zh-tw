---
title: 支援 .NET 應用程式部署的 Firefox 附加元件
ms.date: 03/30/2017
helpviewer_keywords:
- Firefox add-ons for .NET application deployment
- WPF plug-in for Firefox
- .NET application deployment [WPF], deploying with Firefox add-ons
- .NET Framework Assistant for Firefox
ms.assetid: 2403403b-9b14-48e9-b70d-fa288a3c9081
ms.openlocfilehash: 687f61bd3ec7d10c6aa66c20cd5eb58fcc56f18a
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636363"
---
# <a name="firefox-add-ons-to-support-net-application-deployment"></a><span data-ttu-id="62551-102">支援 .NET 應用程式部署的 Firefox 附加元件</span><span class="sxs-lookup"><span data-stu-id="62551-102">Firefox Add-ons to Support .NET Application Deployment</span></span>
<span data-ttu-id="62551-103">適用于 Firefox 的 Windows Presentation Foundation （WPF）外掛程式和 Firefox 的 .NET Framework 小幫手可讓 XAML 瀏覽器應用程式（Xbap）、鬆散 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]和 ClickOnce 應用程式與 Mozilla Firefox 瀏覽器搭配使用。</span><span class="sxs-lookup"><span data-stu-id="62551-103">The Windows Presentation Foundation (WPF) plug-in for Firefox and the .NET Framework Assistant for Firefox enable XAML browser applications (XBAPs), loose [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], and ClickOnce applications to work with the Mozilla Firefox browser.</span></span>  
  
## <a name="wpf-plug-in-for-firefox"></a><span data-ttu-id="62551-104">適用于 Firefox 的 WPF 外掛程式</span><span class="sxs-lookup"><span data-stu-id="62551-104">WPF Plug-in for Firefox</span></span>  
 <span data-ttu-id="62551-105">適用于 Firefox 的 WPF 外掛程式可讓 Xbap 和鬆散 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案導覽至頂層，或在 Firefox 瀏覽器的 HTML IFRAME 中執行。</span><span class="sxs-lookup"><span data-stu-id="62551-105">The WPF plug-in for Firefox enables XBAPs and loose [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files to be navigated to and run at the top-level or in an HTML IFRAME in the Firefox browser.</span></span> <span data-ttu-id="62551-106">XBAP 是 WPF 應用程式，可以發行至 Web 服務器並在支援的瀏覽器中啟動。</span><span class="sxs-lookup"><span data-stu-id="62551-106">An XBAP is a WPF application that can be published to a Web server and launched within supported browsers.</span></span> <span data-ttu-id="62551-107">鬆散 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 是僅限 XAML 的檔案，可在支援的瀏覽器中導覽和顯示，與 XML 檔案非常類似。</span><span class="sxs-lookup"><span data-stu-id="62551-107">Loose [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] is a XAML-only file that can be navigated to and displayed in supported browsers, much like an XML file.</span></span>  
  
 <span data-ttu-id="62551-108">Firefox 的 WPF 外掛程式會與 .NET Framework 3.5 一起安裝。</span><span class="sxs-lookup"><span data-stu-id="62551-108">The WPF plug-in for Firefox is installed with the .NET Framework 3.5.</span></span> <span data-ttu-id="62551-109">Window 7 包含 .NET Framework 3.5，但不包含 Firefox 的 WPF 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="62551-109">Window 7 includes the .NET Framework 3.5, but does not include the WPF plug-in for Firefox.</span></span> <span data-ttu-id="62551-110">您無法在 Windows 7 上安裝 Firefox 的 WPF 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="62551-110">You cannot install the WPF plug-in for Firefox on Windows 7.</span></span>  
  
 <span data-ttu-id="62551-111">.NET Framework 4 不包含 Firefox 的 WPF 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="62551-111">The .NET Framework 4 does not include the WPF plug-in for Firefox.</span></span> <span data-ttu-id="62551-112">不過，如果已安裝 .NET Framework 3.5 和 .NET Framework 4，Firefox 的 WPF 外掛程式會與 .NET Framework 3.5 一起安裝。</span><span class="sxs-lookup"><span data-stu-id="62551-112">However, if both the .NET Framework 3.5 and .NET Framework 4 are installed, the WPF plug-in for Firefox is installed with the .NET Framework 3.5.</span></span> <span data-ttu-id="62551-113">因此 .NET Framework 4 應用程式仍會執行，因為 WPF 主機會載入正確的架構版本。</span><span class="sxs-lookup"><span data-stu-id="62551-113">Therefore .NET Framework 4 applications will still run because the WPF Host will load the correct version of the framework.</span></span> <span data-ttu-id="62551-114">如需詳細資訊，請參閱[WPF Host （presentationhost.exe .exe）](wpf-host-presentationhost-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="62551-114">For more information, see [WPF Host (PresentationHost.exe)](wpf-host-presentationhost-exe.md).</span></span>  
  
## <a name="net-framework-assistant-for-firefox"></a><span data-ttu-id="62551-115">.NET Framework Assistant for Firefox</span><span class="sxs-lookup"><span data-stu-id="62551-115">.NET Framework Assistant for Firefox</span></span>  
 <span data-ttu-id="62551-116">Firefox 的 [.NET Framework 助理] 可讓獨立 ClickOnce 應用程式從 Firefox 瀏覽器執行。</span><span class="sxs-lookup"><span data-stu-id="62551-116">The .NET Framework Assistant for Firefox enables stand-alone ClickOnce applications to run from the Firefox browser.</span></span> <span data-ttu-id="62551-117">Firefox 的 .NET Framework 助理在 Firefox 瀏覽器之前和之後安裝時，會有相同的功能。</span><span class="sxs-lookup"><span data-stu-id="62551-117">The .NET Framework Assistant for Firefox functions identically when it is installed before and after the Firefox browser.</span></span> <span data-ttu-id="62551-118">當 Firefox 瀏覽器啟動且安裝了 .NET Framework 3.5 SP1 時，Firefox 會尋找並安裝 Firefox 的 .NET Framework 助理。</span><span class="sxs-lookup"><span data-stu-id="62551-118">When the Firefox browser is launched and the .NET Framework 3.5 SP1 is installed, Firefox finds and installs the .NET Framework Assistant for Firefox.</span></span> <span data-ttu-id="62551-119">使用者可以設定 Firefox 的 [.NET Framework 助理] 來執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="62551-119">Users can configure the .NET Framework Assistant for Firefox to do the following:</span></span>  
  
- <span data-ttu-id="62551-120">在執行 ClickOnce 應用程式之前提示。</span><span class="sxs-lookup"><span data-stu-id="62551-120">Prompt before running the ClickOnce application.</span></span>  
  
- <span data-ttu-id="62551-121">報告所有已安裝的 .NET Framework 版本或僅限最新版本。</span><span class="sxs-lookup"><span data-stu-id="62551-121">Report all installed versions of the .NET Framework or just the latest version.</span></span>  
  
 <span data-ttu-id="62551-122">適用于 Firefox 的 [.NET Framework 助理] 隨附于 .NET Framework 3.5 SP1。</span><span class="sxs-lookup"><span data-stu-id="62551-122">The .NET Framework Assistant for Firefox is included with the .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="62551-123">如需移除 Firefox 的 [.NET Framework 助理] 的相關資訊，請參閱[如何移除 firefox 的 .NET Framework 助理](https://go.microsoft.com/fwlink/?LinkId=177944)。</span><span class="sxs-lookup"><span data-stu-id="62551-123">For information about removing the .NET Framework Assistant for Firefox, see [How to remove the .NET Framework Assistant for Firefox](https://go.microsoft.com/fwlink/?LinkId=177944).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62551-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="62551-124">See also</span></span>

- [<span data-ttu-id="62551-125">部署 WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="62551-125">Deploying a WPF Application</span></span>](deploying-a-wpf-application-wpf.md)
- [<span data-ttu-id="62551-126">WPF XAML 瀏覽器應用程式概觀</span><span class="sxs-lookup"><span data-stu-id="62551-126">WPF XAML Browser Applications Overview</span></span>](wpf-xaml-browser-applications-overview.md)
- [<span data-ttu-id="62551-127">偵測有無安裝 Firefox 的 WPF 外掛程式</span><span class="sxs-lookup"><span data-stu-id="62551-127">Detect Whether the WPF Plug-In for Firefox Is Installed</span></span>](how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed.md)
