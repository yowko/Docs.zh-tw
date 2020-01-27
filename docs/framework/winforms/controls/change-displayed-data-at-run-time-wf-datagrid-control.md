---
title: 在 DataGrid 控制項中變更執行時間顯示的資料
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
ms.openlocfilehash: f91e2ea01ef4a52dd649efed70319017efb8368a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740598"
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a><span data-ttu-id="72d01-102">如何：在執行階段時變更 Windows Form DataGrid 控制項中顯示的資料</span><span class="sxs-lookup"><span data-stu-id="72d01-102">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="72d01-103"><xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="72d01-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="72d01-104">如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="72d01-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="72d01-105">使用設計階段功能建立 Windows Forms <xref:System.Windows.Forms.DataGrid> 之後，您可能也會想要在執行時間動態變更方格中 <xref:System.Data.DataSet> 物件的元素。</span><span class="sxs-lookup"><span data-stu-id="72d01-105">After you have created a Windows Forms <xref:System.Windows.Forms.DataGrid> using the design-time features, you may also wish to dynamically change elements of the <xref:System.Data.DataSet> object of the grid at run time.</span></span> <span data-ttu-id="72d01-106">這可能包括變更資料表的個別值，或變更哪一個資料來源系結至 <xref:System.Windows.Forms.DataGrid> 控制項。</span><span class="sxs-lookup"><span data-stu-id="72d01-106">This can include changes to either individual values of the table or changing which data source is bound to the <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="72d01-107">個別值的變更是透過 <xref:System.Data.DataSet> 物件來完成，而不是 <xref:System.Windows.Forms.DataGrid> 控制項。</span><span class="sxs-lookup"><span data-stu-id="72d01-107">Changes to individual values are done through the <xref:System.Data.DataSet> object, not the <xref:System.Windows.Forms.DataGrid> control.</span></span>  
  
### <a name="to-change-data-programmatically"></a><span data-ttu-id="72d01-108">以程式設計方式變更資料</span><span class="sxs-lookup"><span data-stu-id="72d01-108">To change data programmatically</span></span>  
  
1. <span data-ttu-id="72d01-109">從 [<xref:System.Data.DataSet>] 物件中指定所需的資料表，並從資料表中指定所需的資料列和欄位，並將資料格設定為等於新的值。</span><span class="sxs-lookup"><span data-stu-id="72d01-109">Specify the desired table from the <xref:System.Data.DataSet> object and the desired row and field from the table and set the cell equal to the new value.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="72d01-110">若要指定 <xref:System.Data.DataSet> 或資料表第一個資料列的第一個資料表，請使用0。</span><span class="sxs-lookup"><span data-stu-id="72d01-110">To specify the first table of the <xref:System.Data.DataSet> or the first row of the table, use 0.</span></span>  
  
     <span data-ttu-id="72d01-111">下列範例顯示如何藉由按一下 [`Button1`] 來變更資料集第一個資料表第一列的第二個專案。</span><span class="sxs-lookup"><span data-stu-id="72d01-111">The following example shows how to change the second entry of the first row of the first table of a dataset by clicking `Button1`.</span></span> <span data-ttu-id="72d01-112">先前已建立 <xref:System.Data.DataSet> （`ds`）和資料表（`0` 和 `1`）。</span><span class="sxs-lookup"><span data-stu-id="72d01-112">The <xref:System.Data.DataSet> (`ds`) and Tables (`0` and `1`) were previously created.</span></span>  
  
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
  
     <span data-ttu-id="72d01-113">（視覺C#效果， C++視覺效果）將下列程式碼放在表單的函式中，以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="72d01-113">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     <span data-ttu-id="72d01-114">在執行時間，您可以使用 <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> 方法，將 <xref:System.Windows.Forms.DataGrid> 控制項系結到不同的資料來源。</span><span class="sxs-lookup"><span data-stu-id="72d01-114">At run time you can use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to bind the <xref:System.Windows.Forms.DataGrid> control to a different data source.</span></span> <span data-ttu-id="72d01-115">例如，您可能有數個 ADO.NET 資料控制項，每個都連接到不同的資料庫。</span><span class="sxs-lookup"><span data-stu-id="72d01-115">For example, you may have several ADO.NET data controls, each connected to a different database.</span></span>  
  
### <a name="to-change-the-datasource-programmatically"></a><span data-ttu-id="72d01-116">以程式設計方式變更資料來源</span><span class="sxs-lookup"><span data-stu-id="72d01-116">To change the DataSource programmatically</span></span>  
  
1. <span data-ttu-id="72d01-117">將 <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> 方法設定為您要系結的資料來源和資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="72d01-117">Set the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to the name of the data source and table you want to bind to.</span></span>  
  
     <span data-ttu-id="72d01-118">下列範例示範如何使用 <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> 方法，將日期來源變更為連接到 Pubs 資料庫中作者資料表的 ADO.NET 資料控制項（adoPubsAuthors）。</span><span class="sxs-lookup"><span data-stu-id="72d01-118">The following example shows how to change the date source using the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to an ADO.NET data control (adoPubsAuthors) that is connected to the Authors table in the Pubs database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="72d01-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="72d01-119">See also</span></span>

- [<span data-ttu-id="72d01-120">ADO.NET 資料集</span><span class="sxs-lookup"><span data-stu-id="72d01-120">ADO.NET DataSets</span></span>](../../data/adonet/ado-net-datasets.md)
- [<span data-ttu-id="72d01-121">操作說明：刪除或隱藏 Windows Forms DataGrid 控制項中的資料行</span><span class="sxs-lookup"><span data-stu-id="72d01-121">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="72d01-122">如何：將資料表和資料行新增至 Windows Forms DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="72d01-122">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="72d01-123">如何：將 Windows Forms DataGrid 控制項繫結至資料來源</span><span class="sxs-lookup"><span data-stu-id="72d01-123">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
