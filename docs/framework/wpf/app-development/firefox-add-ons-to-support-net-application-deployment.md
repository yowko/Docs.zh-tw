---
title: 支援 .NET 應用程式部署的 Firefox 附加元件
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Firefox add-ons for .NET application deployment
- WPF plug-in for Firefox
- .NET application deployment [WPF], deploying with Firefox add-ons
- .NET Framework Assistant for Firefox
ms.assetid: 2403403b-9b14-48e9-b70d-fa288a3c9081
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1066332b8c5b98b5cca45e7ffbea83bd8cee8775
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="firefox-add-ons-to-support-net-application-deployment"></a><span data-ttu-id="e0dd7-102">支援 .NET 應用程式部署的 Firefox 附加元件</span><span class="sxs-lookup"><span data-stu-id="e0dd7-102">Firefox Add-ons to Support .NET Application Deployment</span></span>
<span data-ttu-id="e0dd7-103">Windows Presentation Foundation (WPF) 外掛程式 Firefox 和.NET Framework Assistant firefox 啟用[!INCLUDE[TLA#tla_winfxwebapp#plural](../../../../includes/tlasharptla-winfxwebappsharpplural-md.md)]、 鬆散[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，和 ClickOnce 應用程式 Mozilla Firefox 瀏覽器所使用。</span><span class="sxs-lookup"><span data-stu-id="e0dd7-103">The Windows Presentation Foundation (WPF) plug-in for Firefox and the .NET Framework Assistant for Firefox enable [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../../includes/tlasharptla-winfxwebappsharpplural-md.md)], loose [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], and ClickOnce applications to work with the Mozilla Firefox browser.</span></span>  
  
## <a name="wpf-plug-in-for-firefox"></a><span data-ttu-id="e0dd7-104">WPF Firefox 外掛程式</span><span class="sxs-lookup"><span data-stu-id="e0dd7-104">WPF Plug-in for Firefox</span></span>  
 <span data-ttu-id="e0dd7-105">WPF Firefox 外掛程式可讓[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]和鬆散[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案，以瀏覽至並在最上層，或在 HTML 中的 IFRAME Firefox 瀏覽器中執行。</span><span class="sxs-lookup"><span data-stu-id="e0dd7-105">The WPF plug-in for Firefox enables [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] and loose [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files to be navigated to and run at the top-level or in an HTML IFRAME in the Firefox browser.</span></span> <span data-ttu-id="e0dd7-106">[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]是[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]可以發行到 Web 伺服器和內啟動應用程式支援的瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="e0dd7-106">An [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] is a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application that can be published to a Web server and launched within supported browsers.</span></span> <span data-ttu-id="e0dd7-107">鬆散[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]是僅限 XAML 的檔案，可以瀏覽至並顯示在支援的瀏覽器，非常類似的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="e0dd7-107">Loose [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] is a XAML-only file that can be navigated to and displayed in supported browsers, much like an XML file.</span></span>  
  
 <span data-ttu-id="e0dd7-108">[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]外掛程式與安裝 Firefox [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e0dd7-108">The [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] plug-in for Firefox is installed with the [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)].</span></span> <span data-ttu-id="e0dd7-109">視窗 7 包含[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]，但不包含[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]Firefox 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="e0dd7-109">Window 7 includes the [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)], but does not include the [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] plug-in for Firefox.</span></span> <span data-ttu-id="e0dd7-110">您無法安裝[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]外掛程式，以用於在 Windows 7 上 Firefox。</span><span class="sxs-lookup"><span data-stu-id="e0dd7-110">You cannot install the [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] plug-in for Firefox on Windows 7.</span></span>  
  
 <span data-ttu-id="e0dd7-111">[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]不包含[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]Firefox 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="e0dd7-111">The [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] does not include the [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] plug-in for Firefox.</span></span> <span data-ttu-id="e0dd7-112">不過，如果兩個[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]和[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]會安裝，WPF Firefox 外掛程式會隨[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e0dd7-112">However, if both the [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] and [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] are installed, the WPF plug-in for Firefox is installed with the [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)].</span></span> <span data-ttu-id="e0dd7-113">因此[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]應用程式仍會執行，因為 WPF 主機會載入正確的 framework 版本。</span><span class="sxs-lookup"><span data-stu-id="e0dd7-113">Therefore [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] applications will still run because the WPF Host will load the correct version of the framework.</span></span> <span data-ttu-id="e0dd7-114">如需詳細資訊，請參閱[WPF 主機 (PresentationHost.exe)](../../../../docs/framework/wpf/app-development/wpf-host-presentationhost-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="e0dd7-114">For more information, see [WPF Host (PresentationHost.exe)](../../../../docs/framework/wpf/app-development/wpf-host-presentationhost-exe.md).</span></span>  
  
## <a name="net-framework-assistant-for-firefox"></a><span data-ttu-id="e0dd7-115">.NET Framework Assistant for Firefox</span><span class="sxs-lookup"><span data-stu-id="e0dd7-115">.NET Framework Assistant for Firefox</span></span>  
 <span data-ttu-id="e0dd7-116">.NET Framework 助理 firefox 讓獨立的 ClickOnce 應用程式從 Firefox 瀏覽器執行。</span><span class="sxs-lookup"><span data-stu-id="e0dd7-116">The .NET Framework Assistant for Firefox enables stand-alone ClickOnce applications to run from the Firefox browser.</span></span> <span data-ttu-id="e0dd7-117">.NET Framework 助理 Firefox 函式只有在安裝之前和之後 Firefox 瀏覽器時，即會相同。</span><span class="sxs-lookup"><span data-stu-id="e0dd7-117">The .NET Framework Assistant for Firefox functions identically when it is installed before and after the Firefox browser.</span></span> <span data-ttu-id="e0dd7-118">Firefox 瀏覽器啟動時，[!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)]已安裝，Firefox 找到並安裝.NET Framework 助理 firefox。</span><span class="sxs-lookup"><span data-stu-id="e0dd7-118">When the Firefox browser is launched and the [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)] is installed, Firefox finds and installs the .NET Framework Assistant for Firefox.</span></span> <span data-ttu-id="e0dd7-119">使用者可以設定 .NET Framework 助理 firefox，執行下列操作：</span><span class="sxs-lookup"><span data-stu-id="e0dd7-119">Users can configure the .NET Framework Assistant for Firefox to do the following:</span></span>  
  
-   <span data-ttu-id="e0dd7-120">執行 ClickOnce 應用程式之前提示。</span><span class="sxs-lookup"><span data-stu-id="e0dd7-120">Prompt before running the ClickOnce application.</span></span>  
  
-   <span data-ttu-id="e0dd7-121">報告所有安裝的.NET Framework 版本或最新的版本。</span><span class="sxs-lookup"><span data-stu-id="e0dd7-121">Report all installed versions of the .NET Framework or just the latest version.</span></span>  
  
 <span data-ttu-id="e0dd7-122">.NET Framework 助理 firefox 隨附於[!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e0dd7-122">The .NET Framework Assistant for Firefox is included with the [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)].</span></span> <span data-ttu-id="e0dd7-123">Firefox 移除.NET Framework 助理的詳細資訊，請參閱[如何移除.NET Framework 助理 firefox](http://go.microsoft.com/fwlink/?LinkId=177944)。</span><span class="sxs-lookup"><span data-stu-id="e0dd7-123">For information about removing the .NET Framework Assistant for Firefox, see [How to remove the .NET Framework Assistant for Firefox](http://go.microsoft.com/fwlink/?LinkId=177944).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0dd7-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0dd7-124">See Also</span></span>  
 [<span data-ttu-id="e0dd7-125">部署 WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="e0dd7-125">Deploying a WPF Application</span></span>](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)  
 [<span data-ttu-id="e0dd7-126">WPF XAML 瀏覽器應用程式概觀</span><span class="sxs-lookup"><span data-stu-id="e0dd7-126">WPF XAML Browser Applications Overview</span></span>](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md)  
 [<span data-ttu-id="e0dd7-127">偵測有無安裝 Firefox 的 WPF 外掛程式</span><span class="sxs-lookup"><span data-stu-id="e0dd7-127">Detect Whether the WPF Plug-In for Firefox Is Installed</span></span>](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed.md)
