---
title: IsNot 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: 0a83b48e5e415bd6ca0c777cef6d34f7127691b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966929"
---
# <a name="isnot-operator-visual-basic"></a><span data-ttu-id="0f8b5-102">IsNot 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f8b5-102">IsNot Operator (Visual Basic)</span></span>
<span data-ttu-id="0f8b5-103">比較兩個物件參考變數。</span><span class="sxs-lookup"><span data-stu-id="0f8b5-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f8b5-104">語法</span><span class="sxs-lookup"><span data-stu-id="0f8b5-104">Syntax</span></span>  
  
```  
result = object1 IsNot object2  
```  
  
## <a name="parts"></a><span data-ttu-id="0f8b5-105">組件</span><span class="sxs-lookup"><span data-stu-id="0f8b5-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="0f8b5-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="0f8b5-106">Required.</span></span> <span data-ttu-id="0f8b5-107">`Boolean` 值。</span><span class="sxs-lookup"><span data-stu-id="0f8b5-107">A `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="0f8b5-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="0f8b5-108">Required.</span></span> <span data-ttu-id="0f8b5-109">任何`Object`變數或運算式。</span><span class="sxs-lookup"><span data-stu-id="0f8b5-109">Any `Object` variable or expression.</span></span>  
  
 `object2`  
 <span data-ttu-id="0f8b5-110">必要項。</span><span class="sxs-lookup"><span data-stu-id="0f8b5-110">Required.</span></span> <span data-ttu-id="0f8b5-111">任何`Object`變數或運算式。</span><span class="sxs-lookup"><span data-stu-id="0f8b5-111">Any `Object` variable or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f8b5-112">備註</span><span class="sxs-lookup"><span data-stu-id="0f8b5-112">Remarks</span></span>  
 <span data-ttu-id="0f8b5-113">`IsNot`運算子會判斷兩個物件參考是否參考不同的物件。</span><span class="sxs-lookup"><span data-stu-id="0f8b5-113">The `IsNot` operator determines if two object references refer to different objects.</span></span> <span data-ttu-id="0f8b5-114">不過, 它不會執行值比較。</span><span class="sxs-lookup"><span data-stu-id="0f8b5-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="0f8b5-115">如果`object1`和`False` `result` `result` `True`兩者都參考完全相同的物件實例, 則為; 如果不是, 則為。 `object2`</span><span class="sxs-lookup"><span data-stu-id="0f8b5-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `False`; if they do not, `result` is `True`.</span></span>  
  
 <span data-ttu-id="0f8b5-116">`IsNot`是`Is`運算子的相反。</span><span class="sxs-lookup"><span data-stu-id="0f8b5-116">`IsNot` is the opposite of the `Is` operator.</span></span> <span data-ttu-id="0f8b5-117">的優點`IsNot`是, 您可以避免使用`Not`和`Is`的語法不好, 這可能難以閱讀。</span><span class="sxs-lookup"><span data-stu-id="0f8b5-117">The advantage of `IsNot` is that you can avoid awkward syntax with `Not` and `Is`, which can be difficult to read.</span></span>  
  
 <span data-ttu-id="0f8b5-118">您可以使用`Is`和`IsNot`運算子來測試早期繫結和晚期繫結物件。</span><span class="sxs-lookup"><span data-stu-id="0f8b5-118">You can use the `Is` and `IsNot` operators to test both early-bound and late-bound objects.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0f8b5-119">運算子不能用來比較`TypeOf`從運算子傳回的運算式。 `IsNot`</span><span class="sxs-lookup"><span data-stu-id="0f8b5-119">The `IsNot` operator cannot be used to compare expressions returned from the `TypeOf` operator.</span></span> <span data-ttu-id="0f8b5-120">相反`Not`地, 您必須使用和`Is`運算子。</span><span class="sxs-lookup"><span data-stu-id="0f8b5-120">Instead, you must use the `Not` and `Is` operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f8b5-121">範例</span><span class="sxs-lookup"><span data-stu-id="0f8b5-121">Example</span></span>  
 <span data-ttu-id="0f8b5-122">下列程式碼範例會使用`Is`運算子`IsNot`和運算子來完成相同的比較。</span><span class="sxs-lookup"><span data-stu-id="0f8b5-122">The following code example uses both the `Is` operator and the `IsNot` operator to accomplish the same comparison.</span></span>  
  
 [!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]  
  
## <a name="see-also"></a><span data-ttu-id="0f8b5-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f8b5-123">See also</span></span>

- [<span data-ttu-id="0f8b5-124">Is 運算子</span><span class="sxs-lookup"><span data-stu-id="0f8b5-124">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="0f8b5-125">TypeOf 運算子</span><span class="sxs-lookup"><span data-stu-id="0f8b5-125">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [<span data-ttu-id="0f8b5-126">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="0f8b5-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="0f8b5-127">如何：測試兩個物件是否相同</span><span class="sxs-lookup"><span data-stu-id="0f8b5-127">How to: Test Whether Two Objects Are the Same</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
