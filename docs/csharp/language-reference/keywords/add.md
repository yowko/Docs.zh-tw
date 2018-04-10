---
title: add (C# 參考)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- add_CSharpKeyword
helpviewer_keywords:
- add event accessor [C#]
ms.assetid: faf30b99-10e8-45cd-ab9a-57585d4d1d8d
caps.latest.revision: 7
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cab77ad5a990cf85075455e347a4b1c02645af37
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2017
---
# <a name="add-c-reference"></a>add (C# 參考)
使用 `add` 內容關鍵字定義自訂事件存取子，以在用戶端程式碼訂閱[事件](../../../csharp/language-reference/keywords/event.md)時叫用。 如果提供自訂的 `add` 存取子，您也必須提供 [remove](../../../csharp/language-reference/keywords/remove.md) 存取子。  
  
## <a name="example"></a>範例  
 下例示範具有自訂 `add` 和 [remove](../../../csharp/language-reference/keywords/remove.md) 存取子的事件。 如需完整範例，請參閱[如何：實作介面事件](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)。  
  
 [!code-csharp[csrefKeywordsContextual#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/add_1.cs)]  
  
 您通常不需要提供自己的自訂事件存取子。 宣告事件時編譯器自動產生的存取子，足以應付大部分的狀況。  
  
## <a name="see-also"></a>另請參閱  
 [事件](../../../csharp/programming-guide/events/index.md)
