---
title: 繼承
description: 瞭解如何使用"繼承"關鍵字指定 F# 繼承關係。
ms.date: 05/16/2016
ms.openlocfilehash: 5ab891a93528427a66e4eb8f7bfeccbf6e4d2c7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400285"
---
# <a name="inheritance"></a>繼承

繼承用於在物件導向的程式設計中對"is-a"關係或子類型化建模。

## <a name="specifying-inheritance-relationships"></a>指定繼承關係

通過在類聲明中使用 關鍵字`inherit`指定繼承關係。 基本語法形式如下例所示。

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

類最多隻能有一個直接基類。 如果不使用`inherit`關鍵字指定基類，則類隱式繼承從`System.Object`。

## <a name="inherited-members"></a>繼承的成員

如果類從其他類繼承，則派生類的使用者可以使用基類的方法和成員，就像它們是派生類的直接成員一樣。

任何 let 綁定和建構函式參數都是類的私有參數，因此無法從派生類訪問。

關鍵字`base`在派生類中可用，並引用基類實例。 它像自識別碼一樣使用。

## <a name="virtual-methods-and-overrides"></a>虛擬方法和重寫

與其他 .NET 語言相比，虛擬方法（和屬性）在 F# 中的工作方式略有不同。 要聲明新的虛擬成員，請使用 關鍵字`abstract`。 無論是否為該方法提供預設實現，都可以執行此操作。 因此，基類中虛擬方法的完整定義遵循此模式：

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

在派生類中，此虛擬方法的重寫遵循此模式：

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

如果在基類中省略預設實現，則基類將成為抽象類別。

以下代碼示例演示了基類中新虛擬方法`function1`的聲明以及如何在派生類中重寫它。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]

## <a name="constructors-and-inheritance"></a>建構函式和繼承

基類的建構函式必須在派生類中調用。 基類建構函式的參數出現在`inherit`子句中的參數清單中。 使用的值必須根據提供給派生類建構函式的參數確定。

以下代碼顯示基類和派生類，其中派生類調用繼承子句中的基類建構函式：

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

在多個建構函式的情況下，可以使用以下代碼。 派生類建構函式的第一行是`inherit`子句，欄位顯示為使用 關鍵字聲明的`val`顯式欄位。 有關詳細資訊，請參閱[顯式欄位：`val`關鍵字](./members/explicit-fields-the-val-keyword.md)。

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

## <a name="alternatives-to-inheritance"></a>繼承的替代方法

如果需要對類型進行細微修改，請考慮使用物件運算式作為繼承的替代方法。 以下示例說明了使用物件運算式作為創建新派生類型的替代方法：

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

有關物件運算式的詳細資訊，請參閱[物件運算式](object-expressions.md)。

創建物件層次結構時，請考慮使用受歧視的聯合而不是繼承。 受歧視的聯合還可以對共用公共整體類型的不同物件的不同行為建模。 單個受歧視的聯合通常可以消除對一些派生類的需求，這些類彼此的微小變化。 有關受歧視工會的資訊，請參閱[歧視工會](discriminated-unions.md)。

## <a name="see-also"></a>另請參閱

- [物件運算式](object-expressions.md)
- [F# 語言參考](index.md)
