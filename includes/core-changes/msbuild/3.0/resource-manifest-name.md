---
ms.openlocfilehash: 16ee73bfc0ab33b04ea3e2fa6d0eec521a9b8634
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78967831"
---
### <a name="resource-manifest-file-names"></a><span data-ttu-id="b5b69-101">資源清單檔案名</span><span class="sxs-lookup"><span data-stu-id="b5b69-101">Resource manifest file names</span></span>

<span data-ttu-id="b5b69-102">從 .NET Core 3.0 開始，生成的資源清單檔案名已更改。</span><span class="sxs-lookup"><span data-stu-id="b5b69-102">Starting in .NET Core 3.0, the generated resource manifest file name has changed.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b5b69-103">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="b5b69-103">Version introduced</span></span>

<span data-ttu-id="b5b69-104">3.0</span><span class="sxs-lookup"><span data-stu-id="b5b69-104">3.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="b5b69-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="b5b69-105">Change description</span></span>

<span data-ttu-id="b5b69-106">在 .NET Core 3.0 之前，當在 MSBuild 專案檔案中為資源 *（.resx*） 檔設置[DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile)中繼資料時，生成的清單名稱是*Namespace.classname.resources*。</span><span class="sxs-lookup"><span data-stu-id="b5b69-106">Prior to .NET Core 3.0, when [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) metadata was set for a resource (*.resx*) file in the MSBuild project file, the generated manifest name was *Namespace.Classname.resources*.</span></span> <span data-ttu-id="b5b69-107">未設置["依賴"](/visualstudio/msbuild/common-msbuild-project-items#compile)時，生成的清單名稱為*Namespace.classname.folderpath相對問題.文化.資源*。</span><span class="sxs-lookup"><span data-stu-id="b5b69-107">When [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) was not set, the generated manifest name was *Namespace.Classname.FolderPathRelativeToRoot.Culture.resources*.</span></span>

<span data-ttu-id="b5b69-108">從 .NET Core 3.0 開始，當 *.resx*檔與同名原始檔案同時位於時，例如，在 Windows 表單應用中，資源清單名稱從原始檔案中第一種類型的全名生成。</span><span class="sxs-lookup"><span data-stu-id="b5b69-108">Starting in .NET Core 3.0, when a *.resx* file is colocated with a source file of the same name, for example, in Windows Forms apps, the resource manifest name is generated from the full name of the first type in the source file.</span></span> <span data-ttu-id="b5b69-109">例如，如果*Type.cs*與*Type.resx*同地，則生成的清單名稱為*Namespace.classname.resources*。</span><span class="sxs-lookup"><span data-stu-id="b5b69-109">For example, if *Type.cs* is colocated with *Type.resx*, the generated manifest name is *Namespace.Classname.resources*.</span></span> <span data-ttu-id="b5b69-110">但是，如果修改 *.resx*檔`EmbeddedResource`的屬性上的任何屬性，則生成的清單檔案名可能不同：</span><span class="sxs-lookup"><span data-stu-id="b5b69-110">However, if you modify any of the attributes on the `EmbeddedResource` property for the *.resx* file, the generated manifest file name may be different:</span></span>

- <span data-ttu-id="b5b69-111">如果屬性`LogicalName`上`EmbeddedResource`的屬性已設置，則該值將用作資源清單檔案名。</span><span class="sxs-lookup"><span data-stu-id="b5b69-111">If the `LogicalName` attribute on the `EmbeddedResource` property is set, that value is used as the resource manifest file name.</span></span>

  <span data-ttu-id="b5b69-112">範例：</span><span class="sxs-lookup"><span data-stu-id="b5b69-112">Examples:</span></span>

  ```xml
  <EmbeddedResource Include="X.resx" LogicalName="SomeName.resources" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" LogicalName="SomeName.resources" />
  ```

  <span data-ttu-id="b5b69-113">**生成的資源清單檔案名**：*某些名稱.資源*（無論 *.resx*檔案名或區域性或任何其他中繼資料）。</span><span class="sxs-lookup"><span data-stu-id="b5b69-113">**Generated resource manifest file name**: *SomeName.resources* (regardless of the *.resx* file name or culture or any other metadata).</span></span>

- <span data-ttu-id="b5b69-114">如果未`LogicalName`設置，但`ManifestResourceName``EmbeddedResource`屬性上的屬性已設置，則其值與檔副檔名 *.resources*結合使用，用作資源清單檔案名。</span><span class="sxs-lookup"><span data-stu-id="b5b69-114">If `LogicalName` is not set, but the `ManifestResourceName` attribute on the `EmbeddedResource` property is set, its value, combined with the file extension *.resources*, is used as the resource manifest file name.</span></span>

  <span data-ttu-id="b5b69-115">範例：</span><span class="sxs-lookup"><span data-stu-id="b5b69-115">Examples:</span></span>

  ```xml
  <EmbeddedResource Include="X.resx" ManifestResourceName="SomeName" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" ManifestResourceName="SomeName.fr-FR" />
  ```

  <span data-ttu-id="b5b69-116">**生成的資源清單檔案名**：*某些名稱.資源*或*SomeName.fr-FR.資源*。</span><span class="sxs-lookup"><span data-stu-id="b5b69-116">**Generated resource manifest file name**: *SomeName.resources* or *SomeName.fr-FR.resources*.</span></span>

- <span data-ttu-id="b5b69-117">如果以前的規則不適用，並且`DependentUpon``EmbeddedResource`元素上的屬性設置為原始檔案，則原始檔案中的第一類的類型名稱將用於資源清單檔案名。</span><span class="sxs-lookup"><span data-stu-id="b5b69-117">If the previous rules don't apply, and the `DependentUpon` attribute on the `EmbeddedResource` element is set to a source file, the type name of the first class in the source file is used in the resource manifest file name.</span></span> <span data-ttu-id="b5b69-118">更具體地說，生成的檔案名是*\[Namespace.Classname 。文化]資源*。</span><span class="sxs-lookup"><span data-stu-id="b5b69-118">More specifically, the generated file name is *Namespace.Classname\[.Culture].resources*.</span></span>

  <span data-ttu-id="b5b69-119">範例：</span><span class="sxs-lookup"><span data-stu-id="b5b69-119">Examples:</span></span>

  ```xml
  <EmbeddedResource Include="X.resx" DependentUpon="MyTypes.cs">
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" DependentUpon="MyTypes.cs">
  ```

  <span data-ttu-id="b5b69-120">**生成的資源清單檔案名** *：Namespace.Classname.資源*或*Namespace.Classname.fr-FR.資源*（`Namespace.Classname`其中是*MyTypes.cs*中第一類的名稱）。</span><span class="sxs-lookup"><span data-stu-id="b5b69-120">**Generated resource manifest file name**: *Namespace.Classname.resources* or *Namespace.Classname.fr-FR.resources* (where `Namespace.Classname` is the name of the first class in *MyTypes.cs*).</span></span>

- <span data-ttu-id="b5b69-121">如果`EmbeddedResourceUseDependentUponConvention`前面的規則不適用，則是`true`（.NET Core 的預設值），並且有一個原始檔案與具有相同基本檔案名的 *.resx*檔共存，則 *.resx*檔依賴于匹配的原始檔案，並且生成的名稱與上一個規則相同。</span><span class="sxs-lookup"><span data-stu-id="b5b69-121">If the previous rules don't apply, `EmbeddedResourceUseDependentUponConvention` is `true` (the default for .NET Core), and there's a source file colocated with a *.resx* file that has the same base file name, the *.resx* file is made dependent upon the matching source file, and the generated name is the same as in the previous rule.</span></span> <span data-ttu-id="b5b69-122">這是 .NET Core 專案的"預設設置"規則。</span><span class="sxs-lookup"><span data-stu-id="b5b69-122">This is the "default settings" rule for .NET Core projects.</span></span>
  
  <span data-ttu-id="b5b69-123">範例：</span><span class="sxs-lookup"><span data-stu-id="b5b69-123">Examples:</span></span>
  
  <span data-ttu-id="b5b69-124">MyTypes.cs*和* *MyTypes.resx*或*MyTypes.fr-FR.resx*的檔存在於同一資料夾中。</span><span class="sxs-lookup"><span data-stu-id="b5b69-124">Files *MyTypes.cs* and *MyTypes.resx* or *MyTypes.fr-FR.resx* exist in the same folder.</span></span>
  
  <span data-ttu-id="b5b69-125">**生成的資源清單檔案名** *：Namespace.Classname.資源*或*Namespace.Classname.fr-FR.資源*（`Namespace.Classname`其中是*MyTypes.cs*中第一類的名稱）。</span><span class="sxs-lookup"><span data-stu-id="b5b69-125">**Generated resource manifest file name**: *Namespace.Classname.resources* or *Namespace.Classname.fr-FR.resources* (where `Namespace.Classname` is the name of the first class in *MyTypes.cs*).</span></span>

- <span data-ttu-id="b5b69-126">如果上述規則都不適用，則生成的資源清單檔案名為*RootNamespace。\[文化。資源*.</span><span class="sxs-lookup"><span data-stu-id="b5b69-126">If none of the previous rules apply, the generated resource manifest file name is *RootNamespace.RelativePathWithDotsForSlashes.\[Culture.]resources*.</span></span> <span data-ttu-id="b5b69-127">相對路徑是`Link``EmbeddedResource`元素屬性的值（如果設置為）。</span><span class="sxs-lookup"><span data-stu-id="b5b69-127">The relative path is the value of the `Link` attribute of the `EmbeddedResource` element if it's set.</span></span> <span data-ttu-id="b5b69-128">否則，相對路徑是`Identity``EmbeddedResource`元素屬性的值。</span><span class="sxs-lookup"><span data-stu-id="b5b69-128">Otherwise, the relative path is the value of the `Identity` attribute of the `EmbeddedResource` element.</span></span> <span data-ttu-id="b5b69-129">在 Visual Studio 中，這是從專案根到解決方案資源管理器中檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="b5b69-129">In Visual Studio, this is the path from the project root to the file in Solution Explorer.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b5b69-130">建議的動作</span><span class="sxs-lookup"><span data-stu-id="b5b69-130">Recommended action</span></span>

<span data-ttu-id="b5b69-131">如果您對生成的清單名稱不滿意，您可以：</span><span class="sxs-lookup"><span data-stu-id="b5b69-131">If you're unsatisfied with the generated manifest names, you can:</span></span>

- <span data-ttu-id="b5b69-132">根據前面描述的命名規則之一修改資源檔中繼資料。</span><span class="sxs-lookup"><span data-stu-id="b5b69-132">Modify your resource file metadata according to one of the previously described naming rules.</span></span>

- <span data-ttu-id="b5b69-133">設置為`EmbeddedResourceUseDependentUponConvention``false`專案檔案中，以完全退出新約定：</span><span class="sxs-lookup"><span data-stu-id="b5b69-133">Set `EmbeddedResourceUseDependentUponConvention` to `false` in your project file to opt out of the new convention entirely:</span></span>

   ```xml
   <EmbeddedResourceUseDependentUponConvention>false</EmbeddedResourceUseDependentUponConvention>
   ```

   > [!NOTE]
   > <span data-ttu-id="b5b69-134">如果`LogicalName`或`ManifestResourceName`屬性存在，則其值仍將用於生成的檔案名。</span><span class="sxs-lookup"><span data-stu-id="b5b69-134">If the `LogicalName` or `ManifestResourceName` attributes are present, their values will still be used for the generated file name.</span></span>

#### <a name="category"></a><span data-ttu-id="b5b69-135">類別</span><span class="sxs-lookup"><span data-stu-id="b5b69-135">Category</span></span>

<span data-ttu-id="b5b69-136">MSBuild</span><span class="sxs-lookup"><span data-stu-id="b5b69-136">MSBuild</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b5b69-137">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="b5b69-137">Affected APIs</span></span>

<span data-ttu-id="b5b69-138">N/A</span><span class="sxs-lookup"><span data-stu-id="b5b69-138">N/A</span></span>
