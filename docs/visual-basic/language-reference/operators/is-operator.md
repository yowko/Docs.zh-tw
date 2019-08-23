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
ms.openlocfilehash: a5481a9bce01e84ce4f078335c8cd15a747a3c51
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917222"
---
# <a name="is-operator-visual-basic"></a><span data-ttu-id="4498e-102">Is 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4498e-102">Is Operator (Visual Basic)</span></span>
<span data-ttu-id="4498e-103">比較兩個物件參考變數。</span><span class="sxs-lookup"><span data-stu-id="4498e-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4498e-104">語法</span><span class="sxs-lookup"><span data-stu-id="4498e-104">Syntax</span></span>  
  
```  
result = object1 Is object2  
```  
  
## <a name="parts"></a><span data-ttu-id="4498e-105">組件</span><span class="sxs-lookup"><span data-stu-id="4498e-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="4498e-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="4498e-106">Required.</span></span> <span data-ttu-id="4498e-107">任何`Boolean`值。</span><span class="sxs-lookup"><span data-stu-id="4498e-107">Any `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="4498e-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="4498e-108">Required.</span></span> <span data-ttu-id="4498e-109">任何`Object`名稱。</span><span class="sxs-lookup"><span data-stu-id="4498e-109">Any `Object` name.</span></span>  
  
 `object2`  
 <span data-ttu-id="4498e-110">必要項。</span><span class="sxs-lookup"><span data-stu-id="4498e-110">Required.</span></span> <span data-ttu-id="4498e-111">任何`Object`名稱。</span><span class="sxs-lookup"><span data-stu-id="4498e-111">Any `Object` name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4498e-112">備註</span><span class="sxs-lookup"><span data-stu-id="4498e-112">Remarks</span></span>  
 <span data-ttu-id="4498e-113">`Is`運算子會判斷兩個物件參考是否參考相同的物件。</span><span class="sxs-lookup"><span data-stu-id="4498e-113">The `Is` operator determines if two object references refer to the same object.</span></span> <span data-ttu-id="4498e-114">不過, 它不會執行值比較。</span><span class="sxs-lookup"><span data-stu-id="4498e-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="4498e-115">如果`object1`和`True` `result` `result` `False`兩者都參考完全相同的物件實例, 則為; 如果不是, 則為。 `object2`</span><span class="sxs-lookup"><span data-stu-id="4498e-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `True`; if they do not, `result` is `False`.</span></span>  
  
 <span data-ttu-id="4498e-116">`Is`也可以與`TypeOf`關鍵字搭配使用來`TypeOf`建立 .。。`Is`運算式, 用來測試物件變數是否與資料類型相容。</span><span class="sxs-lookup"><span data-stu-id="4498e-116">`Is` can also be used with the `TypeOf` keyword to make a `TypeOf`...`Is` expression, which tests whether an object variable is compatible with a data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4498e-117">`Is`關鍵字也用於 [[選取 ...]Case 語句](../../../visual-basic/language-reference/statements/select-case-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="4498e-117">The `Is` keyword is also used in the [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4498e-118">範例</span><span class="sxs-lookup"><span data-stu-id="4498e-118">Example</span></span>  
 <span data-ttu-id="4498e-119">下列範例會使用`Is`運算子來比較物件參考的配對。</span><span class="sxs-lookup"><span data-stu-id="4498e-119">The following example uses the `Is` operator to compare pairs of object references.</span></span> <span data-ttu-id="4498e-120">結果會指派給一個`Boolean`值, 表示兩個物件是否相同。</span><span class="sxs-lookup"><span data-stu-id="4498e-120">The results are assigned to a `Boolean` value representing whether the two objects are identical.</span></span>  
  
 [!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]  
  
 <span data-ttu-id="4498e-121">如上述範例所示, 您可以使用`Is`運算子來測試早期繫結和晚期繫結物件。</span><span class="sxs-lookup"><span data-stu-id="4498e-121">As the preceding example demonstrates, you can use the `Is` operator to test both early bound and late bound objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4498e-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4498e-122">See also</span></span>

- [<span data-ttu-id="4498e-123">TypeOf 運算子</span><span class="sxs-lookup"><span data-stu-id="4498e-123">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [<span data-ttu-id="4498e-124">IsNot 運算子</span><span class="sxs-lookup"><span data-stu-id="4498e-124">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="4498e-125">Visual Basic 中的比較運算子</span><span class="sxs-lookup"><span data-stu-id="4498e-125">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="4498e-126">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="4498e-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="4498e-127">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="4498e-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="4498e-128">運算子和運算式</span><span class="sxs-lookup"><span data-stu-id="4498e-128">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
