---
description: value 內容關鍵字 - C# 參考
title: value 內容關鍵字 - C# 參考
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: ad2eb6f12d8c295dc5203994d6c570cd2377e3ee
ms.sourcegitcommit: 43ed174f085840ca18a791dc89fe833174da766d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/21/2020
ms.locfileid: "90828912"
---
# <a name="value-c-reference"></a>value (C# 參考)

內容關鍵字可 `value` 用於 `set` [屬性](../../programming-guide/classes-and-structs/properties.md) 和 [索引子](../../programming-guide/indexers/index.md) 宣告中的存取子。 它類似于方法的輸入參數。 單字 `value` 參考用戶端程式代碼嘗試指派給屬性或索引子的值。 在下例中，`MyDerivedClass` 具有稱為 `Name` 的屬性，它使用 `value` 參數將新的字串指派給支援欄位 `name`。 就用戶端程式碼的觀點而言，是以簡單指派寫入作業。

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

如需詳細資訊，請參閱 [屬性](../../programming-guide/classes-and-structs/properties.md) 和 [索引子](../../programming-guide/indexers/index.md) 文章。

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

- [C # 參考](../index.md)
- [C # 程式設計指南](../../programming-guide/index.md)
- [C # 關鍵字](index.md)
