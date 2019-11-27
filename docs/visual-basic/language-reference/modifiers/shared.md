---
title: Shared
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
ms.openlocfilehash: 98fa25d2283408dfb80e82fbc620a1b284e5c530
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349121"
---
# <a name="shared-visual-basic"></a><span data-ttu-id="11ad8-102">Shared (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11ad8-102">Shared (Visual Basic)</span></span>
<span data-ttu-id="11ad8-103">指定一或多個宣告的程式設計專案與大型的類別或結構相關聯，而不是與類別或結構的特定實例產生關聯。</span><span class="sxs-lookup"><span data-stu-id="11ad8-103">Specifies that one or more declared programming elements are associated with a class or structure at large, and not with a specific instance of the class or structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11ad8-104">備註</span><span class="sxs-lookup"><span data-stu-id="11ad8-104">Remarks</span></span>  
  
## <a name="when-to-use-shared"></a><span data-ttu-id="11ad8-105">使用 Shared 的時機</span><span class="sxs-lookup"><span data-stu-id="11ad8-105">When to Use Shared</span></span>  
 <span data-ttu-id="11ad8-106">共用類別或結構的成員，可讓每個實例（而不是*共用*）使用，而每個實例會保留自己的複本。</span><span class="sxs-lookup"><span data-stu-id="11ad8-106">Sharing a member of a class or structure makes it available to every instance, rather than *nonshared*, where each instance keeps its own copy.</span></span> <span data-ttu-id="11ad8-107">例如，如果變數的值適用于整個應用程式，這就很有用。</span><span class="sxs-lookup"><span data-stu-id="11ad8-107">This is useful, for example, if the value of a variable applies to the entire application.</span></span> <span data-ttu-id="11ad8-108">如果您將該變數宣告為 `Shared`，則所有實例都會存取相同的儲存位置，而如果一個實例變更變數的值，所有實例都會存取更新的值。</span><span class="sxs-lookup"><span data-stu-id="11ad8-108">If you declare that variable to be `Shared`, then all instances access the same storage location, and if one instance changes the variable's value, all instances access the updated value.</span></span>  
  
 <span data-ttu-id="11ad8-109">共用不會改變成員的存取層級。</span><span class="sxs-lookup"><span data-stu-id="11ad8-109">Sharing does not alter the access level of a member.</span></span> <span data-ttu-id="11ad8-110">例如，類別成員可以是共用和私用（只能從類別記憶體取），或非共用和公用。</span><span class="sxs-lookup"><span data-stu-id="11ad8-110">For example, a class member can be shared and private (accessible only from within the class), or nonshared and public.</span></span> <span data-ttu-id="11ad8-111">如需詳細資訊，請參閱[Visual Basic 中的存取層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="11ad8-111">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="11ad8-112">規則</span><span class="sxs-lookup"><span data-stu-id="11ad8-112">Rules</span></span>  
  
- <span data-ttu-id="11ad8-113">**宣告內容。**</span><span class="sxs-lookup"><span data-stu-id="11ad8-113">**Declaration Context.**</span></span> <span data-ttu-id="11ad8-114">您只能在模組層級使用 `Shared`。</span><span class="sxs-lookup"><span data-stu-id="11ad8-114">You can use `Shared` only at module level.</span></span> <span data-ttu-id="11ad8-115">這表示 `Shared` 元素的宣告內容必須是類別或結構，而且不能是原始程式檔、命名空間或程式。</span><span class="sxs-lookup"><span data-stu-id="11ad8-115">This means the declaration context for a `Shared` element must be a class or structure, and cannot be a source file, namespace, or procedure.</span></span>  
  
- <span data-ttu-id="11ad8-116">**合併的修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="11ad8-116">**Combined Modifiers.**</span></span> <span data-ttu-id="11ad8-117">您不能在相同的宣告中[，同時](../../../visual-basic/language-reference/modifiers/overridable.md)使用[覆寫](../../../visual-basic/language-reference/modifiers/overrides.md)、可覆寫、 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)、 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)或[靜態](../../../visual-basic/language-reference/modifiers/static.md)來指定 `Shared`。</span><span class="sxs-lookup"><span data-stu-id="11ad8-117">You cannot specify `Shared` together with [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md), [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md), or [Static](../../../visual-basic/language-reference/modifiers/static.md) in the same declaration.</span></span>  
  
- <span data-ttu-id="11ad8-118">**正在.**</span><span class="sxs-lookup"><span data-stu-id="11ad8-118">**Accessing.**</span></span> <span data-ttu-id="11ad8-119">您可以存取共用專案，方法是以其類別或結構名稱加以限定，而不是使用其類別或結構之特定實例的變數名稱。</span><span class="sxs-lookup"><span data-stu-id="11ad8-119">You access a shared element by qualifying it with its class or structure name, not with the variable name of a specific instance of its class or structure.</span></span> <span data-ttu-id="11ad8-120">您甚至不需要建立類別或結構的實例來存取其共用成員。</span><span class="sxs-lookup"><span data-stu-id="11ad8-120">You do not even have to create an instance of a class or structure to access its shared members.</span></span>  
  
     <span data-ttu-id="11ad8-121">下列範例會呼叫共用程式 <xref:System.Double.IsNaN%2A> 由 <xref:System.Double> 結構所公開。</span><span class="sxs-lookup"><span data-stu-id="11ad8-121">The following example calls the shared procedure <xref:System.Double.IsNaN%2A> exposed by the <xref:System.Double> structure.</span></span>  
  
     `If Double.IsNaN(result) Then MsgBox("Result is mathematically undefined.")`  
  
- <span data-ttu-id="11ad8-122">**隱含共用。**</span><span class="sxs-lookup"><span data-stu-id="11ad8-122">**Implicit Sharing.**</span></span> <span data-ttu-id="11ad8-123">您不能在[Const 語句](../../../visual-basic/language-reference/statements/const-statement.md)中使用 `Shared` 修飾詞，但會隱含地共用常數。</span><span class="sxs-lookup"><span data-stu-id="11ad8-123">You cannot use the `Shared` modifier in a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md), but constants are implicitly shared.</span></span> <span data-ttu-id="11ad8-124">同樣地，您無法將模組或介面的成員宣告為 `Shared`，但它們會隱含共用。</span><span class="sxs-lookup"><span data-stu-id="11ad8-124">Similarly, you cannot declare a member of a module or an interface to be `Shared`, but they are implicitly shared.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="11ad8-125">行為</span><span class="sxs-lookup"><span data-stu-id="11ad8-125">Behavior</span></span>  
  
- <span data-ttu-id="11ad8-126">**容量.**</span><span class="sxs-lookup"><span data-stu-id="11ad8-126">**Storage.**</span></span> <span data-ttu-id="11ad8-127">共用變數或事件只會儲存一次，無論您建立類別或結構的實例有多少或數個。</span><span class="sxs-lookup"><span data-stu-id="11ad8-127">A shared variable or event is stored in memory only once, no matter how many or few instances you create of its class or structure.</span></span> <span data-ttu-id="11ad8-128">同樣地，共用程式或屬性只會保留一組本機變數。</span><span class="sxs-lookup"><span data-stu-id="11ad8-128">Similarly, a shared procedure or property holds only one set of local variables.</span></span>  
  
- <span data-ttu-id="11ad8-129">**透過執行個體變數存取。**</span><span class="sxs-lookup"><span data-stu-id="11ad8-129">**Accessing through an Instance Variable.**</span></span> <span data-ttu-id="11ad8-130">藉由使用包含其類別或結構之特定實例的變數名稱來限定共用專案，可以存取該元素。</span><span class="sxs-lookup"><span data-stu-id="11ad8-130">It is possible to access a shared element by qualifying it with the name of a variable that contains a specific instance of its class or structure.</span></span> <span data-ttu-id="11ad8-131">雖然這通常會如預期般運作，但編譯器會產生警告訊息，並透過類別或結構名稱而不是變數來進行存取。</span><span class="sxs-lookup"><span data-stu-id="11ad8-131">Although this usually works as expected, the compiler generates a warning message and makes the access through the class or structure name instead of the variable.</span></span>  
  
- <span data-ttu-id="11ad8-132">**透過實例運算式來存取。**</span><span class="sxs-lookup"><span data-stu-id="11ad8-132">**Accessing through an Instance Expression.**</span></span> <span data-ttu-id="11ad8-133">如果您透過傳回其類別或結構實例的運算式來存取共用專案，編譯器會透過類別或結構名稱進行存取，而不會評估運算式。</span><span class="sxs-lookup"><span data-stu-id="11ad8-133">If you access a shared element through an expression that returns an instance of its class or structure, the compiler makes the access through the class or structure name instead of evaluating the expression.</span></span> <span data-ttu-id="11ad8-134">如果您想要運算式來執行其他動作以及傳回實例，這會產生非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="11ad8-134">This produces unexpected results if you intended the expression to perform other actions as well as returning the instance.</span></span> <span data-ttu-id="11ad8-135">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="11ad8-135">The following example illustrates this.</span></span>  
  
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
  
     <span data-ttu-id="11ad8-136">在上述範例中，編譯器會同時產生一則警告訊息，這兩次程式碼都會透過實例來存取共用變數 `total`。</span><span class="sxs-lookup"><span data-stu-id="11ad8-136">In the preceding example, the compiler generates a warning message both times the code accesses the shared variable `total` through an instance.</span></span> <span data-ttu-id="11ad8-137">在每個案例中，它會直接透過類別 `shareTotal` 存取，而不會使用任何實例。</span><span class="sxs-lookup"><span data-stu-id="11ad8-137">In each case it makes the access directly through the class `shareTotal` and does not make use of any instance.</span></span> <span data-ttu-id="11ad8-138">在對程式 `returnClass`的預期呼叫中，這表示它甚至不會產生 `returnClass`的呼叫，因此不會執行顯示 "Function returnClass （）的其他動作。</span><span class="sxs-lookup"><span data-stu-id="11ad8-138">In the case of the intended call to the procedure `returnClass`, this means it does not even generate a call to `returnClass`, so the additional action of displaying "Function returnClass() called" is not performed.</span></span>  
  
 <span data-ttu-id="11ad8-139">`Shared` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="11ad8-139">The `Shared` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="11ad8-140">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="11ad8-140">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="11ad8-141">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="11ad8-141">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="11ad8-142">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="11ad8-142">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="11ad8-143">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="11ad8-143">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="11ad8-144">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="11ad8-144">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="11ad8-145">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="11ad8-145">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="11ad8-146">請參閱</span><span class="sxs-lookup"><span data-stu-id="11ad8-146">See also</span></span>

- [<span data-ttu-id="11ad8-147">Shadows</span><span class="sxs-lookup"><span data-stu-id="11ad8-147">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="11ad8-148">Static</span><span class="sxs-lookup"><span data-stu-id="11ad8-148">Static</span></span>](../../../visual-basic/language-reference/modifiers/static.md)
- [<span data-ttu-id="11ad8-149">Visual Basic 中的存留期</span><span class="sxs-lookup"><span data-stu-id="11ad8-149">Lifetime in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="11ad8-150">程序</span><span class="sxs-lookup"><span data-stu-id="11ad8-150">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="11ad8-151">結構</span><span class="sxs-lookup"><span data-stu-id="11ad8-151">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="11ad8-152">物件和類別</span><span class="sxs-lookup"><span data-stu-id="11ad8-152">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
