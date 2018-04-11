---
title: 逐步解說：使用型別提供者存取 SQL 資料庫 (F#)
description: '了解如何使用 SqlDataConnection (LINQ to SQL) 型別提供者在 F # 3.0 有即時資料庫連接時，產生 SQL 資料庫類型。'
keywords: Visual F#, F#, 函式程式設計
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 1c413eb0-16a5-4c1a-9a4e-ad6877e645d6
ms.openlocfilehash: dbc5d889fb7883b4327180fdf34accf45bf519e7
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/10/2018
---
# <a name="walkthrough-accessing-a-sql-database-by-using-type-providers"></a>逐步解說：使用型別提供者存取 SQL 資料庫

> [!NOTE]
本指南針對 F # 3.0 所撰寫，而且會更新。  請參閱 [FSharp.Data](https://fsharp.github.io/FSharp.Data/) 以取得最新的跨平台型別提供者。

> [!NOTE]
應用程式開發介面參考連結將帶您到 MSDN。  docs.microsoft.com API 參考不完整。

本逐步解說將說明如何使用 SqlDataConnection (LINQ to SQL) 型別提供者所提供之 F # 3.0 有即時連接至資料庫時，SQL 資料庫中產生的資料類型。 如果您沒有即時連接到資料庫，但您需要 LINQ to SQL 結構描述檔案 （DBML 檔案），請參閱[逐步解說： 產生 F # 類型從 DBML 檔案](generating-fsharp-types-from-dbml.md)。

這個逐步解說將說明下列工作。 必須執行這些工作順利完成本逐步解說的順序如下：


- 準備測試資料庫

- 建立專案

- 設定類型提供者

- 查詢資料

- 使用可為 null 的欄位

- 呼叫預存程序

- 更新資料庫

- 執行 TRANSACT-SQL 程式碼

- 使用完整資料內容

- 刪除資料

- 建立測試資料庫 （如有需要）

## <a name="preparing-a-test-database"></a>準備測試資料庫
在伺服器上執行 SQL Server，建立資料庫，以進行測試。 您可以使用 「 資料庫建立指令碼的區段中的此頁面底部[建立測試資料庫](#creating-a-test-database)若要這樣做。


#### <a name="to-prepare-a-test-database"></a>若要準備測試資料庫

執行 MyDatabase 建立指令碼，請開啟**檢視**功能表，然後選擇  **SQL Server 物件總管**或選擇 Ctrl +\, Ctrl + S 鍵。 在**SQL Server 物件總管**視窗中，開啟適當的執行個體的捷徑功能表，選擇 **新查詢**複製底部的這個頁面上，指令碼，然後貼到編輯器的 指令碼。 若要執行的 SQL 指令碼，選擇工具列圖示，三重平滑的符號，或選擇 Ctrl + Q 鍵。 如需有關**SQL Server 物件總管**，請參閱[連接的資料庫開發](https://msdn.microsoft.com/library/hh272679(VS.103).aspx)。


## <a name="creating-the-project"></a>建立專案
接下來，您可以建立 F # 應用程式專案。


#### <a name="to-create-and-set-up-the-project"></a>建立並設定專案

1. 建立新的 F # 應用程式專案。

2. 將參考加入至[FSharp.Data.TypeProviders](https://msdn.microsoft.com/library/a858f859-047a-44ab-945b-8731d7a0e6e3)，以及`System.Data`，和`System.Data.Linq`。

3. 將下列程式碼加入至您 F # 程式碼檔案頂端 Program.fs 開啟適當的命名空間。

  ```fsharp
open System
open System.Data
open System.Data.Linq
open Microsoft.FSharp.Data.TypeProviders
open Microsoft.FSharp.Linq
```

4. 如同大部分 F # 程式中，您可以在此逐步解說中當做編譯的程式，執行程式碼，或者您可以執行它以互動方式做為指令碼。 如果您想要使用指令碼，開啟專案的選取節點的捷徑功能表**加入新項目**、 F # 指令碼檔案，加上指令碼中每一個步驟中加入程式碼。 您必須在要載入的組件參考之檔案的頂端加入下列幾行。

  ```fsharp
#r "System.Data.dll"
#r "FSharp.Data.TypeProviders.dll"
#r "System.Data.Linq.dll"
```

  然後，當您將按 Alt + Enter 來執行 F # Interactive 中，您可以選取每個程式碼區塊。

## <a name="setting-up-a-type-provider"></a>設定類型提供者
在此步驟中，您會建立型別提供者的資料庫結構描述。


#### <a name="to-set-up-the-type-provider-from-a-direct-database-connection"></a>若要設定從直接連接資料庫的型別提供者

有兩個重要的行，您需要以建立可讓您查詢 SQL 資料庫使用的型別提供者類型的程式碼。 首先，您具現化型別提供者。 若要這樣做，建立 外觀類型縮寫`SqlDataConnection`與靜態泛型參數。 `SqlDataConnection` SQL 型別提供者，而且不應該與混淆`SqlConnection`類型，它是在 ADO.NET 程式設計中使用。 如果您有一個資料庫，您想要連接，而且連接字串，使用下列程式碼叫用型別提供者。 取代為指定的字串範例連接字串。 例如，如果您的伺服器 MYSERVER 和資料庫執行個體是執行個體、 資料庫名稱是 MyDatabase，和您想要使用 Windows 驗證來存取資料庫，則連接字串會是做為提供下列的範例程式碼。

```fsharp
type dbSchema = SqlDataConnection<"Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;">
let db = dbSchema.GetDataContext()

// Enable the logging of database activity to the console.
db.DataContext.Log <- System.Console.Out
```

現在您有一個型別， `dbSchema`，這是包含所有產生的型別代表資料庫資料表的父類型。 您也可以是物件， `db`，其中包含做為其成員資料庫中的所有資料表。 資料表名稱屬性，且這些屬性的類型由 F # 編譯器產生。 將型別本身顯示底下的巢狀型別為`dbSchema.ServiceTypes`。 因此，擷取這些資料表的資料列的任何資料，都會產生該資料表的適當類型的執行個體。 類型的名稱是`ServiceTypes.Table1`。

您熟悉如何 F # 語言解譯成 SQL 查詢的查詢，檢閱設定列`Log`資料內容上的屬性。

若要進一步探索型別提供者所建立的類型，加入下列程式碼。

```fsharp
let table1 = db.Table1
```

將滑鼠停留在`table1`以查看它的型別。 它的類型是`System.Data.Linq.Table<dbSchema.ServiceTypes.Table1>`和泛型引數表示每個資料列的類型是產生的型別， `dbSchema.ServiceTypes.Table1`。 編譯器會在資料庫中建立的每個資料表類似的類型。

## <a name="querying-the-data"></a>查詢資料
在此步驟中，您可以撰寫查詢，使用 F # 查詢運算式。


#### <a name="to-query-the-data"></a>若要查詢資料

1. 現在在資料庫中建立該資料表的查詢。 加入下列程式碼。

  ```fsharp
   let query1 =
     query {
       for row in db.Table1 do
       select row
     }
   query1 |> Seq.iter (fun row -> printfn "%s %d" row.Name row.TestData1)
```

  文字的外觀`query`指出這是查詢運算式會產生類似一般資料庫查詢結果的集合的計算運算式的型別。 如果您將滑鼠停留在查詢，您會看到它是的執行個體[Linq.QueryBuilder 類別](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.querybuilder-class-%5bfsharp%5d)，定義查詢計算運算式的類型。 如果您將滑鼠停留在`query1`，您會看到它是的執行個體`System.Linq.IQueryable`。 正如其名，`System.Linq.IQueryable`代表資料查詢，不是查詢的結果。 查詢受限於延遲評估，也就是說，資料庫才查詢評估查詢時。 最後一行將透過查詢傳`Seq.iter`。 查詢是可列舉，而且可能會像順序逐一查看。 如需詳細資訊，請參閱[查詢運算式](../../language-reference/query-expressions.md)。

2. 現在加入至查詢的查詢運算子。 有許多查詢運算子可讓您可以建構複雜的查詢。 此範例也會顯示您可以用來消除查詢變數，並改為使用管線運算子。

  ```fsharp
   query {
     for row in db.Table1 do
     where (row.TestData1 > 2)
     select row
   } |> Seq.iter (fun row -> printfn "%d %s" row.TestData1 row.Name)
```

3. 加入兩個資料表的聯結與更複雜的查詢。

  ```fsharp
   query {
     for row1 in db.Table1 do
     join row2 in db.Table2 on (row1.Id = row2.Id)
     select (row1, row2)
   } |> Seq.iteri (fun index (row1, row2) ->
                   if (index = 0) then printfn "Table1.Id TestData1 TestData2 Name Table2.Id TestData1 TestData2 Name"
                   printfn "%d %d %f %s %d %d %f %s" row1.Id row1.TestData1 row1.TestData2 row1.Name
                     row2.Id (row2.TestData1.GetValueOrDefault()) (row2.TestData2.GetValueOrDefault()) row2.Name)
```

4. 在真實世界的程式碼，在您的查詢參數通常值或變數，不會進行編譯時間常數。 加入下列程式碼包裝函式，使用參數，然後再撥打該函式值為 10 中的查詢。

  ```fsharp
   let findData param =
     query {
       for row in db.Table1 do
       where (row.TestData1 = param)
       select row
     }

   findData 10 |> Seq.iter (fun row -> printfn "Found row: %d %d %f %s" row.Id row.TestData1 row.TestData2 row.Name)
```

## <a name="working-with-nullable-fields"></a>使用可為 null 的欄位
在資料庫中，欄位通常會允許 null 值。 在.NET 類型系統中，您無法使用一般的數值資料類型，允許 null 因為這些型別沒有可能的值為 null 的資料。 因此，這些值都由執行個體`System.Nullable`型別。 而不是存取這類欄位的值，直接與欄位的名稱，您需要加入一些額外的步驟。 您可以使用`System.Nullable.Value`屬性來存取可為 null 型別的基礎值。 `System.Nullable.Value`屬性擲回例外狀況的物件是 null，而不是值。 您可以使用`System.Nullable.HasValue`布林方法，以判斷是否有值存在，或使用`System.Nullable.GetValueOrDefault()`以確保您在所有情況下有實際值。 如果您使用`System.Nullable.GetValueOrDefault()`和 null 值在資料庫中，則會被取代的值為空字串的字串類型。 例如，0 的整數類資料類型或浮點 0.0 點類型。

當您需要在可為 null 值上執行等號比較測試或比較`where`子句的查詢中，您可以使用可為 null 的運算子中找到[Linq.NullableOperators 模組](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.nullableoperators-module-%5bfsharp%5d)。 這些就像是一般比較運算子`=`， `>`， `<=`，依此類推，不同之處在於問號會出現在左邊或右邊運算子可為 null 的值。 比方說，運算子`>?`大於-運算子右邊的可為 null 值。 這些運算子的運作的方式是，如果任一邊的運算式為 null，則運算式評估為`false`。 在`where`子句，這通常表示包含 null 欄位的資料列會未選取，而且不會傳回查詢結果中。


#### <a name="to-work-with-nullable-fields"></a>若要使用可為 null 的欄位

下列程式碼將示範使用可為 null 的值;假設**TestData1**是允許 null 整數欄位。

```fsharp
query {
  for row in db.Table2 do
  where (row.TestData1.HasValue && row.TestData1.Value > 2)
  select row
} |> Seq.iter (fun row -> printfn "%d %s" row.TestData1.Value row.Name)

query {
  for row in db.Table2 do
  // Use a nullable operator ?>
  where (row.TestData1 ?> 2)
  select row
} |> Seq.iter (fun row -> printfn "%d %s" (row.TestData1.GetValueOrDefault()) row.Name)
```

## <a name="calling-a-stored-procedure"></a>呼叫預存程序
在資料庫上的任何預存程序可以呼叫從 F #。 您必須設定的靜態參數`StoredProcedures`至`true`型別提供者具現化。 型別提供者`SqlDataConnection`包含數個靜態方法，可讓您設定所產生的型別。 其中的完整說明，請參閱[SqlDataConnection 類型提供者](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqldataconnection-type-provider-%5bfsharp%5d)。 資料內容型別上的方法會產生每個預存程序。


#### <a name="to-call-a-stored-procedure"></a>若要呼叫預存程序

如果預存程序會採用可為 null 的參數，您需要將適當`System.Nullable`值。 傳回純量或資料表的預存程序方法的傳回值是`System.Data.Linq.ISingleResult`，其中包含屬性，讓您存取傳回的資料。 型別引數`System.Data.Linq.ISingleResult`相依於特定的程序，而且也是一樣的型別提供者產生的型別。 名為預存程序`Procedure1`，型別是`Procedure1Result`。 型別`Procedure1Result`包含名稱的資料行中傳回的資料表，或傳回純量值的預存程序，它表示的傳回值。

下列程式碼會假設是程序`Procedure1`採用兩個可為 null 的整數，做為參數的資料庫，執行查詢，傳回的資料行`TestData1`，並傳回一個整數。

```fsharp
type schema = SqlDataConnection<"Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;", StoredProcedures = true>

let testdb = schema.GetDataContext()

let nullable value = new System.Nullable<_>(value)

let callProcedure1 a b =
  let results = testdb.Procedure1(nullable a, nullable b)
  for result in results do
    printfn "%d" (result.TestData1.GetValueOrDefault())
  results.ReturnValue :?> int

printfn "Return Value: %d" (callProcedure1 10 20)
```

## <a name="updating-the-database"></a>更新資料庫
LINQ DataContext 類型包含方法，讓您更輕鬆地在完整輸入的方式，與產生的型別中執行交易的資料庫更新。


#### <a name="to-update-the-database"></a>若要更新資料庫

1. 下列程式碼，在數個資料列會加入至資料庫。 如果您只新增一個資料列，您可以使用`System.Data.Linq.Table.InsertOnSubmit()`來指定要加入新的資料列。 如果您要插入多個資料列，您應該將其放入集合，且呼叫`System.Data.Linq.Table.InsertAllOnSubmit(System.Collections.Generic.IEnumerable)`。 當您呼叫其中一種方法時，資料庫不會立即變更。 您必須呼叫`System.Data.Linq.DataContext.SubmitChanges`實際認可變更。 根據預設，您才能執行的所有項目呼叫`System.Data.Linq.DataContext.SubmitChanges`是隱含的相同交易的一部分。

 ```fsharp
   let newRecord = new dbSchema.ServiceTypes.Table1(Id = 100,
                                                    TestData1 = 35, 
                                                    TestData2 = 2.0,
                                                    Name = "Testing123")

   let newValues =
     [ for i in [1 .. 10] ->
       new dbSchema.ServiceTypes.Table3(Id = 700 + i,
         Name = "Testing" + i.ToString(),
         Data = i) ]

   // Insert the new data into the database.
   db.Table1.InsertOnSubmit(newRecord)
   db.Table3.InsertAllOnSubmit(newValues)

   try
     db.DataContext.SubmitChanges()
     printfn "Successfully inserted new rows."
   with
   | exn -> printfn "Exception:\n%s" exn.Message
```

2. 現在清除資料列藉由呼叫刪除作業。

  ```fsharp
   // Now delete what was added.
   db.Table1.DeleteOnSubmit(newRecord)
   db.Table3.DeleteAllOnSubmit(newValues)

   try
     db.DataContext.SubmitChanges()
     printfn "Successfully deleted all pending rows."
   with
   | exn -> printfn "Exception:\n%s" exn.Message
```

## <a name="executing-transact-sql-code"></a>執行 TRANSACT-SQL 程式碼
您也可以使用來直接指定 TRANSACT-SQL`System.Data.Linq.DataContext.ExecuteCommand(System.String,System.Object[])`方法`DataContext`類別。


#### <a name="to-execute-custom-sql-commands"></a>若要執行自訂的 SQL 命令

下列程式碼會示範如何將 SQL 命令，將記錄插入資料表也可以從資料表刪除記錄傳送。

```fsharp
try
  db.DataContext.ExecuteCommand("INSERT INTO Table3 (Id, Name, Data) VALUES (102, 'Testing', 55)") |> ignore
with
| exn -> printfn "Exception:\n%s" exn.Message

try //AND Name = 'Testing' AND Data = 55
  db.DataContext.ExecuteCommand("DELETE FROM Table3 WHERE Id = 102 ") |> ignore
with
| exn -> printfn "Exception:\n%s" exn.Message
```

## <a name="using-the-full-data-context"></a>使用完整資料內容
在上一個範例中，`GetDataContext`方法用來取得所謂*簡化的資料內容*資料庫結構描述。 簡化的資料內容是您更輕鬆地使用當您建構查詢時，因為沒有為許多成員時。 因此，當您瀏覽在 IntelliSense 中的屬性，您可以專注於資料庫結構，例如資料表和預存程序。 不過，沒有限制您可以使用簡化的資料內容執行。 可讓您執行其他動作的完整資料內容。 也可以使用此檔案位於`ServiceTypes`和名稱為*DataContext*如果您所提供的靜態參數。 如果您未提供，資料內容型別名稱會為您產生由 SqlMetal.exe 根據其他的輸入。 完整資料內容繼承自`System.Data.Linq.DataContext`並公開其基底類別，例如包含 ADO.NET 資料類型的參考成員`Connection`物件，這類方法`System.Data.Linq.DataContext.ExecuteCommand(System.String,System.Object[])`和`System.Data.Linq.DataContext.ExecuteQuery(System.String,System.Object[])`，您可以使用在 SQL 中，撰寫查詢而也表示明確使用交易。


#### <a name="to-use-the-full-data-context"></a>若要使用完整資料內容

下列程式碼示範如何取得完整的資料內容物件，並使用它來直接對資料庫執行命令。 在此情況下，兩個命令會執行相同的交易的一部分。

```fsharp
let dbConnection = testdb.Connection
let fullContext = new dbSchema.ServiceTypes.MyDatabase(dbConnection)

dbConnection.Open()

let transaction = dbConnection.BeginTransaction()
fullContext.Transaction <- transaction

try
  let result1 = fullContext.ExecuteCommand("INSERT INTO Table3 (Id, Name, Data) VALUES (102, 'A', 55)")
  printfn "ExecuteCommand Result: %d" result1
  let result2 = fullContext.ExecuteCommand("INSERT INTO Table3 (Id, Name, Data) VALUES (103, 'B', -2)")
  printfn "ExecuteCommand Result: %d" result2
  if (result1 <> 1 || result2 <> 1) then
    transaction.Rollback()
    printfn "Rolled back creation of two new rows."
  else
    transaction.Commit()
  printfn "Successfully committed two new rows."
with
| exn ->
  transaction.Rollback()
  printfn "Rolled back creation of two new rows due to exception:\n%s" exn.Message

dbConnection.Close()
```

## <a name="deleting-data"></a>刪除資料
此步驟說明如何從資料表刪除資料列。


#### <a name="to-delete-rows-from-the-database"></a>若要從資料庫刪除資料列

現在，清除任何加入的資料列所撰寫的函式會從指定之資料表的執行個體中刪除資料列`System.Data.Linq.Table`類別。 撰寫查詢來尋找您想要刪除的所有資料列，然後將查詢的結果管線傳送`deleteRows`函式。 此程式碼會利用提供的函式引數的部分應用程式的能力。

```fsharp
let deleteRowsFrom (table:Table<_>) rows =
  table.DeleteAllOnSubmit(rows)

query {
  for rows in db.Table3 do
  where (rows.Id > 10)
  select rows
} |> deleteRowsFrom db.Table3

db.DataContext.SubmitChanges()
printfn "Successfully deleted rows with Id greater than 10 in Table3."
```

## <a name="creating-a-test-database"></a>建立測試資料庫
本節說明如何使用此逐步解說中設定測試資料庫。

請注意，是否您改變資料庫，在某些方面，您必須重設型別提供者。 若要重設型別提供者，重建或清除包含型別提供者的專案。


#### <a name="to-create-the-test-database"></a>若要建立測試資料庫

1. 在**伺服器總管**，開啟捷徑功能表**資料連接**] 節點，然後選擇 [**加入連接**。 **加入連接** 對話方塊隨即出現。

2. 在**伺服器名稱**方塊中，指定具有系統管理權限的 SQL Server 執行個體的名稱或您沒有存取伺服器，如果指定 (localdb\v11.0)。 SQL Express LocalDB 提供輕量型的資料庫伺服器供開發及測試您的電腦上。 在 建立新的節點**伺服器總管**下**資料連接**。 如需有關 LocalDB 的詳細資訊，請參閱[逐步解說： 在 Visual Studio 中建立本機資料庫檔案](https://msdn.microsoft.com/library/ms233763.aspx)。

3. 開啟新連接節點的捷徑功能表，然後選取**新查詢**。

4. 複製下列 SQL 指令碼，將它貼到查詢編輯器，然後選擇**Execute**工具列按鈕，或選擇 Ctrl + Shift + E 鍵。

```sql
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO

USE [master];
GO

IF EXISTS (SELECT * FROM sys.databases WHERE name = 'MyDatabase')
  DROP DATABASE MyDatabase;
GO

-- Create the MyDatabase database.
CREATE DATABASE MyDatabase;
GO

-- Specify a simple recovery model 
-- to keep the log growth to a minimum.
ALTER DATABASE MyDatabase 
SET RECOVERY SIMPLE;
GO

USE MyDatabase;
GO

-- Create the Table1 table.
CREATE TABLE [dbo].[Table1] (
  [Id]        INT        NOT NULL,
  [TestData1] INT        NOT NULL,
  [TestData2] FLOAT (53) NOT NULL,
  [Name]      NTEXT      NOT NULL,
  PRIMARY KEY CLUSTERED ([Id] ASC)
);

-- Create the Table2 table.
CREATE TABLE [dbo].[Table2] (
  [Id]        INT        NOT NULL,
  [TestData1] INT        NULL,
  [TestData2] FLOAT (53) NULL,
  [Name]      NTEXT      NOT NULL,
  PRIMARY KEY CLUSTERED ([Id] ASC)
);


-- Create the Table3 table.
CREATE TABLE [dbo].[Table3] (
  [Id]   INT           NOT NULL,
  [Name] NVARCHAR (50) NOT NULL,
  [Data] INT           NOT NULL,
  PRIMARY KEY CLUSTERED ([Id] ASC)
  );
GO

CREATE PROCEDURE [dbo].[Procedure1]
  @param1 int = 0,
  @param2 int
AS
SELECT TestData1 FROM Table1
RETURN 0
GO

USE MyDatabase

-- Insert data into the Table1 table.
INSERT INTO Table1 (Id, TestData1, TestData2, Name)
  VALUES(1, 10, 5.5, 'Testing1');
INSERT INTO Table1 (Id, TestData1, TestData2, Name)
  VALUES(2, 20, -1.2, 'Testing2');

-- Insert data into the Table2 table.
INSERT INTO Table2 (Id, TestData1, TestData2, Name)
  VALUES(1, 10, 5.5, 'Testing1');
INSERT INTO Table2 (Id, TestData1, TestData2, Name)
  VALUES(2, 20, -1.2, 'Testing2');
INSERT INTO Table2 (Id, TestData1, TestData2, Name)
  VALUES(3, NULL, NULL, 'Testing3');

-- Insert data into the Table3 table.
INSERT INTO Table3 (Id, Name, Data)
  VALUES (1, 'Testing1', 10);
INSERT INTO Table3 (Id, Name, Data)
  VALUES (2, 'Testing2', 100);
```


## <a name="see-also"></a>另請參閱
[類型提供者](index.md)

[SqlDataConnection 類型提供者](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqldataconnection-type-provider-%5bfsharp%5d)

[逐步解說： 從 DBML 檔案產生 F # 類型](generating-fsharp-types-from-dbml.md)

[查詢運算式](../../language-reference/query-expressions.md)

[LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)

[SqlMetal.exe&#40;程式碼產生工具&#41;](https://msdn.microsoft.com/library/bb386987)
