---
title: 使用 DataAdapter 更新資料來源
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d1bd9a8c-0e29-40e3-bda8-d89176b72fb1
ms.openlocfilehash: 8feffd5c3a6205dcb67072f8e17b0e771a0f0d6b
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53144737"
---
# <a name="updating-data-sources-with-dataadapters"></a>使用 DataAdapter 更新資料來源
呼叫 `Update` 的 <xref:System.Data.Common.DataAdapter> 方法，可將 <xref:System.Data.DataSet> 的變更解析回資料來源。 `Update` 方法類似 `Fill` 方法，會將 `DataSet` 的執行個體以及選擇性 (Optional) <xref:System.Data.DataTable> 物件或 `DataTable` 名稱做為引數。 `DataSet` 執行個體是包含已進行之變更的 `DataSet`，而 `DataTable` 則識別要從中擷取變更的資料表。 如果沒有指定任何 `DataTable`，就會使用 `DataTable` 中的第一個 `DataSet`。  
  
 當您呼叫 `Update` 方法時，`DataAdapter` 會分析已進行的變更，並執行適當的命令 (INSERT、UPDATE 或 DELETE)。 當 `DataAdapter` 發現 <xref:System.Data.DataRow> 的變更時，它會使用 <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>、<xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> 或 <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> 來處理變更。 如此可讓您於設計階段指定命令語法並盡量利用預存程序 (Stored Procedure)，發揮 ADO.NET 應用程式的最高效能。 您必須在呼叫 `Update` 之前明確地設定命令。 如果呼叫 `Update` 之後，特定更新沒有適當命令可用 (例如，刪除的資料列沒有 `DeleteCommand`)，便會擲回例外狀況 (Exception)。  
  
> [!NOTE]
>  如果您要使用 SQL Server 預存程序搭配 `DataAdapter` 來編輯或刪除資料，請務必不要在預存程序定義中使用 SET NOCOUNT ON。 因為這樣會讓傳回的受影響資料列計數成為零，而 `DataAdapter` 會將它解譯為並行衝突。 在此事件中，系統會擲回 <xref:System.Data.DBConcurrencyException>。  
  
 命令參數可用來針對 `DataSet` 內每個經過修改的資料列指定 SQL 陳述式或預存程序的輸入和輸出值。 如需詳細資訊，請參閱 < [DataAdapter 的參數](../../../../docs/framework/data/adonet/dataadapter-parameters.md)。  
  
> [!NOTE]
>  請務必瞭解刪除 <xref:System.Data.DataTable> 中的資料列與移除資料列之間的差異。 當您呼叫 `Remove` 或 `RemoveAt` 方法時，系統會立即移除資料列。 如果您之後傳遞 `DataTable` 或 `DataSet` 給 `DataAdapter` 並呼叫 `Update`，則後端 (Back End) 資料來源中的任何對應資料列將不會受到影響。 當您使用 `Delete` 方法時，資料列會保留在 `DataTable` 中並標示為待刪除。 如果您之後傳遞 `DataTable` 或 `DataSet` 給 `DataAdapter` 並呼叫 `Update`，系統就會刪除後端資料來源中的對應資料列。  
  
 如果您的 `DataTable` 對應至或產生自單一資料庫資料表，則可以利用 <xref:System.Data.Common.DbCommandBuilder> 物件來自動產生 `DeleteCommand`、`InsertCommand` 以及 `UpdateCommand` 的 `DataAdapter` 物件。 如需詳細資訊，請參閱 < [Commandbuilder 產生命令](../../../../docs/framework/data/adonet/generating-commands-with-commandbuilders.md)。  
  
## <a name="using-updatedrowsource-to-map-values-to-a-dataset"></a>使用 UpdatedRowSource 將值對應至 DataSet  
 在呼叫 `DataTable` 的 Update 方法之後，您可以使用 `DataAdapter` 物件的 <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> 屬性來控制從資料來源傳回的值要如何對應回 <xref:System.Data.Common.DbCommand>。 您可以透過將 `UpdatedRowSource` 屬性設為其中一個 <xref:System.Data.UpdateRowSource> 列舉值，控制要忽略 `DataAdapter` 命令所傳回的輸出參數，還是要將這些參數套用至 `DataSet` 中已變更的資料列。 您還能夠指定是否要將第一個傳回的資料列 (如果存在) 套用至 `DataTable` 中已變更的資料列。  
  
 下列表格說明 `UpdateRowSource` 列舉型別的各種值，以及這些值如何影響與 `DataAdapter` 搭配使用之命令的行為。  
  
|UpdatedRowSource 列舉型別|描述|  
|----------------------------------|-----------------|  
|<xref:System.Data.UpdateRowSource.Both>|輸出參數和傳回結果集的第一個資料列都會對應至 `DataSet` 中已變更的資料列。|  
|<xref:System.Data.UpdateRowSource.FirstReturnedRecord>|只有傳回結果集之第一個資料列內的資料會對應至 `DataSet` 中已變更的資料列。|  
|<xref:System.Data.UpdateRowSource.None>|將忽略任何輸出參數或傳回結果集的資料列。|  
|<xref:System.Data.UpdateRowSource.OutputParameters>|只有輸出參數會對應至 `DataSet` 中已變更的資料列。|  
  
 `Update` 方法會將您的變更解析回資料來源，但是自從您上次填入 `DataSet` 之後，其他用戶端可能也已經修改資料來源的資料。 若要以目前的資料重新整理 `DataSet`，請使用 `DataAdapter` 和 `Fill` 方法。 如此新資料列會加入資料表，而更新資訊也會合併入現有資料列。 `Fill` 方法會藉由檢查 `DataSet` 中資料列的主索引鍵值以及 `SelectCommand` 所傳回的資料列，決定要加入新資料列或更新現有資料列。 如果 `Fill` 方法發現 `DataSet` 中之資料列的主索引鍵值符合 `SelectCommand` 所傳回結果中之資料列的主索引鍵值，它就會以 `SelectCommand` 所傳回之資料列中的資訊更新現有資料列，並將現有資料列的 <xref:System.Data.DataRow.RowState%2A> 設為 `Unchanged`。 如果 `SelectCommand` 傳回之資料列的主索引鍵值與 `DataSet` 中資料列的任何主索引鍵值都不相符，`Fill` 方法就加入 `RowState` 設定為 `Unchanged` 的新資料列。  
  
> [!NOTE]
>  如果 `SelectCommand` 傳回 OUTER JOIN 的結果，`DataAdapter` 將不會為產生的 `PrimaryKey` 設定 `DataTable` 值。 您必須自己定義 `PrimaryKey`，確保正確解析重複的資料列。 如需詳細資訊，請參閱 <<c0> [ 定義主索引鍵](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md)。  
  
 若要處理呼叫時，可能會發生的例外狀況`Update`方法，您可以使用`RowUpdated`事件發生時，資料列更新錯誤回應 (請參閱[處理 DataAdapter 事件](../../../../docs/framework/data/adonet/handling-dataadapter-events.md))，或者您可以設定`DataAdapter.ContinueUpdateOnError`至`true`呼叫之前，先`Update`，並回應錯誤資訊儲存在`RowError`屬性的特定資料列更新完成時 (請參閱[資料列錯誤資訊](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md))。  
  
 **附註**呼叫`AcceptChanges`上`DataSet`， `DataTable`，或`DataRow`會導致所有`Original`值`DataRow`可以覆寫`Current`值`DataRow`。 如果識別資料列為唯一的欄位值已經被修改，則在呼叫 `AcceptChanges` 之後，`Original` 值就不會再與資料來源內的值相符。 此時，系統會在呼叫 `AcceptChanges` 的 Update 方法期間，自動針對每個資料列呼叫 `DataAdapter`。 您可以先將 `AcceptChangesDuringUpdate` 的 `DataAdapter` 屬性設定為 false，或針對 `RowUpdated` 事件建立事件處理常式並將 <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> 設定為 <xref:System.Data.UpdateStatus.SkipCurrentRow>，藉以在呼叫 Update 方法期間保留原始值。 如需詳細資訊，請參閱 <<c0> [ 合併的資料集內容](../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md)並[處理 DataAdapter 事件](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何藉由明確設定執行修改過的資料列更新`UpdateCommand`的`DataAdapter`，然後呼叫其`Update`方法。 請注意，在 UPDATE 陳述式之 WHERE 子句中指定的參數是設定為使用 `Original` 的 `SourceColumn` 值。 這一點相當重要，因為 `Current` 值可能已經修改，而不符合資料來源中的值。 `Original` 值是用來填入資料來源之 `DataTable` 的值。  
  
 [!code-csharp[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/VB/source.vb#1)]  
  
## <a name="autoincrement-columns"></a>AutoIncrement 資料行  
 如果來自資料來源的資料表具有自動遞增的資料行，您就可以將這些資料行填入 `DataSet` 中，方法包括：將自動遞增值當成預存程序的輸出參數傳回並將它對應至資料表的資料行、傳回結果集 (由預存程序或 SQL 陳述式所傳回) 之第一個資料列中的自動遞增值，或使用 `RowUpdated` 的 `DataAdapter` 事件來執行其他 SELECT 陳述式。 如需詳細資訊和範例，請參閱 <<c0> [ 擷取識別或自動編號值](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)。  
  
## <a name="ordering-of-inserts-updates-and-deletes"></a>插入、更新和刪除的順序  
 在許多情況下，以何種順序將透過 `DataSet` 所進行的變更傳送給資料來源是很重要的。 例如，如果更新了現有資料列的主索引鍵值，也加入了以新主索引鍵值當做外部索引鍵的資料列，則先進行更新再執行插入是很重要的。  
  
 您可以使用 `Select` 的 `DataTable` 方法來傳回僅參考具有特定 `DataRow` 之資料列的 `RowState` 陣列。 接著，您可以將傳回的 `DataRow` 陣列傳遞給 `Update` 的 `DataAdapter` 方法來處理已修改的資料列。 您可指定要更新的資料列子集，藉以控制插入、更新和刪除的處理順序。  
  
## <a name="example"></a>範例  
 例如，下列程式碼確保先處理資料表的已刪除資料列，接著處理已更新資料列，然後再處理已插入資料列。  
  
```vb  
Dim table As DataTable = dataSet.Tables("Customers")  
  
' First process deletes.  
dataSet.Update(table.Select(Nothing, Nothing, _  
  DataViewRowState.Deleted))  
  
' Next process updates.  
adapter.Update(table.Select(Nothing, Nothing, _  
  DataViewRowState.ModifiedCurrent))  
  
' Finally, process inserts.  
dataAdapater.Update(table.Select(Nothing, Nothing, _  
  DataViewRowState.Added))  
```  
  
```csharp  
DataTable table = dataSet.Tables["Customers"];  
  
// First process deletes.  
adapter.Update(table.Select(null, null, DataViewRowState.Deleted));  
  
// Next process updates.  
adapter.Update(table.Select(null, null,   
  DataViewRowState.ModifiedCurrent));  
  
// Finally, process inserts.  
adapter.Update(table.Select(null, null, DataViewRowState.Added));  
```  
  
## <a name="use-a-dataadapter-to-retrieve-and-update-data"></a>使用 DataAdapter 擷取和更新資料  
 您可以使用 DataAdapter 擷取和更新資料。  
  
-   範例會使用 DataAdapter.AcceptChangesDuringFill 複製資料庫中的資料。 如果屬性設為 false，填入資料表時就不會呼叫 AcceptChanges，並會將新加入的資料列視為插入的資料列。 因此，範例會使用這些資料列，將新資料列插入資料庫。  
  
-   範例會使用 DataAdapter.TableMappings 定義來源資料表和 DataTable 之間的對應。  
  
-   範例會使用 DataAdapter.FillLoadOption 決定配接器如何從 DbDataReader 填入 DataTable。 建立 DataTable 時，您可以將屬性設定為 LoadOption.Upsert 或 LoadOption.PreserveChanges，只將資料庫的資料寫入目前版本或原始版本。  
  
-   範例也會使用 DbDataAdapter.UpdateBatchSize，更新資料表以執行批次作業。  
  
 在編譯和執行範例之前，您必須建立範例資料庫：  
  
```sql
USE [master]  
GO  
  
CREATE DATABASE [MySchool]   
  
GO  
  
USE [MySchool]  
GO  
  
SET ANSI_NULLS ON  
GO  
SET QUOTED_IDENTIFIER ON  
GO  
CREATE TABLE [dbo].[Course]([CourseID] [nvarchar](10) NOT NULL,  
[Year] [smallint] NOT NULL,  
[Title] [nvarchar](100) NOT NULL,  
[Credits] [int] NOT NULL,  
[DepartmentID] [int] NOT NULL,  
 CONSTRAINT [PK_Course] PRIMARY KEY CLUSTERED  
(  
[CourseID] ASC,  
[Year] ASC  
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]  
  
GO  
  
SET ANSI_NULLS ON  
GO  
SET QUOTED_IDENTIFIER ON  
GO  
CREATE TABLE [dbo].[Department]([DepartmentID] [int] IDENTITY(1,1) NOT NULL,  
[Name] [nvarchar](50) NOT NULL,  
[Budget] [money] NOT NULL,  
[StartDate] [datetime] NOT NULL,  
[Administrator] [int] NULL,  
 CONSTRAINT [PK_Department] PRIMARY KEY CLUSTERED  
(  
[DepartmentID] ASC  
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]  
  
GO  
  
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C1045', 2012, N'Calculus', 4, 7)  
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C1061', 2012, N'Physics', 4, 1)  
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C2021', 2012, N'Composition', 3, 2)  
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C2042', 2012, N'Literature', 4, 2)  
  
SET IDENTITY_INSERT [dbo].[Department] ON   
  
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (1, N'Engineering', 350000.0000, CAST(0x0000999C00000000 AS DateTime), 2)  
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (2, N'English', 120000.0000, CAST(0x0000999C00000000 AS DateTime), 6)  
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (4, N'Economics', 200000.0000, CAST(0x0000999C00000000 AS DateTime), 4)  
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (7, N'Mathematics', 250024.0000, CAST(0x0000999C00000000 AS DateTime), 3)  
SET IDENTITY_INSERT [dbo].[Department] OFF  
  
ALTER TABLE [dbo].[Course]  WITH CHECK ADD  CONSTRAINT [FK_Course_Department] FOREIGN KEY([DepartmentID])  
REFERENCES [dbo].[Department] ([DepartmentID])  
GO  
ALTER TABLE [dbo].[Course] CHECK CONSTRAINT [FK_Course_Department]  
GO  
```  
  
 這個程式碼範例的 C# 和 Visual Basic 專案都位於[開發人員程式碼範例](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=How%20to%20use%20DataAdapter%20to%20retrieve%20and%20update%20data&f%5B1%5D)。  
  
```csharp
using System;  
using System.Data;  
using System.Data.Common;  
using System.Data.SqlClient;  
using System.Linq;  
using CSDataAdapterOperations.Properties;  
  
namespace CSDataAdapterOperations.Properties {  
   internal sealed partial class Settings : global::System.Configuration.ApplicationSettingsBase {  
  
      private static Settings defaultInstance = ((Settings)(global::System.Configuration.ApplicationSettingsBase.Synchronized(new Settings())));  
  
      public static Settings Default {  
         get {  
            return defaultInstance;  
         }  
      }  
  
      [global::System.Configuration.ApplicationScopedSettingAttribute()]  
      [global::System.Configuration.DefaultSettingValueAttribute("Data Source=(local);Initial Catalog=MySchool;Integrated Security=True")]  
      public string MySchoolConnectionString {  
         get {  
            return ((string)(this["MySchoolConnectionString"]));  
         }  
      }  
   }  
}  
  
class Program {  
   static void Main(string[] args) {  
      Settings settings = new Settings();  
  
      // Copy the data from the database.  Get the table Department and Course from the database.  
      String selectString = @"SELECT [DepartmentID],[Name],[Budget],[StartDate],[Administrator]  
                                     FROM [MySchool].[dbo].[Department];  
  
                                   SELECT [CourseID],@Year as [Year],Max([Title]) as [Title],  
                                   Max([Credits]) as [Credits],Max([DepartmentID]) as [DepartmentID]  
                                   FROM [MySchool].[dbo].[Course]  
                                   Group by [CourseID]";  
  
      DataSet mySchool = new DataSet();  
  
      SqlCommand selectCommand = new SqlCommand(selectString);  
      SqlParameter parameter = selectCommand.Parameters.Add("@Year", SqlDbType.SmallInt, 2);  
      parameter.Value = new Random(DateTime.Now.Millisecond).Next(9999);  
  
      // Use DataTableMapping to map the source tables and the destination tables.  
      DataTableMapping[] tableMappings = {new DataTableMapping("Table", "Department"), new DataTableMapping("Table1", "Course")};  
      CopyData(mySchool, settings.MySchoolConnectionString, selectCommand, tableMappings);  
  
      Console.WriteLine("The following tables are from the database.");  
      foreach (DataTable table in mySchool.Tables) {  
         Console.WriteLine(table.TableName);  
         ShowDataTable(table);  
      }  
  
      // Roll back the changes  
      DataTable department = mySchool.Tables["Department"];  
      DataTable course = mySchool.Tables["Course"];  
  
      department.Rows[0]["Name"] = "New" + department.Rows[0][1];  
      course.Rows[0]["Title"] = "New" + course.Rows[0]["Title"];  
      course.Rows[0]["Credits"] = 10;  
  
      Console.WriteLine("After we changed the tables:");  
      foreach (DataTable table in mySchool.Tables) {  
         Console.WriteLine(table.TableName);  
         ShowDataTable(table);  
      }  
  
      department.RejectChanges();  
      Console.WriteLine("After use the RejectChanges method in Department table to roll back the changes:");  
      ShowDataTable(department);  
  
      DataColumn[] primaryColumns = { course.Columns["CourseID"] };  
      DataColumn[] resetColumns = { course.Columns["Title"] };  
      ResetCourse(course, settings.MySchoolConnectionString, primaryColumns, resetColumns);  
      Console.WriteLine("After use the ResetCourse method in Course table to roll back the changes:");  
      ShowDataTable(course);  
  
      // Batch update the table.  
      String insertString = @"Insert into [MySchool].[dbo].[Course]([CourseID],[Year],[Title],   
                                   [Credits],[DepartmentID])   
             values (@CourseID,@Year,@Title,@Credits,@DepartmentID)";  
      SqlCommand insertCommand = new SqlCommand(insertString);  
      insertCommand.Parameters.Add("@CourseID", SqlDbType.NVarChar, 10, "CourseID");  
      insertCommand.Parameters.Add("@Year", SqlDbType.SmallInt, 2, "Year");  
      insertCommand.Parameters.Add("@Title", SqlDbType.NVarChar, 100, "Title");  
      insertCommand.Parameters.Add("@Credits", SqlDbType.Int, 4, "Credits");  
      insertCommand.Parameters.Add("@DepartmentID", SqlDbType.Int, 4, "DepartmentID");  
  
      const Int32 batchSize = 10;  
      BatchInsertUpdate(course, settings.MySchoolConnectionString, insertCommand, batchSize);  
   }  
  
   private static void CopyData(DataSet dataSet, String connectionString, SqlCommand selectCommand, DataTableMapping[] tableMappings) {  
      using (SqlConnection connection = new SqlConnection(connectionString)) {  
         selectCommand.Connection = connection;  
  
         connection.Open();  
  
         using (SqlDataAdapter adapter = new SqlDataAdapter(selectCommand)) {adapter.TableMappings.AddRange(tableMappings);  
            // If set the AcceptChangesDuringFill as the false, AcceptChanges will not be called on a   
            // DataRow after it is added to the DataTable during any of the Fill operations.  
            adapter.AcceptChangesDuringFill = false;  
  
            adapter.Fill(dataSet);  
         }  
      }  
   }  
  
   // Roll back only one column or several columns data of the Course table by call ResetDataTable method.  
   private static void ResetCourse(DataTable table, String connectionString,  
       DataColumn[] primaryColumns, DataColumn[] resetColumns) {  
      table.PrimaryKey = primaryColumns;  
  
      // Build the query string  
      String primaryCols = String.Join(",", primaryColumns.Select(col => col.ColumnName));  
      String resetCols = String.Join(",", resetColumns.Select(col => "Max(" + col.ColumnName + ") as " + col.ColumnName));  
  
      String selectString = String.Format("Select {0},{1} from Course Group by {0}", primaryCols, resetCols);  
  
      SqlCommand selectCommand = new SqlCommand(selectString);  
  
      ResetDataTable(table, connectionString, selectCommand);  
   }  
  
   // RejectChanges will roll back all changes made to the table since it was loaded, or the last time AcceptChanges   
   // was called. When you copy from the database, you can lose all the data after calling RejectChanges  
   // The ResetDataTable method rolls back one or more columns of data.  
   private static void ResetDataTable(DataTable table, String connectionString,  
       SqlCommand selectCommand) {  
      using (SqlConnection connection = new SqlConnection(connectionString)) {  
         selectCommand.Connection = connection;  
  
         connection.Open();  
  
         using (SqlDataAdapter adapter = new SqlDataAdapter(selectCommand)) {  
            // The incoming values for this row will be written to the current version of each   
            // column. The original version of each column's data will not be changed.  
            adapter.FillLoadOption = LoadOption.Upsert;  
  
            adapter.Fill(table);  
         }  
      }  
   }  
  
   private static void BatchInsertUpdate(DataTable table, String connectionString,  
       SqlCommand insertCommand, Int32 batchSize) {  
      using (SqlConnection connection = new SqlConnection(connectionString)) {  
         insertCommand.Connection = connection;  
         // When setting UpdateBatchSize to a value other than 1, all the commands   
         // associated with the SqlDataAdapter have to have their UpdatedRowSource   
         // property set to None or OutputParameters. An exception is thrown otherwise.  
         insertCommand.UpdatedRowSource = UpdateRowSource.None;  
  
         connection.Open();  
  
         using (SqlDataAdapter adapter = new SqlDataAdapter()) {  
            adapter.InsertCommand = insertCommand;  
            // Gets or sets the number of rows that are processed in each round-trip to the server.  
            // Setting it to 1 disables batch updates, as rows are sent one at a time.  
            adapter.UpdateBatchSize = batchSize;  
  
            adapter.Update(table);  
  
            Console.WriteLine("Successfully to update the table.");  
         }  
      }  
   }  
  
   private static void ShowDataTable(DataTable table) {  
      foreach (DataColumn col in table.Columns) {  
         Console.Write("{0,-14}", col.ColumnName);  
      }  
      Console.WriteLine("{0,-14}", "RowState");  
  
      foreach (DataRow row in table.Rows) {  
         foreach (DataColumn col in table.Columns) {  
            if (col.DataType.Equals(typeof(DateTime)))  
               Console.Write("{0,-14:d}", row[col]);  
            else if (col.DataType.Equals(typeof(Decimal)))  
               Console.Write("{0,-14:C}", row[col]);  
            else  
               Console.Write("{0,-14}", row[col]);  
         }  
         Console.WriteLine("{0,-14}", row.RowState);  
      }  
   }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [DataAdapter 和 DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [資料列狀態和資料列版本](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)  
 [AcceptChanges 和 RejectChanges](../../../../docs/framework/data/adonet/dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)  
 [合併 DataSet 內容](../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md)  
 [擷取身分識別或自動編號值](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
