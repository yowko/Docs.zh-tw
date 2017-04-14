---
title: "從 DataAdapter 填入資料集 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3fa0ac7d-e266-4954-bfac-3fbe2f913153
caps.latest.revision: 6
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 6
---
# 從 DataAdapter 填入資料集
[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] <xref:System.Data.DataSet> 是常駐記憶體的資料表示，可提供與資料來源無關的一致性關聯式程式設計模型。`DataSet` 表示一組完整的資料，包括資料表、條件約束和資料表間的關係。 因為 `DataSet` 與資料來源無關，所以 `DataSet` 可包含應用程式的本機資料，以及來自多個資料來源的資料。 而您與現有資料來源的互動則是透過 `DataAdapter`。  
  
 `SelectCommand` 的`DataAdapter` 屬性為 `Command` 物件，可用於從資料來源擷取資料。`InsertCommand` 的`UpdateCommand`、`DeleteCommand` 和 `DataAdapter` 屬性為 `Command` 物件，可根據對 `DataSet` 內資料的修改，管理對資料來源內資料的更新作業。 這些屬性的詳細內容皆涵蓋在 [以 DataAdapter 更新資料來源](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md) 中。  
  
 `Fill` 的 `DataAdapter` 方法用於以`DataSet` 之 `SelectCommand` 的結果填入`DataAdapter`。`Fill` 把下列各項當成引數：要填入的 `DataSet`、`DataTable` 物件，或是以 `DataTable` 傳回資料列填入的 `SelectCommand` 名稱。  
  
> [!NOTE]
>  使用 `DataAdapter` 擷取所有的資料表要花很多時間，特別是資料表包含許多資料列時。 這是因為存取資料庫，尋找和處理資料，然後再將資料傳輸至用戶端的過程非常耗時。 在將所有資料表提取到用戶端時，所有在伺服器上的資料列都會鎖定。 若要提升效能，您可以使用 `WHERE` 子句大幅減少傳回用戶端的資料列數目。 您也可以藉由在 `SELECT` 陳述式中明確列出所需的資料行，以減少傳回用戶端的資料數量。 另一個不錯的解決方法就是以批次方式擷取資料列 \(例如一次擷取數百個資料列\)，同時僅在用戶端完成目前的批次作業後，才擷取下一批次。  
  
 `Fill` 方法會隱含地使用 `DataReader` 物件傳回用於在 `DataSet` 內建立資料表的資料行名稱和型別，以及用於填入 `DataSet` 內資料表資料列的資料。 資料表和資料行只有在不存在時才會建立；否則 `Fill` 會使用現有的 `DataSet` 結構描述。 資料行類型會依照 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 中的資料表建立為 [ADO.NET 中的資料型別對應](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md) 類型。 除非主索引鍵已存在資料來源中而且 `DataAdapter`**.**`MissingSchemaAction` 設定為 `MissingSchemaAction`**.**`AddWithKey`，否則不會建立主索引鍵。 如果 `Fill` 發現主索引鍵已在資料表中，它就會以資料列 \(其主索引鍵的資料行值，符合從資料來源傳回的資料列對應值\) 的資料來源資料，覆寫 `DataSet` 中的資料。 如果沒發現主索引鍵，則資料會附加在 `DataSet` 的資料表內。 填入 `DataSet` 時，`Fill` 會使用任何可能存在的對應 \(請參閱 [DataAdapter DataTable 和 DataColumn 對應](../../../../docs/framework/data/adonet/dataadapter-datatable-and-datacolumn-mappings.md)\)。  
  
> [!NOTE]
>  如果 `SelectCommand` 傳回 OUTER JOIN 的結果，則 `DataAdapter` 便不會為產生的 `PrimaryKey` 設定 `DataTable` 值。 您必須自己定義 `PrimaryKey`，確保正確解析重複的資料列。 如需詳細資訊，請參閱[定義主索引鍵](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md)。  
  
 下列程式碼範例會建立 <xref:System.Data.SqlClient.SqlDataAdapter> 的執行個體，它使用 <xref:System.Data.SqlClient.SqlConnection> 連接至 Microsoft SQL Server `Northwind` 資料庫，並以客戶清單填入 <xref:System.Data.DataTable> 中的 `DataSet`。 SQL 陳述式和傳遞給 <xref:System.Data.SqlClient.SqlConnection> 建構函式的 <xref:System.Data.SqlClient.SqlDataAdapter> 引數，可用於建立 <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> 的 <xref:System.Data.SqlClient.SqlDataAdapter> 屬性。  
  
## 範例  
  
```vb  
' Assumes that connection is a valid SqlConnection object.  
Dim queryString As String = _  
  "SELECT CustomerID, CompanyName FROM dbo.Customers"  
Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
  queryString, connection)  
  
Dim customers As DataSet = New DataSet  
adapter.Fill(customers, "Customers")  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection object.  
string queryString =   
  "SELECT CustomerID, CompanyName FROM dbo.Customers";  
SqlDataAdapter adapter = new SqlDataAdapter(queryString, connection);  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");  
```  
  
> [!NOTE]
>  這個範例所顯示的程式碼並未明確開啟和關閉 `Connection`。`Fill` 方法若發現連接尚未開啟，會隱含開啟 `Connection` 正在使用的 `DataAdapter`。 如果 `Fill` 開啟了連接，則當 `Fill` 結束時也會一併關閉連接。 如此便可在處理單一作業時 \(例如 `Fill` 或 `Update`\)，簡化您的程式碼。 但是，如果您要執行需要開啟連接的多項作業，您可明確呼叫 `Open` 的`Connection` 方法，針對資料來源執行作業，然後呼叫 `Close` 的 `Connection` 方法，如此即可改善應用程式的效能。 您應該儘量減少與資料來源之間的連接，以釋放資源給其他用戶端應用程式使用。  
  
## 多個結果集  
 如果 `DataAdapter` 發現多個結果集，它便會在 `DataSet` 內建立多個資料表。 資料表會指定 Table*N* 的遞增預設名稱，從 "Table" 開始 \(Table0\)。 如果資料表名稱做為引數傳遞至 `Fill` 方法，則資料表會獲得開頭為 "TableName"，格式為 TableName*N* 的遞增預設名稱，例如 TableName0。  
  
## 從多重 DataAdapters 填入 DataSet  
 不論 `DataAdapter` 物件的數量多寡，都可以搭配 `DataSet` 使用。 每個 `DataAdapter` 都可以用以填滿一個或多個 `DataTable` 物件，並將更新解析回相關的資料來源。`DataRelation` 與 `Constraint` 物件可以新增至本機的 `DataSet`，這可讓您將來自不同資料來源的資料關聯。 例如，`DataSet` 包含的資料可來自 Microsoft SQL Server 資料庫、透過 OLE DB 公開的 IBM DB2 資料庫和產生 XML 資料流的資料來源。 與每個資料來源的通訊可以由一個或多個 `DataAdapter` 物件處理。  
  
### 範例  
 下列程式碼範例從 Microsoft SQL Server 上的 `Northwind` 資料庫填入客戶清單，並從存放在 Microsoft Access 2000 的 `Northwind` 資料庫填入訂貨清單。 填入的資料表和 `DataRelation` 有關，之後客戶清單便會顯示該客戶的訂貨。 如需 `DataRelation` 物件的詳細資訊，請參閱 [加入 DataRelations](../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md) 和 [瀏覽 DataRelation](../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations.md)。  
  
```vb  
' Assumes that customerConnection is a valid SqlConnection object.  
' Assumes that orderConnection is a valid OleDbConnection object.  
Dim custAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM dbo.Customers", customerConnection)  
  
Dim ordAdapter As OleDbDataAdapter = New OleDbDataAdapter( _  
  "SELECT * FROM Orders", orderConnection)  
  
Dim customerOrders As DataSet = New DataSet()  
custAdapter.Fill(customerOrders, "Customers")  
ordAdapter.Fill(customerOrders, "Orders")  
  
Dim relation As DataRelation = _  
  customerOrders.Relations.Add("CustOrders", _  
  customerOrders.Tables("Customers").Columns("CustomerID"), _   
  customerOrders.Tables("Orders").Columns("CustomerID"))  
  
Dim pRow, cRow As DataRow  
For Each pRow In customerOrders.Tables("Customers").Rows  
  Console.WriteLine(pRow("CustomerID").ToString())  
  
  For Each cRow In pRow.GetChildRows(relation)  
    Console.WriteLine(vbTab & cRow("OrderID").ToString())  
  Next  
Next  
  
```  
  
```csharp  
// Assumes that customerConnection is a valid SqlConnection object.  
// Assumes that orderConnection is a valid OleDbConnection object.  
SqlDataAdapter custAdapter = new SqlDataAdapter(  
  "SELECT * FROM dbo.Customers", customerConnection);  
OleDbDataAdapter ordAdapter = new OleDbDataAdapter(  
  "SELECT * FROM Orders", orderConnection);  
  
DataSet customerOrders = new DataSet();  
  
custAdapter.Fill(customerOrders, "Customers");  
ordAdapter.Fill(customerOrders, "Orders");  
  
DataRelation relation = customerOrders.Relations.Add("CustOrders",  
  customerOrders.Tables["Customers"].Columns["CustomerID"],  
  customerOrders.Tables["Orders"].Columns["CustomerID"]);  
  
foreach (DataRow pRow in customerOrders.Tables["Customers"].Rows)  
{  
  Console.WriteLine(pRow["CustomerID"]);  
   foreach (DataRow cRow in pRow.GetChildRows(relation))  
    Console.WriteLine("\t" + cRow["OrderID"]);  
}  
```  
  
## SQL Server Decimal 型別  
 依預設，`DataSet` 會使用 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 資料型別儲存資料。 對大部分的應用程式而言，這些型別可便於表示資料來源資訊， 但是當資料來源中的資料型別為 SQL Server decimal 或 numeric 資料型別時，這種表示可能會造成問題。[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]`decimal` 資料型別最多允許 28 位有效位數，而 SQL Server `decimal` 資料型別則允許 38 位有效位數。 在 `SqlDataAdapter` 作業期間，如果 `Fill` 判斷 SQL Server `decimal` 欄位的精確度超過 28 個字元，則目前的資料列便不會加入 `DataTable`。 反而會發生 `FillError` 事件，讓您判斷是否會失去精確度，並做出適當回應。 如需 `FillError` 事件的詳細資訊，請參閱[處理 DataAdapter 事件](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)。 若要取得 SQL Server `decimal` 值，您也可以使用 <xref:System.Data.SqlClient.SqlDataReader> 物件並呼叫 <xref:System.Data.SqlClient.SqlDataReader.GetSqlDecimal%2A> 方法。  
  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0 導入了對於 <xref:System.Data.SqlTypes> 中 `DataSet` 的支援。 如需詳細資訊，請參閱[SqlType 和 DataSet](../../../../docs/framework/data/adonet/sql/sqltypes-and-the-dataset.md)。  
  
## OLE DB 章節  
 您可以使用階層式資料列集 \(Rowset\)，或稱章節 \(OLE DB 型別 `DBTYPE_HCHAPTER`、ADO 型別 `adChapter`\) 來填入 `DataSet` 的內容。 若在 <xref:System.Data.OleDb.OleDbDataAdapter> 作業期間，`Fill` 遇到已章節化的資料行，則會針對該章節化的資料行建立 `DataTable`，且該資料表會填入來自章節的資料行和資料列。 為章節化資料行所建立的資料表會以 "*ParentTableNameChapteredColumnName*" 的形式，取用父資料表名稱和章節化資料行名稱來命名。 如果 `DataSet` 中已有資料表，且與章節化資料行的名稱相符，則目前的資料表內會填入章節資料。 如果現有資料表內沒有資料行符合章節內找到的資料行，則會加入新資料行。  
  
 在 `DataSet` 內的資料表中填入章節化資料行的資料前，會在階層式資料列集的父子資料表間建立關聯，方法是在父子資料表兩方均加入整數資料行，將父資料行設為自動遞增，然後使用加入自兩個資料表的資料行建立 `DataRelation`。 加入的關聯以 "*ParentTableNameChapterColumnName*" 形式，使用父資料表和章節化資料行的名稱來命名。  
  
 請注意，關聯資料行僅存在於 `DataSet`。 來自資料來源的後續填入會造成資料表中加入新資料列，而非將變更合併至現有資料列。  
  
 另外要注意的是，如果您使用的 `DataAdapter.Fill` 多載採用  `DataTable`，則只有該資料表會填入。 自動遞增的整數資料行仍會加入資料表，但不會建立或填入子資料表，也不會建立關聯。  
  
 下列範例使用 MSDataShape 提供者產生客戶清單中，每位客戶訂單的章節資料行。 接著便在 `DataSet` 內填入資料。  
  
```vb  
Using connection As OleDbConnection = New OleDbConnection( _  
  "Provider=MSDataShape;Data Provider=SQLOLEDB;" & _  
  "Data Source=(local);Integrated " & _  
  "Security=SSPI;Initial Catalog=northwind")  
  
Dim adapter As OleDbDataAdapter = New OleDbDataAdapter( _  
  "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " & _  
  "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS Orders " & _  
  "RELATE CustomerID TO CustomerID)", connection)  
  
Dim customers As DataSet = New DataSet()  
  
adapter.Fill(customers, "Customers")  
End Using  
```  
  
```csharp  
using (OleDbConnection connection = new OleDbConnection("Provider=MSDataShape;Data Provider=SQLOLEDB;" +  
  "Data Source=(local);Integrated Security=SSPI;Initial Catalog=northwind"))  
{  
OleDbDataAdapter adapter = new OleDbDataAdapter("SHAPE {SELECT CustomerID, CompanyName FROM Customers} " +  
  "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS Orders " +  
  "RELATE CustomerID TO CustomerID)", connection);  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");  
}  
```  
  
 `Fill` 作業完畢後，`DataSet` 會包含兩個資料表：`Customers` 和 `CustomersOrders`，其中 `CustomersOrders` 表示章節化的資料行。 接下來，另一個名為 `Orders` 的資料行會加入 `Customers` 資料表，而另一個名為 `CustomersOrders` 的資料行會加入 `CustomersOrders` 資料表。`Orders` 資料表內的 `Customers` 資料行設為自動遞增。 接著會使用加入資料表的資料行 \(將 `DataRelation` 當做父資料表\)，建立`CustomersOrders` \(`Customers`\)。 下表顯示一些範例結果。  
  
### TableName：Customers  
  
|CustomerID|CompanyName|Orders|  
|----------------|-----------------|------------|  
|ALFKI|Alfreds Futterkiste|0|  
|ANATR|Ana Trujillo Emparedados y helados|1|  
  
### TableName：CustomersOrders  
  
|CustomerID|OrderID|CustomersOrders|  
|----------------|-------------|---------------------|  
|ALFKI|10643|0|  
|ALFKI|10692|0|  
|ANATR|10308|1|  
|ANATR|10625|1|  
  
## 請參閱  
 [DataAdapter 和 DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)   
 [ADO.NET 中的資料型別對應](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)   
 [使用 DbDataAdapter 來修改資料](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)   
 [Multiple Active Result Set \(MARS\)](../../../../docs/framework/data/adonet/sql/multiple-active-result-sets-mars.md)   
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)