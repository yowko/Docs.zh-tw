---
title: "is (C# 參考) | Microsoft Docs"
keywords: "is 關鍵字 (C#), is (C#)"
ms.date: 2017-02-17
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- is_CSharpKeyword
- is
dev_langs:
- CSharp
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
caps.latest.revision: 20
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c0d300dbb47e64d2425f8af3bc6a819b145786fa
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="is-c-reference"></a>is (C# 參考) #

檢查物件是否與指定的類型相容，或 (從 C# 7 開始) 根據模式來測試運算式。

## <a name="testing-for-type-compatibility"></a>測試類型相容性 ##

`is` 關鍵字會評估執行階段的類型相容性， 並判斷運算式的物件執行個體或結果是否可轉換成指定的類型。 其語法為

```csharp
   expr is type
```

其中 *expr* 是評估為特定類型執行個體的運算式，而 *type* 是 *expr* 的結果要轉換的目標類型名稱。 如果 *expr* 不是 null，而且透過評估運算式所產生的物件可轉換成 *type*，則 `is` 陳述式為 `true`；否則會傳回 `false`。

例如，下列程式碼會判斷 `obj` 是否可轉換成 `Person` 類型的執行個體：

[!code-cs[is#1](../../../../samples/snippets/csharp/language-reference/keywords/is/is1.cs#1)]

如果下列條件為真，則 `is` 陳述式為 true：

- *expr* 是其類型與 *type* 相同的執行個體。

- *expr* 是衍生自 *type* 的類型執行個體。 換句話說，*expr* 的結果可向上轉型成 *type* 的執行個體。

- *expr* 的編譯時期類型為 *type* 的基底類別，而 *expr* 的執行階段類型為 *type* 或衍生自 *type*。 變數的「編譯時期類型」**是定義於變數宣告的變數類型。 變數的「執行階段類型」**是指派給該變數的執行個體類型。

- *expr* 是實作 *type* 介面的類型執行個體。

下列範例顯示在上述每個轉換過程中評估為 `true` 的 `is` 運算式。

[!code-cs[is#3](../../../../samples/snippets/csharp/language-reference/keywords/is/is3.cs#3)]

如果運算式已知一定會是 `true` 或 `false`，`is` 關鍵字會產生編譯時期警告。 它只會考慮參考轉換、boxing 轉換和 unboxing 轉換，不會考慮使用者定義轉換，或是由類型的 [implicit](implicit.md) 和 [explicit](explicit.md) 運算子定義的轉換。 下列範例會產生警告，因為轉換的結果在編譯時期為已知。 請注意，從 `int` 轉換成 `long` 和 `double` 的 `is` 運算式會傳回 false，因為這些轉換是由 [implicit](implicit.md) 運算子處理。

[!code-cs[is#2](../../../../samples/snippets/csharp/language-reference/keywords/is/is2.cs#2)]

`expr` 可以是傳回值的任何運算式，但匿名方法和 Lambda 運算式則除外。 下列範例使用 `is` 來評估方法呼叫的傳回值。   
[!code-cs[is#4](../../../../samples/snippets/csharp/language-reference/keywords/is/is4.cs#4)]

從 C# 7 開始，您可以搭配[類型模式](#type)使用模式比對來撰寫更簡潔的程式碼，以使用 `is` 陳述式。

## <a name="pattern-matching-with-is"></a>以 `is` 進行的模式比對 ##

從 C# 7 開始，`is` 和 [switch](../../../csharp/language-reference/keywords/switch.md) 陳述式支援模式比對。 `is` 關鍵字支援下列模式：

- [類型模式](#type)，測試運算式是否可轉換成指定的類型；如果可以的話，則會將它轉換成該類型的變數。

- [常數模式](#constant)，測試運算式是否評估為指定的常數值。

- [var 模式](#var)，比對一定會成功，而且會將運算式的值繫結至新的區域變數。 

### <a name="type" /> 類型模式 </a>

使用類型模式執行模式比對時，`is` 會測試運算式是否可轉換成指定的類型；如果可以的話，則會將它轉換成該類型的變數。 它是 `is` 陳述式的直接延伸，允許精簡類型的評估和轉換。 `is` 類型模式的一般格式為：

```csharp
   expr is type varname 
```

其中 *expr* 是評估為特定類型執行個體的運算式，*type* 是 *expr* 的結果要轉換的目標類型名稱，而 *varname* 是 *expr* 的結果所轉換的目標物件 (如果 `is` 測試為 `true`)。 

如果下列任一項為真，`is` 運算式為`true`：

- *expr* 是其類型與 *type* 相同的執行個體。

- *expr* 是衍生自 *type* 的類型執行個體。 換句話說，*expr* 的結果可向上轉型成 *type* 的執行個體。

- *expr* 的編譯時期類型為 *type* 的基底類別，而 *expr* 的執行階段類型為 *type* 或衍生自 *type*。 變數的「編譯時期類型」**是定義於變數宣告的變數類型。 變數的「執行階段類型」**是指派給該變數的執行個體類型。

- *expr* 是實作 *type* 介面的類型執行個體。

如果 *exp* 為 `true`，而且 `is` 搭配 `if` 陳述式使用，則 *varname* 會被指派，而且只在 `if` 陳述式內具有區域範圍。

下列範例使用 `is` 類型模式來提供類型之 <xref:System.IComparable.CompareTo(System.Object)?displayProperty=fullName> 方法的實作。

[!code-cs[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

如果沒有模式比對，此程式碼可能會撰寫如下。 使用類型模式比對時，由於不需要測試轉換的結果是否為 `null`，因此會產生更精簡且容易閱讀的程式碼。  

[!code-cs[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

`is` 類型模式也會產生更精簡的程式碼，來判斷實值型別的類型。 下列範例使用 `is` 類型模式來判斷物件為 `Person` 或 `Dog` 執行個體，再顯示適當屬性的值。 

[!code-cs[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

不具有模式比對的對等程式碼需要包含明確轉換的個別指派。

[!code-cs[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="a-nameconstant--constant-pattern"></a><a name="constant" /> 常數模式 ###

以常數模式執行模式比對時，`is` 會測試運算式是否等於指定的常數。 在 C# 6 (含) 以前版本中，[switch](switch.md) 陳述式支援常數模式。 從 C# 7 開始，`is` 陳述式也提供支援。 它的語法為：

```csharp
   expr is constant
```

其中 *expr* 是要評估的運算式，而 *constant* 是要測試的值。 *constant* 可以是下列任何常數運算式： 

- 常值。

- 所宣告之 `const` 變數的名稱。

- 列舉常數。

常數運算式評估如下：

- 如果 *expr* 和 *constant* 是整數型別，C# 等號比較運算子會判斷運算式是否傳回`true` (亦即是否 `expr == constant`)。

- 否則，會呼叫靜態 [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) 方法來判斷運算式的值。  

下列範例結合類型和常數模式來測試物件是否為 `Dice` 執行個體；如果是，則判斷擲出的骰子值是否為 6。

[!code-cs[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]
 
### <a name="var" /> var 模式 </a>

以 var 模式進行模式比對一定會成功。 其語法為

```csharp 
   expr is var varname
```

其中 *expr* 的值一定會指派給名為 *varname* 的區域變數。 *varname* 是其類型與 *expr* 相同的靜態變數。 下列範例使用 var 模式將運算式指派給名為 `obj` 的變數， 然後顯示 `obj` 的值和類型。

[!code-cs[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

請注意，如果 *expr* 為 `null`，`is` 運算式仍為 true，而且會將 `null` 指派給 *varname*。 

# <a name="c-language-specification"></a>C# 語言規格
  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [typeof](../../../csharp/language-reference/keywords/typeof.md)   
 [as](../../../csharp/language-reference/keywords/as.md)   
 [運算子關鍵字](../../../csharp/language-reference/keywords/operator-keywords.md)

