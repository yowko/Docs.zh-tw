---
title: 如何：偵測有無安裝 Firefox 的 WPF 外掛程式
ms.date: 03/30/2017
helpviewer_keywords:
- plug-in for Firefox [WPF]
- detecting Firefox installation [WPF]
- checking for the Firefox plug-in [WPF]
- Firefox [WPF], detecting installation
- detecting whether the WPF plug-in for Firefox is installed [WPF]
ms.assetid: 5f839373-e3fb-44f1-88ad-4a0761f02189
ms.openlocfilehash: ba411d662a8e5b0c4727e23c8d507e8924b6e9e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546984"
---
# <a name="how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed"></a>如何：偵測有無安裝 Firefox 的 WPF 外掛程式
可讓 Windows Presentation Foundation (WPF) 外掛程式，以用於 Firefox[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]而且釋放 Mozilla Firefox 瀏覽器中執行的 XAML 檔案。 本主題提供以 HTML 和系統管理員可用來判斷是否已安裝外掛程式，以用於 Firefox WPF 的 JavaScript 撰寫的指令碼。  
  
> [!NOTE]
>  如需有關安裝、 部署和偵測[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]，請參閱[安裝.NET Framework 開發人員](../../../../docs/framework/install/guide-for-developers.md)。  
  
## <a name="example"></a>範例  
 當[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]已安裝，用戶端電腦都設定搭配外掛程式 WPF firefox。 下列範例指令碼會檢查有外掛程式之 wpf Firefox，，然後顯示適當的狀態訊息。  
  
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
  
 如果 Firefox 外掛程式之 wpf 的檢查成功，則會顯示下列狀態訊息：  
  
 `The WPF plug-in for Firefox is installed.`  
  
 否則，就會顯示下列狀態訊息：  
  
 `The WPF plug-in for Firefox is not installed. Please install or reinstall the .NET Framework 3.5.`  
  
## <a name="see-also"></a>另請參閱  
 [偵測有無安裝 .NET Framework 3.0](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-0-is-installed.md)  
 [偵測有無安裝 .NET Framework 3.5](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-5-is-installed.md)  
 [WPF XAML 瀏覽器應用程式概觀](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md)
