---
title: "開始使用 F # 的命令列工具"
description: "跨平台.NET Core CLI 與了解如何使用 F # 在 Windows、 MacOS （Linux） 的任何作業系統上。"
keywords: "Visual F#, F#, 函式程式設計, .NET, .NET Core"
author: cartermp
ms.author: phcart
ms.date: 06/14/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 615db1ec-6ef3-4de2-bae6-4586affa9771
ms.openlocfilehash: 4820a8a306bd478429b497a8b7c70ff170c1c655
ms.sourcegitcommit: d095094e942eedf09530ea5636fbaf9029853027
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2017
---
# <a name="get-started-with-f-with-the-net-core-cli"></a><span data-ttu-id="31131-104">開始使用 F # 和.NET 核心 CLI</span><span class="sxs-lookup"><span data-stu-id="31131-104">Get started with F# with the .NET Core CLI</span></span>

<span data-ttu-id="31131-105">本文件涵蓋如何您可以使用 F # 的.NET Core CLI 開始 （Windows、 macOS 或 Linux） 的任何作業系統上。</span><span class="sxs-lookup"><span data-stu-id="31131-105">This article covers how you can get started on any OS (Windows, macOS, or Linux) by using F# with the .NET Core CLI.</span></span> <span data-ttu-id="31131-106">它將會經歷建置在多專案方案中的使用主控台應用程式會呼叫類別庫。</span><span class="sxs-lookup"><span data-stu-id="31131-106">It will go through building a multi-project solution with a Class Library that is called by a Console Application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="31131-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="31131-107">Prerequisites</span></span>

<span data-ttu-id="31131-108">若要開始，您必須安裝[.NET Core 1.0 或更新版本的 SDK](https://dot.net/core)。</span><span class="sxs-lookup"><span data-stu-id="31131-108">To begin, you must install the [.NET Core SDK 1.0 or later](https://dot.net/core).</span></span> <span data-ttu-id="31131-109">沒有需要解除安裝舊版的.NET Core SDK，因為它支援由並存安裝。</span><span class="sxs-lookup"><span data-stu-id="31131-109">There is no need to uninstall a previous version of the .NET Core SDK, as it supports side-by-side installations.</span></span>

<span data-ttu-id="31131-110">本文假設您知道如何使用命令列，並以慣用的文字編輯器。</span><span class="sxs-lookup"><span data-stu-id="31131-110">This article assumes that you know how to use a command line and have a preferred text editor.</span></span> <span data-ttu-id="31131-111">如果您已不使用它， [Visual Studio Code](https://code.visualstudio.com)是絕佳的選項為 F # 的文字編輯器。</span><span class="sxs-lookup"><span data-stu-id="31131-111">If you don't already use it, [Visual Studio Code](https://code.visualstudio.com) is a great option as a text editor for F#.</span></span> <span data-ttu-id="31131-112">若要取得實用的功能，如 IntelliSense、 更佳語法反白顯示，以及更多，您可以下載[Ionide 延伸](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)。</span><span class="sxs-lookup"><span data-stu-id="31131-112">To get awesome features like IntelliSense, better syntax highlighting, and more, you can download the [Ionide Extension](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span>

## <a name="building-a-simple-multi-project-solution"></a><span data-ttu-id="31131-113">建立簡單的多專案方案</span><span class="sxs-lookup"><span data-stu-id="31131-113">Building a Simple Multi-project Solution</span></span>

<span data-ttu-id="31131-114">開啟命令提示字元/終端機，並使用`dotnet new`命令以建立新的方案檔稱為`FSNetCore`:</span><span class="sxs-lookup"><span data-stu-id="31131-114">Open a command prompt/terminal and use the `dotnet new` command to create new solution file called `FSNetCore`:</span></span>

```
dotnet new sln -o FSNetCore
```

<span data-ttu-id="31131-115">只要命令完成，則會產生下列目錄結構：</span><span class="sxs-lookup"><span data-stu-id="31131-115">The folowing directory structure is produced as a result of the command completing:</span></span>

```
FSNetCore
    ├── FSNetCore.sln
```

<span data-ttu-id="31131-116">將目錄變更為*FSNetCore*然後開始將專案加入至方案資料夾。</span><span class="sxs-lookup"><span data-stu-id="31131-116">Change directories to *FSNetCore* and start adding projects to the solution folder.</span></span>
 
### <a name="writing-a-class-library"></a><span data-ttu-id="31131-117">撰寫類別程式庫</span><span class="sxs-lookup"><span data-stu-id="31131-117">Writing a Class library</span></span>

<span data-ttu-id="31131-118">使用`dotnet new`命令，建立類別庫專案中的**src**名為程式庫的資料夾。</span><span class="sxs-lookup"><span data-stu-id="31131-118">Use the `dotnet new` command, create a Class Library project in the **src** folder named Library.</span></span> 

```bash
dotnet new lib -lang F# -o src/Library 
```

<span data-ttu-id="31131-119">只要命令完成，則會產生下列目錄結構：</span><span class="sxs-lookup"><span data-stu-id="31131-119">The following directory structure is produced as a result of the command completing:</span></span>

```
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

<span data-ttu-id="31131-120">取代內容`Library.fs`為下列：</span><span class="sxs-lookup"><span data-stu-id="31131-120">Replace the contents of `Library.fs` with the following:</span></span>

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value = 
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value  (JsonConvert.SerializeObject(value))
```

<span data-ttu-id="31131-121">將 Newtonsoft.Json NuGet 套件加入至程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="31131-121">Add the Newtonsoft.Json NuGet package to the Library project.</span></span>

```bash
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

<span data-ttu-id="31131-122">新增`Library`專案加入`FSNetCore`方案中使用`dotnet sln add`命令：</span><span class="sxs-lookup"><span data-stu-id="31131-122">Add the `Library` project to the `FSNetCore` solution using the `dotnet sln add` command:</span></span>

```bash
dotnet sln add src/Library/Library.fsproj
```

<span data-ttu-id="31131-123">還原 NuGet 相依性， `dotnet restore` ([請參閱附註](#dotnet-restore-note)) 並執行`dotnet build`建置專案。</span><span class="sxs-lookup"><span data-stu-id="31131-123">Restore the NuGet dependencies, `dotnet restore` ([see note](#dotnet-restore-note)) and run `dotnet build` to build the project.</span></span>

### <a name="writing-a-console-application-which-consumes-the-class-library"></a><span data-ttu-id="31131-124">撰寫主控台應用程式耗用類別庫</span><span class="sxs-lookup"><span data-stu-id="31131-124">Writing a Console Application which Consumes the Class Library</span></span>

<span data-ttu-id="31131-125">使用`dotnet new`命令，請建立主控台應用程式中的**src**名為應用程式的資料夾。</span><span class="sxs-lookup"><span data-stu-id="31131-125">Use the `dotnet new` command, create a Console app in the **src** folder named App.</span></span> 

```bash
dotnet new console -lang F# -o src/App 
```

<span data-ttu-id="31131-126">只要命令完成，則會產生下列目錄結構：</span><span class="sxs-lookup"><span data-stu-id="31131-126">The following directory structure is produced as a result of the command completing:</span></span>

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

<span data-ttu-id="31131-127">變更`Program.fs`至：</span><span class="sxs-lookup"><span data-stu-id="31131-127">Change `Program.fs` to:</span></span>

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

<span data-ttu-id="31131-128">將參考加入`Library`專案使用`dotnet add reference`。</span><span class="sxs-lookup"><span data-stu-id="31131-128">Add a reference to the `Library` project using `dotnet add reference`.</span></span>

```bash
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

<span data-ttu-id="31131-129">新增`App`專案加入`FSNetCore`方案中使用`dotnet sln add`命令：</span><span class="sxs-lookup"><span data-stu-id="31131-129">Add the `App` project to the `FSNetCore` solution using the `dotnet sln add` command:</span></span>

```bash
dotnet sln add src/App/App.fsproj
```

<span data-ttu-id="31131-130">還原 NuGet 相依性， `dotnet restore` ([請參閱附註](#dotnet-restore-note)) 並執行`dotnet build`建置專案。</span><span class="sxs-lookup"><span data-stu-id="31131-130">Restore the NuGet dependencies, `dotnet restore` ([see note](#dotnet-restore-note)) and run `dotnet build` to build the project.</span></span>

<span data-ttu-id="31131-131">將目錄切換到`src/App`主控台專案並執行專案傳遞`Hello World`做為引數。</span><span class="sxs-lookup"><span data-stu-id="31131-131">Change directory to the `src/App` console project and run the project passing `Hello World` as arguments.</span></span>

```bash
cd src/App
dotnet run Hello World
``` 

<span data-ttu-id="31131-132">您應該會看到下列結果：</span><span class="sxs-lookup"><span data-stu-id="31131-132">You should see the following results:</span></span>

```
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```
<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
