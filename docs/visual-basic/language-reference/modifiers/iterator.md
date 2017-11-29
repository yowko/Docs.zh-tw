---
title: Iterator (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Iterator
helpviewer_keywords: Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 503d586c0515b4cb53f8ec5656e5fe765cc094a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iterator-visual-basic"></a><span data-ttu-id="5d9b7-102">Iterator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d9b7-102">Iterator (Visual Basic)</span></span>
<span data-ttu-id="5d9b7-103">指定的函式或`Get`存取子是迭代器。</span><span class="sxs-lookup"><span data-stu-id="5d9b7-103">Specifies that a function or `Get` accessor is an iterator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d9b7-104">備註</span><span class="sxs-lookup"><span data-stu-id="5d9b7-104">Remarks</span></span>  
 <span data-ttu-id="5d9b7-105">*迭代器*集合上執行自訂反覆項目。</span><span class="sxs-lookup"><span data-stu-id="5d9b7-105">An *iterator* performs a custom iteration over a collection.</span></span> <span data-ttu-id="5d9b7-106">迭代器會使用[產生](../../../visual-basic/language-reference/statements/yield-statement.md)陳述式來一次一個集合中傳回每個項目。</span><span class="sxs-lookup"><span data-stu-id="5d9b7-106">An iterator uses the [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element in the collection one at a time.</span></span> <span data-ttu-id="5d9b7-107">當`Yield`到達陳述式時，保留在程式碼中的目前位置。</span><span class="sxs-lookup"><span data-stu-id="5d9b7-107">When a `Yield` statement is reached, the current location in code is retained.</span></span> <span data-ttu-id="5d9b7-108">下一次呼叫 Iterator 函式時，便會從這個位置重新開始執行。</span><span class="sxs-lookup"><span data-stu-id="5d9b7-108">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="5d9b7-109">可以實作迭代器，為函式或`Get`屬性定義的存取子。</span><span class="sxs-lookup"><span data-stu-id="5d9b7-109">An iterator can be implemented as a function or as a `Get` accessor of a property definition.</span></span> <span data-ttu-id="5d9b7-110">`Iterator`修飾詞會出現在迭代器函式宣告或`Get`存取子。</span><span class="sxs-lookup"><span data-stu-id="5d9b7-110">The `Iterator` modifier appears in the declaration of the iterator function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="5d9b7-111">從用戶端程式碼呼叫迭代器使用[每個...下一個陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="5d9b7-111">You call an iterator from client code by using a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
 <span data-ttu-id="5d9b7-112">Iterator 函式的傳回型別或`Get`存取子可以是<xref:System.Collections.IEnumerable>， <xref:System.Collections.Generic.IEnumerable%601>， <xref:System.Collections.IEnumerator>，或<xref:System.Collections.Generic.IEnumerator%601>。</span><span class="sxs-lookup"><span data-stu-id="5d9b7-112">The return type of an iterator function or `Get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="5d9b7-113">迭代器不能有任何`ByRef`參數。</span><span class="sxs-lookup"><span data-stu-id="5d9b7-113">An iterator cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="5d9b7-114">迭代器不能出現在事件、執行個體建構函式、靜態建構函式或靜態解構函式中。</span><span class="sxs-lookup"><span data-stu-id="5d9b7-114">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="5d9b7-115">迭代器可以是匿名函式。</span><span class="sxs-lookup"><span data-stu-id="5d9b7-115">An iterator can be an anonymous function.</span></span> <span data-ttu-id="5d9b7-116">如需詳細資訊，請參閱[迭代器](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)。</span><span class="sxs-lookup"><span data-stu-id="5d9b7-116">For more information, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
 <span data-ttu-id="5d9b7-117">如需迭代器的詳細資訊，請參閱 [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7) (迭代器)。</span><span class="sxs-lookup"><span data-stu-id="5d9b7-117">For more information about iterators, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
## <a name="usage"></a><span data-ttu-id="5d9b7-118">使用方式</span><span class="sxs-lookup"><span data-stu-id="5d9b7-118">Usage</span></span>  
 <span data-ttu-id="5d9b7-119">`Iterator` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="5d9b7-119">The `Iterator` modifier can be used in these contexts:</span></span>  
  
-   [<span data-ttu-id="5d9b7-120">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="5d9b7-120">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [<span data-ttu-id="5d9b7-121">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="5d9b7-121">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="example"></a><span data-ttu-id="5d9b7-122">範例</span><span class="sxs-lookup"><span data-stu-id="5d9b7-122">Example</span></span>  
 <span data-ttu-id="5d9b7-123">下列範例會示範 iterator 函式。</span><span class="sxs-lookup"><span data-stu-id="5d9b7-123">The following example demonstrates an iterator function.</span></span> <span data-ttu-id="5d9b7-124">迭代器函式有`Yield`陳述式內[For...下一步](../../../visual-basic/language-reference/statements/for-next-statement.md)迴圈。</span><span class="sxs-lookup"><span data-stu-id="5d9b7-124">The iterator function has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="5d9b7-125">每個反覆項目[每個](../../../visual-basic/language-reference/statements/for-each-next-statement.md)陳述式主體中的`Main`建立呼叫`Power`iterator 函式。</span><span class="sxs-lookup"><span data-stu-id="5d9b7-125">Each iteration of the [For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="5d9b7-126">每次呼叫 Iterator 函式都會執行下一個 `Yield` 陳述式，這會在 `For…Next` 迴圈的下一個反覆項目期間發生。</span><span class="sxs-lookup"><span data-stu-id="5d9b7-126">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/iterator_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="5d9b7-127">範例</span><span class="sxs-lookup"><span data-stu-id="5d9b7-127">Example</span></span>  
 <span data-ttu-id="5d9b7-128">下列範例將示範本身為迭代器的 `Get` 存取子。</span><span class="sxs-lookup"><span data-stu-id="5d9b7-128">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="5d9b7-129">`Iterator`修飾詞是屬性宣告中。</span><span class="sxs-lookup"><span data-stu-id="5d9b7-129">The `Iterator` modifier is in the property declaration.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/iterator_2.vb)]  
  
 <span data-ttu-id="5d9b7-130">如需其他範例，請參閱[迭代器](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)。</span><span class="sxs-lookup"><span data-stu-id="5d9b7-130">For additional examples, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d9b7-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d9b7-131">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>  
 [<span data-ttu-id="5d9b7-132">迭代器</span><span class="sxs-lookup"><span data-stu-id="5d9b7-132">Iterators</span></span>](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)  
 [<span data-ttu-id="5d9b7-133">Yield 陳述式</span><span class="sxs-lookup"><span data-stu-id="5d9b7-133">Yield Statement</span></span>](../../../visual-basic/language-reference/statements/yield-statement.md)
