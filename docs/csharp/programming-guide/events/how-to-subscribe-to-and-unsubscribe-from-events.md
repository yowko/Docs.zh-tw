---
title: "如何：訂閱及取消訂閱事件 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- event handlers [C#], creating
- Code Editor, event handlers
- events [C#], creating using the IDE
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: deeed6f6b572e04780f0eda1e7e42f1dd6233567
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-subscribe-to-and-unsubscribe-from-events-c-programming-guide"></a><span data-ttu-id="af8bc-102">如何：訂閱及取消訂閱事件 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="af8bc-102">How to: Subscribe to and Unsubscribe from Events (C# Programming Guide)</span></span>
<span data-ttu-id="af8bc-103">如果您想要撰寫在引發事件時所呼叫的自訂程式碼，您可以訂閱由其他類別發行的事件。</span><span class="sxs-lookup"><span data-stu-id="af8bc-103">You subscribe to an event that is published by another class when you want to write custom code that is called when that event is raised.</span></span> <span data-ttu-id="af8bc-104">例如，您可以訂閱某個按鈕的 `click` 事件，讓應用程式在使用者按下該按鈕時執行某項動作。</span><span class="sxs-lookup"><span data-stu-id="af8bc-104">For example, you might subscribe to a button's `click` event in order to make your application do something useful when the user clicks the button.</span></span>  
  
### <a name="to-subscribe-to-events-by-using-the-visual-studio-ide"></a><span data-ttu-id="af8bc-105">使用 Visual Studio IDE 訂閱事件</span><span class="sxs-lookup"><span data-stu-id="af8bc-105">To subscribe to events by using the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="af8bc-106">如果看不到 [屬性] 視窗，請在 [設計] 檢視中，以滑鼠右鍵按一下您要建立事件處理常式的表單或控制項，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="af8bc-106">If you cannot see the **Properties** window, in **Design** view, right-click the form or control for which you want to create an event handler, and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="af8bc-107">在 [屬性] 視窗頂端，按一下**事件**圖示。</span><span class="sxs-lookup"><span data-stu-id="af8bc-107">On top of the **Properties** window, click the **Events** icon.</span></span>  
  
3.  <span data-ttu-id="af8bc-108">按兩下您要建立的事件，例如 `Load` 事件。</span><span class="sxs-lookup"><span data-stu-id="af8bc-108">Double-click the event that you want to create, for example the `Load` event.</span></span>  
  
     [!INCLUDE[csprcs](~/includes/csprcs-md.md)]<span data-ttu-id="af8bc-109"> 會建立空的事件處理常式方法，並將其新增至您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="af8bc-109"> creates an empty event handler method and adds it to your code.</span></span> <span data-ttu-id="af8bc-110">您也可以在 [程式碼] 檢視中手動新增程式碼。</span><span class="sxs-lookup"><span data-stu-id="af8bc-110">Alternatively you can add the code manually in **Code** view.</span></span> <span data-ttu-id="af8bc-111">例如，下列程式碼行會宣告一個事件處理常式方法，該方法將會在 `Form` 類別引發 `Load` 事件時呼叫。</span><span class="sxs-lookup"><span data-stu-id="af8bc-111">For example, the following lines of code declare an event handler method that will be called when the `Form` class raises the `Load` event.</span></span>  
  
     [!code-csharp[csProgGuideEvents#11](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-subscribe-to-and-unsubscribe-from-events_1.cs)]  
  
     <span data-ttu-id="af8bc-112">訂閱事件所需的程式碼行也會在專案之 Form1.Designer.cs 檔案的 `InitializeComponent` 方法中自動產生。</span><span class="sxs-lookup"><span data-stu-id="af8bc-112">The line of code that is required to subscribe to the event is also automatically generated in the `InitializeComponent` method in the Form1.Designer.cs file in your project.</span></span> <span data-ttu-id="af8bc-113">看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="af8bc-113">It resembles this:</span></span>  
  
    ```  
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
### <a name="to-subscribe-to-events-programmatically"></a><span data-ttu-id="af8bc-114">以程式設計方式訂閱事件</span><span class="sxs-lookup"><span data-stu-id="af8bc-114">To subscribe to events programmatically</span></span>  
  
1.  <span data-ttu-id="af8bc-115">定義事件處理常式方法，其簽章與事件的委派簽章相符。</span><span class="sxs-lookup"><span data-stu-id="af8bc-115">Define an event handler method whose signature matches the delegate signature for the event.</span></span> <span data-ttu-id="af8bc-116">例如，如果事件是以 <xref:System.EventHandler> 委派類型為基礎，則下列程式碼代表方法 Stub：</span><span class="sxs-lookup"><span data-stu-id="af8bc-116">For example, if the event is based on the <xref:System.EventHandler> delegate type, the following code represents the method stub:</span></span>  
  
    ```  
    void HandleCustomEvent(object sender, CustomEventArgs a)  
    {  
       // Do something useful here.  
    }  
    ```  
  
2.  <span data-ttu-id="af8bc-117">使用加法指派運算子 (`+=`) 將事件處理常式附加至事件。</span><span class="sxs-lookup"><span data-stu-id="af8bc-117">Use the addition assignment operator (`+=`) to attach your event handler to the event.</span></span> <span data-ttu-id="af8bc-118">在下列範例中，假設名為 `publisher` 的物件具有名為 `RaiseCustomEvent` 的事件。</span><span class="sxs-lookup"><span data-stu-id="af8bc-118">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent`.</span></span> <span data-ttu-id="af8bc-119">請注意，subscriber 類別需要參考 publisher 類別，才能訂閱其事件。</span><span class="sxs-lookup"><span data-stu-id="af8bc-119">Note that the subscriber class needs a reference to the publisher class in order to subscribe to its events.</span></span>  
  
    ```  
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="af8bc-120">請注意，以上的語法是 C# 2.0 中新增的語法。</span><span class="sxs-lookup"><span data-stu-id="af8bc-120">Note that the previous syntax is new in C# 2.0.</span></span> <span data-ttu-id="af8bc-121">該語法與 C# 1.0 語法完全相同，都必須使用 `new` 關鍵字明確建立封裝委派：</span><span class="sxs-lookup"><span data-stu-id="af8bc-121">It is exactly equivalent to the C# 1.0 syntax in which the encapsulating delegate must be explicitly created by using the `new` keyword:</span></span>  
  
    ```  
    publisher.RaiseCustomEvent += new CustomEventHandler(HandleCustomEvent);  
    ```  
  
     <span data-ttu-id="af8bc-122">您也可以使用 Lambda 運算式新增事件處理常式：</span><span class="sxs-lookup"><span data-stu-id="af8bc-122">An event handler can also be added by using a lambda expression:</span></span>  
  
    ```  
    public Form1()  
    {  
        InitializeComponent();  
        // Use a lambda expression to define an event handler.  
        this.Click += (s,e) => { MessageBox.Show(  
           ((MouseEventArgs)e).Location.ToString());};  
    }  
    ```  
  
     <span data-ttu-id="af8bc-123">如需詳細資訊，請參閱[如何：在 LINQ 之外使用 Lambda 運算式](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="af8bc-123">For more information, see [How to: Use Lambda Expressions Outside LINQ](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md).</span></span>  
  
### <a name="to-subscribe-to-events-by-using-an-anonymous-method"></a><span data-ttu-id="af8bc-124">使用匿名方法訂閱事件</span><span class="sxs-lookup"><span data-stu-id="af8bc-124">To subscribe to events by using an anonymous method</span></span>  
  
-   <span data-ttu-id="af8bc-125">如果您稍後不需要取消訂閱事件，您可以使用加法指派運算子 (`+=`) 將匿名方法附加至事件。</span><span class="sxs-lookup"><span data-stu-id="af8bc-125">If you will not have to unsubscribe to an event later, you can use the addition assignment operator (`+=`) to attach an anonymous method to the event.</span></span> <span data-ttu-id="af8bc-126">在下列範例中，假設名為 `publisher` 的物件具有名為 `RaiseCustomEvent` 的事件，而且也已定義 `CustomEventArgs` 類別來包含特定類型的特製化事件資訊。</span><span class="sxs-lookup"><span data-stu-id="af8bc-126">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent` and that a `CustomEventArgs` class has also been defined to carry some kind of specialized event information.</span></span> <span data-ttu-id="af8bc-127">請注意，subscriber 類別需要參考 `publisher`，才能訂閱其事件。</span><span class="sxs-lookup"><span data-stu-id="af8bc-127">Note that the subscriber class needs a reference to `publisher` in order to subscribe to its events.</span></span>  
  
    ```  
    publisher.RaiseCustomEvent += delegate(object o, CustomEventArgs e)  
    {  
      string s = o.ToString() + " " + e.ToString();  
      Console.WriteLine(s);  
    };  
    ```  
  
     <span data-ttu-id="af8bc-128">請務必注意，如果使用了匿名函式訂閱事件，則無法輕易取消訂閱事件。</span><span class="sxs-lookup"><span data-stu-id="af8bc-128">It is important to notice that you cannot easily unsubscribe from an event if you used an anonymous function to subscribe to it.</span></span> <span data-ttu-id="af8bc-129">若要在這種情況下取消訂閱，您必須回到訂閱事件所在的程式碼，將此匿名方法儲存在委派變數中，然後將委派新增至事件。</span><span class="sxs-lookup"><span data-stu-id="af8bc-129">To unsubscribe in this scenario, it is necessary to go back to the code where you subscribe to the event, store the anonymous method in a delegate variable, and then add the delegate to the event.</span></span> <span data-ttu-id="af8bc-130">一般而言，如果您稍後必須在程式碼中取消訂閱事件，建議您不要使用匿名函式訂閱事件。</span><span class="sxs-lookup"><span data-stu-id="af8bc-130">In general, we recommend that you do not use anonymous functions to subscribe to events if you will have to unsubscribe from the event at some later point in your code.</span></span> <span data-ttu-id="af8bc-131">如需匿名函式的詳細資訊，請參閱[匿名函式](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="af8bc-131">For more information about anonymous functions, see [Anonymous Functions](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="unsubscribing"></a><span data-ttu-id="af8bc-132">取消訂閱</span><span class="sxs-lookup"><span data-stu-id="af8bc-132">Unsubscribing</span></span>  
 <span data-ttu-id="af8bc-133">若要防止在引發事件時叫用事件處理常式，請取消訂閱事件。</span><span class="sxs-lookup"><span data-stu-id="af8bc-133">To prevent your event handler from being invoked when the event is raised, unsubscribe from the event.</span></span> <span data-ttu-id="af8bc-134">為了避免資源流失，請先取消訂閱事件，再處置訂閱者物件。</span><span class="sxs-lookup"><span data-stu-id="af8bc-134">In order to prevent resource leaks, you should unsubscribe from events before you dispose of a subscriber object.</span></span> <span data-ttu-id="af8bc-135">在取消訂閱事件之前，發行物件的事件之下的多點傳送委派都會參考封裝訂閱者事件處理常式的委派。</span><span class="sxs-lookup"><span data-stu-id="af8bc-135">Until you unsubscribe from an event, the multicast delegate that underlies the event in the publishing object has a reference to the delegate that encapsulates the subscriber's event handler.</span></span> <span data-ttu-id="af8bc-136">只要發行物件還有該參考，記憶體回收就不會刪除訂閱者物件。</span><span class="sxs-lookup"><span data-stu-id="af8bc-136">As long as the publishing object holds that reference, garbage collection will not delete your subscriber object.</span></span>  
  
#### <a name="to-unsubscribe-from-an-event"></a><span data-ttu-id="af8bc-137">取消訂閱事件</span><span class="sxs-lookup"><span data-stu-id="af8bc-137">To unsubscribe from an event</span></span>  
  
-   <span data-ttu-id="af8bc-138">使用減法指派運算子 (`-=`) 取消訂閱事件：</span><span class="sxs-lookup"><span data-stu-id="af8bc-138">Use the subtraction assignment operator (`-=`) to unsubscribe from an event:</span></span>  
  
    ```  
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="af8bc-139">在所有訂閱者都已取消訂閱事件之後，publisher 類別中的事件執行個體會設定為 `null`。</span><span class="sxs-lookup"><span data-stu-id="af8bc-139">When all subscribers have unsubscribed from an event, the event instance in the publisher class is set to `null`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af8bc-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af8bc-140">See Also</span></span>  
 [<span data-ttu-id="af8bc-141">事件</span><span class="sxs-lookup"><span data-stu-id="af8bc-141">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
 [<span data-ttu-id="af8bc-142">event</span><span class="sxs-lookup"><span data-stu-id="af8bc-142">event</span></span>](../../../csharp/language-reference/keywords/event.md)  
 [<span data-ttu-id="af8bc-143">如何：發行符合 .NET Framework 方針的事件</span><span class="sxs-lookup"><span data-stu-id="af8bc-143">How to: Publish Events that Conform to .NET Framework Guidelines</span></span>](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
 [<span data-ttu-id="af8bc-144">-= 運算子 （C# 參考）</span><span class="sxs-lookup"><span data-stu-id="af8bc-144">-= Operator (C# Reference)</span></span>](../../language-reference/operators/subtraction-assignment-operator.md)  
 [<span data-ttu-id="af8bc-145">+= 運算子</span><span class="sxs-lookup"><span data-stu-id="af8bc-145">+= Operator</span></span>](../../../csharp/language-reference/operators/addition-assignment-operator.md)
