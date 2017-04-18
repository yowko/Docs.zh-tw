---
title: "擷取 Identity 或 Autonumber 值 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d6b7f9cb-81be-44e1-bb94-56137954876d
caps.latest.revision: 7
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 7
---
# 擷取 Identity 或 Autonumber 值
關聯式資料庫中的主索引鍵是永遠包含唯一值的資料行或資料行組合。  瞭解主索引鍵值可讓您找出包含此值的資料列。  關聯式 Database Engine \(例如 SQL Server、Oracle 和 Microsoft Access\/Jet\) 支援建立可指定為主索引鍵的自動遞增資料行。  上述的值會在資料列加入至資料表時由伺服器產生。  在 SQL Server 中，您可以設定資料行的識別屬性。在 Oracle 中，您可以建立序列 \(Sequence\)。在 Microsoft Access 中，您可以建立 AutoNumber 資料行。  
  
 您也可以將 <xref:System.Data.DataColumn.AutoIncrement%2A> 屬性設定為 true，讓 <xref:System.Data.DataColumn> 用來產生自動遞增的值。  不過，如果多個用戶端應用程式都獨立產生自動遞增的值，您可能會造成 <xref:System.Data.DataTable> 的個別執行個體 \(Instance\) 具有重複的值。  如果讓伺服器產生自動遞增的值，就能排除因允許每位使用者針對每個插入的資料列自行擷取產生的值所可能發生的衝突。  
  
 在呼叫 `DataAdapter` 的 `Update` 方法期間，資料庫可以傳送資料回 ADO.NET 應用程式當做輸出參數，或當做與 INSERT 陳述式在相同批次中執行之 SELECT 陳述式結果集的第一個傳回資料錄。  ADO.NET 可以擷取這些值並在正在更新的 <xref:System.Data.DataRow> 中更新對應的資料行。  
  
 某些 Database Engine \(例如 Microsoft Access Jet Database Engine\) 不支援輸出參數而且無法在單一批次中處理多個陳述式。  使用 Jet Database Engine 時，您可以透過在 `DataAdapter` 之 `RowUpdated` 事件的事件處理常式中執行個別的 SELECT 命令，擷取針對插入資料列所產生的新 AutoNumber 值。  
  
> [!NOTE]
>  使用自動遞增值的替代方式是使用 <xref:System.Guid> 的 <xref:System.Guid.NewGuid%2A> 方法，在用戶端電腦上產生插入每個新資料列時可複製到伺服器的 GUID \(全域唯一識別項\)。  `NewGuid` 方法會產生 16 個位元組的二進位值，而此值是使用盡可能確保沒有任何值會重複的演算法所建立的。  在 SQL Server 資料庫中，GUID 會儲存在 SQL Server 可以使用 Transact\-SQL `NEWID()` 函式來自動產生的 `uniqueidentifier` 資料行中。  使用 GUID 當做主索引鍵可能會對效能造成不良影響。  [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] 提供 `NEWSEQUENTIALID()` 函式的支援，而此函式會產生循序 GUID \(雖然不保證是全域唯一的，但是可更有效率地進行索引\)。  
  
## 擷取 SQL Server Identity 資料行值  
 使用 Microsoft SQL Server 時，您可以建立含有輸出參數的預存程序，以便傳回插入資料列的識別值。  下表將描述 SQL Server 中三個可用來擷取識別資料行值的 Transact\-SQL 函式。  
  
|函式|描述|  
|--------|--------|  
|SCOPE\_IDENTITY|傳回目前執行範圍內的最後一個識別值。  建議您針對大部分案例使用 SCOPE\_IDENTITY。|  
|@@IDENTITY|包含目前工作階段 \(Session\) 中於任何資料表內產生的最後一個識別值。  @@IDENTITY 可能會受到觸發程序 \(Trigger\) 的影響，而且可能無法傳回您所預期的識別值。|  
|IDENT\_CURRENT|傳回在任何工作階段和任何範圍中針對特定資料表所產生的最後一個識別值。|  
  
 下列預存程序將示範如何將資料列插入 **Categories** 資料表，以及使用輸出參數來傳回 Transact\-SQL SCOPE\_IDENTITY\(\) 函式所產生的新識別值。  
  
```  
CREATE PROCEDURE dbo.InsertCategory  
  @CategoryName nvarchar(15),  
  @Identity int OUT  
AS  
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)  
SET @Identity = SCOPE_IDENTITY()  
```  
  
 然後，您可以將此預存程序指定為 <xref:System.Data.SqlClient.SqlDataAdapter> 物件之 <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> 的來源。  <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> 的 <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> 屬性必須設定為 <xref:System.Data.CommandType>。  識別輸出的擷取方式是建立 <xref:System.Data.ParameterDirection> 為 <xref:System.Data.ParameterDirection> 的 <xref:System.Data.SqlClient.SqlParameter>。  如果您將插入命令的 <xref:System.Data.SqlClient.SqlCommand.UpdatedRowSource%2A> 屬性設定為 `UpdateRowSource.OutputParameters` 或 `UpdateRowSource.Both`，當 `InsertCommand` 經過處理之後，系統就會傳回自動遞增的識別值並將它放置於目前資料列的 **CategoryID** 資料行中。  
  
 如果您的插入命令執行了同時包含 INSERT 陳述式和 SELECT 陳述式而且傳回新識別值的批次，您就可以將插入命令的 `UpdatedRowSource` 屬性設定為 `UpdateRowSource.FirstReturnedRecord`，藉以擷取新的值。  
  
 [!code-csharp[DataWorks SqlClient.RetrieveIdentityStoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.RetrieveIdentityStoredProcedure/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.RetrieveIdentityStoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.RetrieveIdentityStoredProcedure/VB/source.vb#1)]  
  
## 合併新的識別值  
 常見的案例是呼叫 `DataTable` 的 `GetChanges` 方法來建立僅包含變更資料列的複本，以及在呼叫 `DataAdapter` 的 `Update` 方法時使用新的複本。  當您必須將變更的資料列封送處理至執行更新的個別元件時，這種做法特別有用。  更新之後，該複本可以包含新的識別值，而這些值之後必須合併回原始的 `DataTable` 中。  新的識別值可能會與 `DataTable` 中的原始值不同。  若要完成合併，您必須保留複本中 **AutoIncrement** 資料行的原始值，才能找出並更新原始 `DataTable` 中的現有資料列，而非附加包含新識別值的新資料列。  不過，根據預設，這些原始值在呼叫 `DataAdapter` 的 `Update` 方法之後都會遺失，因為系統會針對每個更新的 `DataRow` 隱含地呼叫 `AcceptChanges`。  
  
 目前有兩種方式可以在 `DataAdapter` 更新期間保留 `DataRow` 中 `DataColumn` 的原始值。  
  
-   第一種保留原始值的方法是將 `DataAdapter` 的 `AcceptChangesDuringUpdate` 屬性設定為 `false`。  這樣做會影響正在更新之 `DataTable` 中的每個 `DataRow`。  如需詳細資訊和程式碼範例，請參閱 <xref:System.Data.Common.DataAdapter.AcceptChangesDuringUpdate%2A>。  
  
-   第二種方法是在 `DataAdapter` 的 `RowUpdated` 事件處理常式中撰寫程式碼，以便將 <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> 設定為 <xref:System.Data.UpdateStatus>。  如此一來，雖然系統會更新 `DataRow`，卻會保留每個 `DataColumn` 的原始值。  這種方法可讓您保留某些資料列的原始值，而不保留其他資料列的原始值。  例如，您的程式碼可以先檢查 <xref:System.Data.Common.RowUpdatedEventArgs.StatementType%2A> 並僅針對 `StatementType` 為 `Insert` 的資料列將 <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> 設定為 <xref:System.Data.UpdateStatus>，藉以保留已加入資料列的原始值，而不保留已編輯或刪除資料列的原始值。  
  
 當您使用上述任何一種方法在 `DataAdapter` 更新期間保留 `DataRow` 中的原始值時，ADO.NET 會執行一系列動作，將 `DataRow` 的目前值設定為輸出參數或結果集之第一個傳回資料列所傳回的新值，同時仍然保留每個 `DataColumn` 中的原始值。  首先，系統會呼叫 `DataRow` 的 `AcceptChanges` 方法來保留目前的值當做原始值，然後指派新的值。  進行這些動作之後，已將 <xref:System.Data.DataRow.RowState%2A> 屬性設定為 <xref:System.Data.DataRowState> 的 `DataRows` 會將其 `RowState` 屬性設定為 <xref:System.Data.DataRowState> \(可能無法預期\)。  
  
 命令結果套用至正在更新之每個 <xref:System.Data.DataRow> 的方式是由每個 <xref:System.Data.Common.DbCommand> 的 <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> 屬性所決定。  這個屬性會設定為 `UpdateRowSource` 列舉類型 \(Enumeration\) 中的值。  
  
 下表將描述 `UpdateRowSource` 列舉值如何影響已更新資料列的 <xref:System.Data.DataRow.RowState%2A> 屬性。  
  
|成員名稱|描述|  
|----------|--------|  
|<xref:System.Data.UpdateRowSource>|系統會呼叫 `AcceptChanges`，而且輸出參數值和 \(或\) 任何傳回之結果集中第一個資料列的值都會放置於正在更新的 `DataRow` 中。  如果沒有任何要套用的值，`RowState` 將成為 <xref:System.Data.DataRowState>。|  
|<xref:System.Data.UpdateRowSource>|如果傳回了一個資料列，系統就會呼叫 `AcceptChanges`，而且該資料列會對應至 `DataTable` 中的已變更資料列，並將 `RowState` 設定為 `Modified`。  如果沒有傳回任何資料列，系統就不會呼叫 `AcceptChanges` 而且 `RowState` 會維持 `Added`。|  
|<xref:System.Data.UpdateRowSource>|系統會忽略任何傳回的參數或資料列。  系統不會呼叫 `AcceptChanges` 而且 `RowState` 會維持 `Added`。|  
|<xref:System.Data.UpdateRowSource>|系統會呼叫 `AcceptChanges`，而且任何輸出參數都會對應至 `DataTable` 中的已變更資料列，並將 `RowState` 設定為 `Modified`。  如果沒有任何輸出參數，`RowState` 將成為 `Unchanged`。|  
  
### 範例  
 這則範例會示範如何從 `DataTable` 中擷取已變更的資料列，以及使用 <xref:System.Data.SqlClient.SqlDataAdapter> 來更新資料來源並擷取新的識別資料行值。  <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> 會執行兩個 Transact\-SQL 陳述式：第一個陳述式是 INSERT 陳述式，而第二個陳述式是使用 SCOPE\_IDENTITY 函式來擷取識別值的 SELECT 陳述式。  
  
```  
INSERT INTO dbo.Shippers (CompanyName)   
VALUES (@CompanyName);  
SELECT ShipperID, CompanyName FROM dbo.Shippers   
WHERE ShipperID = SCOPE_IDENTITY();  
```  
  
 插入命令的 `UpdatedRowSource` 屬性會設定為 `UpdateRowSource.FirstReturnedRow` 而 `DataAdapter` 的 <xref:System.Data.MissingSchemaAction> 屬性會設定為 `MissingSchemaAction.AddWithKey`。  此時，`DataTable` 已填入內容而且程式碼會將新的資料列加入至 `DataTable`。  然後，系統會將已變更的資料列擷取至新的 `DataTable` 中，然後再傳遞給更新伺服器的 `DataAdapter`。  
  
 [!code-csharp[DataWorks SqlClient.MergeIdentity#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.MergeIdentity#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/VB/source.vb#1)]  
  
 `OnRowUpdated` 事件處理常式會檢查 <xref:System.Data.SqlClient.SqlRowUpdatedEventArgs> 的 <xref:System.Data.Common.RowUpdatedEventArgs.StatementType%2A> 來判斷資料列是否為插入項目。  如果是的話，<xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> 屬性就會設定為 <xref:System.Data.UpdateStatus>。  如此一來，雖然資料列會更新，卻會保留資料列中的原始值。  在此程序的主要本文中，系統會呼叫 <xref:System.Data.DataSet.Merge%2A> 方法，將新的識別值合併至原始的 `DataTable` 中，最後再呼叫 `AcceptChanges`。  
  
 [!code-csharp[DataWorks SqlClient.MergeIdentity#2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/CS/source.cs#2)]
 [!code-vb[DataWorks SqlClient.MergeIdentity#2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/VB/source.vb#2)]  
  
## 擷取 Microsoft Access Autonumber 值  
 本節包含一則說明如何從 Jet 4.0 資料庫中擷取 `Autonumber` 值的範例。  Jet Database Engine 不支援在單一批次中執行多個陳述式或使用輸出參數，因此您無法使用其中的任何技巧來傳回指派給已插入資料列的新 `Autonumber` 值。  不過，您可以將程式碼加入至 `RowUpdated` 事件處理常式，以便執行個別的 SELECT @@IDENTITY 陳述式來擷取新 `Autonumber` 值。  
  
### 範例  
 這則範例會在呼叫 <xref:System.Data.OleDb.OleDbDataAdapter> 來填入 `DataTable` 之前，使用正確的結構描述來設定 `DataTable`，而非使用 `MissingSchemaAction.AddWithKey` 來加入結構描述資訊。  在此情況中，透過將 <xref:System.Data.DataColumn.AutoIncrement%2A> 設定為 `true`、將 <xref:System.Data.DataColumn.AutoIncrementSeed%2A> 設定為 0 以及將 <xref:System.Data.DataColumn.AutoIncrementStep%2A> 設定為 \-1，讓 **CategoryID** 資料行設定為遞減指派給每個已插入資料列的值 \(從零開始\)。  接著，程式碼會加入兩個新的資料列，然後使用 `GetChanges`，將已變更的資料列加入至傳遞給 `Update` 方法的新 `DataTable`。  
  
 [!code-csharp[DataWorks OleDb.JetAutonumberMerge#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/CS/source.cs#1)]
 [!code-vb[DataWorks OleDb.JetAutonumberMerge#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/VB/source.vb#1)]  
  
 `RowUpdated` 事件處理常式與 `OleDbDataAdapter` 的 `Update` 陳述式都會使用相同的已開啟 <xref:System.Data.OleDb.OleDbConnection>。  它會檢查 <xref:System.Data.OleDb.OleDbRowUpdatedEventArgs> 的 `StatementType` 是否有插入的資料列。  系統會針對每個插入的資料列建立新的 <xref:System.Data.OleDb.OleDbCommand>，以便在連接上執行 SELECT @@IDENTITY 陳述式，並傳回新的 `Autonumber` 值 \(放置於 `DataRow` 的 **CategoryID** 資料行中\)。  然後，`Status` 屬性會設定為 `UpdateStatus.SkipCurrentRow`，以便抑制 `AcceptChanges` 的隱藏呼叫。  在此程序的主要本文中，系統會呼叫 `Merge` 方法來合併兩個 `DataTable` 物件，最後再呼叫 `AcceptChanges`。  
  
 [!code-csharp[DataWorks OleDb.JetAutonumberMerge#2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/CS/source.cs#2)]
 [!code-vb[DataWorks OleDb.JetAutonumberMerge#2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/VB/source.vb#2)]  
  
### 擷取識別值  
 當資料行中的值必須是唯一時，通常會將資料行設定為識別資料行。  此外，有時也需要新資料的識別值。  這個範例示範如何擷取識別值：  
  
-   建立預存程序插入資料並傳回識別值。  
  
-   執行命令插入新資料並顯示結果。  
  
-   使用 <xref:System.Data.SqlClient.SqlDataAdapter> 插入新資料並顯示結果。  
  
 編譯及執行範例之前，您必須使用下列指令碼建立範例資料庫：  
  
```  
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
CREATE procedure [dbo].[CourseExtInfo] @CourseId int  
as  
select c.CourseID,c.Title,c.Credits,d.Name as DepartmentName  
from Course as c left outer join Department as d on c.DepartmentID=d.DepartmentID  
where c.CourseID=@CourseId  
  
GO  
  
SET ANSI_NULLS ON  
GO  
SET QUOTED_IDENTIFIER ON  
GO  
create procedure [dbo].[DepartmentInfo] @DepartmentId int,@CourseCount int output  
as  
select @CourseCount=Count(c.CourseID)  
from course as c  
where c.DepartmentID=@DepartmentId  
  
select d.DepartmentID,d.Name,d.Budget,d.StartDate,d.Administrator  
from Department as d  
where d.DepartmentID=@DepartmentId  
  
GO  
  
SET ANSI_NULLS ON  
GO  
SET QUOTED_IDENTIFIER ON  
GO  
Create PROCEDURE [dbo].[GetDepartmentsOfSpecifiedYear]   
@Year int,@BudgetSum money output  
AS  
BEGIN  
        SELECT @BudgetSum=SUM([Budget])  
  FROM [MySchool].[dbo].[Department]  
  Where YEAR([StartDate])=@Year   
  
SELECT [DepartmentID]  
      ,[Name]  
      ,[Budget]  
      ,[StartDate]  
      ,[Administrator]  
  FROM [MySchool].[dbo].[Department]  
  Where YEAR([StartDate])=@Year  
  
END  
GO  
  
SET ANSI_NULLS ON  
GO  
SET QUOTED_IDENTIFIER ON  
GO  
CREATE PROCEDURE [dbo].[GradeOfStudent]   
-- Add the parameters for the stored procedure here  
@CourseTitle nvarchar(100),@FirstName nvarchar(50),  
@LastName nvarchar(50),@Grade decimal(3,2) output  
AS  
BEGIN  
select @Grade=Max(Grade)  
from [dbo].[StudentGrade] as s join [dbo].[Course] as c on   
s.CourseID=c.CourseID join [dbo].[Person] as p on s.StudentID=p.PersonID  
where c.Title=@CourseTitle and p.FirstName=@FirstName   
and p.LastName= @LastName  
END  
GO  
  
SET ANSI_NULLS ON  
GO  
SET QUOTED_IDENTIFIER ON  
GO  
CREATE PROCEDURE [dbo].[InsertPerson]   
-- Add the parameters for the stored procedure here  
@FirstName nvarchar(50),@LastName nvarchar(50),  
@PersonID int output  
AS  
BEGIN  
    insert [dbo].[Person](LastName,FirstName) Values(@LastName,@FirstName)  
  
    set @PersonID=SCOPE_IDENTITY()  
END  
Go  
  
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
  
SET ANSI_NULLS ON  
GO  
SET QUOTED_IDENTIFIER ON  
GO  
SET ANSI_PADDING ON  
GO  
CREATE TABLE [dbo].[Person]([PersonID] [int] IDENTITY(1,1) NOT NULL,  
[LastName] [nvarchar](50) NOT NULL,  
[FirstName] [nvarchar](50) NOT NULL,  
[HireDate] [datetime] NULL,  
[EnrollmentDate] [datetime] NULL,  
[Picture] [varbinary](max) NULL,  
 CONSTRAINT [PK_School.Student] PRIMARY KEY CLUSTERED   
(  
[PersonID] ASC  
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]  
  
GO  
  
SET ANSI_NULLS ON  
GO  
SET QUOTED_IDENTIFIER ON  
GO  
CREATE TABLE [dbo].[StudentGrade]([EnrollmentID] [int] IDENTITY(1,1) NOT NULL,  
[CourseID] [nvarchar](10) NOT NULL,  
[StudentID] [int] NOT NULL,  
[Grade] [decimal](3, 2) NOT NULL,  
 CONSTRAINT [PK_StudentGrade] PRIMARY KEY CLUSTERED   
(  
[EnrollmentID] ASC  
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]  
  
GO  
  
SET ANSI_NULLS ON  
GO  
SET QUOTED_IDENTIFIER ON  
GO  
create view [dbo].[EnglishCourse]  
as  
select c.CourseID,c.Title,c.Credits,c.DepartmentID  
from Course as c join Department as d on c.DepartmentID=d.DepartmentID  
where d.Name=N'English'  
  
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
SET IDENTITY_INSERT [dbo].[Person] ON   
  
INSERT [dbo].[Person] ([PersonID], [LastName], [FirstName], [HireDate], [EnrollmentDate]) VALUES (1, N'Hu', N'Nan', NULL, CAST(0x0000A0BF00000000 AS DateTime))  
INSERT [dbo].[Person] ([PersonID], [LastName], [FirstName], [HireDate], [EnrollmentDate]) VALUES (2, N'Norman', N'Laura', NULL, CAST(0x0000A0BF00000000 AS DateTime))  
INSERT [dbo].[Person] ([PersonID], [LastName], [FirstName], [HireDate], [EnrollmentDate]) VALUES (3, N'Olivotto', N'Nino', NULL, CAST(0x0000A0BF00000000 AS DateTime))  
INSERT [dbo].[Person] ([PersonID], [LastName], [FirstName], [HireDate], [EnrollmentDate]) VALUES (4, N'Anand', N'Arturo', NULL, CAST(0x0000A0BF00000000 AS DateTime))  
INSERT [dbo].[Person] ([PersonID], [LastName], [FirstName], [HireDate], [EnrollmentDate]) VALUES (5, N'Jai', N'Damien', NULL, CAST(0x0000A0BF00000000 AS DateTime))  
INSERT [dbo].[Person] ([PersonID], [LastName], [FirstName], [HireDate], [EnrollmentDate]) VALUES (6, N'Holt', N'Roger', CAST(0x000097F100000000 AS DateTime), NULL)  
INSERT [dbo].[Person] ([PersonID], [LastName], [FirstName], [HireDate], [EnrollmentDate]) VALUES (7, N'Martin', N'Randall', CAST(0x00008B1A00000000 AS DateTime), NULL)  
SET IDENTITY_INSERT [dbo].[Person] OFF  
SET IDENTITY_INSERT [dbo].[StudentGrade] ON   
  
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (1, N'C1045', 1, CAST(3.50 AS Decimal(3, 2)))  
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (2, N'C1045', 2, CAST(3.00 AS Decimal(3, 2)))  
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (3, N'C1045', 3, CAST(2.50 AS Decimal(3, 2)))  
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (4, N'C1045', 4, CAST(4.00 AS Decimal(3, 2)))  
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (5, N'C1045', 5, CAST(3.50 AS Decimal(3, 2)))  
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (6, N'C1061', 1, CAST(4.00 AS Decimal(3, 2)))  
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (7, N'C1061', 3, CAST(3.50 AS Decimal(3, 2)))  
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (8, N'C1061', 4, CAST(2.50 AS Decimal(3, 2)))  
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (9, N'C1061', 5, CAST(1.50 AS Decimal(3, 2)))  
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (10, N'C2021', 1, CAST(2.50 AS Decimal(3, 2)))  
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (11, N'C2021', 2, CAST(3.50 AS Decimal(3, 2)))  
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (12, N'C2021', 4, CAST(3.00 AS Decimal(3, 2)))  
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (13, N'C2021', 5, CAST(3.00 AS Decimal(3, 2)))  
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (14, N'C2042', 1, CAST(2.00 AS Decimal(3, 2)))  
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (15, N'C2042', 2, CAST(3.50 AS Decimal(3, 2)))  
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (16, N'C2042', 3, CAST(4.00 AS Decimal(3, 2)))  
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (17, N'C2042', 5, CAST(3.00 AS Decimal(3, 2)))  
SET IDENTITY_INSERT [dbo].[StudentGrade] OFF  
ALTER TABLE [dbo].[Course]  WITH CHECK ADD  CONSTRAINT [FK_Course_Department] FOREIGN KEY([DepartmentID])  
REFERENCES [dbo].[Department] ([DepartmentID])  
GO  
ALTER TABLE [dbo].[Course] CHECK CONSTRAINT [FK_Course_Department]  
GO  
ALTER TABLE [dbo].[StudentGrade]  WITH CHECK ADD  CONSTRAINT [FK_StudentGrade_Student] FOREIGN KEY([StudentID])  
REFERENCES [dbo].[Person] ([PersonID])  
GO  
ALTER TABLE [dbo].[StudentGrade] CHECK CONSTRAINT [FK_StudentGrade_Student]  
GO  
```  
  
 後面接著程式碼清單：  
  
> [!IMPORTANT]
>  這個程式碼清單參考 Access 資料庫檔案 MySchool.mdb。  您可以從 [Visual Studio 2012 範例](http://code.msdn.microsoft.com/How-to-retrieve-the-95b4ee43)或 [Visual Studio 2013 範例](http://code.msdn.microsoft.com/How-to-Retrieve-the-511acece)下載 MySchool.mdb \(當做完整 C\# 或 Visual Basic 範例專案的一部分下載\)。  
  
```  
using System;  
using System.Data;  
using System.Data.OleDb;  
using System.Data.SqlClient;  
  
class Program {  
   static void Main(string[] args) {  
      String SqlDbConnectionString = "Data Source=(local);Initial Catalog=MySchool;Integrated Security=True;Asynchronous Processing=true;";  
  
      InsertPerson(SqlDbConnectionString, "Janice", "Galvin");  
      Console.WriteLine();  
  
      InsertPersonInAdapter(SqlDbConnectionString, "Peter", "Krebs");  
      Console.WriteLine();  
  
      String oledbConnectionString = "Provider=Microsoft.Jet.OLEDB.4.0; Data Source=Database\\MySchool.mdb";  
      InsertPersonInJet4Database(oledbConnectionString, "Janice", "Galvin");  
      Console.WriteLine();  
  
      Console.WriteLine("Please press any key to exit.....");  
      Console.ReadKey();  
   }  
  
   // Using stored procedure to insert a new row and retrieve the identity value  
   static void InsertPerson(String connectionString, String firstName, String lastName) {  
      String commandText = "dbo.InsertPerson";  
  
      using (SqlConnection conn = new SqlConnection(connectionString)) {  
         using (SqlCommand cmd = new SqlCommand(commandText, conn)) {  
            cmd.CommandType = CommandType.StoredProcedure;  
  
            cmd.Parameters.Add(new SqlParameter("@FirstName", firstName));  
            cmd.Parameters.Add(new SqlParameter("@LastName", lastName));  
            SqlParameter personId = new SqlParameter("@PersonID", SqlDbType.Int);  
            personId.Direction = ParameterDirection.Output;  
            cmd.Parameters.Add(personId);  
  
            conn.Open();  
            cmd.ExecuteNonQuery();  
  
            Console.WriteLine("Person Id of new person:{0}", personId.Value);  
         }  
      }  
   }  
  
   // Using stored procedure in adapter to insert new rows and update the identity value.  
   static void InsertPersonInAdapter(String connectionString, String firstName, String lastName) {  
      String commandText = "dbo.InsertPerson";  
      using (SqlConnection conn = new SqlConnection(connectionString)) {  
         SqlDataAdapter mySchool = new SqlDataAdapter("Select PersonID,FirstName,LastName from [dbo].[Person]", conn);  
  
         mySchool.InsertCommand = new SqlCommand(commandText, conn);  
         mySchool.InsertCommand.CommandType = CommandType.StoredProcedure;  
  
         mySchool.InsertCommand.Parameters.Add(  
             new SqlParameter("@FirstName", SqlDbType.NVarChar, 50, "FirstName"));  
         mySchool.InsertCommand.Parameters.Add(  
             new SqlParameter("@LastName", SqlDbType.NVarChar, 50, "LastName"));  
  
         SqlParameter personId = mySchool.InsertCommand.Parameters.Add(new SqlParameter("@PersonID", SqlDbType.Int, 0, "PersonID"));  
         personId.Direction = ParameterDirection.Output;  
  
         DataTable persons = new DataTable();  
         mySchool.Fill(persons);  
  
         DataRow newPerson = persons.NewRow();  
         newPerson["FirstName"] = firstName;  
         newPerson["LastName"] = lastName;  
         persons.Rows.Add(newPerson);  
  
         mySchool.Update(persons);  
         Console.WriteLine("Show all persons:");  
         ShowDataTable(persons, 14);  
      }  
   }  
  
   /// For a Jet 4.0 database, we need use the sigle statement and event handler to insert new rows and retrieve the identity value.  
   static void InsertPersonInJet4Database(String connectionString, String firstName, String lastName) {  
      String commandText = "Insert into Person(FirstName,LastName) Values(?,?)";  
      using (OleDbConnection conn = new OleDbConnection(connectionString)) {  
         OleDbDataAdapter mySchool = new OleDbDataAdapter("Select PersonID,FirstName,LastName from Person", conn);  
  
         // Create Insert Command  
         mySchool.InsertCommand = new OleDbCommand(commandText, conn);  
         mySchool.InsertCommand.CommandType = CommandType.Text;  
  
         mySchool.InsertCommand.Parameters.Add(new OleDbParameter("@FirstName", OleDbType.VarChar, 50, "FirstName"));  
         mySchool.InsertCommand.Parameters.Add(new OleDbParameter("@LastName", OleDbType.VarChar, 50, "LastName"));  
         mySchool.InsertCommand.UpdatedRowSource = UpdateRowSource.Both;  
  
         DataTable persons = CreatePersonsTable();  
  
         mySchool.Fill(persons);  
  
         DataRow newPerson = persons.NewRow();  
         newPerson["FirstName"] = firstName;  
         newPerson["LastName"] = lastName;  
         persons.Rows.Add(newPerson);  
  
         DataTable dataChanges = persons.GetChanges();  
  
         mySchool.RowUpdated += OnRowUpdated;  
  
         mySchool.Update(dataChanges);  
  
         Console.WriteLine("Data before merging:");  
         ShowDataTable(persons, 14);  
         Console.WriteLine();  
  
         persons.Merge(dataChanges);  
         persons.AcceptChanges();  
  
         Console.WriteLine("Data after merging");  
         ShowDataTable(persons, 14);  
      }  
   }  
  
   static void OnRowUpdated(object sender, OleDbRowUpdatedEventArgs e) {  
      if (e.StatementType == StatementType.Insert) {  
         // Retrieve the identity value  
         OleDbCommand cmdNewId = new OleDbCommand("Select @@IDENTITY", e.Command.Connection);  
         e.Row["PersonID"] = (Int32)cmdNewId.ExecuteScalar();  
  
         // After the status is changed, the original values in the row are preserved. And the   
         // Merge method will be called to merge the new identity value into the original DataTable.  
         e.Status = UpdateStatus.SkipCurrentRow;  
      }  
   }  
  
   // Create the Persons table before filling.  
   private static DataTable CreatePersonsTable() {  
      DataTable persons = new DataTable();  
  
      DataColumn personId = new DataColumn();  
      personId.DataType = Type.GetType("System.Int32");  
      personId.ColumnName = "PersonID";  
      personId.AutoIncrement = true;  
      personId.AutoIncrementSeed = 0;  
      personId.AutoIncrementStep = -1;  
      persons.Columns.Add(personId);  
  
      DataColumn firstName = new DataColumn();  
      firstName.DataType = Type.GetType("System.String");  
      firstName.ColumnName = "FirstName";  
      persons.Columns.Add(firstName);  
  
      DataColumn lastName = new DataColumn();  
      lastName.DataType = Type.GetType("System.String");  
      lastName.ColumnName = "LastName";  
      persons.Columns.Add(lastName);  
  
      DataColumn[] pkey = { personId };  
      persons.PrimaryKey = pkey;  
  
      return persons;  
   }  
  
   private static void ShowDataTable(DataTable table, Int32 length) {  
      foreach (DataColumn col in table.Columns) {  
         Console.Write("{0,-" + length + "}", col.ColumnName);  
      }  
      Console.WriteLine();  
  
      foreach (DataRow row in table.Rows) {  
         foreach (DataColumn col in table.Columns) {  
            if (col.DataType.Equals(typeof(DateTime)))  
               Console.Write("{0,-" + length + ":d}", row[col]);  
            else if (col.DataType.Equals(typeof(Decimal)))   
               Console.Write("{0,-" + length + ":C}", row[col]);  
            else  
               Console.Write("{0,-" + length + "}", row[col]);  
         }  
  
         Console.WriteLine();  
      }  
   }  
}  
```  
  
## 請參閱  
 [擷取和修改 ADO.NET 中的資料](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)   
 [DataAdapter 和 DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)   
 [資料列狀態和資料列版本](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)   
 [AcceptChanges 和 RejectChanges](../../../../docs/framework/data/adonet/dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)   
 [合併 DataSet 內容](../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md)   
 [以 DataAdapter 更新資料來源](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)