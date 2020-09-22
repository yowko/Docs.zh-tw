---
title: Iterator
ms.date: 07/20/2015
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
ms.openlocfilehash: 0b459a16317b8ba55886e52ecadb227ddf2fee83
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875440"
---
# <a name="iterator-visual-basic"></a><span data-ttu-id="b6375-102">Iterator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b6375-102">Iterator (Visual Basic)</span></span>

<span data-ttu-id="b6375-103">指定函數或存取子 `Get` 是反覆運算器。</span><span class="sxs-lookup"><span data-stu-id="b6375-103">Specifies that a function or `Get` accessor is an iterator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6375-104">備註</span><span class="sxs-lookup"><span data-stu-id="b6375-104">Remarks</span></span>  

 <span data-ttu-id="b6375-105">*反覆運算器*會在集合上執行自訂反復專案。</span><span class="sxs-lookup"><span data-stu-id="b6375-105">An *iterator* performs a custom iteration over a collection.</span></span> <span data-ttu-id="b6375-106">反覆運算器會使用 [Yield](../statements/yield-statement.md) 語句，一次傳回集合中的每個元素。</span><span class="sxs-lookup"><span data-stu-id="b6375-106">An iterator uses the [Yield](../statements/yield-statement.md) statement to return each element in the collection one at a time.</span></span> <span data-ttu-id="b6375-107">當 `Yield` 到達語句時，會保留程式碼中的目前位置。</span><span class="sxs-lookup"><span data-stu-id="b6375-107">When a `Yield` statement is reached, the current location in code is retained.</span></span> <span data-ttu-id="b6375-108">下一次呼叫 Iterator 函式時，便會從這個位置重新開始執行。</span><span class="sxs-lookup"><span data-stu-id="b6375-108">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="b6375-109">反覆運算器可以實作為函式或 `Get` 屬性定義的存取子。</span><span class="sxs-lookup"><span data-stu-id="b6375-109">An iterator can be implemented as a function or as a `Get` accessor of a property definition.</span></span> <span data-ttu-id="b6375-110">`Iterator`修飾詞會出現在 iterator 函數或存取子的宣告中 `Get` 。</span><span class="sxs-lookup"><span data-stu-id="b6375-110">The `Iterator` modifier appears in the declaration of the iterator function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="b6375-111">您可以使用 For Each 的，從用戶端程式代碼呼叫反覆運算器。 [下一個語句](../statements/for-each-next-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="b6375-111">You call an iterator from client code by using a [For Each...Next Statement](../statements/for-each-next-statement.md).</span></span>  
  
 <span data-ttu-id="b6375-112">Iterator 函數或存取子的傳回型別 `Get` 可以是 <xref:System.Collections.IEnumerable> 、 <xref:System.Collections.Generic.IEnumerable%601> 、 <xref:System.Collections.IEnumerator> 或 <xref:System.Collections.Generic.IEnumerator%601> 。</span><span class="sxs-lookup"><span data-stu-id="b6375-112">The return type of an iterator function or `Get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="b6375-113">反覆運算器不能有任何 `ByRef` 參數。</span><span class="sxs-lookup"><span data-stu-id="b6375-113">An iterator cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="b6375-114">迭代器不能出現在事件、執行個體建構函式、靜態建構函式或靜態解構函式中。</span><span class="sxs-lookup"><span data-stu-id="b6375-114">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="b6375-115">反覆運算器可以是匿名函數。</span><span class="sxs-lookup"><span data-stu-id="b6375-115">An iterator can be an anonymous function.</span></span> <span data-ttu-id="b6375-116">如需詳細資訊，請參閱 [反覆運算](../../programming-guide/concepts/iterators.md)器。</span><span class="sxs-lookup"><span data-stu-id="b6375-116">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="usage"></a><span data-ttu-id="b6375-117">使用方式</span><span class="sxs-lookup"><span data-stu-id="b6375-117">Usage</span></span>  

 <span data-ttu-id="b6375-118">`Iterator` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="b6375-118">The `Iterator` modifier can be used in these contexts:</span></span>  
  
- [<span data-ttu-id="b6375-119">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="b6375-119">Function Statement</span></span>](../statements/function-statement.md)  
  
- [<span data-ttu-id="b6375-120">Property Statement</span><span class="sxs-lookup"><span data-stu-id="b6375-120">Property Statement</span></span>](../statements/property-statement.md)  
  
## <a name="example"></a><span data-ttu-id="b6375-121">範例</span><span class="sxs-lookup"><span data-stu-id="b6375-121">Example</span></span>  

 <span data-ttu-id="b6375-122">下列範例示範 iterator 函數。</span><span class="sxs-lookup"><span data-stu-id="b6375-122">The following example demonstrates an iterator function.</span></span> <span data-ttu-id="b6375-123">反覆運算器函式的 `Yield` 語句位於 [For .。。Next](../statements/for-next-statement.md) 迴圈。</span><span class="sxs-lookup"><span data-stu-id="b6375-123">The iterator function has a `Yield` statement that is inside a [For…Next](../statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="b6375-124">[每個語句主體](../statements/for-each-next-statement.md)的每個反復專案 `Main` 都會建立 `Power` iterator 函數的呼叫。</span><span class="sxs-lookup"><span data-stu-id="b6375-124">Each iteration of the [For Each](../statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="b6375-125">每次呼叫 Iterator 函式都會執行下一個 `Yield` 陳述式，這會在 `For…Next` 迴圈的下一個反覆項目期間發生。</span><span class="sxs-lookup"><span data-stu-id="b6375-125">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a><span data-ttu-id="b6375-126">範例</span><span class="sxs-lookup"><span data-stu-id="b6375-126">Example</span></span>  

 <span data-ttu-id="b6375-127">下列範例將示範本身為迭代器的 `Get` 存取子。</span><span class="sxs-lookup"><span data-stu-id="b6375-127">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="b6375-128">`Iterator`修飾詞位於屬性宣告中。</span><span class="sxs-lookup"><span data-stu-id="b6375-128">The `Iterator` modifier is in the property declaration.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 <span data-ttu-id="b6375-129">如需其他範例，請參閱 [反覆運算](../../programming-guide/concepts/iterators.md)器。</span><span class="sxs-lookup"><span data-stu-id="b6375-129">For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6375-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6375-130">See also</span></span>

- <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>
- [<span data-ttu-id="b6375-131">迭代器</span><span class="sxs-lookup"><span data-stu-id="b6375-131">Iterators</span></span>](../../programming-guide/concepts/iterators.md)
- [<span data-ttu-id="b6375-132">Yield 陳述式</span><span class="sxs-lookup"><span data-stu-id="b6375-132">Yield Statement</span></span>](../statements/yield-statement.md)
