---
title: "繼承 (F#)"
description: "了解如何指定 F # 繼承關聯性使用 'inherit' 關鍵字。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: b38ab2f6-7ba7-4839-8eff-e6bd6cfd2b2f
ms.openlocfilehash: 331c8f4e39aacd9d5e55bfbaf584f037e58d36a1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="inheritance"></a>繼承

繼承用來建立模型的 「 是-a"關聯性，或子物件導向程式設計中。


## <a name="specifying-inheritance-relationships"></a>指定繼承關聯性
使用指定的繼承關聯性`inherit`類別宣告中的關鍵字。 基本語法形式是由下列範例所示。

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

類別可以有最多一個直接基底類別。 如果您未指定基底類別使用`inherit`關鍵字，在類別隱含繼承自`System.Object`。


## <a name="inherited-members"></a>繼承的成員
如果類別繼承自另一個類別，方法和基底類別成員可用來在衍生類別的使用者，就像是在衍生類別的直接成員一樣。

任何 let 繫結和建構函式參數都是私用至類別，因此，無法從衍生類別存取。

關鍵字`base`隨附在衍生類別中，參考的基底類別的執行個體。 它當成自我識別項。


## <a name="virtual-methods-and-overrides"></a>虛擬方法，並覆寫
虛擬方法 （和屬性） 運作方式稍有不同 F # 中相較於其他.NET 語言。 若要宣告新的虛擬成員，您使用`abstract`關鍵字。 要這麼做，不論您是否提供該方法的預設實作。 因此在基底類別虛擬方法的完整定義會遵循下列模式：

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

並在衍生類別中覆寫此虛擬方法遵循下列模式：

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

如果您省略基底類別中的預設實作，基底類別變成抽象類別。

下列程式碼範例將說明新的虛擬方法的宣告`function1`基底類別，以及如何在衍生類別中覆寫它。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]
    
## <a name="constructors-and-inheritance"></a>建構函式和繼承
在衍生類別中，必須先呼叫基底類別的建構函式。 基底類別建構函式的引數出現在引數清單中`inherit`子句。 可用的值必須由衍生的類別建構函式提供的引數。

下列程式碼將示範基底類別和衍生的類別，其中衍生的類別繼承子句中呼叫基底類別建構函式：

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

在多個建構函式的情況下可以使用下列程式碼。 在衍生的類別建構函式的第一行是`inherit`子句和欄位會顯示為以宣告的明確欄位`val`關鍵字。 如需詳細資訊，請參閱[明確欄位：`val`關鍵字](members/explicit-fields-the-val-keyword.md)。

```fsharp
type BaseClass =
    val string1 : string
    new (str) = { string1 = str }
    new () = { string1 = "" }

type DerivedClass =
    inherit BaseClass

    val string2 : string
    new (str1, str2) = { inherit BaseClass(str1); string2 = str2 }
    new (str2) = { inherit BaseClass(); string2 = str2 }

let obj1 = DerivedClass("A", "B")
let obj2 = DerivedClass("A")
```

## <a name="alternatives-to-inheritance"></a>繼承的替代方案
在需要稍微修改的類型的地方的情況下，請考慮使用物件運算式作為繼承的替代方案。 下列範例將說明建立新的衍生的類型的替代方式為物件運算式使用：

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

如需物件運算式的詳細資訊，請參閱[物件運算式](object-expressions.md)。

當您建立的物件階層架構時，請考慮使用差別聯集而非繼承。 差別等位也可以各不相同的模型行為的不同共用通用的整體類型的物件。 單一的差別聯集通常不需要的數目彼此次要變化的衍生類別。 差別等位的相關資訊，請參閱[差別等位](discriminated-unions.md)。


## <a name="see-also"></a>另請參閱
[物件運算式](object-expressions.md)

[F# 語言參考](index.md)
