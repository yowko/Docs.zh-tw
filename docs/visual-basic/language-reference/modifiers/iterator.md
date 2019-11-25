---
title: Iterator
ms.date: 07/20/2015
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
ms.openlocfilehash: 9d7eaf186bae544031487ce027505e1e0d4ae0f3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351528"
---
# <a name="iterator-visual-basic"></a><span data-ttu-id="3ce2d-102">Iterator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ce2d-102">Iterator (Visual Basic)</span></span>
<span data-ttu-id="3ce2d-103">Specifies that a function or `Get` accessor is an iterator.</span><span class="sxs-lookup"><span data-stu-id="3ce2d-103">Specifies that a function or `Get` accessor is an iterator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3ce2d-104">備註</span><span class="sxs-lookup"><span data-stu-id="3ce2d-104">Remarks</span></span>  
 <span data-ttu-id="3ce2d-105">An *iterator* performs a custom iteration over a collection.</span><span class="sxs-lookup"><span data-stu-id="3ce2d-105">An *iterator* performs a custom iteration over a collection.</span></span> <span data-ttu-id="3ce2d-106">An iterator uses the [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element in the collection one at a time.</span><span class="sxs-lookup"><span data-stu-id="3ce2d-106">An iterator uses the [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element in the collection one at a time.</span></span> <span data-ttu-id="3ce2d-107">When a `Yield` statement is reached, the current location in code is retained.</span><span class="sxs-lookup"><span data-stu-id="3ce2d-107">When a `Yield` statement is reached, the current location in code is retained.</span></span> <span data-ttu-id="3ce2d-108">下一次呼叫 Iterator 函式時，便會從這個位置重新開始執行。</span><span class="sxs-lookup"><span data-stu-id="3ce2d-108">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="3ce2d-109">An iterator can be implemented as a function or as a `Get` accessor of a property definition.</span><span class="sxs-lookup"><span data-stu-id="3ce2d-109">An iterator can be implemented as a function or as a `Get` accessor of a property definition.</span></span> <span data-ttu-id="3ce2d-110">The `Iterator` modifier appears in the declaration of the iterator function or `Get` accessor.</span><span class="sxs-lookup"><span data-stu-id="3ce2d-110">The `Iterator` modifier appears in the declaration of the iterator function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="3ce2d-111">You call an iterator from client code by using a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3ce2d-111">You call an iterator from client code by using a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
 <span data-ttu-id="3ce2d-112">The return type of an iterator function or `Get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="3ce2d-112">The return type of an iterator function or `Get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="3ce2d-113">An iterator cannot have any `ByRef` parameters.</span><span class="sxs-lookup"><span data-stu-id="3ce2d-113">An iterator cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="3ce2d-114">迭代器不能出現在事件、執行個體建構函式、靜態建構函式或靜態解構函式中。</span><span class="sxs-lookup"><span data-stu-id="3ce2d-114">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="3ce2d-115">An iterator can be an anonymous function.</span><span class="sxs-lookup"><span data-stu-id="3ce2d-115">An iterator can be an anonymous function.</span></span> <span data-ttu-id="3ce2d-116">如需詳細資訊，請參閱[迭代器](../../programming-guide/concepts/iterators.md)。</span><span class="sxs-lookup"><span data-stu-id="3ce2d-116">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="usage"></a><span data-ttu-id="3ce2d-117">使用量</span><span class="sxs-lookup"><span data-stu-id="3ce2d-117">Usage</span></span>  
 <span data-ttu-id="3ce2d-118">`Iterator` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="3ce2d-118">The `Iterator` modifier can be used in these contexts:</span></span>  
  
- [<span data-ttu-id="3ce2d-119">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="3ce2d-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
- [<span data-ttu-id="3ce2d-120">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="3ce2d-120">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="example"></a><span data-ttu-id="3ce2d-121">範例</span><span class="sxs-lookup"><span data-stu-id="3ce2d-121">Example</span></span>  
 <span data-ttu-id="3ce2d-122">The following example demonstrates an iterator function.</span><span class="sxs-lookup"><span data-stu-id="3ce2d-122">The following example demonstrates an iterator function.</span></span> <span data-ttu-id="3ce2d-123">The iterator function has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span><span class="sxs-lookup"><span data-stu-id="3ce2d-123">The iterator function has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="3ce2d-124">Each iteration of the [For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span><span class="sxs-lookup"><span data-stu-id="3ce2d-124">Each iteration of the [For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="3ce2d-125">每次呼叫 Iterator 函式都會執行下一個 `Yield` 陳述式，這會在 `For…Next` 迴圈的下一個反覆項目期間發生。</span><span class="sxs-lookup"><span data-stu-id="3ce2d-125">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a><span data-ttu-id="3ce2d-126">範例</span><span class="sxs-lookup"><span data-stu-id="3ce2d-126">Example</span></span>  
 <span data-ttu-id="3ce2d-127">下列範例將示範本身為迭代器的 `Get` 存取子。</span><span class="sxs-lookup"><span data-stu-id="3ce2d-127">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="3ce2d-128">The `Iterator` modifier is in the property declaration.</span><span class="sxs-lookup"><span data-stu-id="3ce2d-128">The `Iterator` modifier is in the property declaration.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 <span data-ttu-id="3ce2d-129">For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="3ce2d-129">For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ce2d-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="3ce2d-130">See also</span></span>

- <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>
- [<span data-ttu-id="3ce2d-131">迭代器</span><span class="sxs-lookup"><span data-stu-id="3ce2d-131">Iterators</span></span>](../../programming-guide/concepts/iterators.md)
- [<span data-ttu-id="3ce2d-132">Yield 陳述式</span><span class="sxs-lookup"><span data-stu-id="3ce2d-132">Yield Statement</span></span>](../../../visual-basic/language-reference/statements/yield-statement.md)
