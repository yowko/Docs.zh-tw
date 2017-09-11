---
title: "如何︰ 變更程序引數 (Visual Basic) 的值 |Microsoft 文件"
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
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: 6fad2368-5da7-4c07-8bf8-0f4e65a1be67
caps.latest.revision: 16
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
ms.openlocfilehash: 3f192d738ca2753cd12b6fffca1f4f94a606a42c
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a><span data-ttu-id="fbf4e-102">如何：變更程序引數的值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fbf4e-102">How to: Change the Value of a Procedure Argument (Visual Basic)</span></span>
<span data-ttu-id="fbf4e-103">當您呼叫程序時，您提供每個引數會對應至其中一個程序中所定義的參數。</span><span class="sxs-lookup"><span data-stu-id="fbf4e-103">When you call a procedure, each argument you supply corresponds to one of the parameters defined in the procedure.</span></span> <span data-ttu-id="fbf4e-104">在某些情況下，程序程式碼可以變更對應的引數呼叫的程式碼中的值。</span><span class="sxs-lookup"><span data-stu-id="fbf4e-104">In some cases, the procedure code can change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="fbf4e-105">在其他情況下，此程序可以變更引數其本機複本。</span><span class="sxs-lookup"><span data-stu-id="fbf4e-105">In other cases, the procedure can change only its local copy of an argument.</span></span>  
  
 <span data-ttu-id="fbf4e-106">當您呼叫程序，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]讓每個傳遞的引數的本機副本[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)。</span><span class="sxs-lookup"><span data-stu-id="fbf4e-106">When you call the procedure, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] makes a local copy of every argument that is passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="fbf4e-107">每個引數傳遞[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]提供程序程式碼直接呼叫程式碼中的引數的程式設計項目參考。</span><span class="sxs-lookup"><span data-stu-id="fbf4e-107">For each argument passed [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] gives the procedure code a direct reference to the programming element underlying the argument in the calling code.</span></span>  
  
 <span data-ttu-id="fbf4e-108">如果呼叫程式碼對應的項目設定為可修改的項目，並傳遞引數的`ByRef`，程序程式碼可以使用直接參考來變更呼叫的程式碼中的項目的值。</span><span class="sxs-lookup"><span data-stu-id="fbf4e-108">If the underlying element in the calling code is a modifiable element and the argument is passed `ByRef`, the procedure code can use the direct reference to change the element's value in the calling code.</span></span>  
  
## <a name="changing-the-underlying-value"></a><span data-ttu-id="fbf4e-109">變更基礎值</span><span class="sxs-lookup"><span data-stu-id="fbf4e-109">Changing the Underlying Value</span></span>  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a><span data-ttu-id="fbf4e-110">若要變更基礎值的程序中的引數呼叫的程式碼</span><span class="sxs-lookup"><span data-stu-id="fbf4e-110">To change the underlying value of a procedure argument in the calling code</span></span>  
  
1.  <span data-ttu-id="fbf4e-111">在程序宣告中，指定[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)參數對應至引數。</span><span class="sxs-lookup"><span data-stu-id="fbf4e-111">In the procedure declaration, specify [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) for the parameter corresponding to the argument.</span></span>  
  
2.  <span data-ttu-id="fbf4e-112">在呼叫的程式碼，將傳遞做為引數的可修改的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="fbf4e-112">In the calling code, pass a modifiable programming element as the argument.</span></span>  
  
3.  <span data-ttu-id="fbf4e-113">在呼叫的程式碼，不要使用引數清單中的括號括住的引數。</span><span class="sxs-lookup"><span data-stu-id="fbf4e-113">In the calling code, do not enclose the argument in parentheses in the argument list.</span></span>  
  
4.  <span data-ttu-id="fbf4e-114">在程序程式碼中使用參數名稱來指派值給呼叫程式碼對應的項目。</span><span class="sxs-lookup"><span data-stu-id="fbf4e-114">In the procedure code, use the parameter name to assign a value to the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="fbf4e-115">請參閱範例進一步示範。</span><span class="sxs-lookup"><span data-stu-id="fbf4e-115">See the example further down for a demonstration.</span></span>  
  
## <a name="changing-local-copies"></a><span data-ttu-id="fbf4e-116">變更本機複本</span><span class="sxs-lookup"><span data-stu-id="fbf4e-116">Changing Local Copies</span></span>  
 <span data-ttu-id="fbf4e-117">如果呼叫程式碼對應的項目不可修改的項目，或如果引數傳遞`ByVal`，程序無法變更其呼叫的程式碼中的值。</span><span class="sxs-lookup"><span data-stu-id="fbf4e-117">If the underlying element in the calling code is a nonmodifiable element, or if the argument is passed `ByVal`, the procedure cannot change its value in the calling code.</span></span> <span data-ttu-id="fbf4e-118">不過，此程序可以變更這類引數的本機複本。</span><span class="sxs-lookup"><span data-stu-id="fbf4e-118">However, the procedure can change its local copy of such an argument.</span></span>  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a><span data-ttu-id="fbf4e-119">若要變更的程序中的引數的程序程式碼複製</span><span class="sxs-lookup"><span data-stu-id="fbf4e-119">To change the copy of a procedure argument in the procedure code</span></span>  
  
1.  <span data-ttu-id="fbf4e-120">在程序宣告中，指定[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)參數對應至引數。</span><span class="sxs-lookup"><span data-stu-id="fbf4e-120">In the procedure declaration, specify [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) for the parameter corresponding to the argument.</span></span>  
  
     <span data-ttu-id="fbf4e-121">-或-</span><span class="sxs-lookup"><span data-stu-id="fbf4e-121">-or-</span></span>  
  
     <span data-ttu-id="fbf4e-122">在呼叫程式碼中，括住引數清單中的括號括住的引數。</span><span class="sxs-lookup"><span data-stu-id="fbf4e-122">In the calling code, enclose the argument in parentheses in the argument list.</span></span> <span data-ttu-id="fbf4e-123">這會強制[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]至引數傳值方式傳遞，即使對應的參數會指定`ByRef`。</span><span class="sxs-lookup"><span data-stu-id="fbf4e-123">This forces [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] to pass the argument by value, even if the corresponding parameter specifies `ByRef`.</span></span>  
  
2.  <span data-ttu-id="fbf4e-124">在程序程式碼中，使用參數名稱來指派值給引數的本機複本。</span><span class="sxs-lookup"><span data-stu-id="fbf4e-124">In the procedure code, use the parameter name to assign a value to the local copy of the argument.</span></span> <span data-ttu-id="fbf4e-125">不會變更呼叫的程式碼中的對應值。</span><span class="sxs-lookup"><span data-stu-id="fbf4e-125">The underlying value in the calling code is not changed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbf4e-126">範例</span><span class="sxs-lookup"><span data-stu-id="fbf4e-126">Example</span></span>  
 <span data-ttu-id="fbf4e-127">下列範例會顯示兩個程序取得陣列變數和操作其項目上。</span><span class="sxs-lookup"><span data-stu-id="fbf4e-127">The following example shows two procedures that take an array variable and operate on its elements.</span></span> <span data-ttu-id="fbf4e-128">`increase`程序只會加入至每個項目。</span><span class="sxs-lookup"><span data-stu-id="fbf4e-128">The `increase` procedure simply adds one to each element.</span></span> <span data-ttu-id="fbf4e-129">`replace`程序會將新的陣列指派給參數`a()`並將每個項目。</span><span class="sxs-lookup"><span data-stu-id="fbf4e-129">The `replace` procedure assigns a new array to the parameter `a()` and then adds one to each element.</span></span>  
  
 <span data-ttu-id="fbf4e-130">[!code-vb[VbVbcnProcedures #&35;](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="fbf4e-130">[!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_1.vb)]</span></span>  
  
 <span data-ttu-id="fbf4e-131">[!code-vb[VbVbcnProcedures #&36;](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="fbf4e-131">[!code-vb[VbVbcnProcedures#36](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_2.vb)]</span></span>  
  
 <span data-ttu-id="fbf4e-132">[!code-vb[VbVbcnProcedures #&37;](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="fbf4e-132">[!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_3.vb)]</span></span>  
  
 <span data-ttu-id="fbf4e-133">第一個`MsgBox`呼叫會顯示 「 後 increase(n): 11、 21、 31、 41 」。</span><span class="sxs-lookup"><span data-stu-id="fbf4e-133">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="fbf4e-134">因為陣列`n`是參考型別，`replace`可以變更其成員，即使傳遞機制`ByVal`。</span><span class="sxs-lookup"><span data-stu-id="fbf4e-134">Because the array `n` is a reference type, `replace` can change its members, even though the passing mechanism is `ByVal`.</span></span>  
  
 <span data-ttu-id="fbf4e-135">第二個`MsgBox`呼叫會顯示 「 後 replace(n): 101、 201、 301 」。</span><span class="sxs-lookup"><span data-stu-id="fbf4e-135">The second `MsgBox` call displays "After replace(n): 101, 201, 301".</span></span> <span data-ttu-id="fbf4e-136">因為`n`傳遞`ByRef`，`replace`可以修改變數`n`呼叫程式碼和指派給它的新陣列中。</span><span class="sxs-lookup"><span data-stu-id="fbf4e-136">Because `n` is passed `ByRef`, `replace` can modify the variable `n` in the calling code and assign a new array to it.</span></span> <span data-ttu-id="fbf4e-137">因為`n`是參考型別，`replace`也可以變更其成員。</span><span class="sxs-lookup"><span data-stu-id="fbf4e-137">Because `n` is a reference type, `replace` can also change its members.</span></span>  
  
 <span data-ttu-id="fbf4e-138">您可以防止程序修改呼叫程式碼本身的變數。</span><span class="sxs-lookup"><span data-stu-id="fbf4e-138">You can prevent the procedure from modifying the variable itself in the calling code.</span></span> <span data-ttu-id="fbf4e-139">請參閱[如何︰ 防止程序引數的值變更](./how-to-protect-a-procedure-argument-against-value-changes.md)。</span><span class="sxs-lookup"><span data-stu-id="fbf4e-139">See [How to: Protect a Procedure Argument Against Value Changes](./how-to-protect-a-procedure-argument-against-value-changes.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fbf4e-140">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="fbf4e-140">Compiling the Code</span></span>  
 <span data-ttu-id="fbf4e-141">當您由參考傳遞的變數時，您必須使用`ByRef`關鍵字來指定這項機制。</span><span class="sxs-lookup"><span data-stu-id="fbf4e-141">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="fbf4e-142">在預設[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]是以傳值方式傳遞引數。</span><span class="sxs-lookup"><span data-stu-id="fbf4e-142">The default in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] is to pass arguments by value.</span></span> <span data-ttu-id="fbf4e-143">不過，它是良好的程式設計作法包含[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)或[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)關鍵字與每個宣告的參數。</span><span class="sxs-lookup"><span data-stu-id="fbf4e-143">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="fbf4e-144">這可讓您的程式碼更容易讀取。</span><span class="sxs-lookup"><span data-stu-id="fbf4e-144">This makes your code easier to read.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="fbf4e-145">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="fbf4e-145">.NET Framework Security</span></span>  
 <span data-ttu-id="fbf4e-146">允許的程序來變更對應的引數呼叫的程式碼中的值總是有潛在的風險。</span><span class="sxs-lookup"><span data-stu-id="fbf4e-146">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="fbf4e-147">請確定您預期此變更，並準備好檢查它的有效性，然後再將它的值。</span><span class="sxs-lookup"><span data-stu-id="fbf4e-147">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbf4e-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fbf4e-148">See Also</span></span>  
 <span data-ttu-id="fbf4e-149">[程序](./index.md) </span><span class="sxs-lookup"><span data-stu-id="fbf4e-149">[Procedures](./index.md) </span></span>  
<span data-ttu-id="fbf4e-150"> [程序參數和引數](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="fbf4e-150"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="fbf4e-151"> [如何︰ 將引數傳遞至程序](./how-to-pass-arguments-to-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="fbf4e-151"> [How to: Pass Arguments to a Procedure](./how-to-pass-arguments-to-a-procedure.md) </span></span>  
<span data-ttu-id="fbf4e-152"> [傳遞引數以傳值或傳址](./passing-arguments-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="fbf4e-152"> [Passing Arguments by Value and by Reference](./passing-arguments-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="fbf4e-153"> [可修改和不可修改引數之間的差異](./differences-between-modifiable-and-nonmodifiable-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="fbf4e-153"> [Differences Between Modifiable and Nonmodifiable Arguments](./differences-between-modifiable-and-nonmodifiable-arguments.md) </span></span>  
<span data-ttu-id="fbf4e-154"> [以傳值或參考所傳遞引數之間的差異](./differences-between-passing-an-argument-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="fbf4e-154"> [Differences Between Passing an Argument By Value and By Reference](./differences-between-passing-an-argument-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="fbf4e-155"> [如何︰ 防止程序引數的值變更](./how-to-protect-a-procedure-argument-against-value-changes.md) </span><span class="sxs-lookup"><span data-stu-id="fbf4e-155"> [How to: Protect a Procedure Argument Against Value Changes](./how-to-protect-a-procedure-argument-against-value-changes.md) </span></span>  
<span data-ttu-id="fbf4e-156"> [如何︰ 強制以傳值方式傳遞引數](./how-to-force-an-argument-to-be-passed-by-value.md) </span><span class="sxs-lookup"><span data-stu-id="fbf4e-156"> [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md) </span></span>  
<span data-ttu-id="fbf4e-157"> [依位置和名稱傳遞引數](./passing-arguments-by-position-and-by-name.md) </span><span class="sxs-lookup"><span data-stu-id="fbf4e-157"> [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md) </span></span>  
<span data-ttu-id="fbf4e-158"> [值類型和參考類型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span><span class="sxs-lookup"><span data-stu-id="fbf4e-158"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span></span>
