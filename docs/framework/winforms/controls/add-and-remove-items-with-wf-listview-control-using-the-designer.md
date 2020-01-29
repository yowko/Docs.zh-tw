---
title: 使用設計工具在 ListView 控制項中新增和移除專案
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], populating
- ListView control [Windows Forms], adding list items
ms.assetid: 217611ee-fd11-4d39-9a54-a37c3e781be1
ms.openlocfilehash: cab40c556d9e5d21ce15bcd3d4da367bc08f33ab
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732304"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control-using-the-designer"></a>如何：使用設計工具搭配 Windows Form ListView 控制項加入和移除項目

將專案加入至 Windows Forms <xref:System.Windows.Forms.ListView> 控制項的程式主要是由指定專案，並為其指派屬性。 您可以隨時完成新增或移除清單專案。

下列程式需要具有包含 <xref:System.Windows.Forms.ListView> 控制項之表單的**Windows 應用程式**專案。 如需設定這類專案的相關資訊，請參閱[如何：建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[如何：將控制項加入至 Windows Forms](how-to-add-controls-to-windows-forms.md)。

### <a name="to-add-or-remove-items-using-the-designer"></a>若要使用設計工具加入或移除專案

1. 選取 <xref:System.Windows.Forms.ListView> 控制項。

2. 在 **屬性** 視窗中<xref:System.Windows.Forms.ListView.Items%2A> ，按一下屬性 (![旁邊的**省略號**Visual Studio](./media/visual-studio-ellipsis-button.png)) 的屬性視窗中的省略號按鈕（...） 按鈕。

     [ **ListViewItem 集合編輯器**] 隨即出現。

3. 若要新增專案，請按一下 [**新增**] 按鈕。 接著，您可以設定新專案的屬性，例如 [<xref:System.Windows.Forms.ListView.Text%2A>] 和 [<xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> 屬性]。

4. 若要移除專案，請選取它，然後按一下 [**移除**] 按鈕。

## <a name="see-also"></a>請參閱

- [ListView 控制項概觀](listview-control-overview-windows-forms.md)
- [操作說明：將資料行加入至 Windows Forms ListView 控制項](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [操作說明：使用 Windows Forms ListView 控制項以資料行顯示子項目](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [操作說明：顯示 Windows Forms ListView 控制項的圖示](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [操作說明：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [操作說明：在 Windows Forms ListView 控制項中群組項目](how-to-group-items-in-a-windows-forms-listview-control.md)
