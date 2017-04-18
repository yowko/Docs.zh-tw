---
title: "如何：設定 Windows Form TreeView 控制項的圖示 | Microsoft Docs"
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
  - "範例 [Windows Form], TreeView 控制項"
  - "圖示, TreeView 控制項的設定"
  - "ImageList 元件 [Windows Form], 加入影像"
  - "TreeView 控制項中的樹狀節點, 圖示"
  - "TreeView 控制項 [Windows Form], 節點圖示"
ms.assetid: c14ddcc0-e5a6-4c21-a2d5-6799fd491781
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# 如何：設定 Windows Form TreeView 控制項的圖示
Windows Form <xref:System.Windows.Forms.TreeView> 控制項可在每個節點旁顯示圖示。  這些圖示緊接著節點文字的左邊。  如果要顯示這些圖示，您必須使樹狀檢視與 <xref:System.Windows.Forms.ImageList> 控制項產生關聯。  如需影像清單的詳細資訊，請參閱 [ImageList 元件](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) 和 [如何：使用 Windows Form ImageList 元件加入或移除影像](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)。  
  
> [!NOTE]
>  當應用程式呼叫 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=fullName> 時，在 Microsoft .NET Framework 1.1 版中的一個錯誤會造成無法在 <xref:System.Windows.Forms.TreeView> 節點上顯示影像。  若要解決這個錯誤，請在呼叫 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> 之後，立即呼叫 `Main` 方法中的 <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=fullName>。  這個錯誤已在 [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] 中修正。  
  
### 若要顯示樹狀檢視中的影像  
  
1.  將 <xref:System.Windows.Forms.TreeView> 控制項的 <xref:System.Windows.Forms.TreeView.ImageList%2A> 屬性設定為要使用的現有 <xref:System.Windows.Forms.ImageList> 控制項。  
  
     這些屬性可使用 \[屬性\] 視窗或程式碼在設計工具中設定。  
  
    ```vb  
    TreeView1.ImageList = ImageList1  
  
    ```  
  
    ```csharp  
    treeView1.ImageList = imageList1;  
  
    ```  
  
    ```cpp  
    treeView1->ImageList = imageList1;  
    ```  
  
2.  設定節點的 <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> 和 <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> 屬性。  <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> 屬性會決定節點的正常和展開狀態所顯示的影像，而 <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> 屬性會決定節點的選取狀態所顯示的影像。  
  
     這些屬性可以用程式碼或在 \[TreeNode 編輯器\] 內設定。  若要開啟 \[TreeNode 編輯器\]，請按一下 \[屬性\] 視窗中 <xref:System.Windows.Forms.TreeView.Nodes%2A> 屬性旁邊的省略按鈕 \(![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\)。  
  
    ```vb  
    ' (Assumes that ImageList1 contains at least two images and  
    ' the TreeView control contains a selected image.)  
    TreeView1.SelectedNode.ImageIndex = 0  
    TreeView1.SelectedNode.SelectedImageIndex = 1  
  
    ```  
  
    ```csharp  
    // (Assumes that imageList1 contains at least two images and  
    // the TreeView control contains a selected image.)  
    treeView1.SelectedNode.ImageIndex = 0;  
    treeView1.SelectedNode.SelectedImageIndex = 1;  
  
    ```  
  
    ```cpp  
    // (Assumes that imageList1 contains at least two images and  
    // the TreeView control contains a selected image.)  
    treeView1->SelectedNode->ImageIndex = 0;  
    treeView1->SelectedNode->SelectedImageIndex = 1;  
    ```  
  
## 請參閱  
 [TreeView 控制項概觀](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)   
 [如何：使用 Windows Form TreeView 控制項加入和移除節點](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)   
 [如何：逐一查看 Windows Form TreeView 控制項的所有節點](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)   
 [如何：判斷按下哪個 TreeView 節點](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)   
 [如何：將自訂資訊加入 TreeView 或 ListView 控制項 \(Windows Form\)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)