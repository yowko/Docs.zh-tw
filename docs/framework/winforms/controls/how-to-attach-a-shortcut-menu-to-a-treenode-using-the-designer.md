---
title: 如何：使用設計工具將捷徑功能表附加至 TreeNode
ms.date: 03/30/2017
helpviewer_keywords:
- shortcut menus [Windows Forms], attaching to TreeNodes
- TreeNode [Windows Forms], attaching a shortcut menu using Designer
ms.assetid: 8e45e184-1313-4f8f-90ff-2cd5789b2268
ms.openlocfilehash: 2700be06ceb4c20926d6af9c962799db4afc31da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treenode-using-the-designer"></a>如何：使用設計工具將捷徑功能表附加至 TreeNode
Windows Form<xref:System.Windows.Forms.TreeView>控制項會顯示節點階層，類似於檔案和資料夾顯示在 Windows 作業系統中 Windows 檔案總管功能左窗格中。 藉由設定<xref:System.Windows.Forms.Control.ContextMenuStrip%2A>屬性，您可以向使用者提供即時線上作業，當它們以滑鼠右鍵按一下<xref:System.Windows.Forms.TreeView>控制項。 透過建立關聯<xref:System.Windows.Forms.ContextMenuStrip>具有個別元件<xref:System.Windows.Forms.TreeNode>項目，您可以加入自訂層級的快顯功能表功能，以您<xref:System.Windows.Forms.TreeView>控制項。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-associate-a-shortcut-menu-with-a-treenode-at-design-time"></a>在設計階段與 TreeNode 的捷徑功能表  
  
1.  新增<xref:System.Windows.Forms.TreeView>控制項加入表單，並再將節點加入<xref:System.Windows.Forms.TreeView>視。 如需詳細資訊，請參閱[如何： 新增和移除節點與 Windows Form TreeView 控制項](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)。  
  
2.  新增<xref:System.Windows.Forms.ContextMenuStrip>元件加入至表單，然後將功能表項目新增至代表您想要在執行階段提供節點層級作業的捷徑功能表。 如需詳細資訊，請參閱[How to： 將功能表項目加入 ContextMenuStrip](../../../../docs/framework/winforms/controls/how-to-add-menu-items-to-a-contextmenustrip.md)。  
  
3.  重新開啟**TreeNodeEditor**對話方塊的 <xref:System.Windows.Forms.TreeView>控制，請選取該節點來編輯，並設定其<xref:System.Windows.Forms.ContextMenuStrip>您新增的快顯功能表的屬性。  
  
4.  當設定這個屬性時，當您以滑鼠右鍵按一下節點將顯示的捷徑功能表。  
  
     此外，您會想要撰寫程式碼以處理<xref:System.Windows.Forms.ToolStripItem.Click>事件的這些功能表項目。  
  
## <a name="see-also"></a>另請參閱  
 [TreeView 控制項](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [TreeView 控制項概觀](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)  
 [ContextMenuStrip 控制項](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)
