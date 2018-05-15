---
title: 將資料加入至 DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d6aa8474-7bde-48f7-949d-20dc38a1625b
ms.openlocfilehash: c58f64dba0bceb4a35c67e16193a6627837436e0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="adding-data-to-a-datatable"></a><span data-ttu-id="0d57b-102">將資料加入至 DataTable</span><span class="sxs-lookup"><span data-stu-id="0d57b-102">Adding Data to a DataTable</span></span>
<span data-ttu-id="0d57b-103">建立 <xref:System.Data.DataTable> 並使用資料行和條件約束定義其結構之後，即可將新資料列加入資料表。</span><span class="sxs-lookup"><span data-stu-id="0d57b-103">After you create a <xref:System.Data.DataTable> and define its structure using columns and constraints, you can add new rows of data to the table.</span></span> <span data-ttu-id="0d57b-104">若要加入新資料列，請將新變數宣告為 <xref:System.Data.DataRow> 型別。</span><span class="sxs-lookup"><span data-stu-id="0d57b-104">To add a new row, declare a new variable as type <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="0d57b-105">新**DataRow**呼叫時，會傳回物件<xref:System.Data.DataTable.NewRow%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="0d57b-105">A new **DataRow** object is returned when you call the <xref:System.Data.DataTable.NewRow%2A> method.</span></span> <span data-ttu-id="0d57b-106">**DataTable**接著會建立**DataRow**物件基礎的資料表，結構所定義的<xref:System.Data.DataColumnCollection>。</span><span class="sxs-lookup"><span data-stu-id="0d57b-106">The **DataTable** then creates the **DataRow** object based on the structure of the table, as defined by the <xref:System.Data.DataColumnCollection>.</span></span>  
  
 <span data-ttu-id="0d57b-107">下列範例示範如何建立新的資料列，藉由呼叫**NewRow**方法。</span><span class="sxs-lookup"><span data-stu-id="0d57b-107">The following example demonstrates how to create a new row by calling the **NewRow** method.</span></span>  
  
```vb  
Dim workRow As DataRow = workTable.NewRow()  
```  
  
```csharp  
DataRow workRow = workTable.NewRow();  
```  
  
 <span data-ttu-id="0d57b-108">接下來您可以使用索引或資料行名稱來管理新加入的資料列，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="0d57b-108">You then can manipulate the newly added row using an index or the column name, as shown in the following example.</span></span>  
  
```vb  
workRow("CustLName") = "Smith"  
workRow(1) = "Smith"  
```  
  
```csharp  
workRow["CustLName"] = "Smith";  
workRow[1] = "Smith";  
```  
  
 <span data-ttu-id="0d57b-109">資料會插入新的資料列之後**新增**方法用來新增列<xref:System.Data.DataRowCollection>，下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="0d57b-109">After data is inserted into the new row, the **Add** method is used to add the row to the <xref:System.Data.DataRowCollection>, shown in the following code.</span></span>  
  
```vb  
workTable.Rows.Add(workRow)  
```  
  
```csharp  
workTable.Rows.Add(workRow);  
```  
  
 <span data-ttu-id="0d57b-110">您也可以呼叫**新增**方法，藉由傳遞陣列的值，將新的資料列型別為<xref:System.Object>，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="0d57b-110">You can also call the **Add** method to add a new row by passing in an array of values, typed as <xref:System.Object>, as shown in the following example.</span></span>  
  
```vb  
workTable.Rows.Add(new Object() {1, "Smith"})  
```  
  
```csharp  
workTable.Rows.Add(new Object[] {1, "Smith"});  
```  
  
 <span data-ttu-id="0d57b-111">傳遞做為輸入的值的陣列**物件**至**新增**方法會建立新資料表內的資料列，並將其資料行值設定為物件陣列中的值。</span><span class="sxs-lookup"><span data-stu-id="0d57b-111">Passing an array of values, typed as **Object**, to the **Add** method creates a new row inside the table and sets its column values to the values in the object array.</span></span> <span data-ttu-id="0d57b-112">請注意，陣列值將根據其在資料表出現的順序，依序和資料行相符。</span><span class="sxs-lookup"><span data-stu-id="0d57b-112">Note that values in the array are matched sequentially to the columns, based on the order in which they appear in the table.</span></span>  
  
 <span data-ttu-id="0d57b-113">下列範例將 10 個資料列加入至新建立**客戶**資料表。</span><span class="sxs-lookup"><span data-stu-id="0d57b-113">The following example adds 10 rows to the newly created **Customers** table.</span></span>  
  
```vb  
Dim workRow As DataRow  
Dim i As Integer  
  
For i = 0 To 9  
  workRow = workTable.NewRow()  
  workRow(0) = i  
  workRow(1) = "CustName" & I.ToString()  
  workTable.Rows.Add(workRow)  
Next  
```  
  
```csharp  
DataRow workRow;  
  
for (int i = 0; i <= 9; i++)   
{  
  workRow = workTable.NewRow();  
  workRow[0] = i;  
  workRow[1] = "CustName" + i.ToString();  
  workTable.Rows.Add(workRow);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="0d57b-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d57b-114">See Also</span></span>  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataRowCollection>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="0d57b-115">在 DataTable 中操作資料</span><span class="sxs-lookup"><span data-stu-id="0d57b-115">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="0d57b-116">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="0d57b-116">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
