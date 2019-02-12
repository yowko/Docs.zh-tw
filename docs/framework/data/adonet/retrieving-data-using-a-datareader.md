---
title: 使用 DataReader 擷取資料
ms.date: 10/29/2018
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.openlocfilehash: ff1869ab17761645321d803f0f7db4bb39c992bc
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2019
ms.locfileid: "56093277"
---
# <a name="retrieve-data-using-a-datareader"></a><span data-ttu-id="177e8-102">使用 DataReader 擷取資料</span><span class="sxs-lookup"><span data-stu-id="177e8-102">Retrieve data using a DataReader</span></span>
<span data-ttu-id="177e8-103">若要擷取的資料使用**DataReader**，建立的執行個體**命令**物件，然後再建立**DataReader**藉由呼叫**Command.ExecuteReader**從資料來源擷取資料列。</span><span class="sxs-lookup"><span data-stu-id="177e8-103">To retrieve data using a **DataReader**, create an instance of the **Command** object, and then create a **DataReader** by calling **Command.ExecuteReader** to retrieve rows from a data source.</span></span> <span data-ttu-id="177e8-104">**DataReader**提供未緩衝處理資料流的資料，可讓程序邏輯有效地循序處理來自資料來源的結果。</span><span class="sxs-lookup"><span data-stu-id="177e8-104">The **DataReader** provides an unbuffered stream of data that allows procedural logic to efficiently process results from a data source sequentially.</span></span> <span data-ttu-id="177e8-105">**DataReader**是不錯的選擇，因為資料不會快取記憶體，在擷取大量資料時。</span><span class="sxs-lookup"><span data-stu-id="177e8-105">The **DataReader** is a good choice when you're retrieving large amounts of data because the data is not cached in memory.</span></span>

<span data-ttu-id="177e8-106">下列範例說明如何利用**DataReader**，其中`reader`代表有效的 DataReader 和`command`代表有效的命令物件。</span><span class="sxs-lookup"><span data-stu-id="177e8-106">The following example illustrates using a **DataReader**, where `reader` represents a valid DataReader and `command` represents a valid Command object.</span></span>  

```csharp
reader = command.ExecuteReader();  
```

```vb
reader = command.ExecuteReader()
```  

<span data-ttu-id="177e8-107">使用**DataReader.Read**方法，以從查詢結果取得資料列。</span><span class="sxs-lookup"><span data-stu-id="177e8-107">Use the **DataReader.Read** method to obtain a row from the query results.</span></span> <span data-ttu-id="177e8-108">您可以藉由傳遞的名稱或序數編號的資料行傳回的資料列的每個資料行**DataReader**。</span><span class="sxs-lookup"><span data-stu-id="177e8-108">You can access each column of the returned row by passing the name or ordinal number of the column to the **DataReader**.</span></span> <span data-ttu-id="177e8-109">不過，為了達到最佳效能， **DataReader**提供一系列的方法，可讓您存取其原生資料類型的資料行值 (**GetDateTime**， **GetDouble**， **GetGuid**， **GetInt32**等等)。</span><span class="sxs-lookup"><span data-stu-id="177e8-109">However, for best performance, the **DataReader** provides a series of methods that allow you to access column values in their native data types (**GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**, and so on).</span></span> <span data-ttu-id="177e8-110">如需資料提供者特有的具型別存取子方法的清單**Datareader**，請參閱<xref:System.Data.OleDb.OleDbDataReader>和<xref:System.Data.SqlClient.SqlDataReader>。</span><span class="sxs-lookup"><span data-stu-id="177e8-110">For a list of typed accessor methods for data provider-specific **DataReaders**, see <xref:System.Data.OleDb.OleDbDataReader> and <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="177e8-111">使用具型別存取子方法，當您知道的基本資料型別可減少擷取資料行的值時所需的型別轉換的量。</span><span class="sxs-lookup"><span data-stu-id="177e8-111">Using the typed accessor methods when you know the underlying data type reduces the amount of type conversion required when retrieving the column value.</span></span>  
  
 <span data-ttu-id="177e8-112">下列範例會逐一**DataReader**物件，並傳回每個資料列的兩個資料行。</span><span class="sxs-lookup"><span data-stu-id="177e8-112">The following example iterates through a **DataReader** object and returns two columns from each row.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
## <a name="closing-the-datareader"></a><span data-ttu-id="177e8-113">關閉 DataReader</span><span class="sxs-lookup"><span data-stu-id="177e8-113">Closing the DataReader</span></span>  
 <span data-ttu-id="177e8-114">請務必呼叫**關閉**方法，當您完成使用**DataReader**物件。</span><span class="sxs-lookup"><span data-stu-id="177e8-114">Always call the **Close** method when you have finished using the **DataReader** object.</span></span>  
  
 <span data-ttu-id="177e8-115">如果您**命令**包含輸出參數或傳回值，這些值沒有直到**DataReader**已關閉。</span><span class="sxs-lookup"><span data-stu-id="177e8-115">If your **Command** contains output parameters or return values, those values are not available until the **DataReader** is closed.</span></span>  
  
 <span data-ttu-id="177e8-116">雖然**DataReader**開啟，請**連線**處於只能供該**DataReader**。</span><span class="sxs-lookup"><span data-stu-id="177e8-116">While a **DataReader** is open, the **Connection** is in use exclusively by that **DataReader**.</span></span> <span data-ttu-id="177e8-117">您無法執行任何命令**連接**，包括建立其他**DataReader**，直到原始**DataReader**已關閉。</span><span class="sxs-lookup"><span data-stu-id="177e8-117">You cannot execute any commands for the **Connection**, including creating another **DataReader**, until the original **DataReader** is closed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="177e8-118">不要呼叫**關閉**或**Dispose**上**連接**，則**DataReader**，或在任何其他 managed 的物件**Finalize**您類別的方法。</span><span class="sxs-lookup"><span data-stu-id="177e8-118">Do not call **Close** or **Dispose** on a **Connection**, a **DataReader**, or any other managed object in the **Finalize** method of your class.</span></span> <span data-ttu-id="177e8-119">在完成項中，只需釋放類別直接擁有的 Unmanaged 資源。</span><span class="sxs-lookup"><span data-stu-id="177e8-119">In a finalizer, only release unmanaged resources that your class owns directly.</span></span> <span data-ttu-id="177e8-120">如果您的類別未擁有任何 unmanaged 的資源，並包含**Finalize**類別定義中的方法。</span><span class="sxs-lookup"><span data-stu-id="177e8-120">If your class does not own any unmanaged resources, do not include a **Finalize** method in your class definition.</span></span> <span data-ttu-id="177e8-121">如需詳細資訊，請參閱 <<c0> [ 回收](../../../../docs/standard/garbage-collection/index.md)。</span><span class="sxs-lookup"><span data-stu-id="177e8-121">For more information, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a><span data-ttu-id="177e8-122">使用 nextresult 來擷取多個結果設定</span><span class="sxs-lookup"><span data-stu-id="177e8-122">Retrieving multiple result sets using NextResult</span></span>  
 <span data-ttu-id="177e8-123">如果**DataReader**會傳回多個結果集，呼叫**NextResult**來逐一查看結果的方法會以循序方式設定。</span><span class="sxs-lookup"><span data-stu-id="177e8-123">If the **DataReader** returns multiple result sets, call the **NextResult** method to iterate through the result sets sequentially.</span></span> <span data-ttu-id="177e8-124">下列範例顯示 <xref:System.Data.SqlClient.SqlDataReader> 使用 <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> 方法，處理兩個 SELECT 陳述式的結果。</span><span class="sxs-lookup"><span data-stu-id="177e8-124">The following example shows the <xref:System.Data.SqlClient.SqlDataReader> processing the results of two SELECT statements using the <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> method.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a><span data-ttu-id="177e8-125">從 DataReader 取得結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="177e8-125">Getting schema information from the DataReader</span></span>  
 <span data-ttu-id="177e8-126">雖然**DataReader**已開啟，您可以擷取目前結果集使用的結構描述資訊**GetSchemaTable**方法。</span><span class="sxs-lookup"><span data-stu-id="177e8-126">While a **DataReader** is open, you can retrieve schema information about the current result set using the **GetSchemaTable** method.</span></span> <span data-ttu-id="177e8-127">**GetSchemaTable**傳回<xref:System.Data.DataTable>填入資料列和資料行包含目前的結果集的結構描述資訊的物件。</span><span class="sxs-lookup"><span data-stu-id="177e8-127">**GetSchemaTable** returns a <xref:System.Data.DataTable> object populated with rows and columns that contain the schema information for the current result set.</span></span> <span data-ttu-id="177e8-128">**DataTable**包含一個資料列結果集的每個資料行。</span><span class="sxs-lookup"><span data-stu-id="177e8-128">The **DataTable** contains one row for each column of the result set.</span></span> <span data-ttu-id="177e8-129">結構描述資料表的每個資料行對應到屬性中傳回的資料行結果的資料列集，其中**ColumnName**是屬性的名稱和資料行的值是屬性的值。</span><span class="sxs-lookup"><span data-stu-id="177e8-129">Each column of the schema table maps to a property of the columns returned in the rows of the result set, where the **ColumnName** is the name of the property and the value of the column is the value of the property.</span></span> <span data-ttu-id="177e8-130">下列範例會寫出的結構描述資訊**DataReader**。</span><span class="sxs-lookup"><span data-stu-id="177e8-130">The following example writes out the schema information for **DataReader**.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a><span data-ttu-id="177e8-131">使用 OLE DB 章節</span><span class="sxs-lookup"><span data-stu-id="177e8-131">Working with OLE DB chapters</span></span>  
 <span data-ttu-id="177e8-132">階層式資料列集或章節 (OLE DB 型別**DBTYPE_HCHAPTER**、 ADO 型別**adChapter**)，您可以使用擷取<xref:System.Data.OleDb.OleDbDataReader>。</span><span class="sxs-lookup"><span data-stu-id="177e8-132">Hierarchical rowsets, or chapters (OLE DB type **DBTYPE_HCHAPTER**, ADO type **adChapter**), can be retrieved using the <xref:System.Data.OleDb.OleDbDataReader>.</span></span> <span data-ttu-id="177e8-133">當其中一章包含的查詢會以傳回**DataReader**，章節會傳回做為資料行中的**DataReader** ，並公開為**DataReader**物件。</span><span class="sxs-lookup"><span data-stu-id="177e8-133">When a query that includes a chapter is returned as a **DataReader**, the chapter is returned as a column in that **DataReader** and is exposed as a **DataReader** object.</span></span>  
  
 <span data-ttu-id="177e8-134">ADO.NET**資料集**也可用來代表階層式資料列集使用資料表之間的父子式關聯性。</span><span class="sxs-lookup"><span data-stu-id="177e8-134">The ADO.NET **DataSet** can also be used to represent hierarchical rowsets by using parent-child relationships between tables.</span></span> <span data-ttu-id="177e8-135">如需詳細資訊，請參閱 < [Dataset、 Datatable 和 Dataview](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)。</span><span class="sxs-lookup"><span data-stu-id="177e8-135">For more information, see [DataSets, DataTables, and DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).</span></span>  
  
 <span data-ttu-id="177e8-136">下列程式碼範例使用 MSDataShape 提供者，替客戶清單中每位客戶的訂單產生章節資料行。</span><span class="sxs-lookup"><span data-stu-id="177e8-136">The following code example uses the MSDataShape Provider to generate a chapter column of orders for each customer in a list of customers.</span></span>  
  
```vb  
Using connection As OleDbConnection = New OleDbConnection(
    "Provider=MSDataShape;Data Provider=SQLOLEDB;" &
    "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind")

    Using custCMD As OleDbCommand = New OleDbCommand(
        "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " &
        "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " &
        "RELATE CustomerID TO CustomerID)", connection)

        connection.Open()

        Using custReader As OleDbDataReader = custCMD.ExecuteReader()

            Do While custReader.Read()
                Console.WriteLine("Orders for " & custReader.GetString(1))
                ' custReader.GetString(1) = CompanyName  

                Using orderReader As OleDbDataReader = custReader.GetValue(2)
                    ' custReader.GetValue(2) = Orders chapter as DataReader  

                    Do While orderReader.Read()
                        Console.WriteLine(vbTab & orderReader.GetInt32(1))
                        ' orderReader.GetInt32(1) = OrderID  
                    Loop
                    orderReader.Close()
                End Using
            Loop
            ' Make sure to always close readers and connections.  
            custReader.Close()
        End Using
    End Using
End Using
```  
  
```csharp  
using (OleDbConnection connection = new OleDbConnection(
    "Provider=MSDataShape;Data Provider=SQLOLEDB;" +
    "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind"))
{
    using (OleDbCommand custCMD = new OleDbCommand(
        "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " +
        "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " +
        "RELATE CustomerID TO CustomerID)", connection))
    {
        connection.Open();

        using (OleDbDataReader custReader = custCMD.ExecuteReader())
        {

            while (custReader.Read())
            {
                Console.WriteLine("Orders for " + custReader.GetString(1));
                // custReader.GetString(1) = CompanyName  

                using (OleDbDataReader orderReader = (OleDbDataReader)custReader.GetValue(2))
                {
                    // custReader.GetValue(2) = Orders chapter as DataReader  

                    while (orderReader.Read())
                        Console.WriteLine("\t" + orderReader.GetInt32(1));
                    // orderReader.GetInt32(1) = OrderID  
                    orderReader.Close();
                }
            }
            // Make sure to always close readers and connections.  
            custReader.Close();
        }
    }
}
```  
  
## <a name="returning-results-with-oracle-ref-cursors"></a><span data-ttu-id="177e8-137">傳回使用 Oracle REF Cursor 的結果</span><span class="sxs-lookup"><span data-stu-id="177e8-137">Returning results with Oracle REF CURSORs</span></span>  
 <span data-ttu-id="177e8-138">Oracle 的 .NET Framework 資料提供者支援使用 Oracle REF CURSOR 傳回查詢結果。</span><span class="sxs-lookup"><span data-stu-id="177e8-138">The .NET Framework Data Provider for Oracle supports the use of Oracle REF CURSORs to return a query result.</span></span> <span data-ttu-id="177e8-139">Oracle REF CURSOR 以 <xref:System.Data.OracleClient.OracleDataReader> 傳回。</span><span class="sxs-lookup"><span data-stu-id="177e8-139">An Oracle REF CURSOR is returned as an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 <span data-ttu-id="177e8-140">您可以擷取<xref:System.Data.OracleClient.OracleDataReader>物件，表示所使用的 Oracle REF CURSOR<xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="177e8-140">You can retrieve an <xref:System.Data.OracleClient.OracleDataReader> object that represents an Oracle REF CURSOR by using the <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> method.</span></span> <span data-ttu-id="177e8-141">您也可以指定<xref:System.Data.OracleClient.OracleCommand>會傳回做為一或多個 Oracle REF Cursor **SelectCommand**如<xref:System.Data.OracleClient.OracleDataAdapter>用來填滿<xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="177e8-141">You can also specify an <xref:System.Data.OracleClient.OracleCommand> that returns one or more Oracle REF CURSORs as the **SelectCommand** for an <xref:System.Data.OracleClient.OracleDataAdapter> used to fill a <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="177e8-142">若要存取從 Oracle 資料來源傳回的 REF CURSOR，請建立<xref:System.Data.OracleClient.OracleCommand>為您的查詢，並新增參考至 REF CURSOR 輸出參數<xref:System.Data.OracleClient.OracleCommand.Parameters>的集合您<xref:System.Data.OracleClient.OracleCommand>。</span><span class="sxs-lookup"><span data-stu-id="177e8-142">To access a REF CURSOR returned from an Oracle data source, create an <xref:System.Data.OracleClient.OracleCommand> for your query and add an output parameter that references the REF CURSOR to the <xref:System.Data.OracleClient.OracleCommand.Parameters> collection of your <xref:System.Data.OracleClient.OracleCommand>.</span></span> <span data-ttu-id="177e8-143">參數的名稱必須符合查詢中 REF CURSOR 參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="177e8-143">The name of the parameter must match the name of the REF CURSOR parameter in your query.</span></span> <span data-ttu-id="177e8-144">設定以參數的型別<xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="177e8-144">Set the type of the parameter to <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>.</span></span> <span data-ttu-id="177e8-145"><xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType>方法您<xref:System.Data.OracleClient.OracleCommand>傳回<xref:System.Data.OracleClient.OracleDataReader>REF cursor。</span><span class="sxs-lookup"><span data-stu-id="177e8-145">The <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> method of your <xref:System.Data.OracleClient.OracleCommand> returns an <xref:System.Data.OracleClient.OracleDataReader> for the REF CURSOR.</span></span>  
  
 <span data-ttu-id="177e8-146">如果您<xref:System.Data.OracleClient.OracleCommand>傳回多個 REF CURSOR，新增多個輸出參數。</span><span class="sxs-lookup"><span data-stu-id="177e8-146">If your <xref:System.Data.OracleClient.OracleCommand> returns multiple REF CURSORS, add multiple output parameters.</span></span> <span data-ttu-id="177e8-147">您可以藉由呼叫不同的 REF Cursor<xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="177e8-147">You can access the different REF CURSORs by calling the <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="177e8-148">若要在呼叫<xref:System.Data.OracleClient.OracleCommand.ExecuteReader>傳回<xref:System.Data.OracleClient.OracleDataReader>參考第一個 REF CURSOR。</span><span class="sxs-lookup"><span data-stu-id="177e8-148">The call to <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> returns an <xref:System.Data.OracleClient.OracleDataReader> referencing the first REF CURSOR.</span></span> <span data-ttu-id="177e8-149">您可以接著呼叫<xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType>方法來存取後續的 REF Cursor。</span><span class="sxs-lookup"><span data-stu-id="177e8-149">You can then call the <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> method to access subsequent REF CURSORs.</span></span> <span data-ttu-id="177e8-150">雖然的參數，在您<xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType>集合與 REF CURSOR 輸出參數名稱，<xref:System.Data.OracleClient.OracleDataReader>存取它們的順序已新增至<xref:System.Data.OracleClient.OracleCommand.Parameters>集合。</span><span class="sxs-lookup"><span data-stu-id="177e8-150">Although the parameters in your <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> collection match the REF CURSOR output parameters by name, the <xref:System.Data.OracleClient.OracleDataReader> accesses them in the order in which they were added to the <xref:System.Data.OracleClient.OracleCommand.Parameters> collection.</span></span>  
  
 <span data-ttu-id="177e8-151">例如，請考慮下列的 Oracle Package 和 Package 內容。</span><span class="sxs-lookup"><span data-stu-id="177e8-151">For example, consider the following Oracle package and package body.</span></span>  
  
```sql
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
  
 <span data-ttu-id="177e8-152">下列程式碼會建立<xref:System.Data.OracleClient.OracleCommand>，從上一個 Oracle package 傳回 REF Cursor 加上兩個參數類型<xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>到<xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType>集合。</span><span class="sxs-lookup"><span data-stu-id="177e8-152">The following code creates an <xref:System.Data.OracleClient.OracleCommand> that returns the REF CURSORs from the previous Oracle package by adding two parameters of type <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> to the <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> collection.</span></span>  
  
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
  
 <span data-ttu-id="177e8-153">下列程式碼會傳回前一個命令使用的結果<xref:System.Data.OracleClient.OracleDataReader.Read>並<xref:System.Data.OracleClient.OracleDataReader.NextResult>方法<xref:System.Data.OracleClient.OracleDataReader>。</span><span class="sxs-lookup"><span data-stu-id="177e8-153">The following code returns the results of the previous command using the <xref:System.Data.OracleClient.OracleDataReader.Read> and <xref:System.Data.OracleClient.OracleDataReader.NextResult> methods of the <xref:System.Data.OracleClient.OracleDataReader>.</span></span> <span data-ttu-id="177e8-154">REF CURSOR 參數會依順序傳回。</span><span class="sxs-lookup"><span data-stu-id="177e8-154">The REF CURSOR parameters are returned in order.</span></span>  
  
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
  
 <span data-ttu-id="177e8-155">下列範例會使用前一個命令來填入<xref:System.Data.DataSet>Oracle package 的結果。</span><span class="sxs-lookup"><span data-stu-id="177e8-155">The following example uses the previous command to populate a <xref:System.Data.DataSet> with the results of the Oracle package.</span></span>  
  
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

> [!NOTE]
>  <span data-ttu-id="177e8-156">若要避免**OverflowException**，我們建議您也會處理任何從 Oracle NUMBER 型別轉換為有效的.NET Framework 型別儲存中的值之前<xref:System.Data.DataRow>。</span><span class="sxs-lookup"><span data-stu-id="177e8-156">To avoid an **OverflowException**, we recommend that you also handle any conversion from the Oracle NUMBER type to a valid .NET Framework type before storing the value in a <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="177e8-157">您可以使用<xref:System.Data.Common.DataAdapter.FillError>事件判斷是否**OverflowException**發生。</span><span class="sxs-lookup"><span data-stu-id="177e8-157">You can use the <xref:System.Data.Common.DataAdapter.FillError> event to determine if an **OverflowException** has occurred.</span></span> <span data-ttu-id="177e8-158">如需詳細資訊<xref:System.Data.Common.DataAdapter.FillError>事件，請參閱 <<c2> [ 處理 DataAdapter 事件](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)。</span><span class="sxs-lookup"><span data-stu-id="177e8-158">For more information on the <xref:System.Data.Common.DataAdapter.FillError> event, see [Handling DataAdapter Events](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="177e8-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="177e8-159">See also</span></span>
- [<span data-ttu-id="177e8-160">DataAdapter 和 DataReader</span><span class="sxs-lookup"><span data-stu-id="177e8-160">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [<span data-ttu-id="177e8-161">命令和參數</span><span class="sxs-lookup"><span data-stu-id="177e8-161">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [<span data-ttu-id="177e8-162">擷取資料庫結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="177e8-162">Retrieving Database Schema Information</span></span>](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)
- [<span data-ttu-id="177e8-163">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="177e8-163">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
