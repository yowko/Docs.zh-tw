---
title: 使用命令列F#工具開始使用
description: '了解如何在 F # 在任何作業系統 （Windows、 macOs 或 Linux） 上使用.NET Core CLI 建置簡單的多專案方案'
ms.date: 03/26/2018
ms.openlocfilehash: 1376b6b5384f380c06a96cdc568ad108de8a6e5f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855831"
---
# <a name="get-started-with-f-with-the-net-core-cli"></a><span data-ttu-id="136ff-103">開始使用 F # 和.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="136ff-103">Get started with F# with the .NET Core CLI</span></span>

<span data-ttu-id="136ff-104">本文說明如何在任何作業系統（Windows、 F# MacOS 或 Linux）上使用 .NET Core CLI 來開始使用。</span><span class="sxs-lookup"><span data-stu-id="136ff-104">This article covers how you can get started with F# on any operating system (Windows, macOS, or Linux) with the .NET Core CLI.</span></span> <span data-ttu-id="136ff-105">它會使用主控台應用程式所呼叫的類別庫，來建立多專案方案。</span><span class="sxs-lookup"><span data-stu-id="136ff-105">It goes through building a multi-project solution with a class library that is called by a console application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="136ff-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="136ff-106">Prerequisites</span></span>

<span data-ttu-id="136ff-107">若要開始，您必須安裝最新的[.NET Core SDK](https://dotnet.microsoft.com/download)。</span><span class="sxs-lookup"><span data-stu-id="136ff-107">To begin, you must install the latest [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>

<span data-ttu-id="136ff-108">本文假設您知道如何使用命令列，並具有慣用的文字編輯器。</span><span class="sxs-lookup"><span data-stu-id="136ff-108">This article assumes that you know how to use a command line and have a preferred text editor.</span></span> <span data-ttu-id="136ff-109">如果您還沒有使用它， [Visual Studio Code](get-started-vscode.md)是的文字編輯器的絕佳選項F#。</span><span class="sxs-lookup"><span data-stu-id="136ff-109">If you don't already use it, [Visual Studio Code](get-started-vscode.md) is a great option as a text editor for F#.</span></span>

## <a name="build-a-simple-multi-project-solution"></a><span data-ttu-id="136ff-110">建立簡單的多專案解決方案</span><span class="sxs-lookup"><span data-stu-id="136ff-110">Build a simple multi-project solution</span></span>

<span data-ttu-id="136ff-111">開啟命令提示字元/終端機，並使用[dotnet new](../../core/tools/dotnet-new.md)命令來建立名`FSNetCore`為的新方案檔：</span><span class="sxs-lookup"><span data-stu-id="136ff-111">Open a command prompt/terminal and use the [dotnet new](../../core/tools/dotnet-new.md) command to create new solution file called `FSNetCore`:</span></span>

```console
dotnet new sln -o FSNetCore
```

<span data-ttu-id="136ff-112">執行上述命令之後，會產生下列目錄結構：</span><span class="sxs-lookup"><span data-stu-id="136ff-112">The following directory structure is produced after running the previous command:</span></span>

```console
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a><span data-ttu-id="136ff-113">撰寫類別庫</span><span class="sxs-lookup"><span data-stu-id="136ff-113">Write a class library</span></span>

<span data-ttu-id="136ff-114">將目錄變更為*FSNetCore*。</span><span class="sxs-lookup"><span data-stu-id="136ff-114">Change directories to *FSNetCore*.</span></span>

<span data-ttu-id="136ff-115">使用命令，在 src 資料夾中建立名為 library 的類別庫專案。 `dotnet new`</span><span class="sxs-lookup"><span data-stu-id="136ff-115">Use the `dotnet new` command, create a class library project in the **src** folder named Library.</span></span>

```console
dotnet new classlib -lang F# -o src/Library
```

<span data-ttu-id="136ff-116">執行上述命令之後，會產生下列目錄結構：</span><span class="sxs-lookup"><span data-stu-id="136ff-116">The following directory structure is produced after running the previous command:</span></span>

```console
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

<span data-ttu-id="136ff-117">將的內容`Library.fs`取代為下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="136ff-117">Replace the contents of `Library.fs` with the following code:</span></span>

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value (JsonConvert.SerializeObject(value))
```

<span data-ttu-id="136ff-118">將 Newtonsoft NuGet 套件新增至程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="136ff-118">Add the Newtonsoft.Json NuGet package to the Library project.</span></span>

```console
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

<span data-ttu-id="136ff-119">使用 dotnet [sln add](../../core/tools/dotnet-sln.md)命令`FSNetCore`將專案新增至方案：`Library`</span><span class="sxs-lookup"><span data-stu-id="136ff-119">Add the `Library` project to the `FSNetCore` solution using the [dotnet sln add](../../core/tools/dotnet-sln.md) command:</span></span>

```console
dotnet sln add src/Library/Library.fsproj
```

<span data-ttu-id="136ff-120">執行`dotnet build`以建立專案。</span><span class="sxs-lookup"><span data-stu-id="136ff-120">Run `dotnet build` to build the project.</span></span> <span data-ttu-id="136ff-121">建立時，將會還原無法解析的相依性。</span><span class="sxs-lookup"><span data-stu-id="136ff-121">Unresolved dependencies will be restored when building.</span></span>

### <a name="write-a-console-application-that-consumes-the-class-library"></a><span data-ttu-id="136ff-122">撰寫使用類別庫的主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="136ff-122">Write a console application that consumes the class library</span></span>

<span data-ttu-id="136ff-123">使用命令，在 src 資料夾中建立名為 App 的主控台應用程式。 `dotnet new`</span><span class="sxs-lookup"><span data-stu-id="136ff-123">Use the `dotnet new` command, create a console application in the **src** folder named App.</span></span>

```console
dotnet new console -lang F# -o src/App
```

<span data-ttu-id="136ff-124">執行上述命令之後，會產生下列目錄結構：</span><span class="sxs-lookup"><span data-stu-id="136ff-124">The following directory structure is produced after running the previous command:</span></span>

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

<span data-ttu-id="136ff-125">使用以下列程式碼取代`Program.fs`的內容：</span><span class="sxs-lookup"><span data-stu-id="136ff-125">Replace the contents of the `Program.fs` file with the following code:</span></span>

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

<span data-ttu-id="136ff-126">使用 dotnet 的`Library` [[加入參考](../../core/tools/dotnet-add-reference.md)]，將參考加入至專案。</span><span class="sxs-lookup"><span data-stu-id="136ff-126">Add a reference to the `Library` project using [dotnet add reference](../../core/tools/dotnet-add-reference.md).</span></span>

```console
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

<span data-ttu-id="136ff-127">`FSNetCore` `App` 使用`dotnet sln add`命令將專案新增至方案：</span><span class="sxs-lookup"><span data-stu-id="136ff-127">Add the `App` project to the `FSNetCore` solution using the `dotnet sln add` command:</span></span>

```console
dotnet sln add src/App/App.fsproj
```

<span data-ttu-id="136ff-128">還原 NuGet 相依性， `dotnet restore`然後執行`dotnet build`以建立專案。</span><span class="sxs-lookup"><span data-stu-id="136ff-128">Restore the NuGet dependencies, `dotnet restore` and run `dotnet build` to build the project.</span></span>

<span data-ttu-id="136ff-129">將目錄變更為`src/App`主控台專案，並執行做為`Hello World`引數傳遞的專案：</span><span class="sxs-lookup"><span data-stu-id="136ff-129">Change directory to the `src/App` console project and run the project passing `Hello World` as arguments:</span></span>

```console
cd src/App
dotnet run Hello World
```

<span data-ttu-id="136ff-130">您應該會看到下列結果:</span><span class="sxs-lookup"><span data-stu-id="136ff-130">You should see the following results:</span></span>

```console
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```

## <a name="next-steps"></a><span data-ttu-id="136ff-131">後續步驟</span><span class="sxs-lookup"><span data-stu-id="136ff-131">Next steps</span></span>

<span data-ttu-id="136ff-132">接下來，請參閱[的F#導覽](../tour.md)以深入瞭解不同F#的功能。</span><span class="sxs-lookup"><span data-stu-id="136ff-132">Next, check out the [Tour of F#](../tour.md) to learn more about different F# features.</span></span>
