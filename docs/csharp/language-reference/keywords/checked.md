---
title: checked 關鍵字 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- checked_CSharpKeyword
- checked
helpviewer_keywords:
- checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
ms.openlocfilehash: e6c28ee0c575bd6010a8aad76fc978062c5fc6a4
ms.sourcegitcommit: ed7b4b9b77d35e94a35a2634e8c874f46603fb2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36948406"
---
# <a name="checked-c-reference"></a>checked (C# 參考)

`checked` 關鍵字是用來明確啟用整數型別算術運算和轉換的溢位檢查。

根據預設，如果運算式產生超出目的地類型範圍的值，則只包含常數值的運算式會導致編譯器錯誤。 如果運算式包含一或多個非常數值，則編譯器偵測不到溢位。 評估下列範例中指派給 `i2` 的運算式不會導致編譯器錯誤。

[!code-csharp[csrefKeywordsChecked#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#3)]

根據預設，不會檢查這些非常數運算式是否在執行階段溢位，而且它們不會引發溢位例外狀況。 先前的範例會顯示 -2,147,483,639 作為兩個正整數的總和。

可以透過編譯器選項、環境設定或使用 `checked` 關鍵字來啟用溢位檢查。 下列範例示範如何使用 `checked` 運算式或 `checked` 區塊，來偵測先前的總和在執行階段所產生的溢位。 這兩個範例都會引發溢位例外狀況。

[!code-csharp[csrefKeywordsChecked#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#4)]

[unchecked](../../../csharp/language-reference/keywords/unchecked.md) 關鍵字可以用來防止溢位檢查。

## <a name="example"></a>範例

這個範例示範如何使用 `checked`，以在執行階段啟用溢位檢查。

[!code-csharp[csrefKeywordsChecked#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#1)]

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

[C# 參考](../../../csharp/language-reference/index.md)  
[C# 程式設計指南](../../../csharp/programming-guide/index.md)  
[C# 關鍵字](../../../csharp/language-reference/keywords/index.md)  
[Checked 與 Unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md)  
[unchecked](../../../csharp/language-reference/keywords/unchecked.md)
