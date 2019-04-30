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
ms.openlocfilehash: a59ff4c956724c614342f0ee4c0622a67f1c25e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054950"
---
# <a name="is-operator-visual-basic"></a><span data-ttu-id="7c140-102">Is 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7c140-102">Is Operator (Visual Basic)</span></span>
<span data-ttu-id="7c140-103">比較兩個物件參考變數。</span><span class="sxs-lookup"><span data-stu-id="7c140-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c140-104">語法</span><span class="sxs-lookup"><span data-stu-id="7c140-104">Syntax</span></span>  
  
```  
result = object1 Is object2  
```  
  
## <a name="parts"></a><span data-ttu-id="7c140-105">組件</span><span class="sxs-lookup"><span data-stu-id="7c140-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="7c140-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="7c140-106">Required.</span></span> <span data-ttu-id="7c140-107">任何`Boolean`值。</span><span class="sxs-lookup"><span data-stu-id="7c140-107">Any `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="7c140-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="7c140-108">Required.</span></span> <span data-ttu-id="7c140-109">任何`Object`名稱。</span><span class="sxs-lookup"><span data-stu-id="7c140-109">Any `Object` name.</span></span>  
  
 `object2`  
 <span data-ttu-id="7c140-110">必要項。</span><span class="sxs-lookup"><span data-stu-id="7c140-110">Required.</span></span> <span data-ttu-id="7c140-111">任何`Object`名稱。</span><span class="sxs-lookup"><span data-stu-id="7c140-111">Any `Object` name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7c140-112">備註</span><span class="sxs-lookup"><span data-stu-id="7c140-112">Remarks</span></span>  
 <span data-ttu-id="7c140-113">`Is`運算子會判斷是否兩個物件參考會參考相同的物件。</span><span class="sxs-lookup"><span data-stu-id="7c140-113">The `Is` operator determines if two object references refer to the same object.</span></span> <span data-ttu-id="7c140-114">不過，它不會執行值比較。</span><span class="sxs-lookup"><span data-stu-id="7c140-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="7c140-115">如果`object1`並`object2`都會參考完全相同的物件執行個體`result`是`True`; 如果沒有的話，`result`是`False`。</span><span class="sxs-lookup"><span data-stu-id="7c140-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `True`; if they do not, `result` is `False`.</span></span>  
  
 <span data-ttu-id="7c140-116">`Is` 也可與`TypeOf`關鍵字，讓`TypeOf`...`Is`測試是否為資料類型相容的物件變數的運算式。</span><span class="sxs-lookup"><span data-stu-id="7c140-116">`Is` can also be used with the `TypeOf` keyword to make a `TypeOf`...`Is` expression, which tests whether an object variable is compatible with a data type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7c140-117">`Is`關鍵字也會在[選取...Case 陳述式](../../../visual-basic/language-reference/statements/select-case-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="7c140-117">The `Is` keyword is also used in the [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c140-118">範例</span><span class="sxs-lookup"><span data-stu-id="7c140-118">Example</span></span>  
 <span data-ttu-id="7c140-119">下列範例會使用`Is`運算子來比較的物件參考的組。</span><span class="sxs-lookup"><span data-stu-id="7c140-119">The following example uses the `Is` operator to compare pairs of object references.</span></span> <span data-ttu-id="7c140-120">結果會指派給`Boolean`值，表示兩個物件是否相同。</span><span class="sxs-lookup"><span data-stu-id="7c140-120">The results are assigned to a `Boolean` value representing whether the two objects are identical.</span></span>  
  
 [!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]  
  
 <span data-ttu-id="7c140-121">如上述範例所示，您可以使用`Is`運算子來測試兩者早期繫結和晚期繫結物件。</span><span class="sxs-lookup"><span data-stu-id="7c140-121">As the preceding example demonstrates, you can use the `Is` operator to test both early bound and late bound objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c140-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c140-122">See also</span></span>

- [<span data-ttu-id="7c140-123">TypeOf 運算子</span><span class="sxs-lookup"><span data-stu-id="7c140-123">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [<span data-ttu-id="7c140-124">IsNot 運算子</span><span class="sxs-lookup"><span data-stu-id="7c140-124">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="7c140-125">在 Visual Basic 中的比較運算子</span><span class="sxs-lookup"><span data-stu-id="7c140-125">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="7c140-126">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="7c140-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="7c140-127">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="7c140-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="7c140-128">運算子和運算式</span><span class="sxs-lookup"><span data-stu-id="7c140-128">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
