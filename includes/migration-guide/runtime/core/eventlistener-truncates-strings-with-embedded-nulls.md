---
ms.openlocfilehash: 6f5c1ecead4e2f74e621354058aab70bfa1cccb6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619965"
---
### <a name="eventlistener-truncates-strings-with-embedded-nulls"></a><span data-ttu-id="e0afe-101">EventListener 會截斷內嵌 Null 的字串</span><span class="sxs-lookup"><span data-stu-id="e0afe-101">EventListener truncates strings with embedded nulls</span></span>

#### <a name="details"></a><span data-ttu-id="e0afe-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e0afe-102">Details</span></span>

<span data-ttu-id="e0afe-103"><xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> 會截斷內嵌 Null 的字串。</span><span class="sxs-lookup"><span data-stu-id="e0afe-103"><xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> truncates strings with embedded nulls.</span></span> <span data-ttu-id="e0afe-104"><xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> 類別不支援 Null 字元。</span><span class="sxs-lookup"><span data-stu-id="e0afe-104">Null characters are not supported by the <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> class.</span></span> <span data-ttu-id="e0afe-105">這項變更只會影響使用 <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> 讀取處理中 <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> 資料並使用 Ｎull 字元做為分隔符號的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e0afe-105">The change only affects apps that use <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> to read <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> data in process and that use null characters as delimiters.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e0afe-106">建議</span><span class="sxs-lookup"><span data-stu-id="e0afe-106">Suggestion</span></span>

<span data-ttu-id="e0afe-107">如果可能的話，您應該更新 <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> 資料，不要使用內嵌 Null 字元。</span><span class="sxs-lookup"><span data-stu-id="e0afe-107"><xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> data should be updated, if possible, to not use embedded null characters.</span></span>

| <span data-ttu-id="e0afe-108">名稱</span><span class="sxs-lookup"><span data-stu-id="e0afe-108">Name</span></span>    | <span data-ttu-id="e0afe-109">值</span><span class="sxs-lookup"><span data-stu-id="e0afe-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e0afe-110">影響範圍</span><span class="sxs-lookup"><span data-stu-id="e0afe-110">Scope</span></span>   |<span data-ttu-id="e0afe-111">Edge</span><span class="sxs-lookup"><span data-stu-id="e0afe-111">Edge</span></span>|
|<span data-ttu-id="e0afe-112">版本</span><span class="sxs-lookup"><span data-stu-id="e0afe-112">Version</span></span>|<span data-ttu-id="e0afe-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="e0afe-113">4.5.1</span></span>|
|<span data-ttu-id="e0afe-114">類型</span><span class="sxs-lookup"><span data-stu-id="e0afe-114">Type</span></span>|<span data-ttu-id="e0afe-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="e0afe-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e0afe-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="e0afe-116">Affected APIs</span></span>

-<xref:System.Diagnostics.Tracing.EventListener.%23ctor></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords,System.Collections.Generic.IDictionary{System.String,System.String})?displayProperty=nameWithType></li></ul>|
