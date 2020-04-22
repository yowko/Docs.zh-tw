---
ms.openlocfilehash: 87ada29e70a94c39e7ffb74767b99d49c52444af
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021549"
---
### <a name="floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception"></a><span data-ttu-id="d8921-101">浮點分析操作不再失敗或引發溢出異常</span><span class="sxs-lookup"><span data-stu-id="d8921-101">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>

<span data-ttu-id="d8921-102">浮點解析方法在解析其<xref:System.OverflowException>數值`false`<xref:System.Single>超出<xref:System.Double>或 浮點類型範圍的字串時不再引發 或返回。</span><span class="sxs-lookup"><span data-stu-id="d8921-102">The floating-point parsing methods no longer throw an <xref:System.OverflowException> or return `false` when they parse a string whose numeric value is outside the range of the <xref:System.Single> or <xref:System.Double> floating-point type.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d8921-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="d8921-103">Change description</span></span>

<span data-ttu-id="d8921-104">在 .NET Core 2.2 與<xref:System.Double.Parse%2A?displayProperty=nameWithType>早期<xref:System.OverflowException><xref:System.Single.Parse%2A?displayProperty=nameWithType>版本中,和方法將為其各自類型範圍之外的值引發 。</span><span class="sxs-lookup"><span data-stu-id="d8921-104">In .NET Core 2.2 and earlier versions, the <xref:System.Double.Parse%2A?displayProperty=nameWithType> and <xref:System.Single.Parse%2A?displayProperty=nameWithType> methods throw an <xref:System.OverflowException> for values that outside the range of their respective type.</span></span> <span data-ttu-id="d8921-105">和<xref:System.Double.TryParse%2A?displayProperty=nameWithType><xref:System.Single.TryParse%2A?displayProperty=nameWithType>方法返回`false`範圍外數值的字串表示形式。</span><span class="sxs-lookup"><span data-stu-id="d8921-105">The <xref:System.Double.TryParse%2A?displayProperty=nameWithType> and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> methods return `false` for the string representations of out-of-range numeric values.</span></span>

<span data-ttu-id="d8921-106">從 .NET Core <xref:System.Double.Parse%2A?displayProperty=nameWithType> <xref:System.Double.TryParse%2A?displayProperty=nameWithType>3.0 開始<xref:System.Single.Parse%2A?displayProperty=nameWithType>, <xref:System.Single.TryParse%2A?displayProperty=nameWithType> , 和 方法在分析範圍外的數位字串時不再失敗。</span><span class="sxs-lookup"><span data-stu-id="d8921-106">Starting with .NET Core 3.0, the <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>, and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> methods no longer fail when parsing out-of-range numeric strings.</span></span> <span data-ttu-id="d8921-107"><xref:System.Double>相反,分析方法返回<xref:System.Double.PositiveInfinity?displayProperty=nameWithType>超過<xref:System.Double.MaxValue?displayProperty=nameWithType>的值,並且返回<xref:System.Double.NegativeInfinity?displayProperty=nameWithType>小<xref:System.Double.MinValue?displayProperty=nameWithType>於的值。</span><span class="sxs-lookup"><span data-stu-id="d8921-107">Instead, the <xref:System.Double> parsing methods return <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> for values that exceed <xref:System.Double.MaxValue?displayProperty=nameWithType>, and they return <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> for values that are less than <xref:System.Double.MinValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d8921-108"><xref:System.Single>同樣,分析方法返回<xref:System.Single.PositiveInfinity?displayProperty=nameWithType>超過<xref:System.Single.MaxValue?displayProperty=nameWithType>的值,並且返回<xref:System.Single.NegativeInfinity?displayProperty=nameWithType>小<xref:System.Single.MinValue?displayProperty=nameWithType>於的值。</span><span class="sxs-lookup"><span data-stu-id="d8921-108">Similarly, the <xref:System.Single> parsing methods return <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> for values that exceed <xref:System.Single.MaxValue?displayProperty=nameWithType>, and they return <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> for values that are less than <xref:System.Single.MinValue?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="d8921-109">此更改是為了改進 IEEE 754:2008 合規性。</span><span class="sxs-lookup"><span data-stu-id="d8921-109">This change was made for improved IEEE 754:2008 compliance.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d8921-110">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="d8921-110">Version introduced</span></span>

<span data-ttu-id="d8921-111">3.0</span><span class="sxs-lookup"><span data-stu-id="d8921-111">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d8921-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="d8921-112">Recommended action</span></span>

<span data-ttu-id="d8921-113">此變更可以通過兩種方式之一影響代碼:</span><span class="sxs-lookup"><span data-stu-id="d8921-113">This change can affect your code in either of two ways:</span></span>

- <span data-ttu-id="d8921-114">代碼取決於在發生溢出時<xref:System.OverflowException>要執行的處理程式。</span><span class="sxs-lookup"><span data-stu-id="d8921-114">Your code depends on the handler for the <xref:System.OverflowException> to execute when an overflow occurs.</span></span> <span data-ttu-id="d8921-115">在這種情況下,應刪除語句`catch`,並將任何必要的代碼放在測試`If`<xref:System.Double.IsInfinity%2A?displayProperty=nameWithType><xref:System.Single.IsInfinity%2A?displayProperty=nameWithType>`true`是否為的語句中。</span><span class="sxs-lookup"><span data-stu-id="d8921-115">In this case, you should remove the `catch` statement and place any necessary code in an `If` statement that tests whether <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> or <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> is `true`.</span></span>

- <span data-ttu-id="d8921-116">您的代碼假的浮點值不是`Infinity`。</span><span class="sxs-lookup"><span data-stu-id="d8921-116">Your code assumes that floating-point values are not `Infinity`.</span></span> <span data-ttu-id="d8921-117">在這種情況下,應添加必要的代碼來檢查和`PositiveInfinity``NegativeInfinity`的浮點值。</span><span class="sxs-lookup"><span data-stu-id="d8921-117">In this case, you should add the necessary code to check for floating-point values of `PositiveInfinity` and `NegativeInfinity`.</span></span>

#### <a name="category"></a><span data-ttu-id="d8921-118">類別</span><span class="sxs-lookup"><span data-stu-id="d8921-118">Category</span></span>

<span data-ttu-id="d8921-119">核心 .NET 函式庫</span><span class="sxs-lookup"><span data-stu-id="d8921-119">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d8921-120">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="d8921-120">Affected APIs</span></span>

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
