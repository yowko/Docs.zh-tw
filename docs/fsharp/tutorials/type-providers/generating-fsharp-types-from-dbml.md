---
title: "逐步解說：從 DBML 檔案產生 F# 類型 (F#)"
description: "了解如何從 F # 3.0 中的資料庫建立 F # 類型的資料，當您有編碼.dbml 檔案中的結構描述資訊。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 6fbb6ccc-248f-4226-95e9-f6f99541dbe4
ms.openlocfilehash: 50e0a2bb6378c82b5c6425589da8a982b5fc496a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-generating-f-types-from-a-dbml-file"></a>逐步解說：從 DBML 檔案產生 F# 類型

> [!NOTE]
本指南針對 F # 3.0 所撰寫，而且會更新。  請參閱 [FSharp.Data](http://fsharp.github.io/FSharp.Data/) 以取得最新的跨平台型別提供者。

> [!NOTE]
應用程式開發介面參考連結將帶您到 MSDN。  docs.microsoft.com API 參考不完整。

這個 F # 3.0 的逐步解說描述如何從資料庫建立的資料類型，當您編碼.dbml 檔案中的結構描述資訊時。 LINQ to SQL 會使用這種檔案格式來表示資料庫結構描述。 您可以使用物件關聯式 (O/R) 的設計工具，Visual Studio 中產生 LINQ to SQL 結構描述檔案。 如需詳細資訊，請參閱[O/R 設計工具概觀](https://msdn.microsoft.com/library/bb384511.aspx)和[LINQ to SQL 中的程式碼產生](https://msdn.microsoft.com/library/bb386976)。

資料庫標記語言 」 (DBML) 型別提供者可讓您撰寫程式碼，會使用基礎資料庫結構描述，而不需要您在編譯時期指定靜態連接字串的類型。 可以是如果您需要完成的應用程式將使用不同的資料庫，不同的認證或不同的連接字串比您用來開發應用程式可能很有用。 如果您有直接的資料庫連接，您可以在編譯時期使用，而且這是相同的資料庫和最終建置應用程式中使用的認證，您也可以使用 SQLDataConnection 類型提供者。 如需詳細資訊，請參閱[逐步解說： 存取 SQL 資料庫所使用的型別提供者](accessing-a-sql-database.md)。

這個逐步解說將說明下列工作。 它們應該依此順序逐步解說中，才能成功完成：


- 建立.dbml 檔案
<br />

- 建立並設定 F # 專案
<br />

- 設定類型提供者和產生的型別
<br />

- 查詢資料庫
<br />


## <a name="prerequisites"></a>必要條件

## <a name="creating-a-dbml-file"></a>建立.dbml 檔案
如果您沒有上測試資料庫，建立一個在底部的指示[逐步解說： 存取 SQL 資料庫所使用的型別提供者](accessing-a-sql-database.md)。 如果您遵循這些指示時，您將建立名為 MyDatabase 包含幾個簡單的資料表和預存程序，在您的 SQL Server 上的資料庫。

如果您已經有.dbml 檔，您可以跳至區段中，**建立並設定 F # 專案**。 否則，您可以建立指定現有的 SQL database 的.dbml 檔案，並使用命令列工具 SqlMetal.exe。


#### <a name="to-create-a-dbml-file-by-using-sqlmetalexe"></a>若要建立使用 SqlMetal.exe.dbml 檔案

1. 開啟**開發人員命令提示字元**。
<br />

2. 請確定您輸入有存取權 SqlMetal.exe`SqlMetal.exe /?`在命令提示字元。 SqlMetal.exe 通常安裝在**Microsoft Sdk**資料夾中的**Program Files**或**Program Files (x86)**。
<br />

3. SqlMetal.exe 執行下列命令列選項。 取代的適當路徑來取代`c:\destpath`若要建立.dbml 檔案，並插入適當的值為資料庫伺服器，執行個體名稱和資料庫名稱。
<br />

```
  SqlMetal.exe /sprocs /dbml:C:\destpath\MyDatabase.dbml /server:SERVER\INSTANCE /database:MyDatabase
```

>[!NOTE]
如果 SqlMetal.exe 無法建立檔案，因為權限問題，請將目前目錄變更到您具有寫入權限的資料夾。


4. 您也可以查看其他可用的命令列選項。 比方說，是如果您想要檢視和 SQL 函式包含在產生的型別，您可以使用的選項。 如需詳細資訊，請參閱[SqlMetal.exe &#40;程式碼產生工具 &#41;](https://msdn.microsoft.com/library/bb386987).
<br />


## <a name="creating-and-setting-up-an-f-project"></a>建立並設定 F # 專案
在此步驟中，您會建立專案，並加入適當的參考，以使用 DBML 型別提供者。


#### <a name="to-create-and-set-up-an-f-project"></a>若要建立並設定 F# 專案

1. 將新的 F # 主控台應用程式專案加入至方案。
<br />

2. 在**方案總管] 中**，開啟捷徑功能表**參考**，然後選擇 [**加入參考**。
<br />

3. 在**組件**區域中，選擇**Framework** ] 節點，然後在可用組件清單中，選擇 [ **System.Data**和**System.Data.Linq**組件。
<br />

4. 在**組件**區域中，選擇**延伸**，然後在可用組件清單中，選擇  **FSharp.Data.TypeProviders**。
<br />

5. 選擇**確定**按鈕，將這些組件的參考加入至您的專案。
<br />

6. (選擇性) 將您在上一個步驟中建立的.dbml 檔案複製和貼上的主要專案資料夾中的檔案。 此資料夾包含專案檔 (.fsproj) 和程式碼檔案。 在功能表列上選擇 **專案**，**加入現有項目**，然後指定.dbml 檔案，將它加入至您的專案。 如果您完成這些步驟，您可以省略 ResolutionFolder 靜態參數，在下一個步驟。
<br />

## <a name="configuring-the-type-provider"></a>設定類型提供者
在本節中，您會建立型別提供者，並從.dbml 檔案中所述的結構描述產生類型。


#### <a name="to-configure-the-type-provider-and-generate-the-types"></a>若要設定型別提供者和產生類型

- 將開啟的程式碼加入**TypeProviders**命名空間和您想要使用的.dbml 檔案的類型提供者具現化。 如果您將.dbml 檔案加入您的專案時，您可以省略 ResolutionFolder 靜態參數。
<br />

```fsharp
open Microsoft.FSharp.Data.TypeProviders


type dbml = DbmlFile<"MyDatabase.dbml", ResolutionFolder = @"<path-to-folder-that-contains-.dbml-file>">

// This connection string can be specified at run time.
let connectionString = "Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;"
let dataContext = new dbml.Mydatabase(connectionString)
```

提供存取所有產生的型別 DataContext 類型，並且會繼承自`System.Data.Linq.DataContext`。 DbmlFile 類型提供者有各種可以設定的靜態參數。 例如，您可以使用 DataContext 類型不同的名稱，藉由指定`DataContext=MyDataContext`。 在此情況下，您的程式碼類似下列的範例：
<br />

```fsharp
open Microsoft.FSharp.Data.TypeProviders


type dbml = DbmlFile<"MyDatabase.dbml", ContextTypeName = "MyDataContext">

// This connection string can be specified at run time.
let connectionString = "Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;"
let db = new dbml.MyDataContext(connectionString)
```

## <a name="querying-the-database"></a>查詢資料庫
在本節中，您可以使用 F # 查詢運算式查詢資料庫。


#### <a name="to-query-the-data"></a>若要查詢資料

- 加入程式碼來查詢資料庫。
<br />

```fsharp
  query {
    for row in db.Table1 do
    where (row.TestData1 > 2)
    select row
  } |> Seq.iter (fun row -> printfn "%d %s" row.TestData1 row.Name)
```

## <a name="next-steps"></a>後續步驟
您可以繼續使用其他查詢的運算式，或從資料內容取得資料庫連接和執行一般 ADO.NET 資料的作業。 如需其他步驟，請參閱章節 「 查詢資料 」 之後[逐步解說： 存取 SQL 資料庫所使用的型別提供者](accessing-a-sql-database.md)。


## <a name="see-also"></a>另請參閱
[DbmlFile 類型提供者](https://msdn.microsoft.com/visualfsharpdocs/conceptual/dbmlfile-type-provider-%5bfsharp%5d)

[類型提供者](index.md)

[逐步解說：使用型別提供者存取 SQL 資料庫](accessing-a-sql-database.md)

[SqlMetal.exe &#40;程式碼產生工具 &#41;](https://msdn.microsoft.com/library/bb386987)

[查詢運算式](../../language-reference/query-expressions.md)
