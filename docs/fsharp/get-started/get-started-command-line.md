---
title: 使用命令列F#工具開始使用
description: '了解如何在 F # 在任何作業系統 （Windows、 macOs 或 Linux） 上使用.NET Core CLI 建置簡單的多專案方案'
ms.date: 03/26/2018
ms.openlocfilehash: f9177e653273e5a2191407c4fb22343ded11fece
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117919"
---
# <a name="get-started-with-f-with-the-net-core-cli"></a>開始使用 F # 和.NET Core CLI

本文說明如何在任何作業系統（Windows、 F# MacOS 或 Linux）上使用 .NET Core CLI 來開始使用。 它會使用主控台應用程式所呼叫的類別庫，來建立多專案方案。

## <a name="prerequisites"></a>必要條件

若要開始，您必須安裝最新的[.NET Core SDK](https://dotnet.microsoft.com/download)。

本文假設您知道如何使用命令列，並具有慣用的文字編輯器。 如果您還沒有使用它， [Visual Studio Code](get-started-vscode.md)是的文字編輯器的絕佳選項F#。

## <a name="build-a-simple-multi-project-solution"></a>建立簡單的多專案解決方案

開啟命令提示字元/終端機，並使用[dotnet new](../../core/tools/dotnet-new.md)命令來建立名`FSNetCore`為的新方案檔：

```dotnetcli
dotnet new sln -o FSNetCore
```

執行上述命令之後，會產生下列目錄結構：

```console
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a>撰寫類別庫

將目錄變更為*FSNetCore*。

使用命令，在 src 資料夾中建立名為 library 的類別庫專案。 `dotnet new`

```dotnetcli
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

將的內容`Library.fs`取代為下列程式碼：

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value (JsonConvert.SerializeObject(value))
```

將 Newtonsoft NuGet 套件新增至程式庫專案。

```dotnetcli
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

使用 dotnet [sln add](../../core/tools/dotnet-sln.md)命令`FSNetCore`將專案新增至方案：`Library`

```dotnetcli
dotnet sln add src/Library/Library.fsproj
```

執行`dotnet build`以建立專案。 建立時，將會還原無法解析的相依性。

### <a name="write-a-console-application-that-consumes-the-class-library"></a>撰寫使用類別庫的主控台應用程式

使用命令，在 src 資料夾中建立名為 App 的主控台應用程式。 `dotnet new`

```dotnetcli
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

使用 dotnet 的`Library` [[加入參考](../../core/tools/dotnet-add-reference.md)]，將參考加入至專案。

```dotnetcli
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

`FSNetCore` `App` 使用`dotnet sln add`命令將專案新增至方案：

```dotnetcli
dotnet sln add src/App/App.fsproj
```

還原 NuGet 相依性， `dotnet restore`然後執行`dotnet build`以建立專案。

將目錄變更為`src/App`主控台專案，並執行做為`Hello World`引數傳遞的專案：

```console
cd src/App
dotnet run Hello World
```

您應該會看到下列結果:

```console
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```

## <a name="next-steps"></a>後續步驟

接下來，請參閱[的F#導覽](../tour.md)以深入瞭解不同F#的功能。
