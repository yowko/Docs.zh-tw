---
title: "如何： 使用 Windows Form DataGrid 控制項建立主從式清單"
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
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 20388c6a-94f9-4d96-be18-8c200491247f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 63cb647e2ed6dcbc97fab15db3166b55c52f635a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-masterdetail-lists-with-the-windows-forms-datagrid-control"></a><span data-ttu-id="4685d-102">如何：使用 Windows Form DataGrid 控制項建立主從式清單</span><span class="sxs-lookup"><span data-stu-id="4685d-102">How to: Create Master/Detail Lists with the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="4685d-103"><xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="4685d-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="4685d-104">如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="4685d-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="4685d-105">如果您<xref:System.Data.DataSet>包含一系列相關的資料表，您可以使用兩個<xref:System.Windows.Forms.DataGrid>控制項以顯示資料的主要/詳細資料格式。</span><span class="sxs-lookup"><span data-stu-id="4685d-105">If your <xref:System.Data.DataSet> contains a series of related tables, you can use two <xref:System.Windows.Forms.DataGrid> controls to display the data in a master/detail format.</span></span> <span data-ttu-id="4685d-106">一個<xref:System.Windows.Forms.DataGrid>指定為主要方格中，與第二個指定為詳細資料方格。</span><span class="sxs-lookup"><span data-stu-id="4685d-106">One <xref:System.Windows.Forms.DataGrid> is designated to be the master grid, and the second is designated to be the details grid.</span></span> <span data-ttu-id="4685d-107">當您的主機清單中選取一個項目時，所有相關的子系項目會顯示在詳細資料清單。</span><span class="sxs-lookup"><span data-stu-id="4685d-107">When you select an entry in the master list, all of the related child entries are shown in the details list.</span></span> <span data-ttu-id="4685d-108">例如，如果您<xref:System.Data.DataSet>包含 Customers 資料表和相關的 Orders 資料表，您會指定為主要的方格的 [客戶] 資料表和訂單資料表詳細資料方格。</span><span class="sxs-lookup"><span data-stu-id="4685d-108">For example, if your <xref:System.Data.DataSet> contains a Customers table and a related Orders table, you would specify the Customers table to be the master grid and the Orders table to be the details grid.</span></span> <span data-ttu-id="4685d-109">從主版方格選取客戶時，所有相關 [Orders] 資料表中與該客戶的訂單會顯示詳細資料方格中。</span><span class="sxs-lookup"><span data-stu-id="4685d-109">When a customer is selected from the master grid, all of the orders associated with that customer in the Orders table would be displayed in the details grid.</span></span>  
  
### <a name="to-set-a-masterdetail-relationship-programmatically"></a><span data-ttu-id="4685d-110">以程式設計方式設定的主要/詳細資料關聯性</span><span class="sxs-lookup"><span data-stu-id="4685d-110">To set a master/detail relationship programmatically</span></span>  
  
1.  <span data-ttu-id="4685d-111">建立兩個新<xref:System.Windows.Forms.DataGrid>控制，並設定其屬性。</span><span class="sxs-lookup"><span data-stu-id="4685d-111">Create two new <xref:System.Windows.Forms.DataGrid> controls and set their properties.</span></span>  
  
2.  <span data-ttu-id="4685d-112">將資料表加入至資料集。</span><span class="sxs-lookup"><span data-stu-id="4685d-112">Add tables to the dataset.</span></span>  
  
3.  <span data-ttu-id="4685d-113">宣告類型的變數<xref:System.Data.DataRelation>來代表您想要建立的關聯性。</span><span class="sxs-lookup"><span data-stu-id="4685d-113">Declare a variable of type <xref:System.Data.DataRelation> to represent the relation you want to create.</span></span>  
  
4.  <span data-ttu-id="4685d-114">所指定關聯性的名稱，並指定資料表、 資料行和會結合兩個資料表的項目產生關聯性。</span><span class="sxs-lookup"><span data-stu-id="4685d-114">Instantiate the relationship by specifying a name for the relationship and specifying the table, column, and item that will tie the two tables.</span></span>  
  
5.  <span data-ttu-id="4685d-115">加入至關聯性<xref:System.Data.DataSet>物件的<xref:System.Data.DataSet.Relations%2A>集合。</span><span class="sxs-lookup"><span data-stu-id="4685d-115">Add the relationship to the <xref:System.Data.DataSet> object's <xref:System.Data.DataSet.Relations%2A> collection.</span></span>  
  
6.  <span data-ttu-id="4685d-116">使用<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法<xref:System.Windows.Forms.DataGrid>繫結至方格的每個<xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="4685d-116">Use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method of the <xref:System.Windows.Forms.DataGrid> to bind each of the grids to the <xref:System.Data.DataSet>.</span></span>  
  
     <span data-ttu-id="4685d-117">下列範例示範如何設定主要/詳細資料之間的關聯性中先前產生的客戶和訂單資料表<xref:System.Data.DataSet>(`ds`)。</span><span class="sxs-lookup"><span data-stu-id="4685d-117">The following example shows how to set a master/detail relationship between the Customers and Orders tables in a previously generated <xref:System.Data.DataSet> (`ds`).</span></span>  
  
    ```vb  
    Dim myDataRelation As DataRelation  
    myDataRelation = New DataRelation _  
       ("CustOrd", ds.Tables("Customers").Columns("CustomerID"), _  
       ds.Tables("Orders").Columns("CustomerID"))  
    ' Add the relation to the DataSet.  
    ds.Relations.Add(myDataRelation)  
    GridOrders.SetDataBinding(ds, "Customers")  
    GridDetails.SetDataBinding(ds, "Customers.CustOrd")  
    ```  
  
    ```csharp  
    DataRelation myDataRelation;  
    myDataRelation = new DataRelation("CustOrd", ds.Tables["Customers"].Columns["CustomerID"], ds.Tables["Orders"].Columns["CustomerID"]);  
    // Add the relation to the DataSet.  
    ds.Relations.Add(myDataRelation);  
    GridOrders.SetDataBinding(ds,"Customers");  
    GridDetails.SetDataBinding(ds,"Customers.CustOrd");  
    ```  
  
    ```cpp  
    DataRelation^ myDataRelation;  
    myDataRelation = gcnew DataRelation("CustOrd",  
       ds->Tables["Customers"]->Columns["CustomerID"],  
       ds->Tables["Orders"]->Columns["CustomerID"]);  
    // Add the relation to the DataSet.  
    ds->Relations->Add(myDataRelation);  
    GridOrders->SetDataBinding(ds, "Customers");  
    GridDetails->SetDataBinding(ds, "Customers.CustOrd");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4685d-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4685d-118">See Also</span></span>  
 [<span data-ttu-id="4685d-119">DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="4685d-119">DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [<span data-ttu-id="4685d-120">DataGrid 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="4685d-120">DataGrid Control Overview</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [<span data-ttu-id="4685d-121">操作說明：將 Windows Forms DataGrid 控制項繫結至資料來源</span><span class="sxs-lookup"><span data-stu-id="4685d-121">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
