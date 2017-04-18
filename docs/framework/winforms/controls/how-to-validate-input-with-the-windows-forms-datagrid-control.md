---
title: "如何：使用 Windows Form DataGrid 控制項驗證輸入 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "DataGrid 控制項 [Windows Form], 範例"
  - "DataGrid 控制項 [Windows Form], 驗證輸入"
  - "範例 [Windows Form], DataGrid 控制項"
  - "使用者輸入, 驗證"
  - "驗證, 使用者輸入"
ms.assetid: f1e9c3a0-d0a1-4893-a615-b4b0db046c63
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：使用 Windows Form DataGrid 控制項驗證輸入
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。  如需詳細資訊，請參閱 [Windows Form DataGridView 和 DataGrid 控制項之間的差異](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 對 Windows Form <xref:System.Windows.Forms.DataGrid> 控制項來說，可用的輸入驗證有兩種。  如果使用者嘗試輸入的值是屬於儲存格無法接受的資料型別，例如要整數卻輸入字串，這個新的無效值就會被舊值取代。  這種輸入驗證是自動執行且無法自訂的。  
  
 另一種輸入驗證可用來拒絕任何無法接受的資料，例如在必須大於或等於 1 的欄位中輸入的零值或是不適當的字串。  您可以在資料集中撰寫 <xref:System.Data.DataTable.ColumnChanging> 或 <xref:System.Data.DataTable.RowChanging> 事件的事件處理常式來進行驗證。  以下範例將使用 <xref:System.Data.DataTable.ColumnChanging> 事件，因為 "Product" 資料行尤其不允許無法接受的值。  您可使用 <xref:System.Data.DataTable.RowChanging> 事件來檢查同一資料列中的 "End Date" 資料行的值是否晚於 "Start Date" 資料行。  
  
### 若要驗證使用者輸入  
  
1.  寫入程式碼來為適當資料表處理 <xref:System.Data.DataTable.ColumnChanging> 事件。  當偵測到不適當的輸入時，呼叫 <xref:System.Data.DataRow> 物件的 <xref:System.Data.DataRow.SetColumnError%2A> 方法。  
  
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
  
2.  將事件處理常式連接到事件。  
  
     將以下程式碼置於表單的 <xref:System.Windows.Forms.Form.Load> 事件或其建構函式中。  
  
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
  
## 請參閱  
 <xref:System.Windows.Forms.DataGrid>   
 <xref:System.Data.DataTable.ColumnChanging>   
 <xref:System.Data.DataRow.SetColumnError%2A>   
 [DataGrid 控制項](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)