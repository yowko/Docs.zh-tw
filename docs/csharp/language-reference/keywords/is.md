---
title: is - C# 參考
ms.custom: seodec18
ms.date: 06/21/2019
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: a04105137fad7cd3a25b869c3aa7fcbe91ed20ab
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566303"
---
# <a name="is-c-reference"></a>is (C# 參考)

`is` 運算子會檢查運算式的結果是否與指定的類型相容，或 (從 C# 7.0 開始) 根據模式來測試運算式。 如需型別測試 `is` 運算子的相關資訊，請參閱[型別測試和轉換運算子](../operators/type-testing-and-cast.md)一文的 [is 運算子](../operators/type-testing-and-cast.md#is-operator)小節。

## <a name="pattern-matching-with-is"></a>以 `is` 進行的模式比對

從 C# 7.0 開始，`is` 和 [switch](switch.md) 陳述式支援模式比對。 `is` 關鍵字支援下列模式：

- [類型模式](#type-pattern)，其能測試運算式是否可轉換成指定的類型；如果可以的話，則會將它轉換成該類型的變數。

- [常數模式](#constant-pattern)，測試運算式是否評估為指定的常數值。

- [var 模式](#var-pattern)，比對一定會成功，而且會將運算式的值繫結至新的區域變數。

### <a name="type-pattern"></a>類型模式

使用類型模式執行模式比對時，`is` 會測試運算式是否可轉換成指定的類型；如果可以的話，則會將它轉換成該類型的變數。 它是 `is` 陳述式的直覺性延伸，允許精簡的類型評估和轉換。 `is` 類型模式的一般格式為：

```csharp
   expr is type varname
```

其中 *expr* 是評估為特定類型執行個體的運算式，*type* 是 *expr* 的結果要轉換的目標類型名稱，而 *varname* 是 *expr* 的結果所轉換的目標物件 (如果 `is` 測試為 `true`)。 

如果 *expr* 不是 `null`，且下列任何一個條件成立，則 `is` 運算式為 `true`：

- *expr* 是其類型與 *type* 相同的執行個體。

- *expr* 是衍生自 *type* 的類型執行個體。 換句話說，*expr* 的結果可向上轉型成 *type* 的執行個體。

- *expr* 的編譯時期類型為 *type* 的基底類別，而 *expr* 的執行階段類型為 *type* 或衍生自 *type*。 變數的「編譯時期類型」  是定義於變數宣告的變數類型。 變數的「執行階段類型」  是指派給該變數的執行個體類型。

- *expr* 是實作 *type* 介面的類型執行個體。

從 C# 7.1 開始，*expr* 可以擁有由泛型類型參數及其條件約束所定義的編譯時間類型。

如果 *expr* 為 `true`，且 `is` 搭配 `if` 陳述式使用，則 *varname* 僅在 `if` 陳述式內指派。 *varname* 的範圍從 `is` 運算式到包含 `if` 陳述式的區塊結尾。 在任何其他位置使用 *varname*，會因使用尚未指派的變數而產生編譯時間錯誤。

下列範例使用 `is` 類型模式來提供類型之 <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> 方法的實作。

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

如果沒有模式比對，此程式碼可能會撰寫如下。 使用類型模式比對時，由於不需要測試轉換的結果是否為 `null`，因此會產生更精簡且容易閱讀的程式碼。  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

`is` 類型模式也會產生更精簡的程式碼，來判斷實值型別的類型。 下列範例使用 `is` 類型模式來判斷物件為 `Person` 或 `Dog` 執行個體，再顯示適當屬性的值。

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

不具有模式比對的對等程式碼需要包含明確轉換的個別指派。

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="constant-pattern"></a>常數模式

以常數模式執行模式比對時，`is` 會測試運算式是否等於指定的常數。 在 C# 6 (含) 以前版本中，[switch](switch.md) 陳述式支援常數模式。 從 C# 7.0 開始，它同時也被 `is` 陳述式支援。 它的語法為：

```csharp
   expr is constant
```

其中 *expr* 是要評估的運算式，而 *constant* 是要測試的值。 *constant* 可以是下列任何常數運算式：

- 常值。

- 所宣告之 `const` 變數的名稱。

- 列舉常數。

常數運算式評估如下：

- 如果 *expr* 和 *constant* 是整數型別，則 C# 等號比較運算子會判斷運算式是否傳回 `true` (亦即是否 `expr == constant`)。

- 否則，會呼叫靜態 [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) 方法來判斷運算式的值。  

下列範例結合類型和常數模式來測試物件是否為 `Dice` 執行個體；如果是，則判斷擲出的骰子值是否為 6。

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]

檢查是否可以使用常數模式來執行 `null`。 `is` 陳述式支援 `null` 關鍵字。 它的語法為：

```csharp
   expr is null
```

下列範例示範 `null` 檢查的比較：

[!code-csharp[is#11](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern11.cs#11)]

### <a name="var-pattern"></a>var 模式

`var` 模式是任何類型或值的全能模式。 *expr* 的值一律會被指派至類型與 *expr* 的編譯時間類型相同的區域變數。 `is` 運算式的結果一律是 `true`。 它的語法為：

```csharp
   expr is var varname
```

下列範例使用 var 模式將運算式指派給名為 `obj` 的變數， 然後顯示 `obj` 的值和類型。

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

## <a name="c-language-specification"></a>C# 語言規格
  
如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的 [is 運算子](~/_csharplang/spec/expressions.md#the-is-operator)一節，以及下列 C# 語言提案：

- [模式比對](~/_csharplang/proposals/csharp-7.0/pattern-matching.md)
- [以一般項進行的模式比對](~/_csharplang/proposals/csharp-7.1/generics-pattern-match.md)
  
## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 關鍵字](index.md)
- [型別測試和轉換運算子](../operators/type-testing-and-cast.md)
