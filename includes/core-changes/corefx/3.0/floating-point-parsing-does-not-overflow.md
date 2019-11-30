---
ms.openlocfilehash: 30580b3fde5b8a99862896bb7d31c6c4024f97e8
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568193"
---
### <a name="floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception"></a><span data-ttu-id="67055-101">浮點剖析作業不再失敗或擲回 OverflowException</span><span class="sxs-lookup"><span data-stu-id="67055-101">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>

<span data-ttu-id="67055-102">浮點剖析方法不會再擲回 <xref:System.OverflowException>，或在剖析其數值超出 <xref:System.Single> 或 <xref:System.Double> 浮點類型範圍的字串時傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="67055-102">The floating-point parsing methods no longer throw an <xref:System.OverflowException> or return `false` when they parse a string whose numeric value is outside the range of the <xref:System.Single> or <xref:System.Double> floating-point type.</span></span>

#### <a name="change-description"></a><span data-ttu-id="67055-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="67055-103">Change description</span></span>

<span data-ttu-id="67055-104">在 .NET Core 2.2 和更早版本中，<xref:System.Double.Parse%2A?displayProperty=nameWithType> 和 <xref:System.Single.Parse%2A?displayProperty=nameWithType> 方法會針對超出其各自類型範圍的值擲回 <xref:System.OverflowException>。</span><span class="sxs-lookup"><span data-stu-id="67055-104">In .NET Core 2.2 and earlier versions, the <xref:System.Double.Parse%2A?displayProperty=nameWithType> and <xref:System.Single.Parse%2A?displayProperty=nameWithType> methods throw an <xref:System.OverflowException> for values that outside the range of their respective type.</span></span> <span data-ttu-id="67055-105"><xref:System.Double.TryParse%2A?displayProperty=nameWithType> 和 <xref:System.Single.TryParse%2A?displayProperty=nameWithType> 方法會針對超出範圍的數值，傳回 `false` 的字串表示。</span><span class="sxs-lookup"><span data-stu-id="67055-105">The <xref:System.Double.TryParse%2A?displayProperty=nameWithType> and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> methods return `false` for the string representations of out-of-range numeric values.</span></span>

<span data-ttu-id="67055-106">從 .NET Core 3.0 開始，在剖析超出範圍的數值字串時，<xref:System.Double.Parse%2A?displayProperty=nameWithType>、<xref:System.Double.TryParse%2A?displayProperty=nameWithType>、<xref:System.Single.Parse%2A?displayProperty=nameWithType>和 <xref:System.Single.TryParse%2A?displayProperty=nameWithType> 方法不會再失敗。</span><span class="sxs-lookup"><span data-stu-id="67055-106">Starting with .NET Core 3.0, the <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>, and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> methods no longer fail when parsing out-of-range numeric strings.</span></span> <span data-ttu-id="67055-107">相反地，<xref:System.Double> 剖析方法會針對超過 <xref:System.Double.MaxValue?displayProperty=nameWithType>的值傳回 <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>，而它們會針對小於 <xref:System.Double.MinValue?displayProperty=nameWithType>的值傳回 <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="67055-107">Instead, the <xref:System.Double> parsing methods return <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> for values that exceed <xref:System.Double.MaxValue?displayProperty=nameWithType>, and they return <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> for values that are less than <xref:System.Double.MinValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="67055-108">同樣地，<xref:System.Single> 剖析方法會針對超過 <xref:System.Single.MaxValue?displayProperty=nameWithType>的值傳回 <xref:System.Single.PositiveInfinity?displayProperty=nameWithType>，而且它們會針對小於 <xref:System.Single.MinValue?displayProperty=nameWithType>的值傳回 <xref:System.Single.NegativeInfinity?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="67055-108">Similarly, the <xref:System.Single> parsing methods return <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> for values that exceed <xref:System.Single.MaxValue?displayProperty=nameWithType>, and they return <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> for values that are less than <xref:System.Single.MinValue?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="67055-109">這是為了改善 IEEE 754:2008 合規性而進行的變更。</span><span class="sxs-lookup"><span data-stu-id="67055-109">This change was made for improved IEEE 754:2008 compliance.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="67055-110">引進的版本</span><span class="sxs-lookup"><span data-stu-id="67055-110">Version introduced</span></span>

<span data-ttu-id="67055-111">3.0</span><span class="sxs-lookup"><span data-stu-id="67055-111">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="67055-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="67055-112">Recommended action</span></span>

<span data-ttu-id="67055-113">這項變更可能會影響您的程式碼，方法有兩種：</span><span class="sxs-lookup"><span data-stu-id="67055-113">This change can affect your code in either of two ways:</span></span>

- <span data-ttu-id="67055-114">您的程式碼取決於要在發生溢位時執行 <xref:System.OverflowException> 的處理常式。</span><span class="sxs-lookup"><span data-stu-id="67055-114">Your code depends on the handler for the <xref:System.OverflowException> to execute when an overflow occurs.</span></span> <span data-ttu-id="67055-115">在此情況下，您應該移除 `catch` 語句，並將任何必要的程式碼放在 `If` 語句中，以測試是否 `true`<xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> 或 <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="67055-115">In this case, you should remove the `catch` statement and place any necessary code in an `If` statement that tests whether <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> or <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> is `true`.</span></span>

- <span data-ttu-id="67055-116">您的程式碼假設浮點值不 `Infinity`。</span><span class="sxs-lookup"><span data-stu-id="67055-116">Your code assumes that floating-point values are not `Infinity`.</span></span> <span data-ttu-id="67055-117">在此情況下，您應該加入必要的程式碼，以檢查 `PositiveInfinity` 和 `NegativeInfinity`的浮點值。</span><span class="sxs-lookup"><span data-stu-id="67055-117">In this case, you should add the necessary code to check for floating-point values of `PositiveInfinity` and `NegativeInfinity`.</span></span>

#### <a name="category"></a><span data-ttu-id="67055-118">Category</span><span class="sxs-lookup"><span data-stu-id="67055-118">Category</span></span>

<span data-ttu-id="67055-119">CoreFx</span><span class="sxs-lookup"><span data-stu-id="67055-119">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="67055-120">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="67055-120">Affected APIs</span></span>

- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->
