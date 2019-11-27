---
title: Boolean 資料類型
ms.date: 07/20/2015
f1_keywords:
- vb.FALSE
- vb.TRUE
- vb.Boolean
helpviewer_keywords:
- Boolean data type
- Boolean values [Visual Basic], False keyword
- False keyword [Visual Basic]
- True keyword [Visual Basic]
- Boolean values [Visual Basic], True keyword
ms.assetid: 4858e630-4813-4216-a55e-f4d0feb884e4
ms.openlocfilehash: 5d05514207c5d07e81aab897f40f728570f6bd87
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347852"
---
# <a name="boolean-data-type-visual-basic"></a><span data-ttu-id="b1219-102">Boolean 資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b1219-102">Boolean Data Type (Visual Basic)</span></span>

<span data-ttu-id="b1219-103">保留只能 `True` 或 `False`的值。</span><span class="sxs-lookup"><span data-stu-id="b1219-103">Holds values that can be only `True` or `False`.</span></span> <span data-ttu-id="b1219-104">`True` 和 `False` 的關鍵字會對應到 `Boolean` 變數的兩種狀態。</span><span class="sxs-lookup"><span data-stu-id="b1219-104">The keywords `True` and `False` correspond to the two states of `Boolean` variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1219-105">備註</span><span class="sxs-lookup"><span data-stu-id="b1219-105">Remarks</span></span>  

 <span data-ttu-id="b1219-106">使用[布林資料類型（Visual Basic）](../../../visual-basic/language-reference/data-types/boolean-data-type.md)來包含兩個狀態值： true/false、yes/no 或 on/off。</span><span class="sxs-lookup"><span data-stu-id="b1219-106">Use the [Boolean Data Type (Visual Basic)](../../../visual-basic/language-reference/data-types/boolean-data-type.md) to contain two-state values such as true/false, yes/no, or on/off.</span></span>  
  
 <span data-ttu-id="b1219-107">`Boolean` 的預設值為 `False`。</span><span class="sxs-lookup"><span data-stu-id="b1219-107">The default value of `Boolean` is `False`.</span></span>  
  
 <span data-ttu-id="b1219-108">`Boolean` 值不會儲存為數字，而且儲存的值不會等同于數位。</span><span class="sxs-lookup"><span data-stu-id="b1219-108">`Boolean` values are not stored as numbers, and the stored values are not intended to be equivalent to numbers.</span></span> <span data-ttu-id="b1219-109">您絕對不應該撰寫依賴對等數值進行 `True` 和 `False`的程式碼。</span><span class="sxs-lookup"><span data-stu-id="b1219-109">You should never write code that relies on equivalent numeric values for `True` and `False`.</span></span> <span data-ttu-id="b1219-110">可能的話，您應該將 `Boolean` 變數的使用限制為其設計的邏輯值。</span><span class="sxs-lookup"><span data-stu-id="b1219-110">Whenever possible, you should restrict usage of `Boolean` variables to the logical values for which they are designed.</span></span>  
  
## <a name="type-conversions"></a><span data-ttu-id="b1219-111">類型轉換</span><span class="sxs-lookup"><span data-stu-id="b1219-111">Type Conversions</span></span>  

 <span data-ttu-id="b1219-112">當 Visual Basic 將數值資料類型值轉換成 `Boolean`時，0會變成 `False`，而所有其他值會變成 `True`。</span><span class="sxs-lookup"><span data-stu-id="b1219-112">When Visual Basic converts numeric data type values to `Boolean`, 0 becomes `False` and all other values become `True`.</span></span> <span data-ttu-id="b1219-113">當 Visual Basic 將 `Boolean` 值轉換為數數值型別時，`False` 會變成0，而 `True` 會變成-1。</span><span class="sxs-lookup"><span data-stu-id="b1219-113">When Visual Basic converts `Boolean` values to numeric types, `False` becomes 0 and `True` becomes -1.</span></span>  
  
 <span data-ttu-id="b1219-114">當您在 `Boolean` 值和數值資料類型之間進行轉換時，請記住，.NET Framework 轉換方法不一定會產生與 Visual Basic 轉換關鍵字相同的結果。</span><span class="sxs-lookup"><span data-stu-id="b1219-114">When you convert between `Boolean` values and numeric data types, keep in mind that the .NET Framework conversion methods do not always produce the same results as the Visual Basic conversion keywords.</span></span> <span data-ttu-id="b1219-115">這是因為 Visual Basic 轉換會保留與先前版本相容的行為。</span><span class="sxs-lookup"><span data-stu-id="b1219-115">This is because the Visual Basic conversion retains behavior compatible with previous versions.</span></span> <span data-ttu-id="b1219-116">如需詳細資訊，請參閱[疑難排解資料類型](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)中的「布林值類型未正確轉換為數數值型別」。</span><span class="sxs-lookup"><span data-stu-id="b1219-116">For more information, see "Boolean Type Does Not Convert to Numeric Type Accurately" in [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="b1219-117">程式設計提示</span><span class="sxs-lookup"><span data-stu-id="b1219-117">Programming Tips</span></span>  
  
- <span data-ttu-id="b1219-118">**負數。**</span><span class="sxs-lookup"><span data-stu-id="b1219-118">**Negative Numbers.**</span></span> <span data-ttu-id="b1219-119">`Boolean` 不是數數值型別，而且不能代表負值。</span><span class="sxs-lookup"><span data-stu-id="b1219-119">`Boolean` is not a numeric type and cannot represent a negative value.</span></span> <span data-ttu-id="b1219-120">在任何情況下，您不應該使用 `Boolean` 來保存數值。</span><span class="sxs-lookup"><span data-stu-id="b1219-120">In any case, you should not use `Boolean` to hold numeric values.</span></span>  
  
- <span data-ttu-id="b1219-121">**輸入字元。**</span><span class="sxs-lookup"><span data-stu-id="b1219-121">**Type Characters.**</span></span> <span data-ttu-id="b1219-122">`Boolean` 沒有常數值型別字元或識別項型別字元。</span><span class="sxs-lookup"><span data-stu-id="b1219-122">`Boolean` has no literal type character or identifier type character.</span></span>  
  
- <span data-ttu-id="b1219-123">**架構類型。**</span><span class="sxs-lookup"><span data-stu-id="b1219-123">**Framework Type.**</span></span> <span data-ttu-id="b1219-124">在 .NET Framework 中對應的類型為 <xref:System.Boolean?displayProperty=nameWithType> 結構。</span><span class="sxs-lookup"><span data-stu-id="b1219-124">The corresponding type in the .NET Framework is the <xref:System.Boolean?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1219-125">範例</span><span class="sxs-lookup"><span data-stu-id="b1219-125">Example</span></span>  

 <span data-ttu-id="b1219-126">在下列範例中，`runningVB` 是 `Boolean` 變數，它會儲存簡單的 [是/否] 設定。</span><span class="sxs-lookup"><span data-stu-id="b1219-126">In the following example, `runningVB` is a `Boolean` variable, which stores a simple yes/no setting.</span></span>  
  
```vb  
Dim runningVB As Boolean  
' Check to see if program is running on Visual Basic engine.  
If scriptEngine = "VB" Then  
    runningVB = True  
End If  
```  
  
## <a name="see-also"></a><span data-ttu-id="b1219-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="b1219-127">See also</span></span>

- <xref:System.Boolean?displayProperty=nameWithType>
- [<span data-ttu-id="b1219-128">資料類型</span><span class="sxs-lookup"><span data-stu-id="b1219-128">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="b1219-129">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="b1219-129">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="b1219-130">轉換摘要</span><span class="sxs-lookup"><span data-stu-id="b1219-130">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="b1219-131">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="b1219-131">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="b1219-132">資料類型的疑難排解</span><span class="sxs-lookup"><span data-stu-id="b1219-132">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="b1219-133">CType 函式</span><span class="sxs-lookup"><span data-stu-id="b1219-133">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)
