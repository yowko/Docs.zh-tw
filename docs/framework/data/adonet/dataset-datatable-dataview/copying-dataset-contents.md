---
title: 複製資料集內容
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
ms.openlocfilehash: de13e07eb5c19b8beffa724fec4a128c418a4fed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151360"
---
# <a name="copying-dataset-contents"></a><span data-ttu-id="515ab-102">複製資料集內容</span><span class="sxs-lookup"><span data-stu-id="515ab-102">Copying DataSet Contents</span></span>
<span data-ttu-id="515ab-103">您可以創建 from 的副本<xref:System.Data.DataSet>，以便可以在不影響原始資料的情況下處理資料，或者處理**DataSet**中資料的子集。</span><span class="sxs-lookup"><span data-stu-id="515ab-103">You can create a copy of a <xref:System.Data.DataSet> so that you can work with data without affecting the original data, or work with a subset of the data from a **DataSet**.</span></span> <span data-ttu-id="515ab-104">複製**資料集**時，您可以：</span><span class="sxs-lookup"><span data-stu-id="515ab-104">When copying a **DataSet**, you can:</span></span>  
  
- <span data-ttu-id="515ab-105">創建**DataSet**的確切副本 ，包括架構、資料、行狀態資訊和行版本。</span><span class="sxs-lookup"><span data-stu-id="515ab-105">Create an exact copy of the **DataSet**, including the schema, data, row state information, and row versions.</span></span>  
  
- <span data-ttu-id="515ab-106">創建包含現有 DataSet 的架構，但僅包含已修改的行**的 DataSet。** **DataSet**</span><span class="sxs-lookup"><span data-stu-id="515ab-106">Create a **DataSet** that contains the schema of an existing **DataSet**, but only rows that have been modified.</span></span> <span data-ttu-id="515ab-107">您可以返回已修改的所有行，或指定特定的**DataRowState**。</span><span class="sxs-lookup"><span data-stu-id="515ab-107">You can return all rows that have been modified, or specify a specific **DataRowState**.</span></span> <span data-ttu-id="515ab-108">有關行狀態的詳細資訊，請參閱[行狀態和行版本](row-states-and-row-versions.md)。</span><span class="sxs-lookup"><span data-stu-id="515ab-108">For more information about row states, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
- <span data-ttu-id="515ab-109">僅複製**DataSet**的架構或關聯式結構，而不復制任何行。</span><span class="sxs-lookup"><span data-stu-id="515ab-109">Copy the schema, or relational structure, of the **DataSet** only, without copying any rows.</span></span> <span data-ttu-id="515ab-110">使用 <xref:System.Data.DataTable>，可以將資料列匯入現有的 <xref:System.Data.DataTable.ImportRow%2A>。</span><span class="sxs-lookup"><span data-stu-id="515ab-110">Rows can be imported into an existing <xref:System.Data.DataTable> using <xref:System.Data.DataTable.ImportRow%2A>.</span></span>  
  
 <span data-ttu-id="515ab-111">要創建包含架構和資料的資料**集**的精確副本，<xref:System.Data.DataSet.Copy%2A>請使用**DataSet**的方法。</span><span class="sxs-lookup"><span data-stu-id="515ab-111">To create an exact copy of the **DataSet** that includes both schema and data, use the <xref:System.Data.DataSet.Copy%2A> method of the **DataSet**.</span></span> <span data-ttu-id="515ab-112">以下代碼示例演示如何創建**DataSet**的確切副本。</span><span class="sxs-lookup"><span data-stu-id="515ab-112">The following code example shows how to create an exact copy of the **DataSet**.</span></span>  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 <span data-ttu-id="515ab-113">要創建**包含**架構且僅表示**已添加**、**已修改**或**已刪除**行的資料集的副本，請使用<xref:System.Data.DataSet.GetChanges%2A>**DataSet**的方法。</span><span class="sxs-lookup"><span data-stu-id="515ab-113">To create a copy of a **DataSet** that includes schema and only the data representing **Added**, **Modified**, or **Deleted** rows, use the <xref:System.Data.DataSet.GetChanges%2A> method of the **DataSet**.</span></span> <span data-ttu-id="515ab-114">您還可以使用**GetChanges**在調用**GetChanges**時傳遞**DataRowState**值，僅返回具有指定行狀態的行。</span><span class="sxs-lookup"><span data-stu-id="515ab-114">You can also use **GetChanges** to return only rows with a specified row state by passing a **DataRowState** value when calling **GetChanges**.</span></span> <span data-ttu-id="515ab-115">以下代碼示例演示如何在調用**GetChanges**時傳遞**DataRowState。**</span><span class="sxs-lookup"><span data-stu-id="515ab-115">The following code example shows how to pass a **DataRowState** when calling **GetChanges**.</span></span>  
  
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
  
 <span data-ttu-id="515ab-116">要創建僅包含架構**的 DataSet**的副本，<xref:System.Data.DataSet.Clone%2A>請使用**DataSet**的方法。</span><span class="sxs-lookup"><span data-stu-id="515ab-116">To create a copy of a **DataSet** that only includes schema, use the <xref:System.Data.DataSet.Clone%2A> method of the **DataSet**.</span></span> <span data-ttu-id="515ab-117">您還可以使用**DataTable**的**ImportRow**方法將現有行添加到克隆**的資料集**。</span><span class="sxs-lookup"><span data-stu-id="515ab-117">You can also add existing rows to the cloned **DataSet** using the **ImportRow** method of the **DataTable**.</span></span> <span data-ttu-id="515ab-118">**ImportRow**將資料、行狀態和行版本資訊添加到指定的表。</span><span class="sxs-lookup"><span data-stu-id="515ab-118">**ImportRow** adds data, row state, and row version information to the specified table.</span></span> <span data-ttu-id="515ab-119">資料行值只會被加入資料行名稱相符且資料型別相容之處。</span><span class="sxs-lookup"><span data-stu-id="515ab-119">Column values are added only where the column name matches and the data type is compatible.</span></span>  
  
 <span data-ttu-id="515ab-120">以下代碼示例創建**DataSet**的克隆，然後將原始**DataSet**中的行添加到**DataSet**克隆中的 **"客戶"** 表中，客戶**國家區域**列的值為"德國"。</span><span class="sxs-lookup"><span data-stu-id="515ab-120">The following code example creates a clone of a **DataSet** and then adds the rows from the original **DataSet** to the **Customers** table in the **DataSet** clone for customers where the **CountryRegion** column has the value "Germany".</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="515ab-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="515ab-121">See also</span></span>

- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="515ab-122">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="515ab-122">DataSets, DataTables, and DataViews</span></span>](index.md)
- <span data-ttu-id="515ab-123">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="515ab-123">[ADO.NET Overview](../ado-net-overview.md)</span></span>
