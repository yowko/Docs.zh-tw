---
ms.openlocfilehash: 5a96b40e5e0df6a47415acecab410444a713632b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497696"
---
### <a name="etw-eventlisteners-do-not-capture-events-from-providers-with-explicit-keywords-like-the-tpl-provider"></a><span data-ttu-id="699de-101">ETW EventListeners 無法使用 Explicit 關鍵字從提供者擷取事件 (例如 TPL 提供者)</span><span class="sxs-lookup"><span data-stu-id="699de-101">ETW EventListeners do not capture events from providers with explicit keywords (like the TPL provider)</span></span>

#### <a name="details"></a><span data-ttu-id="699de-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="699de-102">Details</span></span>

<span data-ttu-id="699de-103">具有空白關鍵字遮罩的 ETW EventListeners 無法使用 Explicit 關鍵字從提供者正確地擷取事件。</span><span class="sxs-lookup"><span data-stu-id="699de-103">ETW EventListeners with a blank keyword mask do not properly capture events from providers with explicit keywords.</span></span> <span data-ttu-id="699de-104">在 .NET Framework 4.5 中，TPL 提供者已開始提供 Explicit 關鍵字並觸發此問題。</span><span class="sxs-lookup"><span data-stu-id="699de-104">In the .NET Framework 4.5, the TPL provider began providing explicit keywords and triggered this issue.</span></span> <span data-ttu-id="699de-105">在 .NET Framework 4.6 中，已更新 EventListeners，因此不會再發生此問題。</span><span class="sxs-lookup"><span data-stu-id="699de-105">In the .NET Framework 4.6, EventListeners have been updated to no longer have this issue.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="699de-106">建議</span><span class="sxs-lookup"><span data-stu-id="699de-106">Suggestion</span></span>

<span data-ttu-id="699de-107">若要解決此問題，請將 <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)> 的呼叫取代為 EnableEvents 多載的呼叫，該呼叫明確指定「任何關鍵字」遮罩以使用︰<code>EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))</code>。此外，此問題在 .NET Framework 4.6 中已修正，因此可藉由升級至該版 .NET Framework 來解決。</span><span class="sxs-lookup"><span data-stu-id="699de-107">To work around this problem, replace calls to <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)> with calls to the EnableEvents overload that explicitly specifies the &quot;any keywords&quot; mask to use: <code>EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))</code>.Alternatively, this issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="699de-108">名稱</span><span class="sxs-lookup"><span data-stu-id="699de-108">Name</span></span>    | <span data-ttu-id="699de-109">值</span><span class="sxs-lookup"><span data-stu-id="699de-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="699de-110">範圍</span><span class="sxs-lookup"><span data-stu-id="699de-110">Scope</span></span>   |<span data-ttu-id="699de-111">Edge</span><span class="sxs-lookup"><span data-stu-id="699de-111">Edge</span></span>|
|<span data-ttu-id="699de-112">版本</span><span class="sxs-lookup"><span data-stu-id="699de-112">Version</span></span>|<span data-ttu-id="699de-113">4.5</span><span class="sxs-lookup"><span data-stu-id="699de-113">4.5</span></span>|
|<span data-ttu-id="699de-114">類型</span><span class="sxs-lookup"><span data-stu-id="699de-114">Type</span></span>|<span data-ttu-id="699de-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="699de-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="699de-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="699de-116">Affected APIs</span></span>

- <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)`

-->
