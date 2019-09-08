---
title: 逐頁查看查詢結果
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa360c46-e5f8-411e-a711-46997771133d
ms.openlocfilehash: 1dbaa159314bf7bb05ff75287f601f619834fd7c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794621"
---
# <a name="paging-through-a-query-result"></a><span data-ttu-id="cec65-102">逐頁查看查詢結果</span><span class="sxs-lookup"><span data-stu-id="cec65-102">Paging Through a Query Result</span></span>
<span data-ttu-id="cec65-103">將查詢結果分頁是以較小資料子集或頁傳回查詢結果的過程。</span><span class="sxs-lookup"><span data-stu-id="cec65-103">Paging through a query result is the process of returning the results of a query in smaller subsets of data, or pages.</span></span> <span data-ttu-id="cec65-104">這是一種常用的方式，可將結果以小型、易於管理的區塊顯示給使用者。</span><span class="sxs-lookup"><span data-stu-id="cec65-104">This is a common practice for displaying results to a user in small, easy-to-manage chunks.</span></span>  
  
 <span data-ttu-id="cec65-105">**DataAdapter**透過**Fill**方法的多載，提供只傳回一頁數據的功能。</span><span class="sxs-lookup"><span data-stu-id="cec65-105">The **DataAdapter** provides a facility for returning only a page of data, through overloads of the **Fill** method.</span></span> <span data-ttu-id="cec65-106">不過，這可能不是分頁到大型查詢結果的最佳選擇，因為雖然**DataAdapter**會填滿目標<xref:System.Data.DataTable>或<xref:System.Data.DataSet>只包含要求的記錄，但仍會使用傳回整個查詢的資源.</span><span class="sxs-lookup"><span data-stu-id="cec65-106">However, this might not be the best choice for paging through large query results because, although the **DataAdapter** fills the target <xref:System.Data.DataTable> or <xref:System.Data.DataSet> with only the requested records, the resources to return the entire query are still used.</span></span> <span data-ttu-id="cec65-107">若您要從資料來源傳回一頁資料，並且不使用傳回整個查詢的資源，請為您的查詢指定其他準則，以將傳回的資料列縮小到必要的範圍內。</span><span class="sxs-lookup"><span data-stu-id="cec65-107">To return a page of data from a data source without using the resources to return the entire query, specify additional criteria for your query that reduce the rows returned to only those required.</span></span>  
  
 <span data-ttu-id="cec65-108">若要使用**Fill**方法傳回一頁數據，請針對資料頁中的第一筆記錄指定**startRecord**參數，並針對資料頁中的記錄數目指定**maxRecords**參數。</span><span class="sxs-lookup"><span data-stu-id="cec65-108">To use the **Fill** method to return a page of data, specify a **startRecord** parameter, for the first record in the page of data, and a **maxRecords** parameter, for the number of records in the page of data.</span></span>  
  
 <span data-ttu-id="cec65-109">下列程式碼範例示範如何使用**Fill**方法傳回查詢結果的第一頁，其中頁面大小為五筆記錄。</span><span class="sxs-lookup"><span data-stu-id="cec65-109">The following code example shows how to use the **Fill** method to return the first page of a query result where the page size is five records.</span></span>  
  
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
  
 <span data-ttu-id="cec65-110">在上述範例中，**資料集**只會填入五筆記錄，但會傳回整個**Orders**資料表。</span><span class="sxs-lookup"><span data-stu-id="cec65-110">In the previous example, the **DataSet** is only filled with five records, but the entire **Orders** table is returned.</span></span> <span data-ttu-id="cec65-111">若要以相同的五筆記錄填入**資料集**，但是只傳回五筆記錄，請在您的 SQL 語句中使用 TOP 和 WHERE 子句，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="cec65-111">To fill the **DataSet** with those same five records, but only return five records, use the TOP and WHERE clauses in your SQL statement, as in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="cec65-112">請注意，若以這種方式進行查詢結果的分頁，您必須保留用來排序資料列的唯一識別項，才能將唯一 ID 傳遞給命令以傳回下一頁記錄，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="cec65-112">Note that, when paging through the query results in this way, you must preserve the unique identifier that orders the rows, in order to pass the unique ID to the command to return the next page of records, as shown in the following code example.</span></span>  
  
```vb  
Dim lastRecord As String = _  
  dataSet.Tables("Orders").Rows(pageSize - 1)("OrderID").ToString()  
```  
  
```csharp  
string lastRecord =   
  dataSet.Tables["Orders"].Rows[pageSize - 1]["OrderID"].ToString();  
```  
  
 <span data-ttu-id="cec65-113">若要使用採用**startRecord**和**MaxRecords**參數的**Fill**方法多載來傳回下一頁記錄，請以頁面大小遞增目前的記錄索引，並填滿資料表。</span><span class="sxs-lookup"><span data-stu-id="cec65-113">To return the next page of records using the overload of the **Fill** method that takes the **startRecord** and **maxRecords** parameters, increment the current record index by the page size and fill the table.</span></span> <span data-ttu-id="cec65-114">請記住，即使只有一個記錄頁面加入至**資料集**，資料庫伺服器還是會傳回整個查詢結果。</span><span class="sxs-lookup"><span data-stu-id="cec65-114">Remember that the database server returns the entire query results even though only one page of records is added to the **DataSet**.</span></span> <span data-ttu-id="cec65-115">下列程式碼範例中，資料表列會先經過清除後，再填入下一頁資料。</span><span class="sxs-lookup"><span data-stu-id="cec65-115">In the following code example, the table rows are cleared before they are filled with the next page of data.</span></span> <span data-ttu-id="cec65-116">您可以在本機快取中保留特定數量的傳回資料列，來降低往返資料庫伺服器的次數。</span><span class="sxs-lookup"><span data-stu-id="cec65-116">You might want to preserve a certain number of returned rows in a local cache to reduce trips to the database server.</span></span>  
  
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
  
 <span data-ttu-id="cec65-117">若要在資料庫伺服器不傳回整個查詢的情況下，傳回下一頁記錄，請對 SELECT 陳述式指定限制準則。</span><span class="sxs-lookup"><span data-stu-id="cec65-117">To return the next page of records without having the database server return the entire query, specify restrictive criteria to the SELECT statement.</span></span> <span data-ttu-id="cec65-118">由於前面的範例保留了最後傳回的記錄，因此您可以在 WHERE 子句使用它來指定查詢的起始點，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="cec65-118">Because the preceding example preserved the last record returned, you can use it in the WHERE clause to specify a starting point for the query, as shown in the following code example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cec65-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cec65-119">See also</span></span>

- [<span data-ttu-id="cec65-120">DataAdapter 和 DataReader</span><span class="sxs-lookup"><span data-stu-id="cec65-120">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="cec65-121">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="cec65-121">ADO.NET Overview</span></span>](ado-net-overview.md)
