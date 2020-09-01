---
description: => 運算子 - C# 參考
title: => 運算子 - C# 參考
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: 6a4df3a4bd358b87f98ff1bd5a3f624b1029a73b
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128357"
---
# <a name="-operator-c-reference"></a>=> 運算子 (C# 參考)

`=>`標記的支援方式有兩種：做為[Lambda 運算子](#lambda-operator)，以及做為成員名稱和[運算式主體定義](#expression-body-definition)中成員實作為分隔符號的形式。

## <a name="lambda-operator"></a>Lambda 運算子

在 [lambda 運算式](lambda-expressions.md)中，Lambda 運算子會將 `=>` 左側的輸入參數與右邊的 lambda 主體分隔開來。

下列範例使用 [LINQ](../../programming-guide/concepts/linq/index.md) 功能並搭配方法語法來示範 Lambda 運算式的使用方式：

[!code-csharp-interactive[infer types of input variables](snippets/shared/LambdaOperator.cs#InferredTypes)]

Lambda 運算式的輸入參數在編譯時期是強型別。 當編譯器可以推斷輸入參數的類型時（如上述範例所示），您可能會省略類型宣告。 如果您需要指定輸入參數的類型，您必須針對每個參數執行此動作，如下列範例所示：

[!code-csharp-interactive[specify types of input variables](snippets/shared/LambdaOperator.cs#ExplicitTypes)]

下列範例顯示如何定義沒有輸入參數的 lambda 運算式：

[!code-csharp-interactive[without input variables](snippets/shared/LambdaOperator.cs#WithoutInput)]

如需詳細資訊，請參閱 [Lambda 運算式](lambda-expressions.md)。

## <a name="expression-body-definition"></a>運算式主體定義

運算式主體定義的一般語法如下︰

```csharp
member => expression;
```

其中 `expression` 是有效的運算式。 `expression` 的傳回型別必須可以隱含地轉換為成員的傳回型別。 如果成員的傳回型別是 `void` ，或是如果成員是一個函式、完成項或屬性或索引子 `set` 存取子，則 `expression` 必須是 [*語句運算式*](~/_csharplang/spec/statements.md#expression-statements)。 因為會捨棄運算式的結果，所以該運算式的傳回型別可以是任何型別。

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

從 c # 6 開始支援方法、運算子和唯讀屬性的運算式主體定義。 從 c # 7.0 開始支援函式、完成項和屬性和索引子存取子的運算式主體定義。

如需詳細資訊，請參閱[運算式主體成員](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)。

## <a name="operator-overloadability"></a>運算子是否可多載

無法多載 `=>` 運算子。

## <a name="c-language-specification"></a>C# 語言規格

如需 Lambda 運算子的詳細資訊，請參閱[c # 語言規格](~/_csharplang/spec/introduction.md)的「[匿名函數運算式](~/_csharplang/spec/expressions.md#anonymous-function-expressions)」一節。

## <a name="see-also"></a>另請參閱

- [C# 參考資料](../index.md)
- [C# 運算子與運算式](index.md)
