---
title: "在 Visual Basic 中的存留期 |Microsoft 文件"
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
- static variables, lifetime
- static variables, Visual Basic
- declared elements, lifetime
- Shared variable lifetime
- lifetime, declared elements
- lifetime, Visual Basic
- lifetime
ms.assetid: bd91e390-690a-469a-9946-8dca70bc14e7
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
ms.openlocfilehash: 4e183d1fa36c967facbb81ebd6917a8fb75d48cd
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="lifetime-in-visual-basic"></a><span data-ttu-id="c4713-102">Visual Basic 中的存留期</span><span class="sxs-lookup"><span data-stu-id="c4713-102">Lifetime in Visual Basic</span></span>
<span data-ttu-id="c4713-103">*存留期*的宣告項目是一段時間期間它是可供使用。</span><span class="sxs-lookup"><span data-stu-id="c4713-103">The *lifetime* of a declared element is the period of time during which it is available for use.</span></span> <span data-ttu-id="c4713-104">變數是唯一的項目存留期。</span><span class="sxs-lookup"><span data-stu-id="c4713-104">Variables are the only elements that have lifetime.</span></span> <span data-ttu-id="c4713-105">基於此目的，編譯器會將程序參數和函式會傳回做為變數的特殊案例。</span><span class="sxs-lookup"><span data-stu-id="c4713-105">For this purpose, the compiler treats procedure parameters and function returns as special cases of variables.</span></span> <span data-ttu-id="c4713-106">變數的存留期代表一段時間期間，它可以保存的值。</span><span class="sxs-lookup"><span data-stu-id="c4713-106">The lifetime of a variable represents the period of time during which it can hold a value.</span></span> <span data-ttu-id="c4713-107">其值會隨著其存留期，而改變，但它永遠會保留某些值。</span><span class="sxs-lookup"><span data-stu-id="c4713-107">Its value can change over its lifetime, but it always holds some value.</span></span>  
  
## <a name="different-lifetimes"></a><span data-ttu-id="c4713-108">不同的存留期</span><span class="sxs-lookup"><span data-stu-id="c4713-108">Different Lifetimes</span></span>  
 <span data-ttu-id="c4713-109">A*成員變數*（在模組層級以外的任何程序宣告） 通常會有相同的存留期宣告它的項目。</span><span class="sxs-lookup"><span data-stu-id="c4713-109">A *member variable* (declared at module level, outside any procedure) typically has the same lifetime as the element in which it is declared.</span></span> <span data-ttu-id="c4713-110">類別或結構中宣告的非共用的變數存在以不同的類別或結構宣告它的每個執行個體的複本。</span><span class="sxs-lookup"><span data-stu-id="c4713-110">A nonshared variable declared in a class or structure exists as a separate copy for each instance of the class or structure in which it is declared.</span></span> <span data-ttu-id="c4713-111">每個這類變數具有相同的存留期與其執行個體。</span><span class="sxs-lookup"><span data-stu-id="c4713-111">Each such variable has the same lifetime as its instance.</span></span> <span data-ttu-id="c4713-112">不過，`Shared`變數具有只有單一存留期，可執行應用程式的整個期間持續的時間。</span><span class="sxs-lookup"><span data-stu-id="c4713-112">However, a `Shared` variable has only a single lifetime, which lasts for the entire time your application is running.</span></span>  
  
 <span data-ttu-id="c4713-113">A*區域變數*（程序內宣告） 宣告它的程序正在執行時才存在。</span><span class="sxs-lookup"><span data-stu-id="c4713-113">A *local variable* (declared inside a procedure) exists only while the procedure in which it is declared is running.</span></span> <span data-ttu-id="c4713-114">這也適用於該程序參數與傳回的任何函式。</span><span class="sxs-lookup"><span data-stu-id="c4713-114">This applies also to that procedure's parameters and to any function return.</span></span> <span data-ttu-id="c4713-115">不過，如果該程序呼叫其他程序，本機變數保留其值在執行時被呼叫的程序。</span><span class="sxs-lookup"><span data-stu-id="c4713-115">However, if that procedure calls other procedures, the local variables retain their values while the called procedures are running.</span></span>  
  
## <a name="beginning-of-lifetime"></a><span data-ttu-id="c4713-116">存留期的開始</span><span class="sxs-lookup"><span data-stu-id="c4713-116">Beginning of Lifetime</span></span>  
 <span data-ttu-id="c4713-117">本機變數的存留期開始，當控制項進入宣告它的程序。</span><span class="sxs-lookup"><span data-stu-id="c4713-117">A local variable's lifetime begins when control enters the procedure in which it is declared.</span></span> <span data-ttu-id="c4713-118">此程序一開始，將會初始化為其資料類型的預設值的每個本機變數執行。</span><span class="sxs-lookup"><span data-stu-id="c4713-118">Every local variable is initialized to the default value for its data type as soon as the procedure begins running.</span></span> <span data-ttu-id="c4713-119">當程序遇到`Dim`指定起始值的陳述式，它會將設定這些變數初始值，即使您的程式碼有已指定其他值給它們。</span><span class="sxs-lookup"><span data-stu-id="c4713-119">When the procedure encounters a `Dim` statement that specifies initial values, it sets those variables to those values, even if your code had already assigned other values to them.</span></span>  
  
 <span data-ttu-id="c4713-120">結構變數中的每個成員都會被視為個別的變數它初始化。</span><span class="sxs-lookup"><span data-stu-id="c4713-120">Each member of a structure variable is initialized as if it were a separate variable.</span></span> <span data-ttu-id="c4713-121">同樣地，會分別初始化陣列變數的每個項目。</span><span class="sxs-lookup"><span data-stu-id="c4713-121">Similarly, each element of an array variable is initialized individually.</span></span>  
  
 <span data-ttu-id="c4713-122">在程序內的區塊內宣告的變數 (例如`For`迴圈) 會初始化程序的項目。</span><span class="sxs-lookup"><span data-stu-id="c4713-122">Variables declared within a block inside a procedure (such as a `For` loop) are initialized on entry to the procedure.</span></span> <span data-ttu-id="c4713-123">無論您的程式碼曾經執行區塊，都會執行初始化。</span><span class="sxs-lookup"><span data-stu-id="c4713-123">These initializations take effect whether or not your code ever executes the block.</span></span>  
  
## <a name="end-of-lifetime"></a><span data-ttu-id="c4713-124">最後的存留期</span><span class="sxs-lookup"><span data-stu-id="c4713-124">End of Lifetime</span></span>  
 <span data-ttu-id="c4713-125">在程序終止時，不會保留其區域變數的值，和[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]回收其記憶體。</span><span class="sxs-lookup"><span data-stu-id="c4713-125">When a procedure terminates, the values of its local variables are not preserved, and [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] reclaims their memory.</span></span> <span data-ttu-id="c4713-126">下次呼叫程序中，所有的區域變數會從頭建立並重新初始化。</span><span class="sxs-lookup"><span data-stu-id="c4713-126">The next time you call the procedure, all its local variables are created afresh and reinitialized.</span></span>  
  
 <span data-ttu-id="c4713-127">在類別或結構的執行個體終止時，非共用的變數會遺失其記憶體和它們的值。</span><span class="sxs-lookup"><span data-stu-id="c4713-127">When an instance of a class or structure terminates, its nonshared variables lose their memory and their values.</span></span> <span data-ttu-id="c4713-128">每個類別或結構的新執行個體建立，並重新初始化非共用的變數。</span><span class="sxs-lookup"><span data-stu-id="c4713-128">Each new instance of the class or structure creates and reinitializes its nonshared variables.</span></span> <span data-ttu-id="c4713-129">不過，`Shared`變數會保留起來，直到您的應用程式停止執行。</span><span class="sxs-lookup"><span data-stu-id="c4713-129">However, `Shared` variables are preserved until your application stops running.</span></span>  
  
## <a name="extension-of-lifetime"></a><span data-ttu-id="c4713-130">延伸模組的存留期</span><span class="sxs-lookup"><span data-stu-id="c4713-130">Extension of Lifetime</span></span>  
 <span data-ttu-id="c4713-131">如果您宣告的區域變數`Static`關鍵字，其存留期就已經超過其程序的執行時間。</span><span class="sxs-lookup"><span data-stu-id="c4713-131">If you declare a local variable with the `Static` keyword, its lifetime is longer than the execution time of its procedure.</span></span> <span data-ttu-id="c4713-132">下表顯示程序宣告如何判斷多久`Static`變數存在。</span><span class="sxs-lookup"><span data-stu-id="c4713-132">The following table shows how the procedure declaration determines how long a `Static` variable exists.</span></span>  
  
|<span data-ttu-id="c4713-133">程序位置及共用</span><span class="sxs-lookup"><span data-stu-id="c4713-133">Procedure location and sharing</span></span>|<span data-ttu-id="c4713-134">靜態變數的存留期開始</span><span class="sxs-lookup"><span data-stu-id="c4713-134">Static variable lifetime begins</span></span>|<span data-ttu-id="c4713-135">靜態變數的存留期結束</span><span class="sxs-lookup"><span data-stu-id="c4713-135">Static variable lifetime ends</span></span>|  
|------------------------------------|-------------------------------------|-----------------------------------|  
|<span data-ttu-id="c4713-136">在模組中 （預設為共用）</span><span class="sxs-lookup"><span data-stu-id="c4713-136">In a module (shared by default)</span></span>|<span data-ttu-id="c4713-137">第一次呼叫程序</span><span class="sxs-lookup"><span data-stu-id="c4713-137">The first time the procedure is called</span></span>|<span data-ttu-id="c4713-138">當您的應用程式停止執行</span><span class="sxs-lookup"><span data-stu-id="c4713-138">When your application stops running</span></span>|  
|<span data-ttu-id="c4713-139">在類別中， `Shared` （程序不是執行個體成員）</span><span class="sxs-lookup"><span data-stu-id="c4713-139">In a class, `Shared` (procedure is not an instance member)</span></span>|<span data-ttu-id="c4713-140">第一次此程序呼叫的特定執行個體或類別或結構的名稱</span><span class="sxs-lookup"><span data-stu-id="c4713-140">The first time the procedure is called either on a specific instance or on the class or structure name itself</span></span>|<span data-ttu-id="c4713-141">當您的應用程式停止執行</span><span class="sxs-lookup"><span data-stu-id="c4713-141">When your application stops running</span></span>|  
|<span data-ttu-id="c4713-142">類別的執行個體中不`Shared`（程序是執行個體成員）</span><span class="sxs-lookup"><span data-stu-id="c4713-142">In an instance of a class, not `Shared` (procedure is an instance member)</span></span>|<span data-ttu-id="c4713-143">第一次在特定的執行個體呼叫程序</span><span class="sxs-lookup"><span data-stu-id="c4713-143">The first time the procedure is called on the specific instance</span></span>|<span data-ttu-id="c4713-144">釋放執行個體進行記憶體回收 (GC)</span><span class="sxs-lookup"><span data-stu-id="c4713-144">When the instance is released for garbage collection (GC)</span></span>|  
  
## <a name="static-variables-of-the-same-name"></a><span data-ttu-id="c4713-145">具有相同名稱的靜態變數</span><span class="sxs-lookup"><span data-stu-id="c4713-145">Static Variables of the Same Name</span></span>  
 <span data-ttu-id="c4713-146">您可以宣告具有相同名稱在一個以上的程序中的靜態變數。</span><span class="sxs-lookup"><span data-stu-id="c4713-146">You can declare static variables with the same name in more than one procedure.</span></span> <span data-ttu-id="c4713-147">如果這樣做，請[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器會考慮每個這類變數來個別項目。</span><span class="sxs-lookup"><span data-stu-id="c4713-147">If you do this, the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler considers each such variable to be a separate element.</span></span> <span data-ttu-id="c4713-148">其中一個變數的初始化不會影響其他的值。</span><span class="sxs-lookup"><span data-stu-id="c4713-148">The initialization of one of these variables does not affect the values of the others.</span></span> <span data-ttu-id="c4713-149">如果您定義具有一組多載的程序，並套用宣告靜態變數具有相同名稱在每個多載。</span><span class="sxs-lookup"><span data-stu-id="c4713-149">The same applies if you define a procedure with a set of overloads and declare a static variable with the same name in each overload.</span></span>  
  
## <a name="containing-elements-for-static-variables"></a><span data-ttu-id="c4713-150">靜態變數的包含項目</span><span class="sxs-lookup"><span data-stu-id="c4713-150">Containing Elements for Static Variables</span></span>  
 <span data-ttu-id="c4713-151">您可以在該類別中的程序內，也就是宣告類別內，靜態區域變數。</span><span class="sxs-lookup"><span data-stu-id="c4713-151">You can declare a static local variable within a class, that is, inside a procedure in that class.</span></span> <span data-ttu-id="c4713-152">不過，您無法宣告結構內，靜態區域變數的結構成員，或在該結構中的程序的本機變數。</span><span class="sxs-lookup"><span data-stu-id="c4713-152">However, you cannot declare a static local variable within a structure, either as a structure member or as a local variable of a procedure within that structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4713-153">範例</span><span class="sxs-lookup"><span data-stu-id="c4713-153">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="c4713-154">說明</span><span class="sxs-lookup"><span data-stu-id="c4713-154">Description</span></span>  
 <span data-ttu-id="c4713-155">下列範例宣告的變數[靜態](../../../../visual-basic/language-reference/modifiers/static.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="c4713-155">The following example declares a variable with the [Static](../../../../visual-basic/language-reference/modifiers/static.md) keyword.</span></span> <span data-ttu-id="c4713-156">(請注意，您不需要`Dim`關鍵字時[Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)使用修飾詞，例如`Static`。)</span><span class="sxs-lookup"><span data-stu-id="c4713-156">(Note that you do not need the `Dim` keyword when the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) uses a modifier such as `Static`.)</span></span>  
  
### <a name="code"></a><span data-ttu-id="c4713-157">程式碼</span><span class="sxs-lookup"><span data-stu-id="c4713-157">Code</span></span>  
 <span data-ttu-id="c4713-158">[!code-vb[VbVbalrKeywords #&13;](../../../../visual-basic/language-reference/codesnippet/VisualBasic/lifetime_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="c4713-158">[!code-vb[VbVbalrKeywords#13](../../../../visual-basic/language-reference/codesnippet/VisualBasic/lifetime_1.vb)]</span></span>  
  
### <a name="comments"></a><span data-ttu-id="c4713-159">註解</span><span class="sxs-lookup"><span data-stu-id="c4713-159">Comments</span></span>  
 <span data-ttu-id="c4713-160">在上述範例中，變數`applesSold`會繼續存在的程序之後`runningTotal`傳回給呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="c4713-160">In the preceding example, the variable `applesSold` continues to exist after the procedure `runningTotal` returns to the calling code.</span></span> <span data-ttu-id="c4713-161">在下一次`runningTotal`呼叫時，`applesSold`會保留其先前的導出值。</span><span class="sxs-lookup"><span data-stu-id="c4713-161">The next time `runningTotal` is called, `applesSold` retains its previously calculated value.</span></span>  
  
 <span data-ttu-id="c4713-162">如果`applesSold`已宣告不使用`Static`，不會跨呼叫保留先前的累積的值`runningTotal`。</span><span class="sxs-lookup"><span data-stu-id="c4713-162">If `applesSold` had been declared without using `Static`, the previous accumulated values would not be preserved across calls to `runningTotal`.</span></span> <span data-ttu-id="c4713-163">在下一次`runningTotal`已呼叫`applesSold`會重新建立並初始化為 0，和`runningTotal`會直接傳回相同的值與被呼叫。</span><span class="sxs-lookup"><span data-stu-id="c4713-163">The next time `runningTotal` was called, `applesSold` would have been recreated and initialized to 0, and `runningTotal` would have simply returned the same value with which it was called.</span></span>  
  
### <a name="compiling-the-code"></a><span data-ttu-id="c4713-164">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="c4713-164">Compiling the Code</span></span>  
 <span data-ttu-id="c4713-165">您可以初始化靜態區域變數做為其宣告的一部分的值。</span><span class="sxs-lookup"><span data-stu-id="c4713-165">You can initialize the value of a static local variable as part of its declaration.</span></span> <span data-ttu-id="c4713-166">如果您宣告為陣列`Static`，您可以初始化其陣序規範 （維度數目）、 每個維度，以及個別項目的值。</span><span class="sxs-lookup"><span data-stu-id="c4713-166">If you declare an array to be `Static`, you can initialize its rank (number of dimensions), the length of each dimension, and the values of the individual elements.</span></span>  
  
### <a name="security"></a><span data-ttu-id="c4713-167">安全性</span><span class="sxs-lookup"><span data-stu-id="c4713-167">Security</span></span>  
 <span data-ttu-id="c4713-168">在上述範例中，您可以產生相同的存留期宣告`applesSold`在模組層級。</span><span class="sxs-lookup"><span data-stu-id="c4713-168">In the preceding example, you can produce the same lifetime by declaring `applesSold` at module level.</span></span> <span data-ttu-id="c4713-169">如果這種方式變更變數的範圍，不過，程序就不再需要獨佔存取。</span><span class="sxs-lookup"><span data-stu-id="c4713-169">If you changed the scope of a variable this way, however, the procedure would no longer have exclusive access to it.</span></span> <span data-ttu-id="c4713-170">因為其他程序無法存取`applesSold`並變更其值、 加總可能不可靠和程式碼可能會更難維護。</span><span class="sxs-lookup"><span data-stu-id="c4713-170">Because other procedures could access `applesSold` and change its value, the running total could be unreliable and the code could be more difficult to maintain.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4713-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4713-171">See Also</span></span>  
 <span data-ttu-id="c4713-172">[共用](../../../../visual-basic/language-reference/modifiers/shared.md) </span><span class="sxs-lookup"><span data-stu-id="c4713-172">[Shared](../../../../visual-basic/language-reference/modifiers/shared.md) </span></span>  
<span data-ttu-id="c4713-173"> [執行任何動作](../../../../visual-basic/language-reference/nothing.md) </span><span class="sxs-lookup"><span data-stu-id="c4713-173"> [Nothing](../../../../visual-basic/language-reference/nothing.md) </span></span>  
<span data-ttu-id="c4713-174"> [宣告項目名稱](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md) </span><span class="sxs-lookup"><span data-stu-id="c4713-174"> [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md) </span></span>  
<span data-ttu-id="c4713-175"> [宣告項目參考](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md) </span><span class="sxs-lookup"><span data-stu-id="c4713-175"> [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md) </span></span>  
<span data-ttu-id="c4713-176"> [在 Visual Basic 中的範圍](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md) </span><span class="sxs-lookup"><span data-stu-id="c4713-176"> [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md) </span></span>  
<span data-ttu-id="c4713-177"> [在 Visual Basic 中的存取層級](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md) </span><span class="sxs-lookup"><span data-stu-id="c4713-177"> [Access Levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md) </span></span>  
<span data-ttu-id="c4713-178"> [變數](../../../../visual-basic/programming-guide/language-features/variables/index.md) </span><span class="sxs-lookup"><span data-stu-id="c4713-178"> [Variables](../../../../visual-basic/programming-guide/language-features/variables/index.md) </span></span>  
<span data-ttu-id="c4713-179"> [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span><span class="sxs-lookup"><span data-stu-id="c4713-179"> [Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span></span>  
<span data-ttu-id="c4713-180"> [資料類型疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="c4713-180"> [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span></span>  
<span data-ttu-id="c4713-181"> [Static](../../../../visual-basic/language-reference/modifiers/static.md)</span><span class="sxs-lookup"><span data-stu-id="c4713-181"> [Static](../../../../visual-basic/language-reference/modifiers/static.md)</span></span>
