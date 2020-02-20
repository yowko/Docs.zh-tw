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
# <a name="get-started-with-f-with-the-net-core-cli"></a><span data-ttu-id="98751-103">開始F#使用 .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="98751-103">Get started with F# with the .NET Core CLI</span></span>

<span data-ttu-id="98751-104">本文說明如何在任何作業系統（Windows、 F# MacOS 或 Linux）上使用 .NET Core CLI 來開始使用。</span><span class="sxs-lookup"><span data-stu-id="98751-104">This article covers how you can get started with F# on any operating system (Windows, macOS, or Linux) with the .NET Core CLI.</span></span> <span data-ttu-id="98751-105">它會使用主控台應用程式所呼叫的類別庫，來建立多專案方案。</span><span class="sxs-lookup"><span data-stu-id="98751-105">It goes through building a multi-project solution with a class library that is called by a console application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="98751-106">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="98751-106">Prerequisites</span></span>

<span data-ttu-id="98751-107">若要開始，您必須安裝最新的[.NET Core SDK](https://dotnet.microsoft.com/download)。</span><span class="sxs-lookup"><span data-stu-id="98751-107">To begin, you must install the latest [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>

<span data-ttu-id="98751-108">本文假設您知道如何使用命令列，並具有慣用的文字編輯器。</span><span class="sxs-lookup"><span data-stu-id="98751-108">This article assumes that you know how to use a command line and have a preferred text editor.</span></span> <span data-ttu-id="98751-109">如果您還沒有使用它， [Visual Studio Code](get-started-vscode.md)是的文字編輯器的絕佳選項F#。</span><span class="sxs-lookup"><span data-stu-id="98751-109">If you don't already use it, [Visual Studio Code](get-started-vscode.md) is a great option as a text editor for F#.</span></span>

## <a name="build-a-simple-multi-project-solution"></a><span data-ttu-id="98751-110">建立簡單的多專案解決方案</span><span class="sxs-lookup"><span data-stu-id="98751-110">Build a simple multi-project solution</span></span>

<span data-ttu-id="98751-111">開啟命令提示字元/終端機，並使用[dotnet new](../../core/tools/dotnet-new.md)命令來建立名為 `FSNetCore`的新方案檔：</span><span class="sxs-lookup"><span data-stu-id="98751-111">Open a command prompt/terminal and use the [dotnet new](../../core/tools/dotnet-new.md) command to create new solution file called `FSNetCore`:</span></span>

```dotnetcli
dotnet new sln -o FSNetCore
```

<span data-ttu-id="98751-112">執行上述命令之後，會產生下列目錄結構：</span><span class="sxs-lookup"><span data-stu-id="98751-112">The following directory structure is produced after running the previous command:</span></span>

```console
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a><span data-ttu-id="98751-113">撰寫類別庫</span><span class="sxs-lookup"><span data-stu-id="98751-113">Write a class library</span></span>

<span data-ttu-id="98751-114">將目錄變更為*FSNetCore*。</span><span class="sxs-lookup"><span data-stu-id="98751-114">Change directories to *FSNetCore*.</span></span>

<span data-ttu-id="98751-115">使用 [`dotnet new`] 命令，在**src**資料夾中建立名為 library 的類別庫專案。</span><span class="sxs-lookup"><span data-stu-id="98751-115">Use the `dotnet new` command, create a class library project in the **src** folder named Library.</span></span>

```dotnetcli
dotnet new classlib -lang "F#" -o src/Library
```

<span data-ttu-id="98751-116">執行上述命令之後，會產生下列目錄結構：</span><span class="sxs-lookup"><span data-stu-id="98751-116">The following directory structure is produced after running the previous command:</span></span>

```console
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

<span data-ttu-id="98751-117">將 `Library.fs` 的內容取代為下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="98751-117">Replace the contents of `Library.fs` with the following code:</span></span>

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value (JsonConvert.SerializeObject(value))
```

<span data-ttu-id="98751-118">將 Newtonsoft NuGet 套件新增至程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="98751-118">Add the Newtonsoft.Json NuGet package to the Library project.</span></span>

```dotnetcli
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

<span data-ttu-id="98751-119">使用[dotnet sln add](../../core/tools/dotnet-sln.md)命令，將 `Library` 專案新增至 `FSNetCore` 解決方案：</span><span class="sxs-lookup"><span data-stu-id="98751-119">Add the `Library` project to the `FSNetCore` solution using the [dotnet sln add](../../core/tools/dotnet-sln.md) command:</span></span>

```dotnetcli
dotnet sln add src/Library/Library.fsproj
```

<span data-ttu-id="98751-120">執行 `dotnet build` 以建立專案。</span><span class="sxs-lookup"><span data-stu-id="98751-120">Run `dotnet build` to build the project.</span></span> <span data-ttu-id="98751-121">建立時，將會還原無法解析的相依性。</span><span class="sxs-lookup"><span data-stu-id="98751-121">Unresolved dependencies will be restored when building.</span></span>

### <a name="write-a-console-application-that-consumes-the-class-library"></a><span data-ttu-id="98751-122">撰寫使用類別庫的主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="98751-122">Write a console application that consumes the class library</span></span>

<span data-ttu-id="98751-123">使用 `dotnet new` 命令，在**src**資料夾中建立名為 App 的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="98751-123">Use the `dotnet new` command, create a console application in the **src** folder named App.</span></span>

```dotnetcli
dotnet new console -lang "F#" -o src/App
```

<span data-ttu-id="98751-124">執行上述命令之後，會產生下列目錄結構：</span><span class="sxs-lookup"><span data-stu-id="98751-124">The following directory structure is produced after running the previous command:</span></span>

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

<span data-ttu-id="98751-125">將 `Program.fs` 檔案的內容取代為下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="98751-125">Replace the contents of the `Program.fs` file with the following code:</span></span>

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

<span data-ttu-id="98751-126">使用 dotnet 的 [[加入參考](../../core/tools/dotnet-add-reference.md)]，將參考加入至 `Library` 專案。</span><span class="sxs-lookup"><span data-stu-id="98751-126">Add a reference to the `Library` project using [dotnet add reference](../../core/tools/dotnet-add-reference.md).</span></span>

```dotnetcli
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

<span data-ttu-id="98751-127">使用 `dotnet sln add` 命令，將 `App` 專案新增至 `FSNetCore` 解決方案：</span><span class="sxs-lookup"><span data-stu-id="98751-127">Add the `App` project to the `FSNetCore` solution using the `dotnet sln add` command:</span></span>

```dotnetcli
dotnet sln add src/App/App.fsproj
```

<span data-ttu-id="98751-128">還原 NuGet 相依性，`dotnet restore` 並執行 `dotnet build` 以建立專案。</span><span class="sxs-lookup"><span data-stu-id="98751-128">Restore the NuGet dependencies, `dotnet restore` and run `dotnet build` to build the project.</span></span>

<span data-ttu-id="98751-129">將目錄變更為 `src/App` 主控台專案，並執行傳遞 `Hello World` 做為引數的專案：</span><span class="sxs-lookup"><span data-stu-id="98751-129">Change directory to the `src/App` console project and run the project passing `Hello World` as arguments:</span></span>

```dotnetcli
cd src/App
dotnet run Hello World
```

<span data-ttu-id="98751-130">您應該會看見下列結果：</span><span class="sxs-lookup"><span data-stu-id="98751-130">You should see the following results:</span></span>

```console
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```

## <a name="next-steps"></a><span data-ttu-id="98751-131">後續步驟</span><span class="sxs-lookup"><span data-stu-id="98751-131">Next steps</span></span>

<span data-ttu-id="98751-132">接下來，請參閱[的F#導覽](../tour.md)以深入瞭解不同F#的功能。</span><span class="sxs-lookup"><span data-stu-id="98751-132">Next, check out the [Tour of F#](../tour.md) to learn more about different F# features.</span></span>
