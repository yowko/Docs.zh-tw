---
title: "如何：在 ToolStrip 控制項中建立切換按鈕 | Microsoft Docs"
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
  - "範例 [Windows Form], 工具列"
  - "切換按鈕, 建立"
  - "ToolStrip 控制項 [Windows Forms], 建立切換按鈕"
ms.assetid: d9c197df-4c65-43f2-beee-b68b52b2befc
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：在 ToolStrip 控制項中建立切換按鈕
當使用者按一下切換按鈕時，此按鈕會下凹並且保持這個狀態直到使用者再按一下按鈕為止。  
  
### 若要建立可切換的 ToolStripButton  
  
-   程式碼使用如下列程式碼範例所示：  這個程式碼會假設您的表單包含 <xref:System.Windows.Forms.ToolStrip> 控制項，而且其 <xref:System.Windows.Forms.ToolStrip.Items%2A> 集合包含稱為 `toolStripButton1` 的 <xref:System.Windows.Forms.ToolStripButton>。  另外還會假設您已擁有稱為 `toolStripButton1_CheckedChanged` 的事件處理常式。  
  
     \[Visual Basic\]  
  
    ```  
    toolStripButton1.CheckOnClick = True  
    toolStripButton1.CheckedChanged AddressOf _  
    EventHandler(toolStripButton1_CheckedChanged);  
  
    ```  
  
     \[C\#\]  
  
    ```  
    toolStripButton1.CheckOnClick = true;  
    toolStripButton1.CheckedChanged += new _  
    EventHandler(toolStripButton1_CheckedChanged);  
  
    ```  
  
## 請參閱  
 <xref:System.Windows.Forms.ToolStripButton>   
 [ToolStrip 控制項概觀](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)