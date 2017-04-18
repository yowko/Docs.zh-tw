---
title: "如何：變更應用程式工作階段之間的設定值 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "應用程式設定 [Windows Form], 應用程式工作階段之間"
  - "應用程式設定 [Windows Form], 變更"
ms.assetid: 1a85911f-97b2-476c-930b-83379edd890c
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：變更應用程式工作階段之間的設定值
有時您可能會想要在編譯和部署應用程式之後，變更應用程式工作階段之間的設定值。  例如，您可能會想要變更指向正確資料位置的連接字串。  因為編譯和部署應用程式之後，設計階段工具將無法使用，所以您必須在檔案中手動變更設定。  
  
### 若要變更應用程式工作階段之間的設定值  
  
1.  使用 Microsoft \[記事本\] 或者某些其他文字或 XML 編輯器，開啟與應用程式相關聯的 .config 檔案。  
  
2.  找出您要變更其設定的項目，  應該會與下列呈現的範例類似。  
  
    ```  
    <setting name="Setting1" serializeAs="String" >  
       <value>My Setting Value</value>  
    </setting>  
    ```  
  
3.  為您的設定輸入新值並儲存檔案。  
  
## 請參閱  
 [使用應用程式設定和使用者設定](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)   
 [應用程式設定概觀](../../../../docs/framework/winforms/advanced/application-settings-overview.md)