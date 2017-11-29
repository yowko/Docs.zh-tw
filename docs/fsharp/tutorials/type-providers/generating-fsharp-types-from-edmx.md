---
title: "逐步解說：從 EDMX 結構描述檔案產生 F# 類型 (F#)"
description: "了解如何建立 F # 類型的資料表示的實體資料模型 (EDM) 在 F # 3.0 中，於.edmx 檔中指定結構描述的位置。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 81adb2eb-625f-4ad8-aeaa-8f672a6d79a2
ms.openlocfilehash: 5c59911f5f880493080ef1838bc015045ce4336a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-generating-f-types-from-an-edmx-schema-file"></a>逐步解說：從 EDMX 結構描述檔案產生 F# 類型

> [!NOTE]
本指南針對 F # 3.0 所撰寫，而且會更新。  請參閱 [FSharp.Data](http://fsharp.github.io/FSharp.Data/) 以取得最新的跨平台型別提供者。

> [!NOTE]
應用程式開發介面參考連結將帶您到 MSDN。  docs.microsoft.com API 參考不完整。

這個 F# 3.0 的逐步解說將說明如何針對實體資料模型 (EDM) 這種在 .edmx 檔案中指定的結構描述所表示的資料建立類型。 這個逐步解說也將示範如何使用 EdmxFile 類型提供者。 在您開始之前，請考慮 SqlEntityConnection 類型提供者是否為更適當的類型提供者選項。 如果您擁有可在專案開發階段連接的線上資料庫，並且不介意在編譯時期指定連接字串，則 SqlEntityConnection 類型提供者會是最適合的選擇。 不過，這種類型提供者也存在限制，它不像 EdmxFile 類型提供者一樣提供許多資料庫功能。 此外，如果您沒有線上資料庫可供使用實體資料模型的資料庫專案使用，您可以使用 .edmx 檔案對資料庫進行編碼。 當您使用 EdmxFile 類型提供者時，F# 編譯器會執行 EdmGen.exe 產生它所提供的類型。

這個逐步解說將說明下列工作，您必須按照這個逐步解說的順序執行才會成功：


- 建立 EDMX 檔案
<br />

- 建立專案
<br />

- 尋找或建立實體資料模型連接字串
<br />

- 設定型別提供者
<br />

- 查詢資料
<br />

- 呼叫預存程序
<br />


## <a name="prerequisites"></a>必要條件

## <a name="creating-an-edmx-file"></a>建立 EDMX 檔案
如果您已經有 EDMX 檔案，就可以略過此步驟。


#### <a name="to-create-an-edmx-file"></a>若要建立 EDMX 檔

- 如果您還沒有 EDMX 檔案，您可以依照本逐步解說步驟中的結尾指示[設定實體資料模型](generating-fsharp-types-from-edmx.md#configuring-the-entity-data-model)。
<br />

## <a name="creating-the-project"></a>建立專案
在這個步驟中，您會建立專案並且在其中加入適當的參考，以便使用 EDMX 類型提供者。


#### <a name="to-create-and-set-up-an-f-project"></a>若要建立並設定 F# 專案

1. 關閉先前的專案，建立另一個專案，並將它命名為 SchoolEDM。
<br />

2. 在**方案總管] 中**，開啟捷徑功能表**參考**，然後選擇 [**加入參考**。
<br />

3. 在**組件**區域中，選擇**Framework**節點。
<br />

4. 在可用組件清單中，選擇  **System.Data.Entity**和**System.Data.Linq**組件，然後選擇 **新增**將參考加入至這些按鈕您的專案的組件。
<br />

5. 在**組件**區域中，選取**延伸**節點。
<br />

6. 在可用的擴充功能清單中，加入 FSharp.Data.TypeProviders 組件的參考。
<br />

7. 加入下列程式碼，開啟適當的命名空間。
<br />

```fsharp
open System.Data.Linq
open System.Data.Entity
open Microsoft.FSharp.Data.TypeProviders
```

## <a name="finding-or-creating-the-connection-string-for-the-entity-data-model"></a>尋找或建立實體資料模型的連接字串
實體資料模型的連接字串 (EDMX 連接字串) 不只包括資料庫提供者的連接字串，還包含其他資訊。 例如，簡單的 SQL Server 資料庫的 EDMX 連接字串類似下列程式碼。

```fsharp
let edmConnectionString = "metadata=res://*/;provider=System.Data.SqlClient;Provider Connection String='Server=SERVER\Instance;Initial Catalog=DatabaseName;Integrated Security=SSPI;'"
```

如需 EDMX 連接字串的詳細資訊，請參閱[連接字串](https://msdn.microsoft.com/library/ms254494.aspx)。


#### <a name="to-find-or-create-the-connection-string-for-the-entity-data-model"></a>若要尋找或建立實體資料模型的連接字串

1. EDMX 連接字串可能不容易手動產生，因此用程式設計方式產生可以為您節省時間。 如果您知道 EDMX 連接字串，就可以略過這個步驟，直接在下一個步驟中使用該字串即可。 否則，請使用下列程式碼從您所提供的資料庫連接字串中產生 EDMX 連接字串。
<br />

```fsharp
open System
open System.Data
open System.Data.SqlClient
open System.Data.EntityClient
open System.Data.Metadata.Edm

let getEDMConnection(dbConnectionString) =
  let dbConnection = new SqlConnection(dbConnectionString)
  let resourceArray = [| "res://*/" |]
  let assemblyList = [| System.Reflection.Assembly.GetCallingAssembly() |]
  let metaData = MetadataWorkspace(resourceArray, assemblyList)
  new EntityConnection(metaData, dbConnection)
```

## <a name="configuring-the-type-provider"></a>設定類型提供者
在這個步驟中，您將建立並設定包含 EDMX 連接字串的類型提供者，然後為 .edmx 檔案中定義的結構描述產生類型。


#### <a name="to-configure-the-type-provider-and-generate-types"></a>若要設定類型提供者和產生類型

1. 將您在這個逐步解說的第一個步驟中產生的 .edmx 檔案複製到專案資料夾。
<br />

2. 開啟專案節點，在 F # 專案的捷徑功能表選擇 **加入現有項目**，然後選擇.edmx 檔案，將它加入至您的專案。
<br />

3. 輸入下列程式碼來啟用 .edmx 檔案的型別提供者。 取代*伺服器*\** 執行個體正在執行的 SQL Server 和您的執行個體的名稱用於此逐步解說的第一個步驟中在.edmx 檔案的名稱伺服器的名稱。
<br />

```fsharp
type edmx = EdmxFile<"Model1.edmx", ResolutionFolder = @"<path-tofolder-that-containsyour.edmx-file>">

use edmConnection =
  getEDMConnection("Data Source=SERVER\instance;Initial Catalog=School;Integrated Security=true;")
use context = new edmx.SchoolModel.SchoolEntities(edmConnection)
```

## <a name="querying-the-data"></a>查詢資料
在這個步驟中，您會使用 F# 查詢運算式查詢資料庫。


#### <a name="to-query-the-data"></a>若要查詢資料

- 輸入下列程式碼可查詢實體資料模型中的資料。
<br />

```fsharp
query { 
  for course in context.Courses do
  select course 
} |> Seq.iter (fun course -> printfn "%s" course.Title)

query { 
  for person in context.Person do
  select person 
} |> Seq.iter (fun person -> printfn "%s %s" person.FirstName person.LastName)

// Add a where clause to filter results
query { 
  for course in context.Courses do
  where (course.DepartmentID = 1)
  select course
} |> Seq.iter (fun course -> printfn "%s" course.Title)

// Join two tables
query { 
  for course in context.Courses do
  join dept in context.Departments on (course.DepartmentID = dept.DepartmentID)
  select (course, dept.Name) 
} |> Seq.iter (fun (course, deptName) -> printfn "%s %s" course.Title deptName)
```

## <a name="calling-a-stored-procedure"></a>呼叫預存程序
您可以使用 EDMX 型別提供者呼叫預存程序。 在下列程序中，School 資料庫包含預存程序， **UpdatePerson**，這會更新記錄時，指定新資料行值。 您可以使用這個預存程序，因為它會做為 DataContext 類型中的方法公開。


#### <a name="to-call-a-stored-procedure"></a>若要呼叫預存程序

- 加入下列程式碼以更新記錄。
<br />

```fsharp
// Call a stored procedure.
let nullable value = new System.Nullable<_>(value)

// Assume now that you must correct someone's hire date.
// Throw an exception if more than one matching person is found.
let changeHireDate(lastName, firstName, hireDate) =

  query { 
    for person in context.People do
    where (person.LastName = lastName &&
           person.FirstName = firstName)
    exactlyOne 
  } |> (fun person ->
            context.UpdatePerson(nullable person.PersonID, person.LastName, person.FirstName, nullable hireDate, person.EnrollmentDate))

changeHireDate("Abercrombie", "Kim", DateTime.Parse("1/12/1998"))
|> printfn "Result: %d"
```

如果成功，則結果會是 1。 請注意， **exactlyOne**以確保只有一個會傳回結果，否則擲回例外狀況是用於查詢運算式。 此外，若要更輕鬆地使用可為 null 的值，您可以使用簡單**可為 null**函式定義於這個程式碼來建立從一般值為 null 的值。

<br />

## <a name="configuring-the-entity-data-model"></a>設定實體資料模型
只有在您想要知道如何從資料庫產生完整的實體資料模型，但是沒有可用來測試的資料庫時，才完成這個程序。


#### <a name="to-configure-the-entity-data-model"></a>若要設定實體資料模型

1. 在功能表列上選擇  **SQL**， **TRANSACT-SQL 編輯器**，**新查詢**建立資料庫。 出現提示時，指定您的資料庫伺服器和執行個體。
<br />

2. 複製並貼上建立學生的資料庫，將資料庫指令碼的內容中所述[Entity Framework 文件](http://msdn.microsoft.com/data/JJ614587.aspx)資料開發人員中心。
<br />

3. 選擇三角形符號的工具列按鈕，或選擇 Ctrl + Q 鍵以執行 SQL 指令碼。
<br />

4. 在**伺服器總管**，開啟捷徑功能表**資料連接**，選擇**加入連接**，然後輸入資料庫伺服器的執行個體名稱的名稱及 School 資料庫。
<br />

5. 建立 C# 或 Visual Basic 主控台應用程式專案，開啟其捷徑功能表，選擇**加入新項目**，然後選擇  **ADO.NET 實體資料模型**。
<br />  [實體資料模型精靈] 隨即開啟。 您可以使用這個精靈選擇要如何建立實體資料模型。
<br />

6. 在下**選擇模型內容**，選取**從資料庫產生**核取方塊。
<br />

7. 在下一頁中，選擇新建立的 School 資料庫做為資料連接。
<br />  這個連接應該類似 **&lt;servername&gt;。&lt;instancename&gt;。School.dbo**。
<br />

8. 將實體連接字串複製到 [剪貼簿]，因為該字串對後續程序可能很重要。
<br />

9. 請確定核取方塊以將實體連接字串儲存**App.Config**檔案已選取，並在文字方塊中，可幫助您尋找該連接字串更新版本中，視記的字串值。
<br />

10. 在下一個頁面上，選擇**資料表**和**預存程序和函式**。
<br />  藉由選擇這些最上層節點，就可以選擇所有資料表、預存程序和函式。 如有需要，您也可以個別選擇這些項目。
<br />

11. 確定已選取其他設定的核取方塊。
<br />  第一個**將化或單數化產生的物件名稱**核取方塊，指出是否將單數形式變更為複數形式，以符合命名代表資料庫資料表物件的慣例。 **在模型中包含外部索引鍵資料行**核取方塊決定是否要包含用途為聯結至其他欄位中的資料庫結構描述產生的物件類型的欄位。 第三個核取方塊表示，是否在模型中包含預存程序和函式。
<br />

12. 選取**完成** 按鈕，產生的.edmx 檔案，包含實體資料模型為基礎的 School 資料庫。
<br />  檔案、 **Model1.edmx**，加入至您的專案，而且資料庫圖表會出現。
<br />

13. 在功能表列上選擇 **檢視**，**其他視窗**，**實體資料模型瀏覽器**檢視模型的所有詳細資料或**實體資料模型對應詳細資料**開啟一個視窗，顯示產生的物件模型如何對應資料庫資料表和資料行。
<br />


## <a name="next-steps"></a>後續步驟
藉由查看可用的查詢運算子，如下所示瀏覽其他查詢[查詢運算式](../../language-reference/query-expressions.md)。


## <a name="see-also"></a>另請參閱
[類型提供者](index.md)

[EdmxFile 類型提供者](https://msdn.microsoft.com/visualfsharpdocs/conceptual/edmxfile-type-provider-%5bfsharp%5d)

[逐步解說：使用型別提供者和實體存取 SQL 資料庫](accessing-a-sql-database-entities.md)

[Entity Framework](http://msdn.microsoft.com/data/ef)

[.edmx 檔案概觀](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)

[EDM 產生器 &#40;EdmGen.exe &#41;](https://msdn.microsoft.com/library/bb387165)

