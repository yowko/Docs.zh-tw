---
title: HOW TO：設定 Windows Forms TreeView 控制項的圖示
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
ms.openlocfilehash: 12b8354890f0ba613b35615dc5cf3a5b3555e7ca
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097615"
---
# <a name="how-to-set-icons-for-the-windows-forms-treeview-control"></a>HOW TO：設定 Windows Forms TreeView 控制項的圖示
Windows Form<xref:System.Windows.Forms.TreeView>控制項可以顯示每個節點旁邊的圖示。 圖示位於節點文字的左邊。 若要顯示這些圖示，您必須建立關聯的樹狀檢視<xref:System.Windows.Forms.ImageList>控制項。 如需有關影像清單的詳細資訊，請參閱[ImageList 元件](imagelist-component-windows-forms.md)和[How to:新增或移除映像的 Windows Form ImageList 元件](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)。  
  
> [!NOTE]
>  Microsoft.NET Framework 1.1 版中的錯誤可防止映像上出現<xref:System.Windows.Forms.TreeView>節點，當您的應用程式呼叫<xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>。 若要解決這個錯誤，請呼叫<xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType>在您`Main`方法呼叫之後立即<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>。 已經修正這個錯誤[!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)]。  
  
### <a name="to-display-images-in-a-tree-view"></a>若要在樹狀檢視中顯示影像  
  
1.  設定<xref:System.Windows.Forms.TreeView>控制項的<xref:System.Windows.Forms.TreeView.ImageList%2A>屬性，以現有<xref:System.Windows.Forms.ImageList>您想要使用的控制項。  
  
     在設計工具中使用 [屬性] 視窗中，或在程式碼，可以設定這些屬性。  
  
    ```vb  
    TreeView1.ImageList = ImageList1  
    ```  
  
    ```csharp  
    treeView1.ImageList = imageList1;  
    ```  
  
    ```cpp  
    treeView1->ImageList = imageList1;  
    ```  
  
2.  將節點的設定<xref:System.Windows.Forms.TreeNode.ImageIndex%2A>和<xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A>屬性。 <xref:System.Windows.Forms.TreeNode.ImageIndex%2A>屬性會決定節點的一般或展開狀態，所顯示的影像和<xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A>屬性決定節點的選取狀態顯示的影像。  
  
     在程式碼，或在 TreeNode 編輯器內，可以設定這些屬性。 若要開啟 TreeNode 編輯器，請按一下 [省略符號按鈕 ( ![VisualStudioEllipsesButton 螢幕擷取畫面](../media/vbellipsesbutton.png "vbEllipsesButton")) 旁<xref:System.Windows.Forms.TreeView.Nodes%2A>屬性] 視窗上的屬性。  
  
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
- [HOW TO：使用 Windows Forms TreeView 控制項新增和移除節點](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [HOW TO：逐一查看 Windows Forms TreeView 控制項的所有節點](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [HOW TO：判斷按下了哪個 TreeView 節點](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [HOW TO：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
