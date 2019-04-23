---
title: 逐頁查看查詢結果
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa360c46-e5f8-411e-a711-46997771133d
ms.openlocfilehash: 023efcc15d7080afc1583f4ad8984e152b86cf23
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59140318"
---
# <a name="paging-through-a-query-result"></a><span data-ttu-id="86e25-102">逐頁查看查詢結果</span><span class="sxs-lookup"><span data-stu-id="86e25-102">Paging Through a Query Result</span></span>
<span data-ttu-id="86e25-103">將查詢結果分頁是以較小資料子集或頁傳回查詢結果的過程。</span><span class="sxs-lookup"><span data-stu-id="86e25-103">Paging through a query result is the process of returning the results of a query in smaller subsets of data, or pages.</span></span> <span data-ttu-id="86e25-104">這是一種常用的方式，可將結果以小型、易於管理的區塊顯示給使用者。</span><span class="sxs-lookup"><span data-stu-id="86e25-104">This is a common practice for displaying results to a user in small, easy-to-manage chunks.</span></span>  
  
 <span data-ttu-id="86e25-105">**DataAdapter**傳回的資料，從多載的頁面上提供的設備**填滿**方法。</span><span class="sxs-lookup"><span data-stu-id="86e25-105">The **DataAdapter** provides a facility for returning only a page of data, through overloads of the **Fill** method.</span></span> <span data-ttu-id="86e25-106">不過，這可能不是最適合逐頁查看大型的查詢結果，因為，雖然**DataAdapter**填入目標<xref:System.Data.DataTable>或<xref:System.Data.DataSet>只要求記錄時，要傳回的資源仍會使用整個查詢。</span><span class="sxs-lookup"><span data-stu-id="86e25-106">However, this might not be the best choice for paging through large query results because, although the **DataAdapter** fills the target <xref:System.Data.DataTable> or <xref:System.Data.DataSet> with only the requested records, the resources to return the entire query are still used.</span></span> <span data-ttu-id="86e25-107">若您要從資料來源傳回一頁資料，並且不使用傳回整個查詢的資源，請為您的查詢指定其他準則，以將傳回的資料列縮小到必要的範圍內。</span><span class="sxs-lookup"><span data-stu-id="86e25-107">To return a page of data from a data source without using the resources to return the entire query, specify additional criteria for your query that reduce the rows returned to only those required.</span></span>  
  
 <span data-ttu-id="86e25-108">若要使用**填滿**方法來傳回一頁資料，指定**startRecord**參數，第一筆記錄，在頁面中的資料，和**maxRecords**參數的數目資料頁中的記錄。</span><span class="sxs-lookup"><span data-stu-id="86e25-108">To use the **Fill** method to return a page of data, specify a **startRecord** parameter, for the first record in the page of data, and a **maxRecords** parameter, for the number of records in the page of data.</span></span>  
  
 <span data-ttu-id="86e25-109">下列程式碼範例示範如何使用**填滿**方法傳回查詢結果的第一頁的頁面大小為五筆記錄的位置。</span><span class="sxs-lookup"><span data-stu-id="86e25-109">The following code example shows how to use the **Fill** method to return the first page of a query result where the page size is five records.</span></span>  
  
```vb  
Dim currentIndex As Integer = 0  
Dim pageSize As Integer = 5  
  
Dim orderSQL As String = "SELECT * FROM dbo.Orders ORDER BY OrderID"  
' Assumes that connection is a valid SqlConnection object.  
Dim adapter As SqlDataAdapter = _  
  New SqlDataAdapter(orderSQL, connection)  
  
Dim dataSet As DataSet = New DataSet()  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders")  
```  
  
```csharp  
int currentIndex = 0;  
int pageSize = 5;  
  
string orderSQL = "SELECT * FROM Orders ORDER BY OrderID";  
// Assumes that connection is a valid SqlConnection object.  
SqlDataAdapter adapter = new SqlDataAdapter(orderSQL, connection);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders");  
```  
  
 <span data-ttu-id="86e25-110">在上述範例中，**資料集**只填入了五筆記錄，但整個**訂單**會傳回資料表。</span><span class="sxs-lookup"><span data-stu-id="86e25-110">In the previous example, the **DataSet** is only filled with five records, but the entire **Orders** table is returned.</span></span> <span data-ttu-id="86e25-111">若要填滿**資料集**這些相同的五筆記錄，但只傳回五筆記錄，同時使用 TOP 和 WHERE 子句，在 SQL 陳述式，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="86e25-111">To fill the **DataSet** with those same five records, but only return five records, use the TOP and WHERE clauses in your SQL statement, as in the following code example.</span></span>  
  
```vb  
Dim pageSize As Integer = 5  
  
Dim orderSQL As String = "SELECT TOP " & pageSize & _  
  " * FROM Orders ORDER BY OrderID"  
Dim adapter As SqlDataAdapter = _  
  New SqlDataAdapter(orderSQL, connection)  
  
Dim dataSet As DataSet = New DataSet()  
adapter.Fill(dataSet, "Orders")   
```  
  
```csharp  
int pageSize = 5;  
  
string orderSQL = "SELECT TOP " + pageSize +   
  " * FROM Orders ORDER BY OrderID";  
SqlDataAdapter adapter = new SqlDataAdapter(orderSQL, connection);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, "Orders");  
```  
  
 <span data-ttu-id="86e25-112">請注意，若以這種方式進行查詢結果的分頁，您必須保留用來排序資料列的唯一識別項，才能將唯一 ID 傳遞給命令以傳回下一頁記錄，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="86e25-112">Note that, when paging through the query results in this way, you must preserve the unique identifier that orders the rows, in order to pass the unique ID to the command to return the next page of records, as shown in the following code example.</span></span>  
  
```vb  
Dim lastRecord As String = _  
  dataSet.Tables("Orders").Rows(pageSize - 1)("OrderID").ToString()  
```  
  
```csharp  
string lastRecord =   
  dataSet.Tables["Orders"].Rows[pageSize - 1]["OrderID"].ToString();  
```  
  
 <span data-ttu-id="86e25-113">若要傳回下一頁記錄使用的多載**填滿**採用方法**startRecord**並**maxRecords**參數遞增目前的記錄索引的頁面大小和填滿資料表中。</span><span class="sxs-lookup"><span data-stu-id="86e25-113">To return the next page of records using the overload of the **Fill** method that takes the **startRecord** and **maxRecords** parameters, increment the current record index by the page size and fill the table.</span></span> <span data-ttu-id="86e25-114">請記住在資料庫伺服器會傳回整個查詢結果，即使只有一頁記錄新增至**資料集**。</span><span class="sxs-lookup"><span data-stu-id="86e25-114">Remember that the database server returns the entire query results even though only one page of records is added to the **DataSet**.</span></span> <span data-ttu-id="86e25-115">下列程式碼範例中，資料表列會先經過清除後，再填入下一頁資料。</span><span class="sxs-lookup"><span data-stu-id="86e25-115">In the following code example, the table rows are cleared before they are filled with the next page of data.</span></span> <span data-ttu-id="86e25-116">您可以在本機快取中保留特定數量的傳回資料列，來降低往返資料庫伺服器的次數。</span><span class="sxs-lookup"><span data-stu-id="86e25-116">You might want to preserve a certain number of returned rows in a local cache to reduce trips to the database server.</span></span>  
  
```vb  
currentIndex = currentIndex + pageSize  
  
dataSet.Tables("Orders").Rows.Clear()  
  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders")  
```  
  
```csharp  
currentIndex += pageSize;  
  
dataSet.Tables["Orders"].Rows.Clear();  
  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders");  
```  
  
 <span data-ttu-id="86e25-117">若要在資料庫伺服器不傳回整個查詢的情況下，傳回下一頁記錄，請對 SELECT 陳述式指定限制準則。</span><span class="sxs-lookup"><span data-stu-id="86e25-117">To return the next page of records without having the database server return the entire query, specify restrictive criteria to the SELECT statement.</span></span> <span data-ttu-id="86e25-118">由於前面的範例保留了最後傳回的記錄，因此您可以在 WHERE 子句使用它來指定查詢的起始點，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="86e25-118">Because the preceding example preserved the last record returned, you can use it in the WHERE clause to specify a starting point for the query, as shown in the following code example.</span></span>  
  
```vb  
orderSQL = "SELECT TOP " & pageSize & _  
  " * FROM Orders WHERE OrderID > " & lastRecord & " ORDER BY OrderID"  
adapter.SelectCommand.CommandText = orderSQL  
  
dataSet.Tables("Orders").Rows.Clear()  
  
adapter.Fill(dataSet, "Orders")  
```  
  
```csharp  
orderSQL = "SELECT TOP " + pageSize +   
  " * FROM Orders WHERE OrderID > " + lastRecord + " ORDER BY OrderID";  
adapter.SelectCommand.CommandText = orderSQL;  
  
dataSet.Tables["Orders"].Rows.Clear();  
  
adapter.Fill(dataSet, "Orders");  
```  
  
## <a name="see-also"></a><span data-ttu-id="86e25-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86e25-119">See also</span></span>

- [<span data-ttu-id="86e25-120">DataAdapter 和 DataReader</span><span class="sxs-lookup"><span data-stu-id="86e25-120">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [<span data-ttu-id="86e25-121">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="86e25-121">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
