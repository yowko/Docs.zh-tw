---
title: '使用 F # 使用 Azure 封裝管理'
description: '使用 Paket 或 Nuget 來管理 F # Azure 相依性'
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: fd9c4a15ab0741d44d6d5cf909b7219d310affb0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566963"
---
# <a name="package-management-for-f-azure-dependencies"></a><span data-ttu-id="c13ce-103">F# Azure 相依性的套件管理</span><span class="sxs-lookup"><span data-stu-id="c13ce-103">Package Management for F# Azure Dependencies</span></span>

<span data-ttu-id="c13ce-104">當您使用封裝管理員時，取得 Azure 開發的封裝很容易。</span><span class="sxs-lookup"><span data-stu-id="c13ce-104">Obtaining packages for Azure development is easy when you use a package manager.</span></span> <span data-ttu-id="c13ce-105">有兩種選項[Paket](https://fsprojects.github.io/Paket/)和[NuGet](https://www.nuget.org/)。</span><span class="sxs-lookup"><span data-stu-id="c13ce-105">The two options are [Paket](https://fsprojects.github.io/Paket/) and [NuGet](https://www.nuget.org/).</span></span>

## <a name="using-paket"></a><span data-ttu-id="c13ce-106">使用 Paket</span><span class="sxs-lookup"><span data-stu-id="c13ce-106">Using Paket</span></span>

<span data-ttu-id="c13ce-107">如果您使用[Paket](https://fsprojects.github.io/Paket/)為相依性管理員中，您可以使用`paket.exe`工具來加入 Azure 相依性。</span><span class="sxs-lookup"><span data-stu-id="c13ce-107">If you're using [Paket](https://fsprojects.github.io/Paket/) as your dependency manager, you can use the `paket.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="c13ce-108">例如: </span><span class="sxs-lookup"><span data-stu-id="c13ce-108">For example:</span></span>

    > paket add nuget WindowsAzure.Storage

<span data-ttu-id="c13ce-109">或者，如果您使用[Mono](https://www.mono-project.com/)適用於跨平台.NET 開發：</span><span class="sxs-lookup"><span data-stu-id="c13ce-109">Or, if you're using [Mono](https://www.mono-project.com/) for cross-platform .NET development:</span></span>

    > mono paket.exe add nuget WindowsAzure.Storage

<span data-ttu-id="c13ce-110">這會新增`WindowsAzure.Storage`至目前目錄中專案的封裝相依性的設定，修改`paket.dependencies`檔案，並下載套件。</span><span class="sxs-lookup"><span data-stu-id="c13ce-110">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, modify the `paket.dependencies` file, and download the package.</span></span> <span data-ttu-id="c13ce-111">如果您先前設定的相依性，或使用專案所在的相依性已設定由另一個開發人員，您可以解決並安裝相依項目在本機像這樣：</span><span class="sxs-lookup"><span data-stu-id="c13ce-111">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

    > paket install

<span data-ttu-id="c13ce-112">或者，若為單聲道開發：</span><span class="sxs-lookup"><span data-stu-id="c13ce-112">Or, for Mono development:</span></span>

    > mono paket.exe install

<span data-ttu-id="c13ce-113">您可以更新所有套件相依性的最新版本，就像這樣：</span><span class="sxs-lookup"><span data-stu-id="c13ce-113">You can update all your package dependencies to the latest version like this:</span></span>

    > paket update

<span data-ttu-id="c13ce-114">或者，若為單聲道開發：</span><span class="sxs-lookup"><span data-stu-id="c13ce-114">Or, for Mono development:</span></span>

    > mono paket.exe update

## <a name="using-nuget"></a><span data-ttu-id="c13ce-115">使用 Nuget</span><span class="sxs-lookup"><span data-stu-id="c13ce-115">Using Nuget</span></span>

<span data-ttu-id="c13ce-116">如果您使用[NuGet](https://www.nuget.org/)為相依性管理員中，您可以使用`nuget.exe`工具來加入 Azure 相依性。</span><span class="sxs-lookup"><span data-stu-id="c13ce-116">If you're using [NuGet](https://www.nuget.org/) as your dependency manager, you can use the `nuget.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="c13ce-117">例如: </span><span class="sxs-lookup"><span data-stu-id="c13ce-117">For example:</span></span>

    > nuget install WindowsAzure.Storage -ExcludeVersion

<span data-ttu-id="c13ce-118">或者，若為單聲道開發：</span><span class="sxs-lookup"><span data-stu-id="c13ce-118">Or, for Mono development:</span></span>

    > mono nuget.exe install WindowsAzure.Storage -ExcludeVersion

<span data-ttu-id="c13ce-119">這會新增`WindowsAzure.Storage`至目前的目錄和下載封裝中的專案的封裝相依性的設定。</span><span class="sxs-lookup"><span data-stu-id="c13ce-119">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, and download the package.</span></span> <span data-ttu-id="c13ce-120">如果您先前設定的相依性，或使用專案所在的相依性已設定由另一個開發人員，您可以解決並安裝相依項目在本機像這樣：</span><span class="sxs-lookup"><span data-stu-id="c13ce-120">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

    > nuget restore 

<span data-ttu-id="c13ce-121">或者，若為單聲道開發：</span><span class="sxs-lookup"><span data-stu-id="c13ce-121">Or, for Mono development:</span></span>

    > mono nuget.exe restore

<span data-ttu-id="c13ce-122">您可以更新所有套件相依性的最新版本，就像這樣：</span><span class="sxs-lookup"><span data-stu-id="c13ce-122">You can update all your package dependencies to the latest version like this:</span></span>

    > nuget update

<span data-ttu-id="c13ce-123">或者，若為單聲道開發：</span><span class="sxs-lookup"><span data-stu-id="c13ce-123">Or, for Mono development:</span></span>

    > mono nuget.exe update

## <a name="referencing-assemblies"></a><span data-ttu-id="c13ce-124">參考組件</span><span class="sxs-lookup"><span data-stu-id="c13ce-124">Referencing Assemblies</span></span>

<span data-ttu-id="c13ce-125">若要在 F # 指令碼中使用您的封裝，您需要參考組件中使用的封裝包含`#r`指示詞。</span><span class="sxs-lookup"><span data-stu-id="c13ce-125">In order to use your packages in your F# script, you need to reference the assemblies included in the packages using a `#r` directive.</span></span> <span data-ttu-id="c13ce-126">例如: </span><span class="sxs-lookup"><span data-stu-id="c13ce-126">For example:</span></span>

    > #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"

<span data-ttu-id="c13ce-127">如您所見，您必須指定 DLL 和完整的 DLL 名稱可能不完全與封裝名稱相同的相對路徑。</span><span class="sxs-lookup"><span data-stu-id="c13ce-127">As you can see, you'll need to specify the relative path to the DLL and the full DLL name, which may not be exactly the same as the package name.</span></span> <span data-ttu-id="c13ce-128">路徑必須包含的 framework 版本，可能是封裝的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="c13ce-128">The path will include a framework version and possibly a package version number.</span></span> <span data-ttu-id="c13ce-129">若要尋找所有已安裝的組件，您可以使用類似下面的 Windows 命令列上：</span><span class="sxs-lookup"><span data-stu-id="c13ce-129">To find all the installed assemblies, you can use something like this on a Windows command line:</span></span>

    > cd packages/WindowsAzure.Storage
    > dir /s/b *.dll

<span data-ttu-id="c13ce-130">或 Unix 殼層，如下：</span><span class="sxs-lookup"><span data-stu-id="c13ce-130">Or in a Unix shell, something like this:</span></span>

    > find packages/WindowsAzure.Storage -name "*.dll"

<span data-ttu-id="c13ce-131">這可讓您的路徑已安裝的組件。</span><span class="sxs-lookup"><span data-stu-id="c13ce-131">This will give you the paths to the installed assemblies.</span></span> <span data-ttu-id="c13ce-132">從該處，您可以選取 framework 版本的正確路徑。</span><span class="sxs-lookup"><span data-stu-id="c13ce-132">From there, you can select the correct path for your framework version.</span></span>
