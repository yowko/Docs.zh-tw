---
title: "如何：實作自訂事件存取子 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
caps.latest.revision: 7
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 71e1c16c9c6426ffb95020e4d7211dc1000f6796
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a>如何：實作自訂事件存取子 (C# 程式設計手冊)
事件是一種特殊的多點傳送委派，只能從宣告所在類別內叫用。 在事件引發時，用戶端程式碼透過提供應該叫用的方法參考，來訂閱事件。 這些方法會透過類似屬性存取子的事件存取子新增至委派叫用清單，不同之處在於事件存取子名為 `add` 和 `remove`。 在大部分情況下，您不必提供自訂事件存取子。 當程式碼中不提供任何自訂事件存取子時，編譯器會自動新增它們。 不過，在某些情況下，您可能必須提供自訂行為。 [如何：實作介面事件](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)主題示範其中一個這類案例。  
  
## <a name="example"></a>範例  
 下例示範如何實作自訂新增和移除事件存取子。 雖然您可以替代存取子中的任何程式碼，但建議您先鎖定事件，再新增或移除新的事件處理常式方法。  
  
```  
event EventHandler IDrawingObject.OnDraw  
        {  
            add  
            {  
                lock (PreDrawEvent)  
                {  
                    PreDrawEvent += value;  
                }  
            }  
            remove  
            {  
                lock (PreDrawEvent)  
                {  
                    PreDrawEvent -= value;  
                }  
            }  
        }  
```  
  
## <a name="see-also"></a>另請參閱  
 [事件](../../../csharp/programming-guide/events/index.md)   
 [event](../../../csharp/language-reference/keywords/event.md)

