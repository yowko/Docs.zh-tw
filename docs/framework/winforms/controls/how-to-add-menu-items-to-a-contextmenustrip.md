---
title: "如何：將功能表項目加入至 ContextMenuStrip | Microsoft Docs"
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
  - "內容功能表, 加入功能表項目"
  - "ContextMenuStrips, 加入功能表項目"
  - "捷徑功能表, 加入項目"
ms.assetid: 1ec14776-3ea2-4752-bd22-4fae0fd19e1a
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：將功能表項目加入至 ContextMenuStrip
您可以只將一個功能表項目或者一次將數個功能表項目加入至 <xref:System.Windows.Forms.ContextMenuStrip>。  
  
### 若要將單一功能表項目加入至 ContextMenuStrip  
  
-   使用 <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> 方法，可將一個功能表項目加入至 <xref:System.Windows.Forms.ContextMenuStrip>。  
  
     \[Visual Basic\]  
  
    ```  
    Me.contextMenuStrip1.Items.Add(Me.toolStripMenuItem1)  
    ```  
  
    ```csharp  
    this.contextMenuStrip1.Items.Add(toolStripMenuItem1);  
    ```  
  
### 若要將數個功能表項目加入至 ContextMenuStrip  
  
-   使用 <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> 方法，可將數個功能表項目加入至 <xref:System.Windows.Forms.ContextMenuStrip>。  
  
     \[Visual Basic\]  
  
    ```  
    Me.contextMenuStrip1.Items.AddRange(New _  
       System.Windows.Forms.ToolStripItem() {Me.toolStripMenuItem1, _  
          Me.toolStripMenuItem2})  
    ```  
  
    ```csharp  
    this.contextMenuStrip1.Items.AddRange(new   
       System.Windows.Forms.ToolStripItem[] {  
          this.toolStripMenuItem1, this.toolStripMenuItem2});  
    ```  
  
## 請參閱  
 [ContextMenuStrip 控制項](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)