---
title: HOW TO：使用設計工具以 Windows Forms TreeView 控制項新增和移除節點
ms.date: 03/30/2017
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
ms.openlocfilehash: ef3a963b5621f0b972b02a007681f600fbdb1050
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "69040069"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control-using-the-designer"></a>HOW TO：使用設計工具以 Windows Forms TreeView 控制項新增和移除節點

由於 Windows Forms <xref:System.Windows.Forms.TreeView>控制項會以階層方式顯示節點，因此當加入節點時，您必須注意其父節點為何。

下列程式需要具有包含<xref:System.Windows.Forms.TreeView>控制項之表單的**Windows 應用程式**專案。 如需設定這類專案的相關資訊， [請參閱如何：建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ， [以及如何：將控制項新增至](how-to-add-controls-to-windows-forms.md)Windows Forms。

### <a name="to-add-or-remove-nodes-in-the-designer"></a>若要在設計工具中加入或移除節點

1. 選取 <xref:System.Windows.Forms.TreeView> 控制項。

2. 在 [**屬性**] 視窗中<xref:System.Windows.Forms.TreeView.Nodes%2A> ，按一下屬性![旁邊的**省略號**（[Visual Studio](./media/visual-studio-ellipsis-button.png)的屬性視窗中的省略號按鈕（...）] 按鈕。

     [ **TreeNode 編輯器**] 隨即出現。

3. 若要加入節點，根節點必須存在;如果其中一個不存在，您必須先按一下 [**新增根**] 按鈕來新增根。 然後，您可以選取根節點或任何其他節點，然後按一下 [**新增子**系] 按鈕，以新增子節點。

4. 若要刪除節點，請選取要刪除的節點，然後按一下 [**刪除**] 按鈕。

## <a name="see-also"></a>另請參閱

- [TreeView 控制項](treeview-control-windows-forms.md)
- [TreeView 控制項概觀](treeview-control-overview-windows-forms.md)
- [如何：設定 Windows Forms TreeView 控制項的圖示](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [如何：逐一查看 Windows Forms TreeView 控制項的所有節點](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [如何：判斷按一下哪個 TreeView 節點](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [如何：將自訂資訊新增至 TreeView 或 ListView 控制項（Windows Forms）](add-custom-information-to-a-treeview-or-listview-control-wf.md)
