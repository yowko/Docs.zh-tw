---
title: value 內容關鍵字 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: 34b192d17bd96b6b893c9f14f0d4a77274a32f78
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771748"
---
# <a name="value-c-reference"></a>value (C# 參考)

內容關鍵字 `value` 用於[屬性](../../programming-guide/classes-and-structs/properties.md)和[索引子](../../programming-guide/indexers/index.md)宣告的 `set` 存取子中。 它類似于方法的輸入參數。 這個字 `value` 會參考用戶端程式代碼嘗試指派給屬性或索引子的值。 在下例中，`MyDerivedClass` 具有稱為 `Name` 的屬性，它使用 `value` 參數將新的字串指派給支援欄位 `name`。 就用戶端程式碼的觀點而言，是以簡單指派寫入作業。

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

如需詳細資訊，請參閱[Properties](../../programming-guide/classes-and-structs/properties.md)和[Indexeres](../../programming-guide/indexers/index.md)文章。

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 關鍵字](index.md)
