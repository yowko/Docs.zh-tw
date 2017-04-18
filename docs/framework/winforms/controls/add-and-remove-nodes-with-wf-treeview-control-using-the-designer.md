---
title: "如何：使用設計工具搭配 Windows Form TreeView 控制項加入和移除節點 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "範例 [Windows Form], TreeView 控制項"
  - "TreeView 控制項中的樹狀節點"
  - "TreeView 控制項 [Windows Form], 加入節點"
  - "TreeView 控制項 [Windows Form], 移除節點"
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：使用設計工具搭配 Windows Form TreeView 控制項加入和移除節點
因為 <xref:System.Windows.Forms.TreeView> 控制項以階層方式顯示節點，在加入節點時，您必須注意其父節點為何。  
  
 下列程序需要 **Windows 應用程式**專案，且專案具有包含 <xref:System.Windows.Forms.TreeView> 控制項的表單。  如需設定這類專案的詳細資訊，請參閱 [How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa) 和 [如何：將控制項加入至 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 在設計工具中加入或移除節點  
  
1.  選取 <xref:System.Windows.Forms.TreeView> 控制項。  
  
2.  在 \[**屬性**\] 視窗中，按一下 <xref:System.Windows.Forms.TreeView.Nodes%2A> 屬性旁邊的**省略符號** \(![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) 按鈕。  
  
     \[**TreeNode 編輯器**\] 隨即出現。  
  
3.  如果要加入節點，必須要有根節點 \(Root Node\)；如果沒有，則必須先按一下 \[**加入根目錄**\] 按鈕以加入根目錄。  您接著可以加入子節點，方法是選取根節點或其他任何節點，再按一下 \[**加入子系**\] 按鈕。  
  
4.  若要刪除節點，請選取要刪除的節點，然後按一下 \[**刪除**\] 按鈕。  
  
## 請參閱  
 [TreeView 控制項](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)   
 [TreeView 控制項概觀](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)   
 [如何：設定 Windows Form TreeView 控制項的圖示](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md)   
 [如何：逐一查看 Windows Form TreeView 控制項的所有節點](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)   
 [如何：判斷按下哪個 TreeView 節點](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)   
 [如何：將自訂資訊加入 TreeView 或 ListView 控制項 \(Windows Form\)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)