---
title: '如何訂閱和取消訂閱事件-c # 程式設計指南'
description: 瞭解如何訂閱和取消訂閱事件。 使用 Visual Studio IDE，以程式設計方式或使用匿名方法來訂閱事件。
ms.date: 07/20/2015
helpviewer_keywords:
- event handlers [C#], creating
- Code Editor, event handlers
- events [C#], creating using the IDE
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
ms.openlocfilehash: 1e090301982a785fed2a8a6a95ee48bd1c7457ab
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167479"
---
# <a name="how-to-subscribe-to-and-unsubscribe-from-events-c-programming-guide"></a><span data-ttu-id="5bdff-104">如何訂閱和取消訂閱事件 (c # 程式設計指南) </span><span class="sxs-lookup"><span data-stu-id="5bdff-104">How to subscribe to and unsubscribe from events (C# Programming Guide)</span></span>

<span data-ttu-id="5bdff-105">如果您想要撰寫在引發事件時所呼叫的自訂程式碼，您可以訂閱由其他類別發行的事件。</span><span class="sxs-lookup"><span data-stu-id="5bdff-105">You subscribe to an event that is published by another class when you want to write custom code that is called when that event is raised.</span></span> <span data-ttu-id="5bdff-106">例如，您可以訂閱某個按鈕的 `click` 事件，讓應用程式在使用者按下該按鈕時執行某項動作。</span><span class="sxs-lookup"><span data-stu-id="5bdff-106">For example, you might subscribe to a button's `click` event in order to make your application do something useful when the user clicks the button.</span></span>  
  
### <a name="to-subscribe-to-events-by-using-the-visual-studio-ide"></a><span data-ttu-id="5bdff-107">使用 Visual Studio IDE 訂閱事件</span><span class="sxs-lookup"><span data-stu-id="5bdff-107">To subscribe to events by using the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="5bdff-108">如果看不到 [屬性]\*\*\*\* 視窗，請在 [設計]\*\*\*\* 檢視中，以滑鼠右鍵按一下您要建立事件處理常式的表單或控制項，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5bdff-108">If you cannot see the **Properties** window, in **Design** view, right-click the form or control for which you want to create an event handler, and select **Properties**.</span></span>  
  
2. <span data-ttu-id="5bdff-109">在 [屬性]\*\*\*\* 視窗頂端，按一下**事件**圖示。</span><span class="sxs-lookup"><span data-stu-id="5bdff-109">On top of the **Properties** window, click the **Events** icon.</span></span>  
  
3. <span data-ttu-id="5bdff-110">按兩下您要建立的事件，例如 `Load` 事件。</span><span class="sxs-lookup"><span data-stu-id="5bdff-110">Double-click the event that you want to create, for example the `Load` event.</span></span>  
  
     <span data-ttu-id="5bdff-111">Visual C# 會建立空的事件處理常式方法，並將其新增至您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="5bdff-111">Visual C# creates an empty event handler method and adds it to your code.</span></span> <span data-ttu-id="5bdff-112">您也可以在 [程式碼]\*\*\*\* 檢視中手動新增程式碼。</span><span class="sxs-lookup"><span data-stu-id="5bdff-112">Alternatively you can add the code manually in **Code** view.</span></span> <span data-ttu-id="5bdff-113">例如，下列程式碼行會宣告一個事件處理常式方法，該方法將會在 `Form` 類別引發 `Load` 事件時呼叫。</span><span class="sxs-lookup"><span data-stu-id="5bdff-113">For example, the following lines of code declare an event handler method that will be called when the `Form` class raises the `Load` event.</span></span>  
  
     [!code-csharp[csProgGuideEvents#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#11)]  
  
     <span data-ttu-id="5bdff-114">訂閱事件所需的程式碼行也會在專案之 Form1.Designer.cs 檔案的 `InitializeComponent` 方法中自動產生。</span><span class="sxs-lookup"><span data-stu-id="5bdff-114">The line of code that is required to subscribe to the event is also automatically generated in the `InitializeComponent` method in the Form1.Designer.cs file in your project.</span></span> <span data-ttu-id="5bdff-115">看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="5bdff-115">It resembles this:</span></span>  
  
    ```csharp
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
### <a name="to-subscribe-to-events-programmatically"></a><span data-ttu-id="5bdff-116">以程式設計方式訂閱事件</span><span class="sxs-lookup"><span data-stu-id="5bdff-116">To subscribe to events programmatically</span></span>  
  
1. <span data-ttu-id="5bdff-117">定義事件處理常式方法，其簽章與事件的委派簽章相符。</span><span class="sxs-lookup"><span data-stu-id="5bdff-117">Define an event handler method whose signature matches the delegate signature for the event.</span></span> <span data-ttu-id="5bdff-118">例如，如果事件是以 <xref:System.EventHandler> 委派類型為基礎，則下列程式碼代表方法 Stub：</span><span class="sxs-lookup"><span data-stu-id="5bdff-118">For example, if the event is based on the <xref:System.EventHandler> delegate type, the following code represents the method stub:</span></span>  
  
    ```csharp
    void HandleCustomEvent(object sender, CustomEventArgs a)  
    {  
       // Do something useful here.  
    }  
    ```  
  
2. <span data-ttu-id="5bdff-119">請使用加法指派運算子 (`+=`) 來將事件處理常式附加到事件。</span><span class="sxs-lookup"><span data-stu-id="5bdff-119">Use the addition assignment operator (`+=`) to attach an event handler to the event.</span></span> <span data-ttu-id="5bdff-120">在下列範例中，假設名為 `publisher` 的物件具有名為 `RaiseCustomEvent` 的事件。</span><span class="sxs-lookup"><span data-stu-id="5bdff-120">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent`.</span></span> <span data-ttu-id="5bdff-121">請注意，subscriber 類別需要參考 publisher 類別，才能訂閱其事件。</span><span class="sxs-lookup"><span data-stu-id="5bdff-121">Note that the subscriber class needs a reference to the publisher class in order to subscribe to its events.</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="5bdff-122">請注意，以上的語法是 C# 2.0 中新增的語法。</span><span class="sxs-lookup"><span data-stu-id="5bdff-122">Note that the previous syntax is new in C# 2.0.</span></span> <span data-ttu-id="5bdff-123">該語法與 C# 1.0 語法完全相同，都必須使用 `new` 關鍵字明確建立封裝委派：</span><span class="sxs-lookup"><span data-stu-id="5bdff-123">It is exactly equivalent to the C# 1.0 syntax in which the encapsulating delegate must be explicitly created by using the `new` keyword:</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += new CustomEventHandler(HandleCustomEvent);  
    ```  
  
     <span data-ttu-id="5bdff-124">您也可以使用 [lambda 運算式](../../language-reference/operators/lambda-expressions.md) 來指定事件處理常式：</span><span class="sxs-lookup"><span data-stu-id="5bdff-124">You can also use a [lambda expression](../../language-reference/operators/lambda-expressions.md) to specify an event handler:</span></span>
  
    ```csharp
    public Form1()  
    {  
        InitializeComponent();  
        this.Click += (s,e) =>
            {
                MessageBox.Show(((MouseEventArgs)e).Location.ToString());
            };
    }  
    ```  
  
### <a name="to-subscribe-to-events-by-using-an-anonymous-method"></a><span data-ttu-id="5bdff-125">使用匿名方法訂閱事件</span><span class="sxs-lookup"><span data-stu-id="5bdff-125">To subscribe to events by using an anonymous method</span></span>  
  
- <span data-ttu-id="5bdff-126">如果您稍後不需要取消訂閱事件，您可以使用加法指派運算子 (`+=`) 將匿名方法附加至事件。</span><span class="sxs-lookup"><span data-stu-id="5bdff-126">If you will not have to unsubscribe to an event later, you can use the addition assignment operator (`+=`) to attach an anonymous method to the event.</span></span> <span data-ttu-id="5bdff-127">在下列範例中，假設名為 `publisher` 的物件具有名為 `RaiseCustomEvent` 的事件，而且也已定義 `CustomEventArgs` 類別來包含特定類型的特製化事件資訊。</span><span class="sxs-lookup"><span data-stu-id="5bdff-127">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent` and that a `CustomEventArgs` class has also been defined to carry some kind of specialized event information.</span></span> <span data-ttu-id="5bdff-128">請注意，subscriber 類別需要參考 `publisher`，才能訂閱其事件。</span><span class="sxs-lookup"><span data-stu-id="5bdff-128">Note that the subscriber class needs a reference to `publisher` in order to subscribe to its events.</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += delegate(object o, CustomEventArgs e)  
    {  
      string s = o.ToString() + " " + e.ToString();  
      Console.WriteLine(s);  
    };  
    ```  
  
     <span data-ttu-id="5bdff-129">請務必注意，如果使用了匿名函式訂閱事件，則無法輕易取消訂閱事件。</span><span class="sxs-lookup"><span data-stu-id="5bdff-129">It is important to notice that you cannot easily unsubscribe from an event if you used an anonymous function to subscribe to it.</span></span> <span data-ttu-id="5bdff-130">若要在這種情況下取消訂閱，您必須回到訂閱事件所在的程式碼，將此匿名方法儲存在委派變數中，然後將委派新增至事件。</span><span class="sxs-lookup"><span data-stu-id="5bdff-130">To unsubscribe in this scenario, it is necessary to go back to the code where you subscribe to the event, store the anonymous method in a delegate variable, and then add the delegate to the event.</span></span> <span data-ttu-id="5bdff-131">一般而言，如果您稍後必須在程式碼中取消訂閱事件，建議您不要使用匿名函式訂閱事件。</span><span class="sxs-lookup"><span data-stu-id="5bdff-131">In general, we recommend that you do not use anonymous functions to subscribe to events if you will have to unsubscribe from the event at some later point in your code.</span></span> <span data-ttu-id="5bdff-132">如需匿名函式的詳細資訊，請參閱[匿名函式](../statements-expressions-operators/anonymous-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="5bdff-132">For more information about anonymous functions, see [Anonymous Functions](../statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="unsubscribing"></a><span data-ttu-id="5bdff-133">取消訂閱</span><span class="sxs-lookup"><span data-stu-id="5bdff-133">Unsubscribing</span></span>  

 <span data-ttu-id="5bdff-134">若要防止在引發事件時叫用事件處理常式，請取消訂閱事件。</span><span class="sxs-lookup"><span data-stu-id="5bdff-134">To prevent your event handler from being invoked when the event is raised, unsubscribe from the event.</span></span> <span data-ttu-id="5bdff-135">為了避免資源流失，請先取消訂閱事件，再處置訂閱者物件。</span><span class="sxs-lookup"><span data-stu-id="5bdff-135">In order to prevent resource leaks, you should unsubscribe from events before you dispose of a subscriber object.</span></span> <span data-ttu-id="5bdff-136">在取消訂閱事件之前，發行物件的事件之下的多點傳送委派都會參考封裝訂閱者事件處理常式的委派。</span><span class="sxs-lookup"><span data-stu-id="5bdff-136">Until you unsubscribe from an event, the multicast delegate that underlies the event in the publishing object has a reference to the delegate that encapsulates the subscriber's event handler.</span></span> <span data-ttu-id="5bdff-137">只要發行物件還有該參考，記憶體回收就不會刪除訂閱者物件。</span><span class="sxs-lookup"><span data-stu-id="5bdff-137">As long as the publishing object holds that reference, garbage collection will not delete your subscriber object.</span></span>  
  
#### <a name="to-unsubscribe-from-an-event"></a><span data-ttu-id="5bdff-138">取消訂閱事件</span><span class="sxs-lookup"><span data-stu-id="5bdff-138">To unsubscribe from an event</span></span>  
  
- <span data-ttu-id="5bdff-139">使用減法指派運算子 (`-=`) 取消訂閱事件：</span><span class="sxs-lookup"><span data-stu-id="5bdff-139">Use the subtraction assignment operator (`-=`) to unsubscribe from an event:</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="5bdff-140">在所有訂閱者都已取消訂閱事件之後，publisher 類別中的事件執行個體會設定為 `null`。</span><span class="sxs-lookup"><span data-stu-id="5bdff-140">When all subscribers have unsubscribed from an event, the event instance in the publisher class is set to `null`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bdff-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5bdff-141">See also</span></span>

- [<span data-ttu-id="5bdff-142">事件</span><span class="sxs-lookup"><span data-stu-id="5bdff-142">Events</span></span>](./index.md)
- [<span data-ttu-id="5bdff-143">event</span><span class="sxs-lookup"><span data-stu-id="5bdff-143">event</span></span>](../../language-reference/keywords/event.md)
- [<span data-ttu-id="5bdff-144">如何發佈符合 .NET 指導方針的事件</span><span class="sxs-lookup"><span data-stu-id="5bdff-144">How to publish events that conform to .NET Guidelines</span></span>](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)
- [<span data-ttu-id="5bdff-145">- 及 = 運算子</span><span class="sxs-lookup"><span data-stu-id="5bdff-145">- and -= operators</span></span>](../../language-reference/operators/subtraction-operator.md)
- [<span data-ttu-id="5bdff-146">+ 及 + = 運算子</span><span class="sxs-lookup"><span data-stu-id="5bdff-146">+ and += operators</span></span>](../../language-reference/operators/addition-operator.md)
