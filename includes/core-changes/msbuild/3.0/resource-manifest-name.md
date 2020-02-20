---
ms.openlocfilehash: 276268d31670b5e7dcd0ae9c0b7a61c3c38ca663
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451877"
---
### <a name="resource-manifest-file-names"></a><span data-ttu-id="db1a2-101">資源資訊清單檔案名</span><span class="sxs-lookup"><span data-stu-id="db1a2-101">Resource manifest file names</span></span>

<span data-ttu-id="db1a2-102">從 .NET Core 3.0 開始，產生的資源資訊清單檔案名已變更。</span><span class="sxs-lookup"><span data-stu-id="db1a2-102">Starting in .NET Core 3.0, the generated resource manifest file name has changed.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="db1a2-103">引進的版本</span><span class="sxs-lookup"><span data-stu-id="db1a2-103">Version introduced</span></span>

<span data-ttu-id="db1a2-104">3.0</span><span class="sxs-lookup"><span data-stu-id="db1a2-104">3.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="db1a2-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="db1a2-105">Change description</span></span>

<span data-ttu-id="db1a2-106">在 .NET Core 3.0 之前，針對 MSBuild 專案檔中的資源（ *.resx*）檔案設定[DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile)中繼資料時，產生的資訊清單名稱是*Namespace. Classname. resources*。</span><span class="sxs-lookup"><span data-stu-id="db1a2-106">Prior to .NET Core 3.0, when [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) metadata was set for a resource (*.resx*) file in the MSBuild project file, the generated manifest name was *Namespace.Classname.resources*.</span></span> <span data-ttu-id="db1a2-107">未設定[DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile)時，產生的資訊清單名稱為*Namespace. FolderPathRelativeToRoot. Culture. resources*。</span><span class="sxs-lookup"><span data-stu-id="db1a2-107">When [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) was not set, the generated manifest name was *Namespace.Classname.FolderPathRelativeToRoot.Culture.resources*.</span></span>

<span data-ttu-id="db1a2-108">從 .NET Core 3.0 開始，當 *.resx*檔案與相同名稱的原始程式檔共存時（例如，在 Windows Forms 應用程式中），會從來源檔案中第一個類型的完整名稱產生資源資訊清單名稱。</span><span class="sxs-lookup"><span data-stu-id="db1a2-108">Starting in .NET Core 3.0, when a *.resx* file is colocated with a source file of the same name, for example, in Windows Forms apps, the resource manifest name is generated from the full name of the first type in the source file.</span></span> <span data-ttu-id="db1a2-109">例如，如果*Type.cs*與 *.resx*共存，則產生的資訊清單名稱會是*Namespace. Classname. resources*。</span><span class="sxs-lookup"><span data-stu-id="db1a2-109">For example, if *Type.cs* is colocated with *Type.resx*, the generated manifest name is *Namespace.Classname.resources*.</span></span> <span data-ttu-id="db1a2-110">不過，如果您修改 *.resx*檔案的 [`EmbeddedResource`] 屬性上的任何屬性，產生的資訊清單檔案名可能會不同：</span><span class="sxs-lookup"><span data-stu-id="db1a2-110">However, if you modify any of the attributes on the `EmbeddedResource` property for the *.resx* file, the generated manifest file name may be different:</span></span>

- <span data-ttu-id="db1a2-111">如果已設定 [`EmbeddedResource`] 屬性上的 [`LogicalName`] 屬性，則會使用該值做為資源資訊清單檔案名。</span><span class="sxs-lookup"><span data-stu-id="db1a2-111">If the `LogicalName` attribute on the `EmbeddedResource` property is set, that value is used as the resource manifest file name.</span></span>

  <span data-ttu-id="db1a2-112">範例：</span><span class="sxs-lookup"><span data-stu-id="db1a2-112">Examples:</span></span>

  ```xml
  <EmbeddedResource Include="X.resx" LogicalName="SomeName.resources" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" LogicalName="SomeName.resources" />
  ```

  <span data-ttu-id="db1a2-113">**產生的資源資訊清單檔案名**： *SomeName* （不論 *.resx*檔案名或文化特性或任何其他中繼資料）。</span><span class="sxs-lookup"><span data-stu-id="db1a2-113">**Generated resource manifest file name**: *SomeName.resources* (regardless of the *.resx* file name or culture or any other metadata).</span></span>

- <span data-ttu-id="db1a2-114">如果未設定 `LogicalName`，但 `EmbeddedResource` 屬性上的 `ManifestResourceName` 屬性已設定，則會使用其值（與副檔名 *.resources*結合）做為資源資訊清單檔案名。</span><span class="sxs-lookup"><span data-stu-id="db1a2-114">If `LogicalName` is not set, but the `ManifestResourceName` attribute on the `EmbeddedResource` property is set, its value, combined with the file extension *.resources*, is used as the resource manifest file name.</span></span>

  <span data-ttu-id="db1a2-115">範例：</span><span class="sxs-lookup"><span data-stu-id="db1a2-115">Examples:</span></span>

  ```xml
  <EmbeddedResource Include="X.resx" ManifestResourceName="SomeName" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" ManifestResourceName="SomeName.fr-FR" />
  ```

  <span data-ttu-id="db1a2-116">**產生的資源資訊清單檔案名**： *SomeName .resources*或*SomeName.fr*。</span><span class="sxs-lookup"><span data-stu-id="db1a2-116">**Generated resource manifest file name**: *SomeName.resources* or *SomeName.fr-FR.resources*.</span></span>

- <span data-ttu-id="db1a2-117">如果先前的規則不適用，而且 `EmbeddedResource` 元素上的 `DependentUpon` 屬性設定為來源檔案，則來源檔案中第一個類別的類型名稱會在資源資訊清單檔案名中使用。</span><span class="sxs-lookup"><span data-stu-id="db1a2-117">If the previous rules don't apply, and the `DependentUpon` attribute on the `EmbeddedResource` element is set to a source file, the type name of the first class in the source file is used in the resource manifest file name.</span></span> <span data-ttu-id="db1a2-118">更明確地說，產生的檔案名是*Namespace. Classname\[。Culture] .resources*。</span><span class="sxs-lookup"><span data-stu-id="db1a2-118">More specifically, the generated file name is *Namespace.Classname\[.Culture].resources*.</span></span>

  <span data-ttu-id="db1a2-119">範例：</span><span class="sxs-lookup"><span data-stu-id="db1a2-119">Examples:</span></span>

  ```xml
  <EmbeddedResource Include="X.resx" DependentUpon="MyTypes.cs">
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" DependentUpon="MyTypes.cs">
  ```

  <span data-ttu-id="db1a2-120">**產生的資源資訊清單檔案名**： *Namespace. Classname. resources*或*Namespace.Classname.fr-fr* （其中 `Namespace.Classname` 是*MyTypes.cs*中第一個類別的名稱）。</span><span class="sxs-lookup"><span data-stu-id="db1a2-120">**Generated resource manifest file name**: *Namespace.Classname.resources* or *Namespace.Classname.fr-FR.resources* (where `Namespace.Classname` is the name of the first class in *MyTypes.cs*).</span></span>

- <span data-ttu-id="db1a2-121">如果先前的規則不適用，`EmbeddedResourceUseDependentUponConvention` 是 `true` （.NET Core 的預設值），而且有一個與 *.resx*檔案共置的原始程式檔具有相同的基底檔案名，則 *.resx*檔案會相依于相符的原始程式檔，而產生的名稱與上一個規則中的相同。</span><span class="sxs-lookup"><span data-stu-id="db1a2-121">If the previous rules don't apply, `EmbeddedResourceUseDependentUponConvention` is `true` (the default for .NET Core), and there's a source file colocated with a *.resx* file that has the same base file name, the *.resx* file is made dependent upon the matching source file, and the generated name is the same as in the previous rule.</span></span> <span data-ttu-id="db1a2-122">這是 .NET Core 專案的「預設設定」規則。</span><span class="sxs-lookup"><span data-stu-id="db1a2-122">This is the "default settings" rule for .NET Core projects.</span></span>
  
  <span data-ttu-id="db1a2-123">範例：</span><span class="sxs-lookup"><span data-stu-id="db1a2-123">Examples:</span></span>
  
  <span data-ttu-id="db1a2-124">Files *MyTypes.cs*和*MyTypes*或*MyTypes.fr-fr*存在於相同的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="db1a2-124">Files *MyTypes.cs* and *MyTypes.resx* or *MyTypes.fr-FR.resx* exist in the same folder.</span></span>
  
  <span data-ttu-id="db1a2-125">**產生的資源資訊清單檔案名**： *Namespace. Classname. resources*或*Namespace.Classname.fr-fr* （其中 `Namespace.Classname` 是*MyTypes.cs*中第一個類別的名稱）。</span><span class="sxs-lookup"><span data-stu-id="db1a2-125">**Generated resource manifest file name**: *Namespace.Classname.resources* or *Namespace.Classname.fr-FR.resources* (where `Namespace.Classname` is the name of the first class in *MyTypes.cs*).</span></span>
    
- <span data-ttu-id="db1a2-126">如果上述規則都不適用，則產生的資源資訊清單檔案名為*RootNamespace. RelativePathWithDotsForSlashes.\[文化特性。]資源*。</span><span class="sxs-lookup"><span data-stu-id="db1a2-126">If none of the previous rules apply, the generated resource manifest file name is *RootNamespace.RelativePathWithDotsForSlashes.\[Culture.]resources*.</span></span> <span data-ttu-id="db1a2-127">相對路徑是 `EmbeddedResource` 元素的 `Link` 屬性值（如果已設定的話）。</span><span class="sxs-lookup"><span data-stu-id="db1a2-127">The relative path is the value of the `Link` attribute of the `EmbeddedResource` element if it's set.</span></span> <span data-ttu-id="db1a2-128">否則，相對路徑就是 `EmbeddedResource` 元素的 `Identity` 屬性值。</span><span class="sxs-lookup"><span data-stu-id="db1a2-128">Otherwise, the relative path is the value of the `Identity` attribute of the `EmbeddedResource` element.</span></span> <span data-ttu-id="db1a2-129">在 Visual Studio 中，這是從專案根目錄到方案總管中檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="db1a2-129">In Visual Studio, this is the path from the project root to the file in Solution Explorer.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="db1a2-130">建議的動作</span><span class="sxs-lookup"><span data-stu-id="db1a2-130">Recommended action</span></span>

<span data-ttu-id="db1a2-131">如果您不滿意所產生的資訊清單名稱，可以：</span><span class="sxs-lookup"><span data-stu-id="db1a2-131">If you're unsatisfied with the generated manifest names, you can:</span></span>

- <span data-ttu-id="db1a2-132">根據先前所述的其中一個命名規則來修改您的資源檔中繼資料。</span><span class="sxs-lookup"><span data-stu-id="db1a2-132">Modify your resource file metadata according to one of the previously described naming rules.</span></span>

- <span data-ttu-id="db1a2-133">在您的專案檔中，將 `EmbeddedResourceUseDependentUponConvention` 設定為 `false`，以完全退出宣告新的慣例：</span><span class="sxs-lookup"><span data-stu-id="db1a2-133">Set `EmbeddedResourceUseDependentUponConvention` to `false` in your project file to opt out of the new convention entirely:</span></span>

   ```xml
   <EmbeddedResourceUseDependentUponConvention>false</EmbeddedResourceUseDependentUponConvention>
   ```

   > [!NOTE]
   > <span data-ttu-id="db1a2-134">如果 `LogicalName` 或 `ManifestResourceName` 屬性存在，其值仍會用於產生的檔案名。</span><span class="sxs-lookup"><span data-stu-id="db1a2-134">If the `LogicalName` or `ManifestResourceName` attributes are present, their values will still be used for the generated file name.</span></span>

#### <a name="category"></a><span data-ttu-id="db1a2-135">類別</span><span class="sxs-lookup"><span data-stu-id="db1a2-135">Category</span></span>

<span data-ttu-id="db1a2-136">MSBuild</span><span class="sxs-lookup"><span data-stu-id="db1a2-136">MSBuild</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="db1a2-137">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="db1a2-137">Affected APIs</span></span>

<span data-ttu-id="db1a2-138">N/A</span><span class="sxs-lookup"><span data-stu-id="db1a2-138">N/A</span></span>
