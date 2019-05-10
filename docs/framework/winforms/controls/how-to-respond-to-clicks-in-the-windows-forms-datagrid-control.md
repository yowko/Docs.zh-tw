---
title: HOW TO：回應 Windows Forms DataGrid 控制項的按一下動作
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Click event [Windows Forms], monitoring in DataGrid controls
- DataGrid control [Windows Forms], examples
- DataGrid control [Windows Forms], returning clicked cell value
- cells [Windows Forms], location in DataGrid
- examples [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], click events
ms.assetid: a0aa204b-8351-4d82-9933-ee21a5c9e409
ms.openlocfilehash: 60c4dac76b4a7868da9143cab1433ee93f97c7d1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64636815"
---
# <a name="how-to-respond-to-clicks-in-the-windows-forms-datagrid-control"></a><span data-ttu-id="48a92-102">HOW TO：回應 Windows Forms DataGrid 控制項的按一下動作</span><span class="sxs-lookup"><span data-stu-id="48a92-102">How to: Respond to Clicks in the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="48a92-103"><xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="48a92-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="48a92-104">如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="48a92-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="48a92-105">在 Windows Form 後<xref:System.Windows.Forms.DataGrid>已連線到資料庫，您可以監視的資料格使用者按下了。</span><span class="sxs-lookup"><span data-stu-id="48a92-105">After the Windows Forms <xref:System.Windows.Forms.DataGrid> is connected to a database, you can monitor which cell the user clicked.</span></span>  
  
### <a name="to-detect-when-the-user-of-the-datagrid-selects-a-different-cell"></a><span data-ttu-id="48a92-106">若要偵測何時 DataGrid 的使用者選取不同的儲存格</span><span class="sxs-lookup"><span data-stu-id="48a92-106">To detect when the user of the DataGrid selects a different cell</span></span>  
  
- <span data-ttu-id="48a92-107">在 <xref:System.Windows.Forms.DataGrid.CurrentCellChanged>事件處理常式中撰寫程式碼來做出適當回應。</span><span class="sxs-lookup"><span data-stu-id="48a92-107">In the <xref:System.Windows.Forms.DataGrid.CurrentCellChanged> event handler, write code to respond appropriately.</span></span>  
  
    ```vb  
    Private Sub myDataGrid_CurrentCellChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles myDataGrid.CurrentCellChanged  
       MessageBox.Show("Col is " & myDataGrid.CurrentCell.ColumnNumber _  
          & ", Row is " & myDataGrid.CurrentCell.RowNumber _  
          & ", Value is " & myDataGrid.Item(myDataGrid.CurrentCell))  
    End Sub  
    ```  
  
    ```csharp  
    private void myDataGrid_CurrentCellChanged(object sender,   
    System.EventArgs e)  
    {  
       MessageBox.Show ("Col is " + myDataGrid.CurrentCell.ColumnNumber  
          + ", Row is " + myDataGrid.CurrentCell.RowNumber   
          + ", Value is " + myDataGrid[myDataGrid.CurrentCell] );  
    }  
    ```  
  
     <span data-ttu-id="48a92-108">(Visual C#)下列程式碼置於表單的建構函式，以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="48a92-108">(Visual C#) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.myDataGrid.CurrentCellChanged += new  
       System.EventHandler(this.myDataGrid_CurrentCellChanged);  
    ```  
  
### <a name="to-determine-which-part-of-the-datagrid-the-user-clicked"></a><span data-ttu-id="48a92-109">若要判斷資料格的哪個部分使用者按下</span><span class="sxs-lookup"><span data-stu-id="48a92-109">To determine which part of the DataGrid the user clicked</span></span>  
  
- <span data-ttu-id="48a92-110">呼叫<xref:System.Windows.Forms.DataGrid.HitTest%2A>方法在適當的事件處理常式，例如 mongoadminusername<xref:System.Windows.Forms.Control.MouseDown>或<xref:System.Windows.Forms.Control.Click>事件。</span><span class="sxs-lookup"><span data-stu-id="48a92-110">Call the <xref:System.Windows.Forms.DataGrid.HitTest%2A> method in an appropriate event handler, such as for the <xref:System.Windows.Forms.Control.MouseDown> or <xref:System.Windows.Forms.Control.Click> event.</span></span>  
  
     <span data-ttu-id="48a92-111"><xref:System.Windows.Forms.DataGrid.HitTest%2A>方法會傳回<xref:System.Windows.Forms.DataGrid.HitTestInfo>物件，包含資料列和按下區域的資料行。</span><span class="sxs-lookup"><span data-stu-id="48a92-111">The <xref:System.Windows.Forms.DataGrid.HitTest%2A> method returns a <xref:System.Windows.Forms.DataGrid.HitTestInfo> object that contains the row and column of a clicked area.</span></span>  
  
    ```vb  
    Private Sub myDataGrid_MouseDown(ByVal sender As Object, _  
    ByVal e As MouseEventArgs) Handles myDataGrid.MouseDown  
       Dim myGrid As DataGrid = CType(sender, DataGrid)  
       Dim hti As System.Windows.Forms.DataGrid.HitTestInfo  
       hti = myGrid.HitTest(e.X, e.Y)  
       Dim message As String = "You clicked "  
  
       Select Case hti.Type  
          Case System.Windows.Forms.DataGrid.HitTestType.None  
             message &= "the background."  
          Case System.Windows.Forms.DataGrid.HitTestType.Cell  
             message &= "cell at row " & hti.Row & ", col " & hti.Column  
          Case System.Windows.Forms.DataGrid.HitTestType.ColumnHeader  
             message &= "the column header for column " & hti.Column  
          Case System.Windows.Forms.DataGrid.HitTestType.RowHeader  
             message &= "the row header for row " & hti.Row  
          Case System.Windows.Forms.DataGrid.HitTestType.ColumnResize  
             message &= "the column resizer for column " & hti.Column  
          Case System.Windows.Forms.DataGrid.HitTestType.RowResize  
             message &= "the row resizer for row " & hti.Row  
          Case System.Windows.Forms.DataGrid.HitTestType.Caption  
             message &= "the caption"  
          Case System.Windows.Forms.DataGrid.HitTestType.ParentRows  
             message &= "the parent row"  
       End Select  
  
       Console.WriteLine(message)  
    End Sub  
    ```  
  
    ```csharp  
    private void myDataGrid_MouseDown(object sender,   
    System.Windows.Forms.MouseEventArgs e)  
    {  
       DataGrid myGrid = (DataGrid) sender;  
       System.Windows.Forms.DataGrid.HitTestInfo hti;  
       hti = myGrid.HitTest(e.X, e.Y);  
       string message = "You clicked ";  
  
       switch (hti.Type)   
       {  
          case System.Windows.Forms.DataGrid.HitTestType.None :  
             message += "the background.";  
             break;  
          case System.Windows.Forms.DataGrid.HitTestType.Cell :  
             message += "cell at row " + hti.Row + ", col " + hti.Column;  
             break;  
          case System.Windows.Forms.DataGrid.HitTestType.ColumnHeader :  
             message += "the column header for column " + hti.Column;  
             break;  
          case System.Windows.Forms.DataGrid.HitTestType.RowHeader :  
             message += "the row header for row " + hti.Row;  
             break;  
          case System.Windows.Forms.DataGrid.HitTestType.ColumnResize :  
             message += "the column resizer for column " + hti.Column;  
             break;  
          case System.Windows.Forms.DataGrid.HitTestType.RowResize :  
             message += "the row resizer for row " + hti.Row;  
             break;  
          case System.Windows.Forms.DataGrid.HitTestType.Caption :  
             message += "the caption";  
             break;  
          case System.Windows.Forms.DataGrid.HitTestType.ParentRows :  
             message += "the parent row";  
             break;  
          }  
  
          Console.WriteLine(message);  
    }  
    ```  
  
     <span data-ttu-id="48a92-112">(Visual C#)下列程式碼置於表單的建構函式，以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="48a92-112">(Visual C#) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.myDataGrid.MouseDown += new  
       System.Windows.Forms.MouseEventHandler  
       (this.myDataGrid_MouseDown);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="48a92-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48a92-113">See also</span></span>

- [<span data-ttu-id="48a92-114">DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="48a92-114">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="48a92-115">如何：在 Windows Forms DataGrid 控制項中的執行階段變更顯示的資料</span><span class="sxs-lookup"><span data-stu-id="48a92-115">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>](change-displayed-data-at-run-time-wf-datagrid-control.md)
