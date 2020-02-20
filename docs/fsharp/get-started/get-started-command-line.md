---
title: 使用命令列F#工具開始使用
description: 瞭解如何在任何作業系統（Windows、macOS 或 Linux F# ）上使用 .NET Core CLI，建立簡單的多專案解決方案。
ms.date: 03/26/2018
ms.openlocfilehash: 6f67314f49150e20b18734f21f24daa3ce856922
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77504139"
---
# <a name="get-started-with-f-with-the-net-core-cli"></a>開始F#使用 .NET Core CLI

本文說明如何在任何作業系統（Windows、 F# MacOS 或 Linux）上使用 .NET Core CLI 來開始使用。 它會使用主控台應用程式所呼叫的類別庫，來建立多專案方案。

## <a name="prerequisites"></a>Prerequisites

若要開始，您必須安裝最新的[.NET Core SDK](https://dotnet.microsoft.com/download)。

本文假設您知道如何使用命令列，並具有慣用的文字編輯器。 如果您還沒有使用它， [Visual Studio Code](get-started-vscode.md)是的文字編輯器的絕佳選項F#。

## <a name="build-a-simple-multi-project-solution"></a>建立簡單的多專案解決方案

開啟命令提示字元/終端機，並使用[dotnet new](../../core/tools/dotnet-new.md)命令來建立名為 `FSNetCore`的新方案檔：

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

使用 [`dotnet new`] 命令，在**src**資料夾中建立名為 library 的類別庫專案。

```dotnetcli
dotnet new classlib -lang "F#" -o src/Library
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

將 `Library.fs` 的內容取代為下列程式碼：

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

使用[dotnet sln add](../../core/tools/dotnet-sln.md)命令，將 `Library` 專案新增至 `FSNetCore` 解決方案：

```dotnetcli
dotnet sln add src/Library/Library.fsproj
```

執行 `dotnet build` 以建立專案。 建立時，將會還原無法解析的相依性。

### <a name="write-a-console-application-that-consumes-the-class-library"></a>撰寫使用類別庫的主控台應用程式

使用 `dotnet new` 命令，在**src**資料夾中建立名為 App 的主控台應用程式。

```dotnetcli
dotnet new console -lang "F#" -o src/App
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

將 `Program.fs` 檔案的內容取代為下列程式碼：

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

使用 dotnet 的 [[加入參考](../../core/tools/dotnet-add-reference.md)]，將參考加入至 `Library` 專案。

```dotnetcli
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

使用 `dotnet sln add` 命令，將 `App` 專案新增至 `FSNetCore` 解決方案：

```dotnetcli
dotnet sln add src/App/App.fsproj
```

還原 NuGet 相依性，`dotnet restore` 並執行 `dotnet build` 以建立專案。

將目錄變更為 `src/App` 主控台專案，並執行傳遞 `Hello World` 做為引數的專案：

```dotnetcli
cd src/App
dotnet run Hello World
```

您應該會看見下列結果：

```console
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```

## <a name="next-steps"></a>後續步驟

接下來，請參閱[的F#導覽](../tour.md)以深入瞭解不同F#的功能。
