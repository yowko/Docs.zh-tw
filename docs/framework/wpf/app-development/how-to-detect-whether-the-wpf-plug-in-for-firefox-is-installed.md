---
title: HOW TO：偵測有無安裝 Firefox 的 WPF 外掛程式
ms.date: 03/30/2017
helpviewer_keywords:
- plug-in for Firefox [WPF]
- detecting Firefox installation [WPF]
- checking for the Firefox plug-in [WPF]
- Firefox [WPF], detecting installation
- detecting whether the WPF plug-in for Firefox is installed [WPF]
ms.assetid: 5f839373-e3fb-44f1-88ad-4a0761f02189
ms.openlocfilehash: 3cc2f95627bc35fa4cb6c486d3b8ad61f69d7fea
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372889"
---
# <a name="how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed"></a><span data-ttu-id="c69eb-102">HOW TO：偵測有無安裝 Firefox 的 WPF 外掛程式</span><span class="sxs-lookup"><span data-stu-id="c69eb-102">How to: Detect Whether the WPF Plug-In for Firefox Is Installed</span></span>
<span data-ttu-id="c69eb-103">Windows Presentation Foundation (WPF) Firefox 的外掛程式可讓[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]鬆散 XAML 檔案，以在 Mozilla Firefox 瀏覽器中執行。</span><span class="sxs-lookup"><span data-stu-id="c69eb-103">The Windows Presentation Foundation (WPF) plug-in for Firefox enables [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] and loose XAML files to run in the Mozilla Firefox browser.</span></span> <span data-ttu-id="c69eb-104">本主題提供以 HTML 和系統管理員可用來判斷是否已安裝的 WPF 外掛程式適用於 Firefox 的 JavaScript 撰寫的指令碼。</span><span class="sxs-lookup"><span data-stu-id="c69eb-104">This topic provides a script written in HTML and JavaScript that administrators can use to determine whether the WPF plug-in for Firefox is installed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c69eb-105">如需有關安裝、 部署和偵測[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]，請參閱 <<c2> [ 安裝適用於開發人員的.NET Framework](../../install/guide-for-developers.md)。</span><span class="sxs-lookup"><span data-stu-id="c69eb-105">For more information about installing, deploying, and detecting the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], see [Install the .NET Framework for developers](../../install/guide-for-developers.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c69eb-106">範例</span><span class="sxs-lookup"><span data-stu-id="c69eb-106">Example</span></span>  
 <span data-ttu-id="c69eb-107">當[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]是安裝，用戶端電腦已使用的 WPF 外掛程式適用於 Firefox。</span><span class="sxs-lookup"><span data-stu-id="c69eb-107">When the [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] is installed, the client computer is configured with a WPF plug-in for Firefox.</span></span> <span data-ttu-id="c69eb-108">下列的範例指令碼會檢查適用於 Firefox 的 WPF 外掛程式，並接著會顯示適當的狀態訊息。</span><span class="sxs-lookup"><span data-stu-id="c69eb-108">The following example script checks for the WPF plug-in for Firefox and then displays an appropriate status message.</span></span>  
  
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
  
 <span data-ttu-id="c69eb-109">如果適用於 Firefox 的 WPF 外掛程式檢查成功，則會顯示下列狀態訊息：</span><span class="sxs-lookup"><span data-stu-id="c69eb-109">If the check for the WPF plug-in for Firefox is successful, the following status message is displayed:</span></span>  
  
 `The WPF plug-in for Firefox is installed.`  
  
 <span data-ttu-id="c69eb-110">否則，會顯示下列狀態訊息：</span><span class="sxs-lookup"><span data-stu-id="c69eb-110">Otherwise, the following status message is displayed:</span></span>  
  
 `The WPF plug-in for Firefox is not installed. Please install or reinstall the .NET Framework 3.5.`  
  
## <a name="see-also"></a><span data-ttu-id="c69eb-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c69eb-111">See also</span></span>
- [<span data-ttu-id="c69eb-112">偵測有無安裝 .NET Framework 3.0</span><span class="sxs-lookup"><span data-stu-id="c69eb-112">Detect Whether the .NET Framework 3.0 Is Installed</span></span>](how-to-detect-whether-the-net-framework-3-0-is-installed.md)
- [<span data-ttu-id="c69eb-113">偵測有無安裝 .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="c69eb-113">Detect Whether the .NET Framework 3.5 Is Installed</span></span>](how-to-detect-whether-the-net-framework-3-5-is-installed.md)
- [<span data-ttu-id="c69eb-114">WPF XAML 瀏覽器應用程式概觀</span><span class="sxs-lookup"><span data-stu-id="c69eb-114">WPF XAML Browser Applications Overview</span></span>](wpf-xaml-browser-applications-overview.md)
