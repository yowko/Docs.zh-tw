---
title: 作法：明確實作介面成員 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: d5630065ae1fbfceca9ce3b5180664bba3a104a6
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/01/2019
ms.locfileid: "57201868"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a>作法：明確實作介面成員 (C# 程式設計指南)
這個範例會宣告[介面](../../../csharp/language-reference/keywords/interface.md) (`IDimensions`) 和類別 (`Box`)，它會明確實作介面成員 `getLength` 和 `getWidth`。 成員是透過介面執行個體 `dimensions` 存取。  
  
## <a name="example"></a>範例  
 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a>穩固程式設計  
  
-   請注意，在 `Main` 方法中，下列各行因為會產生編譯錯誤所以都已註解。 從[類別](../../../csharp/language-reference/keywords/class.md)執行個體無法存取已明確實作的介面成員：  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
-   另請注意，在 `Main` 方法中，下列幾行會成功列印方塊大小，因為正從介面的執行個體呼叫方法：  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md)
- [介面](../../../csharp/programming-guide/interfaces/index.md)
- [如何：明確實作兩個介面的成員](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md)
