---
title: 作法：使用設計工具以 Windows Forms ListView 控制項新增和移除項目
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], populating
- ListView control [Windows Forms], adding list items
ms.assetid: 217611ee-fd11-4d39-9a54-a37c3e781be1
ms.openlocfilehash: 62665746ea9fcd1553717b02b1f1349dc6415ab2
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040091"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control-using-the-designer"></a>作法：使用設計工具以 Windows Forms ListView 控制項新增和移除項目

將專案加入至 Windows Forms <xref:System.Windows.Forms.ListView>控制項的程式主要是由指定專案並指派屬性給它。 您可以隨時完成新增或移除清單專案。

下列程式需要具有包含<xref:System.Windows.Forms.ListView>控制項之表單的**Windows 應用程式**專案。 如需設定這類專案的相關資訊, [請參閱如何:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project) , [以及如何:將控制項新增至](how-to-add-controls-to-windows-forms.md)Windows Forms。

### <a name="to-add-or-remove-items-using-the-designer"></a>若要使用設計工具加入或移除專案

1. 選取 <xref:System.Windows.Forms.ListView> 控制項。

2. 在 [**屬性**] 視窗中<xref:System.Windows.Forms.ListView.Items%2A> , 按一下屬性![旁邊的**省略號**([Visual Studio](./media/visual-studio-ellipsis-button.png)的屬性視窗中的省略號按鈕 (...)] 按鈕。

     [ **ListViewItem 集合編輯器**] 隨即出現。

3. 若要新增專案, 請按一下 [**新增**] 按鈕。 接著, 您可以設定新專案的屬性, 例如<xref:System.Windows.Forms.ListView.Text%2A>和<xref:System.Windows.Forms.ListViewItem.ImageIndex%2A>屬性。

4. 若要移除專案, 請選取它, 然後按一下 [**移除**] 按鈕。

## <a name="see-also"></a>另請參閱

- [ListView 控制項概觀](listview-control-overview-windows-forms.md)
- [如何：將資料行新增至 Windows Forms ListView 控制項](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [如何：在具有 Windows Forms ListView 控制項的資料行中顯示子項](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [如何：顯示 Windows Forms ListView 控制項的圖示](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [如何：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [如何：Windows Forms ListView 控制項中的群組專案](how-to-group-items-in-a-windows-forms-listview-control.md)
