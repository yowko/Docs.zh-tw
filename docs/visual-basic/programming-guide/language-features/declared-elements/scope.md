---
title: "Visual Basic 中的範圍"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- module scope [Visual Basic]
- scope [Visual Basic], levels
- module level
- procedures [Visual Basic], scope
- declared elements [Visual Basic], scope
- namespaces [Visual Basic], scope
- scope [Visual Basic], declared elements
- scope [Visual Basic], about scope
- levels of scope [Visual Basic]
- block scope [Visual Basic]
- scope [Visual Basic], Visual Basic
- procedure scope [Visual Basic]
ms.assetid: 208106fe-79c9-4eec-93c6-55f08548895f
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a9bfda19b9f5ee96d45a0322541b35dfab7635d7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="scope-in-visual-basic"></a><span data-ttu-id="41994-102">Visual Basic 中的範圍</span><span class="sxs-lookup"><span data-stu-id="41994-102">Scope in Visual Basic</span></span>
<span data-ttu-id="41994-103">*範圍*的宣告的項目是 所有程式碼，而不需要限定其名稱，或透過參考一組[Imports 陳述式 （.NET 命名空間和類型）](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)。</span><span class="sxs-lookup"><span data-stu-id="41994-103">The *scope* of a declared element is the set of all code that can refer to it without qualifying its name or making it available through an [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span> <span data-ttu-id="41994-104">元素可以有範圍，在下列層級的其中一個：</span><span class="sxs-lookup"><span data-stu-id="41994-104">An element can have scope at one of the following levels:</span></span>  
  
|<span data-ttu-id="41994-105">層級</span><span class="sxs-lookup"><span data-stu-id="41994-105">Level</span></span>|<span data-ttu-id="41994-106">描述</span><span class="sxs-lookup"><span data-stu-id="41994-106">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="41994-107">區塊範圍</span><span class="sxs-lookup"><span data-stu-id="41994-107">Block scope</span></span>|<span data-ttu-id="41994-108">只有在程式碼內的可用區塊內宣告</span><span class="sxs-lookup"><span data-stu-id="41994-108">Available only within the code block in which it is declared</span></span>|  
|<span data-ttu-id="41994-109">程序範圍</span><span class="sxs-lookup"><span data-stu-id="41994-109">Procedure scope</span></span>|<span data-ttu-id="41994-110">適用於在宣告它的程序中的所有程式碼</span><span class="sxs-lookup"><span data-stu-id="41994-110">Available to all code within the procedure in which it is declared</span></span>|  
|<span data-ttu-id="41994-111">模組範圍</span><span class="sxs-lookup"><span data-stu-id="41994-111">Module scope</span></span>|<span data-ttu-id="41994-112">提供給內模組、 類別或結構宣告它的所有程式碼</span><span class="sxs-lookup"><span data-stu-id="41994-112">Available to all code within the module, class, or structure in which it is declared</span></span>|  
|<span data-ttu-id="41994-113">命名空間範圍</span><span class="sxs-lookup"><span data-stu-id="41994-113">Namespace scope</span></span>|<span data-ttu-id="41994-114">提供給所有的程式碼會宣告命名空間中</span><span class="sxs-lookup"><span data-stu-id="41994-114">Available to all code in the namespace in which it is declared</span></span>|  
  
 <span data-ttu-id="41994-115">這些範圍的層級的最少的 （區塊） 從在寬 （命名空間），其中*最小範圍*表示無限制的項目可以參考程式碼的最小集。</span><span class="sxs-lookup"><span data-stu-id="41994-115">These levels of scope progress from the narrowest (block) to the widest (namespace), where *narrowest scope* means the smallest set of code that can refer to the element without qualification.</span></span> <span data-ttu-id="41994-116">如需詳細資訊，請參閱此頁面上的 「 範圍層級 」。</span><span class="sxs-lookup"><span data-stu-id="41994-116">For more information, see "Levels of Scope" on this page.</span></span>  
  
## <a name="specifying-scope-and-defining-variables"></a><span data-ttu-id="41994-117">指定範圍，以及定義變數</span><span class="sxs-lookup"><span data-stu-id="41994-117">Specifying Scope and Defining Variables</span></span>  
 <span data-ttu-id="41994-118">當您宣告它時，您可以指定項目的範圍。</span><span class="sxs-lookup"><span data-stu-id="41994-118">You specify the scope of an element when you declare it.</span></span> <span data-ttu-id="41994-119">範圍可能會相依於下列因素：</span><span class="sxs-lookup"><span data-stu-id="41994-119">The scope can depend on the following factors:</span></span>  
  
-   <span data-ttu-id="41994-120">您可以在其中宣告項目區域 （區塊、 程序、 模組、 類別或結構）</span><span class="sxs-lookup"><span data-stu-id="41994-120">The region (block, procedure, module, class, or structure) in which you declare the element</span></span>  
  
-   <span data-ttu-id="41994-121">包含的項目宣告的命名空間</span><span class="sxs-lookup"><span data-stu-id="41994-121">The namespace containing the element's declaration</span></span>  
  
-   <span data-ttu-id="41994-122">您宣告的項目存取層級</span><span class="sxs-lookup"><span data-stu-id="41994-122">The access level you declare for the element</span></span>  
  
 <span data-ttu-id="41994-123">注意當您定義使用變數具有相同名稱但不同的範圍，因為這樣做可能會造成非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="41994-123">Use care when you define variables with the same name but different scope, because doing so can lead to unexpected results.</span></span> <span data-ttu-id="41994-124">如需詳細資訊，請參閱 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)。</span><span class="sxs-lookup"><span data-stu-id="41994-124">For more information, see [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
## <a name="levels-of-scope"></a><span data-ttu-id="41994-125">範圍層級</span><span class="sxs-lookup"><span data-stu-id="41994-125">Levels of Scope</span></span>  
 <span data-ttu-id="41994-126">整個區域宣告它使用的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="41994-126">A programming element is available throughout the region in which you declare it.</span></span> <span data-ttu-id="41994-127">相同區域中的所有程式碼可以參考的項目中，而不需要限定其名稱。</span><span class="sxs-lookup"><span data-stu-id="41994-127">All code in the same region can refer to the element without qualifying its name.</span></span>  
  
### <a name="block-scope"></a><span data-ttu-id="41994-128">區塊範圍</span><span class="sxs-lookup"><span data-stu-id="41994-128">Block Scope</span></span>  
 <span data-ttu-id="41994-129">一個區塊是一組陳述式括住初始和終止宣告陳述式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="41994-129">A block is a set of statements enclosed within initiating and terminating declaration statements, such as the following:</span></span>  
  
-   <span data-ttu-id="41994-130">`Do` 和 `Loop`</span><span class="sxs-lookup"><span data-stu-id="41994-130">`Do` and `Loop`</span></span>  
  
-   <span data-ttu-id="41994-131">`For`[`Each`] 和`Next`</span><span class="sxs-lookup"><span data-stu-id="41994-131">`For` [`Each`] and `Next`</span></span>  
  
-   <span data-ttu-id="41994-132">`If` 和 `End If`</span><span class="sxs-lookup"><span data-stu-id="41994-132">`If` and `End If`</span></span>  
  
-   <span data-ttu-id="41994-133">`Select` 和 `End Select`</span><span class="sxs-lookup"><span data-stu-id="41994-133">`Select` and `End Select`</span></span>  
  
-   <span data-ttu-id="41994-134">`SyncLock` 和 `End SyncLock`</span><span class="sxs-lookup"><span data-stu-id="41994-134">`SyncLock` and `End SyncLock`</span></span>  
  
-   <span data-ttu-id="41994-135">`Try` 和 `End Try`</span><span class="sxs-lookup"><span data-stu-id="41994-135">`Try` and `End Try`</span></span>  
  
-   <span data-ttu-id="41994-136">`While` 和 `End While`</span><span class="sxs-lookup"><span data-stu-id="41994-136">`While` and `End While`</span></span>  
  
-   <span data-ttu-id="41994-137">`With` 和 `End With`</span><span class="sxs-lookup"><span data-stu-id="41994-137">`With` and `End With`</span></span>  
  
 <span data-ttu-id="41994-138">如果您宣告的變數在區塊內，您可以使用它只在該區塊內。</span><span class="sxs-lookup"><span data-stu-id="41994-138">If you declare a variable within a block, you can use it only within that block.</span></span> <span data-ttu-id="41994-139">在下列範例中，整數變數的範圍`cube`之間區塊`If`和`End If`，而且您可以不再參考`cube`當執行會通過區塊之外。</span><span class="sxs-lookup"><span data-stu-id="41994-139">In the following example, the scope of the integer variable `cube` is the block between `If` and `End If`, and you can no longer refer to `cube` when execution passes out of the block.</span></span>  
  
```  
If n < 1291 Then  
    Dim cube As Integer  
    cube = n ^ 3  
End If  
```  
  
> [!NOTE]
>  <span data-ttu-id="41994-140">即使變數的範圍僅限於一個區塊，其存留期仍然是整個程序。</span><span class="sxs-lookup"><span data-stu-id="41994-140">Even if the scope of a variable is limited to a block, its lifetime is still that of the entire procedure.</span></span> <span data-ttu-id="41994-141">如果在程序中多次進入區塊時，每個區塊變數會保留先前的值。</span><span class="sxs-lookup"><span data-stu-id="41994-141">If you enter the block more than once during the procedure, each block variable retains its previous value.</span></span> <span data-ttu-id="41994-142">若要避免非預期的結果，在這種情況下，最好將初始化的區塊開頭的區塊變數。</span><span class="sxs-lookup"><span data-stu-id="41994-142">To avoid unexpected results in such a case, it is wise to initialize block variables at the beginning of the block.</span></span>  
  
### <a name="procedure-scope"></a><span data-ttu-id="41994-143">程序範圍</span><span class="sxs-lookup"><span data-stu-id="41994-143">Procedure Scope</span></span>  
 <span data-ttu-id="41994-144">無法使用該程序之外宣告程序內的項目。</span><span class="sxs-lookup"><span data-stu-id="41994-144">An element declared within a procedure is not available outside that procedure.</span></span> <span data-ttu-id="41994-145">包含宣告的程序可以使用它。</span><span class="sxs-lookup"><span data-stu-id="41994-145">Only the procedure that contains the declaration can use it.</span></span> <span data-ttu-id="41994-146">在此層級的變數是也稱為*區域變數*。</span><span class="sxs-lookup"><span data-stu-id="41994-146">Variables at this level are also known as *local variables*.</span></span> <span data-ttu-id="41994-147">您將其與宣告[Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)、 含[靜態](../../../../visual-basic/language-reference/modifiers/static.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="41994-147">You declare them with the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md), with or without the [Static](../../../../visual-basic/language-reference/modifiers/static.md) keyword.</span></span>  
  
 <span data-ttu-id="41994-148">密切相關程序和區塊的範圍。</span><span class="sxs-lookup"><span data-stu-id="41994-148">Procedure and block scope are closely related.</span></span> <span data-ttu-id="41994-149">如果您宣告的變數，該程序內任何區塊內的程序之外，您可以將此變數視為具有區塊範圍，其中區塊是整個程序。</span><span class="sxs-lookup"><span data-stu-id="41994-149">If you declare a variable inside a procedure but outside any block within that procedure, you can think of the variable as having block scope, where the block is the entire procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="41994-150">所有本機元素，即使它們是`Static`變數，都是私用程序以其出現。</span><span class="sxs-lookup"><span data-stu-id="41994-150">All local elements, even if they are `Static` variables, are private to the procedure in which they appear.</span></span> <span data-ttu-id="41994-151">您無法宣告任何項目使用[公用](../../../../visual-basic/language-reference/modifiers/public.md)程序內的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="41994-151">You cannot declare any element using the [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword within a procedure.</span></span>  
  
### <a name="module-scope"></a><span data-ttu-id="41994-152">模組範圍</span><span class="sxs-lookup"><span data-stu-id="41994-152">Module Scope</span></span>  
 <span data-ttu-id="41994-153">為了方便起見，單一詞彙*模組層級*同樣適用於模組、 類別和結構。</span><span class="sxs-lookup"><span data-stu-id="41994-153">For convenience, the single term *module level* applies equally to modules, classes, and structures.</span></span> <span data-ttu-id="41994-154">您可以宣告此層級的項目放入任何程序或區塊外部，但模組、 類別或結構內宣告陳述式。</span><span class="sxs-lookup"><span data-stu-id="41994-154">You can declare elements at this level by placing the declaration statement outside of any procedure or block but within the module, class, or structure.</span></span>  
  
 <span data-ttu-id="41994-155">當您在模組層級的宣告時，您所選擇的存取層級會決定的範圍。</span><span class="sxs-lookup"><span data-stu-id="41994-155">When you make a declaration at the module level, the access level you choose determines the scope.</span></span> <span data-ttu-id="41994-156">包含模組、 類別或結構的命名空間也會影響範圍。</span><span class="sxs-lookup"><span data-stu-id="41994-156">The namespace that contains the module, class, or structure also affects the scope.</span></span>  
  
 <span data-ttu-id="41994-157">在您宣告的項目[私人](../../../../visual-basic/language-reference/modifiers/private.md)存取層級可用每個程序，在該模組中，但是不能在不同的模組中的任何程式碼。</span><span class="sxs-lookup"><span data-stu-id="41994-157">Elements for which you declare [Private](../../../../visual-basic/language-reference/modifiers/private.md) access level are available to every procedure in that module, but not to any code in a different module.</span></span> <span data-ttu-id="41994-158">`Dim`陳述式在模組層級預設為`Private`如果您未使用任何存取層級的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="41994-158">The `Dim` statement at module level defaults to `Private` if you do not use any access level keywords.</span></span> <span data-ttu-id="41994-159">不過，您可以建立將領域和存取層級更明顯使用`Private`關鍵字`Dim`陳述式。</span><span class="sxs-lookup"><span data-stu-id="41994-159">However, you can make the scope and access level more obvious by using the `Private` keyword in the `Dim` statement.</span></span>  
  
 <span data-ttu-id="41994-160">下列範例中，在模組中定義的所有程序可以參考的字串變數`strMsg`。</span><span class="sxs-lookup"><span data-stu-id="41994-160">In the following example, all procedures defined in the module can refer to the string variable `strMsg`.</span></span> <span data-ttu-id="41994-161">第二個程序呼叫時，它會顯示字串變數的內容`strMsg`對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="41994-161">When the second procedure is called, it displays the contents of the string variable `strMsg` in a dialog box.</span></span>  
  
```  
' Put the following declaration at module level (not in any procedure).  
Private strMsg As String  
' Put the following Sub procedure in the same module.  
Sub initializePrivateVariable()  
    strMsg = "This variable cannot be used outside this module."  
End Sub  
' Put the following Sub procedure in the same module.  
Sub usePrivateVariable()  
    MsgBox(strMsg)  
End Sub  
```  
  
### <a name="namespace-scope"></a><span data-ttu-id="41994-162">命名空間範圍</span><span class="sxs-lookup"><span data-stu-id="41994-162">Namespace Scope</span></span>  
 <span data-ttu-id="41994-163">如果您宣告的項目，在模組層級使用[Friend](../../../../visual-basic/language-reference/modifiers/friend.md)或[公用](../../../../visual-basic/language-reference/modifiers/public.md)關鍵字，它就會變成可用至整個宣告項目所在的命名空間的所有程序。</span><span class="sxs-lookup"><span data-stu-id="41994-163">If you declare an element at module level using the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) or [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword, it becomes available to all procedures throughout the namespace in which the element is declared.</span></span> <span data-ttu-id="41994-164">與上述範例中，字串變數將`strMsg`可以參考其宣告的命名空間中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="41994-164">With the following alteration to the preceding example, the string variable `strMsg` can be referred to by code anywhere in the namespace of its declaration.</span></span>  
  
```  
' Include this declaration at module level (not inside any procedure).  
Public strMsg As String  
```  
  
 <span data-ttu-id="41994-165">命名空間範圍包括巢狀命名空間。</span><span class="sxs-lookup"><span data-stu-id="41994-165">Namespace scope includes nested namespaces.</span></span> <span data-ttu-id="41994-166">命名空間內可用的項目也會提供任何巢狀方式置於該命名空間的命名空間內。</span><span class="sxs-lookup"><span data-stu-id="41994-166">An element available from within a namespace is also available from within any namespace nested inside that namespace.</span></span>  
  
 <span data-ttu-id="41994-167">如果您的專案不包含任何[命名空間陳述式](../../../../visual-basic/language-reference/statements/namespace-statement.md)s，專案中的所有項目是在相同的命名空間中。</span><span class="sxs-lookup"><span data-stu-id="41994-167">If your project does not contain any [Namespace Statement](../../../../visual-basic/language-reference/statements/namespace-statement.md)s, everything in the project is in the same namespace.</span></span> <span data-ttu-id="41994-168">在此情況下，命名空間範圍可以視為專案範圍。</span><span class="sxs-lookup"><span data-stu-id="41994-168">In this case, namespace scope can be thought of as project scope.</span></span> <span data-ttu-id="41994-169">`Public`模組、 類別或結構中的項目也可用來參考其專案的任何專案。</span><span class="sxs-lookup"><span data-stu-id="41994-169">`Public` elements in a module, class, or structure are also available to any project that references their project.</span></span>  
  
## <a name="choice-of-scope"></a><span data-ttu-id="41994-170">選擇範圍</span><span class="sxs-lookup"><span data-stu-id="41994-170">Choice of Scope</span></span>  
 <span data-ttu-id="41994-171">當您宣告變數時，您應該記住下列幾點選擇其範圍時。</span><span class="sxs-lookup"><span data-stu-id="41994-171">When you declare a variable, you should keep in mind the following points when choosing its scope.</span></span>  
  
### <a name="advantages-of-local-variables"></a><span data-ttu-id="41994-172">本機變數的優點</span><span class="sxs-lookup"><span data-stu-id="41994-172">Advantages of Local Variables</span></span>  
 <span data-ttu-id="41994-173">本機變數是不錯的選擇對於任何類型的暫存計算，原因如下：</span><span class="sxs-lookup"><span data-stu-id="41994-173">Local variables are a good choice for any kind of temporary calculation, for the following reasons:</span></span>  
  
-   <span data-ttu-id="41994-174">**避免名稱衝突。**</span><span class="sxs-lookup"><span data-stu-id="41994-174">**Name Conflict Avoidance.**</span></span> <span data-ttu-id="41994-175">本機變數名稱不容易發生衝突。</span><span class="sxs-lookup"><span data-stu-id="41994-175">Local variable names are not susceptible to conflict.</span></span> <span data-ttu-id="41994-176">例如，您可以建立數個不同的程序包含名為`intTemp`。</span><span class="sxs-lookup"><span data-stu-id="41994-176">For example, you can create several different procedures containing a variable called `intTemp`.</span></span> <span data-ttu-id="41994-177">只要每個`intTemp`宣告為區域變數，每個程序能夠辨識只有自己版本的`intTemp`。</span><span class="sxs-lookup"><span data-stu-id="41994-177">As long as each `intTemp` is declared as a local variable, each procedure recognizes only its own version of `intTemp`.</span></span> <span data-ttu-id="41994-178">任何一個程序可以改變在其區域變數值`intTemp`而不會影響`intTemp`其他程序中的變數。</span><span class="sxs-lookup"><span data-stu-id="41994-178">Any one procedure can alter the value in its local `intTemp` without affecting `intTemp` variables in other procedures.</span></span>  
  
-   <span data-ttu-id="41994-179">**記憶體耗用量。**</span><span class="sxs-lookup"><span data-stu-id="41994-179">**Memory Consumption.**</span></span> <span data-ttu-id="41994-180">僅執行其程序時，本機變數會耗用記憶體。</span><span class="sxs-lookup"><span data-stu-id="41994-180">Local variables consume memory only while their procedure is running.</span></span> <span data-ttu-id="41994-181">程序傳回呼叫程式碼時，會釋放其記憶體。</span><span class="sxs-lookup"><span data-stu-id="41994-181">Their memory is released when the procedure returns to the calling code.</span></span> <span data-ttu-id="41994-182">相反地，[共用](../../../../visual-basic/language-reference/modifiers/shared.md)和[靜態](../../../../visual-basic/language-reference/modifiers/static.md)變數耗用的記憶體資源，直到您的應用程式停止執行，因此，它們只在必要時使用。</span><span class="sxs-lookup"><span data-stu-id="41994-182">By contrast, [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) and [Static](../../../../visual-basic/language-reference/modifiers/static.md) variables consume memory resources until your application stops running, so use them only when necessary.</span></span> <span data-ttu-id="41994-183">*執行個體變數*耗用的記憶體時，其執行個體會持續存在，使其成為較有效率的區域變數，但可能更有效率`Shared`或`Static`變數。</span><span class="sxs-lookup"><span data-stu-id="41994-183">*Instance variables* consume memory while their instance continues to exist, which makes them less efficient than local variables, but potentially more efficient than `Shared` or `Static` variables.</span></span>  
  
### <a name="minimizing-scope"></a><span data-ttu-id="41994-184">最小化範圍</span><span class="sxs-lookup"><span data-stu-id="41994-184">Minimizing Scope</span></span>  
 <span data-ttu-id="41994-185">一般情況下，宣告任何變數或常數，它是良好的程式設計作法進行範圍愈小愈好 （區塊範圍最小）。</span><span class="sxs-lookup"><span data-stu-id="41994-185">In general, when declaring any variable or constant, it is good programming practice to make the scope as narrow as possible (block scope is the narrowest).</span></span> <span data-ttu-id="41994-186">這有助於節省記憶體，並將程式碼誤用錯誤變數的機會降到最低。</span><span class="sxs-lookup"><span data-stu-id="41994-186">This helps conserve memory and minimizes the chances of your code erroneously referring to the wrong variable.</span></span> <span data-ttu-id="41994-187">同樣地，您應該在其中宣告變數為[靜態](../../../../visual-basic/language-reference/modifiers/static.md)只會在必要時要保留其程序呼叫的間隔值。</span><span class="sxs-lookup"><span data-stu-id="41994-187">Similarly, you should declare a variable to be [Static](../../../../visual-basic/language-reference/modifiers/static.md) only when it is necessary to preserve its value between procedure calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41994-188">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41994-188">See Also</span></span>  
 [<span data-ttu-id="41994-189">宣告項目特性</span><span class="sxs-lookup"><span data-stu-id="41994-189">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [<span data-ttu-id="41994-190">如何：控制變數的範圍</span><span class="sxs-lookup"><span data-stu-id="41994-190">How to: Control the Scope of a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)  
 [<span data-ttu-id="41994-191">在 Visual Basic 中的存留期</span><span class="sxs-lookup"><span data-stu-id="41994-191">Lifetime in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [<span data-ttu-id="41994-192">在 Visual Basic 中的存取層級</span><span class="sxs-lookup"><span data-stu-id="41994-192">Access levels in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="41994-193">對已宣告項目的參考</span><span class="sxs-lookup"><span data-stu-id="41994-193">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="41994-194">變數宣告</span><span class="sxs-lookup"><span data-stu-id="41994-194">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
