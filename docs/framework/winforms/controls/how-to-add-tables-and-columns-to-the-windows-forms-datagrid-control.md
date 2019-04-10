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
ms.openlocfilehash: 55a8d28d04dd05d4dba7ab2b1edbcfbcce97cecb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222038"
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control"></a>HOW TO：將資料表和資料行新增至 Windows Forms DataGrid 控制項
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。 如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 您可以在 Windows Form 中顯示資料<xref:System.Windows.Forms.DataGrid>中資料表和資料行，藉由建立控制項**Styl**物件，並將它們加入至**您**物件，也就是經由<xref:System.Windows.Forms.DataGrid>控制項的**Tablestyle**屬性。 每個資料表樣式會顯示任何資料表中指定的內容**Styl**物件的**MappingName**屬性。 根據預設，任何指定的資料行樣式的資料表樣式會顯示資料的資料表內的所有資料行。 您可以限制哪些資料行從資料表顯示加上**DataGridColumnStyle**物件至**GridColumnStylesCollection**物件，這透過存取**GridColumnStyles**屬性的每個**Styl**物件。  
  
### <a name="to-add-a-table-and-column-to-a-datagrid-programmatically"></a>若要以程式設計方式將資料表和資料行加入到資料格  
  
1.  若要顯示資料表中的資料，您必須先繫結<xref:System.Windows.Forms.DataGrid>資料集的控制項。 如需詳細資訊，請參閱[如何：將 Windows Forms DataGrid 控制項繫結至資料來源](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)。  
  
    > [!CAUTION]
    >  時以程式設計方式指定資料行樣式，一定要建立**DataGridColumnStyle**物件，並將其新增至**GridColumnStylesCollection**物件，然後再加入**Styl**物件至**您**物件。 當您將加入空**Styl**物件加入至集合， **DataGridColumnStyle**自動為您產生的物件。 因此，將會擲回例外狀況如果您嘗試加入新**DataGridColumnStyle**物件具有重複**MappingName**值**GridColumnStylesCollection**物件。  
  
2.  宣告新的表格樣式，並將它對應的名稱。  
  
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
  
3.  宣告新的資料行樣式，並設定其對應的名稱和其他屬性。  
  
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
  
4.  呼叫**新增**方法**GridColumnStylesCollection**將資料行加入資料表樣式的物件  
  
    ```vb  
    ts1.GridColumnStyles.Add(myDataCol)  
    ```  
  
    ```csharp  
    ts1.GridColumnStyles.Add(myDataCol);  
    ```  
  
    ```cpp  
    ts1->GridColumnStyles->Add(myDataCol);  
    ```  
  
5.  呼叫**新增**方法**您**將資料表樣式加入至資料格的物件。  
  
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
- [HOW TO：刪除或隱藏 Windows Forms DataGrid 控制項中的資料行](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
