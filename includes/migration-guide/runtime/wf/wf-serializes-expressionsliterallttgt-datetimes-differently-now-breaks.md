---
ms.openlocfilehash: 87013a04f7ff975e40a3c49c41c1c5acc2374066
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620078"
---
### <a name="wf-serializes-expressionsliterallttgt-datetimes-differently-now-breaks-custom-xaml-parsers"></a><span data-ttu-id="4036a-101">WF 現在會以不同的方式來序列化 Expressions.Literal&lt;T&gt; DateTimes (中斷自訂 XAML 剖析器)</span><span class="sxs-lookup"><span data-stu-id="4036a-101">WF serializes Expressions.Literal&lt;T&gt; DateTimes differently now (breaks custom XAML parsers)</span></span>

#### <a name="details"></a><span data-ttu-id="4036a-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="4036a-102">Details</span></span>

<span data-ttu-id="4036a-103">相關聯的 <xref:System.Windows.Markup.ValueSerializer> 物件會將 Second 和 <xref:System.DateTime.Millisecond?displayProperty=fullName> 元件為非零且 (針對 <xref:System.DateTime?displayProperty=fullName> 值) <xref:System.DateTime.Kind> 屬性不是 Unspecified 的 <xref:System.DateTime?displayProperty=fullName> 或 <xref:System.DateTimeOffset?displayProperty=fullName> 物件轉換為屬性項目語法，而非字串。</span><span class="sxs-lookup"><span data-stu-id="4036a-103">The associated <xref:System.Windows.Markup.ValueSerializer> object will convert a <xref:System.DateTime?displayProperty=fullName> or <xref:System.DateTimeOffset?displayProperty=fullName> object whose Second and <xref:System.DateTime.Millisecond?displayProperty=fullName> components are non-zero and (for a <xref:System.DateTime?displayProperty=fullName> value) whose <xref:System.DateTime.Kind> property is not Unspecified to property element syntax instead of a string.</span></span> <span data-ttu-id="4036a-104">這項變更會允許往返 <xref:System.DateTime?displayProperty=fullName> 和 <xref:System.DateTimeOffset?displayProperty=fullName> 值。</span><span class="sxs-lookup"><span data-stu-id="4036a-104">This change allows <xref:System.DateTime?displayProperty=fullName> and <xref:System.DateTimeOffset?displayProperty=fullName> values to be round-tripped.</span></span> <span data-ttu-id="4036a-105">假設輸入 XAML 是使用屬性語法的自訂 XAML 剖析器將無法正常運作。</span><span class="sxs-lookup"><span data-stu-id="4036a-105">Custom XAML parsers that assume that input XAML is in the attribute syntax will not function correctly.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4036a-106">建議</span><span class="sxs-lookup"><span data-stu-id="4036a-106">Suggestion</span></span>

<span data-ttu-id="4036a-107">這項變更會允許往返 <xref:System.DateTime?displayProperty=fullName> 和 <xref:System.DateTimeOffset?displayProperty=fullName> 值。</span><span class="sxs-lookup"><span data-stu-id="4036a-107">This change allows <xref:System.DateTime?displayProperty=fullName> and <xref:System.DateTimeOffset?displayProperty=fullName> values to be round-tripped.</span></span> <span data-ttu-id="4036a-108">假設輸入 XAML 是使用屬性語法的自訂 XAML 剖析器將無法正常運作。</span><span class="sxs-lookup"><span data-stu-id="4036a-108">Custom XAML parsers that assume that input XAML is in the attribute syntax will not function correctly.</span></span>

| <span data-ttu-id="4036a-109">名稱</span><span class="sxs-lookup"><span data-stu-id="4036a-109">Name</span></span>    | <span data-ttu-id="4036a-110">值</span><span class="sxs-lookup"><span data-stu-id="4036a-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4036a-111">影響範圍</span><span class="sxs-lookup"><span data-stu-id="4036a-111">Scope</span></span>   |<span data-ttu-id="4036a-112">Edge</span><span class="sxs-lookup"><span data-stu-id="4036a-112">Edge</span></span>|
|<span data-ttu-id="4036a-113">版本</span><span class="sxs-lookup"><span data-stu-id="4036a-113">Version</span></span>|<span data-ttu-id="4036a-114">4.5</span><span class="sxs-lookup"><span data-stu-id="4036a-114">4.5</span></span>|
|<span data-ttu-id="4036a-115">類型</span><span class="sxs-lookup"><span data-stu-id="4036a-115">Type</span></span>|<span data-ttu-id="4036a-116">執行階段</span><span class="sxs-lookup"><span data-stu-id="4036a-116">Runtime</span></span>|
