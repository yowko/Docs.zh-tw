---
title: '?: 運算子 (C# 參考)'
ms.date: 07/20/2015
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 3e45ff6eaaefa5829c3ed9415abe1a12b7a1d069
ms.sourcegitcommit: 4bca8f7e172fd019ef437a4803bf5895c6bc4781
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2018
ms.locfileid: "50980618"
---
# <a name="-operator-c-reference"></a>?: 運算子 (C# 參考)

條件運算子 (`?:`) 通稱為三元條件運算式，是根據布林運算式的值傳回兩個值的其中一個。 以下是條件運算子的語法。  

```csharp
condition ? first_expression : second_expression;  
```

從 C# 7.2 開始，`first_expression` 及 `second_expression` 可以是 [`ref` 運算式](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-7.2/conditional-ref.md)：

```csharp
ref condition ? ref first_expression : ref second_expression;  
```

結果可能指派給 `ref` 或 `ref readonly` 變數，或是沒有這兩個修飾詞的變數。

## <a name="remarks"></a>備註

`condition` 必須判斷值為 `true` 或 `false`。 如果 `condition` 為 `true`，則會評估 `first_expression` 並產生結果。 如果 `condition` 為 `false`，則會評估 `second_expression` 並產生結果。 只會評估兩個運算式的其中一個。 這對結果為 `ref` 的運算式特別重要，而下列語法有效：

```csharp
ref (storage != null) ? ref storage[3] : ref defaultValue;
```

當 `storage` 為 null 時，就不會求 `storage` 的參考值。

當結果為值時，`first_expression` 及 `second_expression` 的型別必須相同，或必須為來自兩者其中一種型別的隱含轉換。 當結果為 `ref` 時，`first_expression` 及 `second_expression` 的型別必須相同。

你可以使用條件運算子更精確地表示可能需要 `if-else` 建構的計算。 例如，下列程式碼會先使用 `if` 陳述式，再使用條件運算子將整數分類為正數或負數。

```csharp
int input = Convert.ToInt32(Console.ReadLine());  
string classify;  
  
// if-else construction.  
if (input > 0)  
    classify = "positive";  
else  
    classify = "negative";  
  
// ?: conditional operator.  
classify = (input > 0) ? "positive" : "negative";  
```

條件運算子是右向關聯。 運算式 `a ? b : c ? d : e` 會判斷值為 `a ? b : (c ? d : e)`，而不是 `(a ? b : c) ? d : e`。  
  
條件運算子不能多載。
  
## <a name="example"></a>範例

下列範例顯示了結果為值的條件式運算子：

[!code-csharp[csRefOperators?:](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalValue)]

下列另一種方式顯示了結果為參考的條件式運算子：

[!code-csharp[csRefOperatorsRef?:](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalRef)]

## <a name="see-also"></a>請參閱

- [C# 參考](../../../csharp/language-reference/index.md)  
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [C# 運算子](../../../csharp/language-reference/operators/index.md)  
- [if-else](../../../csharp/language-reference/keywords/if-else.md)  
- [?. 和 ?[] 運算子](../../../csharp/language-reference/operators/null-conditional-operators.md)  
- [??運算子](../../../csharp/language-reference/operators/null-coalescing-operator.md)
