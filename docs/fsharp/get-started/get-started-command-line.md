---
title: '使用命令列工具開始使用 F #'
description: '了解如何在 F # 在任何作業系統 （Windows、 macOs 或 Linux） 上使用.NET Core CLI 建置簡單的多專案方案'
ms.date: 03/26/2018
ms.openlocfilehash: 8a82970f33c8bbe1b8cdd8fb6499b59b16d3cbf3
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2018
ms.locfileid: "45569771"
---
# <a name="get-started-with-f-with-the-net-core-cli"></a><span data-ttu-id="04cf8-103">開始使用 F # 和.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="04cf8-103">Get started with F# with the .NET Core CLI</span></span>

<span data-ttu-id="04cf8-104">本文涵蓋如何您可以開始使用 F # 在任何作業系統上 （Windows、 macOS 或 Linux） 使用.NET Core CLI。</span><span class="sxs-lookup"><span data-stu-id="04cf8-104">This article covers how you can get started with F# on any operating system (Windows, macOS, or Linux) with the .NET Core CLI.</span></span> <span data-ttu-id="04cf8-105">它會經歷建置主控台應用程式會呼叫類別庫的多專案方案。</span><span class="sxs-lookup"><span data-stu-id="04cf8-105">It goes through building a multi-project solution with a class library that is called by a console application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="04cf8-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="04cf8-106">Prerequisites</span></span>

<span data-ttu-id="04cf8-107">若要開始，您必須安裝最新[.NET Core SDK](https://www.microsoft.com/net/download/)。</span><span class="sxs-lookup"><span data-stu-id="04cf8-107">To begin, you must install the latest [.NET Core SDK](https://www.microsoft.com/net/download/).</span></span>

<span data-ttu-id="04cf8-108">本文假設您知道如何使用命令列，並以慣用的文字編輯器。</span><span class="sxs-lookup"><span data-stu-id="04cf8-108">This article assumes that you know how to use a command line and have a preferred text editor.</span></span> <span data-ttu-id="04cf8-109">如果您尚未使用的話[Visual Studio Code](get-started-vscode.md)是以 F # 的文字編輯器的絕佳選項。</span><span class="sxs-lookup"><span data-stu-id="04cf8-109">If you don't already use it, [Visual Studio Code](get-started-vscode.md) is a great option as a text editor for F#.</span></span>

## <a name="build-a-simple-multi-project-solution"></a><span data-ttu-id="04cf8-110">建置簡單的多專案解決方案</span><span class="sxs-lookup"><span data-stu-id="04cf8-110">Build a simple multi-project solution</span></span>

<span data-ttu-id="04cf8-111">開啟命令提示字元/終端機，並使用[dotnet 新](../../core/tools/dotnet-new.md)命令來建立新的方案檔案，稱為`FSNetCore`:</span><span class="sxs-lookup"><span data-stu-id="04cf8-111">Open a command prompt/terminal and use the [dotnet new](../../core/tools/dotnet-new.md) command to create new solution file called `FSNetCore`:</span></span>

```console
dotnet new sln -o FSNetCore
```

<span data-ttu-id="04cf8-112">執行上述命令之後，會產生下列目錄結構：</span><span class="sxs-lookup"><span data-stu-id="04cf8-112">The following directory structure is produced after running the previous command:</span></span>

```console
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a><span data-ttu-id="04cf8-113">撰寫的類別程式庫</span><span class="sxs-lookup"><span data-stu-id="04cf8-113">Write a class library</span></span>

<span data-ttu-id="04cf8-114">將目錄變更為*FSNetCore*。</span><span class="sxs-lookup"><span data-stu-id="04cf8-114">Change directories to *FSNetCore*.</span></span>

<span data-ttu-id="04cf8-115">使用`dotnet new`命令，建立類別庫專案中的**src**名為程式庫的資料夾。</span><span class="sxs-lookup"><span data-stu-id="04cf8-115">Use the `dotnet new` command, create a class library project in the **src** folder named Library.</span></span>

```console
dotnet new classlib -lang F# -o src/Library
```

<span data-ttu-id="04cf8-116">執行上述命令之後，會產生下列目錄結構：</span><span class="sxs-lookup"><span data-stu-id="04cf8-116">The following directory structure is produced after running the previous command:</span></span>

```console
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

<span data-ttu-id="04cf8-117">內容取代`Library.fs`為下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="04cf8-117">Replace the contents of `Library.fs` with the following code:</span></span>

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value (JsonConvert.SerializeObject(value))
```

<span data-ttu-id="04cf8-118">將 Newtonsoft.Json NuGet 套件新增至程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="04cf8-118">Add the Newtonsoft.Json NuGet package to the Library project.</span></span>

```console
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

<span data-ttu-id="04cf8-119">新增`Library`專案加入`FSNetCore`解決方案使用[dotnet sln 新增](../../core/tools/dotnet-sln.md)命令：</span><span class="sxs-lookup"><span data-stu-id="04cf8-119">Add the `Library` project to the `FSNetCore` solution using the [dotnet sln add](../../core/tools/dotnet-sln.md) command:</span></span>

```console
dotnet sln add src/Library/Library.fsproj
```

<span data-ttu-id="04cf8-120">執行`dotnet build`來建置專案。</span><span class="sxs-lookup"><span data-stu-id="04cf8-120">Run `dotnet build` to build the project.</span></span> <span data-ttu-id="04cf8-121">建置時，將會還原無法解析的相依性。</span><span class="sxs-lookup"><span data-stu-id="04cf8-121">Unresolved dependencies will be restored when building.</span></span>

### <a name="write-a-console-application-that-consumes-the-class-library"></a><span data-ttu-id="04cf8-122">撰寫主控台應用程式使用的類別庫</span><span class="sxs-lookup"><span data-stu-id="04cf8-122">Write a console application that consumes the class library</span></span>

<span data-ttu-id="04cf8-123">使用`dotnet new`命令，建立主控台應用程式**src**名為應用程式的資料夾。</span><span class="sxs-lookup"><span data-stu-id="04cf8-123">Use the `dotnet new` command, create a console application in the **src** folder named App.</span></span>

```console
dotnet new console -lang F# -o src/App
```

<span data-ttu-id="04cf8-124">執行上述命令之後，會產生下列目錄結構：</span><span class="sxs-lookup"><span data-stu-id="04cf8-124">The following directory structure is produced after running the previous command:</span></span>

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

<span data-ttu-id="04cf8-125">使用以下列程式碼取代`Program.fs`的內容：</span><span class="sxs-lookup"><span data-stu-id="04cf8-125">Replace the contents of the `Program.fs` file with the following code:</span></span>

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

<span data-ttu-id="04cf8-126">將參考加入`Library`使用的專案[dotnet 新增參考](../../core/tools/dotnet-add-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="04cf8-126">Add a reference to the `Library` project using [dotnet add reference](../../core/tools/dotnet-add-reference.md).</span></span>

```console
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

<span data-ttu-id="04cf8-127">新增`App`專案加入`FSNetCore`解決方案使用`dotnet sln add`命令：</span><span class="sxs-lookup"><span data-stu-id="04cf8-127">Add the `App` project to the `FSNetCore` solution using the `dotnet sln add` command:</span></span>

```console
dotnet sln add src/App/App.fsproj
```

<span data-ttu-id="04cf8-128">還原 NuGet 相依性`dotnet restore`([請參閱附註](#dotnet-restore-note)) 並執行`dotnet build`來建置專案。</span><span class="sxs-lookup"><span data-stu-id="04cf8-128">Restore the NuGet dependencies, `dotnet restore` ([see note](#dotnet-restore-note)) and run `dotnet build` to build the project.</span></span>

<span data-ttu-id="04cf8-129">將目錄變更為`src/App`主控台專案，然後執行專案傳遞`Hello World`做為引數：</span><span class="sxs-lookup"><span data-stu-id="04cf8-129">Change directory to the `src/App` console project and run the project passing `Hello World` as arguments:</span></span>

```console
cd src/App
dotnet run Hello World
```

<span data-ttu-id="04cf8-130">您應該會看到下列結果：</span><span class="sxs-lookup"><span data-stu-id="04cf8-130">You should see the following results:</span></span>

```console
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```

## <a name="next-steps"></a><span data-ttu-id="04cf8-131">後續步驟</span><span class="sxs-lookup"><span data-stu-id="04cf8-131">Next steps</span></span>

<span data-ttu-id="04cf8-132">接下來，請參閱[的 F # 教學課程](../tour.md)若要深入了解不同的 F # 功能。</span><span class="sxs-lookup"><span data-stu-id="04cf8-132">Next, check out the [Tour of F#](../tour.md) to learn more about different F# features.</span></span>
