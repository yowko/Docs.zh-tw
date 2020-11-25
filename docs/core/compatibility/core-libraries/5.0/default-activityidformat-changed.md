---
title: 重大變更：預設 ActivityIdFormat 是 W3C
description: 瞭解在預設 ActivityIdFormat 為 W3C 的核心 .NET 程式庫中，.NET 5.0 的重大變更。
ms.date: 11/01/2020
ms.openlocfilehash: 77ee705ac18065c84ddeab3127e01b6a40c3b84d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760722"
---
# <a name="default-activityidformat-is-w3c"></a><span data-ttu-id="18326-103">預設 ActivityIdFormat 是 W3C</span><span class="sxs-lookup"><span data-stu-id="18326-103">Default ActivityIdFormat is W3C</span></span>

<span data-ttu-id="18326-104">活動 () 的預設識別碼格式 <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> 現在是 <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="18326-104">The default identifier format for activity (<xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType>) is now <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType>.</span></span>

## <a name="change-description"></a><span data-ttu-id="18326-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="18326-105">Change description</span></span>

<span data-ttu-id="18326-106">W3C 活動識別碼格式是在 .NET Core 3.0 中引進，作為階層式識別碼格式的替代方案。</span><span class="sxs-lookup"><span data-stu-id="18326-106">The W3C activity ID format was introduced in .NET Core 3.0 as an alternative to the hierarchical ID format.</span></span> <span data-ttu-id="18326-107">不過，為了保留相容性，W3C 格式不是預設值，除非是 .NET 5.0。</span><span class="sxs-lookup"><span data-stu-id="18326-107">However, to preserve compatibility, the W3C format wasn't made the default until .NET 5.0.</span></span> <span data-ttu-id="18326-108">.NET 5.0 中的預設值已變更，因為 [W3C 格式已經過](https://www.w3.org/TR/trace-context/) 核准，並且在多個語言執行方面獲得了吸引。</span><span class="sxs-lookup"><span data-stu-id="18326-108">The default was changed in .NET 5.0 because the [W3C format has been ratified](https://www.w3.org/TR/trace-context/) and gained traction across multiple language implementations.</span></span>

<span data-ttu-id="18326-109">如果您的應用程式是以 .NET 5.0 或更新版本以外的平臺為目標，則會遇到舊的行為，其中 <xref:System.Diagnostics.ActivityIdFormat.Hierarchical> 是預設格式。</span><span class="sxs-lookup"><span data-stu-id="18326-109">If your app targets a platform other than .NET 5.0 or later, it will experience the old behavior, where <xref:System.Diagnostics.ActivityIdFormat.Hierarchical> is the default format.</span></span> <span data-ttu-id="18326-110">此預設值適用于平臺 net45 +、netstandard 1.1 + 和 netcoreapp (1.x、2.x 和 3.x) 。</span><span class="sxs-lookup"><span data-stu-id="18326-110">This default applies to platforms net45+, netstandard1.1+, and netcoreapp (1.x, 2.x, and 3.x).</span></span> <span data-ttu-id="18326-111">在 .NET 5.0 和更新版本中， <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> 會設定為 <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="18326-111">In .NET 5.0 and later, <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> is set to <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType>.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="18326-112">引進的版本</span><span class="sxs-lookup"><span data-stu-id="18326-112">Version introduced</span></span>

<span data-ttu-id="18326-113">5.0</span><span class="sxs-lookup"><span data-stu-id="18326-113">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="18326-114">建議的動作</span><span class="sxs-lookup"><span data-stu-id="18326-114">Recommended action</span></span>

<span data-ttu-id="18326-115">如果您的應用程式與用於分散式追蹤的識別碼無關，就不需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="18326-115">If your application is agnostic to the identifier that's used for distributed tracing, no action is needed.</span></span> <span data-ttu-id="18326-116">程式庫（例如 ASP.NET Core） <xref:System.Net.Http.HttpClient> 可以取用或傳播的兩個版本 <xref:System.Diagnostics.ActivityIdFormat> 。</span><span class="sxs-lookup"><span data-stu-id="18326-116">Libraries such as ASP.NET Core and <xref:System.Net.Http.HttpClient> can consume or propagate both versions of the <xref:System.Diagnostics.ActivityIdFormat>.</span></span>

<span data-ttu-id="18326-117">如果您需要與現有系統之間的互通性，或是目前的系統依賴識別碼的格式，您可以將設定為，以保留舊的行為 <xref:System.Diagnostics.Activity.DefaultIdFormat> <xref:System.Diagnostics.ActivityIdFormat.Hierarchical?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="18326-117">If you require interoperability with existing systems, or current systems rely on the format of the identifier, you can preserve the old behavior by setting <xref:System.Diagnostics.Activity.DefaultIdFormat> to <xref:System.Diagnostics.ActivityIdFormat.Hierarchical?displayProperty=nameWithType>.</span></span> <span data-ttu-id="18326-118">或者，您可以使用下列三種方式之一來設定 AppCoNtext 交換器：</span><span class="sxs-lookup"><span data-stu-id="18326-118">Alternatively, you can set an AppContext switch in one of three ways:</span></span>

- <span data-ttu-id="18326-119">在專案檔中。</span><span class="sxs-lookup"><span data-stu-id="18326-119">In the project file.</span></span>

  ```xml
  <ItemGroup>
    <RuntimeHostConfigurationOption Include="System.Diagnostics.DefaultActivityIdFormatIsHierarchial" Value="true" />
  </ItemGroup>
  ```

- <span data-ttu-id="18326-120">在檔案的 *runtimeconfig.js* 。</span><span class="sxs-lookup"><span data-stu-id="18326-120">In the *runtimeconfig.json* file.</span></span>

  ```json
  {
      "runtimeOptions": {
          "configProperties": {
              "System.Diagnostics.DefaultActivityIdFormatIsHierarchial": true
          }
      }
  }
  ```

- <span data-ttu-id="18326-121">透過環境變數。</span><span class="sxs-lookup"><span data-stu-id="18326-121">Through an environment variable.</span></span>

  <span data-ttu-id="18326-122">設定 `DOTNET_SYSTEM_DIAGNOSTICS_DEFAULTACTIVITYIDFORMATISHIERARCHIAL` 為 `true` 或1。</span><span class="sxs-lookup"><span data-stu-id="18326-122">Set `DOTNET_SYSTEM_DIAGNOSTICS_DEFAULTACTIVITYIDFORMATISHIERARCHIAL` to `true` or 1.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="18326-123">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="18326-123">Affected APIs</span></span>

- <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Diagnostics.Activity.DefaultIdFormat`

-->
