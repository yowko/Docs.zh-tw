---
title: "如何：使用 WebBrowser 控制項巡覽至 URL | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "WebBrowser.Navigate"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "範例 [Windows Form], WebBrowser 控制項"
  - "URL, 巡覽至"
  - "WebBrowser 控制項 [Windows Form], 範例"
  - "WebBrowser 控制項 [Windows Form], 巡覽至 URL"
ms.assetid: b3ec38cb-f509-4d0b-bd79-9f3611259c62
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：使用 WebBrowser 控制項巡覽至 URL
下列程式碼範例會示範如何將 <xref:System.Windows.Forms.WebBrowser> 控制項巡覽至特定的 URL。  
  
 若要判斷新文件何時完全載入，請處理 <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> 事件。  如需這個事件的示範，請參閱 [如何：使用 WebBrowser 控制項列印](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)。  
  
## 範例  
  
```vb  
Me.webBrowser1.Navigate("http://www.microsoft.com")  
```  
  
```csharp  
this.webBrowser1.Navigate("http://www.microsoft.com");  
```  
  
## 編譯程式碼  
 這個範例需要：  
  
-   名為 `webBrowser1` 的 <xref:System.Windows.Forms.WebBrowser> 控制項。  
  
-   `System` 和 `System.Windows.Forms` 組件的參考。  
  
## 請參閱  
 <xref:System.Windows.Forms.WebBrowser>   
 <xref:System.Windows.Forms.WebBrowser.DocumentCompleted?displayProperty=fullName>   
 <xref:System.Windows.Forms.WebBrowser.Navigating?displayProperty=fullName>   
 <xref:System.Windows.Forms.WebBrowser.Navigated?displayProperty=fullName>   
 [WebBrowser 控制項](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)   
 [如何：使用 WebBrowser 控制項列印](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)