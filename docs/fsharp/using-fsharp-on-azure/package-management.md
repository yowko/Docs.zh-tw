---
title: 使用封裝管理與F#適用於 Azure
description: 使用 Paket 或 Nuget 來管理F#Azure 相依性
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: b180024e2276a2fd7786f35cb922b1aa1d91f0ad
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880011"
---
# <a name="package-management-for-f-azure-dependencies"></a><span data-ttu-id="70305-103">F# Azure 相依性的套件管理</span><span class="sxs-lookup"><span data-stu-id="70305-103">Package Management for F# Azure Dependencies</span></span>

<span data-ttu-id="70305-104">取得適用於 Azure 的開發套件，很容易使用的套件管理員。</span><span class="sxs-lookup"><span data-stu-id="70305-104">Obtaining packages for Azure development is easy when you use a package manager.</span></span> <span data-ttu-id="70305-105">兩個選項都[Paket](https://fsprojects.github.io/Paket/)並[NuGet](https://www.nuget.org/)。</span><span class="sxs-lookup"><span data-stu-id="70305-105">The two options are [Paket](https://fsprojects.github.io/Paket/) and [NuGet](https://www.nuget.org/).</span></span>

## <a name="using-paket"></a><span data-ttu-id="70305-106">使用 Paket</span><span class="sxs-lookup"><span data-stu-id="70305-106">Using Paket</span></span>

<span data-ttu-id="70305-107">如果您使用[Paket](https://fsprojects.github.io/Paket/)為您的相依性管理員，您可以使用`paket.exe`加入 Azure 的相依性的工具。</span><span class="sxs-lookup"><span data-stu-id="70305-107">If you're using [Paket](https://fsprojects.github.io/Paket/) as your dependency manager, you can use the `paket.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="70305-108">例如：</span><span class="sxs-lookup"><span data-stu-id="70305-108">For example:</span></span>

```
> paket add nuget WindowsAzure.Storage
```

<span data-ttu-id="70305-109">或者，如果您使用[Mono](https://www.mono-project.com/)適用於跨平台.NET 開發：</span><span class="sxs-lookup"><span data-stu-id="70305-109">Or, if you're using [Mono](https://www.mono-project.com/) for cross-platform .NET development:</span></span>

```
> mono paket.exe add nuget WindowsAzure.Storage
```

<span data-ttu-id="70305-110">這會新增`WindowsAzure.Storage`到目前的目錄中專案的套件相依性，修改`paket.dependencies`檔案，並下載套件。</span><span class="sxs-lookup"><span data-stu-id="70305-110">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, modify the `paket.dependencies` file, and download the package.</span></span> <span data-ttu-id="70305-111">如果您先前已設定相依性，或正在使用專案所在的相依性已設定的另一個開發人員，您可以解決，並安裝相依項目，在本機像這樣：</span><span class="sxs-lookup"><span data-stu-id="70305-111">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

```
> paket install
```

<span data-ttu-id="70305-112">或者，若為 Mono 的開發：</span><span class="sxs-lookup"><span data-stu-id="70305-112">Or, for Mono development:</span></span>

```
> mono paket.exe install
```

<span data-ttu-id="70305-113">您可以更新所有套件相依性的最新的版本，就像這樣：</span><span class="sxs-lookup"><span data-stu-id="70305-113">You can update all your package dependencies to the latest version like this:</span></span>

```
> paket update
```

<span data-ttu-id="70305-114">或者，若為 Mono 的開發：</span><span class="sxs-lookup"><span data-stu-id="70305-114">Or, for Mono development:</span></span>

```
> mono paket.exe update
```

## <a name="using-nuget"></a><span data-ttu-id="70305-115">使用 Nuget</span><span class="sxs-lookup"><span data-stu-id="70305-115">Using Nuget</span></span>

<span data-ttu-id="70305-116">如果您使用[NuGet](https://www.nuget.org/)為您的相依性管理員，您可以使用`nuget.exe`加入 Azure 的相依性的工具。</span><span class="sxs-lookup"><span data-stu-id="70305-116">If you're using [NuGet](https://www.nuget.org/) as your dependency manager, you can use the `nuget.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="70305-117">例如: </span><span class="sxs-lookup"><span data-stu-id="70305-117">For example:</span></span>

```
> nuget install WindowsAzure.Storage -ExcludeVersion
```

<span data-ttu-id="70305-118">或者，若為 Mono 的開發：</span><span class="sxs-lookup"><span data-stu-id="70305-118">Or, for Mono development:</span></span>

```
> mono nuget.exe install WindowsAzure.Storage -ExcludeVersion
```

<span data-ttu-id="70305-119">這會新增`WindowsAzure.Storage`到目前的目錄，並下載封裝中的專案的套件相依性。</span><span class="sxs-lookup"><span data-stu-id="70305-119">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, and download the package.</span></span> <span data-ttu-id="70305-120">如果您先前已設定相依性，或正在使用專案所在的相依性已設定的另一個開發人員，您可以解決，並安裝相依項目，在本機像這樣：</span><span class="sxs-lookup"><span data-stu-id="70305-120">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

```
> nuget restore
```

<span data-ttu-id="70305-121">或者，若為 Mono 的開發：</span><span class="sxs-lookup"><span data-stu-id="70305-121">Or, for Mono development:</span></span>

```
> mono nuget.exe restore
```

<span data-ttu-id="70305-122">您可以更新所有套件相依性的最新的版本，就像這樣：</span><span class="sxs-lookup"><span data-stu-id="70305-122">You can update all your package dependencies to the latest version like this:</span></span>

```
> nuget update
```

<span data-ttu-id="70305-123">或者，若為 Mono 的開發：</span><span class="sxs-lookup"><span data-stu-id="70305-123">Or, for Mono development:</span></span>

```
> mono nuget.exe update
```

## <a name="referencing-assemblies"></a><span data-ttu-id="70305-124">參考組件</span><span class="sxs-lookup"><span data-stu-id="70305-124">Referencing Assemblies</span></span>

<span data-ttu-id="70305-125">若要使用您的套件，在您F#指令碼中，您必須參考包含在封裝中使用的組件`#r`指示詞。</span><span class="sxs-lookup"><span data-stu-id="70305-125">In order to use your packages in your F# script, you need to reference the assemblies included in the packages using a `#r` directive.</span></span> <span data-ttu-id="70305-126">例如: </span><span class="sxs-lookup"><span data-stu-id="70305-126">For example:</span></span>

```
> #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"
```

<span data-ttu-id="70305-127">如您所見，您必須指定 DLL 和可能不會完全封裝名稱相同的完整 DLL 名稱的相對路徑。</span><span class="sxs-lookup"><span data-stu-id="70305-127">As you can see, you'll need to specify the relative path to the DLL and the full DLL name, which may not be exactly the same as the package name.</span></span> <span data-ttu-id="70305-128">路徑必須包含的 framework 版本和可能的套件版本號碼。</span><span class="sxs-lookup"><span data-stu-id="70305-128">The path will include a framework version and possibly a package version number.</span></span> <span data-ttu-id="70305-129">若要尋找所有已安裝的組件，您可以在 Windows 命令列上使用起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="70305-129">To find all the installed assemblies, you can use something like this on a Windows command line:</span></span>

```
> cd packages/WindowsAzure.Storage
> dir /s/b *.dll
```

<span data-ttu-id="70305-130">或者，在 Unix 殼層中，項目如下所示：</span><span class="sxs-lookup"><span data-stu-id="70305-130">Or in a Unix shell, something like this:</span></span>

```
> find packages/WindowsAzure.Storage -name "*.dll"
```

<span data-ttu-id="70305-131">這可讓您的路徑已安裝的組件。</span><span class="sxs-lookup"><span data-stu-id="70305-131">This will give you the paths to the installed assemblies.</span></span> <span data-ttu-id="70305-132">從該處，您可以選取正確的路徑的 framework 版本。</span><span class="sxs-lookup"><span data-stu-id="70305-132">From there, you can select the correct path for your framework version.</span></span>
