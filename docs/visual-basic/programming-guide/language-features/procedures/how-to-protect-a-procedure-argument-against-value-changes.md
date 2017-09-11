---
title: "如何︰ 防止程序引數的值變更 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- procedures, arguments
- procedures, parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures, calling
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: d2b7c766-ce16-4d2c-8d79-3fc0e7ba2227
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: db40b3426256e7789a5273ab4d0afc8d5b47c8a7
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-protect-a-procedure-argument-against-value-changes-visual-basic"></a><span data-ttu-id="8388f-102">如何：防止程序引數的值變更 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8388f-102">How to: Protect a Procedure Argument Against Value Changes (Visual Basic)</span></span>
<span data-ttu-id="8388f-103">如果程序宣告為參數[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]提供程序程式碼直接呼叫程式碼中的引數的程式設計項目參考。</span><span class="sxs-lookup"><span data-stu-id="8388f-103">If a procedure declares a parameter as [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] gives the procedure code a direct reference to the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="8388f-104">這可讓程序來變更基礎呼叫程式碼中的引數的值。</span><span class="sxs-lookup"><span data-stu-id="8388f-104">This permits the procedure to change the value underlying the argument in the calling code.</span></span> <span data-ttu-id="8388f-105">在某些情況下呼叫程式碼可能會想要防止這類變更。</span><span class="sxs-lookup"><span data-stu-id="8388f-105">In some cases the calling code might want to protect against such a change.</span></span>  
  
 <span data-ttu-id="8388f-106">您永遠可以保護在變更引數，藉由宣告對應參數[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)程序中。</span><span class="sxs-lookup"><span data-stu-id="8388f-106">You can always protect an argument from change by declaring the corresponding parameter [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) in the procedure.</span></span> <span data-ttu-id="8388f-107">如果您想要能夠變更在某些情況下，而不是其他指定的引數，您可以宣告`ByRef`，讓呼叫的程式碼，判斷每個呼叫中的傳遞機制。</span><span class="sxs-lookup"><span data-stu-id="8388f-107">If you want to be able to change a given argument in some cases but not others, you can declare it `ByRef` and let the calling code determine the passing mechanism in each call.</span></span> <span data-ttu-id="8388f-108">它會藉由封閉的對應引數括號，以傳值或不括在括號，以傳址方式傳遞它。</span><span class="sxs-lookup"><span data-stu-id="8388f-108">It does this by enclosing the corresponding argument in parentheses to pass it by value, or not enclosing it in parentheses to pass it by reference.</span></span> <span data-ttu-id="8388f-109">如需詳細資訊，請參閱[如何︰ 強制以傳值方式傳遞引數](./how-to-force-an-argument-to-be-passed-by-value.md)。</span><span class="sxs-lookup"><span data-stu-id="8388f-109">For more information, see [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8388f-110">範例</span><span class="sxs-lookup"><span data-stu-id="8388f-110">Example</span></span>  
 <span data-ttu-id="8388f-111">下列範例會顯示兩個程序取得陣列變數和操作其項目上。</span><span class="sxs-lookup"><span data-stu-id="8388f-111">The following example shows two procedures that take an array variable and operate on its elements.</span></span> <span data-ttu-id="8388f-112">`increase`程序只會加入至每個項目。</span><span class="sxs-lookup"><span data-stu-id="8388f-112">The `increase` procedure simply adds one to each element.</span></span> <span data-ttu-id="8388f-113">`replace`程序會將新的陣列指派給參數`a()`並將每個項目。</span><span class="sxs-lookup"><span data-stu-id="8388f-113">The `replace` procedure assigns a new array to the parameter `a()` and then adds one to each element.</span></span> <span data-ttu-id="8388f-114">不過，重新指派不會影響呼叫程式碼中的陣列變數。</span><span class="sxs-lookup"><span data-stu-id="8388f-114">However, the reassignment does not affect the underlying array variable in the calling code.</span></span>  
  
 <span data-ttu-id="8388f-115">[!code-vb[VbVbcnProcedures #&35;](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="8388f-115">[!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_1.vb)]</span></span>  
  
 <span data-ttu-id="8388f-116">[!code-vb[VbVbcnProcedures #&38;](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="8388f-116">[!code-vb[VbVbcnProcedures#38](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_2.vb)]</span></span>  
  
 <span data-ttu-id="8388f-117">[!code-vb[VbVbcnProcedures #&37;](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="8388f-117">[!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_3.vb)]</span></span>  
  
 <span data-ttu-id="8388f-118">第一個`MsgBox`呼叫會顯示 「 後 increase(n): 11、 21、 31、 41 」。</span><span class="sxs-lookup"><span data-stu-id="8388f-118">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="8388f-119">因為陣列`n`是參考型別，`replace`可以變更其成員，即使傳遞機制`ByVal`。</span><span class="sxs-lookup"><span data-stu-id="8388f-119">Because the array `n` is a reference type, `replace` can change its members, even though the passing mechanism is `ByVal`.</span></span>  
  
 <span data-ttu-id="8388f-120">第二個`MsgBox`呼叫會顯示 「 後 replace(n): 11、 21、 31、 41 」。</span><span class="sxs-lookup"><span data-stu-id="8388f-120">The second `MsgBox` call displays "After replace(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="8388f-121">因為`n`傳遞`ByVal`，`replace`無法修改變數`n`中指定新的陣列，讓呼叫的程式碼。</span><span class="sxs-lookup"><span data-stu-id="8388f-121">Because `n` is passed `ByVal`, `replace` cannot modify the variable `n` in the calling code by assigning a new array to it.</span></span> <span data-ttu-id="8388f-122">當`replace`建立新的陣列執行個體`k`並將它指派給本機變數`a`，它就不會參考`n`傳入呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="8388f-122">When `replace` creates the new array instance `k` and assigns it to the local variable `a`, it loses the reference to `n` passed in by the calling code.</span></span> <span data-ttu-id="8388f-123">它會變更的成員`a`，只有本機陣列`k`會受到影響。</span><span class="sxs-lookup"><span data-stu-id="8388f-123">When it changes the members of `a`, only the local array `k` is affected.</span></span> <span data-ttu-id="8388f-124">因此，`replace`不會增加陣列的值`n`呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="8388f-124">Therefore, `replace` does not increment the values of array `n` in the calling code.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8388f-125">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="8388f-125">Compiling the Code</span></span>  
 <span data-ttu-id="8388f-126">在預設[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]是以傳值方式傳遞引數。</span><span class="sxs-lookup"><span data-stu-id="8388f-126">The default in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] is to pass arguments by value.</span></span> <span data-ttu-id="8388f-127">不過，它是良好的程式設計作法包含[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)或[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)關鍵字與每個宣告的參數。</span><span class="sxs-lookup"><span data-stu-id="8388f-127">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="8388f-128">這可讓您的程式碼更容易讀取。</span><span class="sxs-lookup"><span data-stu-id="8388f-128">This makes your code easier to read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8388f-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8388f-129">See Also</span></span>  
 <span data-ttu-id="8388f-130">[程序](./index.md) </span><span class="sxs-lookup"><span data-stu-id="8388f-130">[Procedures](./index.md) </span></span>  
<span data-ttu-id="8388f-131"> [程序參數和引數](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="8388f-131"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="8388f-132"> [如何︰ 將引數傳遞至程序](./how-to-pass-arguments-to-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="8388f-132"> [How to: Pass Arguments to a Procedure](./how-to-pass-arguments-to-a-procedure.md) </span></span>  
<span data-ttu-id="8388f-133"> [傳遞引數以傳值或傳址](./passing-arguments-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="8388f-133"> [Passing Arguments by Value and by Reference](./passing-arguments-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="8388f-134"> [可修改和不可修改引數之間的差異](./differences-between-modifiable-and-nonmodifiable-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="8388f-134"> [Differences Between Modifiable and Nonmodifiable Arguments](./differences-between-modifiable-and-nonmodifiable-arguments.md) </span></span>  
<span data-ttu-id="8388f-135"> [以傳值或參考所傳遞引數之間的差異](./differences-between-passing-an-argument-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="8388f-135"> [Differences Between Passing an Argument By Value and By Reference](./differences-between-passing-an-argument-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="8388f-136"> [如何︰ 變更程序引數的值](./how-to-change-the-value-of-a-procedure-argument.md) </span><span class="sxs-lookup"><span data-stu-id="8388f-136"> [How to: Change the Value of a Procedure Argument](./how-to-change-the-value-of-a-procedure-argument.md) </span></span>  
<span data-ttu-id="8388f-137"> [如何︰ 強制以傳值方式傳遞引數](./how-to-force-an-argument-to-be-passed-by-value.md) </span><span class="sxs-lookup"><span data-stu-id="8388f-137"> [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md) </span></span>  
<span data-ttu-id="8388f-138"> [依位置和名稱傳遞引數](./passing-arguments-by-position-and-by-name.md) </span><span class="sxs-lookup"><span data-stu-id="8388f-138"> [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md) </span></span>  
<span data-ttu-id="8388f-139"> [值類型和參考類型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span><span class="sxs-lookup"><span data-stu-id="8388f-139"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span></span>
