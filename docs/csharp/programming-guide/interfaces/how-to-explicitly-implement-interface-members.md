---
title: 如何明確執行介面成員-程式C#設計指南
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: dff094aca237ed6146bd9b52813c40549bc99b9b
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627781"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a>如何明確執行介面成員（C#程式設計手冊）
這個範例會宣告[介面](../../language-reference/keywords/interface.md) (`IDimensions`) 和類別 (`Box`)，它會明確實作介面成員 `GetLength` 和 `GetWidth`。 成員是透過介面執行個體 `dimensions` 存取。  
  
## <a name="example"></a>範例  
 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a>最佳化程式設計  
  
- 請注意，在 `Main` 方法中，下列各行因為會產生編譯錯誤所以都已註解。 從[類別](../../language-reference/keywords/class.md)執行個體無法存取已明確實作的介面成員：  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- 另請注意，在 `Main` 方法中，下列幾行會成功列印方塊大小，因為正從介面的執行個體呼叫方法：  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../index.md)
- [類別和結構](../classes-and-structs/index.md)
- [介面](./index.md)
- [如何明確地執行兩個介面的成員](./how-to-explicitly-implement-members-of-two-interfaces.md)
