---
title: "如何：多載使用選擇性參數的程序 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], optional parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: 825f9d56-4cde-43fd-993a-b9171717e2eb
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b4a863944d4f9ab265aab52578fbb704ca376de5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a><span data-ttu-id="cf204-102">如何：多載使用選擇性參數的程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf204-102">How to: Overload a Procedure that Takes Optional Parameters (Visual Basic)</span></span>
<span data-ttu-id="cf204-103">如果程序有一或多個[選擇性](../../../../visual-basic/language-reference/modifiers/optional.md)參數，您不能定義比對任何隱含的多載的多載的版本。</span><span class="sxs-lookup"><span data-stu-id="cf204-103">If a procedure has one or more [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) parameters, you cannot define an overloaded version matching any of its implicit overloads.</span></span> <span data-ttu-id="cf204-104">如需詳細資訊，請參閱 < 隱含多載的選擇性參數 」[中多載化程序的考量](./considerations-in-overloading-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="cf204-104">For more information, see "Implicit Overloads for Optional Parameters" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="one-optional-parameter"></a><span data-ttu-id="cf204-105">一個選擇性參數</span><span class="sxs-lookup"><span data-stu-id="cf204-105">One Optional Parameter</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a><span data-ttu-id="cf204-106">若要多載會接受一個選擇性參數的程序</span><span class="sxs-lookup"><span data-stu-id="cf204-106">To overload a procedure that takes one optional parameter</span></span>  
  
1.  <span data-ttu-id="cf204-107">寫入`Sub`或`Function`包含選擇性參數，參數清單中的宣告陳述式。</span><span class="sxs-lookup"><span data-stu-id="cf204-107">Write a `Sub` or `Function` declaration statement that includes the optional parameter in the parameter list.</span></span> <span data-ttu-id="cf204-108">請勿使用`Optional`關鍵字，在這個多載版本。</span><span class="sxs-lookup"><span data-stu-id="cf204-108">Do not use the `Optional` keyword in this overloaded version.</span></span>  
  
2.  <span data-ttu-id="cf204-109">在前面`Sub`或`Function`關鍵字搭配[多載](../../../../visual-basic/language-reference/modifiers/overloads.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="cf204-109">Precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
3.  <span data-ttu-id="cf204-110">撰寫呼叫的程式碼提供選擇性引數時所應執行的程序程式碼。</span><span class="sxs-lookup"><span data-stu-id="cf204-110">Write the procedure code that should execute when the calling code supplies the optional argument.</span></span>  
  
4.  <span data-ttu-id="cf204-111">終止程序具有`End Sub`或`End Function`視陳述式。</span><span class="sxs-lookup"><span data-stu-id="cf204-111">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
5.  <span data-ttu-id="cf204-112">撰寫等同於第一個宣告不同之處在於它不包含選擇性的參數在參數清單中的第二個宣告陳述式。</span><span class="sxs-lookup"><span data-stu-id="cf204-112">Write a second declaration statement that is identical to the first declaration except that it does not include the optional parameter in the parameter list.</span></span>  
  
6.  <span data-ttu-id="cf204-113">撰寫呼叫的程式碼並不提供選擇性引數時所應執行的程序程式碼。</span><span class="sxs-lookup"><span data-stu-id="cf204-113">Write the procedure code that should execute when the calling code does not supply the optional argument.</span></span> <span data-ttu-id="cf204-114">終止程序具有`End Sub`或`End Function`視陳述式。</span><span class="sxs-lookup"><span data-stu-id="cf204-114">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
     <span data-ttu-id="cf204-115">下列範例顯示具有選擇性參數，兩個多載程序，以及最後的範例不正確且有效的多載版本組定義的程序。</span><span class="sxs-lookup"><span data-stu-id="cf204-115">The following example shows a procedure defined with an optional parameter,  an equivalent set of two overloaded procedures, and finally examples of both invalid and valid overloaded versions.</span></span>  
  
     [!code-vb[VbVbcnProcedures#59](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_1.vb)]  
  
     [!code-vb[VbVbcnProcedures#60](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_2.vb)]  
  
     [!code-vb[VbVbcnProcedures#61](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_3.vb)]  
  
## <a name="multiple-optional-parameters"></a><span data-ttu-id="cf204-116">多個選擇性參數</span><span class="sxs-lookup"><span data-stu-id="cf204-116">Multiple Optional Parameters</span></span>  
 <span data-ttu-id="cf204-117">針對具有一個以上的選擇性參數的程序，您通常需要兩個以上的多載的版本。</span><span class="sxs-lookup"><span data-stu-id="cf204-117">For a procedure with more than one optional parameter, you normally need more than two overloaded versions.</span></span> <span data-ttu-id="cf204-118">例如，如果有兩個選擇性參數，而且呼叫程式碼可以提供或略過每個彼此獨立，您會需要四個多載的版本，一個用於每個可能的組合，提供的引數。</span><span class="sxs-lookup"><span data-stu-id="cf204-118">For example, if there are two optional parameters, and the calling code can supply or omit each one independently of the other, you need four overloaded versions, one for each possible combination of supplied arguments.</span></span>  
  
 <span data-ttu-id="cf204-119">選擇性參數的數目增加時，會增加多載的複雜度。</span><span class="sxs-lookup"><span data-stu-id="cf204-119">As the number of optional parameters increases, the complexity of the overloading increases.</span></span> <span data-ttu-id="cf204-120">某些組合提供的引數不是可接受的除非 N 選擇性參數的您需要 2 ^ N 多載版本。</span><span class="sxs-lookup"><span data-stu-id="cf204-120">Unless some combinations of supplied arguments are not acceptable, for N optional parameters you need 2 ^ N overloaded versions.</span></span> <span data-ttu-id="cf204-121">根據程序的本質，您可能會發現清楚的邏輯靠右對齊的額外努力定義所有多載的版本。</span><span class="sxs-lookup"><span data-stu-id="cf204-121">Depending on the nature of the procedure, you might find that the clarity of logic justifies the extra effort of defining all the overloaded versions.</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a><span data-ttu-id="cf204-122">若要多載會接受一個以上的選擇性參數的程序</span><span class="sxs-lookup"><span data-stu-id="cf204-122">To overload a procedure that takes more than one optional parameter</span></span>  
  
1.  <span data-ttu-id="cf204-123">判斷哪些組合提供的選擇性引數是可接受的程序邏輯。</span><span class="sxs-lookup"><span data-stu-id="cf204-123">Determine which combinations of supplied optional arguments are acceptable to the logic of the procedure.</span></span> <span data-ttu-id="cf204-124">如果一個選擇性參數相依於另一個，可能會引發無法接受的組合。</span><span class="sxs-lookup"><span data-stu-id="cf204-124">An unacceptable combination might arise if one optional parameter depends on another.</span></span> <span data-ttu-id="cf204-125">比方說，如果一個參數接受配偶的名稱，且另一個接受配偶的時代，是無法接受的引數提供存留期，但略過名稱組合。</span><span class="sxs-lookup"><span data-stu-id="cf204-125">For example, if one parameter accepts a spouse's name and another accepts the spouse's age, a combination of arguments supplying the age but omitting the name is unacceptable.</span></span>  
  
2.  <span data-ttu-id="cf204-126">每個可接受的組合提供選擇性引數，寫入`Sub`或`Function`定義對應的參數清單的宣告陳述式。</span><span class="sxs-lookup"><span data-stu-id="cf204-126">For each acceptable combination of supplied optional arguments, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="cf204-127">請勿使用`Optional`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="cf204-127">Do not use the `Optional` keyword.</span></span>  
  
3.  <span data-ttu-id="cf204-128">在每個宣告中前,`Sub`或`Function`關鍵字搭配[多載](../../../../visual-basic/language-reference/modifiers/overloads.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="cf204-128">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
4.  <span data-ttu-id="cf204-129">下列每個宣告中，寫入執行時呼叫的程式碼提供與該宣告的參數清單有對應的引數清單的程序程式碼。</span><span class="sxs-lookup"><span data-stu-id="cf204-129">Following each declaration, write the procedure code that should execute when the calling code supplies an argument list corresponding to that declaration's parameter list.</span></span>  
  
5.  <span data-ttu-id="cf204-130">終止與每個程序`End Sub`或`End Function`視陳述式。</span><span class="sxs-lookup"><span data-stu-id="cf204-130">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf204-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf204-131">See Also</span></span>  
 [<span data-ttu-id="cf204-132">程序</span><span class="sxs-lookup"><span data-stu-id="cf204-132">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="cf204-133">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="cf204-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="cf204-134">選擇性參數</span><span class="sxs-lookup"><span data-stu-id="cf204-134">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="cf204-135">參數陣列</span><span class="sxs-lookup"><span data-stu-id="cf204-135">Parameter Arrays</span></span>](./parameter-arrays.md)  
 [<span data-ttu-id="cf204-136">程序多載化</span><span class="sxs-lookup"><span data-stu-id="cf204-136">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="cf204-137">程序的疑難排解</span><span class="sxs-lookup"><span data-stu-id="cf204-137">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)  
 [<span data-ttu-id="cf204-138">如何：定義程序的多個版本</span><span class="sxs-lookup"><span data-stu-id="cf204-138">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)  
 [<span data-ttu-id="cf204-139">如何：呼叫多載程序</span><span class="sxs-lookup"><span data-stu-id="cf204-139">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)  
 [<span data-ttu-id="cf204-140">如何：多載使用不確定參數數目的程序</span><span class="sxs-lookup"><span data-stu-id="cf204-140">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [<span data-ttu-id="cf204-141">多載解析</span><span class="sxs-lookup"><span data-stu-id="cf204-141">Overload Resolution</span></span>](./overload-resolution.md)
