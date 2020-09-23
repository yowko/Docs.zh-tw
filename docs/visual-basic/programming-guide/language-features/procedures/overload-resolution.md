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
ms.openlocfilehash: 9b83eba8efc8dfe14b6ec1cbab270984977198e5
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071360"
---
# <a name="overload-resolution-visual-basic"></a><span data-ttu-id="553dc-102">多載解析 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="553dc-102">Overload Resolution (Visual Basic)</span></span>

<span data-ttu-id="553dc-103">當 Visual Basic 編譯器遇到數個多載版本中定義的程式呼叫時，編譯器必須決定要呼叫的多載。</span><span class="sxs-lookup"><span data-stu-id="553dc-103">When the Visual Basic compiler encounters a call to a procedure that is defined in several overloaded versions, the compiler must decide which of the overloads to call.</span></span> <span data-ttu-id="553dc-104">它會執行下列步驟來執行此動作：</span><span class="sxs-lookup"><span data-stu-id="553dc-104">It does this by performing the following steps:</span></span>  
  
1. <span data-ttu-id="553dc-105">**協助工具。**</span><span class="sxs-lookup"><span data-stu-id="553dc-105">**Accessibility.**</span></span> <span data-ttu-id="553dc-106">它會消除具有存取層級的任何多載，以防止呼叫程式碼呼叫它。</span><span class="sxs-lookup"><span data-stu-id="553dc-106">It eliminates any overload with an access level that prevents the calling code from calling it.</span></span>  
  
2. <span data-ttu-id="553dc-107">**參數的數目。**</span><span class="sxs-lookup"><span data-stu-id="553dc-107">**Number of Parameters.**</span></span> <span data-ttu-id="553dc-108">它會排除定義與呼叫中所提供之參數數目不同的任何多載。</span><span class="sxs-lookup"><span data-stu-id="553dc-108">It eliminates any overload that defines a different number of parameters than are supplied in the call.</span></span>  
  
3. <span data-ttu-id="553dc-109">**參數資料類型。**</span><span class="sxs-lookup"><span data-stu-id="553dc-109">**Parameter Data Types.**</span></span> <span data-ttu-id="553dc-110">編譯器會針對擴充方法提供實例方法喜好設定。</span><span class="sxs-lookup"><span data-stu-id="553dc-110">The compiler gives instance methods preference over extension methods.</span></span> <span data-ttu-id="553dc-111">如果找到的任何實例方法只需要擴輾轉換來符合程序呼叫，則會卸載所有的擴充方法，而且編譯器只會以實例方法候選項目繼續。</span><span class="sxs-lookup"><span data-stu-id="553dc-111">If any instance method is found that requires only widening conversions to match the procedure call, all extension methods are dropped and the compiler continues with only the instance method candidates.</span></span> <span data-ttu-id="553dc-112">如果找不到這類實例方法，它會繼續執行實例和擴充方法。</span><span class="sxs-lookup"><span data-stu-id="553dc-112">If no such instance method is found, it continues with both instance and extension methods.</span></span>  
  
     <span data-ttu-id="553dc-113">在這個步驟中，它會排除呼叫引數的資料類型無法轉換成多載中所定義之參數類型的任何多載。</span><span class="sxs-lookup"><span data-stu-id="553dc-113">In this step, it eliminates any overload for which the data types of the calling arguments cannot be converted to the parameter types defined in the overload.</span></span>  
  
4. <span data-ttu-id="553dc-114">**縮小轉換。**</span><span class="sxs-lookup"><span data-stu-id="553dc-114">**Narrowing Conversions.**</span></span> <span data-ttu-id="553dc-115">它會消除任何需要從呼叫引數型別轉換成已定義參數類型的多載。</span><span class="sxs-lookup"><span data-stu-id="553dc-115">It eliminates any overload that requires a narrowing conversion from the calling argument types to the defined parameter types.</span></span> <span data-ttu-id="553dc-116">不論類型檢查參數 ([Option Strict 語句](../../../language-reference/statements/option-strict-statement.md)) 是或，都是 `On` 如此 `Off` 。</span><span class="sxs-lookup"><span data-stu-id="553dc-116">This is true whether the type checking switch ([Option Strict Statement](../../../language-reference/statements/option-strict-statement.md)) is `On` or `Off`.</span></span>  
  
5. <span data-ttu-id="553dc-117">**最小擴展。**</span><span class="sxs-lookup"><span data-stu-id="553dc-117">**Least Widening.**</span></span> <span data-ttu-id="553dc-118">編譯器會考慮成對的其餘多載。</span><span class="sxs-lookup"><span data-stu-id="553dc-118">The compiler considers the remaining overloads in pairs.</span></span> <span data-ttu-id="553dc-119">它會針對每個配對，比較所定義參數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="553dc-119">For each pair, it compares the data types of the defined parameters.</span></span> <span data-ttu-id="553dc-120">如果其中一個多載中的型別全部擴展至另一個多載中的對應類型，則編譯器會排除後者。</span><span class="sxs-lookup"><span data-stu-id="553dc-120">If the types in one of the overloads all widen to the corresponding types in the other, the compiler eliminates the latter.</span></span> <span data-ttu-id="553dc-121">也就是說，它會保留需要最少量擴展的多載。</span><span class="sxs-lookup"><span data-stu-id="553dc-121">That is, it retains the overload that requires the least amount of widening.</span></span>  
  
6. <span data-ttu-id="553dc-122">**單一候選。**</span><span class="sxs-lookup"><span data-stu-id="553dc-122">**Single Candidate.**</span></span> <span data-ttu-id="553dc-123">它會繼續考慮成對的多載，直到只剩下一個多載，並解析對該多載的呼叫。</span><span class="sxs-lookup"><span data-stu-id="553dc-123">It continues considering overloads in pairs until only one overload remains, and it resolves the call to that overload.</span></span> <span data-ttu-id="553dc-124">如果編譯器無法將多載縮減為單一候選項，則會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="553dc-124">If the compiler cannot reduce the overloads to a single candidate, it generates an error.</span></span>  
  
 <span data-ttu-id="553dc-125">下圖顯示的程式會判斷要呼叫的一組多載版本。</span><span class="sxs-lookup"><span data-stu-id="553dc-125">The following illustration shows the process that determines which of a set of overloaded versions to call.</span></span>  
  
 <span data-ttu-id="553dc-126">![多載解析程序流程圖](./media/overload-resolution/determine-overloaded-version.gif "在多載版本之間解析")</span><span class="sxs-lookup"><span data-stu-id="553dc-126">![Flow diagram of overload resolution process](./media/overload-resolution/determine-overloaded-version.gif "Resolving among overloaded versions")</span></span>
  
 <span data-ttu-id="553dc-127">下列範例說明此多載解析程式。</span><span class="sxs-lookup"><span data-stu-id="553dc-127">The following example illustrates this overload resolution process.</span></span>  
  
 [!code-vb[VbVbcnProcedures#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbcnProcedures#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#63)]  
  
 <span data-ttu-id="553dc-128">在第一個呼叫中，編譯器會排除第一個多載，因為第一個引數 (的類型 `Short`) 會縮小為對應參數 (`Byte`) 的類型。</span><span class="sxs-lookup"><span data-stu-id="553dc-128">In the first call, the compiler eliminates the first overload because the type of the first argument (`Short`) narrows to the type of the corresponding parameter (`Byte`).</span></span> <span data-ttu-id="553dc-129">然後，它會消除第三個多載，因為第二個多載中的每個引數類型 (`Short` ，且 `Single`) 擴大為第三個多載 (`Integer` 和) 中的對應類型 `Single`</span><span class="sxs-lookup"><span data-stu-id="553dc-129">It then eliminates the third overload because each argument type in the second overload (`Short` and `Single`) widens to the corresponding type in the third overload (`Integer` and `Single`).</span></span> <span data-ttu-id="553dc-130">第二個多載需要較少的擴展，因此編譯器會使用它來進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="553dc-130">The second overload requires less widening, so the compiler uses it for the call.</span></span>  
  
 <span data-ttu-id="553dc-131">在第二個呼叫中，編譯器無法在縮小的基礎上消除任何多載。</span><span class="sxs-lookup"><span data-stu-id="553dc-131">In the second call, the compiler cannot eliminate any of the overloads on the basis of narrowing.</span></span> <span data-ttu-id="553dc-132">它會將第三個多載排除在第一個呼叫中的相同原因，因為它可以使用較少的引數類型擴展來呼叫第二個多載。</span><span class="sxs-lookup"><span data-stu-id="553dc-132">It eliminates the third overload for the same reason as in the first call, because it can call the second overload with less widening of the argument types.</span></span> <span data-ttu-id="553dc-133">不過，編譯器無法在第一個和第二個多載之間解析。</span><span class="sxs-lookup"><span data-stu-id="553dc-133">However, the compiler cannot resolve between the first and second overloads.</span></span> <span data-ttu-id="553dc-134">每個都有一個定義的參數類型，可擴大至其他 (中的對應類型 `Byte` `Short` ，但 `Single` `Double`) 。</span><span class="sxs-lookup"><span data-stu-id="553dc-134">Each has one defined parameter type that widens to the corresponding type in the other (`Byte` to `Short`, but `Single` to `Double`).</span></span> <span data-ttu-id="553dc-135">因此，編譯器會產生多載解析錯誤。</span><span class="sxs-lookup"><span data-stu-id="553dc-135">The compiler therefore generates an overload resolution error.</span></span>  
  
## <a name="overloaded-optional-and-paramarray-arguments"></a><span data-ttu-id="553dc-136">多載的選擇性和 ParamArray 引數</span><span class="sxs-lookup"><span data-stu-id="553dc-136">Overloaded Optional and ParamArray Arguments</span></span>  

 <span data-ttu-id="553dc-137">如果程式的兩個多載具有相同的簽章，但最後一個參數是在另一個[參數中宣告](../../../language-reference/modifiers/paramarray.md)為[選擇性](../../../language-reference/modifiers/optional.md)，則編譯器會解析該程式的呼叫，如下所示：</span><span class="sxs-lookup"><span data-stu-id="553dc-137">If two overloads of a procedure have identical signatures except that the last parameter is declared [Optional](../../../language-reference/modifiers/optional.md) in one and [ParamArray](../../../language-reference/modifiers/paramarray.md) in the other, the compiler resolves a call to that procedure as follows:</span></span>  
  
|<span data-ttu-id="553dc-138">如果呼叫將最後一個引數提供為</span><span class="sxs-lookup"><span data-stu-id="553dc-138">If the call supplies the last argument as</span></span>|<span data-ttu-id="553dc-139">編譯器會將宣告最後一個引數的多載呼叫解析為</span><span class="sxs-lookup"><span data-stu-id="553dc-139">The compiler resolves the call to the overload declaring the last argument as</span></span>|  
|---|---|  
|<span data-ttu-id="553dc-140">未省略值 (引數) </span><span class="sxs-lookup"><span data-stu-id="553dc-140">No value (argument omitted)</span></span>|`Optional`|  
|<span data-ttu-id="553dc-141">單一值</span><span class="sxs-lookup"><span data-stu-id="553dc-141">A single value</span></span>|`Optional`|  
|<span data-ttu-id="553dc-142">逗點分隔清單中的兩個或多個值</span><span class="sxs-lookup"><span data-stu-id="553dc-142">Two or more values in a comma-separated list</span></span>|`ParamArray`|  
|<span data-ttu-id="553dc-143">任何長度的陣列 (包括空陣列) </span><span class="sxs-lookup"><span data-stu-id="553dc-143">An array of any length (including an empty array)</span></span>|`ParamArray`|  
  
## <a name="see-also"></a><span data-ttu-id="553dc-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="553dc-144">See also</span></span>

- [<span data-ttu-id="553dc-145">選擇性參數</span><span class="sxs-lookup"><span data-stu-id="553dc-145">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="553dc-146">參數陣列</span><span class="sxs-lookup"><span data-stu-id="553dc-146">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="553dc-147">程序多載化</span><span class="sxs-lookup"><span data-stu-id="553dc-147">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="553dc-148">程序的疑難排解</span><span class="sxs-lookup"><span data-stu-id="553dc-148">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="553dc-149">如何：定義程序的多個版本</span><span class="sxs-lookup"><span data-stu-id="553dc-149">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="553dc-150">如何：呼叫多載程序</span><span class="sxs-lookup"><span data-stu-id="553dc-150">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="553dc-151">如何：使用選擇性參數的多載程序</span><span class="sxs-lookup"><span data-stu-id="553dc-151">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="553dc-152">如何：多載使用不確定參數數目的程序</span><span class="sxs-lookup"><span data-stu-id="553dc-152">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="553dc-153">多載化程序的考慮因素</span><span class="sxs-lookup"><span data-stu-id="553dc-153">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="553dc-154">多載</span><span class="sxs-lookup"><span data-stu-id="553dc-154">Overloads</span></span>](../../../language-reference/modifiers/overloads.md)
- [<span data-ttu-id="553dc-155">擴充方法</span><span class="sxs-lookup"><span data-stu-id="553dc-155">Extension Methods</span></span>](./extension-methods.md)
