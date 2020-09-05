---
ms.openlocfilehash: 06424c4fa40343a881356c20003300f65e93efbb
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496770"
---
### <a name="wf-serializes-expressionsliterallttgt-datetimes-differently-now-breaks-custom-xaml-parsers"></a><span data-ttu-id="51182-101">WF 現在會以不同的方式來序列化 Expressions.Literal&lt;T&gt; DateTimes (中斷自訂 XAML 剖析器)</span><span class="sxs-lookup"><span data-stu-id="51182-101">WF serializes Expressions.Literal&lt;T&gt; DateTimes differently now (breaks custom XAML parsers)</span></span>

#### <a name="details"></a><span data-ttu-id="51182-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="51182-102">Details</span></span>

<span data-ttu-id="51182-103">相關聯的 <xref:System.Windows.Markup.ValueSerializer> 物件會將 Second 和 <xref:System.DateTime.Millisecond?displayProperty=fullName> 元件為非零且 (針對 <xref:System.DateTime?displayProperty=fullName> 值) <xref:System.DateTime.Kind> 屬性不是 Unspecified 的 <xref:System.DateTime?displayProperty=fullName> 或 <xref:System.DateTimeOffset?displayProperty=fullName> 物件轉換為屬性項目語法，而非字串。</span><span class="sxs-lookup"><span data-stu-id="51182-103">The associated <xref:System.Windows.Markup.ValueSerializer> object will convert a <xref:System.DateTime?displayProperty=fullName> or <xref:System.DateTimeOffset?displayProperty=fullName> object whose Second and <xref:System.DateTime.Millisecond?displayProperty=fullName> components are non-zero and (for a <xref:System.DateTime?displayProperty=fullName> value) whose <xref:System.DateTime.Kind> property is not Unspecified to property element syntax instead of a string.</span></span> <span data-ttu-id="51182-104">這項變更會允許往返 <xref:System.DateTime?displayProperty=fullName> 和 <xref:System.DateTimeOffset?displayProperty=fullName> 值。</span><span class="sxs-lookup"><span data-stu-id="51182-104">This change allows <xref:System.DateTime?displayProperty=fullName> and <xref:System.DateTimeOffset?displayProperty=fullName> values to be round-tripped.</span></span> <span data-ttu-id="51182-105">假設輸入 XAML 是使用屬性語法的自訂 XAML 剖析器將無法正常運作。</span><span class="sxs-lookup"><span data-stu-id="51182-105">Custom XAML parsers that assume that input XAML is in the attribute syntax will not function correctly.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="51182-106">建議</span><span class="sxs-lookup"><span data-stu-id="51182-106">Suggestion</span></span>

<span data-ttu-id="51182-107">這項變更會允許往返 <xref:System.DateTime?displayProperty=fullName> 和 <xref:System.DateTimeOffset?displayProperty=fullName> 值。</span><span class="sxs-lookup"><span data-stu-id="51182-107">This change allows <xref:System.DateTime?displayProperty=fullName> and <xref:System.DateTimeOffset?displayProperty=fullName> values to be round-tripped.</span></span> <span data-ttu-id="51182-108">假設輸入 XAML 是使用屬性語法的自訂 XAML 剖析器將無法正常運作。</span><span class="sxs-lookup"><span data-stu-id="51182-108">Custom XAML parsers that assume that input XAML is in the attribute syntax will not function correctly.</span></span>

| <span data-ttu-id="51182-109">名稱</span><span class="sxs-lookup"><span data-stu-id="51182-109">Name</span></span>    | <span data-ttu-id="51182-110">值</span><span class="sxs-lookup"><span data-stu-id="51182-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="51182-111">範圍</span><span class="sxs-lookup"><span data-stu-id="51182-111">Scope</span></span>   |<span data-ttu-id="51182-112">Edge</span><span class="sxs-lookup"><span data-stu-id="51182-112">Edge</span></span>|
|<span data-ttu-id="51182-113">版本</span><span class="sxs-lookup"><span data-stu-id="51182-113">Version</span></span>|<span data-ttu-id="51182-114">4.5</span><span class="sxs-lookup"><span data-stu-id="51182-114">4.5</span></span>|
|<span data-ttu-id="51182-115">類型</span><span class="sxs-lookup"><span data-stu-id="51182-115">Type</span></span>|<span data-ttu-id="51182-116">執行階段</span><span class="sxs-lookup"><span data-stu-id="51182-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="51182-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="51182-117">Affected APIs</span></span>

<span data-ttu-id="51182-118">無法透過 API 分析偵測。</span><span class="sxs-lookup"><span data-stu-id="51182-118">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
