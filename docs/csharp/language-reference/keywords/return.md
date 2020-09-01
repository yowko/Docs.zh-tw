---
description: return 陳述式 - C# 參考
title: return 陳述式 - C# 參考
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: 486db846304c0972942ff58f3d5b276083681abe
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89136993"
---
# <a name="return-c-reference"></a>return (C# 參考)

`return` 陳述式會終止執行在其中出現的方法，並且將控制權傳回給呼叫方法。 它也可以傳回選擇性值。 如果方法是 `void` 類型，則可以省略 `return` 陳述式。

 如果 return 陳述式位在 `try` 區塊內，則會先執行 `finally` 區塊 (如果存在的話)，控制權才會傳回到呼叫方法。

## <a name="example"></a>範例

 在下列範例中，`CalculateArea()` 方法會將區域變數 `area` 傳回為 `double` 值。

[!code-csharp[csrefKeywordsJump#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#6)]  

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

- [C # 參考](../index.md)
- [C # 程式設計指南](../../programming-guide/index.md)
- [C # 關鍵字](index.md)
- [return 語句](/cpp/cpp/return-statement-cpp)
