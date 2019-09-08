---
title: 在 DataTable 中檢視資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc
ms.openlocfilehash: c13f0b802b2714a17ea4014625a65ebd1b0011f4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785860"
---
# <a name="viewing-data-in-a-datatable"></a><span data-ttu-id="73acc-102">在 DataTable 中檢視資料</span><span class="sxs-lookup"><span data-stu-id="73acc-102">Viewing Data in a DataTable</span></span>

<span data-ttu-id="73acc-103">您<xref:System.Data.DataTable>可以使用**DataTable**的資料**列**和資料**行**集合來存取的內容。</span><span class="sxs-lookup"><span data-stu-id="73acc-103">You can access the contents of a <xref:System.Data.DataTable> by using the **Rows** and **Columns** collections of the **DataTable**.</span></span> <span data-ttu-id="73acc-104">您也可以使用<xref:System.Data.DataTable.Select%2A>方法，根據包含搜尋條件、排序次序和資料列狀態的準則，傳回**DataTable**中的資料子集。</span><span class="sxs-lookup"><span data-stu-id="73acc-104">You can also use the <xref:System.Data.DataTable.Select%2A> method to return subsets of the data in a **DataTable** according to criteria including search criteria, sort order, and row state.</span></span> <span data-ttu-id="73acc-105">此外，您可以在使用<xref:System.Data.DataRowCollection.Find%2A>主鍵值搜尋特定資料列時，使用**DataRowCollection**的方法。</span><span class="sxs-lookup"><span data-stu-id="73acc-105">Additionally, you can use the <xref:System.Data.DataRowCollection.Find%2A> method of the **DataRowCollection** when searching for a particular row using a primary key value.</span></span>

<span data-ttu-id="73acc-106">**選取**方法**DataTable**物件會傳回一組<xref:System.Data.DataRow>符合指定的準則的物件。</span><span class="sxs-lookup"><span data-stu-id="73acc-106">The **Select** method of the **DataTable** object returns a set of <xref:System.Data.DataRow> objects that match the specified criteria.</span></span> <span data-ttu-id="73acc-107">**選取** 採用的篩選條件運算式，排序運算式的選擇性引數和**DataViewRowState**。</span><span class="sxs-lookup"><span data-stu-id="73acc-107">**Select** takes optional arguments of a filter expression, sort expression, and **DataViewRowState**.</span></span> <span data-ttu-id="73acc-108">篩選條件運算式會根據**DataColumn**值識別要傳回的資料列，例如`LastName = 'Smith'`。</span><span class="sxs-lookup"><span data-stu-id="73acc-108">The filter expression identifies which rows to return based on **DataColumn** values, such as `LastName = 'Smith'`.</span></span> <span data-ttu-id="73acc-109">排序運算式會遵照標準的 SQL 慣例排序資料行，例如 `LastName ASC, FirstName ASC`。</span><span class="sxs-lookup"><span data-stu-id="73acc-109">The sort expression follows standard SQL conventions for ordering columns, for example `LastName ASC, FirstName ASC`.</span></span> <span data-ttu-id="73acc-110">如需撰寫運算式的相關規則， <xref:System.Data.DataColumn.Expression%2A>請參閱**DataColumn**類別的屬性。</span><span class="sxs-lookup"><span data-stu-id="73acc-110">For rules about writing expressions, see the <xref:System.Data.DataColumn.Expression%2A> property of the **DataColumn** class.</span></span>

> [!TIP]
> <span data-ttu-id="73acc-111">如果您正在執行的呼叫次數 **選取** 方法 **DataTable**，您可以藉由先建立提升效能 <xref:System.Data.DataView> 如 **DataTable**。</span><span class="sxs-lookup"><span data-stu-id="73acc-111">If you are performing a number of calls to the **Select** method of a **DataTable**, you can increase performance by first creating a <xref:System.Data.DataView> for the **DataTable**.</span></span> <span data-ttu-id="73acc-112">建立**DataView**索引資料表的資料列。</span><span class="sxs-lookup"><span data-stu-id="73acc-112">Creating the **DataView** indexes the rows of the table.</span></span> <span data-ttu-id="73acc-113">然後， **Select**方法會使用該索引，大幅減少產生查詢結果的時間。</span><span class="sxs-lookup"><span data-stu-id="73acc-113">The **Select** method then uses that index, significantly reducing the time to generate the query result.</span></span> <span data-ttu-id="73acc-114">如需建立**DataTable**的**DataView**的詳細資訊，請參閱[dataview](dataviews.md)。</span><span class="sxs-lookup"><span data-stu-id="73acc-114">For information about creating a **DataView** for a **DataTable**, see [DataViews](dataviews.md).</span></span>

<span data-ttu-id="73acc-115">**選取**方法會判斷要檢視或管理的資料列的版本將會根據<xref:System.Data.DataViewRowState>。</span><span class="sxs-lookup"><span data-stu-id="73acc-115">The **Select** method determines which version of the rows to view or manipulate based on a <xref:System.Data.DataViewRowState>.</span></span> <span data-ttu-id="73acc-116">下表描述可能的**DataViewRowState**列舉值。</span><span class="sxs-lookup"><span data-stu-id="73acc-116">The following table describes the possible **DataViewRowState** enumeration values.</span></span>

|<span data-ttu-id="73acc-117">DataViewRowState 值</span><span class="sxs-lookup"><span data-stu-id="73acc-117">DataViewRowState value</span></span>|<span data-ttu-id="73acc-118">說明</span><span class="sxs-lookup"><span data-stu-id="73acc-118">Description</span></span>|
|----------------------------|-----------------|
|<span data-ttu-id="73acc-119">**CurrentRows**</span><span class="sxs-lookup"><span data-stu-id="73acc-119">**CurrentRows**</span></span>|<span data-ttu-id="73acc-120">目前資料列，包括未變更、加入和修改過的資料列。</span><span class="sxs-lookup"><span data-stu-id="73acc-120">Current rows including unchanged, added, and modified rows.</span></span>|
|<span data-ttu-id="73acc-121">**刪除**</span><span class="sxs-lookup"><span data-stu-id="73acc-121">**Deleted**</span></span>|<span data-ttu-id="73acc-122">刪除的資料列。</span><span class="sxs-lookup"><span data-stu-id="73acc-122">A deleted row.</span></span>|
|<span data-ttu-id="73acc-123">**ModifiedCurrent**</span><span class="sxs-lookup"><span data-stu-id="73acc-123">**ModifiedCurrent**</span></span>|<span data-ttu-id="73acc-124">目前的版本，即為原始資料的修改版本</span><span class="sxs-lookup"><span data-stu-id="73acc-124">A current version, which is a modified version of original data.</span></span> <span data-ttu-id="73acc-125">（請參閱**ModifiedOriginal**）。</span><span class="sxs-lookup"><span data-stu-id="73acc-125">(See **ModifiedOriginal**.)</span></span>|
|<span data-ttu-id="73acc-126">**ModifiedOriginal**</span><span class="sxs-lookup"><span data-stu-id="73acc-126">**ModifiedOriginal**</span></span>|<span data-ttu-id="73acc-127">所有修改資料列的原始版本。</span><span class="sxs-lookup"><span data-stu-id="73acc-127">The original version of all modified rows.</span></span> <span data-ttu-id="73acc-128">您可以使用**ModifiedCurrent**來取得目前的版本。</span><span class="sxs-lookup"><span data-stu-id="73acc-128">The current version is available using **ModifiedCurrent**.</span></span>|
|<span data-ttu-id="73acc-129">**加入**</span><span class="sxs-lookup"><span data-stu-id="73acc-129">**Added**</span></span>|<span data-ttu-id="73acc-130">新的資料列。</span><span class="sxs-lookup"><span data-stu-id="73acc-130">A new row.</span></span>|
|<span data-ttu-id="73acc-131">**無**</span><span class="sxs-lookup"><span data-stu-id="73acc-131">**None**</span></span>|<span data-ttu-id="73acc-132">無。</span><span class="sxs-lookup"><span data-stu-id="73acc-132">None.</span></span>|
|<span data-ttu-id="73acc-133">**OriginalRows**</span><span class="sxs-lookup"><span data-stu-id="73acc-133">**OriginalRows**</span></span>|<span data-ttu-id="73acc-134">原始資料列，包括未變更和刪除的資料列。</span><span class="sxs-lookup"><span data-stu-id="73acc-134">Original rows, including unchanged and deleted rows.</span></span>|
|<span data-ttu-id="73acc-135">**任何**</span><span class="sxs-lookup"><span data-stu-id="73acc-135">**Unchanged**</span></span>|<span data-ttu-id="73acc-136">未變更的資料列。</span><span class="sxs-lookup"><span data-stu-id="73acc-136">An unchanged row.</span></span>|

<span data-ttu-id="73acc-137">在下列範例中，會篩選 DataSet 物件，讓您只能使用其**DataViewRowState**設定為**CurrentRows**的**資料**列。</span><span class="sxs-lookup"><span data-stu-id="73acc-137">In the following example, the **DataSet** object is filtered so that you are only working with rows whose **DataViewRowState** is set to **CurrentRows**.</span></span>

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

<span data-ttu-id="73acc-138">**選取 **方法可用來傳回具有不同的資料列**RowState**值或欄位值。</span><span class="sxs-lookup"><span data-stu-id="73acc-138">The **Select** method can be used to return rows with differing **RowState** values or field values.</span></span> <span data-ttu-id="73acc-139">下列範例會傳回一個**datarow**陣列，它會參考所有已刪除的資料列，並傳回另一個以**CustLName**排序的**datarow**陣列，其中**CustID**資料行大於5。</span><span class="sxs-lookup"><span data-stu-id="73acc-139">The following example returns a **DataRow** array that references all rows that have been deleted, and returns another **DataRow** array that references all rows, ordered by **CustLName**, where the **CustID** column is greater than 5.</span></span> <span data-ttu-id="73acc-140">如需如何在**已刪除**的資料列中查看資訊的詳細資訊，請參閱資料[列狀態和資料列版本](row-states-and-row-versions.md)。</span><span class="sxs-lookup"><span data-stu-id="73acc-140">For information about how to view the information in the **Deleted** row, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="73acc-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73acc-141">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataViewRowState>
- [<span data-ttu-id="73acc-142">在 DataTable 中操作資料</span><span class="sxs-lookup"><span data-stu-id="73acc-142">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="73acc-143">資料列狀態和資料列版本</span><span class="sxs-lookup"><span data-stu-id="73acc-143">Row States and Row Versions</span></span>](row-states-and-row-versions.md)
- [<span data-ttu-id="73acc-144">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="73acc-144">ADO.NET Overview</span></span>](../ado-net-overview.md)
