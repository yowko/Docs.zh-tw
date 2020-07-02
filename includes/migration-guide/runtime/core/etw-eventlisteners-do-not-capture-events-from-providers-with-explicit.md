---
ms.openlocfilehash: 7d50962b518c15875a5f1a82f5b89ab87a1db02e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619971"
---
### <a name="etw-eventlisteners-do-not-capture-events-from-providers-with-explicit-keywords-like-the-tpl-provider"></a><span data-ttu-id="7562c-101">ETW EventListeners 無法使用 Explicit 關鍵字從提供者擷取事件 (例如 TPL 提供者)</span><span class="sxs-lookup"><span data-stu-id="7562c-101">ETW EventListeners do not capture events from providers with explicit keywords (like the TPL provider)</span></span>

#### <a name="details"></a><span data-ttu-id="7562c-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="7562c-102">Details</span></span>

<span data-ttu-id="7562c-103">具有空白關鍵字遮罩的 ETW EventListeners 無法使用 Explicit 關鍵字從提供者正確地擷取事件。</span><span class="sxs-lookup"><span data-stu-id="7562c-103">ETW EventListeners with a blank keyword mask do not properly capture events from providers with explicit keywords.</span></span> <span data-ttu-id="7562c-104">在 .NET Framework 4.5 中，TPL 提供者已開始提供 Explicit 關鍵字並觸發此問題。</span><span class="sxs-lookup"><span data-stu-id="7562c-104">In the .NET Framework 4.5, the TPL provider began providing explicit keywords and triggered this issue.</span></span> <span data-ttu-id="7562c-105">在 .NET Framework 4.6 中，已更新 EventListeners，因此不會再發生此問題。</span><span class="sxs-lookup"><span data-stu-id="7562c-105">In the .NET Framework 4.6, EventListeners have been updated to no longer have this issue.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7562c-106">建議</span><span class="sxs-lookup"><span data-stu-id="7562c-106">Suggestion</span></span>

<span data-ttu-id="7562c-107">若要解決此問題，請將 <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)> 的呼叫取代為 EnableEvents 多載的呼叫，該呼叫明確指定「任何關鍵字」遮罩以使用︰<code>EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))</code>。此外，此問題在 .NET Framework 4.6 中已修正，因此可藉由升級至該版 .NET Framework 來解決。</span><span class="sxs-lookup"><span data-stu-id="7562c-107">To work around this problem, replace calls to <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)> with calls to the EnableEvents overload that explicitly specifies the &quot;any keywords&quot; mask to use: <code>EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))</code>.Alternatively, this issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="7562c-108">名稱</span><span class="sxs-lookup"><span data-stu-id="7562c-108">Name</span></span>    | <span data-ttu-id="7562c-109">值</span><span class="sxs-lookup"><span data-stu-id="7562c-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7562c-110">影響範圍</span><span class="sxs-lookup"><span data-stu-id="7562c-110">Scope</span></span>   |<span data-ttu-id="7562c-111">Edge</span><span class="sxs-lookup"><span data-stu-id="7562c-111">Edge</span></span>|
|<span data-ttu-id="7562c-112">版本</span><span class="sxs-lookup"><span data-stu-id="7562c-112">Version</span></span>|<span data-ttu-id="7562c-113">4.5</span><span class="sxs-lookup"><span data-stu-id="7562c-113">4.5</span></span>|
|<span data-ttu-id="7562c-114">類型</span><span class="sxs-lookup"><span data-stu-id="7562c-114">Type</span></span>|<span data-ttu-id="7562c-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="7562c-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7562c-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="7562c-116">Affected APIs</span></span>

-<xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li></ul>|
