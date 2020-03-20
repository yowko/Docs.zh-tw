---
title: 在資料網格控制中更改運行時顯示的資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DataGrid control [Windows Forms], dynamically changing at run time
- DataGrid control [Windows Forms], data binding
- cells [Windows Forms], changing DataGrid cell values
ms.assetid: 0c7a6d00-30de-416e-8223-0a81ddb4c1f8
ms.openlocfilehash: 6b788c10784082a0c74ee09f8cd85d540c670b84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142377"
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a><span data-ttu-id="6a42e-102">如何：在執行階段時變更 Windows Form DataGrid 控制項中顯示的資料</span><span class="sxs-lookup"><span data-stu-id="6a42e-102">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="6a42e-103"><xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="6a42e-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="6a42e-104">如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="6a42e-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="6a42e-105">使用設計時功能創建 Windows<xref:System.Windows.Forms.DataGrid>表單後，您可能還希望在運行時動態更改網格<xref:System.Data.DataSet>物件的元素。</span><span class="sxs-lookup"><span data-stu-id="6a42e-105">After you have created a Windows Forms <xref:System.Windows.Forms.DataGrid> using the design-time features, you may also wish to dynamically change elements of the <xref:System.Data.DataSet> object of the grid at run time.</span></span> <span data-ttu-id="6a42e-106">這可能包括對表的單個值的更改或更改綁定到控制項的<xref:System.Windows.Forms.DataGrid>資料來源。</span><span class="sxs-lookup"><span data-stu-id="6a42e-106">This can include changes to either individual values of the table or changing which data source is bound to the <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="6a42e-107">對單個值的更改是通過<xref:System.Data.DataSet>物件而不是控制項完成的。 <xref:System.Windows.Forms.DataGrid></span><span class="sxs-lookup"><span data-stu-id="6a42e-107">Changes to individual values are done through the <xref:System.Data.DataSet> object, not the <xref:System.Windows.Forms.DataGrid> control.</span></span>  
  
### <a name="to-change-data-programmatically"></a><span data-ttu-id="6a42e-108">以程式設計方式更改資料</span><span class="sxs-lookup"><span data-stu-id="6a42e-108">To change data programmatically</span></span>  
  
1. <span data-ttu-id="6a42e-109">從<xref:System.Data.DataSet>物件指定所需的表，從表中指定所需的行和欄位，並將儲存格設置為等於新值。</span><span class="sxs-lookup"><span data-stu-id="6a42e-109">Specify the desired table from the <xref:System.Data.DataSet> object and the desired row and field from the table and set the cell equal to the new value.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="6a42e-110">要指定 表<xref:System.Data.DataSet>的第一個表或表的第一行，請使用 0。</span><span class="sxs-lookup"><span data-stu-id="6a42e-110">To specify the first table of the <xref:System.Data.DataSet> or the first row of the table, use 0.</span></span>  
  
     <span data-ttu-id="6a42e-111">下面的示例演示如何通過按一下`Button1`來更改資料集第一個表的第一行的第二個條目。</span><span class="sxs-lookup"><span data-stu-id="6a42e-111">The following example shows how to change the second entry of the first row of the first table of a dataset by clicking `Button1`.</span></span> <span data-ttu-id="6a42e-112">以前<xref:System.Data.DataSet>創建的`ds`（ 和`0``1`表 和 ）</span><span class="sxs-lookup"><span data-stu-id="6a42e-112">The <xref:System.Data.DataSet> (`ds`) and Tables (`0` and `1`) were previously created.</span></span>  
  
    ```vb  
    Protected Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       ds.tables(0).rows(0)(1) = "NewEntry"  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       ds.Tables[0].Rows[0][1]="NewEntry";  
    }  
    ```  
  
    ```cpp  
    private:
       void button1_Click(System::Object^ sender, System::EventArgs^ e)  
       {  
          dataSet1->Tables[0]->Rows[0][1] = "NewEntry";  
       }  
    ```  
  
     <span data-ttu-id="6a42e-113">（視覺 C#，視覺C++）將以下代碼放在表單的建構函式中以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="6a42e-113">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     <span data-ttu-id="6a42e-114">在運行時，可以使用 方法<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>將<xref:System.Windows.Forms.DataGrid>控制項綁定到其他資料來源。</span><span class="sxs-lookup"><span data-stu-id="6a42e-114">At run time you can use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to bind the <xref:System.Windows.Forms.DataGrid> control to a different data source.</span></span> <span data-ttu-id="6a42e-115">例如，您可能有多個ADO.NET資料控制項，每個控制項都連接到不同的資料庫。</span><span class="sxs-lookup"><span data-stu-id="6a42e-115">For example, you may have several ADO.NET data controls, each connected to a different database.</span></span>  
  
### <a name="to-change-the-datasource-programmatically"></a><span data-ttu-id="6a42e-116">以程式設計方式更改資料來源</span><span class="sxs-lookup"><span data-stu-id="6a42e-116">To change the DataSource programmatically</span></span>  
  
1. <span data-ttu-id="6a42e-117">將<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法設置為要綁定到的資料來源和表的名稱。</span><span class="sxs-lookup"><span data-stu-id="6a42e-117">Set the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to the name of the data source and table you want to bind to.</span></span>  
  
     <span data-ttu-id="6a42e-118">下面的示例演示如何使用<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法將日期源更改為連接到 Pubs 資料庫中的作者表ADO.NET資料控制項（adoPubsAuthors）。</span><span class="sxs-lookup"><span data-stu-id="6a42e-118">The following example shows how to change the date source using the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to an ADO.NET data control (adoPubsAuthors) that is connected to the Authors table in the Pubs database.</span></span>  
  
    ```vb  
    Private Sub ResetSource()  
       DataGrid1.SetDataBinding(adoPubsAuthors, "Authors")  
    End Sub  
    ```  
  
    ```csharp  
    private void ResetSource()  
    {  
       DataGrid1.SetDataBinding(adoPubsAuthors, "Authors");  
    }  
    ```  
  
    ```cpp  
    private:  
       void ResetSource()  
       {  
          dataGrid1->SetDataBinding(adoPubsAuthors, "Authors");  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="6a42e-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a42e-119">See also</span></span>

- [<span data-ttu-id="6a42e-120">ADO.NET 資料集</span><span class="sxs-lookup"><span data-stu-id="6a42e-120">ADO.NET DataSets</span></span>](../../data/adonet/ado-net-datasets.md)
- [<span data-ttu-id="6a42e-121">如何：刪除或隱藏 Windows Form DataGrid 控制項中的資料行</span><span class="sxs-lookup"><span data-stu-id="6a42e-121">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="6a42e-122">如何：將資料表和資料行加入至 Windows Form DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="6a42e-122">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="6a42e-123">如何：將 Windows Form DataGrid 控制項繫結至資料來源</span><span class="sxs-lookup"><span data-stu-id="6a42e-123">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
