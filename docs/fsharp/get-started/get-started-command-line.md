---
title: '使用命令列工具開始使用 F #'
description: '瞭解如何使用任何作業系統上的 .NET Core CLI （ (Windows、macOS 或 Linux) ），在 F # 上建立簡單的多專案解決方案。'
ms.date: 08/15/2020
ms.openlocfilehash: f890e31fe8c665874dc3034aebfae32e38b9031a
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739911"
---
# <a name="get-started-with-f-with-the-net-core-cli"></a>使用 .NET Core CLI 開始使用 F #

本文涵蓋如何在任何作業系統上開始使用 F #， (Windows、macOS 或 Linux) 與 .NET Core CLI。 它會使用由主控台應用程式呼叫的類別庫，來建立多專案的方案。

## <a name="prerequisites"></a>先決條件

若要開始，您必須安裝最新的 [.NET Core SDK](https://dotnet.microsoft.com/download)。

本文假設您知道如何使用命令列，並擁有慣用的文字編輯器。 如果您還沒有使用它， [Visual Studio Code](get-started-vscode.md) 是適用于 F # 文字編輯器的絕佳選項。

## <a name="build-a-simple-multi-project-solution"></a>建立簡單的多專案方案

開啟命令提示字元/終端機，並使用 [dotnet new](../../core/tools/dotnet-new.md) 命令建立名為的新方案檔 `FSNetCore` ：

```dotnetcli
dotnet new sln -o FSNetCore
```

執行上述命令之後，會產生下列目錄結構：

```console
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a>撰寫類別庫

將目錄變更為 *FSNetCore*。

使用 `dotnet new` 命令，在 **src** 資料夾中建立名為 library 的類別庫專案。

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

以下列程式碼取代的內容 `Library.fs` ：

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    let json = JsonConvert.SerializeObject(value)
    $"I used to be {value} but now I'm {json} thanks to JSON.NET!"
```

將 NuGet 套件上的 Newtonsoft.Js新增至程式庫專案。

```dotnetcli
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

`Library` `FSNetCore` 使用[dotnet .sln add](../../core/tools/dotnet-sln.md)命令將專案新增至方案：

```dotnetcli
dotnet sln add src/Library/Library.fsproj
```

執行 `dotnet build` 以建立專案。 建立時，將會還原未解析的相依性。

### <a name="write-a-console-application-that-consumes-the-class-library"></a>撰寫使用類別庫的主控台應用程式

使用 `dotnet new` 命令，在名為 App 的 **src** 資料夾中建立主控台應用程式。

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

    for arg in argv do
        let value = getJsonNetJson arg
        printfn $"{value}"

    0 // return an integer exit code
```

`Library`使用[dotnet 加入參考](../../core/tools/dotnet-add-reference.md)加入專案的參考。

```dotnetcli
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

`App`使用命令將專案新增至 `FSNetCore` 方案 `dotnet sln add` ：

```dotnetcli
dotnet sln add src/App/App.fsproj
```

還原 NuGet 相依性， `dotnet restore` 並執行 `dotnet build` 以建立專案。

將目錄變更為 `src/App` 主控台專案並執行專案傳遞 `Hello World` 做為引數：

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

接下來，請查看 [F #](../tour.md) 的教學課程，以深入瞭解不同的 f # 功能。
