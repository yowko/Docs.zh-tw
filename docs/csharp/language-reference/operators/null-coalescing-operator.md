---
title: ?? 運算子 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ??_CSharpKeyword
helpviewer_keywords:
- coalesce operator [C#]
- ?? operator [C#]
- conditional-AND operator (&&) [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: b96fe4790aac7ff5ff5394cbaaeaddc1e334e96c
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333209"
---
# <a name="-operator-c-reference"></a>?? operator (C# 參考)

`??` 運算子稱為 null 聯合運算子。  如果運算元不是 null，則會傳回左方運算元，否則傳回右方運算元。

## <a name="remarks"></a>備註

可為 Null 的類型可以表示來自類型網域的值，或值可以是未定義 (這種情況下，值為 null)。 當左方運算元是可為 Null 的型別且其值為 null 時，您可使用 `??` 運算子的語法表達能力傳回適當的值 (右方運算元)。 如果您嘗試在不使用 `??` 運算子的情況下，將可為 null 的實值類型指派給不可為 null 的實值類型，則會產生編譯時期錯誤。 如果您使用轉型，而可為 null 的實值類型目前為未定義，則會擲回 `InvalidOperationException` 例外狀況。

如需詳細資訊，請參閱[可為 Null 的型別](../../programming-guide/nullable-types/index.md)。

?? 運算子的結果 不視為常數，即使它的兩個引數都是常數。

## <a name="example"></a>範例

[!code-csharp[csRefOperators#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#53)]

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的 [null 聯合運算子](~/_csharplang/spec/expressions.md#the-null-coalescing-operator)。 語言規格是 C# 語法及用法的限定來源。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)
- [可為 Null 的型別](../../programming-guide/nullable-types/index.md)
- [「增益」(Lift) 的真正意義是什麼？](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)