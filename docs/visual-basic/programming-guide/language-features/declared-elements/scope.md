---
title: Visual Basic 中的範圍
ms.date: 07/20/2015
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
ms.openlocfilehash: 7f7e32d6ac838e250c260987d3d5c375f8697c45
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512855"
---
# <a name="scope-in-visual-basic"></a><span data-ttu-id="cc579-102">Visual Basic 中的範圍</span><span class="sxs-lookup"><span data-stu-id="cc579-102">Scope in Visual Basic</span></span>

<span data-ttu-id="cc579-103">已宣告專案的*範圍*是一組可以參考它的程式碼, 但不限定其名稱, 或透過[Imports 語句 (.net 命名空間和類型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)提供它。</span><span class="sxs-lookup"><span data-stu-id="cc579-103">The *scope* of a declared element is the set of all code that can refer to it without qualifying its name or making it available through an [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span> <span data-ttu-id="cc579-104">元素的範圍可以是下列其中一個層級:</span><span class="sxs-lookup"><span data-stu-id="cc579-104">An element can have scope at one of the following levels:</span></span>

|<span data-ttu-id="cc579-105">層級</span><span class="sxs-lookup"><span data-stu-id="cc579-105">Level</span></span>|<span data-ttu-id="cc579-106">描述</span><span class="sxs-lookup"><span data-stu-id="cc579-106">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="cc579-107">區塊範圍</span><span class="sxs-lookup"><span data-stu-id="cc579-107">Block scope</span></span>|<span data-ttu-id="cc579-108">只能在其宣告所在的程式碼區塊中使用</span><span class="sxs-lookup"><span data-stu-id="cc579-108">Available only within the code block in which it is declared</span></span>|
|<span data-ttu-id="cc579-109">程式範圍</span><span class="sxs-lookup"><span data-stu-id="cc579-109">Procedure scope</span></span>|<span data-ttu-id="cc579-110">可供宣告之程式內的所有程式碼使用</span><span class="sxs-lookup"><span data-stu-id="cc579-110">Available to all code within the procedure in which it is declared</span></span>|
|<span data-ttu-id="cc579-111">模組範圍</span><span class="sxs-lookup"><span data-stu-id="cc579-111">Module scope</span></span>|<span data-ttu-id="cc579-112">適用于其宣告所在之模組、類別或結構內的所有程式碼</span><span class="sxs-lookup"><span data-stu-id="cc579-112">Available to all code within the module, class, or structure in which it is declared</span></span>|
|<span data-ttu-id="cc579-113">命名空間範圍</span><span class="sxs-lookup"><span data-stu-id="cc579-113">Namespace scope</span></span>|<span data-ttu-id="cc579-114">可供宣告之命名空間中的所有程式碼使用</span><span class="sxs-lookup"><span data-stu-id="cc579-114">Available to all code in the namespace in which it is declared</span></span>|

<span data-ttu-id="cc579-115">從最窄 (區塊) 到最廣泛 (命名空間) 的這些範圍進度層級, 其中最*窄的範圍*表示可以參考該專案但未限定的程式碼之一集。</span><span class="sxs-lookup"><span data-stu-id="cc579-115">These levels of scope progress from the narrowest (block) to the widest (namespace), where *narrowest scope* means the smallest set of code that can refer to the element without qualification.</span></span> <span data-ttu-id="cc579-116">如需詳細資訊, 請參閱此頁面上的「範圍層級」。</span><span class="sxs-lookup"><span data-stu-id="cc579-116">For more information, see "Levels of Scope" on this page.</span></span>

## <a name="specifying-scope-and-defining-variables"></a><span data-ttu-id="cc579-117">指定範圍和定義變數</span><span class="sxs-lookup"><span data-stu-id="cc579-117">Specifying Scope and Defining Variables</span></span>

<span data-ttu-id="cc579-118">當您宣告元素時, 您可以指定專案的範圍。</span><span class="sxs-lookup"><span data-stu-id="cc579-118">You specify the scope of an element when you declare it.</span></span> <span data-ttu-id="cc579-119">範圍可以視下列因素而定:</span><span class="sxs-lookup"><span data-stu-id="cc579-119">The scope can depend on the following factors:</span></span>

- <span data-ttu-id="cc579-120">您在其中宣告元素的區域 (區塊、程式、模組、類別或結構)</span><span class="sxs-lookup"><span data-stu-id="cc579-120">The region (block, procedure, module, class, or structure) in which you declare the element</span></span>

- <span data-ttu-id="cc579-121">包含元素宣告的命名空間</span><span class="sxs-lookup"><span data-stu-id="cc579-121">The namespace containing the element's declaration</span></span>

- <span data-ttu-id="cc579-122">您為元素宣告的存取層級</span><span class="sxs-lookup"><span data-stu-id="cc579-122">The access level you declare for the element</span></span>

<span data-ttu-id="cc579-123">當您定義具有相同名稱但範圍不同的變數時, 請小心使用, 因為這樣做可能會導致非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="cc579-123">Use care when you define variables with the same name but different scope, because doing so can lead to unexpected results.</span></span> <span data-ttu-id="cc579-124">如需詳細資訊，請參閱 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)。</span><span class="sxs-lookup"><span data-stu-id="cc579-124">For more information, see [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

## <a name="levels-of-scope"></a><span data-ttu-id="cc579-125">範圍層級</span><span class="sxs-lookup"><span data-stu-id="cc579-125">Levels of Scope</span></span>

<span data-ttu-id="cc579-126">程式設計項目可在您宣告它的整個區域中使用。</span><span class="sxs-lookup"><span data-stu-id="cc579-126">A programming element is available throughout the region in which you declare it.</span></span> <span data-ttu-id="cc579-127">相同區域中的所有程式碼都可以參考該元素, 而不會限定其名稱。</span><span class="sxs-lookup"><span data-stu-id="cc579-127">All code in the same region can refer to the element without qualifying its name.</span></span>

### <a name="block-scope"></a><span data-ttu-id="cc579-128">封鎖範圍</span><span class="sxs-lookup"><span data-stu-id="cc579-128">Block Scope</span></span>

<span data-ttu-id="cc579-129">區塊是包含在起始和結束宣告語句中的一組語句, 如下所示:</span><span class="sxs-lookup"><span data-stu-id="cc579-129">A block is a set of statements enclosed within initiating and terminating declaration statements, such as the following:</span></span>

- <span data-ttu-id="cc579-130">`Do` 和 `Loop`</span><span class="sxs-lookup"><span data-stu-id="cc579-130">`Do` and `Loop`</span></span>

- <span data-ttu-id="cc579-131">`For`[`Each`] 和`Next`</span><span class="sxs-lookup"><span data-stu-id="cc579-131">`For` [`Each`] and `Next`</span></span>

- <span data-ttu-id="cc579-132">`If` 和 `End If`</span><span class="sxs-lookup"><span data-stu-id="cc579-132">`If` and `End If`</span></span>

- <span data-ttu-id="cc579-133">`Select` 和 `End Select`</span><span class="sxs-lookup"><span data-stu-id="cc579-133">`Select` and `End Select`</span></span>

- <span data-ttu-id="cc579-134">`SyncLock` 和 `End SyncLock`</span><span class="sxs-lookup"><span data-stu-id="cc579-134">`SyncLock` and `End SyncLock`</span></span>

- <span data-ttu-id="cc579-135">`Try` 和 `End Try`</span><span class="sxs-lookup"><span data-stu-id="cc579-135">`Try` and `End Try`</span></span>

- <span data-ttu-id="cc579-136">`While` 和 `End While`</span><span class="sxs-lookup"><span data-stu-id="cc579-136">`While` and `End While`</span></span>

- <span data-ttu-id="cc579-137">`With` 和 `End With`</span><span class="sxs-lookup"><span data-stu-id="cc579-137">`With` and `End With`</span></span>

<span data-ttu-id="cc579-138">如果您在區塊內宣告變數, 就只能在該區塊內使用它。</span><span class="sxs-lookup"><span data-stu-id="cc579-138">If you declare a variable within a block, you can use it only within that block.</span></span> <span data-ttu-id="cc579-139">在下列範例中, `cube`整數變數的範圍是和`End If`之間`If`的區塊`cube` , 而且當執行超出區塊時, 您就不能再參考。</span><span class="sxs-lookup"><span data-stu-id="cc579-139">In the following example, the scope of the integer variable `cube` is the block between `If` and `End If`, and you can no longer refer to `cube` when execution passes out of the block.</span></span>

```vb
If n < 1291 Then
    Dim cube As Integer
    cube = n ^ 3
End If
```

> [!NOTE]
> <span data-ttu-id="cc579-140">即使變數的範圍限制為區塊, 它的存留期仍然是整個程式的存留時間。</span><span class="sxs-lookup"><span data-stu-id="cc579-140">Even if the scope of a variable is limited to a block, its lifetime is still that of the entire procedure.</span></span> <span data-ttu-id="cc579-141">如果您在程式期間多次輸入區塊, 每個區塊變數都會保留其先前的值。</span><span class="sxs-lookup"><span data-stu-id="cc579-141">If you enter the block more than once during the procedure, each block variable retains its previous value.</span></span> <span data-ttu-id="cc579-142">為了避免這種情況發生非預期的結果, 在區塊開頭初始化區塊變數是明智的做法。</span><span class="sxs-lookup"><span data-stu-id="cc579-142">To avoid unexpected results in such a case, it is wise to initialize block variables at the beginning of the block.</span></span>

### <a name="procedure-scope"></a><span data-ttu-id="cc579-143">程式範圍</span><span class="sxs-lookup"><span data-stu-id="cc579-143">Procedure Scope</span></span>

<span data-ttu-id="cc579-144">在程式中宣告的元素無法在該程式之外使用。</span><span class="sxs-lookup"><span data-stu-id="cc579-144">An element declared within a procedure is not available outside that procedure.</span></span> <span data-ttu-id="cc579-145">只有包含宣告的程式可以使用它。</span><span class="sxs-lookup"><span data-stu-id="cc579-145">Only the procedure that contains the declaration can use it.</span></span> <span data-ttu-id="cc579-146">此層級的變數也稱為「*區域變數」 (local variables*)。</span><span class="sxs-lookup"><span data-stu-id="cc579-146">Variables at this level are also known as *local variables*.</span></span> <span data-ttu-id="cc579-147">您可以使用[Dim 語句](../../../../visual-basic/language-reference/statements/dim-statement.md)來宣告它們, 其中包含或不使用[Static](../../../../visual-basic/language-reference/modifiers/static.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="cc579-147">You declare them with the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md), with or without the [Static](../../../../visual-basic/language-reference/modifiers/static.md) keyword.</span></span>

<span data-ttu-id="cc579-148">程式與區塊領域密切相關。</span><span class="sxs-lookup"><span data-stu-id="cc579-148">Procedure and block scope are closely related.</span></span> <span data-ttu-id="cc579-149">如果您在程式中宣告變數, 但在該程式內的任何區塊外, 您可以將變數視為具有區塊範圍, 其中區塊是整個程式。</span><span class="sxs-lookup"><span data-stu-id="cc579-149">If you declare a variable inside a procedure but outside any block within that procedure, you can think of the variable as having block scope, where the block is the entire procedure.</span></span>

> [!NOTE]
> <span data-ttu-id="cc579-150">所有的本機專案 (即使是`Static`變數) 都是其出現所在程式的私用。</span><span class="sxs-lookup"><span data-stu-id="cc579-150">All local elements, even if they are `Static` variables, are private to the procedure in which they appear.</span></span> <span data-ttu-id="cc579-151">您不能在程式內使用[Public](../../../../visual-basic/language-reference/modifiers/public.md)關鍵字來宣告任何專案。</span><span class="sxs-lookup"><span data-stu-id="cc579-151">You cannot declare any element using the [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword within a procedure.</span></span>

### <a name="module-scope"></a><span data-ttu-id="cc579-152">模組範圍</span><span class="sxs-lookup"><span data-stu-id="cc579-152">Module Scope</span></span>

<span data-ttu-id="cc579-153">為了方便起見, 單一詞彙*模組層級*同樣適用于模組、類別和結構。</span><span class="sxs-lookup"><span data-stu-id="cc579-153">For convenience, the single term *module level* applies equally to modules, classes, and structures.</span></span> <span data-ttu-id="cc579-154">您可以在此層級宣告專案, 方法是將宣告語句放在任何程式或區塊的外部, 但是在模組、類別或結構中。</span><span class="sxs-lookup"><span data-stu-id="cc579-154">You can declare elements at this level by placing the declaration statement outside of any procedure or block but within the module, class, or structure.</span></span>

<span data-ttu-id="cc579-155">當您在模組層級進行宣告時, 您選擇的存取層級會決定範圍。</span><span class="sxs-lookup"><span data-stu-id="cc579-155">When you make a declaration at the module level, the access level you choose determines the scope.</span></span> <span data-ttu-id="cc579-156">包含模組、類別或結構的命名空間也會影響範圍。</span><span class="sxs-lookup"><span data-stu-id="cc579-156">The namespace that contains the module, class, or structure also affects the scope.</span></span>

<span data-ttu-id="cc579-157">您宣告[私](../../../../visual-basic/language-reference/modifiers/private.md)用存取層級的專案可用於該模組中的每個程式, 但不適用於不同模組中的任何程式碼。</span><span class="sxs-lookup"><span data-stu-id="cc579-157">Elements for which you declare [Private](../../../../visual-basic/language-reference/modifiers/private.md) access level are available to every procedure in that module, but not to any code in a different module.</span></span> <span data-ttu-id="cc579-158">如果`Dim`您未使用任何存取層`Private`級關鍵字, 則模組層級的語句會預設為。</span><span class="sxs-lookup"><span data-stu-id="cc579-158">The `Dim` statement at module level defaults to `Private` if you do not use any access level keywords.</span></span> <span data-ttu-id="cc579-159">不過, 您可以`Private` `Dim`在語句中使用關鍵字, 讓範圍和存取層級更明顯。</span><span class="sxs-lookup"><span data-stu-id="cc579-159">However, you can make the scope and access level more obvious by using the `Private` keyword in the `Dim` statement.</span></span>

<span data-ttu-id="cc579-160">在下列範例中, 模組中定義的所有程式都可以參考字串變數`strMsg`。</span><span class="sxs-lookup"><span data-stu-id="cc579-160">In the following example, all procedures defined in the module can refer to the string variable `strMsg`.</span></span> <span data-ttu-id="cc579-161">呼叫第二個程式時, 會在對話方塊中顯示字串變數`strMsg`的內容。</span><span class="sxs-lookup"><span data-stu-id="cc579-161">When the second procedure is called, it displays the contents of the string variable `strMsg` in a dialog box.</span></span>

```vb
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

### <a name="namespace-scope"></a><span data-ttu-id="cc579-162">命名空間範圍</span><span class="sxs-lookup"><span data-stu-id="cc579-162">Namespace Scope</span></span>

<span data-ttu-id="cc579-163">如果您使用[Friend](../../../../visual-basic/language-reference/modifiers/friend.md)或[Public](../../../../visual-basic/language-reference/modifiers/public.md)關鍵字在模組層級宣告專案, 它會變成可供在宣告專案之命名空間中的所有程式使用。</span><span class="sxs-lookup"><span data-stu-id="cc579-163">If you declare an element at module level using the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) or [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword, it becomes available to all procedures throughout the namespace in which the element is declared.</span></span> <span data-ttu-id="cc579-164">在上述範例中的下列變更中, 字串變數`strMsg`可以在其宣告的命名空間中的任何位置參考程式碼。</span><span class="sxs-lookup"><span data-stu-id="cc579-164">With the following alteration to the preceding example, the string variable `strMsg` can be referred to by code anywhere in the namespace of its declaration.</span></span>

```vb
' Include this declaration at module level (not inside any procedure).
Public strMsg As String
```

<span data-ttu-id="cc579-165">命名空間範圍包含嵌套的命名空間。</span><span class="sxs-lookup"><span data-stu-id="cc579-165">Namespace scope includes nested namespaces.</span></span> <span data-ttu-id="cc579-166">您也可以從命名空間內的任何命名空間中, 取得可從命名空間中取得的專案。</span><span class="sxs-lookup"><span data-stu-id="cc579-166">An element available from within a namespace is also available from within any namespace nested inside that namespace.</span></span>

<span data-ttu-id="cc579-167">如果您的專案未包含任何[命名空間語句](../../../../visual-basic/language-reference/statements/namespace-statement.md), 則專案中的所有內容都會位於相同的命名空間中。</span><span class="sxs-lookup"><span data-stu-id="cc579-167">If your project does not contain any [Namespace Statement](../../../../visual-basic/language-reference/statements/namespace-statement.md)s, everything in the project is in the same namespace.</span></span> <span data-ttu-id="cc579-168">在此情況下, 可以將命名空間範圍視為專案範圍。</span><span class="sxs-lookup"><span data-stu-id="cc579-168">In this case, namespace scope can be thought of as project scope.</span></span> <span data-ttu-id="cc579-169">`Public`模組、類別或結構中的元素也可供參考其專案的任何專案使用。</span><span class="sxs-lookup"><span data-stu-id="cc579-169">`Public` elements in a module, class, or structure are also available to any project that references their project.</span></span>

## <a name="choice-of-scope"></a><span data-ttu-id="cc579-170">選擇範圍</span><span class="sxs-lookup"><span data-stu-id="cc579-170">Choice of Scope</span></span>

<span data-ttu-id="cc579-171">當您宣告變數時, 在選擇其範圍時, 您應該記住下列幾點。</span><span class="sxs-lookup"><span data-stu-id="cc579-171">When you declare a variable, you should keep in mind the following points when choosing its scope.</span></span>

### <a name="advantages-of-local-variables"></a><span data-ttu-id="cc579-172">本機變數的優點</span><span class="sxs-lookup"><span data-stu-id="cc579-172">Advantages of Local Variables</span></span>

<span data-ttu-id="cc579-173">針對任何類型的暫時計算而言, 本機變數都是不錯的選擇, 原因如下:</span><span class="sxs-lookup"><span data-stu-id="cc579-173">Local variables are a good choice for any kind of temporary calculation, for the following reasons:</span></span>

- <span data-ttu-id="cc579-174">**避免名稱衝突。**</span><span class="sxs-lookup"><span data-stu-id="cc579-174">**Name Conflict Avoidance.**</span></span> <span data-ttu-id="cc579-175">本機變數名稱不容易發生衝突。</span><span class="sxs-lookup"><span data-stu-id="cc579-175">Local variable names are not susceptible to conflict.</span></span> <span data-ttu-id="cc579-176">例如, 您可以建立數個不同的程式, 其中包含`intTemp`名為的變數。</span><span class="sxs-lookup"><span data-stu-id="cc579-176">For example, you can create several different procedures containing a variable called `intTemp`.</span></span> <span data-ttu-id="cc579-177">只要每個`intTemp`都宣告為區域變數, 每個程式就只會辨識自己的`intTemp`版本。</span><span class="sxs-lookup"><span data-stu-id="cc579-177">As long as each `intTemp` is declared as a local variable, each procedure recognizes only its own version of `intTemp`.</span></span> <span data-ttu-id="cc579-178">任何一個程式都可以在其本機`intTemp`中改變值, 而不會影響`intTemp`其他程式中的變數。</span><span class="sxs-lookup"><span data-stu-id="cc579-178">Any one procedure can alter the value in its local `intTemp` without affecting `intTemp` variables in other procedures.</span></span>

- <span data-ttu-id="cc579-179">**記憶體耗用量。**</span><span class="sxs-lookup"><span data-stu-id="cc579-179">**Memory Consumption.**</span></span> <span data-ttu-id="cc579-180">本機變數只有在其程式正在執行時才會耗用記憶體。</span><span class="sxs-lookup"><span data-stu-id="cc579-180">Local variables consume memory only while their procedure is running.</span></span> <span data-ttu-id="cc579-181">當程式返回呼叫的程式碼時, 就會釋放其記憶體。</span><span class="sxs-lookup"><span data-stu-id="cc579-181">Their memory is released when the procedure returns to the calling code.</span></span> <span data-ttu-id="cc579-182">相反地,[共用](../../../../visual-basic/language-reference/modifiers/shared.md)和[靜態](../../../../visual-basic/language-reference/modifiers/static.md)變數會耗用記憶體資源, 直到您的應用程式停止執行為止, 因此只有在必要時才使用它們。</span><span class="sxs-lookup"><span data-stu-id="cc579-182">By contrast, [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) and [Static](../../../../visual-basic/language-reference/modifiers/static.md) variables consume memory resources until your application stops running, so use them only when necessary.</span></span> <span data-ttu-id="cc579-183">*執行個體變數*會耗用記憶體, 而其實例會繼續存在, 讓它們比區域變數更有效率, 但可能比`Shared`或`Static`變數更有效率。</span><span class="sxs-lookup"><span data-stu-id="cc579-183">*Instance variables* consume memory while their instance continues to exist, which makes them less efficient than local variables, but potentially more efficient than `Shared` or `Static` variables.</span></span>

### <a name="minimizing-scope"></a><span data-ttu-id="cc579-184">最小化範圍</span><span class="sxs-lookup"><span data-stu-id="cc579-184">Minimizing Scope</span></span>

<span data-ttu-id="cc579-185">一般來說, 在宣告任何變數或常數時, 最好的程式設計作法是讓範圍盡可能縮小 (區塊範圍是最窄的)。</span><span class="sxs-lookup"><span data-stu-id="cc579-185">In general, when declaring any variable or constant, it is good programming practice to make the scope as narrow as possible (block scope is the narrowest).</span></span> <span data-ttu-id="cc579-186">這有助於節省記憶體, 並將程式碼錯誤地參考錯誤變數的機率降到最低。</span><span class="sxs-lookup"><span data-stu-id="cc579-186">This helps conserve memory and minimizes the chances of your code erroneously referring to the wrong variable.</span></span> <span data-ttu-id="cc579-187">同樣地, 您應該將變數宣告為[靜態](../../../../visual-basic/language-reference/modifiers/static.md), 只有在必要時, 才必須在程序呼叫之間保留其值。</span><span class="sxs-lookup"><span data-stu-id="cc579-187">Similarly, you should declare a variable to be [Static](../../../../visual-basic/language-reference/modifiers/static.md) only when it is necessary to preserve its value between procedure calls.</span></span>

## <a name="see-also"></a><span data-ttu-id="cc579-188">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc579-188">See also</span></span>

- [<span data-ttu-id="cc579-189">宣告項目特性</span><span class="sxs-lookup"><span data-stu-id="cc579-189">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="cc579-190">如何：控制變數的範圍</span><span class="sxs-lookup"><span data-stu-id="cc579-190">How to: Control the Scope of a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)
- [<span data-ttu-id="cc579-191">Visual Basic 中的存留期</span><span class="sxs-lookup"><span data-stu-id="cc579-191">Lifetime in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="cc579-192">Visual Basic 中的存取層級</span><span class="sxs-lookup"><span data-stu-id="cc579-192">Access levels in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="cc579-193">對已宣告項目的參考</span><span class="sxs-lookup"><span data-stu-id="cc579-193">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="cc579-194">變數宣告</span><span class="sxs-lookup"><span data-stu-id="cc579-194">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
