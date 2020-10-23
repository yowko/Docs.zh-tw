---
ms.openlocfilehash: 959d8cb6d3e52916f6777054f3e9b327dc8edb4e
ms.sourcegitcommit: 98d20cb038669dca4a195eb39af37d22ea9d008e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434927"
---
### <a name="global-assembly-cache-apis-are-obsolete"></a><span data-ttu-id="d234b-101">全域組件快取 Api 已淘汰</span><span class="sxs-lookup"><span data-stu-id="d234b-101">Global assembly cache APIs are obsolete</span></span>

<span data-ttu-id="d234b-102">.NET Core 和 .NET 5.0 和更新版本消除了 .NET Framework 中存在的全域組件快取 (GAC) 的概念。</span><span class="sxs-lookup"><span data-stu-id="d234b-102">.NET Core and .NET 5.0 and later versions eliminate the concept of the global assembly cache (GAC) that was present in .NET Framework.</span></span> <span data-ttu-id="d234b-103">因此，處理 GAC 的所有 .NET Core 和 .NET 5 + Api 都會失敗或不執行任何操作。</span><span class="sxs-lookup"><span data-stu-id="d234b-103">As such, all .NET Core and .NET 5+ APIs that deal with the GAC either fail or perform no operation.</span></span>

<span data-ttu-id="d234b-104">為了協助開發人員遠離這些 Api，某些 GAC 相關的 Api 會標示為已淘汰，並 `SYSLIB0005` 在編譯時期產生警告。</span><span class="sxs-lookup"><span data-stu-id="d234b-104">To help steer developers away from these APIs, some GAC-related APIs are marked as obsolete, and generate a `SYSLIB0005` warning at compile time.</span></span> <span data-ttu-id="d234b-105">這些 Api 可能會在未來的 .NET 版本中移除。</span><span class="sxs-lookup"><span data-stu-id="d234b-105">These APIs may be removed in a future version of .NET.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d234b-106">變更描述</span><span class="sxs-lookup"><span data-stu-id="d234b-106">Change description</span></span>

<span data-ttu-id="d234b-107">下列 Api 已標示為過時。</span><span class="sxs-lookup"><span data-stu-id="d234b-107">The following APIs are marked obsolete.</span></span>

| <span data-ttu-id="d234b-108">API</span><span class="sxs-lookup"><span data-stu-id="d234b-108">API</span></span> | <span data-ttu-id="d234b-109">標記為過時</span><span class="sxs-lookup"><span data-stu-id="d234b-109">Marked obsolete in...</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.GlobalAssemblyCache?displayProperty=nameWithType> | <span data-ttu-id="d234b-110">5.0 RC1</span><span class="sxs-lookup"><span data-stu-id="d234b-110">5.0 RC1</span></span> |

<span data-ttu-id="d234b-111">在 .NET Framework 2.x-4.x 中， <xref:System.Reflection.Assembly.GlobalAssemblyCache> `true` 如果查詢的元件是從 GAC 載入，而且 `false` 是從磁片上的其他位置載入，則此屬性會傳回。</span><span class="sxs-lookup"><span data-stu-id="d234b-111">In .NET Framework 2.x - 4.x, the <xref:System.Reflection.Assembly.GlobalAssemblyCache> property returns `true` if the queried assembly was loaded from the GAC, and `false` if it was loaded from a different location on disk.</span></span> <span data-ttu-id="d234b-112">在 .NET Core 2.x-3.x 中， <xref:System.Reflection.Assembly.GlobalAssemblyCache> 一律 `false` 會傳回，以反映 GAC 不存在於 .net core 中。</span><span class="sxs-lookup"><span data-stu-id="d234b-112">In .NET Core 2.x - 3.x, the <xref:System.Reflection.Assembly.GlobalAssemblyCache> always returns `false`, reflecting that the GAC does not exist in .NET Core.</span></span>

```csharp
Assembly asm = typeof(object).Assembly;
// Prints 'True' on .NET Framework, 'False' on .NET Core.
Console.WriteLine(asm.GlobalAssemblyCache);
```

<span data-ttu-id="d234b-113">在 .NET 5.0 和更新版本中， <xref:System.Reflection.Assembly.GlobalAssemblyCache> 屬性會繼續一律傳回 `false` 。</span><span class="sxs-lookup"><span data-stu-id="d234b-113">In .NET 5.0 and later versions, the <xref:System.Reflection.Assembly.GlobalAssemblyCache> property continues to always return `false`.</span></span> <span data-ttu-id="d234b-114">不過，屬性 getter 也會標示為已淘汰，以指出呼叫端應該停止存取屬性。</span><span class="sxs-lookup"><span data-stu-id="d234b-114">However, the property getter is also marked as obsolete to indicate to callers that they should stop accessing the property.</span></span> <span data-ttu-id="d234b-115">程式庫和應用程式不應使用 <xref:System.Reflection.Assembly.GlobalAssemblyCache> API 來判斷執行時間行為，因為它一律會 `false` 在 .net Core 和 .net 5.0 和更新版本中傳回。</span><span class="sxs-lookup"><span data-stu-id="d234b-115">Libraries and apps should not use the <xref:System.Reflection.Assembly.GlobalAssemblyCache> API to make determinations about run-time behavior, as it always returns `false` in .NET Core and .NET 5.0 and later versions.</span></span>

```csharp
Assembly asm = typeof(object).Assembly;
// Prints 'False' on .NET 5.0+; also produces warning SYSLIB0005 at compile time.
Console.WriteLine(asm.GlobalAssemblyCache);
```

<span data-ttu-id="d234b-116">這是僅限編譯時期的變更。</span><span class="sxs-lookup"><span data-stu-id="d234b-116">This is a compile-time only change.</span></span> <span data-ttu-id="d234b-117">舊版 .NET Core 沒有任何執行時間變更。</span><span class="sxs-lookup"><span data-stu-id="d234b-117">There is no run-time change from previous versions of .NET Core.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d234b-118">變更的原因</span><span class="sxs-lookup"><span data-stu-id="d234b-118">Reason for change</span></span>

<span data-ttu-id="d234b-119">全域組件快取 (GAC) 不會以 .NET Core 和 .NET 5.0 和更新版本的概念存在。</span><span class="sxs-lookup"><span data-stu-id="d234b-119">The global assembly cache (GAC) does not exist as a concept in .NET Core and .NET 5.0 and later versions.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d234b-120">引進的版本</span><span class="sxs-lookup"><span data-stu-id="d234b-120">Version introduced</span></span>

<span data-ttu-id="d234b-121">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="d234b-121">.NET 5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d234b-122">建議的動作</span><span class="sxs-lookup"><span data-stu-id="d234b-122">Recommended action</span></span>

- <span data-ttu-id="d234b-123">如果您的應用程式會查詢 <xref:System.Reflection.Assembly.GlobalAssemblyCache> 屬性，請考慮移除呼叫。</span><span class="sxs-lookup"><span data-stu-id="d234b-123">If your application queries the <xref:System.Reflection.Assembly.GlobalAssemblyCache> property, consider removing the call.</span></span> <span data-ttu-id="d234b-124">如果您在 <xref:System.Reflection.Assembly.GlobalAssemblyCache> 執行時間使用值來選擇「gac 中的元件」-flow 與「不在 gac 中的元件」的流程，請重新考慮流程對於 .Net Core 或 .net 5.0 + 應用程式是否仍然合理。</span><span class="sxs-lookup"><span data-stu-id="d234b-124">If you use the <xref:System.Reflection.Assembly.GlobalAssemblyCache> value to choose between an "assembly in the GAC"-flow vs. an "assembly not in the GAC"-flow at run time, reconsider whether the flow still makes sense for a .NET Core or .NET 5.0+ application.</span></span>

- <span data-ttu-id="d234b-125">如果您必須繼續使用已淘汰的 Api，您可以在程式 `SYSLIB0005` 代碼中隱藏警告。</span><span class="sxs-lookup"><span data-stu-id="d234b-125">If you must continue to use the obsolete APIs, you can suppress the `SYSLIB0005` warning in code.</span></span>

  ```csharp
  Assembly asm = typeof(object).Assembly;
  #pragma warning disable SYSLIB0005 // Disable the warning.
  // Prints 'False' on .NET 5.0+.
  Console.WriteLine(asm.GlobalAssemblyCache);
  #pragma warning restore SYSLIB0005 // Re-enable the warning.
  ```

  <span data-ttu-id="d234b-126">您也可以隱藏專案檔中的警告，這會針對專案中的所有原始程式檔停用警告。</span><span class="sxs-lookup"><span data-stu-id="d234b-126">You can also suppress the warning in your project file, which disables the warning for all source files in the project.</span></span>

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- NoWarn below will suppress SYSLIB0005 project-wide -->
     <NoWarn>$(NoWarn);SYSLIB0005</NoWarn>
    </PropertyGroup>
  </Project>
  ```

  <span data-ttu-id="d234b-127">隱藏 `SYSLIB0005` 只會停用 <xref:System.Reflection.Assembly.GlobalAssemblyCache> obsoletion 警告。</span><span class="sxs-lookup"><span data-stu-id="d234b-127">Suppressing `SYSLIB0005` disables only the <xref:System.Reflection.Assembly.GlobalAssemblyCache> obsoletion warning.</span></span> <span data-ttu-id="d234b-128">它不會停用任何其他警告。</span><span class="sxs-lookup"><span data-stu-id="d234b-128">It does not disable any other warnings.</span></span>

#### <a name="category"></a><span data-ttu-id="d234b-129">類別</span><span class="sxs-lookup"><span data-stu-id="d234b-129">Category</span></span>

<span data-ttu-id="d234b-130">Core .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="d234b-130">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d234b-131">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="d234b-131">Affected APIs</span></span>

- <xref:System.Reflection.Assembly.GlobalAssemblyCache?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Reflection.Assembly.GlobalAssemblyCache`

-->
