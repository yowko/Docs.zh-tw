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
ms.openlocfilehash: b51c88e1af3a720912af8ba6aaf8ae4016af9cfa
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990187"
---
# <a name="shared-visual-basic"></a><span data-ttu-id="698e8-102">Shared (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="698e8-102">Shared (Visual Basic)</span></span>

<span data-ttu-id="698e8-103">指定一或多個宣告的程式設計專案與大型的類別或結構相關聯，而不是與類別或結構的特定實例產生關聯。</span><span class="sxs-lookup"><span data-stu-id="698e8-103">Specifies that one or more declared programming elements are associated with a class or structure at large, and not with a specific instance of the class or structure.</span></span>

## <a name="when-to-use-shared"></a><span data-ttu-id="698e8-104">使用 Shared 的時機</span><span class="sxs-lookup"><span data-stu-id="698e8-104">When to Use Shared</span></span>

<span data-ttu-id="698e8-105">共用類別或結構的成員，可將它提供給每個實例，而不是*非共用*，其中每個實例都會保留自己的複本。</span><span class="sxs-lookup"><span data-stu-id="698e8-105">Sharing a member of a class or structure makes it available to every instance, rather than *non-shared*, where each instance keeps its own copy.</span></span> <span data-ttu-id="698e8-106">共用非常有用，例如，如果變數的值適用于整個應用程式。</span><span class="sxs-lookup"><span data-stu-id="698e8-106">Sharing is useful, for example, if the value of a variable applies to the entire application.</span></span> <span data-ttu-id="698e8-107">如果您將該變數宣告為 `Shared` ，則所有實例都會存取相同的儲存位置，而如果一個實例變更變數的值，則所有實例都會存取更新的值。</span><span class="sxs-lookup"><span data-stu-id="698e8-107">If you declare that variable to be `Shared`, then all instances access the same storage location, and if one instance changes the variable's value, all instances access the updated value.</span></span>

<span data-ttu-id="698e8-108">共用不會改變成員的存取層級。</span><span class="sxs-lookup"><span data-stu-id="698e8-108">Sharing does not alter the access level of a member.</span></span> <span data-ttu-id="698e8-109">例如，類別成員可以是共用和私用（只能從類別記憶體取），或非共用和公用。</span><span class="sxs-lookup"><span data-stu-id="698e8-109">For example, a class member can be shared and private (accessible only from within the class), or non-shared and public.</span></span> <span data-ttu-id="698e8-110">如需詳細資訊，請參閱[Visual Basic 中的存取層級](../../programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="698e8-110">For more information, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

## <a name="rules"></a><span data-ttu-id="698e8-111">規則</span><span class="sxs-lookup"><span data-stu-id="698e8-111">Rules</span></span>

- <span data-ttu-id="698e8-112">**宣告內容。**</span><span class="sxs-lookup"><span data-stu-id="698e8-112">**Declaration Context.**</span></span> <span data-ttu-id="698e8-113">您只能在模組層級使用 `Shared`。</span><span class="sxs-lookup"><span data-stu-id="698e8-113">You can use `Shared` only at module level.</span></span> <span data-ttu-id="698e8-114">這表示元素的宣告內容 `Shared` 必須是類別或結構，而且不能是原始程式檔、命名空間或程式。</span><span class="sxs-lookup"><span data-stu-id="698e8-114">This means the declaration context for a `Shared` element must be a class or structure, and cannot be a source file, namespace, or procedure.</span></span>

- <span data-ttu-id="698e8-115">**結合的修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="698e8-115">**Combined Modifiers.**</span></span> <span data-ttu-id="698e8-116">您不能 `Shared` 在相同的宣告[Overridable](overridable.md)中，將[覆寫](overrides.md)、可覆寫、 [NotOverridable](notoverridable.md)、 [MustOverride](mustoverride.md)或[Static](static.md)指定在一起。</span><span class="sxs-lookup"><span data-stu-id="698e8-116">You cannot specify `Shared` together with [Overrides](overrides.md), [Overridable](overridable.md), [NotOverridable](notoverridable.md), [MustOverride](mustoverride.md), or [Static](static.md) in the same declaration.</span></span>

- <span data-ttu-id="698e8-117">**正在.**</span><span class="sxs-lookup"><span data-stu-id="698e8-117">**Accessing.**</span></span> <span data-ttu-id="698e8-118">您可以存取共用專案，方法是以其類別或結構名稱加以限定，而不是使用其類別或結構之特定實例的變數名稱。</span><span class="sxs-lookup"><span data-stu-id="698e8-118">You access a shared element by qualifying it with its class or structure name, not with the variable name of a specific instance of its class or structure.</span></span> <span data-ttu-id="698e8-119">您甚至不需要建立類別或結構的實例來存取其共用成員。</span><span class="sxs-lookup"><span data-stu-id="698e8-119">You do not even have to create an instance of a class or structure to access its shared members.</span></span>

     <span data-ttu-id="698e8-120">下列範例會呼叫結構所公開的共用 <xref:System.Double.IsNaN%2A> 程式 <xref:System.Double> 。</span><span class="sxs-lookup"><span data-stu-id="698e8-120">The following example calls the shared procedure <xref:System.Double.IsNaN%2A> exposed by the <xref:System.Double> structure.</span></span>

     ```vb
     If Double.IsNaN(result) Then Console.WriteLine("Result is mathematically undefined.")
     ```

- <span data-ttu-id="698e8-121">**隱含共用。**</span><span class="sxs-lookup"><span data-stu-id="698e8-121">**Implicit Sharing.**</span></span> <span data-ttu-id="698e8-122">您不能 `Shared` 在[Const 語句](../statements/const-statement.md)中使用修飾詞，但會隱含地共用常數。</span><span class="sxs-lookup"><span data-stu-id="698e8-122">You cannot use the `Shared` modifier in a [Const Statement](../statements/const-statement.md), but constants are implicitly shared.</span></span> <span data-ttu-id="698e8-123">同樣地，您無法將模組或介面的成員宣告為 `Shared` ，但它們會隱含共用。</span><span class="sxs-lookup"><span data-stu-id="698e8-123">Similarly, you cannot declare a member of a module or an interface to be `Shared`, but they are implicitly shared.</span></span>

## <a name="behavior"></a><span data-ttu-id="698e8-124">行為</span><span class="sxs-lookup"><span data-stu-id="698e8-124">Behavior</span></span>

- <span data-ttu-id="698e8-125">**容量.**</span><span class="sxs-lookup"><span data-stu-id="698e8-125">**Storage.**</span></span> <span data-ttu-id="698e8-126">共用變數或事件只會儲存一次，無論您建立類別或結構的實例有多少或數個。</span><span class="sxs-lookup"><span data-stu-id="698e8-126">A shared variable or event is stored in memory only once, no matter how many or few instances you create of its class or structure.</span></span> <span data-ttu-id="698e8-127">同樣地，共用程式或屬性只會保留一組本機變數。</span><span class="sxs-lookup"><span data-stu-id="698e8-127">Similarly, a shared procedure or property holds only one set of local variables.</span></span>

- <span data-ttu-id="698e8-128">**透過執行個體變數存取。**</span><span class="sxs-lookup"><span data-stu-id="698e8-128">**Accessing through an Instance Variable.**</span></span> <span data-ttu-id="698e8-129">藉由使用包含其類別或結構之特定實例的變數名稱來限定共用專案，可以存取該元素。</span><span class="sxs-lookup"><span data-stu-id="698e8-129">It is possible to access a shared element by qualifying it with the name of a variable that contains a specific instance of its class or structure.</span></span> <span data-ttu-id="698e8-130">雖然這通常會如預期般運作，但編譯器會產生警告訊息，並透過類別或結構名稱而不是變數來進行存取。</span><span class="sxs-lookup"><span data-stu-id="698e8-130">Although this usually works as expected, the compiler generates a warning message and makes the access through the class or structure name instead of the variable.</span></span>

- <span data-ttu-id="698e8-131">**透過實例運算式來存取。**</span><span class="sxs-lookup"><span data-stu-id="698e8-131">**Accessing through an Instance Expression.**</span></span> <span data-ttu-id="698e8-132">如果您透過傳回其類別或結構實例的運算式來存取共用專案，編譯器會透過類別或結構名稱進行存取，而不會評估運算式。</span><span class="sxs-lookup"><span data-stu-id="698e8-132">If you access a shared element through an expression that returns an instance of its class or structure, the compiler makes the access through the class or structure name instead of evaluating the expression.</span></span> <span data-ttu-id="698e8-133">如果您想要運算式執行其他動作以及傳回實例，此存取會產生非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="698e8-133">This access produces unexpected results if you intended the expression to perform other actions as well as returning the instance.</span></span> <span data-ttu-id="698e8-134">下列範例將說明這種情況。</span><span class="sxs-lookup"><span data-stu-id="698e8-134">The following example illustrates this situation.</span></span>
  
    ```vb
    Sub Main()
        ' The following line is the preferred way to access Total.
        ShareTotal.Total = 10

        ' The following line generates a compiler warning message and
        ' accesses total through class ShareTotal instead of through
        ' the variable instanceVar. This works as expected and adds
        ' 100 to Total.
        Dim instanceVar As New ShareTotal
        instanceVar.Total += 100

        ' The following line generates a compiler warning message and
        ' accesses total through class ShareTotal instead of calling
        ' ReturnClass(). This adds 1000 to total but does not work as
        ' expected, because the WriteLine in ReturnClass() does not run.
        Console.WriteLine("Value of total is " & CStr(ShareTotal.Total))
        ReturnClass().Total += 1000
    End Sub

    Public Function ReturnClass() As ShareTotal
        Console.WriteLine("Function ReturnClass() called")
        Return New ShareTotal
    End Function

    Public Class ShareTotal
        Public Shared Property Total As Integer
    End Class
    ```

     <span data-ttu-id="698e8-135">在上述範例中，編譯器會產生一則警告訊息，這兩次程式碼都會 `Total` 透過實例存取共用屬性。</span><span class="sxs-lookup"><span data-stu-id="698e8-135">In the preceding example, the compiler generates a warning message both times the code accesses the shared property `Total` through an instance.</span></span> <span data-ttu-id="698e8-136">在每個案例中，它會直接透過類別進行存取 `ShareTotal` ，而不會使用任何實例。</span><span class="sxs-lookup"><span data-stu-id="698e8-136">In each case, it makes the access directly through the class `ShareTotal` and does not make use of any instance.</span></span> <span data-ttu-id="698e8-137">對於程式的預期呼叫 `ReturnClass` ，這表示它甚至不會產生對的呼叫 `ReturnClass` ，因此不會執行顯示 "Function ReturnClass （）" 的其他動作。</span><span class="sxs-lookup"><span data-stu-id="698e8-137">In the case of the intended call to the procedure `ReturnClass`, this means it does not even generate a call to `ReturnClass`, so the additional action of displaying "Function ReturnClass() called" is not performed.</span></span>

<span data-ttu-id="698e8-138">`Shared` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="698e8-138">The `Shared` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="698e8-139">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="698e8-139">Dim Statement</span></span>](../statements/dim-statement.md)
- [<span data-ttu-id="698e8-140">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="698e8-140">Event Statement</span></span>](../statements/event-statement.md)
- [<span data-ttu-id="698e8-141">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="698e8-141">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="698e8-142">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="698e8-142">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="698e8-143">Property Statement</span><span class="sxs-lookup"><span data-stu-id="698e8-143">Property Statement</span></span>](../statements/property-statement.md)
- [<span data-ttu-id="698e8-144">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="698e8-144">Sub Statement</span></span>](../statements/sub-statement.md)
  
## <a name="see-also"></a><span data-ttu-id="698e8-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="698e8-145">See also</span></span>

- [<span data-ttu-id="698e8-146">Shadows</span><span class="sxs-lookup"><span data-stu-id="698e8-146">Shadows</span></span>](shadows.md)
- [<span data-ttu-id="698e8-147">靜態</span><span class="sxs-lookup"><span data-stu-id="698e8-147">Static</span></span>](static.md)
- [<span data-ttu-id="698e8-148">Visual Basic 中的存留期</span><span class="sxs-lookup"><span data-stu-id="698e8-148">Lifetime in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="698e8-149">程序</span><span class="sxs-lookup"><span data-stu-id="698e8-149">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="698e8-150">結構</span><span class="sxs-lookup"><span data-stu-id="698e8-150">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="698e8-151">物件和類別</span><span class="sxs-lookup"><span data-stu-id="698e8-151">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
