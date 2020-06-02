---
title: 使用 DataReader 擷取資料
description: 瞭解如何使用 ADO.NET 中的 DataReader 和此範例程式碼來抓取資料。 DataReader 提供未緩衝的資料流程。
ms.date: 10/29/2018
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.openlocfilehash: 6e5161cc325bf0379bb9241b99c473c539ad1081
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286594"
---
# <a name="retrieve-data-using-a-datareader"></a><span data-ttu-id="b1670-104">使用 DataReader 取出資料</span><span class="sxs-lookup"><span data-stu-id="b1670-104">Retrieve data using a DataReader</span></span>
<span data-ttu-id="b1670-105">若要使用**DataReader**來抓取資料，請建立**command**物件的實例，然後呼叫**ExecuteReader**來建立**DataReader** ，以從資料來源中取出資料列。</span><span class="sxs-lookup"><span data-stu-id="b1670-105">To retrieve data using a **DataReader**, create an instance of the **Command** object, and then create a **DataReader** by calling **Command.ExecuteReader** to retrieve rows from a data source.</span></span> <span data-ttu-id="b1670-106">**DataReader**提供了未緩衝的資料流程，可讓程式邏輯依序有效率地處理來自資料來源的結果。</span><span class="sxs-lookup"><span data-stu-id="b1670-106">The **DataReader** provides an unbuffered stream of data that allows procedural logic to efficiently process results from a data source sequentially.</span></span> <span data-ttu-id="b1670-107">當您正在抓取大量資料時， **DataReader**是不錯的選擇，因為資料不會快取到記憶體中。</span><span class="sxs-lookup"><span data-stu-id="b1670-107">The **DataReader** is a good choice when you're retrieving large amounts of data because the data is not cached in memory.</span></span>

<span data-ttu-id="b1670-108">下列範例說明如何使用**DataReader**，其中 `reader` 代表有效的 datareader，並 `command` 代表有效的命令物件。</span><span class="sxs-lookup"><span data-stu-id="b1670-108">The following example illustrates using a **DataReader**, where `reader` represents a valid DataReader and `command` represents a valid Command object.</span></span>  

```csharp
reader = command.ExecuteReader();  
```

```vb
reader = command.ExecuteReader()
```  

<span data-ttu-id="b1670-109">使用**DataReader. Read**方法，從查詢結果取得資料列。</span><span class="sxs-lookup"><span data-stu-id="b1670-109">Use the **DataReader.Read** method to obtain a row from the query results.</span></span> <span data-ttu-id="b1670-110">您可以將資料行的名稱或序數傳遞至**DataReader**，以存取傳回之資料列的每個資料行。</span><span class="sxs-lookup"><span data-stu-id="b1670-110">You can access each column of the returned row by passing the name or ordinal number of the column to the **DataReader**.</span></span> <span data-ttu-id="b1670-111">不過，為了達到最佳效能， **DataReader**提供一系列的方法，可讓您存取其原生資料類型（**GetDateTime**、 **GetDouble**、 **GetGuid**、 **GetInt32**等）中的資料行值。</span><span class="sxs-lookup"><span data-stu-id="b1670-111">However, for best performance, the **DataReader** provides a series of methods that allow you to access column values in their native data types (**GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**, and so on).</span></span> <span data-ttu-id="b1670-112">如需資料提供者特定**datareader**之具類型存取子方法的清單，請參閱 <xref:System.Data.OleDb.OleDbDataReader> 和 <xref:System.Data.SqlClient.SqlDataReader> 。</span><span class="sxs-lookup"><span data-stu-id="b1670-112">For a list of typed accessor methods for data provider-specific **DataReaders**, see <xref:System.Data.OleDb.OleDbDataReader> and <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="b1670-113">當您知道基礎資料類型時，使用具類型的存取子方法，可減少在抓取資料行值時所需的類型轉換數量。</span><span class="sxs-lookup"><span data-stu-id="b1670-113">Using the typed accessor methods when you know the underlying data type reduces the amount of type conversion required when retrieving the column value.</span></span>  
  
 <span data-ttu-id="b1670-114">下列範例會逐一查看**DataReader**物件，並傳回每個資料列中的兩個數據行。</span><span class="sxs-lookup"><span data-stu-id="b1670-114">The following example iterates through a **DataReader** object and returns two columns from each row.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
## <a name="closing-the-datareader"></a><span data-ttu-id="b1670-115">關閉 DataReader</span><span class="sxs-lookup"><span data-stu-id="b1670-115">Closing the DataReader</span></span>  
 <span data-ttu-id="b1670-116">當您完成使用**DataReader**物件時，請一律呼叫**Close**方法。</span><span class="sxs-lookup"><span data-stu-id="b1670-116">Always call the **Close** method when you have finished using the **DataReader** object.</span></span>  
  
 <span data-ttu-id="b1670-117">如果您的**命令**包含輸出參數或傳回值，則在**DataReader**關閉之前，這些值都無法使用。</span><span class="sxs-lookup"><span data-stu-id="b1670-117">If your **Command** contains output parameters or return values, those values are not available until the **DataReader** is closed.</span></span>  
  
 <span data-ttu-id="b1670-118">當**datareader**開啟時，該**datareader**會以獨佔方式使用**連接**。</span><span class="sxs-lookup"><span data-stu-id="b1670-118">While a **DataReader** is open, the **Connection** is in use exclusively by that **DataReader**.</span></span> <span data-ttu-id="b1670-119">您無法執行**連接**的任何命令，包括建立另一個**datareader**，直到原始**DataReader**關閉為止。</span><span class="sxs-lookup"><span data-stu-id="b1670-119">You cannot execute any commands for the **Connection**, including creating another **DataReader**, until the original **DataReader** is closed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b1670-120">請勿在**連接**、 **DataReader**或您類別的**Finalize**方法中的任何其他 Managed 物件上呼叫**Close**或**Dispose** 。</span><span class="sxs-lookup"><span data-stu-id="b1670-120">Do not call **Close** or **Dispose** on a **Connection**, a **DataReader**, or any other managed object in the **Finalize** method of your class.</span></span> <span data-ttu-id="b1670-121">在完成項中，只需釋放類別直接擁有的 Unmanaged 資源。</span><span class="sxs-lookup"><span data-stu-id="b1670-121">In a finalizer, only release unmanaged resources that your class owns directly.</span></span> <span data-ttu-id="b1670-122">如果您的類別未擁有任何非受控資源，請勿在您的類別定義中包含**Finalize**方法。</span><span class="sxs-lookup"><span data-stu-id="b1670-122">If your class does not own any unmanaged resources, do not include a **Finalize** method in your class definition.</span></span> <span data-ttu-id="b1670-123">如需詳細資訊，請參閱[垃圾收集](../../../standard/garbage-collection/index.md)。</span><span class="sxs-lookup"><span data-stu-id="b1670-123">For more information, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a><span data-ttu-id="b1670-124">使用 NextResult 抓取多個結果集</span><span class="sxs-lookup"><span data-stu-id="b1670-124">Retrieving multiple result sets using NextResult</span></span>  
 <span data-ttu-id="b1670-125">如果**DataReader**傳回多個結果集，請呼叫**NextResult**方法，依序逐一查看結果集。</span><span class="sxs-lookup"><span data-stu-id="b1670-125">If the **DataReader** returns multiple result sets, call the **NextResult** method to iterate through the result sets sequentially.</span></span> <span data-ttu-id="b1670-126">下列範例顯示 <xref:System.Data.SqlClient.SqlDataReader> 使用 <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> 方法，處理兩個 SELECT 陳述式的結果。</span><span class="sxs-lookup"><span data-stu-id="b1670-126">The following example shows the <xref:System.Data.SqlClient.SqlDataReader> processing the results of two SELECT statements using the <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> method.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a><span data-ttu-id="b1670-127">從 DataReader 取得架構資訊</span><span class="sxs-lookup"><span data-stu-id="b1670-127">Getting schema information from the DataReader</span></span>  
 <span data-ttu-id="b1670-128">當**DataReader**開啟時，您可以使用**GetSchemaTable**方法來抓取目前結果集的架構資訊。</span><span class="sxs-lookup"><span data-stu-id="b1670-128">While a **DataReader** is open, you can retrieve schema information about the current result set using the **GetSchemaTable** method.</span></span> <span data-ttu-id="b1670-129">**GetSchemaTable**會傳回一個物件，其中 <xref:System.Data.DataTable> 填入包含目前結果集之架構資訊的資料列和資料行。</span><span class="sxs-lookup"><span data-stu-id="b1670-129">**GetSchemaTable** returns a <xref:System.Data.DataTable> object populated with rows and columns that contain the schema information for the current result set.</span></span> <span data-ttu-id="b1670-130">**DataTable**會針對結果集的每個資料行，各包含一個資料列。</span><span class="sxs-lookup"><span data-stu-id="b1670-130">The **DataTable** contains one row for each column of the result set.</span></span> <span data-ttu-id="b1670-131">架構資料表的每個資料行都會對應到結果集資料列中所傳回之資料行的屬性，其中**ColumnName**是屬性的名稱，而資料行的值是屬性的值。</span><span class="sxs-lookup"><span data-stu-id="b1670-131">Each column of the schema table maps to a property of the columns returned in the rows of the result set, where the **ColumnName** is the name of the property and the value of the column is the value of the property.</span></span> <span data-ttu-id="b1670-132">下列範例會寫出**DataReader**的架構資訊。</span><span class="sxs-lookup"><span data-stu-id="b1670-132">The following example writes out the schema information for **DataReader**.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a><span data-ttu-id="b1670-133">使用 OLE DB 章節</span><span class="sxs-lookup"><span data-stu-id="b1670-133">Working with OLE DB chapters</span></span>  
 <span data-ttu-id="b1670-134">階層式資料列集或章節（OLE DB 類型**DBTYPE_HCHAPTER**，ADO 類型**adChapter**）可以使用來抓取 <xref:System.Data.OleDb.OleDbDataReader> 。</span><span class="sxs-lookup"><span data-stu-id="b1670-134">Hierarchical rowsets, or chapters (OLE DB type **DBTYPE_HCHAPTER**, ADO type **adChapter**), can be retrieved using the <xref:System.Data.OleDb.OleDbDataReader>.</span></span> <span data-ttu-id="b1670-135">當包含章節的查詢當做**datareader**傳回時，該章節會**當做 datareader 中**的資料行傳回，並公開為**datareader**物件。</span><span class="sxs-lookup"><span data-stu-id="b1670-135">When a query that includes a chapter is returned as a **DataReader**, the chapter is returned as a column in that **DataReader** and is exposed as a **DataReader** object.</span></span>  
  
 <span data-ttu-id="b1670-136">ADO.NET**資料集**也可以使用資料表之間的父子式關聯性，來表示階層資料列集。</span><span class="sxs-lookup"><span data-stu-id="b1670-136">The ADO.NET **DataSet** can also be used to represent hierarchical rowsets by using parent-child relationships between tables.</span></span> <span data-ttu-id="b1670-137">如需詳細資訊，請參閱[dataset、datatable 和 dataview](./dataset-datatable-dataview/index.md)。</span><span class="sxs-lookup"><span data-stu-id="b1670-137">For more information, see [DataSets, DataTables, and DataViews](./dataset-datatable-dataview/index.md).</span></span>  
  
 <span data-ttu-id="b1670-138">下列程式碼範例使用 MSDataShape 提供者，替客戶清單中每位客戶的訂單產生章節資料行。</span><span class="sxs-lookup"><span data-stu-id="b1670-138">The following code example uses the MSDataShape Provider to generate a chapter column of orders for each customer in a list of customers.</span></span>  
  
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
  
## <a name="returning-results-with-oracle-ref-cursors"></a><span data-ttu-id="b1670-139">使用 Oracle REF 資料指標傳回結果</span><span class="sxs-lookup"><span data-stu-id="b1670-139">Returning results with Oracle REF CURSORs</span></span>  
 <span data-ttu-id="b1670-140">Oracle 的 .NET Framework 資料提供者支援使用 Oracle REF CURSOR 傳回查詢結果。</span><span class="sxs-lookup"><span data-stu-id="b1670-140">The .NET Framework Data Provider for Oracle supports the use of Oracle REF CURSORs to return a query result.</span></span> <span data-ttu-id="b1670-141">Oracle REF CURSOR 以 <xref:System.Data.OracleClient.OracleDataReader> 傳回。</span><span class="sxs-lookup"><span data-stu-id="b1670-141">An Oracle REF CURSOR is returned as an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 <span data-ttu-id="b1670-142">您可以 <xref:System.Data.OracleClient.OracleDataReader> 使用方法來抓取代表 ORACLE REF 資料指標的物件 <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> 。</span><span class="sxs-lookup"><span data-stu-id="b1670-142">You can retrieve an <xref:System.Data.OracleClient.OracleDataReader> object that represents an Oracle REF CURSOR by using the <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> method.</span></span> <span data-ttu-id="b1670-143">您也可以指定 <xref:System.Data.OracleClient.OracleCommand> ，它會傳回一個或多個 ORACLE REF 資料**SelectCommand**指標做為 <xref:System.Data.OracleClient.OracleDataAdapter> 用來填滿之的 SelectCommand <xref:System.Data.DataSet> 。</span><span class="sxs-lookup"><span data-stu-id="b1670-143">You can also specify an <xref:System.Data.OracleClient.OracleCommand> that returns one or more Oracle REF CURSORs as the **SelectCommand** for an <xref:System.Data.OracleClient.OracleDataAdapter> used to fill a <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="b1670-144">若要存取從 Oracle 資料來源傳回的 REF CURSOR，請 <xref:System.Data.OracleClient.OracleCommand> 為您的查詢建立，並將參考參考游標的輸出參數加入至的 <xref:System.Data.OracleClient.OracleCommand.Parameters> 集合 <xref:System.Data.OracleClient.OracleCommand> 。</span><span class="sxs-lookup"><span data-stu-id="b1670-144">To access a REF CURSOR returned from an Oracle data source, create an <xref:System.Data.OracleClient.OracleCommand> for your query and add an output parameter that references the REF CURSOR to the <xref:System.Data.OracleClient.OracleCommand.Parameters> collection of your <xref:System.Data.OracleClient.OracleCommand>.</span></span> <span data-ttu-id="b1670-145">參數的名稱必須符合查詢中 REF CURSOR 參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="b1670-145">The name of the parameter must match the name of the REF CURSOR parameter in your query.</span></span> <span data-ttu-id="b1670-146">將參數的類型設定為 <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="b1670-146">Set the type of the parameter to <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b1670-147">的 <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> 方法會 <xref:System.Data.OracleClient.OracleCommand> <xref:System.Data.OracleClient.OracleDataReader> 針對 REF 資料指標傳回。</span><span class="sxs-lookup"><span data-stu-id="b1670-147">The <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> method of your <xref:System.Data.OracleClient.OracleCommand> returns an <xref:System.Data.OracleClient.OracleDataReader> for the REF CURSOR.</span></span>  
  
 <span data-ttu-id="b1670-148">如果您傳回 <xref:System.Data.OracleClient.OracleCommand> 多個 REF 資料指標，請加入多個輸出參數。</span><span class="sxs-lookup"><span data-stu-id="b1670-148">If your <xref:System.Data.OracleClient.OracleCommand> returns multiple REF CURSORS, add multiple output parameters.</span></span> <span data-ttu-id="b1670-149">您可以藉由呼叫方法來存取不同的 REF 資料指標 <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="b1670-149">You can access the different REF CURSORs by calling the <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b1670-150">對的呼叫會傳回 <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> <xref:System.Data.OracleClient.OracleDataReader> 參考第一個 REF 資料指標的。</span><span class="sxs-lookup"><span data-stu-id="b1670-150">The call to <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> returns an <xref:System.Data.OracleClient.OracleDataReader> referencing the first REF CURSOR.</span></span> <span data-ttu-id="b1670-151">接著，您可以呼叫 <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> 方法來存取後續的 REF 資料指標。</span><span class="sxs-lookup"><span data-stu-id="b1670-151">You can then call the <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> method to access subsequent REF CURSORs.</span></span> <span data-ttu-id="b1670-152">雖然集合中的參數 <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> 符合 REF CURSOR 輸出參數的名稱，但會依其 <xref:System.Data.OracleClient.OracleDataReader> 加入集合的順序來存取它們 <xref:System.Data.OracleClient.OracleCommand.Parameters> 。</span><span class="sxs-lookup"><span data-stu-id="b1670-152">Although the parameters in your <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> collection match the REF CURSOR output parameters by name, the <xref:System.Data.OracleClient.OracleDataReader> accesses them in the order in which they were added to the <xref:System.Data.OracleClient.OracleCommand.Parameters> collection.</span></span>  
  
 <span data-ttu-id="b1670-153">例如，請考慮下列的 Oracle Package 和 Package 內容。</span><span class="sxs-lookup"><span data-stu-id="b1670-153">For example, consider the following Oracle package and package body.</span></span>  
  
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
  
 <span data-ttu-id="b1670-154">下列程式碼會建立 <xref:System.Data.OracleClient.OracleCommand> ，它會將類型的兩個參數加入至集合，以傳回先前 Oracle 封裝的 REF 資料指標 <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="b1670-154">The following code creates an <xref:System.Data.OracleClient.OracleCommand> that returns the REF CURSORs from the previous Oracle package by adding two parameters of type <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> to the <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> collection.</span></span>  
  
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
  
 <span data-ttu-id="b1670-155">下列程式碼會使用的和方法，傳回上一個命令的結果 <xref:System.Data.OracleClient.OracleDataReader.Read> <xref:System.Data.OracleClient.OracleDataReader.NextResult> <xref:System.Data.OracleClient.OracleDataReader> 。</span><span class="sxs-lookup"><span data-stu-id="b1670-155">The following code returns the results of the previous command using the <xref:System.Data.OracleClient.OracleDataReader.Read> and <xref:System.Data.OracleClient.OracleDataReader.NextResult> methods of the <xref:System.Data.OracleClient.OracleDataReader>.</span></span> <span data-ttu-id="b1670-156">REF CURSOR 參數會依順序傳回。</span><span class="sxs-lookup"><span data-stu-id="b1670-156">The REF CURSOR parameters are returned in order.</span></span>  
  
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
  
 <span data-ttu-id="b1670-157">下列範例會使用先前的命令，將 <xref:System.Data.DataSet> Oracle 封裝的結果填入。</span><span class="sxs-lookup"><span data-stu-id="b1670-157">The following example uses the previous command to populate a <xref:System.Data.DataSet> with the results of the Oracle package.</span></span>  
  
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
> <span data-ttu-id="b1670-158">若要避免**OverflowException**，建議您同時處理從 Oracle NUMBER 類型到有效 .NET Framework 類型的任何轉換，然後再將值儲存在中 <xref:System.Data.DataRow> 。</span><span class="sxs-lookup"><span data-stu-id="b1670-158">To avoid an **OverflowException**, we recommend that you also handle any conversion from the Oracle NUMBER type to a valid .NET Framework type before storing the value in a <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="b1670-159">您可以使用 <xref:System.Data.Common.DataAdapter.FillError> 事件來判斷是否已發生**OverflowException** 。</span><span class="sxs-lookup"><span data-stu-id="b1670-159">You can use the <xref:System.Data.Common.DataAdapter.FillError> event to determine if an **OverflowException** has occurred.</span></span> <span data-ttu-id="b1670-160">如需事件的詳細資訊 <xref:System.Data.Common.DataAdapter.FillError> ，請參閱[處理 DataAdapter 事件](handling-dataadapter-events.md)。</span><span class="sxs-lookup"><span data-stu-id="b1670-160">For more information on the <xref:System.Data.Common.DataAdapter.FillError> event, see [Handling DataAdapter Events](handling-dataadapter-events.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1670-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1670-161">See also</span></span>

- [<span data-ttu-id="b1670-162">DataAdapter 和 DataReader</span><span class="sxs-lookup"><span data-stu-id="b1670-162">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="b1670-163">命令和參數</span><span class="sxs-lookup"><span data-stu-id="b1670-163">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="b1670-164">擷取資料庫結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="b1670-164">Retrieving Database Schema Information</span></span>](retrieving-database-schema-information.md)
- <span data-ttu-id="b1670-165">[ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="b1670-165">[ADO.NET Overview](ado-net-overview.md)</span></span>
