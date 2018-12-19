---
title: HOW TO：宣告、產生和使用委派 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
ms.openlocfilehash: bc9fc81a74d438aca57779fa565fdbeba3968087
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237060"
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a><span data-ttu-id="055de-102">HOW TO：宣告、產生和使用委派 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="055de-102">How to: Declare, Instantiate, and Use a Delegate (C# Programming Guide)</span></span>
<span data-ttu-id="055de-103">在 C# 1.0 和更新版本中，宣告委派的方式如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="055de-103">In C# 1.0 and later, delegates can be declared as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#13](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_1.cs)]  
  
 [!code-csharp[csProgGuideDelegates#14](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_2.cs)]  
  
 <span data-ttu-id="055de-104">C# 2.0 提供更簡單的方式來撰寫先前的宣告，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="055de-104">C# 2.0 provides a simpler way to write the previous declaration, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#32](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_3.cs)]  
  
 <span data-ttu-id="055de-105">在 C# 2.0 和更新版本中，也可以使用匿名方法來宣告和初始化[委派](../../../csharp/language-reference/keywords/delegate.md)，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="055de-105">In C# 2.0 and later, it is also possible to use an anonymous method to declare and initialize a [delegate](../../../csharp/language-reference/keywords/delegate.md), as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#15](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_4.cs)]  
  
 <span data-ttu-id="055de-106">在 C# 3.0 和更新版本中，也可以使用 lambda 運算式來宣告委派並將它具現化，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="055de-106">In C# 3.0 and later, delegates can also be declared and instantiated by using a lambda expression, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#31](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_5.cs)]  
  
 <span data-ttu-id="055de-107">如需詳細資訊，請參閱 [Lambda 運算式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="055de-107">For more information, see [Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="055de-108">下列範例說明如何宣告、具現化和使用委派。</span><span class="sxs-lookup"><span data-stu-id="055de-108">The following example illustrates declaring, instantiating, and using a delegate.</span></span> <span data-ttu-id="055de-109">`BookDB` 類別會封裝用來保留書籍資料的書店資料庫。</span><span class="sxs-lookup"><span data-stu-id="055de-109">The `BookDB` class encapsulates a bookstore database that maintains a database of books.</span></span> <span data-ttu-id="055de-110">它會公開 `ProcessPaperbackBooks` 方法，此方法會尋找資料庫中的所有平裝書，並針對每本書呼叫委派。</span><span class="sxs-lookup"><span data-stu-id="055de-110">It exposes a method, `ProcessPaperbackBooks`, which finds all paperback books in the database and calls a delegate for each one.</span></span> <span data-ttu-id="055de-111">所使用的 `delegate` 類型稱為 `ProcessBookDelegate`。</span><span class="sxs-lookup"><span data-stu-id="055de-111">The `delegate` type that is used is named `ProcessBookDelegate`.</span></span> <span data-ttu-id="055de-112">`Test` 類別會使用這個類別來列印平裝書的書名和平均價格。</span><span class="sxs-lookup"><span data-stu-id="055de-112">The `Test` class uses this class to print the titles and average price of the paperback books.</span></span>  
  
 <span data-ttu-id="055de-113">使用委派，可在書店資料庫和用戶端程式碼之間建立良好的功能區隔。</span><span class="sxs-lookup"><span data-stu-id="055de-113">The use of delegates promotes good separation of functionality between the bookstore database and the client code.</span></span> <span data-ttu-id="055de-114">用戶端程式碼不需要瞭解保存書籍的方式，或是書店程式碼尋找平裝書的方式。</span><span class="sxs-lookup"><span data-stu-id="055de-114">The client code has no knowledge of how the books are stored or how the bookstore code finds paperback books.</span></span> <span data-ttu-id="055de-115">書店程式碼不需要知道當它找到平裝書之後該如何處理它們。</span><span class="sxs-lookup"><span data-stu-id="055de-115">The bookstore code has no knowledge of what processing is performed on the paperback books after it finds them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="055de-116">範例</span><span class="sxs-lookup"><span data-stu-id="055de-116">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#12](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_6.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="055de-117">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="055de-117">Robust Programming</span></span>  
  
-   <span data-ttu-id="055de-118">宣告委派。</span><span class="sxs-lookup"><span data-stu-id="055de-118">Declaring a delegate.</span></span>  
  
     <span data-ttu-id="055de-119">下列陳述式會宣告新的委派類型。</span><span class="sxs-lookup"><span data-stu-id="055de-119">The following statement declares a new delegate type.</span></span>  
  
     [!code-csharp[csProgGuideDelegates#16](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_7.cs)]  
  
     <span data-ttu-id="055de-120">每個委派類型都會描述引數的數目和類型，以及它可以封裝之方法的傳回值類型。</span><span class="sxs-lookup"><span data-stu-id="055de-120">Each delegate type describes the number and types of the arguments, and the type of the return value of methods that it can encapsulate.</span></span> <span data-ttu-id="055de-121">每當需要一組新的引數類型或傳回值類型時，就必須宣告新的委派類型。</span><span class="sxs-lookup"><span data-stu-id="055de-121">Whenever a new set of argument types or return value type is needed, a new delegate type must be declared.</span></span>  
  
-   <span data-ttu-id="055de-122">具現化委派。</span><span class="sxs-lookup"><span data-stu-id="055de-122">Instantiating a delegate.</span></span>  
  
     <span data-ttu-id="055de-123">宣告委派類型之後，就必須建立委派物件並將其關聯至特定的方法。</span><span class="sxs-lookup"><span data-stu-id="055de-123">After a delegate type has been declared, a delegate object must be created and associated with a particular method.</span></span> <span data-ttu-id="055de-124">在上述範例中，您可以藉由將 `PrintTitle` 方法傳遞至 `ProcessPaperbackBooks` 方法來執行此動作，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="055de-124">In the previous example, you do this by passing the `PrintTitle` method to the `ProcessPaperbackBooks` method as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#17](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_8.cs)]  
  
     <span data-ttu-id="055de-125">這會建立與[靜態](../../../csharp/language-reference/keywords/static.md)方法 `Test.PrintTitle` 相關聯的新委派物件。</span><span class="sxs-lookup"><span data-stu-id="055de-125">This creates a new delegate object associated with the [static](../../../csharp/language-reference/keywords/static.md) method `Test.PrintTitle`.</span></span> <span data-ttu-id="055de-126">同樣地，也可傳遞 `totaller` 物件上的非靜態方法 `AddBookToTotal`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="055de-126">Similarly, the non-static method `AddBookToTotal` on the object `totaller` is passed as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#18](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_9.cs)]  
  
     <span data-ttu-id="055de-127">在這兩種情況下，會將新的委派物件傳遞至 `ProcessPaperbackBooks` 方法。</span><span class="sxs-lookup"><span data-stu-id="055de-127">In both cases a new delegate object is passed to the `ProcessPaperbackBooks` method.</span></span>  
  
     <span data-ttu-id="055de-128">建立委派之後，與其相關聯的方法絕對不會變更；委派物件是不可變的。</span><span class="sxs-lookup"><span data-stu-id="055de-128">After a delegate is created, the method it is associated with never changes; delegate objects are immutable.</span></span>  
  
-   <span data-ttu-id="055de-129">呼叫委派。</span><span class="sxs-lookup"><span data-stu-id="055de-129">Calling a delegate.</span></span>  
  
     <span data-ttu-id="055de-130">建立委派物件之後，通常會將委派物件傳遞至其他將呼叫委派的程式碼。</span><span class="sxs-lookup"><span data-stu-id="055de-130">After a delegate object is created, the delegate object is typically passed to other code that will call the delegate.</span></span> <span data-ttu-id="055de-131">委派物件的呼叫方法是，使用委派物件的名稱，後面接著要傳遞至委派且已加上括號的引數。</span><span class="sxs-lookup"><span data-stu-id="055de-131">A delegate object is called by using the name of the delegate object, followed by the parenthesized arguments to be passed to the delegate.</span></span> <span data-ttu-id="055de-132">以下是委派呼叫的範例：</span><span class="sxs-lookup"><span data-stu-id="055de-132">Following is an example of a delegate call:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#19](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_10.cs)]  
  
     <span data-ttu-id="055de-133">委派可以同步呼叫 (如此範例所示)，或使用 `BeginInvoke` 和 `EndInvoke` 方法以非同步方式呼叫。</span><span class="sxs-lookup"><span data-stu-id="055de-133">A delegate can be either called synchronously, as in this example, or asynchronously by using `BeginInvoke` and `EndInvoke` methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="055de-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="055de-134">See Also</span></span>

- [<span data-ttu-id="055de-135">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="055de-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="055de-136">事件</span><span class="sxs-lookup"><span data-stu-id="055de-136">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
- [<span data-ttu-id="055de-137">委派</span><span class="sxs-lookup"><span data-stu-id="055de-137">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
