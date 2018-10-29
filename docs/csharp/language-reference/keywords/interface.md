---
title: interface (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 4adc7ba106e0044ba6aff94ea3180d9c8e3ded7b
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/08/2018
ms.locfileid: "48872939"
---
# <a name="interface-c-reference"></a>interface (C# 參考)

介面只會包含[方法](../../programming-guide/classes-and-structs/methods.md)、[屬性](../../programming-guide/classes-and-structs/properties.md)、[事件](../../programming-guide/events/index.md)或[索引子](../../programming-guide/indexers/index.md)的簽章。 實作介面的類別或結構必須實作在介面定義中指定的介面成員。 在下列範例中，類別 `ImplementationClass` 必須實作名為 `SampleMethod` 的方法，該方法沒有參數並會傳回 `void`。

如需詳細資訊與範例，請參閱[介面](../../programming-guide/interfaces/index.md)。

## <a name="example"></a>範例

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

介面可以是命名空間或類別的成員，而且可以包含下列成員的簽章：

- [方法](../../programming-guide/classes-and-structs/methods.md)

- [屬性](../../programming-guide/classes-and-structs/using-properties.md)

- [索引子](../../programming-guide/indexers/using-indexers.md)

- [事件](event.md)

介面可以繼承一或多個基底介面。

當基底類型清單包含基底類別和介面時，基底類別一定會排在清單的第一個。

實作介面的類別能夠明確實作該介面的成員。 明確實作的成員不能經由類別執行個體存取，只能經由介面的執行個體來存取。

如需明確介面實作的詳細資訊和程式碼範例，請參閱[明確介面實作](../../programming-guide/interfaces/explicit-interface-implementation.md)。

## <a name="example"></a>範例

下列範例示範介面實作。 在此範例中，介面包含屬性宣告，而類別包含實作。 實作 `IPoint` 的任何類別執行個體都有整數屬性 `x` 和 `y`。

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

- [C# 參考](../../../csharp/language-reference/index.md)  
- [C# 程式設計指南](../../programming-guide/index.md)  
- [C# 關鍵字](index.md)  
- [參考型別](reference-types.md)  
- [介面](../../programming-guide/interfaces/index.md)  
- [使用屬性](../../programming-guide/classes-and-structs/using-properties.md)  
- [使用索引子](../../programming-guide/indexers/using-indexers.md)  
- [class](class.md)  
- [struct](struct.md)  
- [介面](../../programming-guide/interfaces/index.md)
