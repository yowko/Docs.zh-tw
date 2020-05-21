---
ms.openlocfilehash: 935d9b2368ea4a0eeca7943dcbd584d24d2a6633
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83720974"
---
### <a name="floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception"></a><span data-ttu-id="ad21f-101">浮點剖析作業不再失敗或擲回 OverflowException</span><span class="sxs-lookup"><span data-stu-id="ad21f-101">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>

<span data-ttu-id="ad21f-102"><xref:System.OverflowException> `false` 當它們剖析的字串的數值超出 <xref:System.Single> 或 <xref:System.Double> 浮點數類型的範圍時，浮點剖析方法不會再擲回或傳回。</span><span class="sxs-lookup"><span data-stu-id="ad21f-102">The floating-point parsing methods no longer throw an <xref:System.OverflowException> or return `false` when they parse a string whose numeric value is outside the range of the <xref:System.Single> or <xref:System.Double> floating-point type.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ad21f-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="ad21f-103">Change description</span></span>

<span data-ttu-id="ad21f-104">在 .NET Core 2.2 和更早版本中， <xref:System.Double.Parse%2A?displayProperty=nameWithType> 和 <xref:System.Single.Parse%2A?displayProperty=nameWithType> 方法 <xref:System.OverflowException> 會針對超出其各自類型範圍的值擲回。</span><span class="sxs-lookup"><span data-stu-id="ad21f-104">In .NET Core 2.2 and earlier versions, the <xref:System.Double.Parse%2A?displayProperty=nameWithType> and <xref:System.Single.Parse%2A?displayProperty=nameWithType> methods throw an <xref:System.OverflowException> for values that outside the range of their respective type.</span></span> <span data-ttu-id="ad21f-105"><xref:System.Double.TryParse%2A?displayProperty=nameWithType>和 <xref:System.Single.TryParse%2A?displayProperty=nameWithType> 方法會 `false` 針對超出範圍的數值，傳回字串表示。</span><span class="sxs-lookup"><span data-stu-id="ad21f-105">The <xref:System.Double.TryParse%2A?displayProperty=nameWithType> and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> methods return `false` for the string representations of out-of-range numeric values.</span></span>

<span data-ttu-id="ad21f-106">從 .net Core 3.0 開始，在 <xref:System.Double.Parse%2A?displayProperty=nameWithType> <xref:System.Double.TryParse%2A?displayProperty=nameWithType> <xref:System.Single.Parse%2A?displayProperty=nameWithType> <xref:System.Single.TryParse%2A?displayProperty=nameWithType> 剖析超出範圍的數值字串時，、、和方法不會再失敗。</span><span class="sxs-lookup"><span data-stu-id="ad21f-106">Starting with .NET Core 3.0, the <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>, and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> methods no longer fail when parsing out-of-range numeric strings.</span></span> <span data-ttu-id="ad21f-107">相反地， <xref:System.Double> 剖析方法 <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> 會針對超過的值傳回 <xref:System.Double.MaxValue?displayProperty=nameWithType> ，而它們 <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> 會針對小於的值傳回 <xref:System.Double.MinValue?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="ad21f-107">Instead, the <xref:System.Double> parsing methods return <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> for values that exceed <xref:System.Double.MaxValue?displayProperty=nameWithType>, and they return <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> for values that are less than <xref:System.Double.MinValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ad21f-108">同樣地， <xref:System.Single> 剖析方法 <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> 會針對超過的值傳回 <xref:System.Single.MaxValue?displayProperty=nameWithType> ，而它們 <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> 會針對小於的值傳回 <xref:System.Single.MinValue?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="ad21f-108">Similarly, the <xref:System.Single> parsing methods return <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> for values that exceed <xref:System.Single.MaxValue?displayProperty=nameWithType>, and they return <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> for values that are less than <xref:System.Single.MinValue?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="ad21f-109">這是為了改善 IEEE 754:2008 合規性而進行的變更。</span><span class="sxs-lookup"><span data-stu-id="ad21f-109">This change was made for improved IEEE 754:2008 compliance.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ad21f-110">引進的版本</span><span class="sxs-lookup"><span data-stu-id="ad21f-110">Version introduced</span></span>

<span data-ttu-id="ad21f-111">3.0</span><span class="sxs-lookup"><span data-stu-id="ad21f-111">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ad21f-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="ad21f-112">Recommended action</span></span>

<span data-ttu-id="ad21f-113">這項變更可能會影響您的程式碼，方法有兩種：</span><span class="sxs-lookup"><span data-stu-id="ad21f-113">This change can affect your code in either of two ways:</span></span>

- <span data-ttu-id="ad21f-114">您的程式碼相依于的處理常式， <xref:System.OverflowException> 以便在發生溢位時執行。</span><span class="sxs-lookup"><span data-stu-id="ad21f-114">Your code depends on the handler for the <xref:System.OverflowException> to execute when an overflow occurs.</span></span> <span data-ttu-id="ad21f-115">在此情況下，您應該移除 `catch` 語句，並將任何必要的程式碼放在 `If` 測試是否為的語句中 <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> `true` 。</span><span class="sxs-lookup"><span data-stu-id="ad21f-115">In this case, you should remove the `catch` statement and place any necessary code in an `If` statement that tests whether <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> or <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> is `true`.</span></span>

- <span data-ttu-id="ad21f-116">您的程式碼假設浮點值不是 `Infinity` 。</span><span class="sxs-lookup"><span data-stu-id="ad21f-116">Your code assumes that floating-point values are not `Infinity`.</span></span> <span data-ttu-id="ad21f-117">在此情況下，您應該加入必要的程式碼，以檢查和的浮點 `PositiveInfinity` 值 `NegativeInfinity` 。</span><span class="sxs-lookup"><span data-stu-id="ad21f-117">In this case, you should add the necessary code to check for floating-point values of `PositiveInfinity` and `NegativeInfinity`.</span></span>

#### <a name="category"></a><span data-ttu-id="ad21f-118">類別</span><span class="sxs-lookup"><span data-stu-id="ad21f-118">Category</span></span>

<span data-ttu-id="ad21f-119">Core .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="ad21f-119">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ad21f-120">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="ad21f-120">Affected APIs</span></span>

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
