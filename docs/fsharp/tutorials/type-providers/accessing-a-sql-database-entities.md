---
title: "逐步解說：使用型別提供者和實體存取 SQL 資料庫 (F#)"
description: "了解如何存取 SQL 資料庫在 F # 3.0 ADO.NET 實體資料模型為基礎的型別的資料。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: dc82a932-5401-4d19-9fb3-92c50d8db514
ms.openlocfilehash: 153050f27ade0152741bdc2d77ab85eefa8418e9
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
---
# <a name="walkthrough-accessing-a-sql-database-by-using-type-providers-and-entities"></a>逐步解說：使用型別提供者和實體存取 SQL 資料庫

> [!NOTE]
本指南針對 F # 3.0 所撰寫，而且會更新。  請參閱 [FSharp.Data](https://fsharp.github.io/FSharp.Data/) 以取得最新的跨平台型別提供者。

> [!NOTE]
應用程式開發介面參考連結將帶您到 MSDN。  docs.microsoft.com API 參考不完整。

這個 F# 3.0 的逐步解說將示範如何根據 ADO.NET 實體資料模型，存取 SQL 資料庫中具類型的資料。 這個逐步解說將示範如何設定 `SqlEntityConnection` F# 類型提供者搭配 SQL 資料庫使用、如何撰寫對資料的查詢、如何在資料庫上呼叫預存程序，以及如何使用某些 ADO.NET Entity Framework 類型和方法更新資料庫。

這個逐步解說將說明下列工作，您應該按照這個逐步解說的順序執行才能成功：


- 建立 School 資料庫
<br />

- 建立並設定 F# 專案
<br />

- 設定類型提供者並連接至實體資料模型
<br />

- 查詢資料庫
<br />

- 更新資料庫
<br />


## <a name="prerequisites"></a>必要條件
您必須能夠存取執行 SQL Server 且可讓您建立資料庫的伺服器，才能完成這些步驟。

## <a name="create-the-school-database"></a>建立 School 資料庫
您可以在任何您具有系統管理存取權限且執行 SQL Server 的伺服器上建立 School 資料庫，或者您也可以使用 LocalDB。


#### <a name="to-create-the-school-database"></a>若要建立 School 資料庫

1. 在**伺服器總管**，開啟捷徑功能表**資料連接**] 節點，然後選擇 [**加入連接**。
<br />  **加入連接** 對話方塊隨即出現。
<br />

2. 在**伺服器名稱**方塊中，指定您具有系統管理權限的 SQL Server 執行個體的名稱或指定 (localdb\v11.0)，如果您沒有伺服器的存取權。
<br />  SQL Server Express LocalDB 提供輕量型的資料庫伺服器，可讓您在電腦上進行開發和測試時使用。 如需有關 LocalDB 的詳細資訊，請參閱[逐步解說： 在 Visual Studio 中建立本機資料庫檔案](https://msdn.microsoft.com/library/ms233763.aspx)。
<br />  在 建立新的節點**伺服器總管**下**資料連接**。
<br />

3. 開啟新連接節點的捷徑功能表，然後選擇**新查詢**。
<br />

4. 開啟[建立 School 範例資料庫](https://msdn.microsoft.com/library/bb399731(v=vs.100).aspx)上 Microsoft 網站，然後複製並貼上將資料庫指令碼會建立 School 資料庫到編輯器視窗。
<br />


## <a name="BKMK_CreateConfigFSProj"> </a>

## <a name="create-and-configure-an-f-project"></a>建立並設定 F# 專案
在這個步驟中，您會建立專案並將進行設定，以便使用類型提供者。


#### <a name="to-create-and-configure-an-f-project"></a>若要建立和設定 F# 專案

1. 關閉先前的專案、 建立另一個專案，並將其命名**SchoolEDM**。
<br />

2. 在**方案總管] 中**，開啟捷徑功能表**參考**，然後選擇 [**加入參考**。
<br />

3. 選擇**Framework**  節點，然後在**Framework**清單中，選擇**System.Data**， **System.Data.Entity**，和**System.Data.Linq**。
<br />

4. 選擇**延伸**] 節點，將參考加入[FSharp.Data.TypeProviders](https://msdn.microsoft.com/library/a858f859-047a-44ab-945b-8731d7a0e6e3)組件，然後選擇 [ **[確定]**按鈕以關閉對話方塊。
<br />

5. 加入下列程式碼可定義內部模組並開啟適當的命名空間。 型別提供者只能將類型插入私用或內部命名空間。
<br />

```fsharp
module internal SchoolEDM

open System.Data.Linq
open System.Data.Entity
open Microsoft.FSharp.Data.TypeProviders
```

6. 在本逐步解說，以互動方式為當做編譯的程式而不是指令碼執行的程式碼，請開啟專案節點的捷徑功能表，選擇 **加入新項目**，加入 F # 指令碼檔，然後加入程式碼中每個步驟的指令碼。 若要載入組件參考，請加入下列各行。
<br />

```fsharp
#r "System.Data.Entity.dll"
#r "FSharp.Data.TypeProviders.dll"
#r "System.Data.Linq.dll"
```

7. 在加入時反白顯示您加入的每一個程式碼區塊，然後選擇 Alt + Enter 鍵以 F# Interactive 執行。
<br />

## <a name="configure-the-type-provider-and-connect-to-the-entity-data-model"></a>設定型別提供者並連接至實體資料模型
在這個步驟中，您將設定具有資料連接的型別提供者，並且取得可讓您使用資料的資料內容。


#### <a name="to-configure-the-type-provider-and-connect-to-the-entity-data-model"></a>若要設定類型提供者並連接至實體資料模型

1. 輸入下列程式碼，依據您先前所建立的實體資料模型設定產生 F# 類型的 `SqlEntityConnection` 類型提供者。 僅使用 SQL 連接字串，而非完整的 EDMX 連接字串。
<br />

```fsharp
type private EntityConnection = SqlEntityConnection<ConnectionString="Server=SERVER\InstanceName;Initial Catalog=School;Integrated Security=SSPI;MultipleActiveResultSets=true",Pluralize = true>
```

  這個動作會設定具有您先前所建立資料庫連接的類型提供者。 當您使用 ADO.NET Entity Framework 時，會需要 `MultipleActiveResultSets` 屬性，因為這個屬性允許在單一連接中，於資料庫上以非同步方式執行多個命令，這種情況在 ADO.NET Entity Framework 程式碼中經常出現。 如需詳細資訊，請參閱 [Multiple Active Result Sets (MARS)](/sql/relational-databases/native-client/features/using-multiple-active-result-sets-mars)。
<br />

2. 取得資料內容，這個物件包含做為屬性的資料庫資料表，以及做為方法的資料庫預存程序和函式。
<br />

```fsharp
let context = EntityConnection.GetDataContext()
```

## <a name="querying-the-database"></a>查詢資料庫
在這個步驟中，您將使用 F# 查詢運算式在資料庫上執行各種查詢。


#### <a name="to-query-the-data"></a>若要查詢資料

- 輸入下列程式碼可查詢實體資料模型中的資料。 請注意 Pluralize = true 的效果，它會將資料庫資料表 Course 變更為 Courses 以及 Person 變更為 People。
<br />

```fsharp
query { 
  for course in context.Courses do
  select course
} |> Seq.iter (fun course -> printfn "%s" course.Title)

query { 
  for person in context.People do
  select person 
} |> Seq.iter (fun person -> printfn "%s %s" person.FirstName person.LastName)

// Add a where clause to filter results.
query {
  for course in context.Courses do
  where (course.DepartmentID = 1)
  select course
} |> Seq.iter (fun course -> printfn "%s" course.Title)

// Join two tables.
query { 
  for course in context.Courses do
  join dept in context.Departments on (course.DepartmentID = dept.DepartmentID)
  select (course, dept.Name) 
} |> Seq.iter (fun (course, deptName) -> printfn "%s %s" course.Title deptName)
```

## <a name="updating-the-database"></a>更新資料庫
若要更新資料庫，您可以使用 Entity Framework 類別和方法。 您可以使用兩種類型的資料內容搭配 SQLEntityConnection 類型提供者。 第一種是 `ServiceTypes.SimpleDataContextTypes.EntityContainer`，這是簡化的資料內容，只包含代表資料庫資料表和資料行的所提供屬性。 第二種是完整資料內容，這是 Entity Framework 類別 `System.Data.Objects.ObjectContext` 的執行個體，其中包含將資料列加入至資料庫的 `System.Data.Objects.ObjectContext.AddObject(System.String,System.Object)` 方法。 Entity Framework 可辨識資料表和資料表之間的關聯性，因此會強制資料庫的一致性。


#### <a name="to-update-the-database"></a>若要更新資料庫

1. 將下列程式碼加入您的程式中。 在這個範例中，您會加入兩個彼此之間具有關聯性的物件，而且會加入一位講師和一份辦公室工作。 資料表 `OfficeAssignments` 包含 `InstructorID` 資料行，該資料行參考 `PersonID` 資料表中的 `Person` 資料行。
<br />

```fsharp
// The full data context
let fullContext = context.DataContext

// A helper function.
let nullable value = new System.Nullable<_>(value)

let addInstructor(lastName, firstName, hireDate, office) =
  let hireDate = DateTime.Parse(hireDate)
  let newPerson = new EntityConnection.ServiceTypes.Person(LastName = lastName,
                                                           FirstName = firstName,
                                                           HireDate = nullable hireDate)
  fullContext.AddObject("People", newPerson)

  let newOffice = new EntityConnection.ServiceTypes.OfficeAssignment(Location = office)

  fullContext.AddObject("OfficeAssignments", newOffice)
  fullContext.CommandTimeout <- nullable 1000
  fullContext.SaveChanges() |> printfn "Saved changes: %d object(s) modified."

addInstructor("Parker", "Darren", "1/1/1998", "41/3720")
```

在您呼叫 `System.Data.Objects.ObjectContext.SaveChanges` 之前，資料庫中不會有任何變更。
<br />

2. 現在將您加入的物件刪除，藉此將資料庫還原至先前的狀態。
<br />

```fsharp
let deleteInstructor(lastName, firstName) =
  query {
    for person in context.People do
    where (person.FirstName = firstName &&
           person.LastName = lastName)
    select person
  } |> Seq.iter (fun person->
                    query {
                      for officeAssignment in context.OfficeAssignments do
                      where (officeAssignment.Person.PersonID = person.PersonID)
                      select officeAssignment
                    } |> Seq.iter (fun officeAssignment -> fullContext.DeleteObject(officeAssignment))

                    fullContext.DeleteObject(person))

  // The call to SaveChanges should be outside of any iteration on the queries.
  fullContext.SaveChanges() |> printfn "Saved changed: %d object(s) modified."

deleteInstructor("Parker", "Darren")
```

>[!WARNING] 
當您使用查詢運算式時，必須記住查詢受到延遲評估限制。 因此，資料庫在任何鏈結評估期間仍會保持開啟可供讀取，例如在 Lambda 運算式區塊中的每一個查詢運算式之後。 所有資料庫作業無論是明確或隱含使用異動，都必須在讀取作業完成之後發生。


## <a name="next-steps"></a>後續步驟
瀏覽其他查詢選項藉由檢視中可用的查詢運算子[查詢運算式](../../language-reference/query-expressions.md)，並同時檢閱[ADO.NET Entity Framework](https://msdn.microsoft.com/library/bb399572)來了解哪些功能時，您可以使用您使用這個型別提供者。


## <a name="see-also"></a>請參閱
[類型提供者](index.md)  
[SqlEntityConnection 類型提供者](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqlentityconnection-type-provider-%5bfsharp%5d)  
[逐步解說： 從 EDMX 結構描述檔案產生 F # 類型](generating-fsharp-types-from-edmx.md)  
[ADO.NET Entity Framework](https://msdn.microsoft.com/library/bb399572)  
[.edmx 檔案概觀](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
[EDM 產生器 &#40;EdmGen.exe &#41;](https://msdn.microsoft.com/library/bb387165)  
