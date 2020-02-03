---
title: 使用 DataGrid 控制項驗證輸入
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid control [Windows Forms], examples
- user input [Windows Forms], validating
- examples [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], validating input
- validation [Windows Forms], user input
ms.assetid: f1e9c3a0-d0a1-4893-a615-b4b0db046c63
ms.openlocfilehash: 3958089007401d2e977c9c96f07c9196e6216596
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728293"
---
# <a name="how-to-validate-input-with-the-windows-forms-datagrid-control"></a>如何：使用 Windows Form DataGrid 控制項驗證輸入

> [!NOTE]
> <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。 如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。

有兩種類型的輸入驗證可用於 Windows Forms <xref:System.Windows.Forms.DataGrid> 控制項。 如果使用者嘗試輸入的值不是資料格可接受的資料類型，例如字串為整數，則新的無效值會取代為舊的值。 這種輸入驗證會自動完成，無法自訂。

另一種輸入驗證可用於拒絕任何無法接受的資料，例如，欄位中必須大於或等於1的0值，或不適當的字串。 這會藉由撰寫 <xref:System.Data.DataTable.ColumnChanging> 或 <xref:System.Data.DataTable.RowChanging> 事件的事件處理常式，在資料集中完成。 下列範例會使用 <xref:System.Data.DataTable.ColumnChanging> 事件，因為特定的「產品」資料行不允許接受的值。 您可以使用 <xref:System.Data.DataTable.RowChanging> 事件來檢查「結束日期」資料行的值是否晚于相同資料列中的「開始日期」資料行。

## <a name="to-validate-user-input"></a>驗證使用者輸入

1. 撰寫程式碼以處理適當資料表的 <xref:System.Data.DataTable.ColumnChanging> 事件。 當偵測到不適當的輸入時，請呼叫 <xref:System.Data.DataRow> 物件的 <xref:System.Data.DataRow.SetColumnError%2A> 方法。

    ```vb
    Private Sub Customers_ColumnChanging(ByVal sender As Object, _
    ByVal e As System.Data.DataColumnChangeEventArgs)
       ' Only check for errors in the Product column
       If (e.Column.ColumnName.Equals("Product")) Then
          ' Do not allow "Automobile" as a product.
          If CType(e.ProposedValue, String) = "Automobile" Then
             Dim badValue As Object = e.ProposedValue
             e.ProposedValue = "Bad Data"
             e.Row.RowError = "The Product column contains an error"
             e.Row.SetColumnError(e.Column, "Product cannot be " & _
             CType(badValue, String))
          End If
       End If
    End Sub
    ```

    ```csharp
    //Handle column changing events on the Customers table
    private void Customers_ColumnChanging(object sender, System.Data.DataColumnChangeEventArgs e) {

       //Only check for errors in the Product column
       if (e.Column.ColumnName.Equals("Product")) {

          //Do not allow "Automobile" as a product
          if (e.ProposedValue.Equals("Automobile")) {
             object badValue = e.ProposedValue;
             e.ProposedValue = "Bad Data";
             e.Row.RowError = "The Product column contains an error";
             e.Row.SetColumnError(e.Column, "Product cannot be " + badValue);
          }
       }
    }
    ```

2. 將事件處理常式連接到事件。

    將下列程式碼放在表單的 <xref:System.Windows.Forms.Form.Load> 事件或其函式中。

    ```vb
    ' Assumes the grid is bound to a dataset called customersDataSet1
    ' with a table called Customers.
    ' Put this code in the form's Load event or its constructor.
    AddHandler customersDataSet1.Tables("Customers").ColumnChanging, AddressOf Customers_ColumnChanging
    ```

    ```csharp
    // Assumes the grid is bound to a dataset called customersDataSet1
    // with a table called Customers.
    // Put this code in the form's Load event or its constructor.
    customersDataSet1.Tables["Customers"].ColumnChanging += new DataColumnChangeEventHandler(this.Customers_ColumnChanging);
    ```

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGrid>
- <xref:System.Data.DataTable.ColumnChanging>
- <xref:System.Data.DataRow.SetColumnError%2A>
- [DataGrid 控制項](datagrid-control-windows-forms.md)
