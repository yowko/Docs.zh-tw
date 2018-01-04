---
title: "如何：在執行階段時變更 Windows Form DataGrid 控制項中顯示的資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DataGrid control [Windows Forms], dynamically changing at run time
- DataGrid control [Windows Forms], data binding
- cells [Windows Forms], changing DataGrid cell values
ms.assetid: 0c7a6d00-30de-416e-8223-0a81ddb4c1f8
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c34c6207c29f008606cc4ace83aa4f94c41f6851
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a><span data-ttu-id="c4be3-102">如何：在執行階段時變更 Windows Form DataGrid 控制項中顯示的資料</span><span class="sxs-lookup"><span data-stu-id="c4be3-102">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="c4be3-103"><xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="c4be3-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="c4be3-104">如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="c4be3-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="c4be3-105">建立 Windows Form 之後<xref:System.Windows.Forms.DataGrid>使用設計階段功能，您可能也想要以動態方式變更項目的<xref:System.Data.DataSet>在執行階段方格的物件。</span><span class="sxs-lookup"><span data-stu-id="c4be3-105">After you have created a Windows Forms <xref:System.Windows.Forms.DataGrid> using the design-time features, you may also wish to dynamically change elements of the <xref:System.Data.DataSet> object of the grid at run time.</span></span> <span data-ttu-id="c4be3-106">這可包括對資料表的個別值或變更資料來源繫結至<xref:System.Windows.Forms.DataGrid>控制項。</span><span class="sxs-lookup"><span data-stu-id="c4be3-106">This can include changes to either individual values of the table or changing which data source is bound to the <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="c4be3-107">個別值的變更會透過<xref:System.Data.DataSet>物件，不<xref:System.Windows.Forms.DataGrid>控制項。</span><span class="sxs-lookup"><span data-stu-id="c4be3-107">Changes to individual values are done through the <xref:System.Data.DataSet> object, not the <xref:System.Windows.Forms.DataGrid> control.</span></span>  
  
### <a name="to-change-data-programmatically"></a><span data-ttu-id="c4be3-108">若要以程式設計方式變更資料</span><span class="sxs-lookup"><span data-stu-id="c4be3-108">To change data programmatically</span></span>  
  
1.  <span data-ttu-id="c4be3-109">指定所需的資料表，從<xref:System.Data.DataSet>物件和想要的資料列和欄位從資料表和資料格設定為等於新值。</span><span class="sxs-lookup"><span data-stu-id="c4be3-109">Specify the desired table from the <xref:System.Data.DataSet> object and the desired row and field from the table and set the cell equal to the new value.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c4be3-110">若要指定的第一個資料表<xref:System.Data.DataSet>或資料表，第一個資料列，請使用 0。</span><span class="sxs-lookup"><span data-stu-id="c4be3-110">To specify the first table of the <xref:System.Data.DataSet> or the first row of the table, use 0.</span></span>  
  
     <span data-ttu-id="c4be3-111">下列範例示範如何變更資料集的第一個資料表的第一個資料列的第二個項目，依序按一下`Button1`。</span><span class="sxs-lookup"><span data-stu-id="c4be3-111">The following example shows how to change the second entry of the first row of the first table of a dataset by clicking `Button1`.</span></span> <span data-ttu-id="c4be3-112"><xref:System.Data.DataSet> (`ds`) 和資料表 (`0`和`1`) 先前所建立。</span><span class="sxs-lookup"><span data-stu-id="c4be3-112">The <xref:System.Data.DataSet> (`ds`) and Tables (`0` and `1`) were previously created.</span></span>  
  
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
  
     <span data-ttu-id="c4be3-113">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]、 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 請將下列程式碼置於表單的建構函式中，以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="c4be3-113">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     <span data-ttu-id="c4be3-114">在執行的階段，您可以使用<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>繫結方法<xref:System.Windows.Forms.DataGrid>不同的資料來源的控制項。</span><span class="sxs-lookup"><span data-stu-id="c4be3-114">At run time you can use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to bind the <xref:System.Windows.Forms.DataGrid> control to a different data source.</span></span> <span data-ttu-id="c4be3-115">例如，您可以有數個[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]資料控制項，每個已連線到不同的資料庫。</span><span class="sxs-lookup"><span data-stu-id="c4be3-115">For example, you may have several [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] data controls, each connected to a different database.</span></span>  
  
### <a name="to-change-the-datasource-programmatically"></a><span data-ttu-id="c4be3-116">若要以程式設計方式變更資料來源</span><span class="sxs-lookup"><span data-stu-id="c4be3-116">To change the DataSource programmatically</span></span>  
  
1.  <span data-ttu-id="c4be3-117">設定<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法的資料來源和您想要繫結至資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="c4be3-117">Set the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to the name of the data source and table you want to bind to.</span></span>  
  
     <span data-ttu-id="c4be3-118">下列範例示範如何變更日期來源使用<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]連線到 Authors 資料表 Pubs 資料庫中的資料控制項 (adoPubsAuthors)。</span><span class="sxs-lookup"><span data-stu-id="c4be3-118">The following example shows how to change the date source using the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to an [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] data control (adoPubsAuthors) that is connected to the Authors table in the Pubs database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c4be3-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="c4be3-119">See Also</span></span>  
 [<span data-ttu-id="c4be3-120">ADO.NET 資料集</span><span class="sxs-lookup"><span data-stu-id="c4be3-120">ADO.NET DataSets</span></span>](../../../../docs/framework/data/adonet/ado-net-datasets.md)  
 [<span data-ttu-id="c4be3-121">操作說明：刪除或隱藏 Windows Forms DataGrid 控制項中的資料行</span><span class="sxs-lookup"><span data-stu-id="c4be3-121">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 [<span data-ttu-id="c4be3-122">操作說明：將資料表和資料行新增至 Windows Forms DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="c4be3-122">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 [<span data-ttu-id="c4be3-123">操作說明：將 Windows Forms DataGrid 控制項繫結至資料來源</span><span class="sxs-lookup"><span data-stu-id="c4be3-123">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
