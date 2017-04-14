---
title: "Windows 市集應用程式的網路隔離 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: b064497c-d956-46b8-838d-7a0223c7e200
caps.latest.revision: 7
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 7
---
# Windows 市集應用程式的網路隔離
在 <xref:System.Net>、 <xref:System.Net.Http>和 <xref:System.Net.Http.Headers> 命名空間中的類別可用來開發 Windows 存放區應用程式或桌上型電腦應用程式。  當使用存放在 Windows 應用程式中，這些命名空間中的類別受網路隔離，一部分的應用程式安全性模型會影響的 [!INCLUDE[win8](../../../includes/win8-md.md)]所使用的。  在 Windows 存放應用程式的應用程式資訊清單必須啟用適當的網路功能系統可以允許的網路存取。  
  
## 網路隔離的清單  
 請使用這份檢查清單確定網路隔離存放區為您的 Windows 應用程式設定。  
  
1.  判斷應用程式所需的網路存取所要求的方向。  這可以是、或傳出用戶端啟始的要求或傳入寄來的需求也可以是這兩個 Web 要求型別的組合。  
  
2.  判斷的網路資源類型該應用程式會進行通訊。  應用程式可能需要與中的信任的資源連接或工作網路。  應用程式可能需要與網際網路資源的通訊。  應用程式可能需要對網路資源的兩種型別的存取。  
  
3.  設定應用程式資訊清單中的最小必要的網路隔離功能。  
  
4.  部署及執行應用程式來測試它用於疑難排解提供的網路隔離工具。  
  
 如需如何為 Web 針對疑難排解網路隔離使用隔離的功能和工具的詳細資訊， [如何設定網路隔離功能。](http://go.microsoft.com/fwlink/?LinkID=228265) 請參閱 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 開發人員文件。  
  
## 請參閱  
 [連接至 Web 服務。](http://go.microsoft.com/fwlink/?LinkID=245696)   
 [方針和列出網路隔離的](http://go.microsoft.com/fwlink/?LinkID=228265)   
 [Quickstart:連接使用 HttpClient](http://go.microsoft.com/fwlink/?LinkId=245697)   
 [如何使用 HttpClient 管理員](http://go.microsoft.com/fwlink/?LinkId=245699)   
 [如何保護 HttpClient 連接](http://go.microsoft.com/fwlink/?LinkId=245698)   
 [HttpClient 範例](http://go.microsoft.com/fwlink/?LinkId=242550)