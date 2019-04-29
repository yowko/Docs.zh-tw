---
title: Boolean 資料類型 (Visual Basic)
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
ms.openlocfilehash: 7b64302d801a08f976de0ec969983c821f7a8471
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796990"
---
# <a name="boolean-data-type-visual-basic"></a><span data-ttu-id="c3811-102">Boolean 資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3811-102">Boolean Data Type (Visual Basic)</span></span>
<span data-ttu-id="c3811-103">可以只保留值`True`或`False`。</span><span class="sxs-lookup"><span data-stu-id="c3811-103">Holds values that can be only `True` or `False`.</span></span> <span data-ttu-id="c3811-104">關鍵字`True`並`False`對應至兩個狀態的`Boolean`變數。</span><span class="sxs-lookup"><span data-stu-id="c3811-104">The keywords `True` and `False` correspond to the two states of `Boolean` variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3811-105">備註</span><span class="sxs-lookup"><span data-stu-id="c3811-105">Remarks</span></span>  
 <span data-ttu-id="c3811-106">使用[布林資料類型 (Visual Basic)](../../../visual-basic/language-reference/data-types/boolean-data-type.md)是/否或是開/關包含兩個狀態的值，例如 true/false。</span><span class="sxs-lookup"><span data-stu-id="c3811-106">Use the [Boolean Data Type (Visual Basic)](../../../visual-basic/language-reference/data-types/boolean-data-type.md) to contain two-state values such as true/false, yes/no, or on/off.</span></span>  
  
 <span data-ttu-id="c3811-107">`Boolean` 的預設值為 `False`。</span><span class="sxs-lookup"><span data-stu-id="c3811-107">The default value of `Boolean` is `False`.</span></span>  
  
 <span data-ttu-id="c3811-108">`Boolean` 值不會儲存為 數字，並儲存的值並非為等同於數字。</span><span class="sxs-lookup"><span data-stu-id="c3811-108">`Boolean` values are not stored as numbers, and the stored values are not intended to be equivalent to numbers.</span></span> <span data-ttu-id="c3811-109">您不需撰寫程式碼，以針對對等數值`True`和`False`。</span><span class="sxs-lookup"><span data-stu-id="c3811-109">You should never write code that relies on equivalent numeric values for `True` and `False`.</span></span> <span data-ttu-id="c3811-110">可能的話，您應該限制的使用方式`Boolean`它們設計的邏輯值的變數。</span><span class="sxs-lookup"><span data-stu-id="c3811-110">Whenever possible, you should restrict usage of `Boolean` variables to the logical values for which they are designed.</span></span>  
  
## <a name="type-conversions"></a><span data-ttu-id="c3811-111">類型轉換</span><span class="sxs-lookup"><span data-stu-id="c3811-111">Type Conversions</span></span>  
 <span data-ttu-id="c3811-112">當 Visual Basic 數值資料型別將值轉換成`Boolean`，0 會變成`False`和所有其他值會變成`True`。</span><span class="sxs-lookup"><span data-stu-id="c3811-112">When Visual Basic converts numeric data type values to `Boolean`, 0 becomes `False` and all other values become `True`.</span></span> <span data-ttu-id="c3811-113">當 Visual Basic 會將轉換`Boolean`為數字類型，值`False`會變成 0 和`True`變成-1。</span><span class="sxs-lookup"><span data-stu-id="c3811-113">When Visual Basic converts `Boolean` values to numeric types, `False` becomes 0 and `True` becomes -1.</span></span>  
  
 <span data-ttu-id="c3811-114">當您將轉換之間`Boolean`值和數值資料類型，請記住，.NET Framework 轉換方法不一定會產生與 Visual Basic 轉換關鍵字相同的結果。</span><span class="sxs-lookup"><span data-stu-id="c3811-114">When you convert between `Boolean` values and numeric data types, keep in mind that the .NET Framework conversion methods do not always produce the same results as the Visual Basic conversion keywords.</span></span> <span data-ttu-id="c3811-115">這是因為 Visual Basic 轉換會保留與舊版相容的行為。</span><span class="sxs-lookup"><span data-stu-id="c3811-115">This is because the Visual Basic conversion retains behavior compatible with previous versions.</span></span> <span data-ttu-id="c3811-116">如需詳細資訊，請參閱"布林類型不會無法轉換以數值類型正確 」 中[疑難排解資料型別](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="c3811-116">For more information, see "Boolean Type Does Not Convert to Numeric Type Accurately" in [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="c3811-117">程式設計提示</span><span class="sxs-lookup"><span data-stu-id="c3811-117">Programming Tips</span></span>  
  
- <span data-ttu-id="c3811-118">**負數的數字。**</span><span class="sxs-lookup"><span data-stu-id="c3811-118">**Negative Numbers.**</span></span> <span data-ttu-id="c3811-119">`Boolean` 不是數值類型，因此無法表示為負數值。</span><span class="sxs-lookup"><span data-stu-id="c3811-119">`Boolean` is not a numeric type and cannot represent a negative value.</span></span> <span data-ttu-id="c3811-120">在任何情況下，您不應該使用`Boolean`來保存數字值。</span><span class="sxs-lookup"><span data-stu-id="c3811-120">In any case, you should not use `Boolean` to hold numeric values.</span></span>  
  
- <span data-ttu-id="c3811-121">**類型字元。**</span><span class="sxs-lookup"><span data-stu-id="c3811-121">**Type Characters.**</span></span> <span data-ttu-id="c3811-122">`Boolean` 沒有任何常值類型字元或識別項類型字元。</span><span class="sxs-lookup"><span data-stu-id="c3811-122">`Boolean` has no literal type character or identifier type character.</span></span>  
  
- <span data-ttu-id="c3811-123">**Framework 型別。**</span><span class="sxs-lookup"><span data-stu-id="c3811-123">**Framework Type.**</span></span> <span data-ttu-id="c3811-124">在 .NET Framework 中對應的類型為 <xref:System.Boolean?displayProperty=nameWithType> 結構。</span><span class="sxs-lookup"><span data-stu-id="c3811-124">The corresponding type in the .NET Framework is the <xref:System.Boolean?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3811-125">範例</span><span class="sxs-lookup"><span data-stu-id="c3811-125">Example</span></span>  
 <span data-ttu-id="c3811-126">在下列範例中，`runningVB`是`Boolean`儲存是/否設定簡單的變數。</span><span class="sxs-lookup"><span data-stu-id="c3811-126">In the following example, `runningVB` is a `Boolean` variable, which stores a simple yes/no setting.</span></span>  
  
```  
Dim runningVB As Boolean  
' Check to see if program is running on Visual Basic engine.  
If scriptEngine = "VB" Then  
    runningVB = True  
End If  
```  
  
## <a name="see-also"></a><span data-ttu-id="c3811-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3811-127">See also</span></span>

- <xref:System.Boolean?displayProperty=nameWithType>
- [<span data-ttu-id="c3811-128">資料類型</span><span class="sxs-lookup"><span data-stu-id="c3811-128">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="c3811-129">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="c3811-129">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="c3811-130">轉換摘要</span><span class="sxs-lookup"><span data-stu-id="c3811-130">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="c3811-131">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="c3811-131">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="c3811-132">資料類型的疑難排解</span><span class="sxs-lookup"><span data-stu-id="c3811-132">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="c3811-133">CType 函式</span><span class="sxs-lookup"><span data-stu-id="c3811-133">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)
