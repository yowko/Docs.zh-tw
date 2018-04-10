---
title: 委派 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- delegates [Visual Basic]
- Visual Basic code, delegates
ms.assetid: 410b60dc-5e60-4ec0-bfae-426755a2ee28
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fe21d8c0dcefaea35d9f96cd2ecbff92a1c83d36
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="delegates-visual-basic"></a><span data-ttu-id="32e9f-102">委派 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="32e9f-102">Delegates (Visual Basic)</span></span>
<span data-ttu-id="32e9f-103">委派是參考方法的物件。</span><span class="sxs-lookup"><span data-stu-id="32e9f-103">Delegates are objects that refer to methods.</span></span> <span data-ttu-id="32e9f-104">它們有時稱為「型別安全的函式指標」，因為它們類似於其他程式設計語言中使用的函式指標。</span><span class="sxs-lookup"><span data-stu-id="32e9f-104">They are sometimes described as *type-safe function pointers* because they are similar to function pointers used in other programming languages.</span></span> <span data-ttu-id="32e9f-105">但不同於函式指標，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 委派是以 <xref:System.Delegate?displayProperty=nameWithType> 類別為基礎的參考型別。</span><span class="sxs-lookup"><span data-stu-id="32e9f-105">But unlike function pointers, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] delegates are a reference type based on the class <xref:System.Delegate?displayProperty=nameWithType>.</span></span> <span data-ttu-id="32e9f-106">委派可以同時參考共用的方法 (不需類別的特定執行個體就能呼叫的方法) 和執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="32e9f-106">Delegates can reference both shared methods — methods that can be called without a specific instance of a class — and instance methods.</span></span>  
  
## <a name="delegates-and-events"></a><span data-ttu-id="32e9f-107">委派和事件</span><span class="sxs-lookup"><span data-stu-id="32e9f-107">Delegates and Events</span></span>  
 <span data-ttu-id="32e9f-108">當您在呼叫程序與被呼叫程序之間需要一個媒介時，委派就很有用。</span><span class="sxs-lookup"><span data-stu-id="32e9f-108">Delegates are useful in situations where you need an intermediary between a calling procedure and the procedure being called.</span></span> <span data-ttu-id="32e9f-109">例如，您想要讓引發事件的物件能夠在不同環境下呼叫不同的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="32e9f-109">For example, you might want an object that raises events to be able to call different event handlers under different circumstances.</span></span> <span data-ttu-id="32e9f-110">不過，引發事件的物件無法事先知道哪一個事件處理常式正在處理特定事件。</span><span class="sxs-lookup"><span data-stu-id="32e9f-110">Unfortunately, the object raising the events cannot know ahead of time which event handler is handling a specific event.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="32e9f-111"> 可讓您藉由在使用 `AddHandler` 陳述式時建立自己的委派，以動態方式建立事件處理常式與事件的關聯。</span><span class="sxs-lookup"><span data-stu-id="32e9f-111"> lets you dynamically associate event handlers with events by creating a delegate for you when you use the `AddHandler` statement.</span></span> <span data-ttu-id="32e9f-112">在執行階段，委派會將呼叫轉送到適當的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="32e9f-112">At run time, the delegate forwards calls to the appropriate event handler.</span></span>  
  
 <span data-ttu-id="32e9f-113">雖然您可以建立自己的委派，但在大部分情況下，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 會建立委派，並為您處理細節。</span><span class="sxs-lookup"><span data-stu-id="32e9f-113">Although you can create your own delegates, in most cases [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] creates the delegate and takes care of the details for you.</span></span> <span data-ttu-id="32e9f-114">例如，`Event` 陳述式會隱含定義名為 `<EventName>EventHandler` 的委派類別做為包含 `Event` 陳述式之類別的巢狀類別，並包含與事件相同的簽章。</span><span class="sxs-lookup"><span data-stu-id="32e9f-114">For example, an `Event` statement implicitly defines a delegate class named `<EventName>EventHandler` as a nested class of the class containing the `Event` statement, and with the same signature as the event.</span></span> <span data-ttu-id="32e9f-115">`AddressOf` 陳述式會隱含建立參考特定程序之委派的執行個體。</span><span class="sxs-lookup"><span data-stu-id="32e9f-115">The `AddressOf` statement implicitly creates an instance of a delegate that refers to a specific procedure.</span></span> <span data-ttu-id="32e9f-116">下兩行程式碼的用法相同。</span><span class="sxs-lookup"><span data-stu-id="32e9f-116">The following two lines of code are equivalent.</span></span> <span data-ttu-id="32e9f-117">在第一行中，您會看到明確建立了 `Eventhandler` 的執行個體，其中包含對傳送為引數之 `Button1_Click` 方法的參考。</span><span class="sxs-lookup"><span data-stu-id="32e9f-117">In the first line, you see the explicit creation of an instance of `Eventhandler`, with a reference to method `Button1_Click` sent as the argument.</span></span> <span data-ttu-id="32e9f-118">第二行則是可執行相同動作的更便捷方法。</span><span class="sxs-lookup"><span data-stu-id="32e9f-118">The second line is a more convenient way to do the same thing.</span></span>  
  
 [!code-vb[VbVbalrDelegates#6](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegates_1.vb)]  
  
 <span data-ttu-id="32e9f-119">您可以使用在任意處建立委派的速成法，讓編譯器可依內容判斷委派的型別。</span><span class="sxs-lookup"><span data-stu-id="32e9f-119">You can use the shorthand way of creating delegates anywhere the compiler can determine the delegate's type by the context.</span></span>  
  
## <a name="declaring-events-that-use-an-existing-delegate-type"></a><span data-ttu-id="32e9f-120">宣告使用現有委派型別的事件</span><span class="sxs-lookup"><span data-stu-id="32e9f-120">Declaring Events that Use an Existing Delegate Type</span></span>  
 <span data-ttu-id="32e9f-121">在某些情況下，您可能想要宣告事件，以使用現有的委派型別做為它的基礎委派。</span><span class="sxs-lookup"><span data-stu-id="32e9f-121">In some situations, you may want to declare an event to use an existing delegate type as its underlying delegate.</span></span> <span data-ttu-id="32e9f-122">下列語法示範做法：</span><span class="sxs-lookup"><span data-stu-id="32e9f-122">The following syntax demonstrates how:</span></span>  
  
 [!code-vb[VbVbalrDelegates#7](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegates_2.vb)]  
  
 <span data-ttu-id="32e9f-123">當您想要將多個事件路由傳送到相同的處理常式時，這非常有用。</span><span class="sxs-lookup"><span data-stu-id="32e9f-123">This is useful when you want to route multiple events to the same handler.</span></span>  
  
## <a name="delegate-variables-and-parameters"></a><span data-ttu-id="32e9f-124">委派變數和參數</span><span class="sxs-lookup"><span data-stu-id="32e9f-124">Delegate Variables and Parameters</span></span>  
 <span data-ttu-id="32e9f-125">您可以針對其他與事件無關的工作 (例如無限制執行緒) 使用委派，或搭配需要在執行階段呼叫不同函式版本的程序來使用委派。</span><span class="sxs-lookup"><span data-stu-id="32e9f-125">You can use delegates for other, non-event related tasks, such as free threading or with procedures that need to call different versions of functions at run time.</span></span>  
  
 <span data-ttu-id="32e9f-126">例如，假設您具有分類廣告應用程式，其中包含具有車名的清單方塊。</span><span class="sxs-lookup"><span data-stu-id="32e9f-126">For example, suppose you have a classified-ad application that includes a list box with the names of cars.</span></span> <span data-ttu-id="32e9f-127">廣告會依標題排序，通常是汽車製造商。</span><span class="sxs-lookup"><span data-stu-id="32e9f-127">The ads are sorted by title, which is normally the make of the car.</span></span> <span data-ttu-id="32e9f-128">當某些汽車在製造商之前包含汽車的年份時，就會發生您可能面臨的問題。</span><span class="sxs-lookup"><span data-stu-id="32e9f-128">A problem you may face occurs when some cars include the year of the car before the make.</span></span> <span data-ttu-id="32e9f-129">問題是清單方塊的內建排序功能只會依照字元碼排序；它會先排序所有以日期開頭的廣告，接著才是以製造商開頭的廣告。</span><span class="sxs-lookup"><span data-stu-id="32e9f-129">The problem is that the built-in sort functionality of the list box sorts only by character codes; it places all the ads starting with dates first, followed by the ads starting with the make.</span></span>  
  
 <span data-ttu-id="32e9f-130">為了修正此問題，您可以在某個類別中使用排序程序 (該類別會在大部分清單方塊中使用標準的依字母順序排序)，但是可以在執行階段切換到自訂排序程序來進行汽車廣告。</span><span class="sxs-lookup"><span data-stu-id="32e9f-130">To fix this, you can create a sort procedure in a class that uses the standard alphabetic sort on most list boxes, but is able to switch at run time to the custom sort procedure for car ads.</span></span> <span data-ttu-id="32e9f-131">若要這樣做，您可以使用委派，在執行階段將自訂排序程序傳遞到排序類別。</span><span class="sxs-lookup"><span data-stu-id="32e9f-131">To do this, you pass the custom sort procedure to the sort class at run time, using delegates.</span></span>  
  
## <a name="addressof-and-lambda-expressions"></a><span data-ttu-id="32e9f-132">AddressOf 和 Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="32e9f-132">AddressOf and Lambda Expressions</span></span>  
 <span data-ttu-id="32e9f-133">每個委派類別會為傳遞的建構函式定義物件方法的規格。</span><span class="sxs-lookup"><span data-stu-id="32e9f-133">Each delegate class defines a constructor that is passed the specification of an object method.</span></span> <span data-ttu-id="32e9f-134">對委派建構函式的引數必須是對方法的參考或 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="32e9f-134">An argument to a delegate constructor must be a reference to a method, or a lambda expression.</span></span>  
  
 <span data-ttu-id="32e9f-135">若要指定對方法的參考，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="32e9f-135">To specify a reference to a method, use the following syntax:</span></span>  
  
 <span data-ttu-id="32e9f-136">`AddressOf` [`expression`.]`methodName`</span><span class="sxs-lookup"><span data-stu-id="32e9f-136">`AddressOf` [`expression`.]`methodName`</span></span>  
  
 <span data-ttu-id="32e9f-137">`expression` 的編譯時期型別必須是類別或介面的名稱，而該類別或介面包含其簽章符合委派類別簽章的特定名稱方法。</span><span class="sxs-lookup"><span data-stu-id="32e9f-137">The compile-time type of the `expression` must be the name of a class or an interface that contains a method of the specified name whose signature matches the signature of the delegate class.</span></span> <span data-ttu-id="32e9f-138">`methodName` 可以是共用的方法或執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="32e9f-138">The `methodName` can be either a shared method or an instance method.</span></span> <span data-ttu-id="32e9f-139">`methodName` 不是選擇性的，即使您為類別的預設方法建立了委派也一樣。</span><span class="sxs-lookup"><span data-stu-id="32e9f-139">The `methodName` is not optional, even if you create a delegate for the default method of the class.</span></span>  
  
 <span data-ttu-id="32e9f-140">若要指定 lambda 運算式，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="32e9f-140">To specify a lambda expression, use the following syntax:</span></span>  
  
 <span data-ttu-id="32e9f-141">`Function` ([`parm` As `type`, `parm2` As `type2`, ...]) `expression`</span><span class="sxs-lookup"><span data-stu-id="32e9f-141">`Function` ([`parm` As `type`, `parm2` As `type2`, ...]) `expression`</span></span>  
  
 <span data-ttu-id="32e9f-142">下列範例示範用來指定委派參考的 `AddressOf` 和 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="32e9f-142">The following example shows both `AddressOf` and lambda expressions used to specify the reference for a delegate.</span></span>  
  
 [!code-vb[VbVbalrDelegates#15](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegates_3.vb)]  
  
 <span data-ttu-id="32e9f-143">函式的簽章必須符合委派型別的簽章。</span><span class="sxs-lookup"><span data-stu-id="32e9f-143">The signature of the function must match that of the delegate type.</span></span> <span data-ttu-id="32e9f-144">如需 Lambda 運算式的詳細資訊，請參閱 [Lambda 運算式](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="32e9f-144">For more information about lambda expressions, see [Lambda Expressions](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span> <span data-ttu-id="32e9f-145">如需 lambda 運算式以及要委派的 `AddressOf` 指派的更多範例，請參閱[寬鬆委派轉換](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)。</span><span class="sxs-lookup"><span data-stu-id="32e9f-145">For more examples of lambda expression and `AddressOf` assignments to delegates, see [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="32e9f-146">相關主題</span><span class="sxs-lookup"><span data-stu-id="32e9f-146">Related Topics</span></span>  
  
|<span data-ttu-id="32e9f-147">標題</span><span class="sxs-lookup"><span data-stu-id="32e9f-147">Title</span></span>|<span data-ttu-id="32e9f-148">描述</span><span class="sxs-lookup"><span data-stu-id="32e9f-148">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="32e9f-149">如何：叫用委派方法</span><span class="sxs-lookup"><span data-stu-id="32e9f-149">How to: Invoke a Delegate Method</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)|<span data-ttu-id="32e9f-150">提供範例，示範如何將方法和委派產生關聯，然後透過委派叫用該方法。</span><span class="sxs-lookup"><span data-stu-id="32e9f-150">Provides an example that shows how to associate a method with a delegate and then invoke that method through the delegate.</span></span>|  
|[<span data-ttu-id="32e9f-151">如何：在 Visual Basic 中將程序傳遞至其他程序</span><span class="sxs-lookup"><span data-stu-id="32e9f-151">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)|<span data-ttu-id="32e9f-152">示範如何使用委派，將一個程序傳遞至另一個程序。</span><span class="sxs-lookup"><span data-stu-id="32e9f-152">Demonstrates how to use delegates to pass one procedure to another procedure.</span></span>|  
|[<span data-ttu-id="32e9f-153">寬鬆委派轉換</span><span class="sxs-lookup"><span data-stu-id="32e9f-153">Relaxed Delegate Conversion</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)|<span data-ttu-id="32e9f-154">描述即便是 Sub 和函式的簽章不同，如何將它們指派給委派或處理常式。</span><span class="sxs-lookup"><span data-stu-id="32e9f-154">Describes how you can assign subs and functions to delegates or handlers even when their signatures are not identical</span></span>|  
|[<span data-ttu-id="32e9f-155">事件</span><span class="sxs-lookup"><span data-stu-id="32e9f-155">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)|<span data-ttu-id="32e9f-156">提供 Visual Basic 中的事件概觀。</span><span class="sxs-lookup"><span data-stu-id="32e9f-156">Provides an overview of events in Visual Basic.</span></span>|
