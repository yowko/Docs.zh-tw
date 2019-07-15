---
ms.openlocfilehash: eab476a1d3f275e851e5af4198c30b60ad0c17b8
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858529"
---
### <a name="etw-eventlisteners-do-not-capture-events-from-providers-with-explicit-keywords-like-the-tpl-provider"></a><span data-ttu-id="58f8a-101">ETW EventListeners 無法使用 Explicit 關鍵字從提供者擷取事件 (例如 TPL 提供者)</span><span class="sxs-lookup"><span data-stu-id="58f8a-101">ETW EventListeners do not capture events from providers with explicit keywords (like the TPL provider)</span></span>

|   |   |
|---|---|
|<span data-ttu-id="58f8a-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="58f8a-102">Details</span></span>|<span data-ttu-id="58f8a-103">具有空白關鍵字遮罩的 ETW EventListeners 無法使用 Explicit 關鍵字從提供者正確地擷取事件。</span><span class="sxs-lookup"><span data-stu-id="58f8a-103">ETW EventListeners with a blank keyword mask do not properly capture events from providers with explicit keywords.</span></span> <span data-ttu-id="58f8a-104">在 .NET Framework 4.5 中，TPL 提供者已開始提供 Explicit 關鍵字並觸發此問題。</span><span class="sxs-lookup"><span data-stu-id="58f8a-104">In the .NET Framework 4.5, the TPL provider began providing explicit keywords and triggered this issue.</span></span> <span data-ttu-id="58f8a-105">在 .NET Framework 4.6 中，已更新 EventListeners，因此不會再發生此問題。</span><span class="sxs-lookup"><span data-stu-id="58f8a-105">In the .NET Framework 4.6, EventListeners have been updated to no longer have this issue.</span></span>|
|<span data-ttu-id="58f8a-106">建議</span><span class="sxs-lookup"><span data-stu-id="58f8a-106">Suggestion</span></span>|<span data-ttu-id="58f8a-107">若要解決此問題，請將 <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)> 的呼叫取代為 EnableEvents 多載的呼叫，該呼叫明確指定「任何關鍵字」遮罩以使用︰<code>EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))</code>。此外，此問題在 .NET Framework 4.6 中已修正，因此可藉由升級至該版 .NET Framework 來解決。</span><span class="sxs-lookup"><span data-stu-id="58f8a-107">To work around this problem, replace calls to <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)> with calls to the EnableEvents overload that explicitly specifies the &quot;any keywords&quot; mask to use: <code>EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))</code>.Alternatively, this issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>|
|<span data-ttu-id="58f8a-108">範圍</span><span class="sxs-lookup"><span data-stu-id="58f8a-108">Scope</span></span>|<span data-ttu-id="58f8a-109">Edge</span><span class="sxs-lookup"><span data-stu-id="58f8a-109">Edge</span></span>|
|<span data-ttu-id="58f8a-110">版本</span><span class="sxs-lookup"><span data-stu-id="58f8a-110">Version</span></span>|<span data-ttu-id="58f8a-111">4.5</span><span class="sxs-lookup"><span data-stu-id="58f8a-111">4.5</span></span>|
|<span data-ttu-id="58f8a-112">類型</span><span class="sxs-lookup"><span data-stu-id="58f8a-112">Type</span></span>|<span data-ttu-id="58f8a-113">執行階段</span><span class="sxs-lookup"><span data-stu-id="58f8a-113">Runtime</span></span>|
|<span data-ttu-id="58f8a-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="58f8a-114">Affected APIs</span></span>|<ul><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li></ul>|

