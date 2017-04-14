---
title: "TabControl 控制項概觀 (Windows Form) | Microsoft Docs"
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
  - "TabControl"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "屬性頁, Windows Form"
  - "索引標籤頁, 關於索引標籤頁"
  - "TabControl 控制項 [Windows Form], 關於 TabControl 控制項"
  - "Windows Form 對話方塊, 索引標籤"
ms.assetid: 2b4ea784-a39d-463c-81d8-af74ce068476
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# TabControl 控制項概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.TabControl> 可顯示多個索引標籤，就如同筆記本的分割線，或檔案櫃中一組資料夾的標籤一樣。  此索引標籤可包含圖片和其他控制項。  您可以使用索引標籤控制項來產生這種多頁面的對話方塊，Windows 作業系統中的許多地方都有出現這種對話方塊，例如 \[控制台\] 的 \[顯示內容\]。  此外，<xref:System.Windows.Forms.TabControl> 可以用來建立用於設定相關屬性的群組的屬性頁面。  
  
## 使用 TabControl  
 <xref:System.Windows.Forms.TabControl> 的最重要屬性是 <xref:System.Windows.Forms.TabControl.TabPages%2A>，其中包含個別的索引標籤。  每個個別的索引標籤都是一個 <xref:System.Windows.Forms.TabPage> 物件。  按一下索引標籤時，它會為 <xref:System.Windows.Forms.TabPage> 物件引發 <xref:System.Windows.Forms.Control.Click> 事件。  
  
## 請參閱  
 <xref:System.Windows.Forms.TabControl>   
 [TabControl 控制項](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)   
 [如何：變更 Windows Form TabControl 的外觀](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)   
 [如何：將控制項加入至索引標籤頁](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)   
 [如何：使用 Windows Form TabControl 加入和移除索引標籤](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)   
 [如何：停用索引標籤頁](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)   
 [Windows Form 中的對話方塊](../../../../docs/framework/winforms/dialog-boxes-in-windows-forms.md)