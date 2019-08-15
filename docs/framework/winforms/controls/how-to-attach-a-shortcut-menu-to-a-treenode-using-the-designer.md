---
title: 作法：使用設計工具將捷徑功能表附加至 TreeNode
ms.date: 03/30/2017
helpviewer_keywords:
- shortcut menus [Windows Forms], attaching to TreeNodes
- TreeNode [Windows Forms], attaching a shortcut menu using Designer
ms.assetid: 8e45e184-1313-4f8f-90ff-2cd5789b2268
ms.openlocfilehash: eb3240d35309e03aa8ce949b9c5000f8581d2c2f
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040451"
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treenode-using-the-designer"></a>作法：使用設計工具將捷徑功能表附加至 TreeNode
[Windows Forms <xref:System.Windows.Forms.TreeView> ] 控制項會顯示節點的階層, 類似于 windows 作業系統中 windows Explorer 功能的左窗格中顯示的檔案和資料夾。 藉由設定<xref:System.Windows.Forms.Control.ContextMenuStrip%2A>屬性, 您可以在使用者以滑鼠右鍵<xref:System.Windows.Forms.TreeView>按一下控制項時, 提供內容相關的作業。 藉由建立<xref:System.Windows.Forms.ContextMenuStrip>元件與個別<xref:System.Windows.Forms.TreeNode>專案的關聯, 您可以在<xref:System.Windows.Forms.TreeView>控制項中加入自訂的快捷方式功能表功能層級。

## <a name="to-associate-a-shortcut-menu-with-a-treenode-at-design-time"></a>在設計階段將快捷方式功能表與 TreeNode 產生關聯

1. 將控制項新增至表單, 然後<xref:System.Windows.Forms.TreeView>視需要將節點加入至。 <xref:System.Windows.Forms.TreeView> 如需詳細資訊，請參閱[如何：使用 Windows Forms TreeView 控制項](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)加入和移除節點。

2. <xref:System.Windows.Forms.ContextMenuStrip>將元件加入至表單, 然後將功能表項目加入至快捷方式功能表, 表示您想要在執行時間提供的節點層級作業。 如需詳細資訊，請參閱[如何：將功能表項目新增至 CoNtextMenuStrip](how-to-add-menu-items-to-a-contextmenustrip.md)。

3. 重新開啟 <xref:System.Windows.Forms.TreeView>控制項的 [TreeNodeEditor] 對話方塊, 選取要編輯的節點, 並將其<xref:System.Windows.Forms.ContextMenuStrip>屬性設定為您加入的快捷方式功能表。

4. 設定此屬性時, 當您以滑鼠右鍵按一下節點時, 將會顯示快捷方式功能表。

     此外, 您也會想要撰寫程式碼來<xref:System.Windows.Forms.ToolStripItem.Click>處理這些功能表項目的事件。

## <a name="see-also"></a>另請參閱

- [TreeView 控制項](treeview-control-windows-forms.md)
- [TreeView 控制項概觀](treeview-control-overview-windows-forms.md)
- [ContextMenuStrip 控制項](contextmenustrip-control.md)
