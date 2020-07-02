---
ms.openlocfilehash: 78faa5f4008b41bac75c94ce09a58c8227e5b485
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614333"
---
### <a name="currentculture-and-currentuiculture-flow-across-tasks"></a><span data-ttu-id="85e25-101">工作之間的 CurrentCulture 和 CurrentUICulture 流程</span><span class="sxs-lookup"><span data-stu-id="85e25-101">CurrentCulture and CurrentUICulture flow across tasks</span></span>

#### <a name="details"></a><span data-ttu-id="85e25-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="85e25-102">Details</span></span>

<span data-ttu-id="85e25-103">從 .NET Framework 4.6 開始，<xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> 和 <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> 會儲存在執行緒的 <xref:System.Threading.ExecutionContext?displayProperty=fullName>，它會在非同步作業之間流動。這表示變更 <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> 或 <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> 會反映在稍後以非同步方式執行的工作。</span><span class="sxs-lookup"><span data-stu-id="85e25-103">Beginning in the .NET Framework 4.6, <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> and <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> are stored in the thread's <xref:System.Threading.ExecutionContext?displayProperty=fullName>, which flows across asynchronous operations.This means that changes to <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> or <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> will be reflected in tasks which are later run asynchronously.</span></span> <span data-ttu-id="85e25-104">這與舊版 .NET Framework 的行為不同，而舊版本會重設所有非同步工作中的 <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> 和 <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="85e25-104">This is different from the behavior of previous .NET Framework versions (which would reset <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> and <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> in all asynchronous tasks).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="85e25-105">建議</span><span class="sxs-lookup"><span data-stu-id="85e25-105">Suggestion</span></span>

<span data-ttu-id="85e25-106">受到此變更影響的應用程式，可以藉由明確地設定所需的 <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> 或 <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> 作為非同步工作中的第一個作業來因應。</span><span class="sxs-lookup"><span data-stu-id="85e25-106">Apps affected by this change may work around it by explicitly setting the desired <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> or <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> as the first operation in an async Task.</span></span> <span data-ttu-id="85e25-107">或者，可以藉由設定下列相容性參數，以選擇加入舊的行為 (不流動 <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName>/<xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName>)：</span><span class="sxs-lookup"><span data-stu-id="85e25-107">Alternatively, the old behavior (of not flowing <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName>/<xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName>) may be opted into by setting the following compatibility switch:</span></span>

```csharp
AppContext.SetSwitch("Switch.System.Globalization.NoAsyncCurrentCulture", true);
```

<span data-ttu-id="85e25-108">.NET Framework 4.6.2 中的 WPF 已修正此問題。</span><span class="sxs-lookup"><span data-stu-id="85e25-108">This issue has been fixed by WPF in .NET Framework 4.6.2.</span></span> <span data-ttu-id="85e25-109">.NET Frameworks 4.6、4.6.1 也已透過 [KB 3139549](https://support.microsoft.com/kb/3139549) 進行修正。</span><span class="sxs-lookup"><span data-stu-id="85e25-109">It has also been fixed in .NET Frameworks 4.6, 4.6.1 through [KB 3139549](https://support.microsoft.com/kb/3139549).</span></span> <span data-ttu-id="85e25-110">以 .NET Framework 4.6 或更新版本為目標的應用程式將在 WPF 應用程式中自動取得正確的行為 - <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName>/<xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> 會跨發送器作業保留。</span><span class="sxs-lookup"><span data-stu-id="85e25-110">Applications targeting .NET Framework 4.6 or later will automatically get the right behavior in WPF applications - <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName>/<xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName>) would be preserved across Dispatcher operations.</span></span>

| <span data-ttu-id="85e25-111">名稱</span><span class="sxs-lookup"><span data-stu-id="85e25-111">Name</span></span>    | <span data-ttu-id="85e25-112">值</span><span class="sxs-lookup"><span data-stu-id="85e25-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="85e25-113">影響範圍</span><span class="sxs-lookup"><span data-stu-id="85e25-113">Scope</span></span>   | <span data-ttu-id="85e25-114">Minor</span><span class="sxs-lookup"><span data-stu-id="85e25-114">Minor</span></span>       |
| <span data-ttu-id="85e25-115">版本</span><span class="sxs-lookup"><span data-stu-id="85e25-115">Version</span></span> | <span data-ttu-id="85e25-116">4.6</span><span class="sxs-lookup"><span data-stu-id="85e25-116">4.6</span></span>         |
| <span data-ttu-id="85e25-117">類型</span><span class="sxs-lookup"><span data-stu-id="85e25-117">Type</span></span>    | <span data-ttu-id="85e25-118">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="85e25-118">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="85e25-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="85e25-119">Affected APIs</span></span>

- <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType>
- <xref:System.Threading.Thread.CurrentCulture?displayProperty=nameWithType>
- <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=nameWithType>
- <xref:System.Threading.Thread.CurrentUICulture?displayProperty=nameWithType>
