---
title: IsNot 運算子 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 969fdebdf15a1f779075c58616ccd16c64976a35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="isnot-operator-visual-basic"></a><span data-ttu-id="0e30b-102">IsNot 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0e30b-102">IsNot Operator (Visual Basic)</span></span>
<span data-ttu-id="0e30b-103">比較兩個物件參考變數。</span><span class="sxs-lookup"><span data-stu-id="0e30b-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e30b-104">語法</span><span class="sxs-lookup"><span data-stu-id="0e30b-104">Syntax</span></span>  
  
```  
result = object1 IsNot object2  
```  
  
## <a name="parts"></a><span data-ttu-id="0e30b-105">組件</span><span class="sxs-lookup"><span data-stu-id="0e30b-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="0e30b-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="0e30b-106">Required.</span></span> <span data-ttu-id="0e30b-107">`Boolean` 值。</span><span class="sxs-lookup"><span data-stu-id="0e30b-107">A `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="0e30b-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="0e30b-108">Required.</span></span> <span data-ttu-id="0e30b-109">任何`Object`變數或運算式。</span><span class="sxs-lookup"><span data-stu-id="0e30b-109">Any `Object` variable or expression.</span></span>  
  
 `object2`  
 <span data-ttu-id="0e30b-110">必要項。</span><span class="sxs-lookup"><span data-stu-id="0e30b-110">Required.</span></span> <span data-ttu-id="0e30b-111">任何`Object`變數或運算式。</span><span class="sxs-lookup"><span data-stu-id="0e30b-111">Any `Object` variable or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e30b-112">備註</span><span class="sxs-lookup"><span data-stu-id="0e30b-112">Remarks</span></span>  
 <span data-ttu-id="0e30b-113">`IsNot`運算子會判斷是否兩個物件參考會參考不同的物件。</span><span class="sxs-lookup"><span data-stu-id="0e30b-113">The `IsNot` operator determines if two object references refer to different objects.</span></span> <span data-ttu-id="0e30b-114">不過，它不會執行值比較。</span><span class="sxs-lookup"><span data-stu-id="0e30b-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="0e30b-115">如果`object1`和`object2`完全相同的物件執行個體都會參考`result`是`False`; 如果沒有的話，`result`是`True`。</span><span class="sxs-lookup"><span data-stu-id="0e30b-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `False`; if they do not, `result` is `True`.</span></span>  
  
 <span data-ttu-id="0e30b-116">`IsNot`相反`Is`運算子。</span><span class="sxs-lookup"><span data-stu-id="0e30b-116">`IsNot` is the opposite of the `Is` operator.</span></span> <span data-ttu-id="0e30b-117">優點`IsNot`是您可以避免造成不便語法與`Not`和`Is`，可能會難以讀取。</span><span class="sxs-lookup"><span data-stu-id="0e30b-117">The advantage of `IsNot` is that you can avoid awkward syntax with `Not` and `Is`, which can be difficult to read.</span></span>  
  
 <span data-ttu-id="0e30b-118">您可以使用`Is`和`IsNot`運算子來測試早期繫結和晚期繫結物件。</span><span class="sxs-lookup"><span data-stu-id="0e30b-118">You can use the `Is` and `IsNot` operators to test both early-bound and late-bound objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0e30b-119">`IsNot`運算子不能用來比較運算式傳回`TypeOf`運算子。</span><span class="sxs-lookup"><span data-stu-id="0e30b-119">The `IsNot` operator cannot be used to compare expressions returned from the `TypeOf` operator.</span></span> <span data-ttu-id="0e30b-120">相反地，您必須使用`Not`和`Is`運算子。</span><span class="sxs-lookup"><span data-stu-id="0e30b-120">Instead, you must use the `Not` and `Is` operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e30b-121">範例</span><span class="sxs-lookup"><span data-stu-id="0e30b-121">Example</span></span>  
 <span data-ttu-id="0e30b-122">下列程式碼範例會使用這兩者`Is`運算子和`IsNot`運算子來完成相同的比較。</span><span class="sxs-lookup"><span data-stu-id="0e30b-122">The following code example uses both the `Is` operator and the `IsNot` operator to accomplish the same comparison.</span></span>  
  
 [!code-vb[VbVbalrOperators#29](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isnot-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="0e30b-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e30b-123">See Also</span></span>  
 [<span data-ttu-id="0e30b-124">Is 運算子</span><span class="sxs-lookup"><span data-stu-id="0e30b-124">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="0e30b-125">TypeOf 運算子</span><span class="sxs-lookup"><span data-stu-id="0e30b-125">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)  
 [<span data-ttu-id="0e30b-126">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="0e30b-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="0e30b-127">如何：測試兩個物件是否相同</span><span class="sxs-lookup"><span data-stu-id="0e30b-127">How to: Test Whether Two Objects Are the Same</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
