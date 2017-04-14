---
title: "如何：使用 ToolStrip 控制項中的工具提示 | Microsoft Docs"
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
  - "工具列 [Windows Form], 加入工具提示"
  - "ToolStrip 控制項 [Windows Forms], 加入工具提示"
  - "工具提示 [Windows Form], 加入"
ms.assetid: c5d86024-a7c5-44ee-8b3f-2daf53d80d3e
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：使用 ToolStrip 控制項中的工具提示
只要將 <xref:System.Windows.Forms.ToolStrip> 控制項的 <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> 屬性設為 `true`，即可顯示該控制項的 <xref:System.Windows.Forms.ToolTip>。  
  
### 若要顯示工具提示  
  
-   將控制項的 <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> 屬性設為 `true`。  
  
     <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=fullName> 的預設值為 `true`，而 <xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=fullName> 和 <xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=fullName> 的預設值則為 `false`。  
  
### 若要使用 ToolStripButton 工具提示文字的 ToolTipText 屬性  
  
1.  將按鈕的 <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> 屬性設為 `true`。  
  
2.  將按鈕的 <xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=fullName> 屬性設為 `false`。  
  
     根據預設，<xref:System.Windows.Forms.ToolStripButton>、<xref:System.Windows.Forms.ToolStripDropDownButton> 和 <xref:System.Windows.Forms.ToolStripSplitButton> 的 `AutoToolTip` 屬性是 `true`。  
  
     根據預設，<xref:System.Windows.Forms.ToolStripButton> 使用它的 `Text` 屬性做為 <xref:System.Windows.Forms.ToolTip> 文字。  若要在 <xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolTip> 中顯示自訂文字，請使用這個程序。  
  
> [!NOTE]
>  如果將 <xref:System.Windows.Forms.ToolStripItemDisplayStyle> 設定為 <xref:System.Windows.Forms.ToolStripItemDisplayStyle> 或 <xref:System.Windows.Forms.ToolStripItemDisplayStyle>，則按鈕上不會顯示文字，但仍會顯示工具提示。  
  
## 請參閱  
 <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>   
 <xref:System.Windows.Forms.ToolStripButton>   
 <xref:System.Windows.Forms.ToolStripDropDownButton>   
 <xref:System.Windows.Forms.ToolStripSplitButton>   
 [ToolStrip 控制項概觀](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)