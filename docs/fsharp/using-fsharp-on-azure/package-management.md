---
title: '使用套件管理搭配適用于 Azure 的 F #'
description: '使用 Paket 或 NuGet 來管理 F # Azure 相依性'
author: sylvanc
ms.date: 09/20/2016
ms.custom: devx-track-fsharp
ms.openlocfilehash: 7816c82e87db113a35fef967886c8c3e27959332
ms.sourcegitcommit: a8a205034eeffc7c3e1bdd6f506a75b0f7099ebf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2020
ms.locfileid: "91756230"
---
# <a name="package-management-for-f-azure-dependencies"></a><span data-ttu-id="70468-103">F# Azure 相依性的套件管理</span><span class="sxs-lookup"><span data-stu-id="70468-103">Package Management for F# Azure Dependencies</span></span>

<span data-ttu-id="70468-104">當您使用套件管理員時，取得 Azure 開發的套件很簡單。</span><span class="sxs-lookup"><span data-stu-id="70468-104">Obtaining packages for Azure development is easy when you use a package manager.</span></span> <span data-ttu-id="70468-105">這兩個選項為 [Paket](https://fsprojects.github.io/Paket/) 和 [NuGet](https://www.nuget.org/)。</span><span class="sxs-lookup"><span data-stu-id="70468-105">The two options are [Paket](https://fsprojects.github.io/Paket/) and [NuGet](https://www.nuget.org/).</span></span>

## <a name="using-paket"></a><span data-ttu-id="70468-106">使用 Paket</span><span class="sxs-lookup"><span data-stu-id="70468-106">Using Paket</span></span>

<span data-ttu-id="70468-107">如果您使用 [Paket](https://fsprojects.github.io/Paket/) 作為相依性管理員，您可以使用此 `paket.exe` 工具來新增 Azure 相依性。</span><span class="sxs-lookup"><span data-stu-id="70468-107">If you're using [Paket](https://fsprojects.github.io/Paket/) as your dependency manager, you can use the `paket.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="70468-108">例如：</span><span class="sxs-lookup"><span data-stu-id="70468-108">For example:</span></span>

```console
> paket add nuget WindowsAzure.Storage
```

<span data-ttu-id="70468-109">或者，如果您要使用 [Mono](https://www.mono-project.com/) 進行跨平臺 .net 開發：</span><span class="sxs-lookup"><span data-stu-id="70468-109">Or, if you're using [Mono](https://www.mono-project.com/) for cross-platform .NET development:</span></span>

```console
> mono paket.exe add nuget WindowsAzure.Storage
```

<span data-ttu-id="70468-110">這會將 `WindowsAzure.Storage` 您在目前目錄中的專案套件相依性集合新增至您的套件相依性集合，並修改該檔案 `paket.dependencies` ，然後下載封裝。</span><span class="sxs-lookup"><span data-stu-id="70468-110">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, modify the `paket.dependencies` file, and download the package.</span></span> <span data-ttu-id="70468-111">如果您先前已設定相依性，或正在使用另一個開發人員已設定相依性的專案，您可以在本機解析並安裝相依性，如下所示：</span><span class="sxs-lookup"><span data-stu-id="70468-111">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

```console
> paket install
```

<span data-ttu-id="70468-112">或者，對於 Mono 開發：</span><span class="sxs-lookup"><span data-stu-id="70468-112">Or, for Mono development:</span></span>

```console
> mono paket.exe install
```

<span data-ttu-id="70468-113">您可以將所有套件相依性更新為最新版本，如下所示：</span><span class="sxs-lookup"><span data-stu-id="70468-113">You can update all your package dependencies to the latest version like this:</span></span>

```console
> paket update
```

<span data-ttu-id="70468-114">或者，對於 Mono 開發：</span><span class="sxs-lookup"><span data-stu-id="70468-114">Or, for Mono development:</span></span>

```console
> mono paket.exe update
```

## <a name="using-nuget"></a><span data-ttu-id="70468-115">使用 NuGet</span><span class="sxs-lookup"><span data-stu-id="70468-115">Using NuGet</span></span>

<span data-ttu-id="70468-116">如果您使用 [NuGet](https://www.nuget.org/) 做為您的相依性管理員，您可以使用此 `nuget.exe` 工具來新增 Azure 相依性。</span><span class="sxs-lookup"><span data-stu-id="70468-116">If you're using [NuGet](https://www.nuget.org/) as your dependency manager, you can use the `nuget.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="70468-117">例如：</span><span class="sxs-lookup"><span data-stu-id="70468-117">For example:</span></span>

```console
> nuget install WindowsAzure.Storage -ExcludeVersion
```

<span data-ttu-id="70468-118">或者，對於 Mono 開發：</span><span class="sxs-lookup"><span data-stu-id="70468-118">Or, for Mono development:</span></span>

```console
> mono nuget.exe install WindowsAzure.Storage -ExcludeVersion
```

<span data-ttu-id="70468-119">這會將 `WindowsAzure.Storage` 您在目前目錄中的專案套件相依性集合新增至集合，並下載套件。</span><span class="sxs-lookup"><span data-stu-id="70468-119">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, and download the package.</span></span> <span data-ttu-id="70468-120">如果您先前已設定相依性，或正在使用另一個開發人員已設定相依性的專案，您可以在本機解析並安裝相依性，如下所示：</span><span class="sxs-lookup"><span data-stu-id="70468-120">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

```console
> nuget restore
```

<span data-ttu-id="70468-121">或者，對於 Mono 開發：</span><span class="sxs-lookup"><span data-stu-id="70468-121">Or, for Mono development:</span></span>

```console
> mono nuget.exe restore
```

<span data-ttu-id="70468-122">您可以將所有套件相依性更新為最新版本，如下所示：</span><span class="sxs-lookup"><span data-stu-id="70468-122">You can update all your package dependencies to the latest version like this:</span></span>

```console
> nuget update
```

<span data-ttu-id="70468-123">或者，對於 Mono 開發：</span><span class="sxs-lookup"><span data-stu-id="70468-123">Or, for Mono development:</span></span>

```console
> mono nuget.exe update
```

## <a name="referencing-assemblies"></a><span data-ttu-id="70468-124">參考組件</span><span class="sxs-lookup"><span data-stu-id="70468-124">Referencing Assemblies</span></span>

<span data-ttu-id="70468-125">若要在 F # 腳本中使用您的封裝，您需要使用指示詞來參考封裝中包含的元件 `#r` 。</span><span class="sxs-lookup"><span data-stu-id="70468-125">In order to use your packages in your F# script, you need to reference the assemblies included in the packages using a `#r` directive.</span></span> <span data-ttu-id="70468-126">例如：</span><span class="sxs-lookup"><span data-stu-id="70468-126">For example:</span></span>

```fsharp
> #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"
```

<span data-ttu-id="70468-127">如您所見，您必須指定 DLL 的相對路徑和完整的 DLL 名稱，這可能與封裝名稱不完全相同。</span><span class="sxs-lookup"><span data-stu-id="70468-127">As you can see, you'll need to specify the relative path to the DLL and the full DLL name, which may not be exactly the same as the package name.</span></span> <span data-ttu-id="70468-128">路徑將包含 framework 版本，也可能包含套件版本號碼。</span><span class="sxs-lookup"><span data-stu-id="70468-128">The path will include a framework version and possibly a package version number.</span></span> <span data-ttu-id="70468-129">若要尋找所有已安裝的元件，您可以在 Windows 命令列上使用像這樣的內容：</span><span class="sxs-lookup"><span data-stu-id="70468-129">To find all the installed assemblies, you can use something like this on a Windows command line:</span></span>

```console
> cd packages/WindowsAzure.Storage
> dir /s/b *.dll
```

<span data-ttu-id="70468-130">或在 Unix shell 中，如下所示：</span><span class="sxs-lookup"><span data-stu-id="70468-130">Or in a Unix shell, something like this:</span></span>

```console
> find packages/WindowsAzure.Storage -name "*.dll"
```

<span data-ttu-id="70468-131">這會提供您已安裝元件的路徑。</span><span class="sxs-lookup"><span data-stu-id="70468-131">This will give you the paths to the installed assemblies.</span></span> <span data-ttu-id="70468-132">您可以從該處選取您 framework 版本的正確路徑。</span><span class="sxs-lookup"><span data-stu-id="70468-132">From there, you can select the correct path for your framework version.</span></span>
