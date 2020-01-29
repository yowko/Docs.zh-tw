---
title: 設定 TreeView 控制項的圖示
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], node icons
- ImageList component [Windows Forms], adding images
- icons [Windows Forms], setting for TreeView control
- tree nodes in TreeView control [Windows Forms], icons
ms.assetid: c14ddcc0-e5a6-4c21-a2d5-6799fd491781
ms.openlocfilehash: e3d7fc35c6d9f70822cdd0b69dd12f3d469f4ffa
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737259"
---
# <a name="how-to-set-icons-for-the-windows-forms-treeview-control"></a>如何：設定 Windows Form TreeView 控制項的圖示
Windows Forms <xref:System.Windows.Forms.TreeView> 控制項可以顯示每個節點旁邊的圖示。 圖示會定位於節點文字的直接左側。 若要顯示這些圖示，您必須將樹狀檢視與 <xref:System.Windows.Forms.ImageList> 控制項產生關聯。 如需影像清單的詳細資訊，請參閱[ImageList 元件](imagelist-component-windows-forms.md)和[如何：使用 Windows Forms ImageList 元件來新增或移除影像](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)。  
  
> [!NOTE]
> Microsoft .NET Framework 版本1.1 中的錯誤，可防止當您的應用程式呼叫 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>時，影像會出現在 <xref:System.Windows.Forms.TreeView> 節點上。 若要解決這個錯誤，請在呼叫 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>之後立即呼叫 `Main` 方法中的 <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType>。 此 bug 在 .NET Framework 2.0 中已修正。  
  
### <a name="to-display-images-in-a-tree-view"></a>若要在樹狀檢視中顯示影像  
  
1. 將 <xref:System.Windows.Forms.TreeView> 控制項的 <xref:System.Windows.Forms.TreeView.ImageList%2A> 屬性設定為您想要使用的現有 <xref:System.Windows.Forms.ImageList> 控制項。  
  
     這些屬性可以在設計工具中，使用屬性視窗或程式碼來設定。  
  
    ```vb  
    TreeView1.ImageList = ImageList1  
    ```  
  
    ```csharp  
    treeView1.ImageList = imageList1;  
    ```  
  
    ```cpp  
    treeView1->ImageList = imageList1;  
    ```  
  
2. 設定節點的 <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> 和 <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> 屬性。 [<xref:System.Windows.Forms.TreeNode.ImageIndex%2A>] 屬性會決定節點的正常和已展開狀態所顯示的影像，而 [<xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A>] 屬性會決定針對節點所選取狀態顯示的影像。  
  
     這些屬性可以在程式碼中設定，或在 TreeNode 編輯器中設定。 若要開啟 [TreeNode 編輯器]，請按一下 [<xref:System.Windows.Forms.TreeView.Nodes%2A>] 上 [屬性視窗] 屬性旁邊的省略號按鈕（![Visual Studio.](./media/visual-studio-ellipsis-button.png)屬性視窗中的省略號按鈕（...）。  
  
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
  
## <a name="see-also"></a>請參閱

- [TreeView 控制項概觀](treeview-control-overview-windows-forms.md)
- [操作說明：使用 Windows Forms TreeView 控制項加入和移除節點](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [操作說明：逐一查看 Windows Forms TreeView 控制項的所有節點](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [操作說明：判斷按下哪個 TreeView 節點](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [操作說明：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
