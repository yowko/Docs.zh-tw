---
title: "remove (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- remove_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- remove event accessor [C#]
ms.assetid: c8223426-c17b-4fe2-8406-01564cf1dd2b
caps.latest.revision: 8
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
ms.openlocfilehash: b34d653a40e1309e281235416c0399abc6dd9a0d
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="remove-c-reference"></a>remove (C# 參考)
使用 `remove` 內容關鍵字定義自訂事件存取子，以在用戶端程式碼取消訂閱[事件](../../../csharp/language-reference/keywords/event.md)時叫用。 如果您提供自訂 `remove` 存取子，則也必須提供 [add](../../../csharp/language-reference/keywords/add.md) 存取子。  
  
## <a name="example"></a>範例  
 下列範例示範具有自訂 [add](../../../csharp/language-reference/keywords/add.md) 和 `remove` 存取子的事件。 如需完整範例，請參閱[如何：實作介面事件](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)。  
  
 [!code-cs[csrefKeywordsContextual#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/remove_1.cs)]  
  
 您通常不需要提供自己的自訂事件存取子。 宣告事件時編譯器自動產生的存取子，足以應付大部分的狀況。  
  
## <a name="see-also"></a>另請參閱  
 [事件](../../../csharp/programming-guide/events/index.md)

