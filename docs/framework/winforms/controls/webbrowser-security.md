---
title: "WebBrowser 安全性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "安全性 [Windows Form], WebBrowser 控制項"
  - "WebBrowser 控制項 [Windows Form], 安全性"
ms.assetid: 0968846e-48ee-485a-9797-65b5b9a622f8
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# WebBrowser 安全性
<xref:System.Windows.Forms.WebBrowser> 控制項設計為在完全信任的狀態下運作。  控制項顯示的 HTML 內容可來自外部 Web 伺服器，且可能包含指令碼或 Web 控制項形式的 Unmanaged 程式碼。  在這種情況下，如果使用 <xref:System.Windows.Forms.WebBrowser> 控制項，其安全性和使用 Internet Explorer 一樣，但是 Managed <xref:System.Windows.Forms.WebBrowser> 控制項不能防止這類 Unmanaged 程式碼執行。  
  
 如需基礎 ActiveX `WebBrowser` 控制項相關安全性問題的詳細資訊，請參閱 [WebBrowser 控制項](http://go.microsoft.com/fwlink/?LinkId=198812) \(英文\)。  
  
## 請參閱  
 <xref:System.Windows.Forms.WebBrowser>   
 [WebBrowser 控制項概觀](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)   
 [WebBrowser 控制項](http://go.microsoft.com/fwlink/?LinkId=198812)