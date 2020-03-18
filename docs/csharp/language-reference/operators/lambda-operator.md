---
title: => 運算子 - C# 參考
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: 15c02e11610866f359e3e3a7e2751ded918154b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846245"
---
# <a name="-operator-c-reference"></a>=> 運算子 (C# 參考)

權杖`=>`以兩種形式得到支援：作為[Lambda 運算子](#lambda-operator)，作為成員名稱的分隔符號和[運算式正文定義](#expression-body-definition)中的成員實現。

## <a name="lambda-operator"></a>Lambda 運算子

在[lambda 運算式中](../../programming-guide/statements-expressions-operators/lambda-expressions.md)，lambda`=>`運算子將左側的輸入參數與右側的 lambda 主體分開。

下列範例使用 [LINQ](../../programming-guide/concepts/linq/index.md) 功能並搭配方法語法來示範 Lambda 運算式的使用方式：

[!code-csharp-interactive[infer types of input variables](snippets/LambdaOperator.cs#InferredTypes)]

lambda 運算式的輸入參數在編譯時進行強型別。 當編譯器可以推斷輸入參數的類型時（如前面的示例中所示）可以省略型別宣告。 如果需要指定輸入參數的類型，則必須為每個參數執行此操作，如下例所示：

[!code-csharp-interactive[specify types of input variables](snippets/LambdaOperator.cs#ExplicitTypes)]

下面的示例演示如何定義沒有輸入參數的 lambda 運算式：

[!code-csharp-interactive[without input variables](snippets/LambdaOperator.cs#WithoutInput)]

如需詳細資訊，請參閱 [Lambda 運算式](../../programming-guide/statements-expressions-operators/lambda-expressions.md)。

## <a name="expression-body-definition"></a>運算式主體定義

運算式主體定義的一般語法如下︰

```csharp
member => expression;
```

其中 `expression` 是有效的運算式。 `expression` 的傳回型別必須可以隱含地轉換為成員的傳回型別。 如果成員的返回類型`void`是或成員是建構函式、終端子或屬性`set`訪問器，`expression`則必須是[*語句運算式*](~/_csharplang/spec/statements.md#expression-statements)，可以是任何類型的語句運算式。

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

從 C# 6 開始，支援方法、運算子和唯讀屬性的運算式正文定義。 支援建構函式、終端子、屬性和索引子訪問器的運算式正文定義，從 C# 7.0 開始。

如需詳細資訊，請參閱[運算式主體成員](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)。

## <a name="operator-overloadability"></a>運算子是否可多載

無法多載 `=>` 運算子。

## <a name="c-language-specification"></a>C# 語言規格

有關 Lambda 運算子的詳細資訊，請參閱[C# 語言規範](~/_csharplang/spec/introduction.md)中的[匿名函數運算式](~/_csharplang/spec/expressions.md#anonymous-function-expressions)部分。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 運算子](index.md)
