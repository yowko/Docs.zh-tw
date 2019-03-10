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
ms.openlocfilehash: dc8c8f157e6673c1bddc68bfb511683e6d2b99be
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720328"
---
# <a name="how-to-validate-input-with-the-windows-forms-datagrid-control"></a><span data-ttu-id="5c999-102">HOW TO：使用 Windows Forms DataGrid 控制項驗證輸入</span><span class="sxs-lookup"><span data-stu-id="5c999-102">How to: Validate Input with the Windows Forms DataGrid Control</span></span>

> [!NOTE]
> <span data-ttu-id="5c999-103">
  <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="5c999-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="5c999-104">如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="5c999-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>

<span data-ttu-id="5c999-105">有兩種類型的輸入驗證適用於 Windows Forms<xref:System.Windows.Forms.DataGrid>控制項。</span><span class="sxs-lookup"><span data-stu-id="5c999-105">There are two types of input validation available for the Windows Forms <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="5c999-106">如果使用者嘗試輸入的值，是無法接受的資料類型的資料格，例如整數，將字串的新無效的值會取代舊值。</span><span class="sxs-lookup"><span data-stu-id="5c999-106">If the user attempts to enter a value that is of an unacceptable data type for the cell, for example a string into an integer, the new invalid value is replaced with the old value.</span></span> <span data-ttu-id="5c999-107">這種輸入驗證會自動完成，且無法自訂。</span><span class="sxs-lookup"><span data-stu-id="5c999-107">This kind of input validation is done automatically and cannot be customized.</span></span>

<span data-ttu-id="5c999-108">其他類型的輸入驗證可用來拒絕任何無法接受的資料，例如必須大於或等於 1 或不適當的字串欄位中的 0 值。</span><span class="sxs-lookup"><span data-stu-id="5c999-108">The other type of input validation can be used to reject any unacceptable data, for example a 0 value in a field that must be greater than or equal to 1, or an inappropriate string.</span></span> <span data-ttu-id="5c999-109">這由資料集內撰寫的事件處理常式<xref:System.Data.DataTable.ColumnChanging>或<xref:System.Data.DataTable.RowChanging>事件。</span><span class="sxs-lookup"><span data-stu-id="5c999-109">This is done in the dataset by writing an event handler for the <xref:System.Data.DataTable.ColumnChanging> or <xref:System.Data.DataTable.RowChanging> event.</span></span> <span data-ttu-id="5c999-110">以下範例使用<xref:System.Data.DataTable.ColumnChanging>事件因為無法接受的值特別允許"Product"資料行。</span><span class="sxs-lookup"><span data-stu-id="5c999-110">The example below uses the <xref:System.Data.DataTable.ColumnChanging> event because the unacceptable value is disallowed for the "Product" column in particular.</span></span> <span data-ttu-id="5c999-111">您可以使用<xref:System.Data.DataTable.RowChanging>檢查 [結束日期] 資料行的值晚於相同的資料列中的"Start Date"資料行的事件。</span><span class="sxs-lookup"><span data-stu-id="5c999-111">You might use the <xref:System.Data.DataTable.RowChanging> event for checking that the value of an "End Date" column is later than the "Start Date" column in the same row.</span></span>

## <a name="to-validate-user-input"></a><span data-ttu-id="5c999-112">若要驗證使用者輸入</span><span class="sxs-lookup"><span data-stu-id="5c999-112">To validate user input</span></span>

1. <span data-ttu-id="5c999-113">撰寫程式碼來處理<xref:System.Data.DataTable.ColumnChanging>適當的資料表事件。</span><span class="sxs-lookup"><span data-stu-id="5c999-113">Write code to handle the <xref:System.Data.DataTable.ColumnChanging> event for the appropriate table.</span></span> <span data-ttu-id="5c999-114">偵測到不適當的輸入時，呼叫<xref:System.Data.DataRow.SetColumnError%2A>方法的<xref:System.Data.DataRow>物件。</span><span class="sxs-lookup"><span data-stu-id="5c999-114">When inappropriate input is detected, call the <xref:System.Data.DataRow.SetColumnError%2A> method of the <xref:System.Data.DataRow> object.</span></span>

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

2. <span data-ttu-id="5c999-115">連接到事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="5c999-115">Connect the event handler to the event.</span></span>

    <span data-ttu-id="5c999-116">下列位置的程式碼內的形式<xref:System.Windows.Forms.Form.Load>事件或其建構函式。</span><span class="sxs-lookup"><span data-stu-id="5c999-116">Place the following code within either the form's <xref:System.Windows.Forms.Form.Load> event or its constructor.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="5c999-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c999-117">See also</span></span>

- <xref:System.Windows.Forms.DataGrid>
- <xref:System.Data.DataTable.ColumnChanging>
- <xref:System.Data.DataRow.SetColumnError%2A>
- [<span data-ttu-id="5c999-118">DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="5c999-118">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
