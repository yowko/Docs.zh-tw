---
ms.openlocfilehash: f24a29a00a1bff34a452c43716d76bf72ef277b5
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206219"
---
### <a name="resource-manifest-file-name-change"></a><span data-ttu-id="3aaf6-101">資源資訊清單檔案名變更</span><span class="sxs-lookup"><span data-stu-id="3aaf6-101">Resource manifest file name change</span></span>

<span data-ttu-id="3aaf6-102">從 .NET Core 3.0 開始，在預設情況下，MSBuild 會為資源檔產生不同的資訊清單檔案名。</span><span class="sxs-lookup"><span data-stu-id="3aaf6-102">Starting in .NET Core 3.0, in the default case, MSBuild generates a different manifest file name for resource files.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3aaf6-103">引進的版本</span><span class="sxs-lookup"><span data-stu-id="3aaf6-103">Version introduced</span></span>

<span data-ttu-id="3aaf6-104">3.0</span><span class="sxs-lookup"><span data-stu-id="3aaf6-104">3.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="3aaf6-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="3aaf6-105">Change description</span></span>

<span data-ttu-id="3aaf6-106">在 .NET Core 3.0 之前，如果 `LogicalName` `ManifestResourceName` 為專案檔中的專案指定了 no、或 `DependentUpon` 中繼資料 `EmbeddedResource` ，則 MSBuild 會在模式中產生資訊清單檔案名 `<RootNamespace>.<ResourceFilePathFromProjectRoot>.resources` 。</span><span class="sxs-lookup"><span data-stu-id="3aaf6-106">Prior to .NET Core 3.0, if no `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata was specified for an `EmbeddedResource` item in the project file, MSBuild generated a manifest file name in the pattern `<RootNamespace>.<ResourceFilePathFromProjectRoot>.resources`.</span></span> <span data-ttu-id="3aaf6-107">如果 `RootNamespace` 專案檔中未定義，它會預設為專案名稱。</span><span class="sxs-lookup"><span data-stu-id="3aaf6-107">If `RootNamespace` is not defined in the project file, it defaults to the project name.</span></span> <span data-ttu-id="3aaf6-108">例如，根專案*目錄中名為*MyProject 的資源檔所產生的資訊清單名稱是*MyProject.Form1.resources*。</span><span class="sxs-lookup"><span data-stu-id="3aaf6-108">For example, the generated manifest name for a resource file named *Form1.resx* in the root project directory was *MyProject.Form1.resources*.</span></span>

<span data-ttu-id="3aaf6-109">從 .NET Core 3.0 開始，如果資源檔與相同名稱的原始程式檔共存 (*例如，Form1.cs) ，MSBuild*會使用來源檔案*Form1.cs*中的類型資訊，以在模式中產生資訊清單檔案名 `<Namespace>.<ClassName>.resources` 。</span><span class="sxs-lookup"><span data-stu-id="3aaf6-109">Starting in .NET Core 3.0, if a resource file is colocated with a source file of the same name (for example, *Form1.resx* and *Form1.cs*), MSBuild uses type information from the source file to generate the manifest file name in the pattern `<Namespace>.<ClassName>.resources`.</span></span> <span data-ttu-id="3aaf6-110">命名空間和類別名稱是從共置原始檔中的第一個型別解壓縮而來。</span><span class="sxs-lookup"><span data-stu-id="3aaf6-110">The namespace and class name are extracted from the first type in the colocated source file.</span></span> <span data-ttu-id="3aaf6-111">例如，與名為*Form1.cs*的*原始程式檔共存的資源*檔所產生的資訊清單名稱，會是*MyNamespace。*</span><span class="sxs-lookup"><span data-stu-id="3aaf6-111">For example, the generated manifest name for a resource file named *Form1.resx* that's colocated with a source file named *Form1.cs* is *MyNamespace.Form1.resources*.</span></span> <span data-ttu-id="3aaf6-112">要注意的重點是，檔案名的第一個部分與舊版的 .NET Core (*MyNamespace* ，而不是 *MyProject*) 。</span><span class="sxs-lookup"><span data-stu-id="3aaf6-112">The key thing to note is that the first part of the file name is different to prior versions of .NET Core (*MyNamespace* instead of *MyProject*).</span></span>

> [!NOTE]
> <span data-ttu-id="3aaf6-113">如果您在 `LogicalName` `ManifestResourceName` 專案檔中的 `DependentUpon` 專案上指定、或中繼資料 `EmbeddedResource` ，則這項變更不會影響該資源檔。</span><span class="sxs-lookup"><span data-stu-id="3aaf6-113">If you have `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata specified on an `EmbeddedResource` item in the project file, then this change does not affect that resource file.</span></span>

<span data-ttu-id="3aaf6-114">這項重大變更是透過將 `EmbeddedResourceUseDependentUponConvention` 屬性新增至 .Net Core 專案所引進。</span><span class="sxs-lookup"><span data-stu-id="3aaf6-114">This breaking change was introduced with the addition of the `EmbeddedResourceUseDependentUponConvention` property to .NET Core projects.</span></span> <span data-ttu-id="3aaf6-115">依預設，不會在 .NET Core 專案檔中明確列出資源檔，因此沒有 `DependentUpon` 中繼資料可指定如何命名產生的 *.resources* 檔案。</span><span class="sxs-lookup"><span data-stu-id="3aaf6-115">By default, resource files aren't explicitly listed in a .NET Core project file, so they have no `DependentUpon` metadata to specify how to name the generated *.resources* file.</span></span> <span data-ttu-id="3aaf6-116">當 `EmbeddedResourceUseDependentUponConvention` 設為 `true` （預設值）時，MSBuild 會尋找共置的原始程式檔，並從該檔案中解壓縮命名空間和類別名稱。</span><span class="sxs-lookup"><span data-stu-id="3aaf6-116">When `EmbeddedResourceUseDependentUponConvention` is set to `true`, which is the default, MSBuild looks for a colocated source file and extracts a namespace and class name from that file.</span></span> <span data-ttu-id="3aaf6-117">如果您將設定 `EmbeddedResourceUseDependentUponConvention` 為 `false` ，MSBuild 會根據先前的行為（結合和相對檔案路徑）來產生資訊清單名稱 `RootNamespace` 。</span><span class="sxs-lookup"><span data-stu-id="3aaf6-117">If you set `EmbeddedResourceUseDependentUponConvention` to `false`, MSBuild generates the manifest name according to the previous behavior, which combines `RootNamespace` and the relative file path.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3aaf6-118">建議的動作</span><span class="sxs-lookup"><span data-stu-id="3aaf6-118">Recommended action</span></span>

<span data-ttu-id="3aaf6-119">在大部分的情況下，開發人員不需要採取任何動作，而且您的應用程式應該會繼續運作。</span><span class="sxs-lookup"><span data-stu-id="3aaf6-119">In most cases, no action is required on the part of the developer, and your app should continue to work.</span></span> <span data-ttu-id="3aaf6-120">但是，如果此變更中斷您的應用程式，您可以：</span><span class="sxs-lookup"><span data-stu-id="3aaf6-120">However, if this change breaks your app, you can either:</span></span>

- <span data-ttu-id="3aaf6-121">將您的程式碼變更為預期新的資訊清單名稱。</span><span class="sxs-lookup"><span data-stu-id="3aaf6-121">Change your code to expect the new manifest name.</span></span>

- <span data-ttu-id="3aaf6-122">在專案檔中將設定為，以退出宣告新的命名慣例 `EmbeddedResourceUseDependentUponConvention` `false` 。</span><span class="sxs-lookup"><span data-stu-id="3aaf6-122">Opt out of the new naming convention by setting `EmbeddedResourceUseDependentUponConvention` to `false` in your project file.</span></span>

  ```xml
  <PropertyGroup>
    <EmbeddedResourceUseDependentUponConvention>false</EmbeddedResourceUseDependentUponConvention>
  </PropertyGroup>
  ```

#### <a name="category"></a><span data-ttu-id="3aaf6-123">類別</span><span class="sxs-lookup"><span data-stu-id="3aaf6-123">Category</span></span>

<span data-ttu-id="3aaf6-124">MSBuild</span><span class="sxs-lookup"><span data-stu-id="3aaf6-124">MSBuild</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3aaf6-125">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="3aaf6-125">Affected APIs</span></span>

<span data-ttu-id="3aaf6-126">N/A</span><span class="sxs-lookup"><span data-stu-id="3aaf6-126">N/A</span></span>
