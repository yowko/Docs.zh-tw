---
title: "可多載的運算子 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, operator overloading
- operator overloading [C#]
ms.assetid: 390d9d01-79fc-40ab-9ed3-0bf448da1b6a
caps.latest.revision: 18
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 982c2b03a81e094d791fef1c3178bc637ef4ad8b
ms.openlocfilehash: 2ba47e8462c3a8dc6baa5ef2dc1f11937ebf6d29
ms.contentlocale: zh-tw
ms.lasthandoff: 08/01/2017

---
# <a name="overloadable-operators-c-programming-guide"></a>可多載的運算子 (C# 程式設計手冊)

C# 允許使用者定義的類型使用 [operator](../../../csharp/language-reference/keywords/operator.md) 關鍵字來定義靜態成員函式，以多載運算子。 不過，並非所有運算子都可以多載，其他運算子有限制，如本表所示：

| 運算子 | Overloadability |
| --------- | --------------- |
|[+](../../../csharp/language-reference/operators/addition-operator.md)、[-](../../../csharp/language-reference/operators/subtraction-operator.md)、[!](../../../csharp/language-reference/operators/logical-negation-operator.md)、[~](../../../csharp/language-reference/operators/bitwise-complement-operator.md)、[++](../../../csharp/language-reference/operators/increment-operator.md)、[--](../../../csharp/language-reference/operators/decrement-operator.md), [true](../../../csharp/language-reference/keywords/true.md)、[false](../../../csharp/language-reference/keywords/false.md)|可多載這些一元運算子。|
|[+](../../../csharp/language-reference/operators/addition-operator.md), [-](../../../csharp/language-reference/operators/subtraction-operator.md), [\*](../../../csharp/language-reference/operators/multiplication-operator.md), [/](../../../csharp/language-reference/operators/division-operator.md), [%](../../../csharp/language-reference/operators/modulus-operator.md), [&](../../../csharp/language-reference/operators/and-operator.md), [&#124;](../../../csharp/language-reference/operators/or-operator.md), [^](../../../csharp/language-reference/operators/xor-operator.md), [\<\<](../../../csharp/language-reference/operators/left-shift-operator.md), [>>](../../../csharp/language-reference/operators/right-shift-operator.md)|可多載這些二元運算子。|
|[==](../../../csharp/language-reference/operators/equality-comparison-operator.md), [!=](../../../csharp/language-reference/operators/not-equal-operator.md), [\<](../../../csharp/language-reference/operators/less-than-operator.md), [>](../../../csharp/language-reference/operators/greater-than-operator.md), [\<=](../../../csharp/language-reference/operators/less-than-equal-operator.md), [>=](../../../csharp/language-reference/operators/greater-than-equal-operator.md)|可多載比較運算子 (但請參閱本表後面的注意事項)。|
|[&&](../../../csharp/language-reference/operators/conditional-and-operator.md), [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md)|條件式邏輯運算子無法多載，但它們可以使用可多載的 `&` 和 <code>&#124;</code> 評估。|
|[&#91;&#93;](../../../csharp/language-reference/operators/index-operator.md)|陣列索引運算子無法多載，但您可以定義索引子。|
|[(T)x](../../../csharp/language-reference/operators/invocation-operator.md)|雖然轉換運算子無法多載，但您可以定義新的轉換運算子 (請參閱[明確](../../../csharp/language-reference/keywords/explicit.md)和[隱含](../../../csharp/language-reference/keywords/implicit.md))。|
|[+=](../../../csharp/language-reference/operators/addition-assignment-operator.md), [-=](../../../csharp/language-reference/operators/subtraction-assignment-operator.md), [\*=](../../../csharp/language-reference/operators/multiplication-assignment-operator.md), [/=](../../../csharp/language-reference/operators/division-assignment-operator.md), [%=](../../../csharp/language-reference/operators/modulus-assignment-operator.md), [&=](../../../csharp/language-reference/operators/and-assignment-operator.md), [&#124;=](../../../csharp/language-reference/operators/or-assignment-operator.md), [^=](../../../csharp/language-reference/operators/xor-assignment-operator.md), [\<\<=](../../../csharp/language-reference/operators/left-shift-assignment-operator.md), [>>=](../../../csharp/language-reference/operators/right-shift-assignment-operator.md)|雖然指派運算子無法多載，但比方說，`+=` 是使用 `+` 進行評估 (可多載)。|
|[=](../../../csharp/language-reference/operators/assignment-operator.md)、[.](../../../csharp/language-reference/operators/member-access-operator.md)、[?:](../../../csharp/language-reference/operators/conditional-operator.md)、[??](../../../csharp/language-reference/operators/null-conditional-operator.md)、[->](../../../csharp/language-reference/operators/dereference-operator.md)、[=>](../../../csharp/language-reference/operators/lambda-operator.md), [f(x)](../../../csharp/language-reference/operators/invocation-operator.md)、[as](../../../csharp/language-reference/keywords/as.md)、[checked](../../../csharp/language-reference/keywords/checked.md)、[unchecked](../../../csharp/language-reference/keywords/unchecked.md)、[default](../../../csharp/programming-guide/generics/default-keyword-in-generic-code.md)、[delegate](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)、[is](../../../csharp/language-reference/keywords/is.md)、[new](../../../csharp/language-reference/keywords/new.md)、[sizeof](../../../csharp/language-reference/keywords/sizeof.md)[typeof](../../../csharp/language-reference/keywords/typeof.md)|這些運算子無法多載。|

> [!NOTE]
> 若要多載比較運算子，則必須成對多載；也就是說，如果多載 `==`，也必須多載 `!=`。 反向也是如此，其中多載 `!=` 需要多載 `==`。 比較運算子 `<` 和 `>` 以及 `<=` 和 `>=` 也是如此。

若要在自訂類別上多載運算子，需要在包含正確簽章的類別上建立方法。 方法必須命名為「operator X」，其中 X 是正在多載的運算子的名稱或符號。 一元運算子有一個參數，而二元運算子有兩個參數。 在各案例中，一個參數必須與宣告運算子的類別或結構擁有相同的類型。

```csharp
public static Complex operator +(Complex c1, Complex c2)
{
    return new Complex(c1.real + c2.real, c1.imaginary + c2.imaginary);
}
```

通常會有定義，只會立即傳回運算式的結果。  在這些情況中，有一個使用 `=>` 的語法捷徑。

```csharp
public static Complex operator +(Complex c1, Complex c2) =>
        new Complex(c1.real + c2.real, c1.imaginary + c2.imaginary);
  
// Override ToString() to display a complex number in the traditional format:
public override string ToString() => $"{this.real} + {this.imaginary}";
```

如需詳細資訊，請參閱[如何：使用運算子多載建立複數類別](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-operator-overloading-to-create-a-complex-number-class.md)。

## <a name="see-also"></a>請參閱

[C# 程式設計指南](../../../csharp/programming-guide/index.md)  
[陳述式、運算式和運算子](../../../csharp/programming-guide/statements-expressions-operators/index.md)  
[運算子](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
[C# 運算子](../../../csharp/language-reference/operators/index.md)  
[Why are overloaded operators always static in C#?](http://go.microsoft.com/fwlink/?LinkId=112383) (為什麼多載運算子在 C# 中一律為靜態？)

