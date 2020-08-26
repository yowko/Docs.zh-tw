---
title: '使用命令列工具開始使用 F #'
description: '瞭解如何使用任何作業系統上的 .NET Core CLI （ (Windows、macOS 或 Linux) ），在 F # 上建立簡單的多專案解決方案。'
ms.date: 08/15/2020
ms.openlocfilehash: e652b66337a3122de8e6bd4d62d86fb6082b759d
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811986"
---
# <a name="get-started-with-f-with-the-net-core-cli"></a><span data-ttu-id="e1cd6-103">使用 .NET Core CLI 開始使用 F #</span><span class="sxs-lookup"><span data-stu-id="e1cd6-103">Get started with F# with the .NET Core CLI</span></span>

<span data-ttu-id="e1cd6-104">本文涵蓋如何在任何作業系統上開始使用 F #， (Windows、macOS 或 Linux) 與 .NET Core CLI。</span><span class="sxs-lookup"><span data-stu-id="e1cd6-104">This article covers how you can get started with F# on any operating system (Windows, macOS, or Linux) with the .NET Core CLI.</span></span> <span data-ttu-id="e1cd6-105">它會使用由主控台應用程式呼叫的類別庫，來建立多專案的方案。</span><span class="sxs-lookup"><span data-stu-id="e1cd6-105">It goes through building a multi-project solution with a class library that is called by a console application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e1cd6-106">先決條件</span><span class="sxs-lookup"><span data-stu-id="e1cd6-106">Prerequisites</span></span>

<span data-ttu-id="e1cd6-107">若要開始，您必須安裝最新的 [.NET Core SDK](https://dotnet.microsoft.com/download)。</span><span class="sxs-lookup"><span data-stu-id="e1cd6-107">To begin, you must install the latest [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>

<span data-ttu-id="e1cd6-108">本文假設您知道如何使用命令列，並擁有慣用的文字編輯器。</span><span class="sxs-lookup"><span data-stu-id="e1cd6-108">This article assumes that you know how to use a command line and have a preferred text editor.</span></span> <span data-ttu-id="e1cd6-109">如果您還沒有使用它， [Visual Studio Code](get-started-vscode.md) 是適用于 F # 文字編輯器的絕佳選項。</span><span class="sxs-lookup"><span data-stu-id="e1cd6-109">If you don't already use it, [Visual Studio Code](get-started-vscode.md) is a great option as a text editor for F#.</span></span>

## <a name="build-a-simple-multi-project-solution"></a><span data-ttu-id="e1cd6-110">建立簡單的多專案方案</span><span class="sxs-lookup"><span data-stu-id="e1cd6-110">Build a simple multi-project solution</span></span>

<span data-ttu-id="e1cd6-111">開啟命令提示字元/終端機，並使用 [dotnet new](../../core/tools/dotnet-new.md) 命令建立名為的新方案檔 `FSNetCore` ：</span><span class="sxs-lookup"><span data-stu-id="e1cd6-111">Open a command prompt/terminal and use the [dotnet new](../../core/tools/dotnet-new.md) command to create new solution file called `FSNetCore`:</span></span>

```dotnetcli
dotnet new sln -o FSNetCore
```

<span data-ttu-id="e1cd6-112">執行上述命令之後，會產生下列目錄結構：</span><span class="sxs-lookup"><span data-stu-id="e1cd6-112">The following directory structure is produced after running the previous command:</span></span>

```console
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a><span data-ttu-id="e1cd6-113">撰寫類別庫</span><span class="sxs-lookup"><span data-stu-id="e1cd6-113">Write a class library</span></span>

<span data-ttu-id="e1cd6-114">將目錄變更為 *FSNetCore*。</span><span class="sxs-lookup"><span data-stu-id="e1cd6-114">Change directories to *FSNetCore*.</span></span>

<span data-ttu-id="e1cd6-115">使用 `dotnet new` 命令，在 **src** 資料夾中建立名為 library 的類別庫專案。</span><span class="sxs-lookup"><span data-stu-id="e1cd6-115">Use the `dotnet new` command, create a class library project in the **src** folder named Library.</span></span>

```dotnetcli
dotnet new classlib -lang "F#" -o src/Library
```

<span data-ttu-id="e1cd6-116">執行上述命令之後，會產生下列目錄結構：</span><span class="sxs-lookup"><span data-stu-id="e1cd6-116">The following directory structure is produced after running the previous command:</span></span>

```console
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

<span data-ttu-id="e1cd6-117">以下列程式碼取代的內容 `Library.fs` ：</span><span class="sxs-lookup"><span data-stu-id="e1cd6-117">Replace the contents of `Library.fs` with the following code:</span></span>

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    let json = JsonConvert.SerializeObject(value)
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value json
```

<span data-ttu-id="e1cd6-118">將 NuGet 套件上的 Newtonsoft.Js新增至程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="e1cd6-118">Add the Newtonsoft.Json NuGet package to the Library project.</span></span>

```dotnetcli
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

<span data-ttu-id="e1cd6-119">`Library` `FSNetCore` 使用[dotnet .sln add](../../core/tools/dotnet-sln.md)命令將專案新增至方案：</span><span class="sxs-lookup"><span data-stu-id="e1cd6-119">Add the `Library` project to the `FSNetCore` solution using the [dotnet sln add](../../core/tools/dotnet-sln.md) command:</span></span>

```dotnetcli
dotnet sln add src/Library/Library.fsproj
```

<span data-ttu-id="e1cd6-120">執行 `dotnet build` 以建立專案。</span><span class="sxs-lookup"><span data-stu-id="e1cd6-120">Run `dotnet build` to build the project.</span></span> <span data-ttu-id="e1cd6-121">建立時，將會還原未解析的相依性。</span><span class="sxs-lookup"><span data-stu-id="e1cd6-121">Unresolved dependencies will be restored when building.</span></span>

### <a name="write-a-console-application-that-consumes-the-class-library"></a><span data-ttu-id="e1cd6-122">撰寫使用類別庫的主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="e1cd6-122">Write a console application that consumes the class library</span></span>

<span data-ttu-id="e1cd6-123">使用 `dotnet new` 命令，在名為 App 的 **src** 資料夾中建立主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="e1cd6-123">Use the `dotnet new` command, create a console application in the **src** folder named App.</span></span>

```dotnetcli
dotnet new console -lang "F#" -o src/App
```

<span data-ttu-id="e1cd6-124">執行上述命令之後，會產生下列目錄結構：</span><span class="sxs-lookup"><span data-stu-id="e1cd6-124">The following directory structure is produced after running the previous command:</span></span>

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

<span data-ttu-id="e1cd6-125">將 `Program.fs` 檔案的內容取代為下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="e1cd6-125">Replace the contents of the `Program.fs` file with the following code:</span></span>

```fsharp
open System
open Library

[<EntryPoint>]
let main argv =
    printfn "Nice command-line arguments! Here's what JSON.NET has to say about them:"

    for arg in argv do
        let value = getJsonNetJson arg
        printfn "%s" value

    0 // return an integer exit code
```

<span data-ttu-id="e1cd6-126">`Library`使用[dotnet 加入參考](../../core/tools/dotnet-add-reference.md)加入專案的參考。</span><span class="sxs-lookup"><span data-stu-id="e1cd6-126">Add a reference to the `Library` project using [dotnet add reference](../../core/tools/dotnet-add-reference.md).</span></span>

```dotnetcli
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

<span data-ttu-id="e1cd6-127">`App`使用命令將專案新增至 `FSNetCore` 方案 `dotnet sln add` ：</span><span class="sxs-lookup"><span data-stu-id="e1cd6-127">Add the `App` project to the `FSNetCore` solution using the `dotnet sln add` command:</span></span>

```dotnetcli
dotnet sln add src/App/App.fsproj
```

<span data-ttu-id="e1cd6-128">還原 NuGet 相依性， `dotnet restore` 並執行 `dotnet build` 以建立專案。</span><span class="sxs-lookup"><span data-stu-id="e1cd6-128">Restore the NuGet dependencies, `dotnet restore` and run `dotnet build` to build the project.</span></span>

<span data-ttu-id="e1cd6-129">將目錄變更為 `src/App` 主控台專案並執行專案傳遞 `Hello World` 做為引數：</span><span class="sxs-lookup"><span data-stu-id="e1cd6-129">Change directory to the `src/App` console project and run the project passing `Hello World` as arguments:</span></span>

```dotnetcli
cd src/App
dotnet run Hello World
```

<span data-ttu-id="e1cd6-130">您應該會看見下列結果：</span><span class="sxs-lookup"><span data-stu-id="e1cd6-130">You should see the following results:</span></span>

```console
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```

## <a name="next-steps"></a><span data-ttu-id="e1cd6-131">後續步驟</span><span class="sxs-lookup"><span data-stu-id="e1cd6-131">Next steps</span></span>

<span data-ttu-id="e1cd6-132">接下來，請查看 [F #](../tour.md) 的教學課程，以深入瞭解不同的 f # 功能。</span><span class="sxs-lookup"><span data-stu-id="e1cd6-132">Next, check out the [Tour of F#](../tour.md) to learn more about different F# features.</span></span>
