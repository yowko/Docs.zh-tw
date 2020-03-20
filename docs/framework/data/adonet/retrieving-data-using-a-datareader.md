---
title: 使用 DataReader 擷取資料
ms.date: 10/29/2018
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.openlocfilehash: 88cd85ce343aaab08b944f81c9659918014da0a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149020"
---
# <a name="retrieve-data-using-a-datareader"></a><span data-ttu-id="b68d3-102">使用資料讀取器檢索資料</span><span class="sxs-lookup"><span data-stu-id="b68d3-102">Retrieve data using a DataReader</span></span>
<span data-ttu-id="b68d3-103">若要使用**DataReader**檢索資料，請創建**命令**物件的實例，然後通過調用**Command.ExecuteReader**從資料來源檢索行來創建**DataReader。**</span><span class="sxs-lookup"><span data-stu-id="b68d3-103">To retrieve data using a **DataReader**, create an instance of the **Command** object, and then create a **DataReader** by calling **Command.ExecuteReader** to retrieve rows from a data source.</span></span> <span data-ttu-id="b68d3-104">**DataReader**提供了一個未緩衝的資料流程，允許過程邏輯按順序有效地處理資料來源的結果。</span><span class="sxs-lookup"><span data-stu-id="b68d3-104">The **DataReader** provides an unbuffered stream of data that allows procedural logic to efficiently process results from a data source sequentially.</span></span> <span data-ttu-id="b68d3-105">當您檢索大量資料時 **，DataReader**是一個不錯的選擇，因為資料未緩存在記憶體中。</span><span class="sxs-lookup"><span data-stu-id="b68d3-105">The **DataReader** is a good choice when you're retrieving large amounts of data because the data is not cached in memory.</span></span>

<span data-ttu-id="b68d3-106">下面的示例演示了使用**DataReader**，`reader`其中表示有效的 DataReader`command`並表示有效的命令物件。</span><span class="sxs-lookup"><span data-stu-id="b68d3-106">The following example illustrates using a **DataReader**, where `reader` represents a valid DataReader and `command` represents a valid Command object.</span></span>  

```csharp
reader = command.ExecuteReader();  
```

```vb
reader = command.ExecuteReader()
```  

<span data-ttu-id="b68d3-107">使用**DataReader.Read**方法從查詢結果中獲取行。</span><span class="sxs-lookup"><span data-stu-id="b68d3-107">Use the **DataReader.Read** method to obtain a row from the query results.</span></span> <span data-ttu-id="b68d3-108">通過將列的名稱或單位編號傳遞給**DataReader，** 可以訪問返回行的每個列。</span><span class="sxs-lookup"><span data-stu-id="b68d3-108">You can access each column of the returned row by passing the name or ordinal number of the column to the **DataReader**.</span></span> <span data-ttu-id="b68d3-109">但是，為了獲得最佳性能 **，DataReader**提供了一系列方法，允許您訪問其本機資料類型中的列值（GetDateTime、GetDouble、GetGuid、GetInt32 等）。\*\* \*\* **GetDouble** **GetGuid** **GetInt32**</span><span class="sxs-lookup"><span data-stu-id="b68d3-109">However, for best performance, the **DataReader** provides a series of methods that allow you to access column values in their native data types (**GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**, and so on).</span></span> <span data-ttu-id="b68d3-110">有關特定于資料提供程式**的資料閱讀器**的鍵入訪問器方法的清單，請參閱<xref:System.Data.OleDb.OleDbDataReader>和<xref:System.Data.SqlClient.SqlDataReader>。</span><span class="sxs-lookup"><span data-stu-id="b68d3-110">For a list of typed accessor methods for data provider-specific **DataReaders**, see <xref:System.Data.OleDb.OleDbDataReader> and <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="b68d3-111">當您知道基礎資料類型時，使用鍵入的訪問器方法可減少檢索列值時所需的類型轉換量。</span><span class="sxs-lookup"><span data-stu-id="b68d3-111">Using the typed accessor methods when you know the underlying data type reduces the amount of type conversion required when retrieving the column value.</span></span>  
  
 <span data-ttu-id="b68d3-112">以下示例通過**DataReader**物件進行遍讀，並從每行返回兩列。</span><span class="sxs-lookup"><span data-stu-id="b68d3-112">The following example iterates through a **DataReader** object and returns two columns from each row.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
## <a name="closing-the-datareader"></a><span data-ttu-id="b68d3-113">關閉 DataReader</span><span class="sxs-lookup"><span data-stu-id="b68d3-113">Closing the DataReader</span></span>  
 <span data-ttu-id="b68d3-114">使用完**DataReader**物件後，始終調用**Close**方法。</span><span class="sxs-lookup"><span data-stu-id="b68d3-114">Always call the **Close** method when you have finished using the **DataReader** object.</span></span>  
  
 <span data-ttu-id="b68d3-115">如果**命令**包含輸出參數或傳回值，則在**關閉 DataReader**之前，這些值不可用。</span><span class="sxs-lookup"><span data-stu-id="b68d3-115">If your **Command** contains output parameters or return values, those values are not available until the **DataReader** is closed.</span></span>  
  
 <span data-ttu-id="b68d3-116">當**資料閱讀器**處於打開狀態時，**該連接**僅由該**資料閱讀器**使用。</span><span class="sxs-lookup"><span data-stu-id="b68d3-116">While a **DataReader** is open, the **Connection** is in use exclusively by that **DataReader**.</span></span> <span data-ttu-id="b68d3-117">在關閉原始**資料閱讀器**之前，您不能執行**連接**的任何命令，包括創建另一個**DataReader。**</span><span class="sxs-lookup"><span data-stu-id="b68d3-117">You cannot execute any commands for the **Connection**, including creating another **DataReader**, until the original **DataReader** is closed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b68d3-118">不要調用**連接\*\*\*\*、DataReader**或**Connection**類**的 Finalize**方法中的任何其他託管**物件。**</span><span class="sxs-lookup"><span data-stu-id="b68d3-118">Do not call **Close** or **Dispose** on a **Connection**, a **DataReader**, or any other managed object in the **Finalize** method of your class.</span></span> <span data-ttu-id="b68d3-119">在完成項中，只需釋放類別直接擁有的 Unmanaged 資源。</span><span class="sxs-lookup"><span data-stu-id="b68d3-119">In a finalizer, only release unmanaged resources that your class owns directly.</span></span> <span data-ttu-id="b68d3-120">如果類不擁有任何非託管資源，請不要在類定義中包括**Finalize**方法。</span><span class="sxs-lookup"><span data-stu-id="b68d3-120">If your class does not own any unmanaged resources, do not include a **Finalize** method in your class definition.</span></span> <span data-ttu-id="b68d3-121">有關詳細資訊，請參閱[垃圾回收](../../../standard/garbage-collection/index.md)。</span><span class="sxs-lookup"><span data-stu-id="b68d3-121">For more information, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a><span data-ttu-id="b68d3-122">使用 NextResult 檢索多個結果集</span><span class="sxs-lookup"><span data-stu-id="b68d3-122">Retrieving multiple result sets using NextResult</span></span>  
 <span data-ttu-id="b68d3-123">如果**DataReader**返回多個結果集，請調用**NextResult**方法以按順序遍讀結果集。</span><span class="sxs-lookup"><span data-stu-id="b68d3-123">If the **DataReader** returns multiple result sets, call the **NextResult** method to iterate through the result sets sequentially.</span></span> <span data-ttu-id="b68d3-124">下列範例顯示 <xref:System.Data.SqlClient.SqlDataReader> 使用 <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> 方法，處理兩個 SELECT 陳述式的結果。</span><span class="sxs-lookup"><span data-stu-id="b68d3-124">The following example shows the <xref:System.Data.SqlClient.SqlDataReader> processing the results of two SELECT statements using the <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> method.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a><span data-ttu-id="b68d3-125">從資料閱讀器獲取架構資訊</span><span class="sxs-lookup"><span data-stu-id="b68d3-125">Getting schema information from the DataReader</span></span>  
 <span data-ttu-id="b68d3-126">打開**DataReader**時，可以使用**GetSchemaTable**方法檢索有關當前結果集的架構資訊。</span><span class="sxs-lookup"><span data-stu-id="b68d3-126">While a **DataReader** is open, you can retrieve schema information about the current result set using the **GetSchemaTable** method.</span></span> <span data-ttu-id="b68d3-127">**GetSchemaTable**返回<xref:System.Data.DataTable>一個包含當前結果集的架構資訊的行和列填充的物件。</span><span class="sxs-lookup"><span data-stu-id="b68d3-127">**GetSchemaTable** returns a <xref:System.Data.DataTable> object populated with rows and columns that contain the schema information for the current result set.</span></span> <span data-ttu-id="b68d3-128">**資料表**包含結果集每一列的一行。</span><span class="sxs-lookup"><span data-stu-id="b68d3-128">The **DataTable** contains one row for each column of the result set.</span></span> <span data-ttu-id="b68d3-129">架構表的每一列映射到結果集行中返回的列的屬性，其中 **"列名稱**"是屬性的名稱，列的值是屬性的值。</span><span class="sxs-lookup"><span data-stu-id="b68d3-129">Each column of the schema table maps to a property of the columns returned in the rows of the result set, where the **ColumnName** is the name of the property and the value of the column is the value of the property.</span></span> <span data-ttu-id="b68d3-130">下面的示例為**DataReader**編寫架構資訊。</span><span class="sxs-lookup"><span data-stu-id="b68d3-130">The following example writes out the schema information for **DataReader**.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a><span data-ttu-id="b68d3-131">使用 OLE DB 章節</span><span class="sxs-lookup"><span data-stu-id="b68d3-131">Working with OLE DB chapters</span></span>  
 <span data-ttu-id="b68d3-132">可以使用 檢索<xref:System.Data.OleDb.OleDbDataReader>層次結構行集或章節（OLE DB 類型**DBTYPE_HCHAPTER**ADO 類型**廣告章節**）。</span><span class="sxs-lookup"><span data-stu-id="b68d3-132">Hierarchical rowsets, or chapters (OLE DB type **DBTYPE_HCHAPTER**, ADO type **adChapter**), can be retrieved using the <xref:System.Data.OleDb.OleDbDataReader>.</span></span> <span data-ttu-id="b68d3-133">當包含章節的查詢作為**DataReader**返回時，該章將作為該**資料閱讀器**中的列返回，並作為**DataReader**物件公開。</span><span class="sxs-lookup"><span data-stu-id="b68d3-133">When a query that includes a chapter is returned as a **DataReader**, the chapter is returned as a column in that **DataReader** and is exposed as a **DataReader** object.</span></span>  
  
 <span data-ttu-id="b68d3-134">**DataSetADO.NET**也可用於使用表之間的父子關係來表示分層行集。</span><span class="sxs-lookup"><span data-stu-id="b68d3-134">The ADO.NET **DataSet** can also be used to represent hierarchical rowsets by using parent-child relationships between tables.</span></span> <span data-ttu-id="b68d3-135">有關詳細資訊，請參閱[資料集、資料表和資料檢視](./dataset-datatable-dataview/index.md)。</span><span class="sxs-lookup"><span data-stu-id="b68d3-135">For more information, see [DataSets, DataTables, and DataViews](./dataset-datatable-dataview/index.md).</span></span>  
  
 <span data-ttu-id="b68d3-136">下列程式碼範例使用 MSDataShape 提供者，替客戶清單中每位客戶的訂單產生章節資料行。</span><span class="sxs-lookup"><span data-stu-id="b68d3-136">The following code example uses the MSDataShape Provider to generate a chapter column of orders for each customer in a list of customers.</span></span>  
  
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
  
## <a name="returning-results-with-oracle-ref-cursors"></a><span data-ttu-id="b68d3-137">使用 Oracle REF CURSORs 返回結果</span><span class="sxs-lookup"><span data-stu-id="b68d3-137">Returning results with Oracle REF CURSORs</span></span>  
 <span data-ttu-id="b68d3-138">Oracle 的 .NET Framework 資料提供者支援使用 Oracle REF CURSOR 傳回查詢結果。</span><span class="sxs-lookup"><span data-stu-id="b68d3-138">The .NET Framework Data Provider for Oracle supports the use of Oracle REF CURSORs to return a query result.</span></span> <span data-ttu-id="b68d3-139">Oracle REF CURSOR 以 <xref:System.Data.OracleClient.OracleDataReader> 傳回。</span><span class="sxs-lookup"><span data-stu-id="b68d3-139">An Oracle REF CURSOR is returned as an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 <span data-ttu-id="b68d3-140">可以使用<xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>方法檢索<xref:System.Data.OracleClient.OracleDataReader>表示 Oracle REF CURSOR 的物件。</span><span class="sxs-lookup"><span data-stu-id="b68d3-140">You can retrieve an <xref:System.Data.OracleClient.OracleDataReader> object that represents an Oracle REF CURSOR by using the <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> method.</span></span> <span data-ttu-id="b68d3-141">還可以指定 返回<xref:System.Data.OracleClient.OracleCommand>一個或多個 Oracle REF CURSOR 作為<xref:System.Data.OracleClient.OracleDataAdapter>用於填充 的<xref:System.Data.DataSet>**SelectCommand 的 指定命令**。</span><span class="sxs-lookup"><span data-stu-id="b68d3-141">You can also specify an <xref:System.Data.OracleClient.OracleCommand> that returns one or more Oracle REF CURSORs as the **SelectCommand** for an <xref:System.Data.OracleClient.OracleDataAdapter> used to fill a <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="b68d3-142">要訪問從 Oracle 資料來源返回的 REF CURSOR，<xref:System.Data.OracleClient.OracleCommand>請為查詢創建 一個，並添加一個輸出參數，<xref:System.Data.OracleClient.OracleCommand.Parameters>將 REF <xref:System.Data.OracleClient.OracleCommand>CURSOR 引用到 集合中。</span><span class="sxs-lookup"><span data-stu-id="b68d3-142">To access a REF CURSOR returned from an Oracle data source, create an <xref:System.Data.OracleClient.OracleCommand> for your query and add an output parameter that references the REF CURSOR to the <xref:System.Data.OracleClient.OracleCommand.Parameters> collection of your <xref:System.Data.OracleClient.OracleCommand>.</span></span> <span data-ttu-id="b68d3-143">參數的名稱必須符合查詢中 REF CURSOR 參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="b68d3-143">The name of the parameter must match the name of the REF CURSOR parameter in your query.</span></span> <span data-ttu-id="b68d3-144">將參數的類型設置為<xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="b68d3-144">Set the type of the parameter to <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b68d3-145"><xref:System.Data.OracleClient.OracleCommand>方法<xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType><xref:System.Data.OracleClient.OracleDataReader>返回 REF CURSOR 的</span><span class="sxs-lookup"><span data-stu-id="b68d3-145">The <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> method of your <xref:System.Data.OracleClient.OracleCommand> returns an <xref:System.Data.OracleClient.OracleDataReader> for the REF CURSOR.</span></span>  
  
 <span data-ttu-id="b68d3-146">如果<xref:System.Data.OracleClient.OracleCommand>返回多個 REF CURSORS，請添加多個輸出參數。</span><span class="sxs-lookup"><span data-stu-id="b68d3-146">If your <xref:System.Data.OracleClient.OracleCommand> returns multiple REF CURSORS, add multiple output parameters.</span></span> <span data-ttu-id="b68d3-147">您可以通過調用<xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType>方法訪問不同的 REF CURSOR。</span><span class="sxs-lookup"><span data-stu-id="b68d3-147">You can access the different REF CURSORs by calling the <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b68d3-148">調用 返回<xref:System.Data.OracleClient.OracleCommand.ExecuteReader>引用第<xref:System.Data.OracleClient.OracleDataReader>一個 REF CURSOR。</span><span class="sxs-lookup"><span data-stu-id="b68d3-148">The call to <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> returns an <xref:System.Data.OracleClient.OracleDataReader> referencing the first REF CURSOR.</span></span> <span data-ttu-id="b68d3-149">然後，<xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType>您可以調用 方法以訪問後續的 REF CURSOR。</span><span class="sxs-lookup"><span data-stu-id="b68d3-149">You can then call the <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> method to access subsequent REF CURSORs.</span></span> <span data-ttu-id="b68d3-150">儘管<xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType>集合中的參數按名稱與 REF CURSOR 輸出參數匹配，但<xref:System.Data.OracleClient.OracleDataReader>訪問參數的順序是添加到集合中<xref:System.Data.OracleClient.OracleCommand.Parameters>的順序。</span><span class="sxs-lookup"><span data-stu-id="b68d3-150">Although the parameters in your <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> collection match the REF CURSOR output parameters by name, the <xref:System.Data.OracleClient.OracleDataReader> accesses them in the order in which they were added to the <xref:System.Data.OracleClient.OracleCommand.Parameters> collection.</span></span>  
  
 <span data-ttu-id="b68d3-151">例如，請考慮下列的 Oracle Package 和 Package 內容。</span><span class="sxs-lookup"><span data-stu-id="b68d3-151">For example, consider the following Oracle package and package body.</span></span>  
  
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
  
 <span data-ttu-id="b68d3-152">以下代碼創建 一<xref:System.Data.OracleClient.OracleCommand>個，通過向<xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType><xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType>集合添加兩個類型的參數來返回上一個 Oracle 包中的 REF CURSOR。</span><span class="sxs-lookup"><span data-stu-id="b68d3-152">The following code creates an <xref:System.Data.OracleClient.OracleCommand> that returns the REF CURSORs from the previous Oracle package by adding two parameters of type <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> to the <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> collection.</span></span>  
  
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
  
 <span data-ttu-id="b68d3-153">以下代碼使用 的<xref:System.Data.OracleClient.OracleDataReader.Read>和<xref:System.Data.OracleClient.OracleDataReader.NextResult>返回上一個命令的結果。 <xref:System.Data.OracleClient.OracleDataReader></span><span class="sxs-lookup"><span data-stu-id="b68d3-153">The following code returns the results of the previous command using the <xref:System.Data.OracleClient.OracleDataReader.Read> and <xref:System.Data.OracleClient.OracleDataReader.NextResult> methods of the <xref:System.Data.OracleClient.OracleDataReader>.</span></span> <span data-ttu-id="b68d3-154">REF CURSOR 參數會依順序傳回。</span><span class="sxs-lookup"><span data-stu-id="b68d3-154">The REF CURSOR parameters are returned in order.</span></span>  
  
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
  
 <span data-ttu-id="b68d3-155">下面的示例使用前面的命令用 Oracle 包<xref:System.Data.DataSet>的結果填充 。</span><span class="sxs-lookup"><span data-stu-id="b68d3-155">The following example uses the previous command to populate a <xref:System.Data.DataSet> with the results of the Oracle package.</span></span>  
  
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
> <span data-ttu-id="b68d3-156">為了避免**溢出異常**，我們建議您在將值存儲在 中之前，還要處理從 Oracle NUMBER 類型到有效的 .NET 框架類型的任何轉換<xref:System.Data.DataRow>。</span><span class="sxs-lookup"><span data-stu-id="b68d3-156">To avoid an **OverflowException**, we recommend that you also handle any conversion from the Oracle NUMBER type to a valid .NET Framework type before storing the value in a <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="b68d3-157">您可以使用該<xref:System.Data.Common.DataAdapter.FillError>事件來確定是否發生了**溢出異常**。</span><span class="sxs-lookup"><span data-stu-id="b68d3-157">You can use the <xref:System.Data.Common.DataAdapter.FillError> event to determine if an **OverflowException** has occurred.</span></span> <span data-ttu-id="b68d3-158">有關事件的詳細資訊，<xref:System.Data.Common.DataAdapter.FillError>請參閱[處理資料配接器事件](handling-dataadapter-events.md)。</span><span class="sxs-lookup"><span data-stu-id="b68d3-158">For more information on the <xref:System.Data.Common.DataAdapter.FillError> event, see [Handling DataAdapter Events](handling-dataadapter-events.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b68d3-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b68d3-159">See also</span></span>

- [<span data-ttu-id="b68d3-160">DataAdapter 和 DataReader</span><span class="sxs-lookup"><span data-stu-id="b68d3-160">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="b68d3-161">命令和參數</span><span class="sxs-lookup"><span data-stu-id="b68d3-161">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="b68d3-162">擷取資料庫結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="b68d3-162">Retrieving Database Schema Information</span></span>](retrieving-database-schema-information.md)
- <span data-ttu-id="b68d3-163">[ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="b68d3-163">[ADO.NET Overview](ado-net-overview.md)</span></span>
