---
title: 明確介面實作 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: 75b031773f8ac34b04f68ec01b12cd9263413bc3
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/01/2019
ms.locfileid: "57200139"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a>明確介面實作 (C# 程式設計手冊)
如果[類別](../../../csharp/language-reference/keywords/class.md)實作兩個具有相同簽章成員的介面，則在類別上實作該成員會造成這兩個介面都使用該成員進行實作。 在下列範例中，所有對 `Paint` 的呼叫都會叫用相同的方法。  
  
 [!code-csharp[csProgGuideInheritance#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#39)]  
  
 但如果兩個[介面](../../../csharp/language-reference/keywords/interface.md)成員不執行相同的函式，這可能會導致其中一或兩個介面實作不正確。 可能可以明確實作介面成員：建立只能透過介面呼叫且專屬於該介面的類別成員。 只要使用介面的名稱和句號命名類別成員，即可達成。 例如：  
  
 [!code-csharp[csProgGuideInheritance#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#40)]  
  
 類別成員 `IControl.Paint` 只能透過 `IControl` 介面取得，`ISurface.Paint` 只能透過 `ISurface` 取得。 這兩種方法實作是分開的，都無法直接在類別上使用。 例如：  
  
 [!code-csharp[csProgGuideInheritance#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#41)]  
  
 兩個介面各自宣告同名之不同成員的情況下，例如屬性和方法，也可以使用明確實作來解決：  
  
 [!code-csharp[csProgGuideInheritance#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#42)]  
  
 若要實作這兩個介面，類別必須針對屬性 P 或方法 P 或兩者使用明確的實作，來避免編譯器錯誤。 例如：  
  
 [!code-csharp[csProgGuideInheritance#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#43)]  
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md)
- [介面](../../../csharp/programming-guide/interfaces/index.md)
- [繼承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)
