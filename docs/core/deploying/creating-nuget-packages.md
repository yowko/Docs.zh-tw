---
title: "使用跨平台工具建立 NuGet 封裝"
description: "了解如何使用 'dotnet pack' 命令建立 NuGet 套件。"
keywords: ".NET、.NET Core、NuGet"
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 2f0415c1-110b-433d-87c1-ae3d543a8844
ms.openlocfilehash: a5738a4f3755a959660db4be683677673af61ef9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-nuget-package-with-cross-platform-tools"></a><span data-ttu-id="747ef-104">如何使用跨平台工具建立 NuGet 封裝</span><span class="sxs-lookup"><span data-stu-id="747ef-104">How to Create a NuGet Package with Cross Platform Tools</span></span>

> [!NOTE]
> <span data-ttu-id="747ef-105">下圖顯示使用 Unix 的命令列範例。</span><span class="sxs-lookup"><span data-stu-id="747ef-105">The following shows command-line samples using Unix.</span></span>  <span data-ttu-id="747ef-106">此處顯示的 `dotnet pack` 命令，運作運作方式與在 Windows 上如出一轍。</span><span class="sxs-lookup"><span data-stu-id="747ef-106">The `dotnet pack` command as shown here works the same way on Windows.</span></span>

<span data-ttu-id="747ef-107">在 .NET Core 1.0，程式庫預期以 NuGet 封裝方式散發。</span><span class="sxs-lookup"><span data-stu-id="747ef-107">For .NET Core 1.0, libraries are expected to be distributed as NuGet packages.</span></span>  <span data-ttu-id="747ef-108">實際上，所有的 .NET 標準程式庫都是以這種方式散發及取用。</span><span class="sxs-lookup"><span data-stu-id="747ef-108">This is in fact how all of the .NET Standard libraries are distributed and consumed.</span></span>  <span data-ttu-id="747ef-109">`dotnet pack` 命令最容易完成此作業。</span><span class="sxs-lookup"><span data-stu-id="747ef-109">This is most easily done with the `dotnet pack` command.</span></span>

<span data-ttu-id="747ef-110">假設您剛寫完酷炫的新程式庫，希望透過 NuGet 散發。</span><span class="sxs-lookup"><span data-stu-id="747ef-110">Imagine that you just wrote an awesome new library that you would like to distribute over NuGet.</span></span>  <span data-ttu-id="747ef-111">您可以使用跨平台工具建立 NuGet 封裝，絲毫不差地完成此作業！</span><span class="sxs-lookup"><span data-stu-id="747ef-111">You can create a NuGet package with cross platform tools to do exactly that!</span></span>  <span data-ttu-id="747ef-112">下例假設 **SuperAwesomeLibrary** 程式庫以 `netstandard1.0` 為目標。</span><span class="sxs-lookup"><span data-stu-id="747ef-112">The following example assumes a library called **SuperAwesomeLibrary** which targets `netstandard1.0`.</span></span>

<span data-ttu-id="747ef-113">如果您有可轉移的相依性，也就是相依於另一個專案的專案，您必須先使用 `dotnet restore` 命令確保還原整個解決方案的封裝，再建立 NuGet 封裝。</span><span class="sxs-lookup"><span data-stu-id="747ef-113">If you have transitive dependencies; that is, a project which depends on another project, you'll need to make sure to restore packages for your entire solution with the `dotnet restore` command before creating a NuGet package.</span></span>  <span data-ttu-id="747ef-114">未完成這項操作，會導致 `dotnet pack` 命令無法正常運作。</span><span class="sxs-lookup"><span data-stu-id="747ef-114">Failing to do so will result in the `dotnet pack` command to not work properly.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]


<span data-ttu-id="747ef-115">在確定封裝還原後，您可以瀏覽至程式庫所在的目錄︰</span><span class="sxs-lookup"><span data-stu-id="747ef-115">After ensuring packages are restored, you can navigate to the directory where a library lives:</span></span>

`$ cd src/SuperAwesomeLibrary`

<span data-ttu-id="747ef-116">然後，只要從命令列發出單一命令︰</span><span class="sxs-lookup"><span data-stu-id="747ef-116">Then it's just a single command from the command line:</span></span>
    
`$ dotnet pack`

<span data-ttu-id="747ef-117">您的 `/bin/Debug` 資料夾現在看起來像這樣︰</span><span class="sxs-lookup"><span data-stu-id="747ef-117">Your `/bin/Debug` folder will now look like this:</span></span>

```
$ ls bin/Debug

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="747ef-118">請注意，這會產生能夠被偵錯的封裝。</span><span class="sxs-lookup"><span data-stu-id="747ef-118">Note that this will produce a package which is capable of being debugged.</span></span>  <span data-ttu-id="747ef-119">如果想要建置具有版本二進位檔案的 NuGet 套件，您只需要新增 `-c`/`--configuration` 參數，並使用 `release` 作為引數。</span><span class="sxs-lookup"><span data-stu-id="747ef-119">If you want to build a NuGet package with release binaries, all you need to do is add the `-c`/`--configuration` switch and use `release` as the argument.</span></span>

`$ dotnet pack --configuration release`

<span data-ttu-id="747ef-120">您的 `/bin` 資料夾就會有 `release` 資料夾，包含二進位版的 NuGet 封裝︰</span><span class="sxs-lookup"><span data-stu-id="747ef-120">Your `/bin` folder will now have a `release` folder containing your NuGet package with release binaries:</span></span>

```
$ ls bin/release

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="747ef-121">現在您有發行 NuGet 封裝所需的檔案！</span><span class="sxs-lookup"><span data-stu-id="747ef-121">And now you have the necessary files to publish a NuGet package!</span></span>

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a><span data-ttu-id="747ef-122">請勿混淆 `dotnet pack` 與 `dotnet publish`</span><span class="sxs-lookup"><span data-stu-id="747ef-122">Don't confuse `dotnet pack` with `dotnet publish`</span></span>

<span data-ttu-id="747ef-123">請務必注意，和 `dotnet publish` 命令一點關係都沒有。</span><span class="sxs-lookup"><span data-stu-id="747ef-123">It is important to note that at no point is the `dotnet publish` command involved.</span></span>  <span data-ttu-id="747ef-124">`dotnet publish` 命令是要使用相同組合中的所有相依性來部署應用程式，不是用來產生要透過 NuGet 散發及使用的 NuGet 封裝。</span><span class="sxs-lookup"><span data-stu-id="747ef-124">The `dotnet publish` command is for deploying applications with all of their dependencies in the same bundle -  not for generating a NuGet package to be distributed and consumed via NuGet.</span></span>
