---
title: 作法：明確實作兩個介面的成員 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
ms.openlocfilehash: 9e4805f2a9d1a4a18166ea7bcc8fbf8a099e0b9e
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/01/2019
ms.locfileid: "57200906"
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a>作法：明確實作兩個介面的成員 (C# 程式設計指南)
明確的[介面](../../../csharp/language-reference/keywords/interface.md)實作也可讓程式設計人員實作具有相同成員名稱的兩個介面，並提供每個介面成員不同的實作。 此範例會顯示方塊尺寸的計量和英制單位。 Box [類別](../../../csharp/language-reference/keywords/class.md)實作 IEnglishDimensions 和 IMetricDimensions 兩個介面，代表不同的量值系統。 這兩個介面具有相同的成員名稱，Length 和 Width。  
  
## <a name="example"></a>範例  
 [!code-csharp[csProgGuideInheritance#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#9)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 如果您想要以英制單位建立預設的量值單位，請按一般方式實作 Length 和 Width 方法，並從 IMetricDimensions 介面明確實作 Length 和 Width 方法：  
  
 [!code-csharp[csProgGuideInheritance#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#10)]  
  
 在本例中，您可以從類別執行個體存取英制單位，從介面執行個體存取計量單位：  
  
 [!code-csharp[csProgGuideInheritance#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#11)]  
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md)
- [介面](../../../csharp/programming-guide/interfaces/index.md)
- [如何：明確實作介面成員](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-interface-members.md)
