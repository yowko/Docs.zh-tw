---
ms.openlocfilehash: 935d9b2368ea4a0eeca7943dcbd584d24d2a6633
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032013"
---
### <a name="floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception"></a><span data-ttu-id="b2347-101">浮點數剖析作業不再失敗或擲回 >overflowexception</span><span class="sxs-lookup"><span data-stu-id="b2347-101">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>

<span data-ttu-id="b2347-102">當浮點剖析方法 <xref:System.OverflowException> `false` 剖析的字串值超出 <xref:System.Single> 或浮點類型的範圍時，不會再擲回或傳回 <xref:System.Double> 。</span><span class="sxs-lookup"><span data-stu-id="b2347-102">The floating-point parsing methods no longer throw an <xref:System.OverflowException> or return `false` when they parse a string whose numeric value is outside the range of the <xref:System.Single> or <xref:System.Double> floating-point type.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b2347-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="b2347-103">Change description</span></span>

<span data-ttu-id="b2347-104">在 .NET Core 2.2 和較早的版本中， <xref:System.Double.Parse%2A?displayProperty=nameWithType> 和 <xref:System.Single.Parse%2A?displayProperty=nameWithType> 方法 <xref:System.OverflowException> 會針對其各自類型範圍之外的值擲回。</span><span class="sxs-lookup"><span data-stu-id="b2347-104">In .NET Core 2.2 and earlier versions, the <xref:System.Double.Parse%2A?displayProperty=nameWithType> and <xref:System.Single.Parse%2A?displayProperty=nameWithType> methods throw an <xref:System.OverflowException> for values that outside the range of their respective type.</span></span> <span data-ttu-id="b2347-105"><xref:System.Double.TryParse%2A?displayProperty=nameWithType>和 <xref:System.Single.TryParse%2A?displayProperty=nameWithType> 方法會 `false` 針對超出範圍數值的字串表示傳回。</span><span class="sxs-lookup"><span data-stu-id="b2347-105">The <xref:System.Double.TryParse%2A?displayProperty=nameWithType> and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> methods return `false` for the string representations of out-of-range numeric values.</span></span>

<span data-ttu-id="b2347-106">從 .net Core 3.0 開始， <xref:System.Double.Parse%2A?displayProperty=nameWithType> <xref:System.Double.TryParse%2A?displayProperty=nameWithType> <xref:System.Single.Parse%2A?displayProperty=nameWithType> <xref:System.Single.TryParse%2A?displayProperty=nameWithType> 當剖析超出範圍的數值字串時，、、和方法不會再失敗。</span><span class="sxs-lookup"><span data-stu-id="b2347-106">Starting with .NET Core 3.0, the <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>, and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> methods no longer fail when parsing out-of-range numeric strings.</span></span> <span data-ttu-id="b2347-107">相反地， <xref:System.Double> 剖析方法 <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> 會傳回超過的值 <xref:System.Double.MaxValue?displayProperty=nameWithType> ，而且會 <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> 針對小於 <xref:System.Double.MinValue?displayProperty=nameWithType> 的值傳回。</span><span class="sxs-lookup"><span data-stu-id="b2347-107">Instead, the <xref:System.Double> parsing methods return <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> for values that exceed <xref:System.Double.MaxValue?displayProperty=nameWithType>, and they return <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> for values that are less than <xref:System.Double.MinValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b2347-108">同樣地， <xref:System.Single> 剖析方法 <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> 會傳回超過的值 <xref:System.Single.MaxValue?displayProperty=nameWithType> ，而且會 <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> 針對小於 <xref:System.Single.MinValue?displayProperty=nameWithType> 的值傳回。</span><span class="sxs-lookup"><span data-stu-id="b2347-108">Similarly, the <xref:System.Single> parsing methods return <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> for values that exceed <xref:System.Single.MaxValue?displayProperty=nameWithType>, and they return <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> for values that are less than <xref:System.Single.MinValue?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="b2347-109">這是為了改善 IEEE 754:2008 合規性所做的變更。</span><span class="sxs-lookup"><span data-stu-id="b2347-109">This change was made for improved IEEE 754:2008 compliance.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b2347-110">引進的版本</span><span class="sxs-lookup"><span data-stu-id="b2347-110">Version introduced</span></span>

<span data-ttu-id="b2347-111">3.0</span><span class="sxs-lookup"><span data-stu-id="b2347-111">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b2347-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="b2347-112">Recommended action</span></span>

<span data-ttu-id="b2347-113">這項變更可能會影響您的程式碼，方法有兩種：</span><span class="sxs-lookup"><span data-stu-id="b2347-113">This change can affect your code in either of two ways:</span></span>

- <span data-ttu-id="b2347-114">您的程式碼取決於在 <xref:System.OverflowException> 發生溢位時要執行的處理常式。</span><span class="sxs-lookup"><span data-stu-id="b2347-114">Your code depends on the handler for the <xref:System.OverflowException> to execute when an overflow occurs.</span></span> <span data-ttu-id="b2347-115">在此情況下，您應該移除 `catch` 語句，並將任何必要的程式碼放在 `If` 測試或是否為的語句中 <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> `true` 。</span><span class="sxs-lookup"><span data-stu-id="b2347-115">In this case, you should remove the `catch` statement and place any necessary code in an `If` statement that tests whether <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> or <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> is `true`.</span></span>

- <span data-ttu-id="b2347-116">您的程式碼假設浮點值不是 `Infinity` 。</span><span class="sxs-lookup"><span data-stu-id="b2347-116">Your code assumes that floating-point values are not `Infinity`.</span></span> <span data-ttu-id="b2347-117">在此情況下，您應該加入必要的程式碼，以檢查和的浮點 `PositiveInfinity` 值 `NegativeInfinity` 。</span><span class="sxs-lookup"><span data-stu-id="b2347-117">In this case, you should add the necessary code to check for floating-point values of `PositiveInfinity` and `NegativeInfinity`.</span></span>

#### <a name="category"></a><span data-ttu-id="b2347-118">類別</span><span class="sxs-lookup"><span data-stu-id="b2347-118">Category</span></span>

<span data-ttu-id="b2347-119">Core .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="b2347-119">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b2347-120">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="b2347-120">Affected APIs</span></span>

- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->
