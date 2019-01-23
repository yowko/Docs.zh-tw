---
title: Shared (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Shared
helpviewer_keywords:
- Shared keyword [Visual Basic]
- members [Visual Basic], shared
- shared members
- nonshared
- shared [elements VB]
- elements [Visual Basic], shared
ms.assetid: 2bf7cf2c-b0dd-485e-8749-b5d674dab4cd
ms.openlocfilehash: 001baa8d3cbd294772bef634825c67ea13b23458
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597277"
---
# <a name="shared-visual-basic"></a><span data-ttu-id="d143f-102">Shared (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d143f-102">Shared (Visual Basic)</span></span>
<span data-ttu-id="d143f-103">指定一或多個宣告的程式設計項目與類別或結構的大規模，而非與該類別或結構的特定執行個體相關聯。</span><span class="sxs-lookup"><span data-stu-id="d143f-103">Specifies that one or more declared programming elements are associated with a class or structure at large, and not with a specific instance of the class or structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d143f-104">備註</span><span class="sxs-lookup"><span data-stu-id="d143f-104">Remarks</span></span>  
  
## <a name="when-to-use-shared"></a><span data-ttu-id="d143f-105">何時使用共用</span><span class="sxs-lookup"><span data-stu-id="d143f-105">When to Use Shared</span></span>  
 <span data-ttu-id="d143f-106">共用的類別或結構成員會將其提供給每個執行個體，而非*非共用*、 其中的每個執行個體保留它自己的複本。</span><span class="sxs-lookup"><span data-stu-id="d143f-106">Sharing a member of a class or structure makes it available to every instance, rather than *nonshared*, where each instance keeps its own copy.</span></span> <span data-ttu-id="d143f-107">例如，如果變數的值會套用到整個應用程式，這十分有用。</span><span class="sxs-lookup"><span data-stu-id="d143f-107">This is useful, for example, if the value of a variable applies to the entire application.</span></span> <span data-ttu-id="d143f-108">如果您宣告該變數`Shared`、 然後所有執行個體存取相同的儲存體位置，以及如果一個執行個體變更變數的值，所有執行個體存取更新的值。</span><span class="sxs-lookup"><span data-stu-id="d143f-108">If you declare that variable to be `Shared`, then all instances access the same storage location, and if one instance changes the variable's value, all instances access the updated value.</span></span>  
  
 <span data-ttu-id="d143f-109">共用時，不會更改成員的存取層級。</span><span class="sxs-lookup"><span data-stu-id="d143f-109">Sharing does not alter the access level of a member.</span></span> <span data-ttu-id="d143f-110">例如，可共用的類別成員和私用 （只能從存取類別內），或非共用和公用。</span><span class="sxs-lookup"><span data-stu-id="d143f-110">For example, a class member can be shared and private (accessible only from within the class), or nonshared and public.</span></span> <span data-ttu-id="d143f-111">如需詳細資訊，請參閱 <<c0> [ 存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="d143f-111">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="d143f-112">規則</span><span class="sxs-lookup"><span data-stu-id="d143f-112">Rules</span></span>  
  
-   <span data-ttu-id="d143f-113">**宣告內容。**</span><span class="sxs-lookup"><span data-stu-id="d143f-113">**Declaration Context.**</span></span> <span data-ttu-id="d143f-114">您只能在模組層級使用 `Shared`。</span><span class="sxs-lookup"><span data-stu-id="d143f-114">You can use `Shared` only at module level.</span></span> <span data-ttu-id="d143f-115">這表示的宣告內容`Shared`項目必須是類別或結構，並不能是原始程式檔、 命名空間或程序。</span><span class="sxs-lookup"><span data-stu-id="d143f-115">This means the declaration context for a `Shared` element must be a class or structure, and cannot be a source file, namespace, or procedure.</span></span>  
  
-   <span data-ttu-id="d143f-116">**結合的修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="d143f-116">**Combined Modifiers.**</span></span> <span data-ttu-id="d143f-117">您無法指定`Shared`連同[覆寫](../../../visual-basic/language-reference/modifiers/overrides.md)， [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)， [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)， [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)，或[靜態](../../../visual-basic/language-reference/modifiers/static.md)相同宣告中。</span><span class="sxs-lookup"><span data-stu-id="d143f-117">You cannot specify `Shared` together with [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md), [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md), or [Static](../../../visual-basic/language-reference/modifiers/static.md) in the same declaration.</span></span>  
  
-   <span data-ttu-id="d143f-118">**存取。**</span><span class="sxs-lookup"><span data-stu-id="d143f-118">**Accessing.**</span></span> <span data-ttu-id="d143f-119">您可以限定其名稱與其類別或結構的名稱，而非與特定的執行個體，其類別或結構的變數名稱，以存取共用的項目。</span><span class="sxs-lookup"><span data-stu-id="d143f-119">You access a shared element by qualifying it with its class or structure name, not with the variable name of a specific instance of its class or structure.</span></span> <span data-ttu-id="d143f-120">您甚至不必建立的類別或結構，以存取其共用的成員執行個體。</span><span class="sxs-lookup"><span data-stu-id="d143f-120">You do not even have to create an instance of a class or structure to access its shared members.</span></span>  
  
     <span data-ttu-id="d143f-121">下列範例會呼叫共用的程序<xref:System.Double.IsNaN%2A>由<xref:System.Double>結構。</span><span class="sxs-lookup"><span data-stu-id="d143f-121">The following example calls the shared procedure <xref:System.Double.IsNaN%2A> exposed by the <xref:System.Double> structure.</span></span>  
  
     `If Double.IsNaN(result) Then MsgBox("Result is mathematically undefined.")`  
  
-   <span data-ttu-id="d143f-122">**隱含的共用。**</span><span class="sxs-lookup"><span data-stu-id="d143f-122">**Implicit Sharing.**</span></span> <span data-ttu-id="d143f-123">您無法使用`Shared`修飾詞[Const 陳述式](../../../visual-basic/language-reference/statements/const-statement.md)，但是常數會以隱含方式共用。</span><span class="sxs-lookup"><span data-stu-id="d143f-123">You cannot use the `Shared` modifier in a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md), but constants are implicitly shared.</span></span> <span data-ttu-id="d143f-124">同樣地，您無法在此宣告的模組或介面成員，才能被`Shared`，但它們會以隱含方式共用。</span><span class="sxs-lookup"><span data-stu-id="d143f-124">Similarly, you cannot declare a member of a module or an interface to be `Shared`, but they are implicitly shared.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="d143f-125">行為</span><span class="sxs-lookup"><span data-stu-id="d143f-125">Behavior</span></span>  
  
-   <span data-ttu-id="d143f-126">**儲存體。**</span><span class="sxs-lookup"><span data-stu-id="d143f-126">**Storage.**</span></span> <span data-ttu-id="d143f-127">共用的變數或事件會儲存在記憶體中一次，不論多少個執行個體建立其類別或結構。</span><span class="sxs-lookup"><span data-stu-id="d143f-127">A shared variable or event is stored in memory only once, no matter how many or few instances you create of its class or structure.</span></span> <span data-ttu-id="d143f-128">同樣地，共用的程序或屬性會保留只有一組本機變數。</span><span class="sxs-lookup"><span data-stu-id="d143f-128">Similarly, a shared procedure or property holds only one set of local variables.</span></span>  
  
-   <span data-ttu-id="d143f-129">**透過執行個體變數存取。**</span><span class="sxs-lookup"><span data-stu-id="d143f-129">**Accessing through an Instance Variable.**</span></span> <span data-ttu-id="d143f-130">可以限定其名稱的變數，包含其類別或結構的特定執行個體的名稱來存取共用的項目。</span><span class="sxs-lookup"><span data-stu-id="d143f-130">It is possible to access a shared element by qualifying it with the name of a variable that contains a specific instance of its class or structure.</span></span> <span data-ttu-id="d143f-131">雖然這通常在如預期般運作，編譯器會產生一則警告訊息，並可透過類別或結構名稱，而不是變數的存取權。</span><span class="sxs-lookup"><span data-stu-id="d143f-131">Although this usually works as expected, the compiler generates a warning message and makes the access through the class or structure name instead of the variable.</span></span>  
  
-   <span data-ttu-id="d143f-132">**透過執行個體運算式的存取。**</span><span class="sxs-lookup"><span data-stu-id="d143f-132">**Accessing through an Instance Expression.**</span></span> <span data-ttu-id="d143f-133">如果您透過該運算式會傳回其類別或結構的執行個體存取共用的項目，編譯器就會進行與存取的類別或結構的名稱，而不是評估運算式。</span><span class="sxs-lookup"><span data-stu-id="d143f-133">If you access a shared element through an expression that returns an instance of its class or structure, the compiler makes the access through the class or structure name instead of evaluating the expression.</span></span> <span data-ttu-id="d143f-134">如果您想要執行其他動作，以及傳回執行個體的運算式，這會產生非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="d143f-134">This produces unexpected results if you intended the expression to perform other actions as well as returning the instance.</span></span> <span data-ttu-id="d143f-135">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="d143f-135">The following example illustrates this.</span></span>  
  
    ```vb
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
  
     <span data-ttu-id="d143f-136">在上述範例中，編譯器會產生一則警告訊息的程式碼會存取共用的變數這兩個時間`total`透過執行個體。</span><span class="sxs-lookup"><span data-stu-id="d143f-136">In the preceding example, the compiler generates a warning message both times the code accesses the shared variable `total` through an instance.</span></span> <span data-ttu-id="d143f-137">它可讓每個案例中透過類別直接存取`shareTotal`，而且使用的任何執行個體。</span><span class="sxs-lookup"><span data-stu-id="d143f-137">In each case it makes the access directly through the class `shareTotal` and does not make use of any instance.</span></span> <span data-ttu-id="d143f-138">在程序想要呼叫的情況下`returnClass`，這表示它甚至不會產生呼叫`returnClass`，因此不會執行其他動作，顯示 「 呼叫函式 returnClass()"。</span><span class="sxs-lookup"><span data-stu-id="d143f-138">In the case of the intended call to the procedure `returnClass`, this means it does not even generate a call to `returnClass`, so the additional action of displaying "Function returnClass() called" is not performed.</span></span>  
  
 <span data-ttu-id="d143f-139">`Shared` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="d143f-139">The `Shared` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="d143f-140">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="d143f-140">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="d143f-141">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="d143f-141">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="d143f-142">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="d143f-142">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="d143f-143">Operator 陳述式</span><span class="sxs-lookup"><span data-stu-id="d143f-143">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="d143f-144">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="d143f-144">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="d143f-145">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="d143f-145">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="d143f-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d143f-146">See also</span></span>
- [<span data-ttu-id="d143f-147">Shadows</span><span class="sxs-lookup"><span data-stu-id="d143f-147">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="d143f-148">Static</span><span class="sxs-lookup"><span data-stu-id="d143f-148">Static</span></span>](../../../visual-basic/language-reference/modifiers/static.md)
- [<span data-ttu-id="d143f-149">在 Visual Basic 中的存留期</span><span class="sxs-lookup"><span data-stu-id="d143f-149">Lifetime in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="d143f-150">程序</span><span class="sxs-lookup"><span data-stu-id="d143f-150">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="d143f-151">結構</span><span class="sxs-lookup"><span data-stu-id="d143f-151">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="d143f-152">物件和類別</span><span class="sxs-lookup"><span data-stu-id="d143f-152">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
