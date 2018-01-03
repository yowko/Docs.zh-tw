---
title: "在 DataTable 中檢視資料"
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
ms.assetid: 1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ab7a60b4195f3d8976a61e3909682b3748e30341
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="viewing-data-in-a-datatable"></a><span data-ttu-id="8ab1d-102">在 DataTable 中檢視資料</span><span class="sxs-lookup"><span data-stu-id="8ab1d-102">Viewing Data in a DataTable</span></span>
<span data-ttu-id="8ab1d-103">您可以存取的內容<xref:System.Data.DataTable>使用**列**和**資料行**集合**DataTable**。</span><span class="sxs-lookup"><span data-stu-id="8ab1d-103">You can access the contents of a <xref:System.Data.DataTable> by using the **Rows** and **Columns** collections of the **DataTable**.</span></span> <span data-ttu-id="8ab1d-104">您也可以使用<xref:System.Data.DataTable.Select%2A>方法來傳回中的資料子集**DataTable**根據包括搜尋條件的準則，排序順序，與資料列狀態。</span><span class="sxs-lookup"><span data-stu-id="8ab1d-104">You can also use the <xref:System.Data.DataTable.Select%2A> method to return subsets of the data in a **DataTable** according to criteria including search criteria, sort order, and row state.</span></span> <span data-ttu-id="8ab1d-105">此外，您可以使用<xref:System.Data.DataRowCollection.Find%2A>方法**DataRowCollection**搜尋特定的資料列，使用主索引鍵值時。</span><span class="sxs-lookup"><span data-stu-id="8ab1d-105">Additionally, you can use the <xref:System.Data.DataRowCollection.Find%2A> method of the **DataRowCollection** when searching for a particular row using a primary key value.</span></span>  
  
 <span data-ttu-id="8ab1d-106">**選取**方法**DataTable**物件會傳回一組<xref:System.Data.DataRow>符合指定的準則的物件。</span><span class="sxs-lookup"><span data-stu-id="8ab1d-106">The **Select** method of the **DataTable** object returns a set of <xref:System.Data.DataRow> objects that match the specified criteria.</span></span> <span data-ttu-id="8ab1d-107">**選取**接受選擇性引數的篩選運算式，排序運算式和**DataViewRowState**。</span><span class="sxs-lookup"><span data-stu-id="8ab1d-107">**Select** takes optional arguments of a filter expression, sort expression, and **DataViewRowState**.</span></span> <span data-ttu-id="8ab1d-108">篩選條件運算式會識別要根據傳回的資料列**DataColumn**值，例如`LastName = 'Smith'`。</span><span class="sxs-lookup"><span data-stu-id="8ab1d-108">The filter expression identifies which rows to return based on **DataColumn** values, such as `LastName = 'Smith'`.</span></span> <span data-ttu-id="8ab1d-109">排序運算式會遵照標準的 SQL 慣例排序資料行，例如 `LastName ASC, FirstName ASC`。</span><span class="sxs-lookup"><span data-stu-id="8ab1d-109">The sort expression follows standard SQL conventions for ordering columns, for example `LastName ASC, FirstName ASC`.</span></span> <span data-ttu-id="8ab1d-110">如需有關撰寫運算式的規則，請參閱<xref:System.Data.DataColumn.Expression%2A>屬性**DataColumn**類別。</span><span class="sxs-lookup"><span data-stu-id="8ab1d-110">For rules about writing expressions, see the <xref:System.Data.DataColumn.Expression%2A> property of the **DataColumn** class.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="8ab1d-111">如果您正在執行的呼叫程序數**選取**方法**DataTable**，您可以先建立，以提升效能<xref:System.Data.DataView>如**DataTable**。</span><span class="sxs-lookup"><span data-stu-id="8ab1d-111">If you are performing a number of calls to the **Select** method of a **DataTable**, you can increase performance by first creating a <xref:System.Data.DataView> for the **DataTable**.</span></span> <span data-ttu-id="8ab1d-112">建立**DataView**編製索引之資料表的資料列。</span><span class="sxs-lookup"><span data-stu-id="8ab1d-112">Creating the **DataView** indexes the rows of the table.</span></span> <span data-ttu-id="8ab1d-113">**選取**方法則了建立索引，大幅減少產生查詢結果的時間。</span><span class="sxs-lookup"><span data-stu-id="8ab1d-113">The **Select** method then usees that index, significantly reducing the time to generate the query result.</span></span> <span data-ttu-id="8ab1d-114">如需建立資訊**DataView**如**DataTable**，請參閱[Dataview](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)。</span><span class="sxs-lookup"><span data-stu-id="8ab1d-114">For information about creating a **DataView** for a **DataTable**, see [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md).</span></span>  
  
 <span data-ttu-id="8ab1d-115">**選取**方法會判斷要檢視或管理的資料列的版本將會根據<xref:System.Data.DataViewRowState>。</span><span class="sxs-lookup"><span data-stu-id="8ab1d-115">The **Select** method determines which version of the rows to view or manipulate based on a <xref:System.Data.DataViewRowState>.</span></span> <span data-ttu-id="8ab1d-116">下表描述可能的**DataViewRowState**列舉值。</span><span class="sxs-lookup"><span data-stu-id="8ab1d-116">The following table describes the possible **DataViewRowState** enumeration values.</span></span>  
  
|<span data-ttu-id="8ab1d-117">DataViewRowState 值</span><span class="sxs-lookup"><span data-stu-id="8ab1d-117">DataViewRowState value</span></span>|<span data-ttu-id="8ab1d-118">描述</span><span class="sxs-lookup"><span data-stu-id="8ab1d-118">Description</span></span>|  
|----------------------------|-----------------|  
|<span data-ttu-id="8ab1d-119">**CurrentRows**</span><span class="sxs-lookup"><span data-stu-id="8ab1d-119">**CurrentRows**</span></span>|<span data-ttu-id="8ab1d-120">目前資料列，包括未變更、加入和修改過的資料列。</span><span class="sxs-lookup"><span data-stu-id="8ab1d-120">Current rows including unchanged, added, and modified rows.</span></span>|  
|<span data-ttu-id="8ab1d-121">**刪除**</span><span class="sxs-lookup"><span data-stu-id="8ab1d-121">**Deleted**</span></span>|<span data-ttu-id="8ab1d-122">刪除的資料列。</span><span class="sxs-lookup"><span data-stu-id="8ab1d-122">A deleted row.</span></span>|  
|<span data-ttu-id="8ab1d-123">**ModifiedCurrent**</span><span class="sxs-lookup"><span data-stu-id="8ab1d-123">**ModifiedCurrent**</span></span>|<span data-ttu-id="8ab1d-124">目前的版本，即為原始資料的修改版本</span><span class="sxs-lookup"><span data-stu-id="8ab1d-124">A current version, which is a modified version of original data.</span></span> <span data-ttu-id="8ab1d-125">(請參閱**ModifiedOriginal**。)</span><span class="sxs-lookup"><span data-stu-id="8ab1d-125">(See **ModifiedOriginal**.)</span></span>|  
|<span data-ttu-id="8ab1d-126">**ModifiedOriginal**</span><span class="sxs-lookup"><span data-stu-id="8ab1d-126">**ModifiedOriginal**</span></span>|<span data-ttu-id="8ab1d-127">所有修改資料列的原始版本。</span><span class="sxs-lookup"><span data-stu-id="8ab1d-127">The original version of all modified rows.</span></span> <span data-ttu-id="8ab1d-128">目前的版本是提供使用**ModifiedCurrent**。</span><span class="sxs-lookup"><span data-stu-id="8ab1d-128">The current version is available using **ModifiedCurrent**.</span></span>|  
|<span data-ttu-id="8ab1d-129">**加入**</span><span class="sxs-lookup"><span data-stu-id="8ab1d-129">**Added**</span></span>|<span data-ttu-id="8ab1d-130">新的資料列。</span><span class="sxs-lookup"><span data-stu-id="8ab1d-130">A new row.</span></span>|  
|<span data-ttu-id="8ab1d-131">**無**</span><span class="sxs-lookup"><span data-stu-id="8ab1d-131">**None**</span></span>|<span data-ttu-id="8ab1d-132">無。</span><span class="sxs-lookup"><span data-stu-id="8ab1d-132">None.</span></span>|  
|<span data-ttu-id="8ab1d-133">**OriginalRows**</span><span class="sxs-lookup"><span data-stu-id="8ab1d-133">**OriginalRows**</span></span>|<span data-ttu-id="8ab1d-134">原始資料列，包括未變更和刪除的資料列。</span><span class="sxs-lookup"><span data-stu-id="8ab1d-134">Original rows, including unchanged and deleted rows.</span></span>|  
|<span data-ttu-id="8ab1d-135">**不變**</span><span class="sxs-lookup"><span data-stu-id="8ab1d-135">**Unchanged**</span></span>|<span data-ttu-id="8ab1d-136">未變更的資料列。</span><span class="sxs-lookup"><span data-stu-id="8ab1d-136">An unchanged row.</span></span>|  
  
 <span data-ttu-id="8ab1d-137">在下列範例中，**資料集**物件已經過篩選，讓您只使用資料列的**DataViewRowState**設**CurrentRows**。</span><span class="sxs-lookup"><span data-stu-id="8ab1d-137">In the following example, the **DataSet** object is filtered so that you are only working with rows whose **DataViewRowState** is set to **CurrentRows**.</span></span>  
  
```vb  
Dim column As DataColumn  
Dim row As DataRow  
  
Dim currentRows() As DataRow = _  
    workTable.Select(Nothing, Nothing, DataViewRowState.CurrentRows)  
  
If (currentRows.Length < 1 ) Then  
  Console.WriteLine("No Current Rows Found")  
Else  
  For Each column in workTable.Columns  
    Console.Write(vbTab & column.ColumnName)  
  Next  
  
  Console.WriteLine(vbTab & "RowState")  
  
  For Each row In currentRows  
    For Each column In workTable.Columns  
      Console.Write(vbTab & row(column).ToString())  
    Next  
  
    Dim rowState As String = _  
        System.Enum.GetName(row.RowState.GetType(), row.RowState)  
    Console.WriteLine(vbTab & rowState)  
  Next  
End If  
```  
  
```csharp  
DataRow[] currentRows = workTable.Select(  
    null, null, DataViewRowState.CurrentRows);  
  
if (currentRows.Length < 1 )  
  Console.WriteLine("No Current Rows Found");  
else  
{  
  foreach (DataColumn column in workTable.Columns)  
    Console.Write("\t{0}", column.ColumnName);  
  
  Console.WriteLine("\tRowState");  
  
  foreach (DataRow row in currentRows)  
  {  
    foreach (DataColumn column in workTable.Columns)  
      Console.Write("\t{0}", row[column]);  
  
    Console.WriteLine("\t" + row.RowState);  
  }  
}  
```  
  
 <span data-ttu-id="8ab1d-138">**選取**方法可以用來傳回具有不同的資料列**RowState**值或欄位值。</span><span class="sxs-lookup"><span data-stu-id="8ab1d-138">The **Select** method can be used to return rows with differing **RowState** values or field values.</span></span> <span data-ttu-id="8ab1d-139">下列範例會傳回**DataRow**參考所有資料列已刪除，並傳回另一個陣列**DataRow**陣列所參考的所有資料列，依**CustLName**，其中**CustID**資料行大於 5。</span><span class="sxs-lookup"><span data-stu-id="8ab1d-139">The following example returns a **DataRow** array that references all rows that have been deleted, and returns another **DataRow** array that references all rows, ordered by **CustLName**, where the **CustID** column is greater than 5.</span></span> <span data-ttu-id="8ab1d-140">如需有關如何檢視中的資訊資訊**刪除**資料列中，請參閱[資料列狀態和資料列版本](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)。</span><span class="sxs-lookup"><span data-stu-id="8ab1d-140">For information about how to view the information in the **Deleted** row, see [Row States and Row Versions](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span>  
  
```vb  
' Retrieve all deleted rows.  
Dim deletedRows() As DataRow = workTable.Select(Nothing, Nothing, DataViewRowState.Deleted)  
  
' Retrieve rows where CustID > 5, and order by CustLName.  
Dim custRows() As DataRow = workTable.Select( _  
    "CustID > 5", "CustLName ASC")  
```  
  
```csharp  
// Retrieve all deleted rows.  
DataRow[] deletedRows = workTable.Select(  
    null, null, DataViewRowState.Deleted);  
  
// Retrieve rows where CustID > 5, and order by CustLName.  
DataRow[] custRows = workTable.Select("CustID > 5", "CustLName ASC");  
```  
  
## <a name="see-also"></a><span data-ttu-id="8ab1d-141">請參閱</span><span class="sxs-lookup"><span data-stu-id="8ab1d-141">See Also</span></span>  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataViewRowState>  
 [<span data-ttu-id="8ab1d-142">在 DataTable 中操作資料</span><span class="sxs-lookup"><span data-stu-id="8ab1d-142">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="8ab1d-143">資料列狀態和資料列版本</span><span class="sxs-lookup"><span data-stu-id="8ab1d-143">Row States and Row Versions</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)  
 [<span data-ttu-id="8ab1d-144">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="8ab1d-144">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
