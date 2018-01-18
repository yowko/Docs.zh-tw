---
title: "逐頁查看查詢結果"
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
ms.assetid: fa360c46-e5f8-411e-a711-46997771133d
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 83e8241fed71ec4dd0ea32f97b02373f3a1d56bb
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="paging-through-a-query-result"></a><span data-ttu-id="9ee29-102">逐頁查看查詢結果</span><span class="sxs-lookup"><span data-stu-id="9ee29-102">Paging Through a Query Result</span></span>
<span data-ttu-id="9ee29-103">將查詢結果分頁是以較小資料子集或頁傳回查詢結果的過程。</span><span class="sxs-lookup"><span data-stu-id="9ee29-103">Paging through a query result is the process of returning the results of a query in smaller subsets of data, or pages.</span></span> <span data-ttu-id="9ee29-104">這是一種常用的方式，可將結果以小型、易於管理的區塊顯示給使用者。</span><span class="sxs-lookup"><span data-stu-id="9ee29-104">This is a common practice for displaying results to a user in small, easy-to-manage chunks.</span></span>  
  
 <span data-ttu-id="9ee29-105">**DataAdapter**傳回的資料，透過多載的頁面，來提供設備**填滿**方法。</span><span class="sxs-lookup"><span data-stu-id="9ee29-105">The **DataAdapter** provides a facility for returning only a page of data, through overloads of the **Fill** method.</span></span> <span data-ttu-id="9ee29-106">不過，這可能不是最佳選擇進行大型查詢結果的分頁，因為雖然**DataAdapter**填入目標<xref:System.Data.DataTable>或<xref:System.Data.DataSet>只要求記錄時，要傳回的資源仍會使用整個查詢。</span><span class="sxs-lookup"><span data-stu-id="9ee29-106">However, this might not be the best choice for paging through large query results because, although the **DataAdapter** fills the target <xref:System.Data.DataTable> or <xref:System.Data.DataSet> with only the requested records, the resources to return the entire query are still used.</span></span> <span data-ttu-id="9ee29-107">若您要從資料來源傳回一頁資料，並且不使用傳回整個查詢的資源，請為您的查詢指定其他準則，以將傳回的資料列縮小到必要的範圍內。</span><span class="sxs-lookup"><span data-stu-id="9ee29-107">To return a page of data from a data source without using the resources to return the entire query, specify additional criteria for your query that reduce the rows returned to only those required.</span></span>  
  
 <span data-ttu-id="9ee29-108">若要使用**填滿**方法來傳回一頁資料，指定**startRecord**參數，在頁面中的資料，第一筆記錄和**maxRecords**參數的數目資料頁中的記錄。</span><span class="sxs-lookup"><span data-stu-id="9ee29-108">To use the **Fill** method to return a page of data, specify a **startRecord** parameter, for the first record in the page of data, and a **maxRecords** parameter, for the number of records in the page of data.</span></span>  
  
 <span data-ttu-id="9ee29-109">下列程式碼範例示範如何使用**填滿**方法來傳回查詢結果的第一頁的頁面大小為五筆記錄的位置。</span><span class="sxs-lookup"><span data-stu-id="9ee29-109">The following code example shows how to use the **Fill** method to return the first page of a query result where the page size is five records.</span></span>  
  
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
  
 <span data-ttu-id="9ee29-110">在上述範例中，**資料集**只填入了五筆記錄，但整個**訂單**會傳回資料表。</span><span class="sxs-lookup"><span data-stu-id="9ee29-110">In the previous example, the **DataSet** is only filled with five records, but the entire **Orders** table is returned.</span></span> <span data-ttu-id="9ee29-111">填滿**資料集**相同的五筆記錄，但是只傳回五筆記錄，同時使用 TOP 和 WHERE 子句中 SQL 陳述式，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="9ee29-111">To fill the **DataSet** with those same five records, but only return five records, use the TOP and WHERE clauses in your SQL statement, as in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="9ee29-112">請注意，若以這種方式進行查詢結果的分頁，您必須保留用來排序資料列的唯一識別項，才能將唯一 ID 傳遞給命令以傳回下一頁記錄，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="9ee29-112">Note that, when paging through the query results in this way, you must preserve the unique identifier that orders the rows, in order to pass the unique ID to the command to return the next page of records, as shown in the following code example.</span></span>  
  
```vb  
Dim lastRecord As String = _  
  dataSet.Tables("Orders").Rows(pageSize - 1)("OrderID").ToString()  
```  
  
```csharp  
string lastRecord =   
  dataSet.Tables["Orders"].Rows[pageSize - 1]["OrderID"].ToString();  
```  
  
 <span data-ttu-id="9ee29-113">若要傳回記錄的多載的下一個頁面**填滿**採用方法**startRecord**和**maxRecords**參數，遞增目前所記錄索引頁面大小] 與 [填滿資料表中。</span><span class="sxs-lookup"><span data-stu-id="9ee29-113">To return the next page of records using the overload of the **Fill** method that takes the **startRecord** and **maxRecords** parameters, increment the current record index by the page size and fill the table.</span></span> <span data-ttu-id="9ee29-114">請記住資料庫伺服器會傳回整個查詢結果，即使只有一個分頁的記錄加入至**資料集**。</span><span class="sxs-lookup"><span data-stu-id="9ee29-114">Remember that the database server returns the entire query results even though only one page of records is added to the **DataSet**.</span></span> <span data-ttu-id="9ee29-115">下列程式碼範例中，資料表列會先經過清除後，再填入下一頁資料。</span><span class="sxs-lookup"><span data-stu-id="9ee29-115">In the following code example, the table rows are cleared before they are filled with the next page of data.</span></span> <span data-ttu-id="9ee29-116">您可以在本機快取中保留特定數量的傳回資料列，來降低往返資料庫伺服器的次數。</span><span class="sxs-lookup"><span data-stu-id="9ee29-116">You might want to preserve a certain number of returned rows in a local cache to reduce trips to the database server.</span></span>  
  
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
  
 <span data-ttu-id="9ee29-117">若要在資料庫伺服器不傳回整個查詢的情況下，傳回下一頁記錄，請對 SELECT 陳述式指定限制準則。</span><span class="sxs-lookup"><span data-stu-id="9ee29-117">To return the next page of records without having the database server return the entire query, specify restrictive criteria to the SELECT statement.</span></span> <span data-ttu-id="9ee29-118">由於前面的範例保留了最後傳回的記錄，因此您可以在 WHERE 子句使用它來指定查詢的起始點，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="9ee29-118">Because the preceding example preserved the last record returned, you can use it in the WHERE clause to specify a starting point for the query, as shown in the following code example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9ee29-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="9ee29-119">See Also</span></span>  
 [<span data-ttu-id="9ee29-120">DataAdapter 和 DataReader</span><span class="sxs-lookup"><span data-stu-id="9ee29-120">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="9ee29-121">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="9ee29-121">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
