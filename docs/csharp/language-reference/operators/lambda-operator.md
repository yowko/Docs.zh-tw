---
title: =&gt; 運算子 - C# 參考
ms.custom: seodec18
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: fa2e149f5b19e80e3171d08519be3ae249d2a112
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540802"
---
# <a name="gt-operator-c-reference"></a>=&gt; 運算子 (C# 參考)

支援兩種形式的 `=>` 語彙基元：作為 Lambda 運算子，以及作為運算式主體定義中成員名稱和成員實作的分隔符號。

## <a name="lambda-operator"></a>Lambda 運算子

在 [Lambda 運算式](../../programming-guide/statements-expressions-operators/lambda-expressions.md)中，Lambda 運算子 `=>` 會分開右邊的 Lambda 主體和左邊的輸入變數。

下列範例使用 [LINQ](../../programming-guide/concepts/linq/index.md) 功能並搭配方法語法來示範 Lambda 運算式的使用方式：

[!code-csharp-interactive[infer types of input variables](~/samples/snippets/csharp/language-reference/operators/LambdaOperatorExamples.cs#InferredTypes)]

Lambda 運算式的輸入變數在編譯時間為強型別。 當編譯器可以推斷輸入變數的類型時 (如上述範例所示)，您可以省略型別宣告。 如果您需要指定輸入變數的類型，您必須針對每個變數執行，如下列範例所示：

[!code-csharp-interactive[specify types of input variables](~/samples/snippets/csharp/language-reference/operators/LambdaOperatorExamples.cs#ExplicitTypes)]

下列範例示範如何定義 Lambda 運算式而不需要輸入變數：

[!code-csharp-interactive[without input variables](~/samples/snippets/csharp/language-reference/operators/LambdaOperatorExamples.cs#WithoutInput)]

如需詳細資訊，請參閱 [Lambda 運算式](../../programming-guide/statements-expressions-operators/lambda-expressions.md)。

## <a name="expression-body-definition"></a>運算式主體定義

運算式主體定義的一般語法如下︰

```csharp
member => expression;
```

其中 *expression* 是有效的運算式。 請注意，只有在成員的傳回型別為 `void` 時，或成員為建構函式、完成項或屬性 `set` 存取子時，*expression* 才可以是「陳述式運算式」。

下列範例顯示 `Person.ToString` 方法的運算式主體定義：

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

它是下列方法定義的簡短版：

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```

從 C# 6 開始支援方法和唯讀屬性的運算式主體定義。 從 C# 7.0 開始支援建構函式、完成項、屬性存取子和索引子的運算式主體定義。

如需詳細資訊，請參閱[運算式主體成員](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)。

## <a name="operator-overloadability"></a>運算子是否可多載

無法多載 `=>` 運算子。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[匿名函式運算式](~/_csharplang/spec/expressions.md#anonymous-function-expressions)一節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)
- [Lambda 運算式](../../programming-guide/statements-expressions-operators/lambda-expressions.md)
- [運算式主體成員](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)