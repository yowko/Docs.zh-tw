---
title: 泛型和屬性 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
ms.openlocfilehash: 99a24a7069145dfad5ce6c9c91f2a8653eb9a224
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589635"
---
# <a name="generics-and-attributes-c-programming-guide"></a>泛型和屬性 (C# 程式設計手冊)
屬性可以使用與非泛型型別相同的方式，套用至泛型型別。 如需套用屬性的詳細資訊，請參閱[屬性](../concepts/attributes/index.md)。  
  
 自訂屬性只能參考開放式泛型型別 (未獲得任何型別引數的泛型型別) 和封閉式建構泛型型別 (為所有型別參數提供引數)。  
  
 下列範例使用這個自訂屬性：  
  
 [!code-csharp[csProgGuideGenerics#48](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#48)]  
  
 屬性可以參考開放式泛型型別：  
  
 [!code-csharp[csProgGuideGenerics#49](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#49)]  
  
 指定多個使用適當逗點數目的型別參數。 在此範例中，`GenericClass2` 有兩個型別參數：  
  
 [!code-csharp[csProgGuideGenerics#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#50)]  
  
 屬性可以參考封閉式建構泛型型別：  
  
 [!code-csharp[csProgGuideGenerics#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#51)]  
  
 參考泛型型別參數的屬性會造成編譯時期錯誤：  
  
 [!code-csharp[csProgGuideGenerics#52](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#52)]  
  
 泛型型別無法繼承自 <xref:System.Attribute>：  
  
 [!code-csharp[csProgGuideGenerics#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#53)]  
  
 若要取得執行階段的泛型型別或型別參數的相關資訊，您可以使用 <xref:System.Reflection> 的方法。 如需詳細資訊，請參閱[泛型和反映](./generics-and-reflection.md)。  
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../index.md)
- [泛型](./index.md)
- [屬性](../../../standard/attributes/index.md)
