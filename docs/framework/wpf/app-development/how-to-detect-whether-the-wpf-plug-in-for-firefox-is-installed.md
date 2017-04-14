---
title: "如何：偵測有無安裝 Firefox 的 WPF 外掛程式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "檢查 Firefox 外掛程式 [WPF]"
  - "偵測 Firefox 安裝 [WPF]"
  - "偵測有無安裝 Firefox 的 WPF 外掛程式 [WPF]"
  - "Firefox [WPF], 偵測安裝"
  - "Firefox 的外掛程式 [WPF]"
ms.assetid: 5f839373-e3fb-44f1-88ad-4a0761f02189
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：偵測有無安裝 Firefox 的 WPF 外掛程式
Firefox 的 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 外掛程式可讓 [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] 和鬆散的 XAML 檔案在 Mozilla Firefox 瀏覽器中執行。  本主題提供以 HTML 和 JavaScript 撰寫的指令碼，供系統管理員用來判斷是否已安裝 Firefox 的 WPF 外掛程式。  
  
> [!NOTE]
>  如需安裝、部署及偵測 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 的詳細資訊，請參閱[安裝.NET Framework](../../../../docs/framework/install/guide-for-developers.md)。  
  
## 範例  
 若已安裝 [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]，用戶端電腦便會設定為使用 Firefox 的 WPF 外掛程式。  下列指令碼範例會檢查是否有 Firefox 的 WPF 外掛程式，然後顯示適當的狀態訊息。  
  
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
  
 如果檢查出有 Firefox 的 WPF 外掛程式，則會顯示下列狀態訊息：  
  
 `The WPF plug-in for Firefox is installed.`  
  
 否則，便會顯示下列狀態訊息：  
  
 `The WPF plug-in for Firefox is not installed.  Please install or reinstall the .NET Framework 3.5.`  
  
## 請參閱  
 [偵測有無安裝 .NET Framework 3.0](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-0-is-installed.md)   
 [偵測有無安裝 .NET Framework 3.5](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-5-is-installed.md)   
 [WPF XAML 瀏覽器應用程式概觀](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md)