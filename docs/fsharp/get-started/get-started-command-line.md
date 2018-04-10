---
title: '開始使用 F # 的命令列工具'
description: '了解如何在 F # 在任何作業系統 （Windows、 macOs 或 Linux） 上使用.NET 核心 CLI 建置簡單的多專案方案。'
author: cartermp
ms.author: phcart
ms.date: 03/26/2018
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.openlocfilehash: e48e1291bbe91da0d9ca2adbb08662bd106c8fb4
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="get-started-with-f-with-the-net-core-cli"></a>開始使用 F # 和.NET 核心 CLI

本文件涵蓋如何您可以在任何作業系統上 （Windows、 macOS 或 Linux） 與.NET Core CLI 開始使用 F #。 它將經歷建置在多專案方案中的使用主控台應用程式會呼叫類別庫。

## <a name="prerequisites"></a>必要條件

若要開始，您必須安裝[.NET Core 1.0 或更新版本的 SDK](https://www.microsoft.com/net/download/)。 沒有需要解除安裝舊版的.NET Core SDK，因為它支援由並存安裝。

本文假設您知道如何使用命令列，並以慣用的文字編輯器。 如果您已不使用它， [Visual Studio Code](https://code.visualstudio.com)是絕佳的選項為 F # 的文字編輯器。 若要取得實用的功能，如 IntelliSense、 更佳語法反白顯示，以及更多，您可以下載[Ionide 延伸](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)。

## <a name="build-a-simple-multi-project-solution"></a>建置簡單的多專案方案

開啟命令提示字元/終端機，並使用[dotnet 新](../../core/tools/dotnet-new.md)命令以建立新的方案檔稱為`FSNetCore`:

```
dotnet new sln -o FSNetCore
```

執行前一個命令之後，會產生下列目錄結構：

```
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a>撰寫類別庫

將目錄變更為*FSNetCore*。

使用`dotnet new`命令，建立類別庫專案中的**src**名為程式庫的資料夾。

```
dotnet new lib -lang F# -o src/Library
```

執行前一個命令之後，會產生下列目錄結構：

```
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

取代內容`Library.fs`為下列程式碼：

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value (JsonConvert.SerializeObject(value))
```

將 Newtonsoft.Json NuGet 套件加入至程式庫專案。

```
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

新增`Library`專案加入`FSNetCore`方案中使用[dotnet sln 新增](../../core/tools/dotnet-sln.md)命令：

```
dotnet sln add src/Library/Library.fsproj
```

還原 NuGet 相依性，使用`dotnet restore`命令 ([請參閱附註](#dotnet-restore-note)) 並執行`dotnet build`建置專案。

### <a name="write-a-console-application-that-consumes-the-class-library"></a>撰寫使用類別庫的主控台應用程式

使用`dotnet new`命令，請建立主控台應用程式中的**src**名為應用程式的資料夾。

```
dotnet new console -lang F# -o src/App
```

執行前一個命令之後，會產生下列目錄結構：

```
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        ├── App
        │   ├── App.fsproj
        │   ├── Program.fs
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

使用以下列程式碼取代`Program.fs`的內容：

```fsharp
open System
open Library

[<EntryPoint>]
let main argv =
    printfn "Nice command-line arguments! Here's what JSON.NET has to say about them:"

    argv
    |> Array.map getJsonNetJson
    |> Array.iter (printfn "%s")

    0 // return an integer exit code
```

將參考加入`Library`專案使用[dotnet 將參考加入](../../core/tools/dotnet-add-reference.md)。

```
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

新增`App`專案加入`FSNetCore`方案中使用`dotnet sln add`命令：

```
dotnet sln add src/App/App.fsproj
```

還原 NuGet 相依性， `dotnet restore` ([請參閱附註](#dotnet-restore-note)) 並執行`dotnet build`建置專案。

將目錄切換到`src/App`主控台專案並執行專案傳遞`Hello World`做為引數：

```
cd src/App
dotnet run Hello World
```

您應該會看到下列結果：

```
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]