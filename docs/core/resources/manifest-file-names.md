---
title: MSBuild 如何產生資訊清單檔案名
description: 描述影響在編譯時期由 MSBuild 產生之資源資訊清單檔案名的因素。
ms.date: 05/08/2020
ms.topic: conceptual
ms.openlocfilehash: 383bf6a077b0631e70ddaa4721b20e992127a73c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83232323"
---
# <a name="how-resource-manifest-files-are-named"></a><span data-ttu-id="75ea1-103">資源資訊清單檔案的命名方式</span><span class="sxs-lookup"><span data-stu-id="75ea1-103">How resource manifest files are named</span></span>

<span data-ttu-id="75ea1-104">當 MSBuild 編譯 .NET Core 專案時，具有 *.resx*副檔名的 XML 資源檔會轉換成二進位 *.resources*檔案。</span><span class="sxs-lookup"><span data-stu-id="75ea1-104">When MSBuild compiles a .NET Core project, XML resource files, which have the *.resx* file extension, are converted into binary *.resources* files.</span></span> <span data-ttu-id="75ea1-105">二進位檔案會內嵌到編譯器的輸出中，而且可由讀取 <xref:System.Resources.ResourceManager> 。</span><span class="sxs-lookup"><span data-stu-id="75ea1-105">The binary files are embedded into the output of the compiler and can be read by the <xref:System.Resources.ResourceManager>.</span></span> <span data-ttu-id="75ea1-106">本文說明 MSBuild 如何為每個 *.resources*檔案選擇名稱。</span><span class="sxs-lookup"><span data-stu-id="75ea1-106">This article describes how MSBuild chooses a name for each *.resources* file.</span></span>

> [!TIP]
> <span data-ttu-id="75ea1-107">如果您明確地將資源專案新增至專案檔，而且它也[隨附于 .Net Core 的預設 [包含 glob](../project-sdk/overview.md#default-compilation-includes)]，您將會收到組建錯誤。</span><span class="sxs-lookup"><span data-stu-id="75ea1-107">If you explicitly add a resource item to your project file, and it's also [included with the default include globs for .NET Core](../project-sdk/overview.md#default-compilation-includes), you will get a build error.</span></span> <span data-ttu-id="75ea1-108">若要手動將資源檔納入為 `EmbeddedResource` 專案，請將 `EnableDefaultEmbeddedResourceItems` 屬性設定為 false。</span><span class="sxs-lookup"><span data-stu-id="75ea1-108">To manually include resource files as `EmbeddedResource` items, set the `EnableDefaultEmbeddedResourceItems` property to false.</span></span>

## <a name="default-name"></a><span data-ttu-id="75ea1-109">預設名稱</span><span class="sxs-lookup"><span data-stu-id="75ea1-109">Default name</span></span>

<span data-ttu-id="75ea1-110">在 .NET Core 3.0 和更新版本中，當下列兩個條件都符合時，會使用資源資訊清單的預設名稱：</span><span class="sxs-lookup"><span data-stu-id="75ea1-110">In .NET Core 3.0 and later, the default name for a resource manifest is used when both of the following conditions are met:</span></span>

- <span data-ttu-id="75ea1-111">資源檔不會明確地包含在專案檔中，做為 `EmbeddedResource` `LogicalName` 、 `ManifestResourceName` 或 `DependentUpon` 中繼資料的專案。</span><span class="sxs-lookup"><span data-stu-id="75ea1-111">The resource file is not explicitly included in the project file as an `EmbeddedResource` item with `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata.</span></span>
- <span data-ttu-id="75ea1-112">在 `EmbeddedResourceUseDependentUponConvention` 專案檔中，屬性未設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="75ea1-112">The `EmbeddedResourceUseDependentUponConvention` property is not set to `false` in the project file.</span></span> <span data-ttu-id="75ea1-113">根據預設，這個屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="75ea1-113">By default, this property is set to `true`.</span></span> <span data-ttu-id="75ea1-114">如需詳細資訊，請參閱[EmbeddedResourceUseDependentUponConvention](../project-sdk/msbuild-props.md#embeddedresourceusedependentuponconvention)。</span><span class="sxs-lookup"><span data-stu-id="75ea1-114">For more information, see [EmbeddedResourceUseDependentUponConvention](../project-sdk/msbuild-props.md#embeddedresourceusedependentuponconvention).</span></span>

<span data-ttu-id="75ea1-115">如果資源檔與相同根檔案名的原始程式檔（*.cs*或 *.vb*）共存，則會使用原始程式檔中定義之第一個類型的完整名稱做為資訊清單檔案名。</span><span class="sxs-lookup"><span data-stu-id="75ea1-115">If the resource file is colocated with a source file (*.cs* or *.vb*) of the same root file name, the full name of the first type that's defined in the source file is used for the manifest file name.</span></span> <span data-ttu-id="75ea1-116">例如，如果 `MyNamespace.Form1` 是*Form1.cs*中所定義的第一個型別，而且*Form1.cs*與*Form1*共存，則該資源檔產生的資訊清單名稱會是*MyNamespace。*</span><span class="sxs-lookup"><span data-stu-id="75ea1-116">For example, if `MyNamespace.Form1` is the first type defined in *Form1.cs*, and *Form1.cs* is colocated with *Form1.resx*, the generated manifest name for that resource file is *MyNamespace.Form1.resources*.</span></span>

## <a name="logicalname-metadata"></a><span data-ttu-id="75ea1-117">LogicalName 中繼資料</span><span class="sxs-lookup"><span data-stu-id="75ea1-117">LogicalName metadata</span></span>

<span data-ttu-id="75ea1-118">如果資源檔已明確包含在專案檔中當做 `EmbeddedResource` 具有 `LogicalName` 中繼資料的專案，則 `LogicalName` 會使用此值做為資訊清單名稱。</span><span class="sxs-lookup"><span data-stu-id="75ea1-118">If a resource file is explicitly included in the project file as an `EmbeddedResource` item with `LogicalName` metadata, the `LogicalName` value is used as the manifest name.</span></span> <span data-ttu-id="75ea1-119">`LogicalName`優先于其他任何中繼資料或設定。</span><span class="sxs-lookup"><span data-stu-id="75ea1-119">`LogicalName` takes precedence over any other metadata or setting.</span></span>

<span data-ttu-id="75ea1-120">例如，在下列專案檔程式碼片段中定義之資源檔的資訊清單名稱是*SomeName。*</span><span class="sxs-lookup"><span data-stu-id="75ea1-120">For example, the manifest name for the resource file that's defined in the following project file snippet is *SomeName.resources*.</span></span>

```xml
<EmbeddedResource Include="X.resx" LogicalName="SomeName.resources" />
```

<span data-ttu-id="75ea1-121">-或-</span><span class="sxs-lookup"><span data-stu-id="75ea1-121">-or-</span></span>

```xml
<EmbeddedResource Include="X.fr-FR.resx" LogicalName="SomeName.resources" />
```

## <a name="manifestresourcename-metadata"></a><span data-ttu-id="75ea1-122">ManifestResourceName 中繼資料</span><span class="sxs-lookup"><span data-stu-id="75ea1-122">ManifestResourceName metadata</span></span>

<span data-ttu-id="75ea1-123">如果資源檔已明確包含在專案檔中，做為 `EmbeddedResource` 具有 `ManifestResourceName` 中繼資料的專案（且 `LogicalName` 不存在），則 `ManifestResourceName` 會使用值加上副檔名 *.resources*，做為資訊清單檔案名。</span><span class="sxs-lookup"><span data-stu-id="75ea1-123">If a resource file is explicitly included in the project file as an `EmbeddedResource` item with `ManifestResourceName` metadata (and `LogicalName` is absent), the `ManifestResourceName` value, combined with the file extension *.resources*, is used as the manifest file name.</span></span>

<span data-ttu-id="75ea1-124">例如，在下列專案檔程式碼片段中定義之資源檔的資訊清單名稱是*SomeName。*</span><span class="sxs-lookup"><span data-stu-id="75ea1-124">For example, the manifest name for the resource file that's defined in the following project file snippet is *SomeName.resources*.</span></span>

```xml
<EmbeddedResource Include="X.resx" ManifestResourceName="SomeName" />
```

<span data-ttu-id="75ea1-125">在下列專案檔程式碼片段中定義之資源檔的資訊清單名稱是*SomeName.fr*。</span><span class="sxs-lookup"><span data-stu-id="75ea1-125">The manifest name for the resource file that's defined in the following project file snippet is *SomeName.fr-FR.resources*.</span></span>

```xml
<EmbeddedResource Include="X.fr-FR.resx" ManifestResourceName="SomeName.fr-FR" />
```

## <a name="dependentupon-metadata"></a><span data-ttu-id="75ea1-126">DependentUpon 中繼資料</span><span class="sxs-lookup"><span data-stu-id="75ea1-126">DependentUpon metadata</span></span>

<span data-ttu-id="75ea1-127">如果資源檔已明確包含在專案檔中當做 `EmbeddedResource` 具有 `DependentUpon` 中繼資料的專案（和 `LogicalName` 並 `ManifestResourceName` 不存在），則會使用所定義之來源檔案中的資訊 `DependentUpon` 做為資源資訊清單檔案名。</span><span class="sxs-lookup"><span data-stu-id="75ea1-127">If a resource file is explicitly included in the project file as an `EmbeddedResource` item with `DependentUpon` metadata (and `LogicalName` and `ManifestResourceName` are absent), information from the source file defined by `DependentUpon` is used for the resource manifest file name.</span></span> <span data-ttu-id="75ea1-128">具體而言，在原始程式檔中定義的第一個型別名稱會用在資訊清單名稱中，如下所示： *Namespace. Classname \[ 。Culture] .resources*。</span><span class="sxs-lookup"><span data-stu-id="75ea1-128">Specifically, the name of the first type that's defined in the source file is used in the manifest name as follows: *Namespace.Classname\[.Culture].resources*.</span></span>

<span data-ttu-id="75ea1-129">例如，在下列專案檔程式碼片段中定義之資源檔的資訊清單名稱是*Namespace. Classname. resources* （其中 `Namespace.Classname` 是*MyTypes.cs*中定義的第一個類別）。</span><span class="sxs-lookup"><span data-stu-id="75ea1-129">For example, the manifest name for the resource file that's defined in the following project file snippet is *Namespace.Classname.resources* (where `Namespace.Classname` is the first class that's defined in *MyTypes.cs*).</span></span>

```xml
<EmbeddedResource Include="X.resx" DependentUpon="MyTypes.cs">
```

<span data-ttu-id="75ea1-130">在下列專案檔程式碼片段中定義之資源檔的資訊清單名稱是*Namespace.Classname.fr-fr .resources* （其中 `Namespace.Classname` 是*MyTypes.cs*中定義的第一個類別）。</span><span class="sxs-lookup"><span data-stu-id="75ea1-130">The manifest name for the resource file that's defined in the following project file snippet is *Namespace.Classname.fr-FR.resources* (where `Namespace.Classname` is the first class that's defined in *MyTypes.cs*).</span></span>

```xml
<EmbeddedResource Include="X.fr-FR.resx" DependentUpon="MyTypes.cs">
```

## <a name="embeddedresourceusedependentuponconvention-property"></a><span data-ttu-id="75ea1-131">EmbeddedResourceUseDependentUponConvention 屬性</span><span class="sxs-lookup"><span data-stu-id="75ea1-131">EmbeddedResourceUseDependentUponConvention property</span></span>

<span data-ttu-id="75ea1-132">如果在 `EmbeddedResourceUseDependentUponConvention` 專案檔中將設定為 `false` ，則每個資源資訊清單檔案名都會以專案的根命名空間為基礎，而從專案根目錄到 *.resx*檔案的相對路徑。</span><span class="sxs-lookup"><span data-stu-id="75ea1-132">If `EmbeddedResourceUseDependentUponConvention` is set to `false` in the project file, each resource manifest file name is based off the root namespace for the project and the relative path from the project root to the *.resx* file.</span></span> <span data-ttu-id="75ea1-133">更明確地說，產生的資源資訊清單檔案名是*RootNamespace. RelativePathWithDotsForSlashes。 \[文化特性。]資源*。</span><span class="sxs-lookup"><span data-stu-id="75ea1-133">More specifically, the generated resource manifest file name is *RootNamespace.RelativePathWithDotsForSlashes.\[Culture.]resources*.</span></span> <span data-ttu-id="75ea1-134">這也是在3.0 之前的 .NET Core 版本中，用來產生資訊清單名稱的邏輯。</span><span class="sxs-lookup"><span data-stu-id="75ea1-134">This is also the logic used to generate manifest names in .NET Core versions prior to 3.0.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="75ea1-135">如果 `RootNamespace` 未定義，則會預設為專案名稱。</span><span class="sxs-lookup"><span data-stu-id="75ea1-135">If `RootNamespace` is not defined, it defaults to the project name.</span></span>
> - <span data-ttu-id="75ea1-136">如果 `LogicalName` `ManifestResourceName` `DependentUpon` 已針對專案檔中的專案指定、或中繼資料 `EmbeddedResource` ，則此命名規則不會套用至該資源檔。</span><span class="sxs-lookup"><span data-stu-id="75ea1-136">If `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for an `EmbeddedResource` item in the project file, this naming rule does not apply to that resource file.</span></span>

## <a name="see-also"></a><span data-ttu-id="75ea1-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="75ea1-137">See also</span></span>

- [<span data-ttu-id="75ea1-138">資訊清單資源命名的運作方式</span><span class="sxs-lookup"><span data-stu-id="75ea1-138">How Manifest Resource Naming Works</span></span>](https://gist.github.com/BenVillalobos/041673b9a73bec60fdc3bf0f86fae62a)
- [<span data-ttu-id="75ea1-139">.NET Core SDK 專案的 MSBuild 屬性</span><span class="sxs-lookup"><span data-stu-id="75ea1-139">MSBuild properties for .NET Core SDK projects</span></span>](../project-sdk/msbuild-props.md)
- [<span data-ttu-id="75ea1-140">MSBuild 的重大變更</span><span class="sxs-lookup"><span data-stu-id="75ea1-140">MSBuild breaking changes</span></span>](../compatibility/msbuild.md)
