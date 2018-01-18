---
title: "複製資料集內容"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: bdeb462955816a53372719bf374f7d4b55aa7f18
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="copying-dataset-contents"></a><span data-ttu-id="d70ba-102">複製資料集內容</span><span class="sxs-lookup"><span data-stu-id="d70ba-102">Copying DataSet Contents</span></span>
<span data-ttu-id="d70ba-103">您可以建立一份<xref:System.Data.DataSet>，讓您可以使用資料，而不會影響原始資料，或處理的資料子集**資料集**。</span><span class="sxs-lookup"><span data-stu-id="d70ba-103">You can create a copy of a <xref:System.Data.DataSet> so that you can work with data without affecting the original data, or work with a subset of the data from a **DataSet**.</span></span> <span data-ttu-id="d70ba-104">當複製**資料集**，您可以：</span><span class="sxs-lookup"><span data-stu-id="d70ba-104">When copying a **DataSet**, you can:</span></span>  
  
-   <span data-ttu-id="d70ba-105">建立完全相同複本**資料集**，包括結構描述、 資料、 資料列狀態資訊，以及資料列版本。</span><span class="sxs-lookup"><span data-stu-id="d70ba-105">Create an exact copy of the **DataSet**, including the schema, data, row state information, and row versions.</span></span>  
  
-   <span data-ttu-id="d70ba-106">建立**資料集**，其中包含針對現有的結構描述**資料集**，但已修改的資料列。</span><span class="sxs-lookup"><span data-stu-id="d70ba-106">Create a **DataSet** that contains the schema of an existing **DataSet**, but only rows that have been modified.</span></span> <span data-ttu-id="d70ba-107">您可以傳回已修改的所有資料列，或指定特定**Getchanges**。</span><span class="sxs-lookup"><span data-stu-id="d70ba-107">You can return all rows that have been modified, or specify a specific **DataRowState**.</span></span> <span data-ttu-id="d70ba-108">如需資料列狀態的詳細資訊，請參閱[資料列狀態和資料列版本](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)。</span><span class="sxs-lookup"><span data-stu-id="d70ba-108">For more information about row states, see [Row States and Row Versions](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span>  
  
-   <span data-ttu-id="d70ba-109">複製結構描述或關聯式結構**資料集**，而不複製任何資料列。</span><span class="sxs-lookup"><span data-stu-id="d70ba-109">Copy the schema, or relational structure, of the **DataSet** only, without copying any rows.</span></span> <span data-ttu-id="d70ba-110">使用 <xref:System.Data.DataTable>，可以將資料列匯入現有的 <xref:System.Data.DataTable.ImportRow%2A>。</span><span class="sxs-lookup"><span data-stu-id="d70ba-110">Rows can be imported into an existing <xref:System.Data.DataTable> using <xref:System.Data.DataTable.ImportRow%2A>.</span></span>  
  
 <span data-ttu-id="d70ba-111">若要建立的完全相同複本**資料集**包含結構描述和資料，請使用<xref:System.Data.DataSet.Copy%2A>方法**資料集**。</span><span class="sxs-lookup"><span data-stu-id="d70ba-111">To create an exact copy of the **DataSet** that includes both schema and data, use the <xref:System.Data.DataSet.Copy%2A> method of the **DataSet**.</span></span> <span data-ttu-id="d70ba-112">下列程式碼範例示範如何建立完全相同的複本**資料集**。</span><span class="sxs-lookup"><span data-stu-id="d70ba-112">The following code example shows how to create an exact copy of the **DataSet**.</span></span>  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 <span data-ttu-id="d70ba-113">若要建立一份**資料集**包含結構描述和只有資料表示的**Added**， **Modified**，或**刪除**資料列，使用<xref:System.Data.DataSet.GetChanges%2A>方法**資料集**。</span><span class="sxs-lookup"><span data-stu-id="d70ba-113">To create a copy of a **DataSet** that includes schema and only the data representing **Added**, **Modified**, or **Deleted** rows, use the <xref:System.Data.DataSet.GetChanges%2A> method of the **DataSet**.</span></span> <span data-ttu-id="d70ba-114">您也可以使用**Datarowstate**藉由傳遞傳回具有指定的資料列狀態的資料列**Getchanges**時呼叫的值**Datarowstate**。</span><span class="sxs-lookup"><span data-stu-id="d70ba-114">You can also use **GetChanges** to return only rows with a specified row state by passing a **DataRowState** value when calling **GetChanges**.</span></span> <span data-ttu-id="d70ba-115">下列程式碼範例示範如何傳遞**Getchanges**呼叫時**Datarowstate**。</span><span class="sxs-lookup"><span data-stu-id="d70ba-115">The following code example shows how to pass a **DataRowState** when calling **GetChanges**.</span></span>  
  
```vb  
' Copy all changes.  
Dim changeDataSet As DataSet = customerDataSet.GetChanges()  
' Copy only new rows.  
Dim addedDataSetAs DataSet = _  
    customerDataSet.GetChanges(DataRowState.Added)  
```  
  
```csharp  
// Copy all changes.  
DataSet changeDataSet = customerDataSet.GetChanges();  
// Copy only new rows.  
DataSet addedDataSet= customerDataSet.GetChanges(DataRowState.Added);  
```  
  
 <span data-ttu-id="d70ba-116">若要建立一份**資料集**只包含結構描述，請使用<xref:System.Data.DataSet.Clone%2A>方法**資料集**。</span><span class="sxs-lookup"><span data-stu-id="d70ba-116">To create a copy of a **DataSet** that only includes schema, use the <xref:System.Data.DataSet.Clone%2A> method of the **DataSet**.</span></span> <span data-ttu-id="d70ba-117">您也可以將現有的資料列加入複製**資料集**使用**ImportRow**方法**DataTable**。</span><span class="sxs-lookup"><span data-stu-id="d70ba-117">You can also add existing rows to the cloned **DataSet** using the **ImportRow** method of the **DataTable**.</span></span> <span data-ttu-id="d70ba-118">**ImportRow**將資料、 資料列狀態和資料列版本資訊加入至指定的資料表。</span><span class="sxs-lookup"><span data-stu-id="d70ba-118">**ImportRow** adds data, row state, and row version information to the specified table.</span></span> <span data-ttu-id="d70ba-119">資料行值只會被加入資料行名稱相符且資料型別相容之處。</span><span class="sxs-lookup"><span data-stu-id="d70ba-119">Column values are added only where the column name matches and the data type is compatible.</span></span>  
  
 <span data-ttu-id="d70ba-120">下列程式碼範例會建立複製的**資料集**然後將原始資料列**資料集**至**客戶**資料表中**資料集**客戶複製其中**CountryRegion**資料行有值為"Germany"。</span><span class="sxs-lookup"><span data-stu-id="d70ba-120">The following code example creates a clone of a **DataSet** and then adds the rows from the original **DataSet** to the **Customers** table in the **DataSet** clone for customers where the **CountryRegion** column has the value "Germany".</span></span>  
  
```vb  
Dim customerDataSet As New DataSet  
        customerDataSet.Tables.Add(New DataTable("Customers"))  
        customerDataSet.Tables("Customers").Columns.Add("Name", GetType(String))  
        customerDataSet.Tables("Customers").Columns.Add("CountryRegion", GetType(String))  
        customerDataSet.Tables("Customers").Rows.Add("Juan", "Spain")  
        customerDataSet.Tables("Customers").Rows.Add("Johann", "Germany")  
        customerDataSet.Tables("Customers").Rows.Add("John", "UK")  
  
Dim germanyCustomers As DataSet = customerDataSet.Clone()  
  
Dim copyRows() As DataRow = _  
  customerDataSet.Tables("Customers").Select("CountryRegion = 'Germany'")  
  
Dim customerTable As DataTable = germanyCustomers.Tables("Customers")  
Dim copyRow As DataRow  
  
For Each copyRow In copyRows  
  customerTable.ImportRow(copyRow)  
Next  
```  
  
```csharp  
DataSet customerDataSet = new DataSet();  
customerDataSet.Tables.Add(new DataTable("Customers"));  
customerDataSet.Tables["Customers"].Columns.Add("Name", typeof(string));  
customerDataSet.Tables["Customers"].Columns.Add("CountryRegion", typeof(string));  
customerDataSet.Tables["Customers"].Rows.Add("Juan", "Spain");  
customerDataSet.Tables["Customers"].Rows.Add("Johann", "Germany");  
customerDataSet.Tables["Customers"].Rows.Add("John", "UK");  
  
DataSet germanyCustomers = customerDataSet.Clone();  
  
DataRow[] copyRows =   
  customerDataSet.Tables["Customers"].Select("CountryRegion = 'Germany'");  
  
DataTable customerTable = germanyCustomers.Tables["Customers"];  
  
foreach (DataRow copyRow in copyRows)  
  customerTable.ImportRow(copyRow);  
```  
  
## <a name="see-also"></a><span data-ttu-id="d70ba-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="d70ba-121">See Also</span></span>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="d70ba-122">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="d70ba-122">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="d70ba-123">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="d70ba-123">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
