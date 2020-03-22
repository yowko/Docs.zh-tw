---
title: Overload Resolution
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
ms.openlocfilehash: 84d52bbbfb34c2e5d67ed6a1810ab3e32fafda22
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266868"
---
# <a name="overload-resolution-visual-basic"></a><span data-ttu-id="774a7-102">多載解析 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="774a7-102">Overload Resolution (Visual Basic)</span></span>
<span data-ttu-id="774a7-103">當 Visual Basic 編譯器遇到對在多個重載版本中定義的過程的調用時，編譯器必須決定調用的重載。</span><span class="sxs-lookup"><span data-stu-id="774a7-103">When the Visual Basic compiler encounters a call to a procedure that is defined in several overloaded versions, the compiler must decide which of the overloads to call.</span></span> <span data-ttu-id="774a7-104">它通過執行以下步驟來完成此工作：</span><span class="sxs-lookup"><span data-stu-id="774a7-104">It does this by performing the following steps:</span></span>  
  
1. <span data-ttu-id="774a7-105">**協助工具。**</span><span class="sxs-lookup"><span data-stu-id="774a7-105">**Accessibility.**</span></span> <span data-ttu-id="774a7-106">它通過阻止調用代碼調用它的存取層級消除了任何重載。</span><span class="sxs-lookup"><span data-stu-id="774a7-106">It eliminates any overload with an access level that prevents the calling code from calling it.</span></span>  
  
2. <span data-ttu-id="774a7-107">**參數數。**</span><span class="sxs-lookup"><span data-stu-id="774a7-107">**Number of Parameters.**</span></span> <span data-ttu-id="774a7-108">它消除了定義與調用中提供的參數數不同的任何重載。</span><span class="sxs-lookup"><span data-stu-id="774a7-108">It eliminates any overload that defines a different number of parameters than are supplied in the call.</span></span>  
  
3. <span data-ttu-id="774a7-109">**參數資料類型。**</span><span class="sxs-lookup"><span data-stu-id="774a7-109">**Parameter Data Types.**</span></span> <span data-ttu-id="774a7-110">編譯器給予實例方法優先于擴充方法。</span><span class="sxs-lookup"><span data-stu-id="774a7-110">The compiler gives instance methods preference over extension methods.</span></span> <span data-ttu-id="774a7-111">如果發現任何實例方法只需要加寬轉換以匹配程序呼叫，則所有擴充方法都將被刪除，編譯器僅繼續使用實例方法候選項。</span><span class="sxs-lookup"><span data-stu-id="774a7-111">If any instance method is found that requires only widening conversions to match the procedure call, all extension methods are dropped and the compiler continues with only the instance method candidates.</span></span> <span data-ttu-id="774a7-112">如果未找到此類實例方法，則繼續使用實例和擴充方法。</span><span class="sxs-lookup"><span data-stu-id="774a7-112">If no such instance method is found, it continues with both instance and extension methods.</span></span>  
  
     <span data-ttu-id="774a7-113">在此步驟中，它消除了調用參數的資料類型無法轉換為重載中定義的參數類型的任何重載。</span><span class="sxs-lookup"><span data-stu-id="774a7-113">In this step, it eliminates any overload for which the data types of the calling arguments cannot be converted to the parameter types defined in the overload.</span></span>  
  
4. <span data-ttu-id="774a7-114">**縮小轉換。**</span><span class="sxs-lookup"><span data-stu-id="774a7-114">**Narrowing Conversions.**</span></span> <span data-ttu-id="774a7-115">它消除了任何需要從調用參數類型到定義的參數類型進行縮小轉換的重載。</span><span class="sxs-lookup"><span data-stu-id="774a7-115">It eliminates any overload that requires a narrowing conversion from the calling argument types to the defined parameter types.</span></span> <span data-ttu-id="774a7-116">無論類型檢查開關（[選項嚴格語句](../../../../visual-basic/language-reference/statements/option-strict-statement.md)）是`On`還是`Off`，都是如此。</span><span class="sxs-lookup"><span data-stu-id="774a7-116">This is true whether the type checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) is `On` or `Off`.</span></span>  
  
5. <span data-ttu-id="774a7-117">**最小加寬。**</span><span class="sxs-lookup"><span data-stu-id="774a7-117">**Least Widening.**</span></span> <span data-ttu-id="774a7-118">編譯器將剩餘的重載成對。</span><span class="sxs-lookup"><span data-stu-id="774a7-118">The compiler considers the remaining overloads in pairs.</span></span> <span data-ttu-id="774a7-119">對於每對，它比較已定義參數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="774a7-119">For each pair, it compares the data types of the defined parameters.</span></span> <span data-ttu-id="774a7-120">如果其中一個重載中的類型都擴展到另一個重載中的相應類型，編譯器將消除後者。</span><span class="sxs-lookup"><span data-stu-id="774a7-120">If the types in one of the overloads all widen to the corresponding types in the other, the compiler eliminates the latter.</span></span> <span data-ttu-id="774a7-121">也就是說，它保留需要最少加寬量的重載。</span><span class="sxs-lookup"><span data-stu-id="774a7-121">That is, it retains the overload that requires the least amount of widening.</span></span>  
  
6. <span data-ttu-id="774a7-122">**單位候選人。**</span><span class="sxs-lookup"><span data-stu-id="774a7-122">**Single Candidate.**</span></span> <span data-ttu-id="774a7-123">它繼續考慮成對的重載，直到只剩下一個重載，並且它解決了對該重載的調用。</span><span class="sxs-lookup"><span data-stu-id="774a7-123">It continues considering overloads in pairs until only one overload remains, and it resolves the call to that overload.</span></span> <span data-ttu-id="774a7-124">如果編譯器無法將重載減少到單個候選項，則會建置錯誤。</span><span class="sxs-lookup"><span data-stu-id="774a7-124">If the compiler cannot reduce the overloads to a single candidate, it generates an error.</span></span>  
  
 <span data-ttu-id="774a7-125">下圖顯示了確定要調用的一組重載版本中哪個的過程。</span><span class="sxs-lookup"><span data-stu-id="774a7-125">The following illustration shows the process that determines which of a set of overloaded versions to call.</span></span>  
  
 <span data-ttu-id="774a7-126">![多載解析程序流程圖](./media/overload-resolution/determine-overloaded-version.gif "在重載版本之間解決")</span><span class="sxs-lookup"><span data-stu-id="774a7-126">![Flow diagram of overload resolution process](./media/overload-resolution/determine-overloaded-version.gif "Resolving among overloaded versions")</span></span>
  
 <span data-ttu-id="774a7-127">下面的示例說明了此重載解決過程。</span><span class="sxs-lookup"><span data-stu-id="774a7-127">The following example illustrates this overload resolution process.</span></span>  
  
 [!code-vb[VbVbcnProcedures#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbcnProcedures#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#63)]  
  
 <span data-ttu-id="774a7-128">在第一個調用中，編譯器消除了第一個重載，因為第一個參數`Short`（ ） 的類型縮小到相應參數 （`Byte`的類型）。</span><span class="sxs-lookup"><span data-stu-id="774a7-128">In the first call, the compiler eliminates the first overload because the type of the first argument (`Short`) narrows to the type of the corresponding parameter (`Byte`).</span></span> <span data-ttu-id="774a7-129">然後，它消除了第三個重載，因為第二個重載`Short` `Single`（和 ） 中的每個參數類型在第三個重`Integer`載`Single`（和 ） 中擴展到相應的類型。</span><span class="sxs-lookup"><span data-stu-id="774a7-129">It then eliminates the third overload because each argument type in the second overload (`Short` and `Single`) widens to the corresponding type in the third overload (`Integer` and `Single`).</span></span> <span data-ttu-id="774a7-130">第二個重載需要較少的擴展，因此編譯器使用它進行調用。</span><span class="sxs-lookup"><span data-stu-id="774a7-130">The second overload requires less widening, so the compiler uses it for the call.</span></span>  
  
 <span data-ttu-id="774a7-131">在第二個調用中，編譯器不能在縮小的基礎上消除任何重載。</span><span class="sxs-lookup"><span data-stu-id="774a7-131">In the second call, the compiler cannot eliminate any of the overloads on the basis of narrowing.</span></span> <span data-ttu-id="774a7-132">它消除了第三個重載的原因與第一個調用相同，因為它可以調用第二個重載，而參數類型的擴展更少。</span><span class="sxs-lookup"><span data-stu-id="774a7-132">It eliminates the third overload for the same reason as in the first call, because it can call the second overload with less widening of the argument types.</span></span> <span data-ttu-id="774a7-133">但是，編譯器無法在第一個重載和第二個重載之間解析。</span><span class="sxs-lookup"><span data-stu-id="774a7-133">However, the compiler cannot resolve between the first and second overloads.</span></span> <span data-ttu-id="774a7-134">每個參數類型都有一個已定義的參數類型，該參數類型將擴展到另`Byte`一`Short`個類型`Single`（`Double`到 ，但為 ）</span><span class="sxs-lookup"><span data-stu-id="774a7-134">Each has one defined parameter type that widens to the corresponding type in the other (`Byte` to `Short`, but `Single` to `Double`).</span></span> <span data-ttu-id="774a7-135">因此，編譯器生成重載解析錯誤。</span><span class="sxs-lookup"><span data-stu-id="774a7-135">The compiler therefore generates an overload resolution error.</span></span>  
  
## <a name="overloaded-optional-and-paramarray-arguments"></a><span data-ttu-id="774a7-136">重載可選參數和參數參數</span><span class="sxs-lookup"><span data-stu-id="774a7-136">Overloaded Optional and ParamArray Arguments</span></span>  
 <span data-ttu-id="774a7-137">如果過程的兩個重載具有相同的簽名，但最後一個參數在一個參數中聲明[為可選](../../../../visual-basic/language-reference/modifiers/optional.md)，另一個參數為[ParamArray，](../../../../visual-basic/language-reference/modifiers/paramarray.md)則編譯器將按如下方式解析對該過程的調用：</span><span class="sxs-lookup"><span data-stu-id="774a7-137">If two overloads of a procedure have identical signatures except that the last parameter is declared [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) in one and [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) in the other, the compiler resolves a call to that procedure as follows:</span></span>  
  
|<span data-ttu-id="774a7-138">如果調用提供最後一個參數為</span><span class="sxs-lookup"><span data-stu-id="774a7-138">If the call supplies the last argument as</span></span>|<span data-ttu-id="774a7-139">編譯器解析對重載的調用，將最後一個參數聲明為</span><span class="sxs-lookup"><span data-stu-id="774a7-139">The compiler resolves the call to the overload declaring the last argument as</span></span>|  
|---|---|  
|<span data-ttu-id="774a7-140">無值（省略參數）</span><span class="sxs-lookup"><span data-stu-id="774a7-140">No value (argument omitted)</span></span>|`Optional`|  
|<span data-ttu-id="774a7-141">單個值</span><span class="sxs-lookup"><span data-stu-id="774a7-141">A single value</span></span>|`Optional`|  
|<span data-ttu-id="774a7-142">逗號分隔清單中的兩個或多個值</span><span class="sxs-lookup"><span data-stu-id="774a7-142">Two or more values in a comma-separated list</span></span>|`ParamArray`|  
|<span data-ttu-id="774a7-143">任何長度的陣列（包括空陣列）</span><span class="sxs-lookup"><span data-stu-id="774a7-143">An array of any length (including an empty array)</span></span>|`ParamArray`|  
  
## <a name="see-also"></a><span data-ttu-id="774a7-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="774a7-144">See also</span></span>

- [<span data-ttu-id="774a7-145">可選參數</span><span class="sxs-lookup"><span data-stu-id="774a7-145">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="774a7-146">參數陣列</span><span class="sxs-lookup"><span data-stu-id="774a7-146">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="774a7-147">程序多載化</span><span class="sxs-lookup"><span data-stu-id="774a7-147">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="774a7-148">程序的疑難排解</span><span class="sxs-lookup"><span data-stu-id="774a7-148">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="774a7-149">如何：定義程序的多個版本</span><span class="sxs-lookup"><span data-stu-id="774a7-149">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="774a7-150">如何：呼叫多載程序</span><span class="sxs-lookup"><span data-stu-id="774a7-150">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="774a7-151">如何：使用選擇性參數的多載程序</span><span class="sxs-lookup"><span data-stu-id="774a7-151">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="774a7-152">如何：多載使用不確定參數數目的程序</span><span class="sxs-lookup"><span data-stu-id="774a7-152">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="774a7-153">多載化程序的考慮因素</span><span class="sxs-lookup"><span data-stu-id="774a7-153">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="774a7-154">重載</span><span class="sxs-lookup"><span data-stu-id="774a7-154">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [<span data-ttu-id="774a7-155">擴充方法</span><span class="sxs-lookup"><span data-stu-id="774a7-155">Extension Methods</span></span>](./extension-methods.md)
