---
title: "如何：變更 Windows Form 中 ToolStrip 文字和影像的外觀 | Microsoft Docs"
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
  - "工具列 [Windows Form], 外觀"
  - "工具列 [Windows Form], 影像"
  - "工具列 [Windows Form], 文字"
  - "ToolStrip 控制項 [Windows Forms], 外觀"
  - "ToolStrip 控制項 [Windows Forms], 影像"
  - "ToolStrip 控制項 [Windows Forms], 文字"
ms.assetid: d62dc9d1-2edd-4dfa-aed7-1335d6e13d86
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：變更 Windows Form 中 ToolStrip 文字和影像的外觀
您可以控制 <xref:System.Windows.Forms.ToolStripItem> 上是否要顯示文字和影像，以及它們之間和它們與 <xref:System.Windows.Forms.ToolStrip> 之間的對齊方式。  
  
### 若要定義 ToolStripItem 上所顯示的內容  
  
-   將 <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> 屬性設為需要的值。  可能值為 `Image`、`ImageAndText`, `None` 和 `Text`。  預設值為 `ImageAndText`。  
  
    ```vb  
    ToolStripButton2.DisplayStyle = _  
        System.Windows.Forms.ToolStripItemDisplayStyle.Image  
  
    ```  
  
    ```csharp  
    toolStripButton2.DisplayStyle = System.Windows.Forms.ToolStripItemDisplayStyle.Image;  
  
    ```  
  
### 若要對齊 ToolStripItem 上的文字  
  
-   將 <xref:System.Windows.Forms.ToolStripItem.TextAlign%2A> 屬性設為需要的值。  可能值為 top、middle、bottom 與 left、center、right 的任何組合。  預設值為 `MiddleCenter`。  
  
    ```vb  
    ToolStripSplitButton1.TextAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
  
    ```  
  
    ```csharp  
    toolStripSplitButton1.TextAlign = System.Drawing.ContentAlignment.MiddleRight;  
  
    ```  
  
### 若要對齊 ToolStripItem 上的影像  
  
-   將 <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> 屬性設為需要的值。  可能值為 top、middle、bottom 與 left、center、right 的任何組合。  預設值為 `MiddleLeft`。  
  
    ```vb  
    ToolStripSplitButton1.ImageAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
  
    ```  
  
    ```csharp  
    toolStripSplitButton1.ImageAlign = System.Drawing.ContentAlignment.MiddleRight;  
  
    ```  
  
### 若要定義 ToolStripItem 文字和影像彼此之間的顯示關係  
  
-   將 <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> 屬性設為需要的值。  可能值為 `ImageAboveText`、`ImageBeforeText`、`Overlay`、`TextAboveImage` 和 `TextBeforeImage`。  預設值為 `ImageBeforeText`。  
  
    ```vb  
    ToolStripButton1.TextImageRelation = _  
        System.Windows.Forms.TextImageRelation.ImageAboveText  
  
    ```  
  
    ```csharp  
    toolStripButton1.TextImageRelation = System.Windows.Forms.TextImageRelation.ImageAboveText;  
  
    ```  
  
## 請參閱  
 <xref:System.Windows.Forms.ToolStrip>   
 [ToolStrip 控制項概觀](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)   
 [ToolStrip 控制項架構](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)   
 [ToolStrip 技術摘要](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)