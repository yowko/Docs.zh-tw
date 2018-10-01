---
title: 預設值運算式 (C# 程式設計指南)
description: 預設值運算式會為任何參考型別或實值型別產生預設值
ms.date: 04/25/2018
helpviewer_keywords:
- generics [C#], default keyword
- default keyword [C#], generic programming
ms.openlocfilehash: 94866f22fb3ad921a834cffb16fe17e44cef5965
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2018
ms.locfileid: "47192624"
---
# <a name="default-value-expressions-c-programming-guide"></a>預設值運算式 (C# 程式設計指南)

預設值運算式 `default(T)` 會產生型別 `T` 的預設值。 下表顯示將為各種型別產生哪些值：

|類型|預設值|
|---------|---------|
|任何參考類型|`null`|
|數值型別|零|
|[bool](../../language-reference/keywords/bool.md)|`false`|
|[char](../../language-reference/keywords/char.md)|`'\0'`|
|[enum](../../language-reference/keywords/enum.md)|這個值是由運算式 `(E)0` 所產生，其中 `E` 是列舉識別碼。|
|[struct](../../language-reference/keywords/struct.md)|這個值是藉由將所有實值型別欄位設定為其預設值，並將所有參考型別欄位設定為 `null` 所產生。|
|可為 Null 的型別|<xref:System.Nullable%601.HasValue%2A> 屬性是 `false` 且未定義 <xref:System.Nullable%601.Value%2A> 屬性的執行個體。|

預設值運算式對泛型類別和方法特別有用。 使用泛型時會發生一個問題，也就是當您無法預先知道下列資訊時，如何指派參數化型別 `T` 的預設值：

- `T` 是參考型別或實值型別。
- 如果 `T` 是實值型別，則其是數值還是結構。

 假設有參數化型別 `T` 的變數 `t`，陳述式 `t = null` 就只在 `T` 為參考型別時有效。 指派 `t = 0` 僅適用於數值型別，而不適用於結構。 若要解決該問題，請使用預設值運算式：

```csharp
T t = default(T);
```

`default(T)` 運算式不限於泛型類別及方法。 預設值運算式可搭配任何 managed 型別使用。 以下任一運算式均有效：

 [!code-csharp[csProgGuideGenerics#1](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-value-expressions.cs)]

 下列 `GenericList<T>` 類別的範例示範如何在泛型類別中使用 `default(T)` 運算子。 如需詳細資訊，請參閱[泛型簡介](../generics/introduction-to-generics.md)。

 [!code-csharp[csProgGuideGenerics#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#Snippet41)]

## <a name="default-literal-and-type-inference"></a>預設常值和型別推斷

從 C# 7.1 開始，可以在編譯器能推斷運算式型別時，將 `default` 用於預設值運算式。 `default` 常值會產生與對等 `default(T)` 相同的值，其中 `T` 是推斷出來的型別。 這樣能夠減少宣告型別一次以上所產生的冗餘，讓程式碼更精簡。 `default` 常值可以用在下列任一位置：

- 變數初始設定式
- 變數設定
- 宣告選用參數的預設值
- 提供方法呼叫引數的值
- 傳回陳述式 (或運算式主體成員中的運算式)

下列範例示範 `default` 常值在預設值運算式中的多種使用方式：

[!code-csharp[csProgGuideGenerics#3](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-literal.cs)]

## <a name="see-also"></a>請參閱

- <xref:System.Collections.Generic>  
- [C# 程式設計指南](../index.md)  
- [泛型 (C# 程式設計手冊)](../generics/index.md)  
- [泛型方法](../generics/generic-methods.md)  
- [.NET 的泛型](~/docs/standard/generics/index.md)  
- [預設值表](../../language-reference/keywords/default-values-table.md)
