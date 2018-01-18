---
title: "資料列狀態和資料列版本"
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
ms.assetid: 2e6642c9-bfc6-425c-b3a7-e4912ffa6c1f
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6c37c33f5deda2d16e24fab77f394d97749ae63e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="row-states-and-row-versions"></a><span data-ttu-id="a655e-102">資料列狀態和資料列版本</span><span class="sxs-lookup"><span data-stu-id="a655e-102">Row States and Row Versions</span></span>
<span data-ttu-id="a655e-103">ADO.NET 使用資料列狀態和版本來管理資料表中的資料列。</span><span class="sxs-lookup"><span data-stu-id="a655e-103">ADO.NET manages rows in tables using row states and versions.</span></span> <span data-ttu-id="a655e-104">資料列狀態表示資料列的狀態；修改資料列時，資料列版本會維護存放在資料列中的值，包括目前值、原始值和預設值。</span><span class="sxs-lookup"><span data-stu-id="a655e-104">A row state indicates the status of a row; row versions maintain the values stored in a row as it is modified, including current, original, and default values.</span></span> <span data-ttu-id="a655e-105">例如，修改資料列中的資料行後，資料列的狀態為 `Modified`，並有兩個資料列版本：`Current` (包含目前的資料列值) 和 `Original` (包含修改資料行之前的資料列值)。</span><span class="sxs-lookup"><span data-stu-id="a655e-105">For example, after you have made a modification to a column in a row, the row will have a row state of `Modified`, and two row versions: `Current`, which contains the current row values, and `Original`, which contains the row values before the column was modified.</span></span>  
  
 <span data-ttu-id="a655e-106">每個 <xref:System.Data.DataRow> 物件都有 <xref:System.Data.DataRow.RowState%2A> 屬性，您可以檢查該屬性來判斷資料列的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="a655e-106">Each <xref:System.Data.DataRow> object has a <xref:System.Data.DataRow.RowState%2A> property that you can examine to determine the current state of the row.</span></span> <span data-ttu-id="a655e-107">下列表格簡短說明每個 `RowState` 列舉值。</span><span class="sxs-lookup"><span data-stu-id="a655e-107">The following table gives a brief description of each `RowState` enumeration value.</span></span>  
  
|<span data-ttu-id="a655e-108">RowState 值</span><span class="sxs-lookup"><span data-stu-id="a655e-108">RowState value</span></span>|<span data-ttu-id="a655e-109">描述</span><span class="sxs-lookup"><span data-stu-id="a655e-109">Description</span></span>|  
|--------------------|-----------------|  
|<xref:System.Data.DataRowState.Unchanged>|<span data-ttu-id="a655e-110">自上次呼叫 `AcceptChanges` 或由 `DataAdapter.Fill` 建立資料列後，沒有任何變更。</span><span class="sxs-lookup"><span data-stu-id="a655e-110">No changes have been made since the last call to `AcceptChanges` or since the row was created by `DataAdapter.Fill`.</span></span>|  
|<xref:System.Data.DataRowState.Added>|<span data-ttu-id="a655e-111">資料列已加入至資料表，但尚未呼叫 `AcceptChanges`。</span><span class="sxs-lookup"><span data-stu-id="a655e-111">The row has been added to the table, but `AcceptChanges` has not been called.</span></span>|  
|<xref:System.Data.DataRowState.Modified>|<span data-ttu-id="a655e-112">有些資料列項目已變更。</span><span class="sxs-lookup"><span data-stu-id="a655e-112">Some element of the row has been changed.</span></span>|  
|<xref:System.Data.DataRowState.Deleted>|<span data-ttu-id="a655e-113">已從資料表中刪除資料列，但是尚未呼叫 `AcceptChanges`。</span><span class="sxs-lookup"><span data-stu-id="a655e-113">The row has been deleted from a table, and `AcceptChanges` has not been called.</span></span>|  
|<xref:System.Data.DataRowState.Detached>|<span data-ttu-id="a655e-114">資料列不屬於任何 `DataRowCollection`。</span><span class="sxs-lookup"><span data-stu-id="a655e-114">The row is not part of any `DataRowCollection`.</span></span> <span data-ttu-id="a655e-115">已將新建立資料列的 `RowState` 設為 `Detached`。</span><span class="sxs-lookup"><span data-stu-id="a655e-115">The `RowState` of a newly created row is set to `Detached`.</span></span> <span data-ttu-id="a655e-116">呼叫 `DataRow` 方法以將新 `DataRowCollection` 加入至 `Add` 後，`RowState` 屬性的值會設為 `Added`。</span><span class="sxs-lookup"><span data-stu-id="a655e-116">After the new `DataRow` is added to the `DataRowCollection` by calling the `Add` method, the value of the `RowState` property is set to `Added`.</span></span><br /><br /> <span data-ttu-id="a655e-117">使用 `Detached` 方法，或是先使用 `DataRowCollection` 方法再使用 `Remove` 方法，從 `Delete` 中移除的資料列也會設定為 `AcceptChanges`。</span><span class="sxs-lookup"><span data-stu-id="a655e-117">`Detached` is also set for a row that has been removed from a `DataRowCollection` using the `Remove` method, or by the `Delete` method followed by the `AcceptChanges` method.</span></span>|  
  
 <span data-ttu-id="a655e-118">在 `AcceptChanges`、<xref:System.Data.DataSet> 或 <xref:System.Data.DataTable> 上呼叫 <xref:System.Data.DataRow> 時，具有 `Deleted` 資料列狀態的所有資料列都將移除。</span><span class="sxs-lookup"><span data-stu-id="a655e-118">When `AcceptChanges` is called on a <xref:System.Data.DataSet>, <xref:System.Data.DataTable> , or <xref:System.Data.DataRow>, all rows with a row state of `Deleted` are removed.</span></span> <span data-ttu-id="a655e-119">其餘資料列的狀態將設為 `Unchanged`，而 `Original` 資料列版本中的值將以 `Current` 資料列版本值覆寫。</span><span class="sxs-lookup"><span data-stu-id="a655e-119">The remaining rows are given a row state of `Unchanged`, and the values in the `Original` row version are overwritten with the `Current` row version values.</span></span> <span data-ttu-id="a655e-120">在呼叫 `RejectChanges` 時，所有狀態為 `Added` 的資料列都會移除。</span><span class="sxs-lookup"><span data-stu-id="a655e-120">When `RejectChanges` is called, all rows with a row state of `Added` are removed.</span></span> <span data-ttu-id="a655e-121">其餘資料列的狀態將設為 `Unchanged`，而 `Current` 資料列版本中的值將以 `Original` 資料列版本值覆寫。</span><span class="sxs-lookup"><span data-stu-id="a655e-121">The remaining rows are given a row state of `Unchanged`, and the values in the `Current` row version are overwritten with the `Original` row version values.</span></span>  
  
 <span data-ttu-id="a655e-122">您可以檢視資料列的不同資料列版本，方法是使用資料行參考傳遞 <xref:System.Data.DataRowVersion> 參數，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="a655e-122">You can view the different row versions of a row by passing a <xref:System.Data.DataRowVersion> parameter with the column reference, as shown in the following example.</span></span>  
  
```vb  
Dim custRow As DataRow = custTable.Rows(0)  
Dim custID As String = custRow("CustomerID", DataRowVersion.Original).ToString()  
```  
  
```csharp  
DataRow custRow = custTable.Rows[0];  
string custID = custRow["CustomerID", DataRowVersion.Original].ToString();  
```  
  
 <span data-ttu-id="a655e-123">下列表格簡短說明每個 `DataRowVersion` 列舉值。</span><span class="sxs-lookup"><span data-stu-id="a655e-123">The following table gives a brief description of each `DataRowVersion` enumeration value.</span></span>  
  
|<span data-ttu-id="a655e-124">DataRowVersion 值</span><span class="sxs-lookup"><span data-stu-id="a655e-124">DataRowVersion value</span></span>|<span data-ttu-id="a655e-125">描述</span><span class="sxs-lookup"><span data-stu-id="a655e-125">Description</span></span>|  
|--------------------------|-----------------|  
|<xref:System.Data.DataRowVersion.Current>|<span data-ttu-id="a655e-126">資料列的目前值。</span><span class="sxs-lookup"><span data-stu-id="a655e-126">The current values for the row.</span></span> <span data-ttu-id="a655e-127">對於 `RowState` 為 `Deleted` 的資料列，此資料列版本不存在。</span><span class="sxs-lookup"><span data-stu-id="a655e-127">This row version does not exist for rows with a `RowState` of `Deleted`.</span></span>|  
|<xref:System.Data.DataRowVersion.Default>|<span data-ttu-id="a655e-128">指定資料列的預設資料列版本。</span><span class="sxs-lookup"><span data-stu-id="a655e-128">The default row version for a particular row.</span></span> <span data-ttu-id="a655e-129">`Added`、`Modified` 或 `Unchanged` 資料列的預設資料列版本為 `Current`。</span><span class="sxs-lookup"><span data-stu-id="a655e-129">The default row version for an `Added`, `Modified`, or `Unchanged` row is `Current`.</span></span> <span data-ttu-id="a655e-130">`Deleted` 資料列的預設資料列版本為 `Original`。</span><span class="sxs-lookup"><span data-stu-id="a655e-130">The default row version for a `Deleted` row is `Original`.</span></span> <span data-ttu-id="a655e-131">`Detached` 資料列的預設資料列版本為 `Proposed`。</span><span class="sxs-lookup"><span data-stu-id="a655e-131">The default row version for a `Detached` row is `Proposed`.</span></span>|  
|<xref:System.Data.DataRowVersion.Original>|<span data-ttu-id="a655e-132">資料列的原始值。</span><span class="sxs-lookup"><span data-stu-id="a655e-132">The original values for the row.</span></span> <span data-ttu-id="a655e-133">對於 `RowState` 為 `Added` 的資料列，此資料列版本不存在。</span><span class="sxs-lookup"><span data-stu-id="a655e-133">This row version does not exist for rows with a `RowState` of `Added`.</span></span>|  
|<xref:System.Data.DataRowVersion.Proposed>|<span data-ttu-id="a655e-134">資料列的建議值。</span><span class="sxs-lookup"><span data-stu-id="a655e-134">The proposed values for the row.</span></span> <span data-ttu-id="a655e-135">這個資料列版本存在於資料列的編輯作業期間，或是當資料列不屬於 `DataRowCollection` 時。</span><span class="sxs-lookup"><span data-stu-id="a655e-135">This row version exists during an edit operation on a row, or for a row that is not part of a `DataRowCollection`.</span></span>|  
  
 <span data-ttu-id="a655e-136">您可以測試 `DataRow` 是否具有特定的資料列版本，方法是呼叫 <xref:System.Data.DataRow.HasVersion%2A> 方法，並將 `DataRowVersion` 當做引數傳遞。</span><span class="sxs-lookup"><span data-stu-id="a655e-136">You can test whether a `DataRow` has a particular row version by calling the <xref:System.Data.DataRow.HasVersion%2A> method and passing a `DataRowVersion` as an argument.</span></span> <span data-ttu-id="a655e-137">例如，`DataRow.HasVersion(DataRowVersion.Original)` 將在呼叫 `false` 之前，針對所新建立的資料列傳回 `AcceptChanges`。</span><span class="sxs-lookup"><span data-stu-id="a655e-137">For example, `DataRow.HasVersion(DataRowVersion.Original)` will return `false` for newly added rows before `AcceptChanges` has been called.</span></span>  
  
 <span data-ttu-id="a655e-138">下列程式碼範例顯示資料表內所有已刪除的資料列中的值。</span><span class="sxs-lookup"><span data-stu-id="a655e-138">The following code example displays the values in all the deleted rows of a table.</span></span> <span data-ttu-id="a655e-139">`Deleted` 資料列沒有 `Current` 資料列版本，因此您必須在存取資料行值時傳遞 `DataRowVersion.Original`。</span><span class="sxs-lookup"><span data-stu-id="a655e-139">`Deleted` rows do not have a `Current` row version, so you must pass `DataRowVersion.Original` when accessing the column values.</span></span>  
  
```vb  
Dim catTable As DataTable = catDS.Tables("Categories")  
  
Dim delRows() As DataRow = catTable.Select(Nothing, Nothing, DataViewRowState.Deleted)  
  
Console.WriteLine("Deleted rows:" & vbCrLf)  
  
Dim catCol As DataColumn  
Dim delRow As DataRow  
  
For Each catCol In catTable.Columns  
  Console.Write(catCol.ColumnName & vbTab)  
Next  
Console.WriteLine()  
  
For Each delRow In delRows  
  For Each catCol In catTable.Columns  
    Console.Write(delRow(catCol, DataRowVersion.Original) & vbTab)  
  Next  
  Console.WriteLine()  
Next  
```  
  
```csharp  
DataTable catTable = catDS.Tables["Categories"];  
  
DataRow[] delRows = catTable.Select(null, null, DataViewRowState.Deleted);  
  
Console.WriteLine("Deleted rows:\n");  
  
foreach (DataColumn catCol in catTable.Columns)  
  Console.Write(catCol.ColumnName + "\t");  
Console.WriteLine();  
  
foreach (DataRow delRow in delRows)  
{  
  foreach (DataColumn catCol in catTable.Columns)  
    Console.Write(delRow[catCol, DataRowVersion.Original] + "\t");  
  Console.WriteLine();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a655e-140">請參閱</span><span class="sxs-lookup"><span data-stu-id="a655e-140">See Also</span></span>  
 [<span data-ttu-id="a655e-141">在 DataTable 中操作資料</span><span class="sxs-lookup"><span data-stu-id="a655e-141">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="a655e-142">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="a655e-142">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="a655e-143">DataAdapter 和 DataReader</span><span class="sxs-lookup"><span data-stu-id="a655e-143">DataAdapters and DataReaders</span></span>](../../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="a655e-144">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="a655e-144">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
