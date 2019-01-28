---
title: HOW TO：使用物件初始設定式初始化物件 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 12/20/2018
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: 2ac4242eb1bd24fd54cc1eca97acb96f39cc050b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607026"
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a>HOW TO：使用物件初始設定式初始化物件 (C# 程式設計手冊)

您可以使用物件初始設定式以宣告方式初始化類型物件，而不需要明確叫用該類型的建構函式。  
  
下列範例示範如何搭配具名物件使用物件初始設定式。 編譯器會先存取預設執行個體建構函式，再處理成員初始化，來處理物件初始設定式。 因此，如果預設建構函式在類別中宣告為 `private`，需要公用存取的物件初始設定式將會失敗。
  
如果您要定義匿名型別，則必須使用物件初始設定式。 如需詳細資訊，請參閱[＜How to：在查詢中傳回項目屬性的子集](how-to-return-subsets-of-element-properties-in-a-query.md)。  
  
## <a name="example"></a>範例  

下列範例示範如何使用物件初始設定式，來初始化新的 `StudentName` 類型。 此範例會設定 `StudentName` 類型中的屬性：
  
[!code-csharp-interactive[InitializerObjectExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToObjectInitializers.cs#HowToObjectInitializers)]  

物件初始設定式可用來設定物件中的索引子。 下列範例定義 `BaseballTeam` 類別，該類別使用索引子來取得及設定不同位置的球員。 初始設定式可以根據位置縮寫，或用於每個位置棒球計分卡的數字，來指派球員：

[!code-csharp-interactive[InitializerIndexerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToIndexInitializer.cs#HowToIndexInitializer)]  

## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../index.md)
- [物件和集合初始設定式](object-and-collection-initializers.md)
