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
ms.openlocfilehash: 851c524a83c5f24b77a151634a96798249c5905e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374417"
---
# <a name="boolean-data-type-visual-basic"></a><span data-ttu-id="dc133-102">Boolean 資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dc133-102">Boolean Data Type (Visual Basic)</span></span>

<span data-ttu-id="dc133-103">保留只能是或的值 `True` `False` 。</span><span class="sxs-lookup"><span data-stu-id="dc133-103">Holds values that can be only `True` or `False`.</span></span> <span data-ttu-id="dc133-104">關鍵字 `True` 並 `False` 對應至變數的兩個狀態 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="dc133-104">The keywords `True` and `False` correspond to the two states of `Boolean` variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc133-105">備註</span><span class="sxs-lookup"><span data-stu-id="dc133-105">Remarks</span></span>  

 <span data-ttu-id="dc133-106">使用[布林資料類型（Visual Basic）](boolean-data-type.md)來包含兩個狀態值： true/false、yes/no 或 on/off。</span><span class="sxs-lookup"><span data-stu-id="dc133-106">Use the [Boolean Data Type (Visual Basic)](boolean-data-type.md) to contain two-state values such as true/false, yes/no, or on/off.</span></span>  
  
 <span data-ttu-id="dc133-107">`Boolean` 的預設值為 `False`。</span><span class="sxs-lookup"><span data-stu-id="dc133-107">The default value of `Boolean` is `False`.</span></span>  
  
 <span data-ttu-id="dc133-108">`Boolean`值不會儲存為數字，而且儲存的值不會與數位相等。</span><span class="sxs-lookup"><span data-stu-id="dc133-108">`Boolean` values are not stored as numbers, and the stored values are not intended to be equivalent to numbers.</span></span> <span data-ttu-id="dc133-109">您絕對不應該撰寫依賴和的對等數值的程式碼 `True` `False` 。</span><span class="sxs-lookup"><span data-stu-id="dc133-109">You should never write code that relies on equivalent numeric values for `True` and `False`.</span></span> <span data-ttu-id="dc133-110">可能的話，您應該將變數的使用限制 `Boolean` 為其設計的邏輯值。</span><span class="sxs-lookup"><span data-stu-id="dc133-110">Whenever possible, you should restrict usage of `Boolean` variables to the logical values for which they are designed.</span></span>  
  
## <a name="type-conversions"></a><span data-ttu-id="dc133-111">類型轉換</span><span class="sxs-lookup"><span data-stu-id="dc133-111">Type Conversions</span></span>  

 <span data-ttu-id="dc133-112">當 Visual Basic 將數值資料類型值轉換為時 `Boolean` ，0會變成， `False` 而所有其他值會變成 `True` 。</span><span class="sxs-lookup"><span data-stu-id="dc133-112">When Visual Basic converts numeric data type values to `Boolean`, 0 becomes `False` and all other values become `True`.</span></span> <span data-ttu-id="dc133-113">當 Visual Basic 將 `Boolean` 值轉換為數數值型別時， `False` 會變成0，並 `True` 變成-1。</span><span class="sxs-lookup"><span data-stu-id="dc133-113">When Visual Basic converts `Boolean` values to numeric types, `False` becomes 0 and `True` becomes -1.</span></span>  
  
 <span data-ttu-id="dc133-114">當您在 `Boolean` 值和數值資料類型之間進行轉換時，請記住，.NET Framework 的轉換方法不一定會產生與 Visual Basic 轉換關鍵字相同的結果。</span><span class="sxs-lookup"><span data-stu-id="dc133-114">When you convert between `Boolean` values and numeric data types, keep in mind that the .NET Framework conversion methods do not always produce the same results as the Visual Basic conversion keywords.</span></span> <span data-ttu-id="dc133-115">這是因為 Visual Basic 轉換會保留與先前版本相容的行為。</span><span class="sxs-lookup"><span data-stu-id="dc133-115">This is because the Visual Basic conversion retains behavior compatible with previous versions.</span></span> <span data-ttu-id="dc133-116">如需詳細資訊，請參閱[疑難排解資料類型](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)中的「布林值類型未正確轉換為數數值型別」。</span><span class="sxs-lookup"><span data-stu-id="dc133-116">For more information, see "Boolean Type Does Not Convert to Numeric Type Accurately" in [Troubleshooting Data Types](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="dc133-117">程式設計提示</span><span class="sxs-lookup"><span data-stu-id="dc133-117">Programming Tips</span></span>  
  
- <span data-ttu-id="dc133-118">**負數。**</span><span class="sxs-lookup"><span data-stu-id="dc133-118">**Negative Numbers.**</span></span> <span data-ttu-id="dc133-119">`Boolean`不是數數值型別，而且不能代表負值。</span><span class="sxs-lookup"><span data-stu-id="dc133-119">`Boolean` is not a numeric type and cannot represent a negative value.</span></span> <span data-ttu-id="dc133-120">在任何情況下，您都不應該使用 `Boolean` 來保存數值。</span><span class="sxs-lookup"><span data-stu-id="dc133-120">In any case, you should not use `Boolean` to hold numeric values.</span></span>  
  
- <span data-ttu-id="dc133-121">**輸入字元。**</span><span class="sxs-lookup"><span data-stu-id="dc133-121">**Type Characters.**</span></span> <span data-ttu-id="dc133-122">`Boolean`沒有常數值型別字元或識別項型別字元。</span><span class="sxs-lookup"><span data-stu-id="dc133-122">`Boolean` has no literal type character or identifier type character.</span></span>  
  
- <span data-ttu-id="dc133-123">**架構類型：**</span><span class="sxs-lookup"><span data-stu-id="dc133-123">**Framework Type.**</span></span> <span data-ttu-id="dc133-124">在 .NET Framework 中對應的類型為 <xref:System.Boolean?displayProperty=nameWithType> 結構。</span><span class="sxs-lookup"><span data-stu-id="dc133-124">The corresponding type in the .NET Framework is the <xref:System.Boolean?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc133-125">範例</span><span class="sxs-lookup"><span data-stu-id="dc133-125">Example</span></span>  

 <span data-ttu-id="dc133-126">在下列範例中， `runningVB` 是一個 `Boolean` 變數，它會儲存簡單的 [是/否] 設定。</span><span class="sxs-lookup"><span data-stu-id="dc133-126">In the following example, `runningVB` is a `Boolean` variable, which stores a simple yes/no setting.</span></span>  
  
```vb  
Dim runningVB As Boolean  
' Check to see if program is running on Visual Basic engine.  
If scriptEngine = "VB" Then  
    runningVB = True  
End If  
```  
  
## <a name="see-also"></a><span data-ttu-id="dc133-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc133-127">See also</span></span>

- <xref:System.Boolean?displayProperty=nameWithType>
- [<span data-ttu-id="dc133-128">資料類型</span><span class="sxs-lookup"><span data-stu-id="dc133-128">Data Types</span></span>](index.md)
- [<span data-ttu-id="dc133-129">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="dc133-129">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="dc133-130">轉換摘要</span><span class="sxs-lookup"><span data-stu-id="dc133-130">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="dc133-131">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="dc133-131">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="dc133-132">疑難排解資料類型的問題</span><span class="sxs-lookup"><span data-stu-id="dc133-132">Troubleshooting Data Types</span></span>](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="dc133-133">CType Function</span><span class="sxs-lookup"><span data-stu-id="dc133-133">CType Function</span></span>](../functions/ctype-function.md)
