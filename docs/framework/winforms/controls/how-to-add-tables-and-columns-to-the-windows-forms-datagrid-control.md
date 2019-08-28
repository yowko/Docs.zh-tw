---
title: HOW TO：將資料表和資料行新增至 Windows Forms DataGrid 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- columns [Windows Forms], adding to DataGrid control
- tables [Windows Forms], adding to DataGrid control
- DataGrid control [Windows Forms], adding tables and columns
ms.assetid: 2fe661b9-aa06-49b9-a314-a0d3cbfdcb4d
ms.openlocfilehash: bfb0296566fecc2029df16d91c9c04d7daa4b4b5
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046160"
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control"></a>作法：將資料表和資料行新增至 Windows Forms DataGrid 控制項

> [!NOTE]
> <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。 如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。

您可以藉由建立**DataGridTableStyle**物件<xref:System.Windows.Forms.DataGrid>並將其加入至**system.windows.forms.gridtablestylescollection>** 物件<xref:System.Windows.Forms.DataGrid> , 以在 [資料表和資料行] 的 [Windows Forms] 控制項中顯示資料, 這是透過控制項的**System.windows.forms.datagrid.tablestyles**屬性。 每個資料表樣式都會顯示在**DataGridTableStyle**物件的**MappingName**屬性中指定之任何資料表的內容。 根據預設, 未指定資料行樣式的資料表樣式, 將會顯示該資料表中的所有資料行。 您可以藉由將**system.windows.forms.datagridcolumnstyle>** 物件新增至**system.windows.forms.gridcolumnstylescollection>** 物件 (透過每個**DataGridTableStyle**的**system.windows.forms.datagridtablestyle.gridcolumnstyles**屬性來存取), 來限制資料表中的哪些資料行出現。目標.

### <a name="to-add-a-table-and-column-to-a-datagrid-programmatically"></a>以程式設計方式將資料表和資料行加入至 DataGrid

1. 若要在資料表中顯示資料, 您必須先<xref:System.Windows.Forms.DataGrid>將控制項系結至資料集。 如需詳細資訊，請參閱[如何：將 Windows Forms DataGrid 控制項系結至資料來源](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)。

    > [!CAUTION]
    > 以程式設計方式指定資料行樣式時, 請一律先建立**system.windows.forms.datagridcolumnstyle>** 物件, 並將其加入至**system.windows.forms.gridcolumnstylescollection>** 物件, 然後再將**DataGridTableStyle**物件新增至**System.windows.forms.gridtablestylescollection>** 物件。 當您將空的**DataGridTableStyle**物件新增至集合時, 系統會自動為您產生**system.windows.forms.datagridcolumnstyle>** 物件。 因此, 如果您嘗試將具有重複**MappingName**值的新**System.windows.forms.datagridcolumnstyle>** 物件加入**system.windows.forms.gridcolumnstylescollection>** 物件, 則會擲回例外狀況。

2. 宣告新的資料表樣式, 並設定其對應名稱。

    ```vb
    Dim ts1 As New DataGridTableStyle()
    ts1.MappingName = "Customers"
    ```

    ```csharp
    DataGridTableStyle ts1 = new DataGridTableStyle();
    ts1.MappingName = "Customers";
    ```

    ```cpp
    DataGridTableStyle* ts1 = new DataGridTableStyle();
    ts1->MappingName = S"Customers";
    ```

3. 宣告新的資料行樣式, 並設定其對應名稱和其他屬性。

    ```vb
    Dim myDataCol As New DataGridBoolColumn()
    myDataCol.HeaderText = "My New Column"
    myDataCol.MappingName = "Current"
    ```

    ```csharp
    DataGridBoolColumn myDataCol = new DataGridBoolColumn();
    myDataCol.HeaderText = "My New Column";
    myDataCol.MappingName = "Current";
    ```

    ```cpp
    DataGridBoolColumn^ myDataCol = gcnew DataGridBoolColumn();
    myDataCol->HeaderText = "My New Column";
    myDataCol->MappingName = "Current";
    ```

4. 呼叫**system.windows.forms.gridcolumnstylescollection>** 物件的**add**方法, 將該資料行加入至資料表樣式

    ```vb
    ts1.GridColumnStyles.Add(myDataCol)
    ```

    ```csharp
    ts1.GridColumnStyles.Add(myDataCol);
    ```

    ```cpp
    ts1->GridColumnStyles->Add(myDataCol);
    ```

5. 呼叫**system.windows.forms.gridtablestylescollection>** 物件的**add**方法, 將資料表樣式加入至資料方格。

    ```vb
    DataGrid1.TableStyles.Add(ts1)
    ```

    ```csharp
    dataGrid1.TableStyles.Add(ts1);
    ```

    ```cpp
    dataGrid1->TableStyles->Add(ts1);
    ```

## <a name="see-also"></a>另請參閱

- [DataGrid 控制項](datagrid-control-windows-forms.md)
- [如何：刪除或隱藏 Windows Forms DataGrid 控制項中的資料行](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
