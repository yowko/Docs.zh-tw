---
title: "多載解析 (Visual Basic) |Microsoft 文件"
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
- Visual Basic code, procedures
- overload resolution
- procedures, overloading
- procedures, calling
- procedure overloading, overload resolution
- signatures, procedure
- overloads, resolution
ms.assetid: 766115d1-4352-45fb-859f-6063e0de0ec0
caps.latest.revision: 21
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
ms.openlocfilehash: a4f350af0f7d964df45974990991a2e94b26551e
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="overload-resolution-visual-basic"></a><span data-ttu-id="78f48-102">多載解析 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="78f48-102">Overload Resolution (Visual Basic)</span></span>
<span data-ttu-id="78f48-103">當[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器遇到定義數個多載版本的程序呼叫，編譯器必須決定要呼叫的多載。</span><span class="sxs-lookup"><span data-stu-id="78f48-103">When the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler encounters a call to a procedure that is defined in several overloaded versions, the compiler must decide which of the overloads to call.</span></span> <span data-ttu-id="78f48-104">它會執行下列步驟︰</span><span class="sxs-lookup"><span data-stu-id="78f48-104">It does this by performing the following steps:</span></span>  
  
1.  <span data-ttu-id="78f48-105">**存取範圍。**</span><span class="sxs-lookup"><span data-stu-id="78f48-105">**Accessibility.**</span></span> <span data-ttu-id="78f48-106">它會排除任何防止呼叫程式碼呼叫它的存取層級。</span><span class="sxs-lookup"><span data-stu-id="78f48-106">It eliminates any overload with an access level that prevents the calling code from calling it.</span></span>  
  
2.  <span data-ttu-id="78f48-107">**參數的數目。**</span><span class="sxs-lookup"><span data-stu-id="78f48-107">**Number of Parameters.**</span></span> <span data-ttu-id="78f48-108">這可避免在呼叫中定義不同的參數數目所提供的任何多載。</span><span class="sxs-lookup"><span data-stu-id="78f48-108">It eliminates any overload that defines a different number of parameters than are supplied in the call.</span></span>  
  
3.  <span data-ttu-id="78f48-109">**參數資料類型。**</span><span class="sxs-lookup"><span data-stu-id="78f48-109">**Parameter Data Types.**</span></span> <span data-ttu-id="78f48-110">編譯器會透過擴充方法的執行個體方法的喜好設定。</span><span class="sxs-lookup"><span data-stu-id="78f48-110">The compiler gives instance methods preference over extension methods.</span></span> <span data-ttu-id="78f48-111">如果找不到，只需要擴展轉換來比對程序呼叫的任何執行個體方法，會卸除所有的擴充方法，並只執行個體方法候選對象，編譯器會繼續執行。</span><span class="sxs-lookup"><span data-stu-id="78f48-111">If any instance method is found that requires only widening conversions to match the procedure call, all extension methods are dropped and the compiler continues with only the instance method candidates.</span></span> <span data-ttu-id="78f48-112">如果找到這類的執行個體方法，它會繼續與執行個體和擴充方法。</span><span class="sxs-lookup"><span data-stu-id="78f48-112">If no such instance method is found, it continues with both instance and extension methods.</span></span>  
  
     <span data-ttu-id="78f48-113">在此步驟中，它會排除任何為其呼叫之引數的資料型別無法轉換成在多載中定義的參數型別。</span><span class="sxs-lookup"><span data-stu-id="78f48-113">In this step, it eliminates any overload for which the data types of the calling arguments cannot be converted to the parameter types defined in the overload.</span></span>  
  
4.  <span data-ttu-id="78f48-114">**縮小轉換。**</span><span class="sxs-lookup"><span data-stu-id="78f48-114">**Narrowing Conversions.**</span></span> <span data-ttu-id="78f48-115">這可避免需要從呼叫的引數型別定義的參數型別來縮小轉換的多載。</span><span class="sxs-lookup"><span data-stu-id="78f48-115">It eliminates any overload that requires a narrowing conversion from the calling argument types to the defined parameter types.</span></span> <span data-ttu-id="78f48-116">這是，則為 true 的型別檢查切換是否 ([Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) 是`On`或`Off`。</span><span class="sxs-lookup"><span data-stu-id="78f48-116">This is true whether the type checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) is `On` or `Off`.</span></span>  
  
5.  <span data-ttu-id="78f48-117">**最小的擴展。**</span><span class="sxs-lookup"><span data-stu-id="78f48-117">**Least Widening.**</span></span> <span data-ttu-id="78f48-118">編譯器會考慮在配對中剩餘的多載。</span><span class="sxs-lookup"><span data-stu-id="78f48-118">The compiler considers the remaining overloads in pairs.</span></span> <span data-ttu-id="78f48-119">針對每一個組，它會比較定義之參數的資料型別。</span><span class="sxs-lookup"><span data-stu-id="78f48-119">For each pair, it compares the data types of the defined parameters.</span></span> <span data-ttu-id="78f48-120">如果所有多載中的型別擴展為其他對應的型別，編譯器會排除後者。</span><span class="sxs-lookup"><span data-stu-id="78f48-120">If the types in one of the overloads all widen to the corresponding types in the other, the compiler eliminates the latter.</span></span> <span data-ttu-id="78f48-121">也就是說，它會保留需要最少的擴展的多載。</span><span class="sxs-lookup"><span data-stu-id="78f48-121">That is, it retains the overload that requires the least amount of widening.</span></span>  
  
6.  <span data-ttu-id="78f48-122">**單一的候選。**</span><span class="sxs-lookup"><span data-stu-id="78f48-122">**Single Candidate.**</span></span> <span data-ttu-id="78f48-123">它會繼續考量成對直到只能有一個多載多載被保留，且能解決該多載的呼叫。</span><span class="sxs-lookup"><span data-stu-id="78f48-123">It continues considering overloads in pairs until only one overload remains, and it resolves the call to that overload.</span></span> <span data-ttu-id="78f48-124">如果編譯器無法減少為單一的候選者的多載，它會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="78f48-124">If the compiler cannot reduce the overloads to a single candidate, it generates an error.</span></span>  
  
 <span data-ttu-id="78f48-125">下圖顯示指定的一組多載版本來呼叫哪一個程序。</span><span class="sxs-lookup"><span data-stu-id="78f48-125">The following illustration shows the process that determines which of a set of overloaded versions to call.</span></span>  
  
 <span data-ttu-id="78f48-126">![多載解析程序流程圖](./media/overloadres.gif "OverloadRes")</span><span class="sxs-lookup"><span data-stu-id="78f48-126">![Flow diagram of overload resolution process](./media/overloadres.gif "OverloadRes")</span></span>  
<span data-ttu-id="78f48-127">在多載版本中進行解析</span><span class="sxs-lookup"><span data-stu-id="78f48-127">Resolving among overloaded versions</span></span>  
  
 <span data-ttu-id="78f48-128">下列範例說明此多載解析程序。</span><span class="sxs-lookup"><span data-stu-id="78f48-128">The following example illustrates this overload resolution process.</span></span>  
  
 <span data-ttu-id="78f48-129">[!code-vb[VbVbcnProcedures #&62;](./codesnippet/VisualBasic/overload-resolution_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="78f48-129">[!code-vb[VbVbcnProcedures#62](./codesnippet/VisualBasic/overload-resolution_1.vb)]</span></span>  
  
 <span data-ttu-id="78f48-130">[!code-vb[VbVbcnProcedures #&63;](./codesnippet/VisualBasic/overload-resolution_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="78f48-130">[!code-vb[VbVbcnProcedures#63](./codesnippet/VisualBasic/overload-resolution_2.vb)]</span></span>  
  
 <span data-ttu-id="78f48-131">在第一次呼叫時，編譯器會排除第一個多載因為第一個引數型別 (`Short`) 的範圍縮小，對應參數的型別 (`Byte`)。</span><span class="sxs-lookup"><span data-stu-id="78f48-131">In the first call, the compiler eliminates the first overload because the type of the first argument (`Short`) narrows to the type of the corresponding parameter (`Byte`).</span></span> <span data-ttu-id="78f48-132">它接著排除第三個多載，因為每個引數型別中的第二個多載 (`Short`和`Single`) 擴展至對應的型別中的第三個多載 (`Integer`和`Single`)。</span><span class="sxs-lookup"><span data-stu-id="78f48-132">It then eliminates the third overload because each argument type in the second overload (`Short` and `Single`) widens to the corresponding type in the third overload (`Integer` and `Single`).</span></span> <span data-ttu-id="78f48-133">第二個多載需要較少的擴展，因此編譯器會將它的呼叫。</span><span class="sxs-lookup"><span data-stu-id="78f48-133">The second overload requires less widening, so the compiler uses it for the call.</span></span>  
  
 <span data-ttu-id="78f48-134">在第二個呼叫中，編譯器無法排除任何以縮小為基礎的多載。</span><span class="sxs-lookup"><span data-stu-id="78f48-134">In the second call, the compiler cannot eliminate any of the overloads on the basis of narrowing.</span></span> <span data-ttu-id="78f48-135">它也消除了第三個多載基於相同理由，第一個呼叫，因為它可以呼叫第二個多載，較不需要擴展引數型別。</span><span class="sxs-lookup"><span data-stu-id="78f48-135">It eliminates the third overload for the same reason as in the first call, because it can call the second overload with less widening of the argument types.</span></span> <span data-ttu-id="78f48-136">不過，編譯器無法解析的第一個和第二個多載之間。</span><span class="sxs-lookup"><span data-stu-id="78f48-136">However, the compiler cannot resolve between the first and second overloads.</span></span> <span data-ttu-id="78f48-137">每個都有擴展至對應的型別，在另一個定義的參數型別 (`Byte`至`Short`，但`Single`到`Double`)。</span><span class="sxs-lookup"><span data-stu-id="78f48-137">Each has one defined parameter type that widens to the corresponding type in the other (`Byte` to `Short`, but `Single` to `Double`).</span></span> <span data-ttu-id="78f48-138">因此，編譯器會產生多載解析錯誤。</span><span class="sxs-lookup"><span data-stu-id="78f48-138">The compiler therefore generates an overload resolution error.</span></span>  
  
## <a name="overloaded-optional-and-paramarray-arguments"></a><span data-ttu-id="78f48-139">選擇性的多載和 ParamArray 引數</span><span class="sxs-lookup"><span data-stu-id="78f48-139">Overloaded Optional and ParamArray Arguments</span></span>  
 <span data-ttu-id="78f48-140">如果程序的兩個多載具有相同的簽章，不同之處在於最後一個參數宣告[選擇性](../../../../visual-basic/language-reference/modifiers/optional.md)之一和[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)在另一個，編譯器會解析該程序的呼叫，如下所示︰</span><span class="sxs-lookup"><span data-stu-id="78f48-140">If two overloads of a procedure have identical signatures except that the last parameter is declared [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) in one and [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) in the other, the compiler resolves a call to that procedure as follows:</span></span>  
  
|<span data-ttu-id="78f48-141">如果呼叫所提供做為最後一個引數</span><span class="sxs-lookup"><span data-stu-id="78f48-141">If the call supplies the last argument as</span></span>|<span data-ttu-id="78f48-142">編譯器將呼叫解析為宣告做為最後一個引數的多載</span><span class="sxs-lookup"><span data-stu-id="78f48-142">The compiler resolves the call to the overload declaring the last argument as</span></span>|  
|---|---|  
|<span data-ttu-id="78f48-143">沒有值 （省略引數）</span><span class="sxs-lookup"><span data-stu-id="78f48-143">No value (argument omitted)</span></span>|`Optional`|  
|<span data-ttu-id="78f48-144">單一值</span><span class="sxs-lookup"><span data-stu-id="78f48-144">A single value</span></span>|`Optional`|  
|<span data-ttu-id="78f48-145">以逗號分隔的清單中的兩個或多個值</span><span class="sxs-lookup"><span data-stu-id="78f48-145">Two or more values in a comma-separated list</span></span>|`ParamArray`|  
|<span data-ttu-id="78f48-146">陣列的長度 （包括空的陣列）</span><span class="sxs-lookup"><span data-stu-id="78f48-146">An array of any length (including an empty array)</span></span>|`ParamArray`|  
  
## <a name="see-also"></a><span data-ttu-id="78f48-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78f48-147">See Also</span></span>  
 <span data-ttu-id="78f48-148">[選擇性參數](./optional-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="78f48-148">[Optional Parameters](./optional-parameters.md) </span></span>  
<span data-ttu-id="78f48-149"> [參數陣列](./parameter-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="78f48-149"> [Parameter Arrays](./parameter-arrays.md) </span></span>  
<span data-ttu-id="78f48-150"> [多載化程序](./procedure-overloading.md) </span><span class="sxs-lookup"><span data-stu-id="78f48-150"> [Procedure Overloading](./procedure-overloading.md) </span></span>  
<span data-ttu-id="78f48-151"> [疑難排解程序](./troubleshooting-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="78f48-151"> [Troubleshooting Procedures](./troubleshooting-procedures.md) </span></span>  
<span data-ttu-id="78f48-152"> [如何︰ 定義程序的多個版本](./how-to-define-multiple-versions-of-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="78f48-152"> [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md) </span></span>  
<span data-ttu-id="78f48-153"> [如何︰ 呼叫多載程序](./how-to-call-an-overloaded-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="78f48-153"> [How to: Call an Overloaded Procedure](./how-to-call-an-overloaded-procedure.md) </span></span>  
<span data-ttu-id="78f48-154"> [如何︰ 多載使用選擇性參數的程序](./how-to-overload-a-procedure-that-takes-optional-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="78f48-154"> [How to: Overload a Procedure that Takes Optional Parameters](./how-to-overload-a-procedure-that-takes-optional-parameters.md) </span></span>  
<span data-ttu-id="78f48-155"> [如何︰ 多載使用不定數目參數的程序](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="78f48-155"> [How to: Overload a Procedure that Takes an Indefinite Number of Parameters](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md) </span></span>  
<span data-ttu-id="78f48-156"> [多載化程序的考量](./considerations-in-overloading-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="78f48-156"> [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md) </span></span>  
<span data-ttu-id="78f48-157"> [多載](../../../../visual-basic/language-reference/modifiers/overloads.md) </span><span class="sxs-lookup"><span data-stu-id="78f48-157"> [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) </span></span>  
<span data-ttu-id="78f48-158"> [擴充方法](./extension-methods.md)</span><span class="sxs-lookup"><span data-stu-id="78f48-158"> [Extension Methods](./extension-methods.md)</span></span>
