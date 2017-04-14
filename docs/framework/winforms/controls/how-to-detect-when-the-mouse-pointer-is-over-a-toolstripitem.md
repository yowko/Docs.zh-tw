---
title: "如何：當滑鼠指標移至 ToolStripItem 上時偵測 | Microsoft Docs"
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
  - "滑鼠, 偵測工具列上的移動"
  - "工具列 [Windows Form], 偵測滑鼠移動"
  - "ToolStrip 控制項 [Windows Forms], 偵測滑鼠移動"
  - "ToolStripItem 類別, 偵測滑鼠移動"
ms.assetid: d38b5082-aba7-4f6c-841b-bd9714e307fd
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：當滑鼠指標移至 ToolStripItem 上時偵測
請使用下列程序，當滑鼠指標移至 <xref:System.Windows.Forms.ToolStripItem> 上時進行偵測。  
  
### 若要在指標移至 ToolStripItem 上時偵測  
  
-   請使用項目的 <xref:System.Windows.Forms.ToolStripItem.Selected%2A> 屬性，此項目中的 <xref:System.Windows.Forms.ToolStripItem.CanSelect%2A> 是 `true`。  
  
     這可讓您避免必須同步處理 <xref:System.Windows.Forms.ToolStripItem.MouseEnter> 和 <xref:System.Windows.Forms.ToolStripItem.MouseLeave> 事件的情形。  
  
## 請參閱  
 <xref:System.Windows.Forms.ToolStripItem>   
 <xref:System.Windows.Forms.ToolStripItem.Selected%2A>   
 [ToolStrip 控制項概觀](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)