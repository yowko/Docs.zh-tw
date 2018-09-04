---
title: 使用 DataReader 擷取資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.openlocfilehash: 4370a7a700a01943548bf067827e6640245caf4e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516787"
---
# <a name="retrieving-data-using-a-datareader"></a><span data-ttu-id="4caec-102">使用 DataReader 擷取資料</span><span class="sxs-lookup"><span data-stu-id="4caec-102">Retrieving Data Using a DataReader</span></span>
<span data-ttu-id="4caec-103">使用擷取的資料**DataReader**牽涉到建立的執行個體**命令**物件，然後再建立**DataReader**藉由呼叫**Command.ExecuteReader**從資料來源擷取資料列。</span><span class="sxs-lookup"><span data-stu-id="4caec-103">Retrieving data using a **DataReader** involves creating an instance of the **Command** object and then creating a **DataReader** by calling **Command.ExecuteReader** to retrieve rows from a data source.</span></span> <span data-ttu-id="4caec-104">下列範例說明如何利用**DataReader**何處`reader`代表有效的 DataReader 和`command`代表有效的命令物件。</span><span class="sxs-lookup"><span data-stu-id="4caec-104">The following example illustrates using a **DataReader** where `reader` represents a valid DataReader and `command` represents a valid Command object.</span></span>  
  
```  
reader = command.ExecuteReader();  
```  
  
 <span data-ttu-id="4caec-105">您使用**讀取**方法**DataReader**物件，以從查詢的結果取得資料列。</span><span class="sxs-lookup"><span data-stu-id="4caec-105">You use the **Read** method of the **DataReader** object to obtain a row from the results of the query.</span></span> <span data-ttu-id="4caec-106">您可以藉由傳遞的名稱或序數參考的資料行傳回的資料列的每個資料行**DataReader**。</span><span class="sxs-lookup"><span data-stu-id="4caec-106">You can access each column of the returned row by passing the name or ordinal reference of the column to the **DataReader**.</span></span> <span data-ttu-id="4caec-107">不過，為了達到最佳效能， **DataReader**提供一系列的方法，可讓您存取其原生資料類型的資料行值 (**GetDateTime**， **GetDouble**， **GetGuid**， **GetInt32**等等)。</span><span class="sxs-lookup"><span data-stu-id="4caec-107">However, for best performance, the **DataReader** provides a series of methods that allow you to access column values in their native data types (**GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**, and so on).</span></span> <span data-ttu-id="4caec-108">如需資料提供者特有的具型別存取子方法的清單**Datareader**，請參閱<xref:System.Data.OleDb.OleDbDataReader>和<xref:System.Data.SqlClient.SqlDataReader>。</span><span class="sxs-lookup"><span data-stu-id="4caec-108">For a list of typed accessor methods for data provider-specific **DataReaders**, see <xref:System.Data.OleDb.OleDbDataReader> and <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="4caec-109">假設已知基礎資料型別時，若使用具型別的存取子方法，可減少擷取資料行值時所需的型別轉換量。</span><span class="sxs-lookup"><span data-stu-id="4caec-109">Using the typed accessor methods, assuming the underlying data type is known, reduces the amount of type conversion required when retrieving the column value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4caec-110">Windows Server 2003 版本的.NET framework 包含的額外屬性**DataReader**， **HasRows**，這可讓您判斷如果**DataReader**從中傳回任何結果之前讀取。</span><span class="sxs-lookup"><span data-stu-id="4caec-110">The Windows Server 2003 release of the .NET Framework includes an additional property for the **DataReader**, **HasRows**, which enables you to determine if the **DataReader** has returned any results before reading from it.</span></span>  
  
 <span data-ttu-id="4caec-111">下列程式碼範例會逐一**DataReader**物件，並傳回每個資料列的兩個資料行。</span><span class="sxs-lookup"><span data-stu-id="4caec-111">The following code example iterates through a **DataReader** object, and returns two columns from each row.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
 <span data-ttu-id="4caec-112">**DataReader**提供未緩衝處理資料流的資料，可讓程序邏輯有效地循序處理來自資料來源的結果。</span><span class="sxs-lookup"><span data-stu-id="4caec-112">The **DataReader** provides an unbuffered stream of data that allows procedural logic to efficiently process results from a data source sequentially.</span></span> <span data-ttu-id="4caec-113">**DataReader**擷取大量資料，因為資料不會快取記憶體時，是不錯的選擇。</span><span class="sxs-lookup"><span data-stu-id="4caec-113">The **DataReader** is a good choice when retrieving large amounts of data because the data is not cached in memory.</span></span>  
  
## <a name="closing-the-datareader"></a><span data-ttu-id="4caec-114">關閉 DataReader</span><span class="sxs-lookup"><span data-stu-id="4caec-114">Closing the DataReader</span></span>  
 <span data-ttu-id="4caec-115">您應該一律呼叫**關閉**方法，當您完成使用**DataReader**物件。</span><span class="sxs-lookup"><span data-stu-id="4caec-115">You should always call the **Close** method when you have finished using the **DataReader** object.</span></span>  
  
 <span data-ttu-id="4caec-116">如果您**命令**包含輸出參數或傳回值，它們將無法使用之前**DataReader**已關閉。</span><span class="sxs-lookup"><span data-stu-id="4caec-116">If your **Command** contains output parameters or return values, they will not be available until the **DataReader** is closed.</span></span>  
  
 <span data-ttu-id="4caec-117">請注意，雖然**DataReader**開啟，請**連線**處於只能供該**DataReader**。</span><span class="sxs-lookup"><span data-stu-id="4caec-117">Note that while a **DataReader** is open, the **Connection** is in use exclusively by that **DataReader**.</span></span> <span data-ttu-id="4caec-118">您無法執行任何命令**連接**，包括建立其他**DataReader**，直到原始**DataReader**已關閉。</span><span class="sxs-lookup"><span data-stu-id="4caec-118">You cannot execute any commands for the **Connection**, including creating another **DataReader**, until the original **DataReader** is closed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4caec-119">不要呼叫**關閉**或**Dispose**上**連接**，則**DataReader**，或在任何其他 managed 的物件**Finalize**您類別的方法。</span><span class="sxs-lookup"><span data-stu-id="4caec-119">Do not call **Close** or **Dispose** on a **Connection**, a **DataReader**, or any other managed object in the **Finalize** method of your class.</span></span> <span data-ttu-id="4caec-120">在完成項中，只需釋放類別直接擁有的 Unmanaged 資源。</span><span class="sxs-lookup"><span data-stu-id="4caec-120">In a finalizer, only release unmanaged resources that your class owns directly.</span></span> <span data-ttu-id="4caec-121">如果您的類別未擁有任何 unmanaged 的資源，並包含**Finalize**類別定義中的方法。</span><span class="sxs-lookup"><span data-stu-id="4caec-121">If your class does not own any unmanaged resources, do not include a **Finalize** method in your class definition.</span></span> <span data-ttu-id="4caec-122">如需詳細資訊，請參閱 <<c0> [ 回收](../../../../docs/standard/garbage-collection/index.md)。</span><span class="sxs-lookup"><span data-stu-id="4caec-122">For more information, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a><span data-ttu-id="4caec-123">使用 NextResult 來擷取多個結果集</span><span class="sxs-lookup"><span data-stu-id="4caec-123">Retrieving Multiple Result Sets using NextResult</span></span>  
 <span data-ttu-id="4caec-124">如果傳回多個結果集， **DataReader**提供**NextResult**方法來逐一查看結果集中的順序。</span><span class="sxs-lookup"><span data-stu-id="4caec-124">If multiple result sets are returned, the **DataReader** provides the **NextResult** method to iterate through the result sets in order.</span></span> <span data-ttu-id="4caec-125">下列範例顯示 <xref:System.Data.SqlClient.SqlDataReader> 使用 <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> 方法，處理兩個 SELECT 陳述式的結果。</span><span class="sxs-lookup"><span data-stu-id="4caec-125">The following example shows the <xref:System.Data.SqlClient.SqlDataReader> processing the results of two SELECT statements using the <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> method.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a><span data-ttu-id="4caec-126">從 DataReader 取得結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="4caec-126">Getting Schema Information from the DataReader</span></span>  
 <span data-ttu-id="4caec-127">雖然**DataReader**已開啟，您可以擷取目前結果集使用的結構描述資訊**GetSchemaTable**方法。</span><span class="sxs-lookup"><span data-stu-id="4caec-127">While a **DataReader** is open, you can retrieve schema information about the current result set using the **GetSchemaTable** method.</span></span> <span data-ttu-id="4caec-128">**GetSchemaTable**傳回<xref:System.Data.DataTable>填入資料列和資料行包含目前的結果集的結構描述資訊的物件。</span><span class="sxs-lookup"><span data-stu-id="4caec-128">**GetSchemaTable** returns a <xref:System.Data.DataTable> object populated with rows and columns that contain the schema information for the current result set.</span></span> <span data-ttu-id="4caec-129">**DataTable**包含一個資料列結果集的每個資料行。</span><span class="sxs-lookup"><span data-stu-id="4caec-129">The **DataTable** contains one row for each column of the result set.</span></span> <span data-ttu-id="4caec-130">結構描述資料表資料列的每個資料行對應到屬性中傳回的資料行的結果集，其中**ColumnName**是屬性的名稱和資料行的值是屬性的值。</span><span class="sxs-lookup"><span data-stu-id="4caec-130">Each column of the schema table row maps to a property of the column returned in the result set, where the **ColumnName** is the name of the property and the value of the column is the value of the property.</span></span> <span data-ttu-id="4caec-131">下列的程式碼範例會寫出的結構描述資訊**DataReader**。</span><span class="sxs-lookup"><span data-stu-id="4caec-131">The following code example writes out the schema information for **DataReader**.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a><span data-ttu-id="4caec-132">使用 OLE DB 章節</span><span class="sxs-lookup"><span data-stu-id="4caec-132">Working with OLE DB Chapters</span></span>  
 <span data-ttu-id="4caec-133">階層式資料列集或章節 (OLE DB 型別**DBTYPE_HCHAPTER**、 ADO 型別**adChapter**) 可以使用擷取<xref:System.Data.OleDb.OleDbDataReader>。</span><span class="sxs-lookup"><span data-stu-id="4caec-133">Hierarchical rowsets, or chapters (OLE DB type **DBTYPE_HCHAPTER**, ADO type **adChapter**) can be retrieved using the <xref:System.Data.OleDb.OleDbDataReader>.</span></span> <span data-ttu-id="4caec-134">當其中一章包含的查詢會以傳回**DataReader**，章節會傳回做為資料行中的**DataReader** ，並公開為**DataReader**物件。</span><span class="sxs-lookup"><span data-stu-id="4caec-134">When a query that includes a chapter is returned as a **DataReader**, the chapter is returned as a column in that **DataReader** and is exposed as a **DataReader** object.</span></span>  
  
 <span data-ttu-id="4caec-135">ADO.NET**資料集**也可用來代表使用資料表之間的父子式關聯性的階層式資料列集。</span><span class="sxs-lookup"><span data-stu-id="4caec-135">The ADO.NET **DataSet** can also be used to represent hierarchical rowsets using parent-child relationships between tables.</span></span> <span data-ttu-id="4caec-136">如需詳細資訊，請參閱 < [Dataset、 Datatable 和 Dataview](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)。</span><span class="sxs-lookup"><span data-stu-id="4caec-136">For more information, see [DataSets, DataTables, and DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).</span></span>  
  
 <span data-ttu-id="4caec-137">下列程式碼範例使用 MSDataShape 提供者，替客戶清單中每位客戶的訂單產生章節資料行。</span><span class="sxs-lookup"><span data-stu-id="4caec-137">The following code example uses the MSDataShape Provider to generate a chapter column of orders for each customer in a list of customers.</span></span>  
  
```vb  
Using connection As OleDbConnection = New OleDbConnection( _  
  "Provider=MSDataShape;Data Provider=SQLOLEDB;" & _  
  "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind")  
  
Dim custCMD As OleDbCommand = New OleDbCommand( _  
  "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " & _  
  "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " & _  
  "RELATE CustomerID TO CustomerID)", connection)  
connection.Open()  
  
Dim custReader As OleDbDataReader = custCMD.ExecuteReader()  
Dim orderReader As OleDbDataReader  
  
Do While custReader.Read()  
  Console.WriteLine("Orders for " & custReader.GetString(1))   
  ' custReader.GetString(1) = CompanyName  
  
  orderReader = custReader.GetValue(2)  
  ' custReader.GetValue(2) = Orders chapter as DataReader  
  
  Do While orderReader.Read()  
    Console.WriteLine(vbTab & orderReader.GetInt32(1))  
    ' orderReader.GetInt32(1) = OrderID  
  Loop  
  orderReader.Close()  
Loop  
' Make sure to always close readers and connections.  
custReader.Close()  
End Using  
```  
  
```csharp  
Using (OleDbConnection connection = new OleDbConnection(  
  "Provider=MSDataShape;Data Provider=SQLOLEDB;" +  
  "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind"));  
{  
OleDbCommand custCMD = new OleDbCommand(  
  "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " +  
  "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " +  
  "RELATE CustomerID TO CustomerID)", connection);  
connection.Open();  
  
OleDbDataReader custReader = custCMD.ExecuteReader();  
OleDbDataReader orderReader;  
  
while (custReader.Read())  
{  
  Console.WriteLine("Orders for " + custReader.GetString(1));   
  // custReader.GetString(1) = CompanyName  
  
  orderReader = (OleDbDataReader)custReader.GetValue(2);        
  // custReader.GetValue(2) = Orders chapter as DataReader  
  
  while (orderReader.Read())  
    Console.WriteLine("\t" + orderReader.GetInt32(1));          
    // orderReader.GetInt32(1) = OrderID  
  orderReader.Close();  
}  
// Make sure to always close readers and connections.  
custReader.Close();  
}  
```  
  
## <a name="returning-results-with-oracle-ref-cursors"></a><span data-ttu-id="4caec-138">使用 Oracle REF CURSOR 來傳回結果</span><span class="sxs-lookup"><span data-stu-id="4caec-138">Returning Results with Oracle REF CURSORs</span></span>  
 <span data-ttu-id="4caec-139">Oracle 的 .NET Framework 資料提供者支援使用 Oracle REF CURSOR 傳回查詢結果。</span><span class="sxs-lookup"><span data-stu-id="4caec-139">The .NET Framework Data Provider for Oracle supports the use of Oracle REF CURSORs to return a query result.</span></span> <span data-ttu-id="4caec-140">Oracle REF CURSOR 以 <xref:System.Data.OracleClient.OracleDataReader> 傳回。</span><span class="sxs-lookup"><span data-stu-id="4caec-140">An Oracle REF CURSOR is returned as an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 <span data-ttu-id="4caec-141">您可以擷取**OracleDataReader**物件，表示使用 Oracle REF CURSOR<xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>方法，而且您也可以指定<xref:System.Data.OracleClient.OracleCommand>傳回做為一或多個 Oracle REF Cursor **SelectCommand** for<xref:System.Data.OracleClient.OracleDataAdapter>用來填滿<xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="4caec-141">You can retrieve an **OracleDataReader** object, that represents an Oracle REF CURSOR using the <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> method, and you can also specify an <xref:System.Data.OracleClient.OracleCommand> that returns one or more Oracle REF CURSORs as the **SelectCommand** for an <xref:System.Data.OracleClient.OracleDataAdapter> used to fill a <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="4caec-142">若要存取從 Oracle 資料來源傳回的 REF CURSOR，請建立**OracleCommand**為您的查詢，並新增參考至 REF CURSOR 輸出參數**參數**您的集合**OracleCommand**。</span><span class="sxs-lookup"><span data-stu-id="4caec-142">To access a REF CURSOR returned from an Oracle data source, create an **OracleCommand** for your query and add an output parameter that references the REF CURSOR to the **Parameters** collection of your **OracleCommand**.</span></span> <span data-ttu-id="4caec-143">參數的名稱必須符合查詢中 REF CURSOR 參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="4caec-143">The name of the parameter must match the name of the REF CURSOR parameter in your query.</span></span> <span data-ttu-id="4caec-144">設定以參數的型別**OracleType.Cursor**。</span><span class="sxs-lookup"><span data-stu-id="4caec-144">Set the type of the parameter to **OracleType.Cursor**.</span></span> <span data-ttu-id="4caec-145">**ExecuteReader**方法的程式**OracleCommand**會傳回**OracleDataReader** REF cursor。</span><span class="sxs-lookup"><span data-stu-id="4caec-145">The **ExecuteReader** method of your **OracleCommand** will return an **OracleDataReader** for the REF CURSOR.</span></span>  
  
 <span data-ttu-id="4caec-146">如果您**OracleCommand**傳回多個 REF CURSOR，新增多個輸出參數。</span><span class="sxs-lookup"><span data-stu-id="4caec-146">If your **OracleCommand** returns multiple REF CURSORS, add multiple output parameters.</span></span> <span data-ttu-id="4caec-147">您可以藉由呼叫不同的 REF Cursor **OracleCommand.ExecuteReader**方法。</span><span class="sxs-lookup"><span data-stu-id="4caec-147">You can access the different REF CURSORs by calling the **OracleCommand.ExecuteReader** method.</span></span> <span data-ttu-id="4caec-148">若要在呼叫**ExecuteReader**會傳回**OracleDataReader**參考第一個 REF CURSOR。</span><span class="sxs-lookup"><span data-stu-id="4caec-148">The call to **ExecuteReader** returns an **OracleDataReader** referencing the first REF CURSOR.</span></span> <span data-ttu-id="4caec-149">您可以接著呼叫**OracleDataReader.NextResult**方法來存取後續的 REF Cursor。</span><span class="sxs-lookup"><span data-stu-id="4caec-149">You can then call the **OracleDataReader.NextResult** method to access subsequent REF CURSORs.</span></span> <span data-ttu-id="4caec-150">雖然參數在您**OracleCommand.Parameters**集合與 REF CURSOR 輸出參數名稱， **OracleDataReader**存取它們的順序，其已加入**參數**集合。</span><span class="sxs-lookup"><span data-stu-id="4caec-150">Although the parameters in your **OracleCommand.Parameters** collection match the REF CURSOR output parameters by name, the **OracleDataReader** accesses them in the order that they were added to the **Parameters** collection.</span></span>  
  
 <span data-ttu-id="4caec-151">例如，請考慮下列的 Oracle Package 和 Package 內容。</span><span class="sxs-lookup"><span data-stu-id="4caec-151">For example, consider the following Oracle package and package body.</span></span>  
  
```  
CREATE OR REPLACE PACKAGE CURSPKG AS   
  TYPE T_CURSOR IS REF CURSOR;   
  PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,   
    DEPTCURSOR OUT T_CURSOR);   
END CURSPKG;  
  
CREATE OR REPLACE PACKAGE BODY CURSPKG AS   
  PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,   
    DEPTCURSOR OUT T_CURSOR)   
  IS   
  BEGIN   
    OPEN EMPCURSOR FOR SELECT * FROM DEMO.EMPLOYEE;   
    OPEN DEPTCURSOR FOR SELECT * FROM DEMO.DEPARTMENT;   
  END OPEN_TWO_CURSORS;   
END CURSPKG;   
```  
  
 <span data-ttu-id="4caec-152">下列程式碼會建立**OracleCommand** ，從上一個 Oracle package 傳回 REF Cursor 加上兩個參數的型別**OracleType.Cursor**到**參數**集合。</span><span class="sxs-lookup"><span data-stu-id="4caec-152">The following code creates an **OracleCommand** that returns the REF CURSORs from the previous Oracle package by adding two parameters of type **OracleType.Cursor** to the **Parameters** collection.</span></span>  
  
```vb  
Dim cursCmd As OracleCommand = New OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn)  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
```  
  
```csharp  
OracleCommand cursCmd = new OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn);  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
```  
  
 <span data-ttu-id="4caec-153">下列程式碼會傳回前一個命令使用的結果**讀取**並**NextResult**方法**OracleDataReader**。</span><span class="sxs-lookup"><span data-stu-id="4caec-153">The following code returns the results of the previous command using the **Read** and **NextResult** methods of the **OracleDataReader**.</span></span> <span data-ttu-id="4caec-154">REF CURSOR 參數會依順序傳回。</span><span class="sxs-lookup"><span data-stu-id="4caec-154">The REF CURSOR parameters are returned in order.</span></span>  
  
```vb  
oraConn.Open()  
  
Dim cursCmd As OracleCommand = New OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn)  
cursCmd.CommandType = CommandType.StoredProcedure  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
  
Dim reader As OracleDataReader = cursCmd.ExecuteReader()  
  
Console.WriteLine(vbCrLf & "Emp ID" & vbTab & "Name")  
  
Do While reader.Read()  
  Console.WriteLine("{0}" & vbTab & "{1}, {2}", reader.GetOracleNumber(0), reader.GetString(1), reader.GetString(2))  
Loop  
  
reader.NextResult()  
  
Console.WriteLine(vbCrLf & "Dept ID" & vbTab & "Name")  
  
Do While reader.Read()  
  Console.WriteLine("{0}" & vbTab & "{1}", reader.GetOracleNumber(0), reader.GetString(1))  
Loop  
' Make sure to always close readers and connections.  
reader.Close()  
oraConn.Close()  
```  
  
```csharp  
oraConn.Open();  
  
OracleCommand cursCmd = new OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn);  
cursCmd.CommandType = CommandType.StoredProcedure;  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
  
OracleDataReader reader = cursCmd.ExecuteReader();  
  
Console.WriteLine("\nEmp ID\tName");  
  
while (reader.Read())  
  Console.WriteLine("{0}\t{1}, {2}", reader.GetOracleNumber(0), reader.GetString(1), reader.GetString(2));  
  
reader.NextResult();  
  
Console.WriteLine("\nDept ID\tName");  
  
while (reader.Read())  
  Console.WriteLine("{0}\t{1}", reader.GetOracleNumber(0), reader.GetString(1));  
// Make sure to always close readers and connections.  
reader.Close();  
oraConn.Close();  
```  
  
 <span data-ttu-id="4caec-155">下列範例會使用前一個命令來填入**資料集**Oracle package 的結果。</span><span class="sxs-lookup"><span data-stu-id="4caec-155">The following example uses the previous command to populate a **DataSet** with the results of the Oracle package.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4caec-156">若要避免**OverflowException**，我們建議您也會處理任何從 Oracle NUMBER 型別轉換為有效的.NET Framework 型別儲存中的值之前**DataRow**。</span><span class="sxs-lookup"><span data-stu-id="4caec-156">To avoid an **OverflowException**, we recommend that you also handle any conversion from the Oracle NUMBER type to a valid .NET Framework type before storing the value in a **DataRow**.</span></span> <span data-ttu-id="4caec-157">您可以使用**FillError**事件，以判斷**OverflowException**發生。</span><span class="sxs-lookup"><span data-stu-id="4caec-157">You can use the **FillError** event to determine if an **OverflowException** has occurred.</span></span> <span data-ttu-id="4caec-158">如需詳細資訊**FillError**事件，請參閱[處理 DataAdapter 事件](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)。</span><span class="sxs-lookup"><span data-stu-id="4caec-158">For more information on the **FillError** event, see [Handling DataAdapter Events](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span></span>  
  
```vb  
Dim ds As DataSet = New DataSet()  
  
Dim adapter As OracleDataAdapter = New OracleDataAdapter(cursCmd)  
adapter.TableMappings.Add("Table", "Employees")  
adapter.TableMappings.Add("Table1", "Departments")  
  
adapter.Fill(ds)  
```  
  
```csharp  
DataSet ds = new DataSet();  
  
OracleDataAdapter adapter = new OracleDataAdapter(cursCmd);  
adapter.TableMappings.Add("Table", "Employees");  
adapter.TableMappings.Add("Table1", "Departments");  
  
adapter.Fill(ds);  
```  
  
## <a name="see-also"></a><span data-ttu-id="4caec-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4caec-159">See Also</span></span>  
 [<span data-ttu-id="4caec-160">使用 Datareader</span><span class="sxs-lookup"><span data-stu-id="4caec-160">Working with DataReaders</span></span>](https://msdn.microsoft.com/library/126a966a-d08d-4d22-a19f-f432908b2b54)  
 [<span data-ttu-id="4caec-161">DataAdapter 和 DataReader</span><span class="sxs-lookup"><span data-stu-id="4caec-161">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="4caec-162">命令和參數</span><span class="sxs-lookup"><span data-stu-id="4caec-162">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="4caec-163">擷取資料庫結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="4caec-163">Retrieving Database Schema Information</span></span>](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [<span data-ttu-id="4caec-164">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="4caec-164">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
