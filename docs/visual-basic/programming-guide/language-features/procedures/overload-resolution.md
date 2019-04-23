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
ms.openlocfilehash: 4f81c7377423899c142c4270f325bbd7ed20b877
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59312237"
---
# <a name="overload-resolution-visual-basic"></a><span data-ttu-id="4f445-102">多載解析 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f445-102">Overload Resolution (Visual Basic)</span></span>
<span data-ttu-id="4f445-103">當 Visual Basic 編譯器遇到定義在數個多載版本的程序的呼叫時，編譯器必須決定要呼叫的多載。</span><span class="sxs-lookup"><span data-stu-id="4f445-103">When the Visual Basic compiler encounters a call to a procedure that is defined in several overloaded versions, the compiler must decide which of the overloads to call.</span></span> <span data-ttu-id="4f445-104">它會執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="4f445-104">It does this by performing the following steps:</span></span>  
  
1. <span data-ttu-id="4f445-105">**協助工具。**</span><span class="sxs-lookup"><span data-stu-id="4f445-105">**Accessibility.**</span></span> <span data-ttu-id="4f445-106">它會排除任何多載，以防止呼叫程式碼呼叫它的存取層級。</span><span class="sxs-lookup"><span data-stu-id="4f445-106">It eliminates any overload with an access level that prevents the calling code from calling it.</span></span>  
  
2. <span data-ttu-id="4f445-107">**參數的數目。**</span><span class="sxs-lookup"><span data-stu-id="4f445-107">**Number of Parameters.**</span></span> <span data-ttu-id="4f445-108">它會排除任何在呼叫中定義不同數目的參數所提供的多載。</span><span class="sxs-lookup"><span data-stu-id="4f445-108">It eliminates any overload that defines a different number of parameters than are supplied in the call.</span></span>  
  
3. <span data-ttu-id="4f445-109">**參數資料類型。**</span><span class="sxs-lookup"><span data-stu-id="4f445-109">**Parameter Data Types.**</span></span> <span data-ttu-id="4f445-110">編譯器會提供於延伸方法的執行個體方法的喜好設定。</span><span class="sxs-lookup"><span data-stu-id="4f445-110">The compiler gives instance methods preference over extension methods.</span></span> <span data-ttu-id="4f445-111">如果找不到需要僅限於擴展轉換，來比對程序呼叫的任何執行個體方法，會卸除所有擴充方法，編譯器會繼續進行 僅執行個體方法候選對象。</span><span class="sxs-lookup"><span data-stu-id="4f445-111">If any instance method is found that requires only widening conversions to match the procedure call, all extension methods are dropped and the compiler continues with only the instance method candidates.</span></span> <span data-ttu-id="4f445-112">如果找不到任何這類執行個體方法，它會繼續與執行個體和擴充方法。</span><span class="sxs-lookup"><span data-stu-id="4f445-112">If no such instance method is found, it continues with both instance and extension methods.</span></span>  
  
     <span data-ttu-id="4f445-113">在此步驟中，它會排除任何多載的呼叫的引數的資料類型無法轉換至多載中定義的參數類型。</span><span class="sxs-lookup"><span data-stu-id="4f445-113">In this step, it eliminates any overload for which the data types of the calling arguments cannot be converted to the parameter types defined in the overload.</span></span>  
  
4. <span data-ttu-id="4f445-114">**縮小轉換。**</span><span class="sxs-lookup"><span data-stu-id="4f445-114">**Narrowing Conversions.**</span></span> <span data-ttu-id="4f445-115">它會排除任何多載，必須呼叫的引數型別定義的參數類型是縮小轉換。</span><span class="sxs-lookup"><span data-stu-id="4f445-115">It eliminates any overload that requires a narrowing conversion from the calling argument types to the defined parameter types.</span></span> <span data-ttu-id="4f445-116">這是 true 不論類型檢查參數 ([Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) 是`On`或`Off`。</span><span class="sxs-lookup"><span data-stu-id="4f445-116">This is true whether the type checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) is `On` or `Off`.</span></span>  
  
5. <span data-ttu-id="4f445-117">**最小的擴展。**</span><span class="sxs-lookup"><span data-stu-id="4f445-117">**Least Widening.**</span></span> <span data-ttu-id="4f445-118">編譯器會考慮在配對中剩餘的多載。</span><span class="sxs-lookup"><span data-stu-id="4f445-118">The compiler considers the remaining overloads in pairs.</span></span> <span data-ttu-id="4f445-119">針對每一組，它會比較定義之參數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="4f445-119">For each pair, it compares the data types of the defined parameters.</span></span> <span data-ttu-id="4f445-120">如果中其中一個所有多載的型別會擴展為其他對應的型別，則編譯器會排除後者。</span><span class="sxs-lookup"><span data-stu-id="4f445-120">If the types in one of the overloads all widen to the corresponding types in the other, the compiler eliminates the latter.</span></span> <span data-ttu-id="4f445-121">也就是說，它會保留需要最少擴展的多載。</span><span class="sxs-lookup"><span data-stu-id="4f445-121">That is, it retains the overload that requires the least amount of widening.</span></span>  
  
6. <span data-ttu-id="4f445-122">**單一的候選項目。**</span><span class="sxs-lookup"><span data-stu-id="4f445-122">**Single Candidate.**</span></span> <span data-ttu-id="4f445-123">它會繼續考量之前只有一個配對中的多載多載會保留，且能解決該多載的呼叫。</span><span class="sxs-lookup"><span data-stu-id="4f445-123">It continues considering overloads in pairs until only one overload remains, and it resolves the call to that overload.</span></span> <span data-ttu-id="4f445-124">如果編譯器無法減少為單一的候選者的多載，它會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="4f445-124">If the compiler cannot reduce the overloads to a single candidate, it generates an error.</span></span>  
  
 <span data-ttu-id="4f445-125">下圖顯示決定哪一個多載版本，以呼叫一組程序。</span><span class="sxs-lookup"><span data-stu-id="4f445-125">The following illustration shows the process that determines which of a set of overloaded versions to call.</span></span>  
  
 <span data-ttu-id="4f445-126">![多載解析程序流程圖](./media/overload-resolution/determine-overloaded-version.gif "解析多載的版本")</span><span class="sxs-lookup"><span data-stu-id="4f445-126">![Flow diagram of overload resolution process](./media/overload-resolution/determine-overloaded-version.gif "Resolving among overloaded versions")</span></span>    
  
 <span data-ttu-id="4f445-127">下列範例說明此多載解析程序。</span><span class="sxs-lookup"><span data-stu-id="4f445-127">The following example illustrates this overload resolution process.</span></span>  
  
 [!code-vb[VbVbcnProcedures#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbcnProcedures#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#63)]  
  
 <span data-ttu-id="4f445-128">在第一個呼叫中，編譯器會排除第一個多載因為第一個引數的類型 (`Short`) 的範圍縮小，對應參數的型別 (`Byte`)。</span><span class="sxs-lookup"><span data-stu-id="4f445-128">In the first call, the compiler eliminates the first overload because the type of the first argument (`Short`) narrows to the type of the corresponding parameter (`Byte`).</span></span> <span data-ttu-id="4f445-129">它然後排除第三個多載，因為每個引數類型中的第二個多載 (`Short`並`Single`) 可擴展為對應的型別中的第三個多載 (`Integer`和`Single`)。</span><span class="sxs-lookup"><span data-stu-id="4f445-129">It then eliminates the third overload because each argument type in the second overload (`Short` and `Single`) widens to the corresponding type in the third overload (`Integer` and `Single`).</span></span> <span data-ttu-id="4f445-130">第二個多載都需要較少的擴展，因此編譯器會將它用於呼叫。</span><span class="sxs-lookup"><span data-stu-id="4f445-130">The second overload requires less widening, so the compiler uses it for the call.</span></span>  
  
 <span data-ttu-id="4f445-131">在第二個呼叫中，編譯器無法排除任何根據縮小的多載。</span><span class="sxs-lookup"><span data-stu-id="4f445-131">In the second call, the compiler cannot eliminate any of the overloads on the basis of narrowing.</span></span> <span data-ttu-id="4f445-132">基於相同理由，如同第一次呼叫中中,，因為它可以呼叫第二個多載，較不需要擴展的引數類型，它會排除第三個多載。</span><span class="sxs-lookup"><span data-stu-id="4f445-132">It eliminates the third overload for the same reason as in the first call, because it can call the second overload with less widening of the argument types.</span></span> <span data-ttu-id="4f445-133">不過，編譯器無法解析的第一個和第二個多載之間。</span><span class="sxs-lookup"><span data-stu-id="4f445-133">However, the compiler cannot resolve between the first and second overloads.</span></span> <span data-ttu-id="4f445-134">各有一個定義的參數類型可擴展成其他對應的類型 (`Byte`來`Short`，但`Single`至`Double`)。</span><span class="sxs-lookup"><span data-stu-id="4f445-134">Each has one defined parameter type that widens to the corresponding type in the other (`Byte` to `Short`, but `Single` to `Double`).</span></span> <span data-ttu-id="4f445-135">因此，編譯器會產生多載解析錯誤。</span><span class="sxs-lookup"><span data-stu-id="4f445-135">The compiler therefore generates an overload resolution error.</span></span>  
  
## <a name="overloaded-optional-and-paramarray-arguments"></a><span data-ttu-id="4f445-136">選擇性的多載和 ParamArray 引數</span><span class="sxs-lookup"><span data-stu-id="4f445-136">Overloaded Optional and ParamArray Arguments</span></span>  
 <span data-ttu-id="4f445-137">如果程序的兩個多載具有相同簽章，不同之處在於最後一個參數宣告[選擇性](../../../../visual-basic/language-reference/modifiers/optional.md)其中一並[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)在另一個，編譯器會解析為該程序的呼叫如下所示：</span><span class="sxs-lookup"><span data-stu-id="4f445-137">If two overloads of a procedure have identical signatures except that the last parameter is declared [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) in one and [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) in the other, the compiler resolves a call to that procedure as follows:</span></span>  
  
|<span data-ttu-id="4f445-138">如果呼叫所提供作為最後一個引數</span><span class="sxs-lookup"><span data-stu-id="4f445-138">If the call supplies the last argument as</span></span>|<span data-ttu-id="4f445-139">編譯器會解析宣告做為最後一個引數的多載的呼叫</span><span class="sxs-lookup"><span data-stu-id="4f445-139">The compiler resolves the call to the overload declaring the last argument as</span></span>|  
|---|---|  
|<span data-ttu-id="4f445-140">沒有值 （省略的引數）</span><span class="sxs-lookup"><span data-stu-id="4f445-140">No value (argument omitted)</span></span>|`Optional`|  
|<span data-ttu-id="4f445-141">單一值</span><span class="sxs-lookup"><span data-stu-id="4f445-141">A single value</span></span>|`Optional`|  
|<span data-ttu-id="4f445-142">以逗號分隔的清單中的兩個或多個值</span><span class="sxs-lookup"><span data-stu-id="4f445-142">Two or more values in a comma-separated list</span></span>|`ParamArray`|  
|<span data-ttu-id="4f445-143">（包括空的陣列） 任何長度的陣列</span><span class="sxs-lookup"><span data-stu-id="4f445-143">An array of any length (including an empty array)</span></span>|`ParamArray`|  
  
## <a name="see-also"></a><span data-ttu-id="4f445-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f445-144">See also</span></span>

- [<span data-ttu-id="4f445-145">選擇性參數</span><span class="sxs-lookup"><span data-stu-id="4f445-145">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="4f445-146">參數陣列</span><span class="sxs-lookup"><span data-stu-id="4f445-146">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="4f445-147">程序多載化</span><span class="sxs-lookup"><span data-stu-id="4f445-147">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="4f445-148">程序的疑難排解</span><span class="sxs-lookup"><span data-stu-id="4f445-148">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="4f445-149">如何：定義多個版本的程序</span><span class="sxs-lookup"><span data-stu-id="4f445-149">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="4f445-150">如何：呼叫多載程序</span><span class="sxs-lookup"><span data-stu-id="4f445-150">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="4f445-151">如何：多載會採用選擇性參數的程序</span><span class="sxs-lookup"><span data-stu-id="4f445-151">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="4f445-152">如何：多載不定數目參數的程序</span><span class="sxs-lookup"><span data-stu-id="4f445-152">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="4f445-153">多載化程序的考慮因素</span><span class="sxs-lookup"><span data-stu-id="4f445-153">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="4f445-154">多載</span><span class="sxs-lookup"><span data-stu-id="4f445-154">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [<span data-ttu-id="4f445-155">擴充方法</span><span class="sxs-lookup"><span data-stu-id="4f445-155">Extension Methods</span></span>](./extension-methods.md)
