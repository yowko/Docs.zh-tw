---
title: "如何：實作介面事件 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- interfaces [C#], event implementation in classes
- events [C#], in interfaces
ms.assetid: 63527447-9535-4880-8e95-35e2075827df
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a53c6ba29837ad8827d97ea745be0462451eb145
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2018
---
# <a name="how-to-implement-interface-events-c-programming-guide"></a><span data-ttu-id="33625-102">如何：實作介面事件 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="33625-102">How to: Implement Interface Events (C# Programming Guide)</span></span>
<span data-ttu-id="33625-103">[介面](../../../csharp/language-reference/keywords/interface.md)可以宣告[事件](../../../csharp/language-reference/keywords/event.md)。</span><span class="sxs-lookup"><span data-stu-id="33625-103">An [interface](../../../csharp/language-reference/keywords/interface.md) can declare an [event](../../../csharp/language-reference/keywords/event.md).</span></span> <span data-ttu-id="33625-104">下列範例示範如何在類別中實作介面事件。</span><span class="sxs-lookup"><span data-stu-id="33625-104">The following example shows how to implement interface events in a class.</span></span> <span data-ttu-id="33625-105">基本上，規則與您在實作任何介面方法或屬性時相同。</span><span class="sxs-lookup"><span data-stu-id="33625-105">Basically the rules are the same as when you implement any interface method or property.</span></span>  
  
### <a name="to-implement-interface-events-in-a-class"></a><span data-ttu-id="33625-106">在類別中實作介面事件</span><span class="sxs-lookup"><span data-stu-id="33625-106">To implement interface events in a class</span></span>  
  
-   <span data-ttu-id="33625-107">在類別中宣告事件，然後在適當的區域中加以叫用。</span><span class="sxs-lookup"><span data-stu-id="33625-107">Declare the event in your class and then invoke it in the appropriate areas.</span></span>  
  
    ```csharp
    namespace ImplementInterfaceEvents  
    {  
        public interface IDrawingObject  
        {  
            event EventHandler ShapeChanged;  
        }  
        public class MyEventArgs : EventArgs   
        {  
            // class members  
        }  
        public class Shape : IDrawingObject  
        {  
            public event EventHandler ShapeChanged;  
            void ChangeShape()  
            {  
                // Do something here before the event…  
  
                OnShapeChanged(new MyEventArgs(/*arguments*/));  
  
                // or do something here after the event.   
            }  
            protected virtual void OnShapeChanged(MyEventArgs e)  
            {  
                if(ShapeChanged != null)  
                {  
                   ShapeChanged(this, e);  
                }  
            }  
        }  
  
    }  
    ```  
  
## <a name="example"></a><span data-ttu-id="33625-108">範例</span><span class="sxs-lookup"><span data-stu-id="33625-108">Example</span></span>  
 <span data-ttu-id="33625-109">下列範例示範如何處理以下較不常見的狀況：您的類別繼承自兩個或多個介面，且每個介面具有相同名稱的事件。</span><span class="sxs-lookup"><span data-stu-id="33625-109">The following example shows how to handle the less-common situation in which your class inherits from two or more interfaces and each interface has an event with the same name.</span></span> <span data-ttu-id="33625-110">在此情況下，您必須針對其中至少一個事件提供明確介面實作。</span><span class="sxs-lookup"><span data-stu-id="33625-110">In this situation, you must provide an explicit interface implementation for at least one of the events.</span></span> <span data-ttu-id="33625-111">當您針對事件撰寫明確介面實作時，也必須撰寫 `add` 和 `remove` 事件存取子。</span><span class="sxs-lookup"><span data-stu-id="33625-111">When you write an explicit interface implementation for an event, you must also write the `add` and `remove` event accessors.</span></span> <span data-ttu-id="33625-112">這些通常是由編譯器所提供的，但在此案例中，編譯器無法提供它們。</span><span class="sxs-lookup"><span data-stu-id="33625-112">Normally these are provided by the compiler, but in this case the compiler cannot provide them.</span></span>  
  
 <span data-ttu-id="33625-113">您可以提供自己的存取子，來指定是否要透過類別中的相同事件或透過不同的事件來表示這兩個事件。</span><span class="sxs-lookup"><span data-stu-id="33625-113">By providing your own accessors, you can specify whether the two events are represented by the same event in your class, or by different events.</span></span> <span data-ttu-id="33625-114">例如，如果根據介面規格應該在不同時間引發事件，則可以將每個事件與類別中的個別實作產生關聯。</span><span class="sxs-lookup"><span data-stu-id="33625-114">For example, if the events should be raised at different times according to the interface specifications, you can associate each event with a separate implementation in your class.</span></span> <span data-ttu-id="33625-115">在下列範例中，訂閱者會藉由將圖形參考轉換為 `IShape` 或 `IDrawingObject`，來判斷他們將接收哪些 `OnDraw` 事件。</span><span class="sxs-lookup"><span data-stu-id="33625-115">In the following example, subscribers determine which `OnDraw` event they will receive by casting the shape reference to either an `IShape` or an `IDrawingObject`.</span></span>  
  
 [!code-csharp[csProgGuideEvents#10](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-implement-interface-events_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="33625-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="33625-116">See Also</span></span>  
 [<span data-ttu-id="33625-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="33625-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="33625-118">事件</span><span class="sxs-lookup"><span data-stu-id="33625-118">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
 [<span data-ttu-id="33625-119">委派</span><span class="sxs-lookup"><span data-stu-id="33625-119">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="33625-120">明確介面實作</span><span class="sxs-lookup"><span data-stu-id="33625-120">Explicit Interface Implementation</span></span>](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)  
 [<span data-ttu-id="33625-121">如何：在衍生類別中引發基底類別事件</span><span class="sxs-lookup"><span data-stu-id="33625-121">How to: Raise Base Class Events in Derived Classes</span></span>](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)
