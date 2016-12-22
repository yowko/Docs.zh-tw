---
title: "如何：實作介面事件 (C# 程式設計手冊) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "事件 [C#], 介面中"
  - "介面 [C#], 類別中的事件實作"
ms.assetid: 63527447-9535-4880-8e95-35e2075827df
caps.latest.revision: 21
caps.handback.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 如何：實作介面事件 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

[介面](../../../csharp/language-reference/keywords/interface.md)可以宣告[事件](../../../csharp/language-reference/keywords/event.md)。  下列範例會示範如何在類別內實作介面事件，  其規則基本上與實作任何介面方法或屬性相同。  
  
### 若要在類別內實作介面事件  
  
-   在類別內宣告該事件，然後在適當的區域予以叫用。  
  
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
  
## 範例  
 下列範例會示範如何處理一個較不常見的狀況，也就是您的類別繼承自兩個或多個介面，而每一個介面都有一個同名的事件。  在這種情形下，您至少必須為其中一個事件提供明確的介面實作 \(Implementation\)。  當您為事件撰寫明確的介面實作時，也必須撰寫 `add` 和 `remove` 事件存取子 \(Accessor\)。  通常這些事件存取子是由編譯器 \(Compiler\) 所提供，但在這個情況下，編譯器無法提供這些事件存取子。  
  
 提供您自己的存取子後，您就可以指定這兩個事件會以類別內的相同事件還是不同事件來表示。  例如，如果根據介面的指定，事件應該在不同時間引發，您便可以讓每一個事件與類別內的各個實作產生關聯。  在下列範例中，訂閱者會藉由轉換 `IShape` 或 `IDrawingObject` 的圖案參考，以判斷將會接收到哪一個 `OnDraw` 事件。  
  
 [!code-cs[csProgGuideEvents#10](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-implement-interface-events_1.cs)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [事件](../../../csharp/programming-guide/events/index.md)   
 [委派](../../../visual-basic/reference/command-line-compiler/index.md)   
 [明確介面實作](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)   
 [如何：在衍生類別中引發基底類別事件](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)