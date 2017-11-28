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
ms.openlocfilehash: 944b894e7e5f305d35d4db96d7426bf05322ca54
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-interface-events-c-programming-guide"></a>如何：實作介面事件 (C# 程式設計手冊)
[介面](../../../csharp/language-reference/keywords/interface.md)可以宣告[事件](../../../csharp/language-reference/keywords/event.md)。 下列範例示範如何在類別中實作介面事件。 基本上，規則與您在實作任何介面方法或屬性時相同。  
  
### <a name="to-implement-interface-events-in-a-class"></a>在類別中實作介面事件  
  
-   在類別中宣告事件，然後在適當的區域中加以叫用。  
  
    ```  
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
  
## <a name="example"></a>範例  
 下列範例示範如何處理以下較不常見的狀況：您的類別繼承自兩個或多個介面，且每個介面具有相同名稱的事件。 在此情況下，您必須針對其中至少一個事件提供明確介面實作。 當您針對事件撰寫明確介面實作時，也必須撰寫 `add` 和 `remove` 事件存取子。 這些通常是由編譯器所提供的，但在此案例中，編譯器無法提供它們。  
  
 您可以提供自己的存取子，來指定是否要透過類別中的相同事件或透過不同的事件來表示這兩個事件。 例如，如果根據介面規格應該在不同時間引發事件，則可以將每個事件與類別中的個別實作產生關聯。 在下列範例中，訂閱者會藉由將圖形參考轉換為 `IShape` 或 `IDrawingObject`，來判斷他們將接收哪些 `OnDraw` 事件。  
  
 [!code-csharp[csProgGuideEvents#10](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-implement-interface-events_1.cs)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [事件](../../../csharp/programming-guide/events/index.md)  
 [委派](../../../csharp/programming-guide/delegates/index.md)  
 [明確介面實作](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)  
 [如何：在衍生類別中引發基底類別事件](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)
