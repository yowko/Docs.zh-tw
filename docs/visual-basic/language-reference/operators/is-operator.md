---
title: Is 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
ms.openlocfilehash: 0351d224d9bf08a8f3ca74090de7b9c51c2c61bf
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701371"
---
# <a name="is-operator-visual-basic"></a><span data-ttu-id="787c0-102">Is 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="787c0-102">Is Operator (Visual Basic)</span></span>
<span data-ttu-id="787c0-103">比較兩個物件參考變數。</span><span class="sxs-lookup"><span data-stu-id="787c0-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="787c0-104">語法</span><span class="sxs-lookup"><span data-stu-id="787c0-104">Syntax</span></span>  
  
```vb  
result = object1 Is object2  
```  
  
## <a name="parts"></a><span data-ttu-id="787c0-105">組件</span><span class="sxs-lookup"><span data-stu-id="787c0-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="787c0-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="787c0-106">Required.</span></span> <span data-ttu-id="787c0-107">任何 `Boolean` 值。</span><span class="sxs-lookup"><span data-stu-id="787c0-107">Any `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="787c0-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="787c0-108">Required.</span></span> <span data-ttu-id="787c0-109">任何 `Object` 名稱。</span><span class="sxs-lookup"><span data-stu-id="787c0-109">Any `Object` name.</span></span>  
  
 `object2`  
 <span data-ttu-id="787c0-110">必要項。</span><span class="sxs-lookup"><span data-stu-id="787c0-110">Required.</span></span> <span data-ttu-id="787c0-111">任何 `Object` 名稱。</span><span class="sxs-lookup"><span data-stu-id="787c0-111">Any `Object` name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="787c0-112">備註</span><span class="sxs-lookup"><span data-stu-id="787c0-112">Remarks</span></span>  
 <span data-ttu-id="787c0-113">@No__t-0 運算子會判斷兩個物件參考是否參考相同的物件。</span><span class="sxs-lookup"><span data-stu-id="787c0-113">The `Is` operator determines if two object references refer to the same object.</span></span> <span data-ttu-id="787c0-114">不過，它不會執行值比較。</span><span class="sxs-lookup"><span data-stu-id="787c0-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="787c0-115">如果 `object1` 和 `object2` 都參考完全相同的物件實例，`result` 會 `True`;如果不是，`result` `False`。</span><span class="sxs-lookup"><span data-stu-id="787c0-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `True`; if they do not, `result` is `False`.</span></span>  
  
 <span data-ttu-id="787c0-116">`Is` 也可以與 `TypeOf` 關鍵字搭配使用，以建立 `TypeOf` ... `Is` 運算式，以測試物件變數是否與資料類型相容。</span><span class="sxs-lookup"><span data-stu-id="787c0-116">`Is` can also be used with the `TypeOf` keyword to make a `TypeOf`...`Is` expression, which tests whether an object variable is compatible with a data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="787c0-117">[@No__t-0] 關鍵字也用於 [[選取 ...]Case 語句](../../../visual-basic/language-reference/statements/select-case-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="787c0-117">The `Is` keyword is also used in the [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="787c0-118">範例</span><span class="sxs-lookup"><span data-stu-id="787c0-118">Example</span></span>  
 <span data-ttu-id="787c0-119">下列範例會使用 `Is` 運算子來比較物件參考的配對。</span><span class="sxs-lookup"><span data-stu-id="787c0-119">The following example uses the `Is` operator to compare pairs of object references.</span></span> <span data-ttu-id="787c0-120">結果會指派給 @no__t 0 值，表示兩個物件是否相同。</span><span class="sxs-lookup"><span data-stu-id="787c0-120">The results are assigned to a `Boolean` value representing whether the two objects are identical.</span></span>  
  
 [!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]  
  
 <span data-ttu-id="787c0-121">如上述範例所示，您可以使用 `Is` 運算子來測試早期繫結和晚期繫結物件。</span><span class="sxs-lookup"><span data-stu-id="787c0-121">As the preceding example demonstrates, you can use the `Is` operator to test both early bound and late bound objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="787c0-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="787c0-122">See also</span></span>

- [<span data-ttu-id="787c0-123">TypeOf 運算子</span><span class="sxs-lookup"><span data-stu-id="787c0-123">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [<span data-ttu-id="787c0-124">IsNot 運算子</span><span class="sxs-lookup"><span data-stu-id="787c0-124">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="787c0-125">Visual Basic 中的比較運算子</span><span class="sxs-lookup"><span data-stu-id="787c0-125">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="787c0-126">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="787c0-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="787c0-127">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="787c0-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="787c0-128">運算子和運算式</span><span class="sxs-lookup"><span data-stu-id="787c0-128">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
