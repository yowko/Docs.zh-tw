---
title: Shared (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Shared
helpviewer_keywords:
- Shared keyword [Visual Basic]
- members [Visual Basic], shared
- shared members
- nonshared
- shared [elements VB]
- elements [Visual Basic], shared
ms.assetid: 2bf7cf2c-b0dd-485e-8749-b5d674dab4cd
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fce13c308a449e63eacc2bc4c94c274c7e25506a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="shared-visual-basic"></a><span data-ttu-id="cccf2-102">Shared (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cccf2-102">Shared (Visual Basic)</span></span>
<span data-ttu-id="cccf2-103">指定一或多個宣告的程式設計項目相關聯的類別或結構，而不在類別或結構的特定執行個體。</span><span class="sxs-lookup"><span data-stu-id="cccf2-103">Specifies that one or more declared programming elements are associated with a class or structure at large, and not with a specific instance of the class or structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cccf2-104">備註</span><span class="sxs-lookup"><span data-stu-id="cccf2-104">Remarks</span></span>  
  
## <a name="when-to-use-shared"></a><span data-ttu-id="cccf2-105">何時使用共用</span><span class="sxs-lookup"><span data-stu-id="cccf2-105">When to Use Shared</span></span>  
 <span data-ttu-id="cccf2-106">共用的類別或結構成員會使其可使用每個執行個體，而非*非共用*、 其中的每個執行個體保留其自己的複本。</span><span class="sxs-lookup"><span data-stu-id="cccf2-106">Sharing a member of a class or structure makes it available to every instance, rather than *nonshared*, where each instance keeps its own copy.</span></span> <span data-ttu-id="cccf2-107">這非常有用，例如，如果變數的值套用至整個應用程式。</span><span class="sxs-lookup"><span data-stu-id="cccf2-107">This is useful, for example, if the value of a variable applies to the entire application.</span></span> <span data-ttu-id="cccf2-108">如果您宣告該變數`Shared`、 所有執行個體存取相同的儲存位置，和一個執行個體變更變數的值，如果所有執行個體存取更新的值。</span><span class="sxs-lookup"><span data-stu-id="cccf2-108">If you declare that variable to be `Shared`, then all instances access the same storage location, and if one instance changes the variable's value, all instances access the updated value.</span></span>  
  
 <span data-ttu-id="cccf2-109">共用並不會改變成員的存取層級。</span><span class="sxs-lookup"><span data-stu-id="cccf2-109">Sharing does not alter the access level of a member.</span></span> <span data-ttu-id="cccf2-110">比方說，您可以共用的類別成員和私用 （只能從存取類別內），或非共用及公用。</span><span class="sxs-lookup"><span data-stu-id="cccf2-110">For example, a class member can be shared and private (accessible only from within the class), or nonshared and public.</span></span> <span data-ttu-id="cccf2-111">如需詳細資訊，請參閱[存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="cccf2-111">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="cccf2-112">規則</span><span class="sxs-lookup"><span data-stu-id="cccf2-112">Rules</span></span>  
  
-   <span data-ttu-id="cccf2-113">**宣告內容。**</span><span class="sxs-lookup"><span data-stu-id="cccf2-113">**Declaration Context.**</span></span> <span data-ttu-id="cccf2-114">您只能在模組層級使用 `Shared`。</span><span class="sxs-lookup"><span data-stu-id="cccf2-114">You can use `Shared` only at module level.</span></span> <span data-ttu-id="cccf2-115">這表示宣告內容`Shared`項目必須是類別或結構，並不能是原始程式檔、 命名空間或程序。</span><span class="sxs-lookup"><span data-stu-id="cccf2-115">This means the declaration context for a `Shared` element must be a class or structure, and cannot be a source file, namespace, or procedure.</span></span>  
  
-   <span data-ttu-id="cccf2-116">**結合的修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="cccf2-116">**Combined Modifiers.**</span></span> <span data-ttu-id="cccf2-117">您無法指定`Shared`搭配[會覆寫](../../../visual-basic/language-reference/modifiers/overrides.md)， [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)， [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)， [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)，或[靜態](../../../visual-basic/language-reference/modifiers/static.md)相同宣告中。</span><span class="sxs-lookup"><span data-stu-id="cccf2-117">You cannot specify `Shared` together with [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md), [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md), or [Static](../../../visual-basic/language-reference/modifiers/static.md) in the same declaration.</span></span>  
  
-   <span data-ttu-id="cccf2-118">**存取。**</span><span class="sxs-lookup"><span data-stu-id="cccf2-118">**Accessing.**</span></span> <span data-ttu-id="cccf2-119">您可以限定其名稱與其類別或結構的名稱，而非其類別或結構的特定執行個體的變數名稱存取共用項目。</span><span class="sxs-lookup"><span data-stu-id="cccf2-119">You access a shared element by qualifying it with its class or structure name, not with the variable name of a specific instance of its class or structure.</span></span> <span data-ttu-id="cccf2-120">您甚至不必建立類別或結構，以存取其共用的成員的執行個體。</span><span class="sxs-lookup"><span data-stu-id="cccf2-120">You do not even have to create an instance of a class or structure to access its shared members.</span></span>  
  
     <span data-ttu-id="cccf2-121">下列範例會呼叫共用的程序<xref:System.Double.IsNaN%2A>所公開<xref:System.Double>結構。</span><span class="sxs-lookup"><span data-stu-id="cccf2-121">The following example calls the shared procedure <xref:System.Double.IsNaN%2A> exposed by the <xref:System.Double> structure.</span></span>  
  
     `If Double.IsNaN(result) Then MsgBox("Result is mathematically undefined.")`  
  
-   <span data-ttu-id="cccf2-122">**隱含的共用。**</span><span class="sxs-lookup"><span data-stu-id="cccf2-122">**Implicit Sharing.**</span></span> <span data-ttu-id="cccf2-123">您無法使用`Shared`修飾詞[Const 陳述式](../../../visual-basic/language-reference/statements/const-statement.md)，但是常數會隱含地共用。</span><span class="sxs-lookup"><span data-stu-id="cccf2-123">You cannot use the `Shared` modifier in a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md), but constants are implicitly shared.</span></span> <span data-ttu-id="cccf2-124">同樣地，您無法宣告指向成員的模組或介面`Shared`，但是隱含共用它們。</span><span class="sxs-lookup"><span data-stu-id="cccf2-124">Similarly, you cannot declare a member of a module or an interface to be `Shared`, but they are implicitly shared.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="cccf2-125">行為</span><span class="sxs-lookup"><span data-stu-id="cccf2-125">Behavior</span></span>  
  
-   <span data-ttu-id="cccf2-126">**儲存體。**</span><span class="sxs-lookup"><span data-stu-id="cccf2-126">**Storage.**</span></span> <span data-ttu-id="cccf2-127">共用的變數或事件會儲存在記憶體中一次，不論多少個執行個體建立其類別或結構。</span><span class="sxs-lookup"><span data-stu-id="cccf2-127">A shared variable or event is stored in memory only once, no matter how many or few instances you create of its class or structure.</span></span> <span data-ttu-id="cccf2-128">同樣地，共用的程序或屬性會保存只有一個本機變數的集合。</span><span class="sxs-lookup"><span data-stu-id="cccf2-128">Similarly, a shared procedure or property holds only one set of local variables.</span></span>  
  
-   <span data-ttu-id="cccf2-129">**透過執行個體變數存取。**</span><span class="sxs-lookup"><span data-stu-id="cccf2-129">**Accessing through an Instance Variable.**</span></span> <span data-ttu-id="cccf2-130">您可存取共用項目來限定變數，內含其類別或結構的特定執行個體的名稱取代。</span><span class="sxs-lookup"><span data-stu-id="cccf2-130">It is possible to access a shared element by qualifying it with the name of a variable that contains a specific instance of its class or structure.</span></span> <span data-ttu-id="cccf2-131">雖然這通常在如預期般運作，編譯器會產生警告訊息，而且會透過類別或結構名稱，而不是變數的存取權。</span><span class="sxs-lookup"><span data-stu-id="cccf2-131">Although this usually works as expected, the compiler generates a warning message and makes the access through the class or structure name instead of the variable.</span></span>  
  
-   <span data-ttu-id="cccf2-132">**透過執行個體運算式存取。**</span><span class="sxs-lookup"><span data-stu-id="cccf2-132">**Accessing through an Instance Expression.**</span></span> <span data-ttu-id="cccf2-133">如果您是透過傳回其類別或結構的執行個體的運算式存取共用項目，編譯器會透過類別或結構名稱，而不是評估運算式的存取權。</span><span class="sxs-lookup"><span data-stu-id="cccf2-133">If you access a shared element through an expression that returns an instance of its class or structure, the compiler makes the access through the class or structure name instead of evaluating the expression.</span></span> <span data-ttu-id="cccf2-134">如果您想要執行其他動作，以及傳回執行個體的運算式，這會產生非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="cccf2-134">This produces unexpected results if you intended the expression to perform other actions as well as returning the instance.</span></span> <span data-ttu-id="cccf2-135">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="cccf2-135">The following example illustrates this.</span></span>  
  
    ```  
    Sub main()  
        shareTotal.total = 10  
        ' The preceding line is the preferred way to access total.  
        Dim instanceVar As New shareTotal  
        instanceVar.total += 100  
        ' The preceding line generates a compiler warning message and  
        ' accesses total through class shareTotal instead of through  
        ' the variable instanceVar. This works as expected and adds  
        ' 100 to total.  
        returnClass().total += 1000  
        ' The preceding line generates a compiler warning message and  
        ' accesses total through class shareTotal instead of calling  
        ' returnClass(). This adds 1000 to total but does not work as  
        ' expected, because the MsgBox in returnClass() does not run.  
        MsgBox("Value of total is " & CStr(shareTotal.total))  
    End Sub  
    Public Function returnClass() As shareTotal  
        MsgBox("Function returnClass() called")  
        Return New shareTotal  
    End Function  
    Public Class shareTotal  
        Public Shared total As Integer  
    End Class  
    ```  
  
     <span data-ttu-id="cccf2-136">在上述範例中，編譯器會產生一則警告訊息的程式碼會存取共用的變數這兩個時間`total`透過執行個體。</span><span class="sxs-lookup"><span data-stu-id="cccf2-136">In the preceding example, the compiler generates a warning message both times the code accesses the shared variable `total` through an instance.</span></span> <span data-ttu-id="cccf2-137">在每個案例會透過類別的直接存取`shareTotal`而且也不會使用任何執行個體。</span><span class="sxs-lookup"><span data-stu-id="cccf2-137">In each case it makes the access directly through the class `shareTotal` and does not make use of any instance.</span></span> <span data-ttu-id="cccf2-138">在預期的呼叫程序的情況下`returnClass`，這表示它甚至不會產生呼叫`returnClass`，因此不會執行其他動作的顯示"呼叫的函式 returnClass()"。</span><span class="sxs-lookup"><span data-stu-id="cccf2-138">In the case of the intended call to the procedure `returnClass`, this means it does not even generate a call to `returnClass`, so the additional action of displaying "Function returnClass() called" is not performed.</span></span>  
  
 <span data-ttu-id="cccf2-139">`Shared` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="cccf2-139">The `Shared` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="cccf2-140">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="cccf2-140">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="cccf2-141">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="cccf2-141">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="cccf2-142">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="cccf2-142">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="cccf2-143">Operator 陳述式</span><span class="sxs-lookup"><span data-stu-id="cccf2-143">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="cccf2-144">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="cccf2-144">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="cccf2-145">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="cccf2-145">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="cccf2-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cccf2-146">See Also</span></span>  
 [<span data-ttu-id="cccf2-147">Shadows</span><span class="sxs-lookup"><span data-stu-id="cccf2-147">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="cccf2-148">Static</span><span class="sxs-lookup"><span data-stu-id="cccf2-148">Static</span></span>](../../../visual-basic/language-reference/modifiers/static.md)  
 [<span data-ttu-id="cccf2-149">在 Visual Basic 中的存留期</span><span class="sxs-lookup"><span data-stu-id="cccf2-149">Lifetime in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [<span data-ttu-id="cccf2-150">程序</span><span class="sxs-lookup"><span data-stu-id="cccf2-150">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="cccf2-151">結構</span><span class="sxs-lookup"><span data-stu-id="cccf2-151">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="cccf2-152">物件和類別</span><span class="sxs-lookup"><span data-stu-id="cccf2-152">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
