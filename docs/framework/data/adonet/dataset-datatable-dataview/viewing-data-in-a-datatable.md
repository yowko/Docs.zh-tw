---
title: 在 DataTable 中檢視資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc
ms.openlocfilehash: fa8749550e10256ee0623714cc95e03a838655c8
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364485"
---
# <a name="viewing-data-in-a-datatable"></a><span data-ttu-id="7e6f5-102">在 DataTable 中檢視資料</span><span class="sxs-lookup"><span data-stu-id="7e6f5-102">Viewing Data in a DataTable</span></span>

<span data-ttu-id="7e6f5-103">您可以存取的內容<xref:System.Data.DataTable>利用**資料列**並**資料行**的集合**DataTable**。</span><span class="sxs-lookup"><span data-stu-id="7e6f5-103">You can access the contents of a <xref:System.Data.DataTable> by using the **Rows** and **Columns** collections of the **DataTable**.</span></span> <span data-ttu-id="7e6f5-104">您也可以使用<xref:System.Data.DataTable.Select%2A>方法來傳回中的資料子集**DataTable**根據包括搜尋條件的準則，排序順序和資料列狀態。</span><span class="sxs-lookup"><span data-stu-id="7e6f5-104">You can also use the <xref:System.Data.DataTable.Select%2A> method to return subsets of the data in a **DataTable** according to criteria including search criteria, sort order, and row state.</span></span> <span data-ttu-id="7e6f5-105">此外，您可以使用<xref:System.Data.DataRowCollection.Find%2A>方法**DataRowCollection**時搜尋特定的資料列，使用主索引鍵值。</span><span class="sxs-lookup"><span data-stu-id="7e6f5-105">Additionally, you can use the <xref:System.Data.DataRowCollection.Find%2A> method of the **DataRowCollection** when searching for a particular row using a primary key value.</span></span>

<span data-ttu-id="7e6f5-106">**選取**方法**DataTable**物件會傳回一組<xref:System.Data.DataRow>符合指定的準則的物件。</span><span class="sxs-lookup"><span data-stu-id="7e6f5-106">The **Select** method of the **DataTable** object returns a set of <xref:System.Data.DataRow> objects that match the specified criteria.</span></span> <span data-ttu-id="7e6f5-107">**選取 **採用的篩選條件運算式，排序運算式的選擇性引數和**DataViewRowState**。</span><span class="sxs-lookup"><span data-stu-id="7e6f5-107">**Select** takes optional arguments of a filter expression, sort expression, and **DataViewRowState**.</span></span> <span data-ttu-id="7e6f5-108">篩選條件運算式會識別要根據傳回的資料列**DataColumn**值，例如`LastName = 'Smith'`。</span><span class="sxs-lookup"><span data-stu-id="7e6f5-108">The filter expression identifies which rows to return based on **DataColumn** values, such as `LastName = 'Smith'`.</span></span> <span data-ttu-id="7e6f5-109">排序運算式會遵照標準的 SQL 慣例排序資料行，例如 `LastName ASC, FirstName ASC`。</span><span class="sxs-lookup"><span data-stu-id="7e6f5-109">The sort expression follows standard SQL conventions for ordering columns, for example `LastName ASC, FirstName ASC`.</span></span> <span data-ttu-id="7e6f5-110">如需有關撰寫運算式的規則，請參閱<xref:System.Data.DataColumn.Expression%2A>的屬性**DataColumn**類別。</span><span class="sxs-lookup"><span data-stu-id="7e6f5-110">For rules about writing expressions, see the <xref:System.Data.DataColumn.Expression%2A> property of the **DataColumn** class.</span></span>

> [!TIP]
> <span data-ttu-id="7e6f5-111">如果您正在執行的呼叫次數 **選取** 方法 **DataTable**，您可以藉由先建立提升效能 <xref:System.Data.DataView> 如 **DataTable**。</span><span class="sxs-lookup"><span data-stu-id="7e6f5-111">If you are performing a number of calls to the **Select** method of a **DataTable**, you can increase performance by first creating a <xref:System.Data.DataView> for the **DataTable**.</span></span> <span data-ttu-id="7e6f5-112">建立**DataView**資料表的資料列的索引。</span><span class="sxs-lookup"><span data-stu-id="7e6f5-112">Creating the **DataView** indexes the rows of the table.</span></span> <span data-ttu-id="7e6f5-113">**選取**方法接著會使用該索引，大幅減少產生查詢結果的時間。</span><span class="sxs-lookup"><span data-stu-id="7e6f5-113">The **Select** method then uses that index, significantly reducing the time to generate the query result.</span></span> <span data-ttu-id="7e6f5-114">如需建立資訊**DataView** for **DataTable**，請參閱[Dataview](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)。</span><span class="sxs-lookup"><span data-stu-id="7e6f5-114">For information about creating a **DataView** for a **DataTable**, see [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md).</span></span>

<span data-ttu-id="7e6f5-115">**選取**方法會判斷要檢視或管理的資料列的版本將會根據<xref:System.Data.DataViewRowState>。</span><span class="sxs-lookup"><span data-stu-id="7e6f5-115">The **Select** method determines which version of the rows to view or manipulate based on a <xref:System.Data.DataViewRowState>.</span></span> <span data-ttu-id="7e6f5-116">下表描述可能**DataViewRowState**列舉值。</span><span class="sxs-lookup"><span data-stu-id="7e6f5-116">The following table describes the possible **DataViewRowState** enumeration values.</span></span>

|<span data-ttu-id="7e6f5-117">DataViewRowState 值</span><span class="sxs-lookup"><span data-stu-id="7e6f5-117">DataViewRowState value</span></span>|<span data-ttu-id="7e6f5-118">描述</span><span class="sxs-lookup"><span data-stu-id="7e6f5-118">Description</span></span>|
|----------------------------|-----------------|
|<span data-ttu-id="7e6f5-119">**CurrentRows**</span><span class="sxs-lookup"><span data-stu-id="7e6f5-119">**CurrentRows**</span></span>|<span data-ttu-id="7e6f5-120">目前資料列，包括未變更、加入和修改過的資料列。</span><span class="sxs-lookup"><span data-stu-id="7e6f5-120">Current rows including unchanged, added, and modified rows.</span></span>|
|<span data-ttu-id="7e6f5-121">**刪除**</span><span class="sxs-lookup"><span data-stu-id="7e6f5-121">**Deleted**</span></span>|<span data-ttu-id="7e6f5-122">刪除的資料列。</span><span class="sxs-lookup"><span data-stu-id="7e6f5-122">A deleted row.</span></span>|
|<span data-ttu-id="7e6f5-123">**ModifiedCurrent**</span><span class="sxs-lookup"><span data-stu-id="7e6f5-123">**ModifiedCurrent**</span></span>|<span data-ttu-id="7e6f5-124">目前的版本，即為原始資料的修改版本</span><span class="sxs-lookup"><span data-stu-id="7e6f5-124">A current version, which is a modified version of original data.</span></span> <span data-ttu-id="7e6f5-125">(請參閱**ModifiedOriginal**。)</span><span class="sxs-lookup"><span data-stu-id="7e6f5-125">(See **ModifiedOriginal**.)</span></span>|
|<span data-ttu-id="7e6f5-126">**ModifiedOriginal**</span><span class="sxs-lookup"><span data-stu-id="7e6f5-126">**ModifiedOriginal**</span></span>|<span data-ttu-id="7e6f5-127">所有修改資料列的原始版本。</span><span class="sxs-lookup"><span data-stu-id="7e6f5-127">The original version of all modified rows.</span></span> <span data-ttu-id="7e6f5-128">目前的版本是可透過**ModifiedCurrent**。</span><span class="sxs-lookup"><span data-stu-id="7e6f5-128">The current version is available using **ModifiedCurrent**.</span></span>|
|<span data-ttu-id="7e6f5-129">**加入**</span><span class="sxs-lookup"><span data-stu-id="7e6f5-129">**Added**</span></span>|<span data-ttu-id="7e6f5-130">新的資料列。</span><span class="sxs-lookup"><span data-stu-id="7e6f5-130">A new row.</span></span>|
|<span data-ttu-id="7e6f5-131">**無**</span><span class="sxs-lookup"><span data-stu-id="7e6f5-131">**None**</span></span>|<span data-ttu-id="7e6f5-132">無。</span><span class="sxs-lookup"><span data-stu-id="7e6f5-132">None.</span></span>|
|<span data-ttu-id="7e6f5-133">**OriginalRows**</span><span class="sxs-lookup"><span data-stu-id="7e6f5-133">**OriginalRows**</span></span>|<span data-ttu-id="7e6f5-134">原始資料列，包括未變更和刪除的資料列。</span><span class="sxs-lookup"><span data-stu-id="7e6f5-134">Original rows, including unchanged and deleted rows.</span></span>|
|<span data-ttu-id="7e6f5-135">**未變更**</span><span class="sxs-lookup"><span data-stu-id="7e6f5-135">**Unchanged**</span></span>|<span data-ttu-id="7e6f5-136">未變更的資料列。</span><span class="sxs-lookup"><span data-stu-id="7e6f5-136">An unchanged row.</span></span>|

<span data-ttu-id="7e6f5-137">在下列範例中，**資料集**物件會經過篩選，因此您只需使用資料列其**DataViewRowState**設定為**CurrentRows**。</span><span class="sxs-lookup"><span data-stu-id="7e6f5-137">In the following example, the **DataSet** object is filtered so that you are only working with rows whose **DataViewRowState** is set to **CurrentRows**.</span></span>

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

<span data-ttu-id="7e6f5-138">**選取 **方法可用來傳回具有不同的資料列**RowState**值或欄位值。</span><span class="sxs-lookup"><span data-stu-id="7e6f5-138">The **Select** method can be used to return rows with differing **RowState** values or field values.</span></span> <span data-ttu-id="7e6f5-139">下列範例會傳回**DataRow**參考已刪除，並傳回另一個的所有資料列的陣列**DataRow**陣列參考的所有資料列，依**CustLName**，其中**CustID**資料行大於 5。</span><span class="sxs-lookup"><span data-stu-id="7e6f5-139">The following example returns a **DataRow** array that references all rows that have been deleted, and returns another **DataRow** array that references all rows, ordered by **CustLName**, where the **CustID** column is greater than 5.</span></span> <span data-ttu-id="7e6f5-140">如需有關如何檢視中的資訊資訊**Deleted**資料列中，請參閱[資料列狀態和資料列版本](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)。</span><span class="sxs-lookup"><span data-stu-id="7e6f5-140">For information about how to view the information in the **Deleted** row, see [Row States and Row Versions](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7e6f5-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e6f5-141">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataViewRowState>
- [<span data-ttu-id="7e6f5-142">在 DataTable 中操作資料</span><span class="sxs-lookup"><span data-stu-id="7e6f5-142">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="7e6f5-143">資料列狀態和資料列版本</span><span class="sxs-lookup"><span data-stu-id="7e6f5-143">Row States and Row Versions</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)
- [<span data-ttu-id="7e6f5-144">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="7e6f5-144">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
