---
title: '開始使用 F # 的命令列工具'
description: '了解如何在 F # 在任何作業系統 （Windows、 macOs 或 Linux） 上使用.NET 核心 CLI 建置簡單的多專案方案。'
ms.date: 03/26/2018
ms.openlocfilehash: 35ec2313742a0b14c92f3de2662a16aff389b214
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562033"
---
# <a name="get-started-with-f-with-the-net-core-cli"></a><span data-ttu-id="c6cff-103">開始使用 F # 和.NET 核心 CLI</span><span class="sxs-lookup"><span data-stu-id="c6cff-103">Get started with F# with the .NET Core CLI</span></span>

<span data-ttu-id="c6cff-104">本文件涵蓋如何您可以在任何作業系統上 （Windows、 macOS 或 Linux） 與.NET Core CLI 開始使用 F #。</span><span class="sxs-lookup"><span data-stu-id="c6cff-104">This article covers how you can get started with F# on any operating system (Windows, macOS, or Linux) with the .NET Core CLI.</span></span> <span data-ttu-id="c6cff-105">它將經歷建置在多專案方案中的使用主控台應用程式會呼叫類別庫。</span><span class="sxs-lookup"><span data-stu-id="c6cff-105">It goes through building a multi-project solution with a class library that is called by a console application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c6cff-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="c6cff-106">Prerequisites</span></span>

<span data-ttu-id="c6cff-107">若要開始，您必須安裝[.NET Core 1.0 或更新版本的 SDK](https://www.microsoft.com/net/download/)。</span><span class="sxs-lookup"><span data-stu-id="c6cff-107">To begin, you must install the [.NET Core SDK 1.0 or later](https://www.microsoft.com/net/download/).</span></span> <span data-ttu-id="c6cff-108">沒有需要解除安裝舊版的.NET Core SDK，因為它支援由並存安裝。</span><span class="sxs-lookup"><span data-stu-id="c6cff-108">There is no need to uninstall a previous version of the .NET Core SDK, as it supports side-by-side installations.</span></span>

<span data-ttu-id="c6cff-109">本文假設您知道如何使用命令列，並以慣用的文字編輯器。</span><span class="sxs-lookup"><span data-stu-id="c6cff-109">This article assumes that you know how to use a command line and have a preferred text editor.</span></span> <span data-ttu-id="c6cff-110">如果您已不使用它， [Visual Studio Code](https://code.visualstudio.com)是絕佳的選項為 F # 的文字編輯器。</span><span class="sxs-lookup"><span data-stu-id="c6cff-110">If you don't already use it, [Visual Studio Code](https://code.visualstudio.com) is a great option as a text editor for F#.</span></span> <span data-ttu-id="c6cff-111">若要取得實用的功能，如 IntelliSense、 更佳語法反白顯示，以及更多，您可以下載[Ionide 延伸](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)。</span><span class="sxs-lookup"><span data-stu-id="c6cff-111">To get awesome features like IntelliSense, better syntax highlighting, and more, you can download the [Ionide Extension](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span>

## <a name="build-a-simple-multi-project-solution"></a><span data-ttu-id="c6cff-112">建置簡單的多專案方案</span><span class="sxs-lookup"><span data-stu-id="c6cff-112">Build a simple multi-project solution</span></span>

<span data-ttu-id="c6cff-113">開啟命令提示字元/終端機，並使用[dotnet 新](../../core/tools/dotnet-new.md)命令以建立新的方案檔稱為`FSNetCore`:</span><span class="sxs-lookup"><span data-stu-id="c6cff-113">Open a command prompt/terminal and use the [dotnet new](../../core/tools/dotnet-new.md) command to create new solution file called `FSNetCore`:</span></span>

```
dotnet new sln -o FSNetCore
```

<span data-ttu-id="c6cff-114">執行前一個命令之後，會產生下列目錄結構：</span><span class="sxs-lookup"><span data-stu-id="c6cff-114">The following directory structure is produced after running the previous command:</span></span>

```
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a><span data-ttu-id="c6cff-115">撰寫類別庫</span><span class="sxs-lookup"><span data-stu-id="c6cff-115">Write a class library</span></span>

<span data-ttu-id="c6cff-116">將目錄變更為*FSNetCore*。</span><span class="sxs-lookup"><span data-stu-id="c6cff-116">Change directories to *FSNetCore*.</span></span>

<span data-ttu-id="c6cff-117">使用`dotnet new`命令，建立類別庫專案中的**src**名為程式庫的資料夾。</span><span class="sxs-lookup"><span data-stu-id="c6cff-117">Use the `dotnet new` command, create a class library project in the **src** folder named Library.</span></span>

```
dotnet new lib -lang F# -o src/Library
```

<span data-ttu-id="c6cff-118">執行前一個命令之後，會產生下列目錄結構：</span><span class="sxs-lookup"><span data-stu-id="c6cff-118">The following directory structure is produced after running the previous command:</span></span>

```
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

<span data-ttu-id="c6cff-119">取代內容`Library.fs`為下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="c6cff-119">Replace the contents of `Library.fs` with the following code:</span></span>

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value (JsonConvert.SerializeObject(value))
```

<span data-ttu-id="c6cff-120">將 Newtonsoft.Json NuGet 套件加入至程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="c6cff-120">Add the Newtonsoft.Json NuGet package to the Library project.</span></span>

```
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

<span data-ttu-id="c6cff-121">新增`Library`專案加入`FSNetCore`方案中使用[dotnet sln 新增](../../core/tools/dotnet-sln.md)命令：</span><span class="sxs-lookup"><span data-stu-id="c6cff-121">Add the `Library` project to the `FSNetCore` solution using the [dotnet sln add](../../core/tools/dotnet-sln.md) command:</span></span>

```
dotnet sln add src/Library/Library.fsproj
```

<span data-ttu-id="c6cff-122">還原 NuGet 相依性，使用`dotnet restore`命令 ([請參閱附註](#dotnet-restore-note)) 並執行`dotnet build`建置專案。</span><span class="sxs-lookup"><span data-stu-id="c6cff-122">Restore the NuGet dependencies using the `dotnet restore` command ([see note](#dotnet-restore-note)) and run `dotnet build` to build the project.</span></span>

### <a name="write-a-console-application-that-consumes-the-class-library"></a><span data-ttu-id="c6cff-123">撰寫使用類別庫的主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="c6cff-123">Write a console application that consumes the class library</span></span>

<span data-ttu-id="c6cff-124">使用`dotnet new`命令，請建立主控台應用程式中的**src**名為應用程式的資料夾。</span><span class="sxs-lookup"><span data-stu-id="c6cff-124">Use the `dotnet new` command, create a console application in the **src** folder named App.</span></span>

```
dotnet new console -lang F# -o src/App
```

<span data-ttu-id="c6cff-125">執行前一個命令之後，會產生下列目錄結構：</span><span class="sxs-lookup"><span data-stu-id="c6cff-125">The following directory structure is produced after running the previous command:</span></span>

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

<span data-ttu-id="c6cff-126">使用以下列程式碼取代`Program.fs`的內容：</span><span class="sxs-lookup"><span data-stu-id="c6cff-126">Replace the contents of the `Program.fs` file with the following code:</span></span>

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

<span data-ttu-id="c6cff-127">將參考加入`Library`專案使用[dotnet 將參考加入](../../core/tools/dotnet-add-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="c6cff-127">Add a reference to the `Library` project using [dotnet add reference](../../core/tools/dotnet-add-reference.md).</span></span>

```
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

<span data-ttu-id="c6cff-128">新增`App`專案加入`FSNetCore`方案中使用`dotnet sln add`命令：</span><span class="sxs-lookup"><span data-stu-id="c6cff-128">Add the `App` project to the `FSNetCore` solution using the `dotnet sln add` command:</span></span>

```
dotnet sln add src/App/App.fsproj
```

<span data-ttu-id="c6cff-129">還原 NuGet 相依性， `dotnet restore` ([請參閱附註](#dotnet-restore-note)) 並執行`dotnet build`建置專案。</span><span class="sxs-lookup"><span data-stu-id="c6cff-129">Restore the NuGet dependencies, `dotnet restore` ([see note](#dotnet-restore-note)) and run `dotnet build` to build the project.</span></span>

<span data-ttu-id="c6cff-130">將目錄切換到`src/App`主控台專案並執行專案傳遞`Hello World`做為引數：</span><span class="sxs-lookup"><span data-stu-id="c6cff-130">Change directory to the `src/App` console project and run the project passing `Hello World` as arguments:</span></span>

```
cd src/App
dotnet run Hello World
```

<span data-ttu-id="c6cff-131">您應該會看到下列結果：</span><span class="sxs-lookup"><span data-stu-id="c6cff-131">You should see the following results:</span></span>

```
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]