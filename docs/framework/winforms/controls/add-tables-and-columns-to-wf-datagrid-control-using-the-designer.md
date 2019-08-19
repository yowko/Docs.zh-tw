---
title: HOW TO：使用設計工具將資料表和資料行新增至 Windows Forms DataGrid 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], adding to DataGrid control
- tables [Windows Forms], adding to DataGrid control
- DataGrid control [Windows Forms], adding tables and columns
ms.assetid: 4a6d1b34-b696-476b-bf8a-57c6230aa9e1
ms.openlocfilehash: d11c4f7e4cdfb597477bb99f38612ed648849f20
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040044"
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control-using-the-designer"></a>HOW TO：使用設計工具將資料表和資料行新增至 Windows Forms DataGrid 控制項

> [!NOTE]
>           <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。 如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。

您可以藉<xref:System.Windows.Forms.DataGrid>由建立<xref:System.Windows.Forms.DataGridTableStyle>物件<xref:System.Windows.Forms.GridTableStylesCollection>並將其加入至物件 (可透過<xref:System.Windows.Forms.DataGrid>控制項的<xref:System.Windows.Forms.DataGrid.TableStyles%2A>屬性存取), 在 [資料表和資料行] 的 Windows Forms 控制項中顯示資料。 每個資料表樣式都會顯示在的<xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A>屬性<xref:System.Windows.Forms.DataGridTableStyle>中指定任何資料表的內容。 根據預設, 如果沒有指定資料行樣式的資料表樣式, 將會顯示該資料表中的所有資料行。 您可以藉<xref:System.Windows.Forms.DataGridColumnStyle>由將物件加入<xref:System.Windows.Forms.GridColumnStylesCollection>至, 以限制資料表中的哪些資料行出現, <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>其可透過每<xref:System.Windows.Forms.DataGridTableStyle>個的屬性存取。

下列程式需要具有包含<xref:System.Windows.Forms.DataGrid>控制項之表單的**Windows 應用程式**專案。 如需如何設定這類專案的相關資訊, 請[參閱如何:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project) , [以及如何:將控制項新增至](how-to-add-controls-to-windows-forms.md)Windows Forms。 根據預設, 在 Visual Studio 2005 中<xref:System.Windows.Forms.DataGrid> , 控制項不在 [**工具箱**] 中。 如需新增它的相關資訊[, 請參閱如何:將專案加入 [工具箱](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100))]。

### <a name="to-add-a-table-to-the-datagrid-control-in-the-designer"></a>若要將資料表加入至設計工具中的 DataGrid 控制項

1. 若要在資料表中顯示資料, 您必須先<xref:System.Windows.Forms.DataGrid>將控制項系結至資料集。 如需詳細資訊，請參閱[如何：使用設計](bind-wf-datagrid-control-to-a-data-source-using-the-designer.md)工具, 將 Windows Forms DataGrid 控制項系結至資料來源。

2. 在 屬性視窗中<xref:System.Windows.Forms.DataGrid.TableStyles%2A>選取![ ](./media/visual-studio-ellipsis-button.png)控制項的屬性, 然後按一下屬性旁邊的省略號按鈕 (...), 以顯示 [屬性視窗的 Visual Studio)]。 <xref:System.Windows.Forms.DataGrid>**DataGridTableStyle 集合編輯器**。

3. 在 [集合編輯器] 中, 按一下 [**加入**] 以插入資料表樣式。

4. 按一下 **[確定]** 關閉 [集合編輯器], 然後按一下<xref:System.Windows.Forms.DataGrid.TableStyles%2A>屬性旁邊的省略號按鈕, 將其重新開啟。

     當您重新開啟 [集合編輯器] 時, 系結至控制項的任何資料表都會出現在資料表樣式之<xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A>屬性的下拉式清單中。

5. 在 [集合編輯器] 的 [**成員**] 方塊中, 按一下資料表樣式。

6. 在 [集合編輯器] 的 [**屬性**] 方塊中<xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> , 選取您想要顯示之資料表的值。

### <a name="to-add-a-column-to-the-datagrid-control-in-the-designer"></a>若要將資料行加入至設計工具中的 DataGrid 控制項

1. 在 [ **DataGridTableStyle 集合編輯器**] 的 [**成員**] 方塊中, 選取適當的資料表樣式。 在 [集合編輯器] 的 [**屬性**] 方塊中<xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> , 選取集合, 然後按一下屬性旁邊的![省略號按鈕 (...), 然後再按 屬性視窗的 Visual Studio)](./media/visual-studio-ellipsis-button.png)。顯示 [ **System.windows.forms.datagridcolumnstyle> 集合編輯器**]。

2. 在 [集合編輯器] 中, 按一下 [**加入**] 以插入資料行樣式, 或按一下 [**加入**] 旁的向下箭號來指定資料行類型。

     在下拉式方塊中, 您可以選取<xref:System.Windows.Forms.DataGridTextBoxColumn>或<xref:System.Windows.Forms.DataGridBoolColumn>類型。

3. 按一下 [確定] 關閉 [ **system.windows.forms.datagridcolumnstyle> 集合編輯器**], 然後按一下<xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>屬性旁的省略號按鈕, 將其重新開啟。

     當您重新開啟 [集合編輯器] 時, 系結資料表中的任何資料行都會出現在資料行樣式之<xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A>屬性的下拉式清單中。

4. 在 [集合編輯器] 的 [**成員**] 方塊中, 按一下 [資料行] 樣式。

5. 在 [集合編輯器] 的 [**屬性**] 方塊中<xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> , 選取您想要顯示之資料行的值。

## <a name="see-also"></a>另請參閱

- [DataGrid 控制項](datagrid-control-windows-forms.md)
- [如何：刪除或隱藏 Windows Forms DataGrid 控制項中的資料行](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
