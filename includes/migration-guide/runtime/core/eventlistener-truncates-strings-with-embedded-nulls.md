---
ms.openlocfilehash: e47a24239872e3fe86ff6902f66b38daaa106598
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497635"
---
### <a name="eventlistener-truncates-strings-with-embedded-nulls"></a><span data-ttu-id="2f14e-101">EventListener 會截斷內嵌 Null 的字串</span><span class="sxs-lookup"><span data-stu-id="2f14e-101">EventListener truncates strings with embedded nulls</span></span>

#### <a name="details"></a><span data-ttu-id="2f14e-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2f14e-102">Details</span></span>

<span data-ttu-id="2f14e-103"><xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> 會截斷內嵌 Null 的字串。</span><span class="sxs-lookup"><span data-stu-id="2f14e-103"><xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> truncates strings with embedded nulls.</span></span> <span data-ttu-id="2f14e-104"><xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> 類別不支援 Null 字元。</span><span class="sxs-lookup"><span data-stu-id="2f14e-104">Null characters are not supported by the <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> class.</span></span> <span data-ttu-id="2f14e-105">這項變更只會影響使用 <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> 讀取處理中 <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> 資料並使用 Ｎull 字元做為分隔符號的應用程式。</span><span class="sxs-lookup"><span data-stu-id="2f14e-105">The change only affects apps that use <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> to read <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> data in process and that use null characters as delimiters.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2f14e-106">建議</span><span class="sxs-lookup"><span data-stu-id="2f14e-106">Suggestion</span></span>

<span data-ttu-id="2f14e-107">如果可能的話，您應該更新 <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> 資料，不要使用內嵌 Null 字元。</span><span class="sxs-lookup"><span data-stu-id="2f14e-107"><xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> data should be updated, if possible, to not use embedded null characters.</span></span>

| <span data-ttu-id="2f14e-108">名稱</span><span class="sxs-lookup"><span data-stu-id="2f14e-108">Name</span></span>    | <span data-ttu-id="2f14e-109">值</span><span class="sxs-lookup"><span data-stu-id="2f14e-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2f14e-110">範圍</span><span class="sxs-lookup"><span data-stu-id="2f14e-110">Scope</span></span>   |<span data-ttu-id="2f14e-111">Edge</span><span class="sxs-lookup"><span data-stu-id="2f14e-111">Edge</span></span>|
|<span data-ttu-id="2f14e-112">版本</span><span class="sxs-lookup"><span data-stu-id="2f14e-112">Version</span></span>|<span data-ttu-id="2f14e-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="2f14e-113">4.5.1</span></span>|
|<span data-ttu-id="2f14e-114">類型</span><span class="sxs-lookup"><span data-stu-id="2f14e-114">Type</span></span>|<span data-ttu-id="2f14e-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="2f14e-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="2f14e-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="2f14e-116">Affected APIs</span></span>

- <xref:System.Diagnostics.Tracing.EventListener.%23ctor>
- <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType>
- <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords)?displayProperty=nameWithType>
- <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords,System.Collections.Generic.IDictionary{System.String,System.String})?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Diagnostics.Tracing.EventListener.#ctor`
- `M:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)`
- `M:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords)`
- `M:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords,System.Collections.Generic.IDictionary{System.String,System.String})`

-->
