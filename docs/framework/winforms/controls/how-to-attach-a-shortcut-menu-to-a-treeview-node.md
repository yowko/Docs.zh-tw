---
title: "如何：將捷徑功能表附加至 TreeView 節點 | Microsoft Docs"
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
  - "捷徑功能表, 加入到 TreeView 控制項"
  - "TreeView 控制項中的樹狀節點, 捷徑功能表"
  - "TreeView 控制項 [Windows Form], 加入快速鍵功能表"
ms.assetid: a23c6752-fd8f-44ad-b781-bab37962fc7c
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：將捷徑功能表附加至 TreeView 節點
Windows Form <xref:System.Windows.Forms.TreeView> 控制項顯示節點的階層架構，顯示的方法如同 Windows 檔案總管左窗格中所顯示的檔案和資料夾。  設定好 <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> 屬性之後，當使用者在 <xref:System.Windows.Forms.TreeView> 控制項上按一下滑鼠右鍵時，便可提供內容相關性的作業。  將 <xref:System.Windows.Forms.ContextMenuStrip> 元件與個別 <xref:System.Windows.Forms.TreeNode> 項目產生關聯之後，便可將捷徑功能表功能的自訂層級加入至 <xref:System.Windows.Forms.TreeView> 控制項。  
  
### 若要以程式設計方式將捷徑功能表與 TreeNode 產生關聯  
  
1.  以適當的屬性設定產生 \(Instantiate\) <xref:System.Windows.Forms.TreeView> 控制項，接著建立根 <xref:System.Windows.Forms.TreeNode>，然後再加入子節點。  
  
2.  產生 <xref:System.Windows.Forms.ContextMenuStrip> 元件，然後再為每個想在執行階段使用的作業加入 <xref:System.Windows.Forms.ToolStripMenuItem>。  
  
3.  將適當的 <xref:System.Windows.Forms.TreeNode> 的 <xref:System.Windows.Forms.TreeNode.ContextMenuStrip%2A> 屬性設為所建立的捷徑功能表。  
  
4.  設定好這個屬性之後，當在節點上按一下滑鼠右鍵時將會出現捷徑功能表。  
  
 下列程式碼範例將建立基本的 <xref:System.Windows.Forms.TreeView> 以及與 <xref:System.Windows.Forms.TreeView> 的根 <xref:System.Windows.Forms.TreeNode> 關聯的 <xref:System.Windows.Forms.ContextMenuStrip>。  您將需要自訂功能表選擇，以符合正在開發的 <xref:System.Windows.Forms.TreeView>。  此外，需要撰寫程式碼以處理這些功能表項目的 <xref:System.Windows.Forms.ToolStripItem.Click> 事件。  
  
 [!code-cpp[System.Windows.Forms.TreeNodeContextMenuStrip#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/cpp/Form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.TreeNodeContextMenuStrip#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.TreeNodeContextMenuStrip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/VB/Form1.vb#1)]  
  
## 請參閱  
 <xref:System.Windows.Forms.ContextMenuStrip>   
 [TreeView 控制項](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)