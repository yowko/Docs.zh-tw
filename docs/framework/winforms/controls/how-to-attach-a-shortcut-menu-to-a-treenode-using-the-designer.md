---
title: 如何：使用設計工具將捷徑功能表附加至 TreeNode
ms.date: 03/30/2017
helpviewer_keywords:
- shortcut menus [Windows Forms], attaching to TreeNodes
- TreeNode [Windows Forms], attaching a shortcut menu using Designer
ms.assetid: 8e45e184-1313-4f8f-90ff-2cd5789b2268
ms.openlocfilehash: 77c4b01100aec2df16d5eb844f73f7a2bfa115aa
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43785413"
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treenode-using-the-designer"></a>如何：使用設計工具將捷徑功能表附加至 TreeNode
Windows Form<xref:System.Windows.Forms.TreeView>控制項顯示的節點，類似於檔案和資料夾顯示在 Windows 作業系統中 Windows 檔案總管功能左窗格中的階層。 藉由設定<xref:System.Windows.Forms.Control.ContextMenuStrip%2A>屬性，您可以向使用者提供即時線上作業，當他們以滑鼠右鍵按一下<xref:System.Windows.Forms.TreeView>控制項。 產生關聯<xref:System.Windows.Forms.ContextMenuStrip>元件的個別<xref:System.Windows.Forms.TreeNode>項目，您可以加入自訂的層級的快顯功能表功能，以您<xref:System.Windows.Forms.TreeView>控制項。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-associate-a-shortcut-menu-with-a-treenode-at-design-time"></a>在設計階段相關聯的樹狀結構節點的捷徑功能表  
  
1.  新增<xref:System.Windows.Forms.TreeView>控制項至表單，並再將節點加入到<xref:System.Windows.Forms.TreeView>視。 如需詳細資訊，請參閱 <<c0> [ 如何： 新增和移除節點，而在 Windows Form TreeView 控制項](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)。  
  
2.  新增<xref:System.Windows.Forms.ContextMenuStrip>元件至表單，然後加入代表您想要在執行階段提供節點層級作業的捷徑功能表中的功能表項目。 如需詳細資訊，請參閱 <<c0> [ 如何： 將功能表項目加入 ContextMenuStrip](../../../../docs/framework/winforms/controls/how-to-add-menu-items-to-a-contextmenustrip.md)。  
  
3.  重新開啟**TreeNodeEditor**  對話方塊<xref:System.Windows.Forms.TreeView>控制項，選取該節點來編輯，並設定其<xref:System.Windows.Forms.ContextMenuStrip>屬性，以您所新增的捷徑功能表。  
  
4.  當設定這個屬性時，當您以滑鼠右鍵按一下節點時將顯示快顯功能表。  
  
     此外，您會想要撰寫程式碼來處理<xref:System.Windows.Forms.ToolStripItem.Click>事件的這些功能表項目。  
  
## <a name="see-also"></a>另請參閱  
 [TreeView 控制項](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [TreeView 控制項概觀](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)  
 [ContextMenuStrip 控制項](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)
