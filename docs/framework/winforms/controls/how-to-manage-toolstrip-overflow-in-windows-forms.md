---
title: "如何：管理 Windows Form 中的 ToolStrip 溢位 | Microsoft Docs"
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
  - "CanOverflow 屬性"
  - "範例 [Windows Form], 工具列"
  - "Overflow 屬性"
  - "工具列 [Windows Form], 管理溢位"
  - "ToolStrip 控制項 [Windows Forms], 管理溢位"
ms.assetid: fa10e0ad-4cbf-4c0d-9082-359c2f855d4e
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：管理 Windows Form 中的 ToolStrip 溢位
當分配的空間無法容納 <xref:System.Windows.Forms.ToolStrip> 控制項上的所有項目時，您可以啟用 <xref:System.Windows.Forms.ToolStrip> 上的溢位功能並且決定特定 <xref:System.Windows.Forms.ToolStripItem> 的溢位行為。  
  
 如果 <xref:System.Windows.Forms.ToolStripItem> 所需的空間大於指定的空間，當您將它加入至設定為目前表單大小的 <xref:System.Windows.Forms.ToolStrip> 時，<xref:System.Windows.Forms.ToolStrip> 上會自動出現 <xref:System.Windows.Forms.ToolStripOverflowButton>。  <xref:System.Windows.Forms.ToolStripOverflowButton> 出現後，啟用溢位的項目會被移到下拉式溢位功能表中。  這可讓您自訂和排列 <xref:System.Windows.Forms.ToolStrip> 項目要如何適當地調整以配合不同的表單大小。  當項目發生溢位情形時，也可以利用 <xref:System.Windows.Forms.ToolStripItem.Placement%2A> 屬性、<xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=fullName> 屬性和 <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> 事件來變更項目的外觀。  不論在設計階段或是在執行階段放大表單，主要 <xref:System.Windows.Forms.ToolStrip> 上將能夠顯示更多的 <xref:System.Windows.Forms.ToolStripItem>，而在縮小表單之前，<xref:System.Windows.Forms.ToolStripOverflowButton> 甚至可能消失。  
  
### 若要在 ToolStrip 控制項上啟用溢位  
  
-   請確認 <xref:System.Windows.Forms.ToolStrip> 的 <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> 屬性不是設定為 `false`。  預設為 `True`。  
  
     如果 <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> 是 `True` \(預設值\)，當 <xref:System.Windows.Forms.ToolStripItem> 的內容超過水平 <xref:System.Windows.Forms.ToolStrip> 的寬度或超過垂直 <xref:System.Windows.Forms.ToolStrip> 的高度時，<xref:System.Windows.Forms.ToolStripItem> 會設定為下拉式溢位功能表。  
  
### 若要指定特定 ToolStripItem 的溢位行為  
  
-   將 <xref:System.Windows.Forms.ToolStripItem> 的 <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> 屬性設為所需的值。  其可能值為 `Always`、`Never` 和 `AsNeeded`。  The defaultis `AsNeeded`.  
  
    ```vb  
    toolStripTextBox1.Overflow = _  
    System.Windows.Forms.ToolStripItemOverflow.Never  
  
    ```  
  
    ```csharp  
    toolStripTextBox1.Overflow = _  
    System.Windows.Forms.ToolStripItemOverflow.Never;  
  
    ```  
  
## 請參閱  
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.ToolStripOverflowButton>   
 <xref:System.Windows.Forms.ToolStripItem.Overflow%2A>   
 <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>   
 [ToolStrip 控制項概觀](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)   
 [ToolStrip 控制項架構](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)   
 [ToolStrip 技術摘要](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)