---
title: 存留期
ms.date: 07/20/2015
helpviewer_keywords:
- static variables [Visual Basic], lifetime
- static variables [Visual Basic], Visual Basic
- declared elements [Visual Basic], lifetime
- Shared variable lifetime [Visual Basic]
- lifetime [Visual Basic], declared elements
- lifetime [Visual Basic], Visual Basic
- lifetime [Visual Basic]
ms.assetid: bd91e390-690a-469a-9946-8dca70bc14e7
ms.openlocfilehash: 67fe63eecd2aa0c134682708cdeddb21ba06db12
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91087488"
---
# <a name="lifetime-in-visual-basic"></a><span data-ttu-id="e708a-102">Visual Basic 中的存留期</span><span class="sxs-lookup"><span data-stu-id="e708a-102">Lifetime in Visual Basic</span></span>

<span data-ttu-id="e708a-103">宣告專案的 *存留* 期是可供使用的時間週期。</span><span class="sxs-lookup"><span data-stu-id="e708a-103">The *lifetime* of a declared element is the period of time during which it is available for use.</span></span> <span data-ttu-id="e708a-104">變數是具有存留期的唯一元素。</span><span class="sxs-lookup"><span data-stu-id="e708a-104">Variables are the only elements that have lifetime.</span></span> <span data-ttu-id="e708a-105">基於這個目的，編譯器會將程式參數和函數傳回視為變數的特殊案例。</span><span class="sxs-lookup"><span data-stu-id="e708a-105">For this purpose, the compiler treats procedure parameters and function returns as special cases of variables.</span></span> <span data-ttu-id="e708a-106">變數的存留期代表可保存值的時間週期。</span><span class="sxs-lookup"><span data-stu-id="e708a-106">The lifetime of a variable represents the period of time during which it can hold a value.</span></span> <span data-ttu-id="e708a-107">其值可能會在其存留期內變更，但永遠會保留一些值。</span><span class="sxs-lookup"><span data-stu-id="e708a-107">Its value can change over its lifetime, but it always holds some value.</span></span>  
  
## <a name="different-lifetimes"></a><span data-ttu-id="e708a-108">不同的存留期</span><span class="sxs-lookup"><span data-stu-id="e708a-108">Different Lifetimes</span></span>  

 <span data-ttu-id="e708a-109">*成員變數* (在模組層級宣告，而在任何程式之外) 通常與宣告它的元素具有相同的存留期。</span><span class="sxs-lookup"><span data-stu-id="e708a-109">A *member variable* (declared at module level, outside any procedure) typically has the same lifetime as the element in which it is declared.</span></span> <span data-ttu-id="e708a-110">在類別或結構中宣告的非共用變數，會以個別的複本形式存在，其為其宣告所在之類別或結構的每個實例。</span><span class="sxs-lookup"><span data-stu-id="e708a-110">A nonshared variable declared in a class or structure exists as a separate copy for each instance of the class or structure in which it is declared.</span></span> <span data-ttu-id="e708a-111">每個這類變數的存留期都與其實例相同。</span><span class="sxs-lookup"><span data-stu-id="e708a-111">Each such variable has the same lifetime as its instance.</span></span> <span data-ttu-id="e708a-112">不過， `Shared` 變數只會有單一存留期，這會在您的應用程式執行的整個時間持續運作。</span><span class="sxs-lookup"><span data-stu-id="e708a-112">However, a `Shared` variable has only a single lifetime, which lasts for the entire time your application is running.</span></span>  
  
 <span data-ttu-id="e708a-113">只有在宣告中的程式正在執行時，才會在程式中宣告 (*區域變數*) 存在。</span><span class="sxs-lookup"><span data-stu-id="e708a-113">A *local variable* (declared inside a procedure) exists only while the procedure in which it is declared is running.</span></span> <span data-ttu-id="e708a-114">這也適用于該程式的參數和任何函數傳回。</span><span class="sxs-lookup"><span data-stu-id="e708a-114">This applies also to that procedure's parameters and to any function return.</span></span> <span data-ttu-id="e708a-115">但是，如果該程式呼叫其他程式，則區域變數會在呼叫的程式執行時保留其值。</span><span class="sxs-lookup"><span data-stu-id="e708a-115">However, if that procedure calls other procedures, the local variables retain their values while the called procedures are running.</span></span>  
  
## <a name="beginning-of-lifetime"></a><span data-ttu-id="e708a-116">存留期開頭</span><span class="sxs-lookup"><span data-stu-id="e708a-116">Beginning of Lifetime</span></span>  

 <span data-ttu-id="e708a-117">本機變數的存留期會在控制項進入其宣告的程式時開始。</span><span class="sxs-lookup"><span data-stu-id="e708a-117">A local variable's lifetime begins when control enters the procedure in which it is declared.</span></span> <span data-ttu-id="e708a-118">一旦程式開始執行，每個區域變數都會初始化為其資料類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="e708a-118">Every local variable is initialized to the default value for its data type as soon as the procedure begins running.</span></span> <span data-ttu-id="e708a-119">當 `Dim` 程式遇到指定初始值的語句時，它會將這些變數設定為這些值，即使您的程式碼已經將其他值指派給它們也是一樣。</span><span class="sxs-lookup"><span data-stu-id="e708a-119">When the procedure encounters a `Dim` statement that specifies initial values, it sets those variables to those values, even if your code had already assigned other values to them.</span></span>  
  
 <span data-ttu-id="e708a-120">結構變數的每個成員都是以不同的變數來初始化。</span><span class="sxs-lookup"><span data-stu-id="e708a-120">Each member of a structure variable is initialized as if it were a separate variable.</span></span> <span data-ttu-id="e708a-121">同樣地，陣列變數的每個元素都會個別初始化。</span><span class="sxs-lookup"><span data-stu-id="e708a-121">Similarly, each element of an array variable is initialized individually.</span></span>  
  
 <span data-ttu-id="e708a-122">在程式內的區塊中宣告的變數 (例如 `For` 迴圈) 會在進入程式時初始化。</span><span class="sxs-lookup"><span data-stu-id="e708a-122">Variables declared within a block inside a procedure (such as a `For` loop) are initialized on entry to the procedure.</span></span> <span data-ttu-id="e708a-123">無論您的程式碼是否執行區塊，這些初始化都會生效。</span><span class="sxs-lookup"><span data-stu-id="e708a-123">These initializations take effect whether or not your code ever executes the block.</span></span>  
  
## <a name="end-of-lifetime"></a><span data-ttu-id="e708a-124">存留期結束</span><span class="sxs-lookup"><span data-stu-id="e708a-124">End of Lifetime</span></span>  

 <span data-ttu-id="e708a-125">當程式終止時，不會保留其區域變數的值，Visual Basic 回收其記憶體。</span><span class="sxs-lookup"><span data-stu-id="e708a-125">When a procedure terminates, the values of its local variables are not preserved, and Visual Basic reclaims their memory.</span></span> <span data-ttu-id="e708a-126">下次當您呼叫程式時，會再次並重新初始化其所有區域變數。</span><span class="sxs-lookup"><span data-stu-id="e708a-126">The next time you call the procedure, all its local variables are created afresh and reinitialized.</span></span>  
  
 <span data-ttu-id="e708a-127">當類別或結構的實例結束時，其非共用變數會遺失其記憶體和值。</span><span class="sxs-lookup"><span data-stu-id="e708a-127">When an instance of a class or structure terminates, its nonshared variables lose their memory and their values.</span></span> <span data-ttu-id="e708a-128">類別或結構的每個新實例都會建立並重新初始化其非共用的變數。</span><span class="sxs-lookup"><span data-stu-id="e708a-128">Each new instance of the class or structure creates and reinitializes its nonshared variables.</span></span> <span data-ttu-id="e708a-129">不過， `Shared` 在您的應用程式停止執行之前，會保留變數。</span><span class="sxs-lookup"><span data-stu-id="e708a-129">However, `Shared` variables are preserved until your application stops running.</span></span>  
  
## <a name="extension-of-lifetime"></a><span data-ttu-id="e708a-130">存留期的延伸</span><span class="sxs-lookup"><span data-stu-id="e708a-130">Extension of Lifetime</span></span>  

 <span data-ttu-id="e708a-131">如果您使用關鍵字宣告本機變數 `Static` ，其存留期會超過其程式的執行時間。</span><span class="sxs-lookup"><span data-stu-id="e708a-131">If you declare a local variable with the `Static` keyword, its lifetime is longer than the execution time of its procedure.</span></span> <span data-ttu-id="e708a-132">下表顯示程式聲明如何判斷變數存在的時間長度 `Static` 。</span><span class="sxs-lookup"><span data-stu-id="e708a-132">The following table shows how the procedure declaration determines how long a `Static` variable exists.</span></span>  
  
|<span data-ttu-id="e708a-133">程式位置和共用</span><span class="sxs-lookup"><span data-stu-id="e708a-133">Procedure location and sharing</span></span>|<span data-ttu-id="e708a-134">靜態變數存留期開始</span><span class="sxs-lookup"><span data-stu-id="e708a-134">Static variable lifetime begins</span></span>|<span data-ttu-id="e708a-135">靜態變數存留期結束</span><span class="sxs-lookup"><span data-stu-id="e708a-135">Static variable lifetime ends</span></span>|  
|------------------------------------|-------------------------------------|-----------------------------------|  
|<span data-ttu-id="e708a-136">在模組 (預設為共用) </span><span class="sxs-lookup"><span data-stu-id="e708a-136">In a module (shared by default)</span></span>|<span data-ttu-id="e708a-137">第一次呼叫程式時</span><span class="sxs-lookup"><span data-stu-id="e708a-137">The first time the procedure is called</span></span>|<span data-ttu-id="e708a-138">當您的應用程式停止執行時</span><span class="sxs-lookup"><span data-stu-id="e708a-138">When your application stops running</span></span>|  
|<span data-ttu-id="e708a-139">在類別中， `Shared` (程式不是實例成員) </span><span class="sxs-lookup"><span data-stu-id="e708a-139">In a class, `Shared` (procedure is not an instance member)</span></span>|<span data-ttu-id="e708a-140">第一次在特定實例上或類別或結構名稱本身呼叫程式</span><span class="sxs-lookup"><span data-stu-id="e708a-140">The first time the procedure is called either on a specific instance or on the class or structure name itself</span></span>|<span data-ttu-id="e708a-141">當您的應用程式停止執行時</span><span class="sxs-lookup"><span data-stu-id="e708a-141">When your application stops running</span></span>|  
|<span data-ttu-id="e708a-142">在類別的實例中，not `Shared` (程式是實例成員) </span><span class="sxs-lookup"><span data-stu-id="e708a-142">In an instance of a class, not `Shared` (procedure is an instance member)</span></span>|<span data-ttu-id="e708a-143">第一次在特定實例上呼叫程式</span><span class="sxs-lookup"><span data-stu-id="e708a-143">The first time the procedure is called on the specific instance</span></span>|<span data-ttu-id="e708a-144">釋放實例以進行垃圾收集時 (GC) </span><span class="sxs-lookup"><span data-stu-id="e708a-144">When the instance is released for garbage collection (GC)</span></span>|  
  
## <a name="static-variables-of-the-same-name"></a><span data-ttu-id="e708a-145">相同名稱的靜態變數</span><span class="sxs-lookup"><span data-stu-id="e708a-145">Static Variables of the Same Name</span></span>  

 <span data-ttu-id="e708a-146">您可以在多個程式中宣告具有相同名稱的靜態變數。</span><span class="sxs-lookup"><span data-stu-id="e708a-146">You can declare static variables with the same name in more than one procedure.</span></span> <span data-ttu-id="e708a-147">如果您這麼做，Visual Basic 編譯器會將每個這類變數視為個別的元素。</span><span class="sxs-lookup"><span data-stu-id="e708a-147">If you do this, the Visual Basic compiler considers each such variable to be a separate element.</span></span> <span data-ttu-id="e708a-148">初始化其中一個變數並不會影響其他變數的值。</span><span class="sxs-lookup"><span data-stu-id="e708a-148">The initialization of one of these variables does not affect the values of the others.</span></span> <span data-ttu-id="e708a-149">如果您定義具有一組多載的程式，並在每個多載中宣告具有相同名稱的靜態變數，則同樣適用。</span><span class="sxs-lookup"><span data-stu-id="e708a-149">The same applies if you define a procedure with a set of overloads and declare a static variable with the same name in each overload.</span></span>  
  
## <a name="containing-elements-for-static-variables"></a><span data-ttu-id="e708a-150">包含靜態變數的元素</span><span class="sxs-lookup"><span data-stu-id="e708a-150">Containing Elements for Static Variables</span></span>  

 <span data-ttu-id="e708a-151">您可以在類別內宣告靜態區域變數，也就是在該類別中的程式內。</span><span class="sxs-lookup"><span data-stu-id="e708a-151">You can declare a static local variable within a class, that is, inside a procedure in that class.</span></span> <span data-ttu-id="e708a-152">不過，您不能在結構內宣告靜態區域變數（可以是結構成員），也不能宣告為該結構內之程式的本機變數。</span><span class="sxs-lookup"><span data-stu-id="e708a-152">However, you cannot declare a static local variable within a structure, either as a structure member or as a local variable of a procedure within that structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e708a-153">範例</span><span class="sxs-lookup"><span data-stu-id="e708a-153">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="e708a-154">描述</span><span class="sxs-lookup"><span data-stu-id="e708a-154">Description</span></span>  

 <span data-ttu-id="e708a-155">下列範例會宣告具有 [Static](../../../language-reference/modifiers/static.md) 關鍵字的變數。</span><span class="sxs-lookup"><span data-stu-id="e708a-155">The following example declares a variable with the [Static](../../../language-reference/modifiers/static.md) keyword.</span></span> <span data-ttu-id="e708a-156"> (請注意， `Dim` 當 [Dim 語句](../../../language-reference/statements/dim-statement.md) 使用的修飾詞（例如）時，您不需要關鍵字 `Static` 。 ) </span><span class="sxs-lookup"><span data-stu-id="e708a-156">(Note that you do not need the `Dim` keyword when the [Dim Statement](../../../language-reference/statements/dim-statement.md) uses a modifier such as `Static`.)</span></span>  
  
### <a name="code"></a><span data-ttu-id="e708a-157">程式碼</span><span class="sxs-lookup"><span data-stu-id="e708a-157">Code</span></span>  

 [!code-vb[VbVbalrKeywords#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#13)]  
  
### <a name="comments"></a><span data-ttu-id="e708a-158">註解</span><span class="sxs-lookup"><span data-stu-id="e708a-158">Comments</span></span>  

 <span data-ttu-id="e708a-159">在上述範例中，此變數會在程式 `applesSold` 返回呼叫程式碼之後繼續存在 `runningTotal` 。</span><span class="sxs-lookup"><span data-stu-id="e708a-159">In the preceding example, the variable `applesSold` continues to exist after the procedure `runningTotal` returns to the calling code.</span></span> <span data-ttu-id="e708a-160">下一次 `runningTotal` 呼叫時，會 `applesSold` 保留先前所計算的值。</span><span class="sxs-lookup"><span data-stu-id="e708a-160">The next time `runningTotal` is called, `applesSold` retains its previously calculated value.</span></span>  
  
 <span data-ttu-id="e708a-161">如果在未 `applesSold` 使用的情況 `Static` 下宣告，則不會在的呼叫之間保留先前的累積值 `runningTotal` 。</span><span class="sxs-lookup"><span data-stu-id="e708a-161">If `applesSold` had been declared without using `Static`, the previous accumulated values would not be preserved across calls to `runningTotal`.</span></span> <span data-ttu-id="e708a-162">下一次 `runningTotal` 呼叫時， `applesSold` 會重新建立並將它初始化為0，而且 `runningTotal` 只會傳回與其所呼叫的相同值。</span><span class="sxs-lookup"><span data-stu-id="e708a-162">The next time `runningTotal` was called, `applesSold` would have been recreated and initialized to 0, and `runningTotal` would have simply returned the same value with which it was called.</span></span>  
  
### <a name="compile-the-code"></a><span data-ttu-id="e708a-163">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="e708a-163">Compile the code</span></span>  

 <span data-ttu-id="e708a-164">您可以將靜態區域變數的值初始化為其宣告的一部分。</span><span class="sxs-lookup"><span data-stu-id="e708a-164">You can initialize the value of a static local variable as part of its declaration.</span></span> <span data-ttu-id="e708a-165">如果您將陣列宣告為 `Static` ，則可以將其排名 () 的維度數目、每個維度的長度，以及個別元素的值。</span><span class="sxs-lookup"><span data-stu-id="e708a-165">If you declare an array to be `Static`, you can initialize its rank (number of dimensions), the length of each dimension, and the values of the individual elements.</span></span>  
  
### <a name="security"></a><span data-ttu-id="e708a-166">安全性</span><span class="sxs-lookup"><span data-stu-id="e708a-166">Security</span></span>  

 <span data-ttu-id="e708a-167">在上述範例中，您可以 `applesSold` 在模組層級宣告來產生相同的存留期。</span><span class="sxs-lookup"><span data-stu-id="e708a-167">In the preceding example, you can produce the same lifetime by declaring `applesSold` at module level.</span></span> <span data-ttu-id="e708a-168">但是，如果您以這種方式變更了變數的範圍，此程式將不再具有其獨佔存取權。</span><span class="sxs-lookup"><span data-stu-id="e708a-168">If you changed the scope of a variable this way, however, the procedure would no longer have exclusive access to it.</span></span> <span data-ttu-id="e708a-169">由於其他程式可以存取 `applesSold` 和變更其值，因此執行總數可能不可靠，而且程式碼可能更難維護。</span><span class="sxs-lookup"><span data-stu-id="e708a-169">Because other procedures could access `applesSold` and change its value, the running total could be unreliable and the code could be more difficult to maintain.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e708a-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e708a-170">See also</span></span>

- <span data-ttu-id="e708a-171">[共用][](../../../language-reference/modifiers/shared.md)</span><span class="sxs-lookup"><span data-stu-id="e708a-171">[Shared](../../../language-reference/modifiers/shared.md)</span></span>
- [<span data-ttu-id="e708a-172">什麼</span><span class="sxs-lookup"><span data-stu-id="e708a-172">Nothing</span></span>](../../../language-reference/nothing.md)
- [<span data-ttu-id="e708a-173">Declared Element Names</span><span class="sxs-lookup"><span data-stu-id="e708a-173">Declared Element Names</span></span>](declared-element-names.md)
- [<span data-ttu-id="e708a-174">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="e708a-174">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="e708a-175">Visual Basic 中的範圍</span><span class="sxs-lookup"><span data-stu-id="e708a-175">Scope in Visual Basic</span></span>](scope.md)
- [<span data-ttu-id="e708a-176">Visual Basic 中的存取層級</span><span class="sxs-lookup"><span data-stu-id="e708a-176">Access levels in Visual Basic</span></span>](access-levels.md)
- [<span data-ttu-id="e708a-177">變數</span><span class="sxs-lookup"><span data-stu-id="e708a-177">Variables</span></span>](../variables/index.md)
- [<span data-ttu-id="e708a-178">變數宣告</span><span class="sxs-lookup"><span data-stu-id="e708a-178">Variable Declaration</span></span>](../variables/variable-declaration.md)
- [<span data-ttu-id="e708a-179">疑難排解資料類型的問題</span><span class="sxs-lookup"><span data-stu-id="e708a-179">Troubleshooting Data Types</span></span>](../data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="e708a-180">靜態</span><span class="sxs-lookup"><span data-stu-id="e708a-180">Static</span></span>](../../../language-reference/modifiers/static.md)
