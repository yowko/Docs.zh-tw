---
title: 作法：實作自訂事件存取子 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
ms.openlocfilehash: 4eaf8b4c3038d07d5b0fc021e21c7f1a2de85d74
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590521"
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a>作法：實作自訂事件存取子 (C# 程式設計手冊)
事件是一種特殊的多點傳送委派，只能從宣告所在類別內叫用。 在事件引發時，用戶端程式碼透過提供應該叫用的方法參考，來訂閱事件。 這些方法會透過類似屬性存取子的事件存取子新增至委派叫用清單，不同之處在於事件存取子名為 `add` 和 `remove`。 在大部分情況下，您不必提供自訂事件存取子。 當程式碼中不提供任何自訂事件存取子時，編譯器會自動新增它們。 不過，在某些情況下，您可能必須提供自訂行為。 其中一個這類案例顯示於主題[如何：實作介面事件](./how-to-implement-interface-events.md)。  
  
## <a name="example"></a>範例  
 下例示範如何實作自訂新增和移除事件存取子。 雖然您可以替代存取子中的任何程式碼，但建議您先鎖定事件，再新增或移除新的事件處理常式方法。  
  
[!code-csharp[IDrawingObject.OnDraw](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#IDrawingObjectOnDraw)]  
  
## <a name="see-also"></a>另請參閱

- [事件](./index.md)
- [event](../../language-reference/keywords/event.md)
