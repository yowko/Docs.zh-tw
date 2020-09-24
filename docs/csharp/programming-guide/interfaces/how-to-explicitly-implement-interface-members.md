---
title: '如何明確地執行介面成員-c # 程式設計指南'
description: '瞭解如何在此 c # 範例中明確地執行介面成員。 成員是透過介面實例來存取。'
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: a9c019cdcf6e229199d980a2d1913df7c72a2169
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157391"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a>如何 (c # 程式設計手冊) 明確地執行介面成員

這個範例會宣告 [介面](../../language-reference/keywords/interface.md)、 `IDimensions` 和類別，其會 `Box` 明確地執行介面成員 `GetLength` 和 `GetWidth` 。 成員是透過介面執行個體 `dimensions` 存取。  
  
## <a name="example"></a>範例  

 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a>穩固程式設計  
  
- 請注意，在 `Main` 方法中，下列各行因為會產生編譯錯誤所以都已註解。 從[類別](../../language-reference/keywords/class.md)執行個體無法存取已明確實作的介面成員：  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- 另請注意，在 `Main` 方法中，下列幾行會成功列印方塊大小，因為正從介面的執行個體呼叫方法：  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a>另請參閱

- [C # 程式設計指南](../index.md)
- [類別和結構](../classes-and-structs/index.md)
- [介面](./index.md)
- [如何明確實作兩個介面的成員](./how-to-explicitly-implement-members-of-two-interfaces.md)
