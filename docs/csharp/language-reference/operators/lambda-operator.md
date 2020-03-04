---
title: => 運算子 - C# 參考
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: 5df1ae60ddc298f75d70db7769ec1bf1d21b8ef2
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239283"
---
# <a name="-operator-c-reference"></a>=> 運算子 (C# 參考)

`=>` token 支援兩種形式：做為[Lambda 運算子](#lambda-operator)，以及做為成員名稱的分隔符號，以及[運算式主體定義](#expression-body-definition)中的成員執行。

## <a name="lambda-operator"></a>Lambda 運算子

在[lambda 運算式](../../programming-guide/statements-expressions-operators/lambda-expressions.md)中，Lambda 運算子 `=>` 會將左側的輸入參數與右側的 lambda 主體分開。

下列範例使用 [LINQ](../../programming-guide/concepts/linq/index.md) 功能並搭配方法語法來示範 Lambda 運算式的使用方式：

[!code-csharp-interactive[infer types of input variables](~/samples/snippets/csharp/language-reference/operators/LambdaOperator.cs#InferredTypes)]

Lambda 運算式的輸入參數是在編譯時期的強型別。 當編譯器可以推斷輸入參數的類型（如上述範例所示）時，您可能會省略類型宣告。 如果您需要指定輸入參數的類型，您必須針對每個參數執行此動作，如下列範例所示：

[!code-csharp-interactive[specify types of input variables](~/samples/snippets/csharp/language-reference/operators/LambdaOperator.cs#ExplicitTypes)]

下列範例顯示如何定義不含輸入參數的 lambda 運算式：

[!code-csharp-interactive[without input variables](~/samples/snippets/csharp/language-reference/operators/LambdaOperator.cs#WithoutInput)]

如需詳細資訊，請參閱 [Lambda 運算式](../../programming-guide/statements-expressions-operators/lambda-expressions.md)。

## <a name="expression-body-definition"></a>運算式主體定義

運算式主體定義的一般語法如下︰

```csharp
member => expression;
```

其中 `expression` 是有效的運算式。 `expression` 的傳回型別必須可以隱含地轉換為成員的傳回型別。 如果成員的傳回型別是 `void` 或成員是一個函式、完成項或屬性 `set` 存取子，`expression` 必須是[*語句運算式*](~/_csharplang/spec/statements.md#expression-statements)，它可以是任何型別。

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

從C# 6 開始，支援方法、運算子和唯讀屬性的運算式主體定義。 從C# 7.0 開始支援函式、完成項和屬性和索引子存取子的運算式主體定義。

如需詳細資訊，請參閱[運算式主體成員](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)。

## <a name="operator-overloadability"></a>運算子是否可多載

無法多載 `=>` 運算子。

## <a name="c-language-specification"></a>C# 語言規格

如需 Lambda 運算子的詳細資訊，請參閱[ C#語言規格](~/_csharplang/spec/introduction.md)的[匿名函數運算式](~/_csharplang/spec/expressions.md#anonymous-function-expressions)一節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 運算子](index.md)
