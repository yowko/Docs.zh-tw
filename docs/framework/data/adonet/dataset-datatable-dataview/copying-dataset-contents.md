---
title: 複製資料集內容
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
ms.openlocfilehash: d8a7762c4ec5d650295ca0626180285723549051
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786522"
---
# <a name="copying-dataset-contents"></a><span data-ttu-id="1aa73-102">複製資料集內容</span><span class="sxs-lookup"><span data-stu-id="1aa73-102">Copying DataSet Contents</span></span>
<span data-ttu-id="1aa73-103">您可以建立的複本<xref:System.Data.DataSet> ，如此一來，您就可以使用資料，而不會影響原始資料，或從資料**集**使用資料的子集。</span><span class="sxs-lookup"><span data-stu-id="1aa73-103">You can create a copy of a <xref:System.Data.DataSet> so that you can work with data without affecting the original data, or work with a subset of the data from a **DataSet**.</span></span> <span data-ttu-id="1aa73-104">複製**資料集**時，您可以：</span><span class="sxs-lookup"><span data-stu-id="1aa73-104">When copying a **DataSet**, you can:</span></span>  
  
- <span data-ttu-id="1aa73-105">建立**資料集**的完全複本，包括架構、資料、資料列狀態資訊和資料列版本。</span><span class="sxs-lookup"><span data-stu-id="1aa73-105">Create an exact copy of the **DataSet**, including the schema, data, row state information, and row versions.</span></span>  
  
- <span data-ttu-id="1aa73-106">建立包含現有**資料集**之架構的**資料集**，但只有已修改的資料列。</span><span class="sxs-lookup"><span data-stu-id="1aa73-106">Create a **DataSet** that contains the schema of an existing **DataSet**, but only rows that have been modified.</span></span> <span data-ttu-id="1aa73-107">您可以傳回所有已修改的資料列，或指定特定的**DataRowState**。</span><span class="sxs-lookup"><span data-stu-id="1aa73-107">You can return all rows that have been modified, or specify a specific **DataRowState**.</span></span> <span data-ttu-id="1aa73-108">如需資料列狀態的詳細資訊，請參閱資料[列狀態和資料列版本](row-states-and-row-versions.md)。</span><span class="sxs-lookup"><span data-stu-id="1aa73-108">For more information about row states, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
- <span data-ttu-id="1aa73-109">只複製**資料集**的架構或關聯式結構，而不復制任何資料列。</span><span class="sxs-lookup"><span data-stu-id="1aa73-109">Copy the schema, or relational structure, of the **DataSet** only, without copying any rows.</span></span> <span data-ttu-id="1aa73-110">使用 <xref:System.Data.DataTable>，可以將資料列匯入現有的 <xref:System.Data.DataTable.ImportRow%2A>。</span><span class="sxs-lookup"><span data-stu-id="1aa73-110">Rows can be imported into an existing <xref:System.Data.DataTable> using <xref:System.Data.DataTable.ImportRow%2A>.</span></span>  
  
 <span data-ttu-id="1aa73-111">若要建立包含架構和資料之**資料集**的完全相同複本，請使用<xref:System.Data.DataSet.Copy%2A> **資料集**的方法。</span><span class="sxs-lookup"><span data-stu-id="1aa73-111">To create an exact copy of the **DataSet** that includes both schema and data, use the <xref:System.Data.DataSet.Copy%2A> method of the **DataSet**.</span></span> <span data-ttu-id="1aa73-112">下列程式碼範例示範如何建立**資料集**的完全相同複本。</span><span class="sxs-lookup"><span data-stu-id="1aa73-112">The following code example shows how to create an exact copy of the **DataSet**.</span></span>  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 <span data-ttu-id="1aa73-113">若要建立**資料集**的複本，其中包含架構，而且只有代表**已加入**、**已修改**或**已刪除**之資料<xref:System.Data.DataSet.GetChanges%2A>列的資料，請使用**資料集**的方法。</span><span class="sxs-lookup"><span data-stu-id="1aa73-113">To create a copy of a **DataSet** that includes schema and only the data representing **Added**, **Modified**, or **Deleted** rows, use the <xref:System.Data.DataSet.GetChanges%2A> method of the **DataSet**.</span></span> <span data-ttu-id="1aa73-114">您也可以使用**GetChanges** ，在呼叫**GetChanges**時傳遞**DataRowState**值，只傳回具有指定資料列狀態的資料列。</span><span class="sxs-lookup"><span data-stu-id="1aa73-114">You can also use **GetChanges** to return only rows with a specified row state by passing a **DataRowState** value when calling **GetChanges**.</span></span> <span data-ttu-id="1aa73-115">下列程式碼範例顯示如何在呼叫**GetChanges**時傳遞**DataRowState** 。</span><span class="sxs-lookup"><span data-stu-id="1aa73-115">The following code example shows how to pass a **DataRowState** when calling **GetChanges**.</span></span>  
  
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
  
 <span data-ttu-id="1aa73-116">若要建立只包含架構的**資料集**複本，請使用<xref:System.Data.DataSet.Clone%2A> **資料集**的方法。</span><span class="sxs-lookup"><span data-stu-id="1aa73-116">To create a copy of a **DataSet** that only includes schema, use the <xref:System.Data.DataSet.Clone%2A> method of the **DataSet**.</span></span> <span data-ttu-id="1aa73-117">您也可以使用**DataTable**的**ImportRow**方法，將現有的資料列加入至複製的**資料集**。</span><span class="sxs-lookup"><span data-stu-id="1aa73-117">You can also add existing rows to the cloned **DataSet** using the **ImportRow** method of the **DataTable**.</span></span> <span data-ttu-id="1aa73-118">**ImportRow**會將資料、資料列狀態和資料列版本資訊加入至指定的資料表。</span><span class="sxs-lookup"><span data-stu-id="1aa73-118">**ImportRow** adds data, row state, and row version information to the specified table.</span></span> <span data-ttu-id="1aa73-119">資料行值只會被加入資料行名稱相符且資料型別相容之處。</span><span class="sxs-lookup"><span data-stu-id="1aa73-119">Column values are added only where the column name matches and the data type is compatible.</span></span>  
  
 <span data-ttu-id="1aa73-120">下列程式碼範例會建立**資料集**的複製品，然後將原始**資料集**的資料列加入至**資料集**複製品中的**Customers**資料表，其中**國家/地區**資料行的值為 "德國".</span><span class="sxs-lookup"><span data-stu-id="1aa73-120">The following code example creates a clone of a **DataSet** and then adds the rows from the original **DataSet** to the **Customers** table in the **DataSet** clone for customers where the **CountryRegion** column has the value "Germany".</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1aa73-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1aa73-121">See also</span></span>

- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="1aa73-122">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="1aa73-122">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="1aa73-123">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="1aa73-123">ADO.NET Overview</span></span>](../ado-net-overview.md)
