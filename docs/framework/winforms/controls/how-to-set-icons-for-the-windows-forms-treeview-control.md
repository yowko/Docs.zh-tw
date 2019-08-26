---
title: 作法：設定 Windows Forms TreeView 控制項的圖示
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
ms.openlocfilehash: 451f9ab2b35ad1fbbe9401dacbc8aab44e302701
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69909801"
---
# <a name="how-to-set-icons-for-the-windows-forms-treeview-control"></a>HOW TO：設定 Windows Forms TreeView 控制項的圖示
Windows Forms <xref:System.Windows.Forms.TreeView>控制項可以顯示每個節點旁邊的圖示。 圖示會定位於節點文字的直接左側。 若要顯示這些圖示, 您必須將樹狀檢視與控制項<xref:System.Windows.Forms.ImageList>產生關聯。 如需影像清單的詳細資訊, 請參閱[ImageList 元件](imagelist-component-windows-forms.md)和[如何:使用 Windows Forms ImageList 元件](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)來新增或移除映射。  
  
> [!NOTE]
> Microsoft .NET Framework 版本1.1 中的錯誤, 可防止在您<xref:System.Windows.Forms.TreeView>的應用程式呼叫<xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>時, 在節點上顯示影像。 若要解決這個錯誤, 請<xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> `Main`在呼叫<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>之後立即呼叫方法中的。 此 bug 在 .NET Framework 2.0 中已修正。  
  
### <a name="to-display-images-in-a-tree-view"></a>若要在樹狀檢視中顯示影像  
  
1. 將控制項的<xref:System.Windows.Forms.TreeView.ImageList%2A>屬性設為您想<xref:System.Windows.Forms.ImageList>要使用的現有控制項。 <xref:System.Windows.Forms.TreeView>  
  
     這些屬性可以在設計工具中, 使用屬性視窗或程式碼來設定。  
  
    ```vb  
    TreeView1.ImageList = ImageList1  
    ```  
  
    ```csharp  
    treeView1.ImageList = imageList1;  
    ```  
  
    ```cpp  
    treeView1->ImageList = imageList1;  
    ```  
  
2. 設定節點的<xref:System.Windows.Forms.TreeNode.ImageIndex%2A>和<xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A>屬性。 屬性會決定針對節點的正常和擴充狀態顯示的影像, <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A>而屬性會決定針對節點所選取狀態顯示的影像。 <xref:System.Windows.Forms.TreeNode.ImageIndex%2A>  
  
     這些屬性可以在程式碼中設定, 或在 TreeNode 編輯器中設定。 若要開啟 [TreeNode 編輯器], 請按一下 ![屬性視窗上<xref:System.Windows.Forms.TreeView.Nodes%2A>屬性旁邊的省略號按鈕 (](./media/visual-studio-ellipsis-button.png)Visual Studio 的屬性視窗中的省略號按鈕 (...)。  
  
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
  
## <a name="see-also"></a>另請參閱

- [TreeView 控制項概觀](treeview-control-overview-windows-forms.md)
- [如何：使用 Windows Forms TreeView 控制項加入和移除節點](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [如何：逐一查看 Windows Forms TreeView 控制項的所有節點](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [如何：判斷按一下哪個 TreeView 節點](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [如何：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
