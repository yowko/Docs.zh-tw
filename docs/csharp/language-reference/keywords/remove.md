---
title: "remove (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: remove_CSharpKeyword
helpviewer_keywords: remove event accessor [C#]
ms.assetid: c8223426-c17b-4fe2-8406-01564cf1dd2b
caps.latest.revision: "8"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 66647dee0c4cc728ae5e19457a4a5ef0e7f72248
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2017
---
# <a name="remove-c-reference"></a>remove (C# 參考)
使用 `remove` 內容關鍵字定義自訂事件存取子，以在用戶端程式碼取消訂閱[事件](../../../csharp/language-reference/keywords/event.md)時叫用。 如果您提供自訂 `remove` 存取子，則也必須提供 [add](../../../csharp/language-reference/keywords/add.md) 存取子。  
  
## <a name="example"></a>範例  
 下列範例示範具有自訂 [add](../../../csharp/language-reference/keywords/add.md) 和 `remove` 存取子的事件。 如需完整範例，請參閱[如何：實作介面事件](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)。  
  
 [!code-csharp[csrefKeywordsContextual#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/remove_1.cs)]  
  
 您通常不需要提供自己的自訂事件存取子。 宣告事件時編譯器自動產生的存取子，足以應付大部分的狀況。  
  
## <a name="see-also"></a>另請參閱  
 [事件](../../../csharp/programming-guide/events/index.md)
