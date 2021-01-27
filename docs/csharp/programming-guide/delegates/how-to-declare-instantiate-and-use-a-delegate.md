---
title: '如何宣告、具現化和使用委派-c # 程式設計指南'
description: '瞭解如何宣告、具現化和使用委派。 請參閱涵蓋 c # 1.0、2.0 和3.0 和更新版本的範例。'
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
ms.openlocfilehash: 08d8e10b4aba3fd75e200b2c8c14bb3d1825b318
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/27/2021
ms.locfileid: "98898875"
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a><span data-ttu-id="e403b-104">如何宣告、具現化和使用委派 (c # 程式設計手冊) </span><span class="sxs-lookup"><span data-stu-id="e403b-104">How to declare, instantiate, and use a Delegate (C# Programming Guide)</span></span>

<span data-ttu-id="e403b-105">在 C# 1.0 和更新版本中，宣告委派的方式如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="e403b-105">In C# 1.0 and later, delegates can be declared as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#13)]  
  
 [!code-csharp[csProgGuideDelegates#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#14)]  
  
 <span data-ttu-id="e403b-106">C# 2.0 提供更簡單的方式來撰寫先前的宣告，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="e403b-106">C# 2.0 provides a simpler way to write the previous declaration, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#32)]  
  
 <span data-ttu-id="e403b-107">在 C# 2.0 和更新版本中，也可以使用匿名方法來宣告和初始化[委派](../../language-reference/builtin-types/reference-types.md)，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="e403b-107">In C# 2.0 and later, it is also possible to use an anonymous method to declare and initialize a [delegate](../../language-reference/builtin-types/reference-types.md), as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#15)]  
  
 <span data-ttu-id="e403b-108">在 C# 3.0 和更新版本中，也可以使用 lambda 運算式來宣告委派並將它具現化，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="e403b-108">In C# 3.0 and later, delegates can also be declared and instantiated by using a lambda expression, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#31)]  
  
 <span data-ttu-id="e403b-109">如需詳細資訊，請參閱 [Lambda 運算式](../../language-reference/operators/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="e403b-109">For more information, see [Lambda Expressions](../../language-reference/operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="e403b-110">下列範例說明如何宣告、具現化和使用委派。</span><span class="sxs-lookup"><span data-stu-id="e403b-110">The following example illustrates declaring, instantiating, and using a delegate.</span></span> <span data-ttu-id="e403b-111">`BookDB` 類別會封裝用來保留書籍資料的書店資料庫。</span><span class="sxs-lookup"><span data-stu-id="e403b-111">The `BookDB` class encapsulates a bookstore database that maintains a database of books.</span></span> <span data-ttu-id="e403b-112">它會公開 `ProcessPaperbackBooks` 方法，此方法會尋找資料庫中的所有平裝書，並針對每本書呼叫委派。</span><span class="sxs-lookup"><span data-stu-id="e403b-112">It exposes a method, `ProcessPaperbackBooks`, which finds all paperback books in the database and calls a delegate for each one.</span></span> <span data-ttu-id="e403b-113">所使用的 `delegate` 類型稱為 `ProcessBookCallback`。</span><span class="sxs-lookup"><span data-stu-id="e403b-113">The `delegate` type that is used is named `ProcessBookCallback`.</span></span> <span data-ttu-id="e403b-114">`Test` 類別會使用這個類別來列印平裝書的書名和平均價格。</span><span class="sxs-lookup"><span data-stu-id="e403b-114">The `Test` class uses this class to print the titles and average price of the paperback books.</span></span>  
  
 <span data-ttu-id="e403b-115">使用委派，可在書店資料庫和用戶端程式碼之間建立良好的功能區隔。</span><span class="sxs-lookup"><span data-stu-id="e403b-115">The use of delegates promotes good separation of functionality between the bookstore database and the client code.</span></span> <span data-ttu-id="e403b-116">用戶端程式碼不需要瞭解保存書籍的方式，或是書店程式碼尋找平裝書的方式。</span><span class="sxs-lookup"><span data-stu-id="e403b-116">The client code has no knowledge of how the books are stored or how the bookstore code finds paperback books.</span></span> <span data-ttu-id="e403b-117">書店程式碼不需要知道當它找到平裝書之後該如何處理它們。</span><span class="sxs-lookup"><span data-stu-id="e403b-117">The bookstore code has no knowledge of what processing is performed on the paperback books after it finds them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e403b-118">範例</span><span class="sxs-lookup"><span data-stu-id="e403b-118">Example</span></span>  

 [!code-csharp[csProgGuideDelegates#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#12)]  
  
## <a name="robust-programming"></a><span data-ttu-id="e403b-119">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="e403b-119">Robust Programming</span></span>  
  
- <span data-ttu-id="e403b-120">宣告委派。</span><span class="sxs-lookup"><span data-stu-id="e403b-120">Declaring a delegate.</span></span>  
  
     <span data-ttu-id="e403b-121">下列陳述式會宣告新的委派類型。</span><span class="sxs-lookup"><span data-stu-id="e403b-121">The following statement declares a new delegate type.</span></span>  
  
     [!code-csharp[csProgGuideDelegates#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#16)]  
  
     <span data-ttu-id="e403b-122">每個委派類型都會描述引數的數目和類型，以及它可以封裝之方法的傳回值類型。</span><span class="sxs-lookup"><span data-stu-id="e403b-122">Each delegate type describes the number and types of the arguments, and the type of the return value of methods that it can encapsulate.</span></span> <span data-ttu-id="e403b-123">每當需要一組新的引數類型或傳回值類型時，就必須宣告新的委派類型。</span><span class="sxs-lookup"><span data-stu-id="e403b-123">Whenever a new set of argument types or return value type is needed, a new delegate type must be declared.</span></span>  
  
- <span data-ttu-id="e403b-124">具現化委派。</span><span class="sxs-lookup"><span data-stu-id="e403b-124">Instantiating a delegate.</span></span>  
  
     <span data-ttu-id="e403b-125">宣告委派類型之後，就必須建立委派物件並將其關聯至特定的方法。</span><span class="sxs-lookup"><span data-stu-id="e403b-125">After a delegate type has been declared, a delegate object must be created and associated with a particular method.</span></span> <span data-ttu-id="e403b-126">在上述範例中，您可以藉由將 `PrintTitle` 方法傳遞至 `ProcessPaperbackBooks` 方法來執行此動作，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="e403b-126">In the previous example, you do this by passing the `PrintTitle` method to the `ProcessPaperbackBooks` method as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#17)]  
  
     <span data-ttu-id="e403b-127">這會建立與[靜態](../../language-reference/keywords/static.md)方法 `Test.PrintTitle` 相關聯的新委派物件。</span><span class="sxs-lookup"><span data-stu-id="e403b-127">This creates a new delegate object associated with the [static](../../language-reference/keywords/static.md) method `Test.PrintTitle`.</span></span> <span data-ttu-id="e403b-128">同樣地，也可傳遞 `totaller` 物件上的非靜態方法 `AddBookToTotal`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="e403b-128">Similarly, the non-static method `AddBookToTotal` on the object `totaller` is passed as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#18)]  
  
     <span data-ttu-id="e403b-129">在這兩種情況下，會將新的委派物件傳遞至 `ProcessPaperbackBooks` 方法。</span><span class="sxs-lookup"><span data-stu-id="e403b-129">In both cases a new delegate object is passed to the `ProcessPaperbackBooks` method.</span></span>  
  
     <span data-ttu-id="e403b-130">建立委派之後，與其相關聯的方法絕對不會變更；委派物件是不可變的。</span><span class="sxs-lookup"><span data-stu-id="e403b-130">After a delegate is created, the method it is associated with never changes; delegate objects are immutable.</span></span>  
  
- <span data-ttu-id="e403b-131">呼叫委派。</span><span class="sxs-lookup"><span data-stu-id="e403b-131">Calling a delegate.</span></span>  
  
     <span data-ttu-id="e403b-132">建立委派物件之後，通常會將委派物件傳遞至其他將呼叫委派的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e403b-132">After a delegate object is created, the delegate object is typically passed to other code that will call the delegate.</span></span> <span data-ttu-id="e403b-133">委派物件的呼叫方法是，使用委派物件的名稱，後面接著要傳遞至委派且已加上括號的引數。</span><span class="sxs-lookup"><span data-stu-id="e403b-133">A delegate object is called by using the name of the delegate object, followed by the parenthesized arguments to be passed to the delegate.</span></span> <span data-ttu-id="e403b-134">以下是委派呼叫的範例：</span><span class="sxs-lookup"><span data-stu-id="e403b-134">Following is an example of a delegate call:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#19)]  
  
     <span data-ttu-id="e403b-135">委派可以同步呼叫 (如此範例所示)，或使用 `BeginInvoke` 和 `EndInvoke` 方法以非同步方式呼叫。</span><span class="sxs-lookup"><span data-stu-id="e403b-135">A delegate can be either called synchronously, as in this example, or asynchronously by using `BeginInvoke` and `EndInvoke` methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e403b-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e403b-136">See also</span></span>

- [<span data-ttu-id="e403b-137">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="e403b-137">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e403b-138">事件</span><span class="sxs-lookup"><span data-stu-id="e403b-138">Events</span></span>](../events/index.md)
- [<span data-ttu-id="e403b-139">委派</span><span class="sxs-lookup"><span data-stu-id="e403b-139">Delegates</span></span>](./index.md)
