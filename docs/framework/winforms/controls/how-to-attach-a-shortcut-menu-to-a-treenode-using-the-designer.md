---
title: "如何：使用設計工具將捷徑功能表附加至 TreeNode | Microsoft Docs"
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
  - "捷徑功能表, 附加到 TreeNodes"
  - "TreeNode, 使用設計工具附加捷徑功能表"
ms.assetid: 8e45e184-1313-4f8f-90ff-2cd5789b2268
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：使用設計工具將捷徑功能表附加至 TreeNode
Windows Form <xref:System.Windows.Forms.TreeView> 控制項會顯示節點的階層架構，就和在 Windows 作業系統的 Windows 檔案總管左窗格中所顯示的檔案和資料夾相類似。  設定好 <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> 屬性之後，當使用者在 <xref:System.Windows.Forms.TreeView> 控制項上按一下滑鼠右鍵時，便可提供內容相關性的作業。  將 <xref:System.Windows.Forms.ContextMenuStrip> 元件與個別 <xref:System.Windows.Forms.TreeNode> 項目產生關聯之後，便可將捷徑功能表功能的自訂層級加入至 <xref:System.Windows.Forms.TreeView> 控制項。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要在設計階段將捷徑功能表與 TreeNode 產生關聯  
  
1.  加入 <xref:System.Windows.Forms.TreeView> 控制項至表單，然後視需要加入節點至 <xref:System.Windows.Forms.TreeView>。  如需詳細資訊，請參閱 [如何：使用 Windows Form TreeView 控制項加入和移除節點](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)。  
  
2.  加入 <xref:System.Windows.Forms.ContextMenuStrip> 元件至表單，然後加入項目至捷徑功能表，此功能表代表您希望在執行階段可以使用的節點層級作業。  如需詳細資訊，請參閱 [如何：將功能表項目加入至 ContextMenuStrip](../../../../docs/framework/winforms/controls/how-to-add-menu-items-to-a-contextmenustrip.md)。  
  
3.  重新開啟 <xref:System.Windows.Forms.TreeView> 控制項的 \[**TreeNodeEditor**\] 對話方塊，選取要編輯的節點，並將該節點的 <xref:System.Windows.Forms.ContextMenuStrip> 屬性設定至您加入的捷徑功能表。  
  
4.  設定好這個屬性之後，當在節點上按一下滑鼠右鍵時將會出現捷徑功能表。  
  
     此外，需要撰寫程式碼以處理這些功能表項目的 <xref:System.Windows.Forms.ToolStripItem.Click> 事件。  
  
## 請參閱  
 [TreeView 控制項](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)   
 [TreeView 控制項概觀](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)   
 [ContextMenuStrip 控制項](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)