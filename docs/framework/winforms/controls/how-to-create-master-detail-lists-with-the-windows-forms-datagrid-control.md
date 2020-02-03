---
title: 使用 DataGrid 控制項建立主版詳細資料清單
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 20388c6a-94f9-4d96-be18-8c200491247f
ms.openlocfilehash: e8ab63d52d97a8a6e6f60da741186e3937350e1e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76730991"
---
# <a name="how-to-create-masterdetail-lists-with-the-windows-forms-datagrid-control"></a><span data-ttu-id="9522a-102">如何：使用 Windows Form DataGrid 控制項建立主從式清單</span><span class="sxs-lookup"><span data-stu-id="9522a-102">How to: Create Master/Detail Lists with the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="9522a-103"><xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="9522a-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="9522a-104">如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="9522a-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="9522a-105">如果您的 <xref:System.Data.DataSet> 包含一系列相關的資料表，您可以使用兩個 <xref:System.Windows.Forms.DataGrid> 控制項，以主要/詳細資料格式顯示資料。</span><span class="sxs-lookup"><span data-stu-id="9522a-105">If your <xref:System.Data.DataSet> contains a series of related tables, you can use two <xref:System.Windows.Forms.DataGrid> controls to display the data in a master/detail format.</span></span> <span data-ttu-id="9522a-106">其中一個 <xref:System.Windows.Forms.DataGrid> 會指定為主要方格，而第二個則指定為詳細資料方格。</span><span class="sxs-lookup"><span data-stu-id="9522a-106">One <xref:System.Windows.Forms.DataGrid> is designated to be the master grid, and the second is designated to be the details grid.</span></span> <span data-ttu-id="9522a-107">當您選取 [主要] 清單中的專案時，[詳細資料] 清單中會顯示所有相關的子專案。</span><span class="sxs-lookup"><span data-stu-id="9522a-107">When you select an entry in the master list, all of the related child entries are shown in the details list.</span></span> <span data-ttu-id="9522a-108">例如，如果您的 <xref:System.Data.DataSet> 包含 Customers 資料表和相關的 Orders 資料表，您會將 Customers 資料表指定為主要方格，而 Orders 資料表則為詳細資料方格。</span><span class="sxs-lookup"><span data-stu-id="9522a-108">For example, if your <xref:System.Data.DataSet> contains a Customers table and a related Orders table, you would specify the Customers table to be the master grid and the Orders table to be the details grid.</span></span> <span data-ttu-id="9522a-109">從主要方格中選取客戶時，[訂單] 資料表中與該客戶相關聯的所有訂單都會顯示在 [詳細資料] 方格中。</span><span class="sxs-lookup"><span data-stu-id="9522a-109">When a customer is selected from the master grid, all of the orders associated with that customer in the Orders table would be displayed in the details grid.</span></span>  
  
### <a name="to-set-a-masterdetail-relationship-programmatically"></a><span data-ttu-id="9522a-110">以程式設計方式設定主要/詳細資料關聯性</span><span class="sxs-lookup"><span data-stu-id="9522a-110">To set a master/detail relationship programmatically</span></span>  
  
1. <span data-ttu-id="9522a-111">建立兩個新的 <xref:System.Windows.Forms.DataGrid> 控制項，並設定其屬性。</span><span class="sxs-lookup"><span data-stu-id="9522a-111">Create two new <xref:System.Windows.Forms.DataGrid> controls and set their properties.</span></span>  
  
2. <span data-ttu-id="9522a-112">將資料表加入至資料集。</span><span class="sxs-lookup"><span data-stu-id="9522a-112">Add tables to the dataset.</span></span>  
  
3. <span data-ttu-id="9522a-113">宣告 <xref:System.Data.DataRelation> 類型的變數，以代表您想要建立的關聯性。</span><span class="sxs-lookup"><span data-stu-id="9522a-113">Declare a variable of type <xref:System.Data.DataRelation> to represent the relation you want to create.</span></span>  
  
4. <span data-ttu-id="9522a-114">指定關聯性的名稱，並指定將結合兩個數據表的資料表、資料行和專案，以具現化關聯性。</span><span class="sxs-lookup"><span data-stu-id="9522a-114">Instantiate the relationship by specifying a name for the relationship and specifying the table, column, and item that will tie the two tables.</span></span>  
  
5. <span data-ttu-id="9522a-115">將關聯性加入至 <xref:System.Data.DataSet> 物件的 <xref:System.Data.DataSet.Relations%2A> 集合。</span><span class="sxs-lookup"><span data-stu-id="9522a-115">Add the relationship to the <xref:System.Data.DataSet> object's <xref:System.Data.DataSet.Relations%2A> collection.</span></span>  
  
6. <span data-ttu-id="9522a-116">使用 <xref:System.Windows.Forms.DataGrid> 的 <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> 方法，將每個格線系結至 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="9522a-116">Use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method of the <xref:System.Windows.Forms.DataGrid> to bind each of the grids to the <xref:System.Data.DataSet>.</span></span>  
  
     <span data-ttu-id="9522a-117">下列範例示範如何在先前產生的 <xref:System.Data.DataSet> （`ds`）中設定 Customers 和 Orders 資料表之間的主要/詳細關係。</span><span class="sxs-lookup"><span data-stu-id="9522a-117">The following example shows how to set a master/detail relationship between the Customers and Orders tables in a previously generated <xref:System.Data.DataSet> (`ds`).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9522a-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9522a-118">See also</span></span>

- [<span data-ttu-id="9522a-119">DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="9522a-119">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="9522a-120">DataGrid 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="9522a-120">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)
- [<span data-ttu-id="9522a-121">如何：將 Windows Forms DataGrid 控制項繫結至資料來源</span><span class="sxs-lookup"><span data-stu-id="9522a-121">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
