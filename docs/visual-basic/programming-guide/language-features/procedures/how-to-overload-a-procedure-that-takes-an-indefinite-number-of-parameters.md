---
title: "如何︰ 多載不定數目參數 (Visual Basic) 的程序 |Microsoft 文件"
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
- procedures, parameters
- procedure overloading, indefinite number of parameters
- procedures, defining
- Visual Basic code, procedures
- procedure parameters
- procedures, overloading
- procedures, multiple versions
ms.assetid: c7042de2-2422-4039-94e8-ac298896af69
caps.latest.revision: 18
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
ms.openlocfilehash: 3e4ef81049f3b0d3ab1271fb709f07c37f274a88
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a><span data-ttu-id="c4cd2-102">如何：多載使用不定數目參數的程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4cd2-102">How to: Overload a Procedure that Takes an Indefinite Number of Parameters (Visual Basic)</span></span>
<span data-ttu-id="c4cd2-103">如果程序[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)參數，您不能定義採取參數陣列的一維陣列的多載的版本。</span><span class="sxs-lookup"><span data-stu-id="c4cd2-103">If a procedure has a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, you cannot define an overloaded version taking a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="c4cd2-104">如需詳細資訊，請參閱 「 隱含多載的參數陣列參數 」 中[中多載化程序的考量](./considerations-in-overloading-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="c4cd2-104">For more information, see "Implicit Overloads for a ParamArray Parameter" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a><span data-ttu-id="c4cd2-105">若要多載接受可變數目之參數的程序</span><span class="sxs-lookup"><span data-stu-id="c4cd2-105">To overload a procedure that takes a variable number of parameters</span></span>  
  
1.  <span data-ttu-id="c4cd2-106">確定此程序與呼叫程式碼邏輯也可利用多載版本，從多個`ParamArray`參數。</span><span class="sxs-lookup"><span data-stu-id="c4cd2-106">Ascertain that the procedure and calling code logic benefits from overloaded versions more than from a `ParamArray` parameter.</span></span> <span data-ttu-id="c4cd2-107">請參閱 < 多載和參數陣列"[多載化程序的考量](./considerations-in-overloading-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="c4cd2-107">See "Overloads and ParamArrays" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
2.  <span data-ttu-id="c4cd2-108">決定程序應該接受的參數清單的變動部分的提供值的數目。</span><span class="sxs-lookup"><span data-stu-id="c4cd2-108">Determine which numbers of supplied values the procedure should accept in the variable part of the parameter list.</span></span> <span data-ttu-id="c4cd2-109">這可能包括大小寫的任何值，且可能包含單一的一維陣列的大小寫。</span><span class="sxs-lookup"><span data-stu-id="c4cd2-109">This might include the case of no value, and it might include the case of a single one-dimensional array.</span></span>  
  
3.  <span data-ttu-id="c4cd2-110">針對每個可接受提供的值數目，寫入`Sub`或`Function`宣告陳述式來定義對應的參數清單。</span><span class="sxs-lookup"><span data-stu-id="c4cd2-110">For each acceptable number of supplied values, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="c4cd2-111">請勿使用 `Optional`或`ParamArray`這個多載版本中的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="c4cd2-111">Do not use either the `Optional` or the `ParamArray` keyword in this overloaded version.</span></span>  
  
4.  <span data-ttu-id="c4cd2-112">在每個宣告中前,`Sub`或`Function`關鍵字[多載](../../../../visual-basic/language-reference/modifiers/overloads.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="c4cd2-112">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
5.  <span data-ttu-id="c4cd2-113">下列每個宣告，撰寫呼叫的程式碼提供與該宣告的參數清單的對應值時所應執行的程序程式碼。</span><span class="sxs-lookup"><span data-stu-id="c4cd2-113">Following each declaration, write the procedure code that should execute when the calling code supplies values corresponding to that declaration's parameter list.</span></span>  
  
6.  <span data-ttu-id="c4cd2-114">終止與每個程序`End Sub`或`End Function`視陳述式。</span><span class="sxs-lookup"><span data-stu-id="c4cd2-114">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4cd2-115">範例</span><span class="sxs-lookup"><span data-stu-id="c4cd2-115">Example</span></span>  
 <span data-ttu-id="c4cd2-116">下列範例顯示定義的程序[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)參數，然後再組多載程序。</span><span class="sxs-lookup"><span data-stu-id="c4cd2-116">The following example shows a procedure defined with a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, and then an equivalent set of overloaded procedures.</span></span>  
  
 <span data-ttu-id="c4cd2-117">[!code-vb[VbVbcnProcedures #&69;](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="c4cd2-117">[!code-vb[VbVbcnProcedures#69](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_1.vb)]</span></span>  
  
 <span data-ttu-id="c4cd2-118">[!code-vb[VbVbcnProcedures #&70;](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="c4cd2-118">[!code-vb[VbVbcnProcedures#70](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_2.vb)]</span></span>  
  
 <span data-ttu-id="c4cd2-119">您無法多載，這樣的程序的參數清單，會採用參數陣列的一維陣列。</span><span class="sxs-lookup"><span data-stu-id="c4cd2-119">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="c4cd2-120">不過，您可以使用其他隱含多載的簽章。</span><span class="sxs-lookup"><span data-stu-id="c4cd2-120">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="c4cd2-121">下列宣告可說明這點。</span><span class="sxs-lookup"><span data-stu-id="c4cd2-121">The following declarations illustrate this.</span></span>  
  
 <span data-ttu-id="c4cd2-122">[!code-vb[VbVbcnProcedures #&71;](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="c4cd2-122">[!code-vb[VbVbcnProcedures#71](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_3.vb)]</span></span>  
  
 <span data-ttu-id="c4cd2-123">若要測試是否呼叫的程式碼提供一個或多個值並沒有多載版本中的程式碼`ParamArray`參數，或如果是這樣，多少。</span><span class="sxs-lookup"><span data-stu-id="c4cd2-123">The code in the overloaded versions does not have to test whether the calling code supplied one or more values for the `ParamArray` parameter, or if so, how many.</span></span> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="c4cd2-124">將控制項傳遞到符合呼叫的引數清單的版本。</span><span class="sxs-lookup"><span data-stu-id="c4cd2-124"> passes control to the version matching the calling argument list.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c4cd2-125">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="c4cd2-125">Compiling the Code</span></span>  
 <span data-ttu-id="c4cd2-126">因為程序時使用`ParamArray`參數相當於一組多載版本，您無法多載，這樣的程序使用的參數清單，對應到任何這些隱含多載。</span><span class="sxs-lookup"><span data-stu-id="c4cd2-126">Because a procedure with a `ParamArray` parameter is equivalent to a set of overloaded versions, you cannot overload such a procedure with a parameter list corresponding to any of these implicit overloads.</span></span> <span data-ttu-id="c4cd2-127">如需詳細資訊，請參閱[中多載化程序的考量](./considerations-in-overloading-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="c4cd2-127">For more information, see [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="c4cd2-128">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="c4cd2-128">.NET Framework Security</span></span>  
 <span data-ttu-id="c4cd2-129">只要處理陣列，其中可能會無限期地大，會造成您的應用程式內部容量滿溢的風險。</span><span class="sxs-lookup"><span data-stu-id="c4cd2-129">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="c4cd2-130">如果您接受參數陣列時，您應該測試呼叫程式碼傳遞給它，陣列的長度，並採取適當步驟，如果您的應用程式而言太大。</span><span class="sxs-lookup"><span data-stu-id="c4cd2-130">If you accept a parameter array, you should test for the length of the array the calling code passed to it, and take appropriate steps if it is too large for your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4cd2-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4cd2-131">See Also</span></span>  
 <span data-ttu-id="c4cd2-132">[程序](./index.md) </span><span class="sxs-lookup"><span data-stu-id="c4cd2-132">[Procedures](./index.md) </span></span>  
<span data-ttu-id="c4cd2-133"> [程序參數和引數](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="c4cd2-133"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="c4cd2-134"> [選擇性參數](./optional-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="c4cd2-134"> [Optional Parameters](./optional-parameters.md) </span></span>  
<span data-ttu-id="c4cd2-135"> [參數陣列](./parameter-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="c4cd2-135"> [Parameter Arrays](./parameter-arrays.md) </span></span>  
<span data-ttu-id="c4cd2-136"> [多載化程序](./procedure-overloading.md) </span><span class="sxs-lookup"><span data-stu-id="c4cd2-136"> [Procedure Overloading](./procedure-overloading.md) </span></span>  
<span data-ttu-id="c4cd2-137"> [疑難排解程序](./troubleshooting-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="c4cd2-137"> [Troubleshooting Procedures](./troubleshooting-procedures.md) </span></span>  
<span data-ttu-id="c4cd2-138"> [如何︰ 定義程序的多個版本](./how-to-define-multiple-versions-of-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="c4cd2-138"> [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md) </span></span>  
<span data-ttu-id="c4cd2-139"> [如何︰ 呼叫多載程序](./how-to-call-an-overloaded-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="c4cd2-139"> [How to: Call an Overloaded Procedure](./how-to-call-an-overloaded-procedure.md) </span></span>  
<span data-ttu-id="c4cd2-140"> [如何︰ 多載使用選擇性參數的程序](./how-to-overload-a-procedure-that-takes-optional-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="c4cd2-140"> [How to: Overload a Procedure that Takes Optional Parameters](./how-to-overload-a-procedure-that-takes-optional-parameters.md) </span></span>  
<span data-ttu-id="c4cd2-141"> [多載解析](./overload-resolution.md)</span><span class="sxs-lookup"><span data-stu-id="c4cd2-141"> [Overload Resolution](./overload-resolution.md)</span></span>
