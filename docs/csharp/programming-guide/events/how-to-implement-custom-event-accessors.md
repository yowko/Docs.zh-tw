---
title: "如何：實作自訂事件存取子 (C# 程式設計手冊) | Microsoft Docs"
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
  - "存取子 [C#], 事件存取子"
  - "add 存取子 [C#]"
  - "事件 [C#], add 存取子"
  - "事件 [C#], remove 存取子"
  - "remove 存取子 [C#]"
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 如何：實作自訂事件存取子 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

事件是一種特殊的多點傳送委派，只能從宣告該事件的類別內叫用。  用戶端程式碼會藉由提供事件發生時應叫用的方法參考來訂閱事件。  這些方法會透過事件存取子加入委派的叫用清單中，這些存取子與屬性存取子類似，其差異在於事件存取子為具名的 `add` 和 `remove`。  大部分情況下，您不需要提供自訂的事件存取子。  當程式碼中沒有提供任何自訂的事件存取子時，編譯器會自動將它們加入。  不過，在某些情況下，您可能必須提供自訂行為。  其中一個案例如主題 [如何：實作介面事件](../../../csharp/programming-guide/events/how-to-implement-interface-events.md) 中所示。  
  
## 範例  
 以下範例說明如何實作自訂的 add 和 remove 事件存取子。  即使您可以替換存取子中的任何程式碼，仍建議您在加入或移除新的事件處理常式方法之前，先鎖定事件。  
  
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
  
## 請參閱  
 [事件](../../../csharp/programming-guide/events/index.md)   
 [event](../../../csharp/language-reference/keywords/event.md)