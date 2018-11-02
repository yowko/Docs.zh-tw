---
title: '使用命令列工具開始使用 F #'
description: '了解如何在 F # 在任何作業系統 （Windows、 macOs 或 Linux） 上使用.NET Core CLI 建置簡單的多專案方案'
ms.date: 03/26/2018
ms.openlocfilehash: 8a82970f33c8bbe1b8cdd8fb6499b59b16d3cbf3
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "45673905"
---
# <a name="get-started-with-f-with-the-net-core-cli"></a>開始使用 F # 和.NET Core CLI

本文涵蓋如何您可以開始使用 F # 在任何作業系統上 （Windows、 macOS 或 Linux） 使用.NET Core CLI。 它會經歷建置主控台應用程式會呼叫類別庫的多專案方案。

## <a name="prerequisites"></a>必要條件

若要開始，您必須安裝最新[.NET Core SDK](https://www.microsoft.com/net/download/)。

本文假設您知道如何使用命令列，並以慣用的文字編輯器。 如果您尚未使用的話[Visual Studio Code](get-started-vscode.md)是以 F # 的文字編輯器的絕佳選項。

## <a name="build-a-simple-multi-project-solution"></a>建置簡單的多專案解決方案

開啟命令提示字元/終端機，並使用[dotnet 新](../../core/tools/dotnet-new.md)命令來建立新的方案檔案，稱為`FSNetCore`:

```console
dotnet new sln -o FSNetCore
```

執行上述命令之後，會產生下列目錄結構：

```console
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a>撰寫的類別程式庫

將目錄變更為*FSNetCore*。

使用`dotnet new`命令，建立類別庫專案中的**src**名為程式庫的資料夾。

```console
dotnet new classlib -lang F# -o src/Library
```

執行上述命令之後，會產生下列目錄結構：

```console
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

內容取代`Library.fs`為下列程式碼：

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value (JsonConvert.SerializeObject(value))
```

將 Newtonsoft.Json NuGet 套件新增至程式庫專案。

```console
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

新增`Library`專案加入`FSNetCore`解決方案使用[dotnet sln 新增](../../core/tools/dotnet-sln.md)命令：

```console
dotnet sln add src/Library/Library.fsproj
```

執行`dotnet build`來建置專案。 建置時，將會還原無法解析的相依性。

### <a name="write-a-console-application-that-consumes-the-class-library"></a>撰寫主控台應用程式使用的類別庫

使用`dotnet new`命令，建立主控台應用程式**src**名為應用程式的資料夾。

```console
dotnet new console -lang F# -o src/App
```

執行上述命令之後，會產生下列目錄結構：

```console
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

將參考加入`Library`使用的專案[dotnet 新增參考](../../core/tools/dotnet-add-reference.md)。

```console
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

新增`App`專案加入`FSNetCore`解決方案使用`dotnet sln add`命令：

```console
dotnet sln add src/App/App.fsproj
```

還原 NuGet 相依性`dotnet restore`([請參閱附註](#dotnet-restore-note)) 並執行`dotnet build`來建置專案。

將目錄變更為`src/App`主控台專案，然後執行專案傳遞`Hello World`做為引數：

```console
cd src/App
dotnet run Hello World
```

您應該會看到下列結果：

```console
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```

## <a name="next-steps"></a>後續步驟

接下來，請參閱[的 F # 教學課程](../tour.md)若要深入了解不同的 F # 功能。
