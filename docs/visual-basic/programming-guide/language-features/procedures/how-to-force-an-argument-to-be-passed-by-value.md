---
title: "如何︰ 強制以傳值 (Visual Basic) 引數 |Microsoft 文件"
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
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures, calling
- arguments [Visual Basic], in parentheses
- procedure arguments, in parentheses
- arguments [Visual Basic], changing value
ms.assetid: 77b4f2d2-1055-4c2f-a521-874d1db86946
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
ms.openlocfilehash: b151c319489ccda357faa082ce0b3c1addad0458
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a><span data-ttu-id="f72b3-102">如何：強制以傳值方式傳遞引數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f72b3-102">How to: Force an Argument to Be Passed by Value (Visual Basic)</span></span>
<span data-ttu-id="f72b3-103">程序宣告決定傳遞機制。</span><span class="sxs-lookup"><span data-stu-id="f72b3-103">The procedure declaration determines the passing mechanism.</span></span> <span data-ttu-id="f72b3-104">如果參數宣告[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]預期相對應的引數傳址方式傳遞。</span><span class="sxs-lookup"><span data-stu-id="f72b3-104">If a parameter is declared [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] expects to pass the corresponding argument by reference.</span></span> <span data-ttu-id="f72b3-105">這可讓變更的基礎呼叫程式碼中的引數的程式設計項目值的程序。</span><span class="sxs-lookup"><span data-stu-id="f72b3-105">This allows the procedure to change the value of the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="f72b3-106">如果您想要保護對應的項目，針對這類變更，您可以覆寫`ByRef`程序中的傳遞機制來呼叫以括號括住的引數名稱。</span><span class="sxs-lookup"><span data-stu-id="f72b3-106">If you wish to protect the underlying element against such change, you can override the `ByRef` passing mechanism in the procedure call by enclosing the argument name in parentheses.</span></span> <span data-ttu-id="f72b3-107">這些括號是封閉的呼叫中引數清單的括號。</span><span class="sxs-lookup"><span data-stu-id="f72b3-107">These parentheses are in addition to the parentheses enclosing the argument list in the call.</span></span>  
  
 <span data-ttu-id="f72b3-108">呼叫程式碼無法覆寫[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)機制。</span><span class="sxs-lookup"><span data-stu-id="f72b3-108">The calling code cannot override a [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) mechanism.</span></span>  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a><span data-ttu-id="f72b3-109">若要強制以傳值方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="f72b3-109">To force an argument to be passed by value</span></span>  
  
-   <span data-ttu-id="f72b3-110">如果對應的參數宣告`ByVal`在程序中，您不需要採取任何額外的步驟。</span><span class="sxs-lookup"><span data-stu-id="f72b3-110">If the corresponding parameter is declared `ByVal` in the procedure, you do not need to take any additional steps.</span></span> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="f72b3-111">已預期傳值方式傳遞引數。</span><span class="sxs-lookup"><span data-stu-id="f72b3-111"> already expects to pass the argument by value.</span></span>  
  
-   <span data-ttu-id="f72b3-112">如果對應的參數宣告`ByRef`在程序，將括在括號內的程序呼叫的引數。</span><span class="sxs-lookup"><span data-stu-id="f72b3-112">If the corresponding parameter is declared `ByRef` in the procedure, enclose the argument in parentheses in the procedure call.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f72b3-113">範例</span><span class="sxs-lookup"><span data-stu-id="f72b3-113">Example</span></span>  
 <span data-ttu-id="f72b3-114">下列範例會覆寫`ByRef`參數宣告。</span><span class="sxs-lookup"><span data-stu-id="f72b3-114">The following example overrides a `ByRef` parameter declaration.</span></span> <span data-ttu-id="f72b3-115">在呼叫中，以強制`ByVal`，請注意括號括住的兩個層級。</span><span class="sxs-lookup"><span data-stu-id="f72b3-115">In the call that forces `ByVal`, note the two levels of parentheses.</span></span>  
  
 <span data-ttu-id="f72b3-116">[!code-vb[VbVbcnProcedures #&39;](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="f72b3-116">[!code-vb[VbVbcnProcedures#39](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_1.vb)]</span></span>  
  
 <span data-ttu-id="f72b3-117">[!code-vb[VbVbcnProcedures #&40;](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="f72b3-117">[!code-vb[VbVbcnProcedures#40](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_2.vb)]</span></span>  
  
 <span data-ttu-id="f72b3-118">當`str`在引數清單中，額外的括號括住`setNewString`程序無法變更呼叫的程式碼，其值和`MsgBox`顯示"如果傳遞 ByVal 無法取代 」。</span><span class="sxs-lookup"><span data-stu-id="f72b3-118">When `str` is enclosed in extra parentheses within the argument list, the `setNewString` procedure cannot change its value in the calling code, and `MsgBox` displays "Cannot be replaced if passed ByVal".</span></span> <span data-ttu-id="f72b3-119">當`str`未隨附在額外的括號中的程序能夠加以修改，和`MsgBox`會顯示 「 這是 inString 引數的新值 」。</span><span class="sxs-lookup"><span data-stu-id="f72b3-119">When `str` is not enclosed in extra parentheses, the procedure can change it, and `MsgBox` displays "This is a new value for the inString argument."</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f72b3-120">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="f72b3-120">Compiling the Code</span></span>  
 <span data-ttu-id="f72b3-121">當您由參考傳遞的變數時，您必須使用`ByRef`關鍵字來指定這項機制。</span><span class="sxs-lookup"><span data-stu-id="f72b3-121">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="f72b3-122">在預設[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]是以傳值方式傳遞引數。</span><span class="sxs-lookup"><span data-stu-id="f72b3-122">The default in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] is to pass arguments by value.</span></span> <span data-ttu-id="f72b3-123">不過，它是良好的程式設計作法包含[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)或[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)關鍵字與每個宣告的參數。</span><span class="sxs-lookup"><span data-stu-id="f72b3-123">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="f72b3-124">這可讓您的程式碼更容易讀取。</span><span class="sxs-lookup"><span data-stu-id="f72b3-124">This makes your code easier to read.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f72b3-125">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="f72b3-125">Robust Programming</span></span>  
 <span data-ttu-id="f72b3-126">如果程序會宣告參數[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)，正確執行的程式碼可能相依於不能變更呼叫的程式碼對應的項目。</span><span class="sxs-lookup"><span data-stu-id="f72b3-126">If a procedure declares a parameter [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), the correct execution of the code might depend on being able to change the underlying element in the calling code.</span></span> <span data-ttu-id="f72b3-127">如果呼叫程式碼覆寫此呼叫的機制以括號括住引數，或將不可修改引數傳遞，此程序無法變更對應的項目。</span><span class="sxs-lookup"><span data-stu-id="f72b3-127">If the calling code overrides this calling mechanism by enclosing the argument in parentheses, or if it passes a nonmodifiable argument, the procedure cannot change the underlying element.</span></span> <span data-ttu-id="f72b3-128">這可能會產生非預期的結果，在呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="f72b3-128">This might produce unexpected results in the calling code.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="f72b3-129">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="f72b3-129">.NET Framework Security</span></span>  
 <span data-ttu-id="f72b3-130">允許的程序來變更對應的引數呼叫的程式碼中的值總是有潛在的風險。</span><span class="sxs-lookup"><span data-stu-id="f72b3-130">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="f72b3-131">請確定您預期此變更，並準備好檢查它的有效性，然後再將它的值。</span><span class="sxs-lookup"><span data-stu-id="f72b3-131">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f72b3-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f72b3-132">See Also</span></span>  
 <span data-ttu-id="f72b3-133">[程序](./index.md) </span><span class="sxs-lookup"><span data-stu-id="f72b3-133">[Procedures](./index.md) </span></span>  
<span data-ttu-id="f72b3-134"> [程序參數和引數](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="f72b3-134"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="f72b3-135"> [如何︰ 將引數傳遞至程序](./how-to-pass-arguments-to-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="f72b3-135"> [How to: Pass Arguments to a Procedure](./how-to-pass-arguments-to-a-procedure.md) </span></span>  
<span data-ttu-id="f72b3-136"> [傳遞引數以傳值或傳址](./passing-arguments-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="f72b3-136"> [Passing Arguments by Value and by Reference](./passing-arguments-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="f72b3-137"> [可修改和不可修改引數之間的差異](./differences-between-modifiable-and-nonmodifiable-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="f72b3-137"> [Differences Between Modifiable and Nonmodifiable Arguments](./differences-between-modifiable-and-nonmodifiable-arguments.md) </span></span>  
<span data-ttu-id="f72b3-138"> [以傳值或參考所傳遞引數之間的差異](./differences-between-passing-an-argument-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="f72b3-138"> [Differences Between Passing an Argument By Value and By Reference](./differences-between-passing-an-argument-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="f72b3-139"> [如何︰ 變更程序引數的值](./how-to-change-the-value-of-a-procedure-argument.md) </span><span class="sxs-lookup"><span data-stu-id="f72b3-139"> [How to: Change the Value of a Procedure Argument](./how-to-change-the-value-of-a-procedure-argument.md) </span></span>  
<span data-ttu-id="f72b3-140"> [如何︰ 防止程序引數的值變更](./how-to-protect-a-procedure-argument-against-value-changes.md) </span><span class="sxs-lookup"><span data-stu-id="f72b3-140"> [How to: Protect a Procedure Argument Against Value Changes](./how-to-protect-a-procedure-argument-against-value-changes.md) </span></span>  
<span data-ttu-id="f72b3-141"> [依位置和名稱傳遞引數](./passing-arguments-by-position-and-by-name.md) </span><span class="sxs-lookup"><span data-stu-id="f72b3-141"> [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md) </span></span>  
<span data-ttu-id="f72b3-142"> [值類型和參考類型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span><span class="sxs-lookup"><span data-stu-id="f72b3-142"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span></span>
