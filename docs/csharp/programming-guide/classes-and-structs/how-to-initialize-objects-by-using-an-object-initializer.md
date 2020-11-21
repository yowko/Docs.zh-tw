---
title: '如何使用物件初始化運算式初始化物件-c # 程式設計手冊'
description: '瞭解如何在 c # 中使用物件初始化運算式來初始化類型物件，而不需要叫用函式。 使用物件初始化運算式來定義匿名型別。'
ms.date: 12/20/2018
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.topic: how-to
ms.custom: contperfq2
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: 032bbbff3ad356f9718053e8ba54a53559ef1ace
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2020
ms.locfileid: "95098680"
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a>如何使用物件初始化運算式初始化物件 (c # 程式設計手冊) 

您可以使用物件初始設定式以宣告方式初始化類型物件，而不需要明確叫用該類型的建構函式。  
  
下列範例示範如何搭配具名物件使用物件初始設定式。 編譯器會先存取無參數實例的函式，然後處理成員初始化，藉以處理物件初始化運算式。 因此，如果無參數建構函式在類別中宣告為 `private`，需要公用存取的物件初始設定式將會失敗。
  
如果您要定義匿名型別，則必須使用物件初始設定式。 如需詳細資訊，請參閱 [如何在查詢中傳回元素屬性的子集](how-to-return-subsets-of-element-properties-in-a-query.md)。  
  
## <a name="example"></a>範例  

下列範例示範如何使用物件初始設定式，來初始化新的 `StudentName` 類型。 此範例會設定 `StudentName` 類型中的屬性：
  
[!code-csharp[InitializerObjectExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToObjectInitializers.cs#HowToObjectInitializers)]  

物件初始設定式可用來設定物件中的索引子。 下列範例定義 `BaseballTeam` 類別，該類別使用索引子來取得及設定不同位置的球員。 初始設定式可以根據位置縮寫，或用於每個位置棒球計分卡的數字，來指派球員：

[!code-csharp[InitializerIndexerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToIndexInitializer.cs#HowToIndexInitializer)]  

## <a name="see-also"></a>另請參閱

- [C # 程式設計指南](../index.md)
- [物件和集合初始設定式](object-and-collection-initializers.md)
