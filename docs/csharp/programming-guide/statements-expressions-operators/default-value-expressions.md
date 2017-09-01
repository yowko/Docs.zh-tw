---
title: "預設值運算式 (C# 程式設計指南)"
description: "預設值運算式會為任何參考型別或實值型別產生預設值"
ms.date: 2017-08-23
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], default keyword
- default keyword [C#], generic programming
ms.assetid: b9daf449-4e64-496e-8592-6ed2c8875a98
caps.latest.revision: 22
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 1e548df4de2c07934313311a7ffcfae82be76000
ms.openlocfilehash: 7b5b53d7ed92c6f6377a3e494daf1d02a4cf0934
ms.contentlocale: zh-tw
ms.lasthandoff: 08/29/2017

---
# <a name="default-value-expressions-c-programming-guide"></a>預設值運算式 (C# 程式設計指南)

預設值運算式會為型別產生預設值。 預設值運算式對泛型類別和方法特別有用。 使用泛型時會發生一個問題，也就是當您無法預先知道下列資訊時，如何將預設值指派給參數化型別 `T`：

- `T` 是參考型別或實值型別。
- 如果 `T` 是實值型別，則會是數值或使用者定義結構。

 假設有參數化型別 `T` 的變數 `t`，陳述式 `t = null` 就只在 `T` 為參考型別時有效。 指派 `t = 0` 僅適用於數值型別，而不適用於結構。 解決方案是使用預設值運算式，若為參考型別 (類別類型及介面類型)，其傳回 `null`；若為數值型別，其傳回零。 若是使用者定義結構，其傳回已初始化為零位元模式的結構，而依據成員為數值或參考型別，來為各成員產生 0 或 `null`。 若是可為 Null 的實值型別，`default` 會傳回 <xref:System.Nullable%601?displayProperty=fullName>，該值會與任何結構一樣經過初始化。

`default(T)` 運算式不限於泛型類別及方法。 預設值運算式可搭配任何 managed 型別使用。 以下任一運算式均有效：

 [!code-cs[csProgGuideGenerics#1](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-value-expressions.cs)]

 下列 `GenericList<T>` 類別的範例示範如何在泛型類別中使用 `default(T)` 運算子。 如需詳細資訊，請參閱[泛型概觀](../generics/introduction-to-generics.md)。

 [!code-cs[csProgGuideGenerics#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#Snippet41)]

## <a name="default-literal-and-type-inference"></a>預設常值和型別推斷

從 C# 7.1 開始，可以在編譯器能推斷運算式型別時，將 `default` 用於預設值運算式。 `default` 常值會產生與對等 `default(T)` 相同的值，其中 `T` 是推斷出來的型別。 這樣能夠減少宣告型別一次以上所產生的冗餘，讓程式碼更精簡。 `default` 常值可以用在下列任一位置：

- 變數初始設定式
- 變數設定
- 宣告選用參數的預設值
- 提供方法呼叫引數的值
- 傳回陳述式 (或運算式主體成員中的運算式)

下列範例示範 `default` 常值在預設值運算式中的多種使用方式：

[!code-cs[csProgGuideGenerics#3](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-literal.cs)]

## <a name="see-also"></a>請參閱

 <xref:System.Collections.Generic> [C# 程式設計指南](../index.md)   
 [泛型](../generics/index.md)   
 [泛型方法](../generics/generic-methods.md)   
 [泛型](~/docs/standard/generics/index.md)   

