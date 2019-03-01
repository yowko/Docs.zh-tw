---
title: 多載解析 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- overload resolution
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedure overloading [Visual Basic], overload resolution
- signatures [Visual Basic], procedure
- overloads [Visual Basic], resolution
ms.assetid: 766115d1-4352-45fb-859f-6063e0de0ec0
ms.openlocfilehash: c55b1c001ae1c74b0c34d716b9fa3f90dade3e28
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966225"
---
# <a name="overload-resolution-visual-basic"></a><span data-ttu-id="ae2f6-102">多載解析 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae2f6-102">Overload Resolution (Visual Basic)</span></span>
<span data-ttu-id="ae2f6-103">當 Visual Basic 編譯器遇到定義在數個多載版本的程序的呼叫時，編譯器必須決定要呼叫的多載。</span><span class="sxs-lookup"><span data-stu-id="ae2f6-103">When the Visual Basic compiler encounters a call to a procedure that is defined in several overloaded versions, the compiler must decide which of the overloads to call.</span></span> <span data-ttu-id="ae2f6-104">它會執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="ae2f6-104">It does this by performing the following steps:</span></span>  
  
1.  <span data-ttu-id="ae2f6-105">**協助工具。**</span><span class="sxs-lookup"><span data-stu-id="ae2f6-105">**Accessibility.**</span></span> <span data-ttu-id="ae2f6-106">它會排除任何多載，以防止呼叫程式碼呼叫它的存取層級。</span><span class="sxs-lookup"><span data-stu-id="ae2f6-106">It eliminates any overload with an access level that prevents the calling code from calling it.</span></span>  
  
2.  <span data-ttu-id="ae2f6-107">**參數的數目。**</span><span class="sxs-lookup"><span data-stu-id="ae2f6-107">**Number of Parameters.**</span></span> <span data-ttu-id="ae2f6-108">它會排除任何在呼叫中定義不同數目的參數所提供的多載。</span><span class="sxs-lookup"><span data-stu-id="ae2f6-108">It eliminates any overload that defines a different number of parameters than are supplied in the call.</span></span>  
  
3.  <span data-ttu-id="ae2f6-109">**參數資料類型。**</span><span class="sxs-lookup"><span data-stu-id="ae2f6-109">**Parameter Data Types.**</span></span> <span data-ttu-id="ae2f6-110">編譯器會提供於延伸方法的執行個體方法的喜好設定。</span><span class="sxs-lookup"><span data-stu-id="ae2f6-110">The compiler gives instance methods preference over extension methods.</span></span> <span data-ttu-id="ae2f6-111">如果找不到需要僅限於擴展轉換，來比對程序呼叫的任何執行個體方法，會卸除所有擴充方法，編譯器會繼續進行 僅執行個體方法候選對象。</span><span class="sxs-lookup"><span data-stu-id="ae2f6-111">If any instance method is found that requires only widening conversions to match the procedure call, all extension methods are dropped and the compiler continues with only the instance method candidates.</span></span> <span data-ttu-id="ae2f6-112">如果找不到任何這類執行個體方法，它會繼續與執行個體和擴充方法。</span><span class="sxs-lookup"><span data-stu-id="ae2f6-112">If no such instance method is found, it continues with both instance and extension methods.</span></span>  
  
     <span data-ttu-id="ae2f6-113">在此步驟中，它會排除任何多載的呼叫的引數的資料類型無法轉換至多載中定義的參數類型。</span><span class="sxs-lookup"><span data-stu-id="ae2f6-113">In this step, it eliminates any overload for which the data types of the calling arguments cannot be converted to the parameter types defined in the overload.</span></span>  
  
4.  <span data-ttu-id="ae2f6-114">**縮小轉換。**</span><span class="sxs-lookup"><span data-stu-id="ae2f6-114">**Narrowing Conversions.**</span></span> <span data-ttu-id="ae2f6-115">它會排除任何多載，必須呼叫的引數型別定義的參數類型是縮小轉換。</span><span class="sxs-lookup"><span data-stu-id="ae2f6-115">It eliminates any overload that requires a narrowing conversion from the calling argument types to the defined parameter types.</span></span> <span data-ttu-id="ae2f6-116">這是 true 不論類型檢查參數 ([Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) 是`On`或`Off`。</span><span class="sxs-lookup"><span data-stu-id="ae2f6-116">This is true whether the type checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) is `On` or `Off`.</span></span>  
  
5.  <span data-ttu-id="ae2f6-117">**最小的擴展。**</span><span class="sxs-lookup"><span data-stu-id="ae2f6-117">**Least Widening.**</span></span> <span data-ttu-id="ae2f6-118">編譯器會考慮在配對中剩餘的多載。</span><span class="sxs-lookup"><span data-stu-id="ae2f6-118">The compiler considers the remaining overloads in pairs.</span></span> <span data-ttu-id="ae2f6-119">針對每一組，它會比較定義之參數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="ae2f6-119">For each pair, it compares the data types of the defined parameters.</span></span> <span data-ttu-id="ae2f6-120">如果中其中一個所有多載的型別會擴展為其他對應的型別，則編譯器會排除後者。</span><span class="sxs-lookup"><span data-stu-id="ae2f6-120">If the types in one of the overloads all widen to the corresponding types in the other, the compiler eliminates the latter.</span></span> <span data-ttu-id="ae2f6-121">也就是說，它會保留需要最少擴展的多載。</span><span class="sxs-lookup"><span data-stu-id="ae2f6-121">That is, it retains the overload that requires the least amount of widening.</span></span>  
  
6.  <span data-ttu-id="ae2f6-122">**單一的候選項目。**</span><span class="sxs-lookup"><span data-stu-id="ae2f6-122">**Single Candidate.**</span></span> <span data-ttu-id="ae2f6-123">它會繼續考量之前只有一個配對中的多載多載會保留，且能解決該多載的呼叫。</span><span class="sxs-lookup"><span data-stu-id="ae2f6-123">It continues considering overloads in pairs until only one overload remains, and it resolves the call to that overload.</span></span> <span data-ttu-id="ae2f6-124">如果編譯器無法減少為單一的候選者的多載，它會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="ae2f6-124">If the compiler cannot reduce the overloads to a single candidate, it generates an error.</span></span>  
  
 <span data-ttu-id="ae2f6-125">下圖顯示決定哪一個多載版本，以呼叫一組程序。</span><span class="sxs-lookup"><span data-stu-id="ae2f6-125">The following illustration shows the process that determines which of a set of overloaded versions to call.</span></span>  
  
 <span data-ttu-id="ae2f6-126">![多載解析程序流程圖](./media/overloadres.gif "OverloadRes")</span><span class="sxs-lookup"><span data-stu-id="ae2f6-126">![Flow diagram of overload resolution process](./media/overloadres.gif "OverloadRes")</span></span>  
<span data-ttu-id="ae2f6-127">在多載版本中進行解析</span><span class="sxs-lookup"><span data-stu-id="ae2f6-127">Resolving among overloaded versions</span></span>  
  
 <span data-ttu-id="ae2f6-128">下列範例說明此多載解析程序。</span><span class="sxs-lookup"><span data-stu-id="ae2f6-128">The following example illustrates this overload resolution process.</span></span>  
  
 [!code-vb[VbVbcnProcedures#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbcnProcedures#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#63)]  
  
 <span data-ttu-id="ae2f6-129">在第一個呼叫中，編譯器會排除第一個多載因為第一個引數的類型 (`Short`) 的範圍縮小，對應參數的型別 (`Byte`)。</span><span class="sxs-lookup"><span data-stu-id="ae2f6-129">In the first call, the compiler eliminates the first overload because the type of the first argument (`Short`) narrows to the type of the corresponding parameter (`Byte`).</span></span> <span data-ttu-id="ae2f6-130">它然後排除第三個多載，因為每個引數類型中的第二個多載 (`Short`並`Single`) 可擴展為對應的型別中的第三個多載 (`Integer`和`Single`)。</span><span class="sxs-lookup"><span data-stu-id="ae2f6-130">It then eliminates the third overload because each argument type in the second overload (`Short` and `Single`) widens to the corresponding type in the third overload (`Integer` and `Single`).</span></span> <span data-ttu-id="ae2f6-131">第二個多載都需要較少的擴展，因此編譯器會將它用於呼叫。</span><span class="sxs-lookup"><span data-stu-id="ae2f6-131">The second overload requires less widening, so the compiler uses it for the call.</span></span>  
  
 <span data-ttu-id="ae2f6-132">在第二個呼叫中，編譯器無法排除任何根據縮小的多載。</span><span class="sxs-lookup"><span data-stu-id="ae2f6-132">In the second call, the compiler cannot eliminate any of the overloads on the basis of narrowing.</span></span> <span data-ttu-id="ae2f6-133">基於相同理由，如同第一次呼叫中中,，因為它可以呼叫第二個多載，較不需要擴展的引數類型，它會排除第三個多載。</span><span class="sxs-lookup"><span data-stu-id="ae2f6-133">It eliminates the third overload for the same reason as in the first call, because it can call the second overload with less widening of the argument types.</span></span> <span data-ttu-id="ae2f6-134">不過，編譯器無法解析的第一個和第二個多載之間。</span><span class="sxs-lookup"><span data-stu-id="ae2f6-134">However, the compiler cannot resolve between the first and second overloads.</span></span> <span data-ttu-id="ae2f6-135">各有一個定義的參數類型可擴展成其他對應的類型 (`Byte`來`Short`，但`Single`至`Double`)。</span><span class="sxs-lookup"><span data-stu-id="ae2f6-135">Each has one defined parameter type that widens to the corresponding type in the other (`Byte` to `Short`, but `Single` to `Double`).</span></span> <span data-ttu-id="ae2f6-136">因此，編譯器會產生多載解析錯誤。</span><span class="sxs-lookup"><span data-stu-id="ae2f6-136">The compiler therefore generates an overload resolution error.</span></span>  
  
## <a name="overloaded-optional-and-paramarray-arguments"></a><span data-ttu-id="ae2f6-137">選擇性的多載和 ParamArray 引數</span><span class="sxs-lookup"><span data-stu-id="ae2f6-137">Overloaded Optional and ParamArray Arguments</span></span>  
 <span data-ttu-id="ae2f6-138">如果程序的兩個多載具有相同簽章，不同之處在於最後一個參數宣告[選擇性](../../../../visual-basic/language-reference/modifiers/optional.md)其中一並[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)在另一個，編譯器會解析為該程序的呼叫如下所示：</span><span class="sxs-lookup"><span data-stu-id="ae2f6-138">If two overloads of a procedure have identical signatures except that the last parameter is declared [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) in one and [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) in the other, the compiler resolves a call to that procedure as follows:</span></span>  
  
|<span data-ttu-id="ae2f6-139">如果呼叫所提供作為最後一個引數</span><span class="sxs-lookup"><span data-stu-id="ae2f6-139">If the call supplies the last argument as</span></span>|<span data-ttu-id="ae2f6-140">編譯器會解析宣告做為最後一個引數的多載的呼叫</span><span class="sxs-lookup"><span data-stu-id="ae2f6-140">The compiler resolves the call to the overload declaring the last argument as</span></span>|  
|---|---|  
|<span data-ttu-id="ae2f6-141">沒有值 （省略的引數）</span><span class="sxs-lookup"><span data-stu-id="ae2f6-141">No value (argument omitted)</span></span>|`Optional`|  
|<span data-ttu-id="ae2f6-142">單一值</span><span class="sxs-lookup"><span data-stu-id="ae2f6-142">A single value</span></span>|`Optional`|  
|<span data-ttu-id="ae2f6-143">以逗號分隔的清單中的兩個或多個值</span><span class="sxs-lookup"><span data-stu-id="ae2f6-143">Two or more values in a comma-separated list</span></span>|`ParamArray`|  
|<span data-ttu-id="ae2f6-144">（包括空的陣列） 任何長度的陣列</span><span class="sxs-lookup"><span data-stu-id="ae2f6-144">An array of any length (including an empty array)</span></span>|`ParamArray`|  
  
## <a name="see-also"></a><span data-ttu-id="ae2f6-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae2f6-145">See also</span></span>
- [<span data-ttu-id="ae2f6-146">選擇性參數</span><span class="sxs-lookup"><span data-stu-id="ae2f6-146">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="ae2f6-147">參數陣列</span><span class="sxs-lookup"><span data-stu-id="ae2f6-147">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="ae2f6-148">程序多載化</span><span class="sxs-lookup"><span data-stu-id="ae2f6-148">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="ae2f6-149">程序的疑難排解</span><span class="sxs-lookup"><span data-stu-id="ae2f6-149">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="ae2f6-150">如何：定義多個版本的程序</span><span class="sxs-lookup"><span data-stu-id="ae2f6-150">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="ae2f6-151">如何：呼叫多載程序</span><span class="sxs-lookup"><span data-stu-id="ae2f6-151">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="ae2f6-152">如何：多載會採用選擇性參數的程序</span><span class="sxs-lookup"><span data-stu-id="ae2f6-152">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="ae2f6-153">如何：多載不定數目參數的程序</span><span class="sxs-lookup"><span data-stu-id="ae2f6-153">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="ae2f6-154">多載化程序的考慮因素</span><span class="sxs-lookup"><span data-stu-id="ae2f6-154">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="ae2f6-155">多載</span><span class="sxs-lookup"><span data-stu-id="ae2f6-155">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [<span data-ttu-id="ae2f6-156">擴充方法</span><span class="sxs-lookup"><span data-stu-id="ae2f6-156">Extension Methods</span></span>](./extension-methods.md)
