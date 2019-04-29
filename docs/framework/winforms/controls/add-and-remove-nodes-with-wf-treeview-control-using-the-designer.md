---
title: HOW TO：使用設計工具以 Windows Forms TreeView 控制項新增和移除節點
ms.date: 03/30/2017
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
ms.openlocfilehash: ecf0b758a9c45a0354a68b6cbfecdb1c49ab390f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61640364"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control-using-the-designer"></a>HOW TO：使用設計工具以 Windows Forms TreeView 控制項新增和移除節點
因為 Windows Form<xref:System.Windows.Forms.TreeView>控制項會顯示節點階層的方式，新增節點，您必須注意其父節點的功能時。  
  
 下列程序需要**Windows 應用程式**表單，其中包含專案<xref:System.Windows.Forms.TreeView>控制項。 如需這類專案的設定資訊，請參閱[How to:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[How to:將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-add-or-remove-nodes-in-the-designer"></a>若要新增或移除節點，在設計工具  
  
1. 選取 <xref:System.Windows.Forms.TreeView> 控制項。  
  
2. 在 [**屬性**] 視窗中，按一下**省略符號**(![VisualStudioEllipsesButton 螢幕擷取畫面](../media/vbellipsesbutton.png "vbEllipsesButton")) 下一步按鈕<xref:System.Windows.Forms.TreeView.Nodes%2A>屬性。  
  
     **TreeNode 編輯器**隨即出現。  
  
3. 若要新增節點，必須要有一個根節點;如果不存在的話，您必須先按一下 [新增根**新增根**] 按鈕。 然後您可以加入子節點選取根節點或任何其他節點，然後按一下**新增子系** 按鈕。  
  
4. 若要刪除節點，選取要刪除，然後按一下 [節點**刪除**] 按鈕。  
  
## <a name="see-also"></a>另請參閱

- [TreeView 控制項](treeview-control-windows-forms.md)
- [TreeView 控制項概觀](treeview-control-overview-windows-forms.md)
- [如何：設定 Windows Form TreeView 控制項的圖示](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [如何：逐一查看 Windows Forms TreeView 控制項的所有節點](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [如何：判斷按下哪個 TreeView 節點](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [如何：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Form)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
