---
ms.openlocfilehash: d75dc2caa3a002b9d34ac74f2c5c5e192281c0df
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281290"
---
### <a name="default-activityidformat-is-w3c"></a><span data-ttu-id="ac45d-101">預設 ActivityIdFormat 是 W3C</span><span class="sxs-lookup"><span data-stu-id="ac45d-101">Default ActivityIdFormat is W3C</span></span>

<span data-ttu-id="ac45d-102">活動 () 的預設識別碼格式 <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> 現在是 <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="ac45d-102">The default identifier format for activity (<xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType>) is now <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ac45d-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="ac45d-103">Change description</span></span>

<span data-ttu-id="ac45d-104">W3C 活動識別碼格式是在 .NET Core 3.0 中引進，作為階層式識別碼格式的替代方案。</span><span class="sxs-lookup"><span data-stu-id="ac45d-104">The W3C activity ID format was introduced in .NET Core 3.0 as an alternative to the hierarchical ID format.</span></span> <span data-ttu-id="ac45d-105">不過，為了保留相容性，W3C 格式不是預設值，除非是 .NET 5.0。</span><span class="sxs-lookup"><span data-stu-id="ac45d-105">However, to preserve compatibility, the W3C format wasn't made the default until .NET 5.0.</span></span> <span data-ttu-id="ac45d-106">.NET 5.0 中的預設值已變更，因為 [W3C 格式已經過](https://www.w3.org/TR/trace-context/) 核准，並且在多個語言執行方面獲得了吸引。</span><span class="sxs-lookup"><span data-stu-id="ac45d-106">The default was changed in .NET 5.0 because the [W3C format has been ratified](https://www.w3.org/TR/trace-context/) and gained traction across multiple language implementations.</span></span>

<span data-ttu-id="ac45d-107">如果您的應用程式是以 .NET 5.0 或更新版本以外的平臺為目標，則會遇到舊的行為，其中 <xref:System.Diagnostics.ActivityIdFormat.Hierarchical> 是預設格式。</span><span class="sxs-lookup"><span data-stu-id="ac45d-107">If your app targets a platform other than .NET 5.0 or later, it will experience the old behavior, where <xref:System.Diagnostics.ActivityIdFormat.Hierarchical> is the default format.</span></span> <span data-ttu-id="ac45d-108">此預設值適用于平臺 net45 +、netstandard 1.1 + 和 netcoreapp (1.x、2.x 和 3.x) 。</span><span class="sxs-lookup"><span data-stu-id="ac45d-108">This default applies to platforms net45+, netstandard1.1+, and netcoreapp (1.x, 2.x, and 3.x).</span></span> <span data-ttu-id="ac45d-109">在 .NET 5.0 和更新版本中， <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> 會設定為 <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="ac45d-109">In .NET 5.0 and later, <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> is set to <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType>.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ac45d-110">引進的版本</span><span class="sxs-lookup"><span data-stu-id="ac45d-110">Version introduced</span></span>

<span data-ttu-id="ac45d-111">5.0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="ac45d-111">5.0 Preview 7</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ac45d-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="ac45d-112">Recommended action</span></span>

<span data-ttu-id="ac45d-113">如果您的應用程式與用於分散式追蹤的識別碼無關，就不需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="ac45d-113">If your application is agnostic to the identifier that's used for distributed tracing, no action is needed.</span></span> <span data-ttu-id="ac45d-114">程式庫（例如 ASP.NET Core） <xref:System.Net.Http.HttpClient> 可以取用或傳播的兩個版本 <xref:System.Diagnostics.ActivityIdFormat> 。</span><span class="sxs-lookup"><span data-stu-id="ac45d-114">Libraries such as ASP.NET Core and <xref:System.Net.Http.HttpClient> can consume or propagate both versions of the <xref:System.Diagnostics.ActivityIdFormat>.</span></span>

<span data-ttu-id="ac45d-115">如果您需要與現有系統之間的互通性，或是目前的系統依賴識別碼的格式，您可以將設定為，以保留舊的行為 <xref:System.Diagnostics.Activity.DefaultIdFormat> <xref:System.Diagnostics.ActivityIdFormat.Hierarchical?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="ac45d-115">If you require interoperability with existing systems, or current systems rely on the format of the identifier, you can preserve the old behavior by setting <xref:System.Diagnostics.Activity.DefaultIdFormat> to <xref:System.Diagnostics.ActivityIdFormat.Hierarchical?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ac45d-116">或者，您可以使用下列三種方式之一來設定 AppCoNtext 交換器：</span><span class="sxs-lookup"><span data-stu-id="ac45d-116">Alternatively, you can set an AppContext switch in one of three ways:</span></span>

- <span data-ttu-id="ac45d-117">在專案檔中。</span><span class="sxs-lookup"><span data-stu-id="ac45d-117">In the project file.</span></span>

  ```xml
  <ItemGroup>
    <RuntimeHostConfigurationOption Include="System.Diagnostics.DefaultActivityIdFormatIsHierarchial" Value="true" />
  </ItemGroup>
  ```

- <span data-ttu-id="ac45d-118">在檔案的 *runtimeconfig.js* 。</span><span class="sxs-lookup"><span data-stu-id="ac45d-118">In the *runtimeconfig.json* file.</span></span>

  ```json
  {
      "runtimeOptions": {
          "configProperties": {
              "System.Diagnostics.DefaultActivityIdFormatIsHierarchial": true
          }
      }
  }
  ```

- <span data-ttu-id="ac45d-119">透過環境變數。</span><span class="sxs-lookup"><span data-stu-id="ac45d-119">Through an environment variable.</span></span>

  <span data-ttu-id="ac45d-120">設定 `DOTNET_SYSTEM_DIAGNOSTICS_DEFAULTACTIVITYIDFORMATISHIERARCHIAL` 為 `true` 或1。</span><span class="sxs-lookup"><span data-stu-id="ac45d-120">Set `DOTNET_SYSTEM_DIAGNOSTICS_DEFAULTACTIVITYIDFORMATISHIERARCHIAL` to `true` or 1.</span></span>

#### <a name="category"></a><span data-ttu-id="ac45d-121">類別</span><span class="sxs-lookup"><span data-stu-id="ac45d-121">Category</span></span>

<span data-ttu-id="ac45d-122">Core .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="ac45d-122">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ac45d-123">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="ac45d-123">Affected APIs</span></span>

- <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Diagnostics.Activity.DefaultIdFormat`

-->
