---
title: value 內容關鍵字 - C# 參考
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: 84d0c51ddafb59144f4ba8c6e73412642fa8fa28
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712893"
---
# <a name="value-c-reference"></a>value (C# 參考)

上下文關鍵字`value`用於`set`[屬性](../../programming-guide/classes-and-structs/properties.md)和[索引子](../../programming-guide/indexers/index.md)聲明中的訪問器。 它類似于方法的輸入參數。 該單詞`value`引用用戶端代碼嘗試分配給屬性或索引子的值。 在下例中，`MyDerivedClass` 具有稱為 `Name` 的屬性，它使用 `value` 參數將新的字串指派給支援欄位 `name`。 就用戶端程式碼的觀點而言，是以簡單指派寫入作業。

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

有關詳細資訊，請參閱[屬性](../../programming-guide/classes-and-structs/properties.md)和[索引子](../../programming-guide/indexers/index.md)文章。

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 關鍵字](index.md)
