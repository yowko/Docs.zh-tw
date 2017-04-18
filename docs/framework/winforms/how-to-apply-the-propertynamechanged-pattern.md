---
title: "如何：套用 PropertyNameChanged 模式 | Microsoft Docs"
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
  - "自訂控制項 [Windows Form], 屬性變更 (使用程式碼)"
  - "資料繫結, 自訂控制項"
  - "PropertyNameChanged 模式, 套用"
ms.assetid: aa47ddf6-5223-40c4-833f-a78992194836
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 如何：套用 PropertyNameChanged 模式
下列程式碼範例示範如何將 *PropertyName*Changed 模式套用至自訂控制項。  在您實作與 Windows Form 資料繫結引擎一起使用的自訂控制項時套用此模式。  
  
## 範例  
 [!code-csharp[System.Windows.Forms.ChangeNotification#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/CS/Form1.cs#3)]
 [!code-vb[System.Windows.Forms.ChangeNotification#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/VB/Form1.vb#3)]  
  
## 編譯程式碼  
 若要編譯前一個程式碼範例：  
  
-   請將這個程式碼貼至空的程式碼檔。  您必須在包含 `Main` 方法的 Windows Form 上使用自訂控制項。  
  
## 請參閱  
 [如何：實作 INotifyPropertyChanged 介面](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md)   
 [Windows Form 資料繫結中的變更告知](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)   
 [Windows Form 資料繫結](../../../docs/framework/winforms/windows-forms-data-binding.md)