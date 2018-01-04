---
title: "如何：偵測有無安裝 Firefox 的 WPF 外掛程式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- plug-in for Firefox [WPF]
- detecting Firefox installation [WPF]
- checking for the Firefox plug-in [WPF]
- Firefox [WPF], detecting installation
- detecting whether the WPF plug-in for Firefox is installed [WPF]
ms.assetid: 5f839373-e3fb-44f1-88ad-4a0761f02189
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 87e821bd95679372fd169b7880e969fd10b5d03c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed"></a><span data-ttu-id="ed3dc-102">如何：偵測有無安裝 Firefox 的 WPF 外掛程式</span><span class="sxs-lookup"><span data-stu-id="ed3dc-102">How to: Detect Whether the WPF Plug-In for Firefox Is Installed</span></span>
<span data-ttu-id="ed3dc-103">[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] Firefox 讓外掛程式[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]而且釋放 Mozilla Firefox 瀏覽器中執行的 XAML 檔案。</span><span class="sxs-lookup"><span data-stu-id="ed3dc-103">The [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] plug-in for Firefox enables [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] and loose XAML files to run in the Mozilla Firefox browser.</span></span> <span data-ttu-id="ed3dc-104">本主題提供以 HTML 和系統管理員可用來判斷是否已安裝外掛程式，以用於 Firefox WPF 的 JavaScript 撰寫的指令碼。</span><span class="sxs-lookup"><span data-stu-id="ed3dc-104">This topic provides a script written in HTML and JavaScript that administrators can use to determine whether the WPF plug-in for Firefox is installed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ed3dc-105">如需有關安裝、 部署和偵測[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]，請參閱[安裝.NET Framework 開發人員](../../../../docs/framework/install/guide-for-developers.md)。</span><span class="sxs-lookup"><span data-stu-id="ed3dc-105">For more information about installing, deploying, and detecting the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], see [Install the .NET Framework for developers](../../../../docs/framework/install/guide-for-developers.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed3dc-106">範例</span><span class="sxs-lookup"><span data-stu-id="ed3dc-106">Example</span></span>  
 <span data-ttu-id="ed3dc-107">當[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]已安裝，用戶端電腦都設定搭配外掛程式 WPF firefox。</span><span class="sxs-lookup"><span data-stu-id="ed3dc-107">When the [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] is installed, the client computer is configured with a WPF plug-in for Firefox.</span></span> <span data-ttu-id="ed3dc-108">下列範例指令碼會檢查有外掛程式之 wpf Firefox，，然後顯示適當的狀態訊息。</span><span class="sxs-lookup"><span data-stu-id="ed3dc-108">The following example script checks for the WPF plug-in for Firefox and then displays an appropriate status message.</span></span>  
  
```  
<HTML>  
  
  <HEAD>  
    <TITLE>Test for the WPF plug-in for Firefox</TITLE>  
    <META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=utf-8" />  
    <SCRIPT type="text/javascript">  
    <!--  
    function OnLoad()  
    {  
  
       // Check for the WPF plug-in for Firefox and report  
       var msg = "The WPF plug-in for Firefox is ";  
       var wpfPlugin = navigator.plugins["Windows Presentation Foundation"];  
       if( wpfPlugin != null ) {  
          document.writeln(msg + " installed.");  
       }  
       else {  
          document.writeln(msg + " not installed. Please install or reinstall the .NET Framework 3.5.");  
       }  
    }  
    -->  
    </SCRIPT>  
  </HEAD>  
  
  <BODY onload="OnLoad()" />  
  
</HTML>  
```  
  
 <span data-ttu-id="ed3dc-109">如果 Firefox 外掛程式之 wpf 的檢查成功，則會顯示下列狀態訊息：</span><span class="sxs-lookup"><span data-stu-id="ed3dc-109">If the check for the WPF plug-in for Firefox is successful, the following status message is displayed:</span></span>  
  
 `The WPF plug-in for Firefox is installed.`  
  
 <span data-ttu-id="ed3dc-110">否則，就會顯示下列狀態訊息：</span><span class="sxs-lookup"><span data-stu-id="ed3dc-110">Otherwise, the following status message is displayed:</span></span>  
  
 `The WPF plug-in for Firefox is not installed. Please install or reinstall the .NET Framework 3.5.`  
  
## <a name="see-also"></a><span data-ttu-id="ed3dc-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="ed3dc-111">See Also</span></span>  
 [<span data-ttu-id="ed3dc-112">偵測有無安裝 .NET Framework 3.0</span><span class="sxs-lookup"><span data-stu-id="ed3dc-112">Detect Whether the .NET Framework 3.0 Is Installed</span></span>](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-0-is-installed.md)  
 [<span data-ttu-id="ed3dc-113">偵測有無安裝 .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="ed3dc-113">Detect Whether the .NET Framework 3.5 Is Installed</span></span>](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-5-is-installed.md)  
 [<span data-ttu-id="ed3dc-114">WPF XAML 瀏覽器應用程式概觀</span><span class="sxs-lookup"><span data-stu-id="ed3dc-114">WPF XAML Browser Applications Overview</span></span>](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md)
