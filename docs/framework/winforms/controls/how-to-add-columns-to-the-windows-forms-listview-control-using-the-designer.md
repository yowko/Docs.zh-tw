---
title: 使用設計工具將資料行新增至 ListView 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
ms.assetid: 5b1a8b4d-587e-479a-95c1-f9b90884f13a
ms.openlocfilehash: 627f8627aac861877a05c13def07427199807754
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744613"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control-using-the-designer"></a>如何：使用設計工具在 Windows Form ListView 控制項中加入資料行

在**詳細資料**視圖中，Windows Forms <xref:System.Windows.Forms.ListView> 控制項可以顯示每個清單專案的多個欄位。 您可以使用這些資料行顯示每個清單專案的數種類型資訊。 例如，檔案清單可以顯示檔案上次修改的檔案名、檔案類型、大小和日期。 如需建立資料行的相關資訊，請參閱[如何：在具有 Windows Forms ListView 控制項的資料行中顯示](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)子工作。

下列程式需要具有包含 <xref:System.Windows.Forms.ListView> 控制項之表單的**Windows 應用程式**專案。 如需設定這類專案的相關資訊，請參閱[如何：建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[如何：將控制項加入至 Windows Forms](how-to-add-controls-to-windows-forms.md)。

### <a name="to-add-columns-in-the-designer"></a>若要在設計工具中加入資料行

1. 在 [**屬性**] 視窗中，將控制項的 [<xref:System.Windows.Forms.ListView.View%2A>] 屬性設定為 [<xref:System.Windows.Forms.View.Details>]。

2. 在 [**屬性**] 視窗中，按一下 [<xref:System.Windows.Forms.ListView.Columns%2A>] 屬性旁邊的**省略號**按鈕（![Visual Studio.](./media/visual-studio-ellipsis-button.png)）屬性視窗中的省略號按鈕（...）。

     [ **ColumnHeader 集合編輯器**] 隨即出現。

3. 使用 [**加入**] 按鈕來加入新的資料行。 然後，您可以選取資料行標頭，並設定其文字（欄的標題）、文字對齊和寬度。

## <a name="see-also"></a>另請參閱

- [ListView 控制項概觀](listview-control-overview-windows-forms.md)
- [操作說明：使用 Windows Forms ListView 控制項加入和移除項目](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [操作說明：使用 Windows Forms ListView 控制項以資料行顯示子項目](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [操作說明：顯示 Windows Forms ListView 控制項的圖示](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [操作說明：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
