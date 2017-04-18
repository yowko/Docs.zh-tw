---
title: "如何：啟用 Windows Form 在執行階段時重新排列 ToolStrip 項目 | Microsoft Docs"
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
  - "AllowItemReorder 屬性"
  - "範例 [Windows Form], 工具列"
  - "工具列 [Windows Form], 重先排列控制項"
  - "ToolStrip 控制項 [Windows Forms], 範例"
  - "ToolStrip 控制項 [Windows Forms], 重新排序項目"
ms.assetid: 8480b69a-379f-4dc2-8dcf-365ed93692b2
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：啟用 Windows Form 在執行階段時重新排列 ToolStrip 項目
您可以讓使用者重新整理 <xref:System.Windows.Forms.ToolStrip> 上的 <xref:System.Windows.Forms.ToolStripItem> 控制項。  
  
### 若要在執行階段啟用 ToolStripItem 重新整理  
  
-   將 <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> 屬性設為 `true`。  根據預設，<xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> 為 `false`。  
  
     在執行階段中，使用者只要按住 ALT 鍵和滑鼠左鍵，即可將 <xref:System.Windows.Forms.ToolStripItem> 拖曳到 <xref:System.Windows.Forms.ToolStrip> 上的不同位置。  
  
    ```vb  
    toolStrip1.AllowItemReorder = True  
  
    ```  
  
    ```csharp  
    toolStrip1.AllowItemReorder = true;  
  
    ```  
  
## 請參閱  
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>   
 [ToolStrip 控制項概觀](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)   
 [ToolStrip 控制項架構](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)   
 [ToolStrip 技術摘要](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)