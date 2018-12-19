---
title: 明確介面實作 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: e985da878ca4160938f29911d4313ee6cd731aeb
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244826"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a>明確介面實作 (C# 程式設計手冊)
如果[類別](../../../csharp/language-reference/keywords/class.md)實作兩個具有相同簽章成員的介面，則在類別上實作該成員會造成這兩個介面都使用該成員進行實作。 在下列範例中，所有對 `Paint` 的呼叫都會叫用相同的方法。  
  
 [!code-csharp[csProgGuideInheritance#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_1.cs)]  
  
 但如果兩個[介面](../../../csharp/language-reference/keywords/interface.md)成員不執行相同的函式，這可能會導致其中一或兩個介面實作不正確。 可能可以明確實作介面成員：建立只能透過介面呼叫且專屬於該介面的類別成員。 只要使用介面的名稱和句號命名類別成員，即可達成。 例如:   
  
 [!code-csharp[csProgGuideInheritance#40](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_2.cs)]  
  
 類別成員 `IControl.Paint` 只能透過 `IControl` 介面取得，`ISurface.Paint` 只能透過 `ISurface` 取得。 這兩種方法實作是分開的，都無法直接在類別上使用。 例如:   
  
 [!code-csharp[csProgGuideInheritance#41](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_3.cs)]  
  
 兩個介面各自宣告同名之不同成員的情況下，例如屬性和方法，也可以使用明確實作來解決：  
  
 [!code-csharp[csProgGuideInheritance#42](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_4.cs)]  
  
 若要實作這兩個介面，類別必須針對屬性 P 或方法 P 或兩者使用明確的實作，來避免編譯器錯誤。 例如：  
  
 [!code-csharp[csProgGuideInheritance#43](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_5.cs)]  
  
## <a name="see-also"></a>請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [介面](../../../csharp/programming-guide/interfaces/index.md)  
- [繼承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)
