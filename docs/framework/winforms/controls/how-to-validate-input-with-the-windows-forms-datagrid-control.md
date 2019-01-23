---
title: HOW TO：使用 Windows Forms DataGrid 控制項驗證輸入
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
ms.openlocfilehash: 55de6fc1ef4fdf94495ddb07f3329ef9d46b5818
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54609482"
---
# <a name="how-to-validate-input-with-the-windows-forms-datagrid-control"></a>HOW TO：使用 Windows Forms DataGrid 控制項驗證輸入
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。 如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 有兩種類型的輸入驗證適用於 Windows Forms<xref:System.Windows.Forms.DataGrid>控制項。 如果使用者嘗試輸入的值，是無法接受的資料類型的資料格，例如整數，將字串的新無效的值會取代舊值。 這種輸入驗證會自動完成，且無法自訂。  
  
 其他類型的輸入驗證可用來拒絕任何無法接受的資料，例如必須大於或等於 1 或不適當的字串欄位中的 0 值。 這由資料集內撰寫的事件處理常式<xref:System.Data.DataTable.ColumnChanging>或<xref:System.Data.DataTable.RowChanging>事件。 以下範例使用<xref:System.Data.DataTable.ColumnChanging>事件因為無法接受的值特別允許"Product"資料行。 您可以使用<xref:System.Data.DataTable.RowChanging>檢查 [結束日期] 資料行的值晚於相同的資料列中的"Start Date"資料行的事件。  
  
### <a name="to-validate-user-input"></a>若要驗證使用者輸入  
  
1.  撰寫程式碼來處理<xref:System.Data.DataTable.ColumnChanging>適當的資料表事件。 偵測到不適當的輸入時，呼叫<xref:System.Data.DataRow.SetColumnError%2A>方法的<xref:System.Data.DataRow>物件。  
  
    ```vb  
    Private Sub Customers_ColumnChanging(ByVal sender As Object, _  
    ByVal e As System.Data.DataColumnChangeEventArgs)  
       ' Only check for errors in the Product column  
       If (e.Column.ColumnName.Equals("Product")) Then  
          ' Do not allow "Automobile" as a product.  
          If CType(e.ProposedValue, String) = "Automobile" Then  
             Dim badValue As Object = e.ProposedValue  
             e.ProposedValue = "Bad Data"  
             e.Row.RowError = "The Product column contians an error"  
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
  
2.  連接到事件的事件處理常式。  
  
     下列位置的程式碼內的形式<xref:System.Windows.Forms.Form.Load>事件或其建構函式。  
  
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
- [DataGrid 控制項](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
