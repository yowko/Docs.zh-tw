---
title: "如何：變更 Windows Form 中 ToolStrip 項目的間距和對齊方式 | Microsoft Docs"
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
  - "工具列 [Windows Form], 對齊項目"
  - "ToolStrip 控制項 [Windows Forms], 對齊項目"
ms.assetid: cd483466-0f49-43df-addf-e2b5fcd64027
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：變更 Windows Form 中 ToolStrip 項目的間距和對齊方式
<xref:System.Windows.Forms.ToolStrip> 控制項完全支援配置功能，例如：<xref:System.Windows.Forms.ToolStripItem> 控制項的縮放和控制項彼此之間的間距、排列 <xref:System.Windows.Forms.ToolStrip> 上的控制項，以及控制項相對於 <xref:System.Windows.Forms.ToolStrip> 的間距。  
  
 由於 <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> 屬性的預設值為 `true`，因此控制項會自動縮放，除非您將 <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> 屬性改設為 `false`。  
  
### 若要手動縮放 ToolStripItem  
  
1.  將相關控制項的 <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> 屬性設為 `false`。  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
  
    ```  
  
2.  依照您想要的方式為相關聯的 <xref:System.Windows.Forms.ToolStripItem> 設定 <xref:System.Windows.Forms.ToolStripItem.Size%2A> 屬性。  
  
### 若要設定 ToolStripItem 的間距  
  
1.  將所需的值 \(以像素為單位\) 插入至相關控制項的 <xref:System.Windows.Forms.ToolStripItem.Margin%2A> 屬性。  
  
     <xref:System.Windows.Forms.ToolStripItem.Margin%2A> 屬性的值會依「左、上、右、下」的順序，指定項目和相鄰項目之間的間距。  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding   
        (3, 0, 3, 0);  
  
    ```  
  
### 若要將 ToolStripItem 對齊 ToolStrip 的右邊  
  
1.  將相關控制項的 <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> 屬性設為 <xref:System.Windows.Forms.ToolStripItemAlignment>。  根據預設，<xref:System.Windows.Forms.ToolStripItem.Alignment%2A> 會設定為 <xref:System.Windows.Forms.ToolStripItemAlignment>，使控制項對齊 <xref:System.Windows.Forms.ToolStrip> 的左邊。  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =   
        System.Windows.Forms.ToolStripItemAlignment.Right;  
  
    ```  
  
### 若要排列 ToolStrip 上的 ToolStrip 項目  
  
-   將 <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> 屬性設為想要的 <xref:System.Windows.Forms.ToolStripLayoutStyle> 值。  
  
    ```vb  
    ToolStripDropDown1.LayoutStyle = _  
        System.Windows.Forms.ToolStripLayoutStyle.Flow  
  
    ```  
  
    ```csharp  
    toolStripDropDown1.LayoutStyle =   
        System.Windows.Forms.ToolStripLayoutStyle.Flow;  
  
    ```  
  
## 請參閱  
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.Control.Layout>   
 <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>   
 <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>   
 <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>   
 <xref:System.Windows.Forms.ToolStripItem.Placement%2A>   
 <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>   
 [ToolStrip 控制項概觀](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)   
 [ToolStrip 控制項架構](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)   
 [ToolStrip 技術摘要](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)