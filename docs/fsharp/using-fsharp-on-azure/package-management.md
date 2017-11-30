---
title: "使用 F # 使用 Azure 封裝管理"
description: "使用 Paket 或 Nuget 來管理 F # Azure 相依性"
keywords: "visual f #、 f #，功能性程式設計，.NET 中，.NET Core，Azure"
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: dd32ef9c-5416-467e-9fa3-c9ee3bb08456
ms.openlocfilehash: 22dc94ea69e0dfb95e22da4bc64ce915398190d2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="package-management-for-f-azure-dependencies"></a><span data-ttu-id="10e42-104">F# Azure 相依性的套件管理</span><span class="sxs-lookup"><span data-stu-id="10e42-104">Package Management for F# Azure Dependencies</span></span>

<span data-ttu-id="10e42-105">當您使用封裝管理員時，取得 Azure 開發的封裝很容易。</span><span class="sxs-lookup"><span data-stu-id="10e42-105">Obtaining packages for Azure development is easy when you use a package manager.</span></span> <span data-ttu-id="10e42-106">有兩種選項[Paket](https://fsprojects.github.io/Paket/)和[NuGet](https://www.nuget.org/)。</span><span class="sxs-lookup"><span data-stu-id="10e42-106">The two options are [Paket](https://fsprojects.github.io/Paket/) and [NuGet](https://www.nuget.org/).</span></span>

## <a name="using-paket"></a><span data-ttu-id="10e42-107">使用 Paket</span><span class="sxs-lookup"><span data-stu-id="10e42-107">Using Paket</span></span>

<span data-ttu-id="10e42-108">如果您使用[Paket](https://fsprojects.github.io/Paket/)為相依性管理員中，您可以使用`paket.exe`工具來加入 Azure 相依性。</span><span class="sxs-lookup"><span data-stu-id="10e42-108">If you're using [Paket](https://fsprojects.github.io/Paket/) as your dependency manager, you can use the `paket.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="10e42-109">例如: </span><span class="sxs-lookup"><span data-stu-id="10e42-109">For example:</span></span>

    > paket add nuget WindowsAzure.Storage

<span data-ttu-id="10e42-110">或者，如果您使用[Mono](http://www.mono-project.com/)適用於跨平台.NET 開發：</span><span class="sxs-lookup"><span data-stu-id="10e42-110">Or, if you're using [Mono](http://www.mono-project.com/) for cross-platform .NET development:</span></span>

    > mono paket.exe add nuget WindowsAzure.Storage

<span data-ttu-id="10e42-111">這會新增`WindowsAzure.Storage`至目前目錄中專案的封裝相依性的設定，修改`paket.dependencies`檔案，並下載套件。</span><span class="sxs-lookup"><span data-stu-id="10e42-111">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, modify the `paket.dependencies` file, and download the package.</span></span> <span data-ttu-id="10e42-112">如果您先前設定的相依性，或使用專案所在的相依性已設定由另一個開發人員，您可以解決並安裝相依項目在本機像這樣：</span><span class="sxs-lookup"><span data-stu-id="10e42-112">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

    > paket install

<span data-ttu-id="10e42-113">或者，若為單聲道開發：</span><span class="sxs-lookup"><span data-stu-id="10e42-113">Or, for Mono development:</span></span>

    > mono paket.exe install

<span data-ttu-id="10e42-114">您可以更新所有套件相依性的最新版本，就像這樣：</span><span class="sxs-lookup"><span data-stu-id="10e42-114">You can update all your package dependencies to the latest version like this:</span></span>

    > paket update

<span data-ttu-id="10e42-115">或者，若為單聲道開發：</span><span class="sxs-lookup"><span data-stu-id="10e42-115">Or, for Mono development:</span></span>

    > mono paket.exe update

## <a name="using-nuget"></a><span data-ttu-id="10e42-116">使用 Nuget</span><span class="sxs-lookup"><span data-stu-id="10e42-116">Using Nuget</span></span>

<span data-ttu-id="10e42-117">如果您使用[NuGet](https://www.nuget.org/)為相依性管理員中，您可以使用`nuget.exe`工具來加入 Azure 相依性。</span><span class="sxs-lookup"><span data-stu-id="10e42-117">If you're using [NuGet](https://www.nuget.org/) as your dependency manager, you can use the `nuget.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="10e42-118">例如: </span><span class="sxs-lookup"><span data-stu-id="10e42-118">For example:</span></span>

    > nuget install WindowsAzure.Storage -ExcludeVersion

<span data-ttu-id="10e42-119">或者，若為單聲道開發：</span><span class="sxs-lookup"><span data-stu-id="10e42-119">Or, for Mono development:</span></span>

    > mono nuget.exe install WindowsAzure.Storage -ExcludeVersion

<span data-ttu-id="10e42-120">這會新增`WindowsAzure.Storage`至目前的目錄和下載封裝中的專案的封裝相依性的設定。</span><span class="sxs-lookup"><span data-stu-id="10e42-120">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, and download the package.</span></span> <span data-ttu-id="10e42-121">如果您先前設定的相依性，或使用專案所在的相依性已設定由另一個開發人員，您可以解決並安裝相依項目在本機像這樣：</span><span class="sxs-lookup"><span data-stu-id="10e42-121">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

    > nuget restore 

<span data-ttu-id="10e42-122">或者，若為單聲道開發：</span><span class="sxs-lookup"><span data-stu-id="10e42-122">Or, for Mono development:</span></span>

    > mono nuget.exe restore

<span data-ttu-id="10e42-123">您可以更新所有套件相依性的最新版本，就像這樣：</span><span class="sxs-lookup"><span data-stu-id="10e42-123">You can update all your package dependencies to the latest version like this:</span></span>

    > nuget update

<span data-ttu-id="10e42-124">或者，若為單聲道開發：</span><span class="sxs-lookup"><span data-stu-id="10e42-124">Or, for Mono development:</span></span>

    > mono nuget.exe update

## <a name="referencing-assemblies"></a><span data-ttu-id="10e42-125">參考組件</span><span class="sxs-lookup"><span data-stu-id="10e42-125">Referencing Assemblies</span></span>

<span data-ttu-id="10e42-126">若要在 F # 指令碼中使用您的封裝，您需要參考組件中使用的封裝包含`#r`指示詞。</span><span class="sxs-lookup"><span data-stu-id="10e42-126">In order to use your packages in your F# script, you need to reference the assemblies included in the packages using a `#r` directive.</span></span> <span data-ttu-id="10e42-127">例如: </span><span class="sxs-lookup"><span data-stu-id="10e42-127">For example:</span></span>

    > #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"

<span data-ttu-id="10e42-128">如您所見，您必須指定 DLL 和完整的 DLL 名稱可能不完全與封裝名稱相同的相對路徑。</span><span class="sxs-lookup"><span data-stu-id="10e42-128">As you can see, you'll need to specify the relative path to the DLL and the full DLL name, which may not be exactly the same as the package name.</span></span> <span data-ttu-id="10e42-129">路徑必須包含的 framework 版本，可能是封裝的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="10e42-129">The path will include a framework version and possibly a package version number.</span></span> <span data-ttu-id="10e42-130">若要尋找所有已安裝的組件，您可以使用類似下面的 Windows 命令列上：</span><span class="sxs-lookup"><span data-stu-id="10e42-130">To find all the installed assemblies, you can use something like this on a Windows command line:</span></span>

    > cd packages/WindowsAzure.Storage
    > dir /s/b *.dll

<span data-ttu-id="10e42-131">或 Unix 殼層，如下：</span><span class="sxs-lookup"><span data-stu-id="10e42-131">Or in a Unix shell, something like this:</span></span>

    > find packages/WindowsAzure.Storage -name "*.dll"

<span data-ttu-id="10e42-132">這可讓您的路徑已安裝的組件。</span><span class="sxs-lookup"><span data-stu-id="10e42-132">This will give you the paths to the installed assemblies.</span></span> <span data-ttu-id="10e42-133">從該處，您可以選取 framework 版本的正確路徑。</span><span class="sxs-lookup"><span data-stu-id="10e42-133">From there, you can select the correct path for your framework version.</span></span>
