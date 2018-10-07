---
title: TreeView 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- TreeView
helpviewer_keywords:
- TreeView control [Windows Forms], about TreeView control
ms.assetid: 0ece823a-9508-478a-bbdb-7d7c3bae51d5
ms.openlocfilehash: cc3fb394a2c55b7095a8111e7018b754985ab0e1
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2018
ms.locfileid: "48839030"
---
# <a name="treeview-control-overview-windows-forms"></a>TreeView 控制項概觀 (Windows Form)

使用 Windows Form <xref:System.Windows.Forms.TreeView> 控制項，您可以向使用者顯示節點階層，就像 Windows 作業系統中 Windows 檔案總管功能左窗格顯示檔案和資料夾的方式。 樹狀檢視中的每個節點都可能包含其他節點，稱為*子節點*。 您可以顯示父節點或包含子節點的節點為展開或摺疊。 您也可以藉由設定樹狀檢視的 <xref:System.Windows.Forms.TreeView.CheckBoxes%2A> 屬性為 `true`來顯示節點旁邊核取方塊的樹狀檢視。 藉由設定節點的 <xref:System.Windows.Forms.TreeNode.Checked%2A> 屬性為 `true` 或 `false`，您可以程式設計的方式選取或清除節點。

## <a name="key-properties"></a>主要屬性

<xref:System.Windows.Forms.TreeView> 控制項的索引鍵屬性為 <xref:System.Windows.Forms.TreeView.Nodes%2A> 和 <xref:System.Windows.Forms.TreeView.SelectedNode%2A>。 <xref:System.Windows.Forms.TreeView.Nodes%2A> 屬性包含樹狀檢視中最上層節點的清單。 <xref:System.Windows.Forms.TreeView.SelectedNode%2A> 屬性會設定目前選取的節點。 您可以在節點旁邊顯示圖示。 此控制項會使用來自樹狀檢視的 <xref:System.Windows.Forms.TreeView.ImageList%2A> 屬性中命名的 <xref:System.Windows.Forms.ImageList> 影像。 <xref:System.Windows.Forms.TreeView.ImageIndex%2A> 屬性會設定樹狀檢視節點中的預設影像。 如需有關顯示影像的詳細資訊，請參閱 <<c0> [ 如何： 設定 Windows Forms TreeView 控制項的圖示](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md)。 如果您使用 Visual Studio 2005，您可以存取您可以搭配使用的標準映像的大型程式庫<xref:System.Windows.Forms.TreeView>控制項。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.TreeView>
- [TreeView 控制項](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)
- [操作說明：設定 Windows Forms TreeView 控制項的圖示](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [操作說明：使用 Windows Forms TreeView 控制項加入和移除節點](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [操作說明：逐一查看 Windows Forms TreeView 控制項的所有節點](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [操作說明：判斷按下哪個 TreeView 節點](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [操作說明：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)