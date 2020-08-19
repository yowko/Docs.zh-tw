---
title: 關鍵字參考
description: '尋找所有 F # 語言關鍵字的相關資訊連結。'
f1_keywords:
- new_FS
- use_FS
- end_FS
- lsl_FS
- exception_FS
- asr_FS
- if_FS
- internal_FS
- default_FS
- in_FS
- lsr_FS
- open_FS
- static_FS
- assert_FS
- match_FS
- land_FS
- with_FS
- inherit_FS
- mutable_FS
- downto_FS
- false_FS
- sig_FS
- and_FS
- true_FS
- namespace_FS
- public_FS
- lxor_FS
- val_FS
- void_FS
- downcast_FS
- function_FS
- while_FS
- for_FS
- class_FS
- done_FS
- to_FS
- module_FS
- let_FS
- delegate_FS
- abstract_FS
- then_FS
- when_FS
- lazy_FS
- try_FS
- inline_FS
- do_FS
- upcast_FS
- begin_FS
- base_FS
- fun_FS
- struct_FS
- as_FS
- extern_FS
- null_FS
- lor_FS
- return_FS
- mod_FS
- private_FS
- of_FS
- or_FS
- member_FS
- type_FS
- rec_FS
- elif_FS
- override_FS
- interface_FS
- yield_FS
- else_FS
- finally_FS
- global_FS
- select_FS
- use!_FS
- const_FS
dev_langs:
- FSharp
ms.date: 08/15/2020
ms.openlocfilehash: 15505c123dd0d6497fbc80c8fc9f0910018911ea
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558097"
---
# <a name="keyword-reference"></a>關鍵字參考

本主題包含所有 F # 語言關鍵字的相關資訊連結。

## <a name="f-keyword-table"></a>F # 關鍵字表

下表依字母順序顯示所有 F # 關鍵字，以及包含詳細資訊的簡短描述和相關主題的連結。

|關鍵字|連結|描述|
|-------|----|-----------|
|`abstract`|[成員](./members/index.md)<br /><br />[抽象類別](abstract-classes.md)|表示方法，該方法在宣告或為虛擬的類型中沒有任何實值，而且具有預設實值。|
|`and`|[`let` 綁定](./functions/let-bindings.md)<br /><br />[記錄](records.md)<br /><br />[成員](./members/index.md)<br /><br />[約束](./generics/constraints.md)|用於相互遞迴系結和記錄、屬性宣告，以及泛型參數的多個條件約束。|
|`as`|[類別](classes.md)<br /><br />[模式比對](Pattern-Matching.md)|用來為目前的類別物件提供物件名稱。 也可用來為模式比對中的整個模式提供名稱。|
|`assert`|[判斷提示](assertions.md)|用於在偵錯工具期間驗證程式代碼。|
|`base`|[類別](classes.md)<br /><br />[繼承](inheritance.md)|用作基類物件的名稱。|
|`begin`|[詳細語法](verbose-syntax.md)|在詳細資訊語法中，表示程式碼區塊的開頭。|
|`class`|[類別](classes.md)|在詳細資訊語法中，指出類別定義的開頭。|
|`default`|[成員](./members/index.md)|表示抽象方法的執行。與抽象方法宣告一起使用，以建立虛擬方法。|
|`delegate`|[委派](delegates.md)|用來宣告委派。|
|`do`|[do 繫結](./functions/do-bindings.md)<br /><br />[迴圈：`for...to` 運算式](loops-for-to-expression.md)<br /><br />[迴圈：`for...in` 運算式](loops-for-in-expression.md)<br /><br />[迴圈：`while...do` 運算式](loops-while-do-expression.md)|用於迴圈結構或執行命令式程式碼。|
|`done`|[詳細語法](verbose-syntax.md)|在詳細資訊語法中，指出迴圈運算式中程式碼區塊的結尾。|
|`downcast`|[轉型和轉換](casting-and-conversions.md)|用來轉換為繼承鏈中較低的類型。|
|`downto`|[迴圈：`for...to` 運算式](loops-for-to-expression.md)|在 `for` 運算式中，用於反向計算時使用。|
|`elif`|[條件運算式： `if...then...else`](conditional-expressions-if-then-else.md)|用於條件式分支。 的簡短形式 `else if` 。|
|`else`|[條件運算式： `if...then...else`](conditional-expressions-if-then-else.md)|用於條件式分支。|
|`end`|[結構](structures.md)<br /><br />[已區分的聯集](discriminated-unions.md)<br /><br />[記錄](records.md)<br /><br />[類型擴充](type-extensions.md)<br /><br />[詳細語法](verbose-syntax.md)|在 [型別定義和類型延伸] 中，指出成員定義區段的結尾。<br /><br />在詳細資訊語法中，用來指定開頭為關鍵字的程式碼區塊結尾 `begin` 。|
|`exception`|[例外狀況處理](./exception-handling/index.md)<br /><br />[例外狀況類型](./exception-handling/exception-types.md)|用來宣告例外狀況類型。|
|`extern`|[外部函式](./functions/external-functions.md)|指出宣告的程式元素是在另一個二進位或元件中定義。|
|`false`|[基本類型](basic-types.md)|當做布林常值使用。|
|`finally`|[例外狀況：`try...finally` 運算式](./exception-handling/the-try-finally-expression.md)|與一起使用 `try` ，以引入無論是否發生例外狀況都會執行的程式碼區塊。|
|`fixed`|[固定](fixed.md)|用來「釘選」堆疊上的指標，以防止它被垃圾收集。|
|`for`|[迴圈：`for...to` 運算式](loops-for-to-expression.md)<br /><br />[迴圈：for...in 運算式](loops-for-in-expression.md)|用於迴圈結構。|
|`fun`|[Lambda 運算式： `fun` 關鍵字](./functions/lambda-expressions-the-fun-keyword.md)|用於 lambda 運算式，也稱為匿名函數。|
|`function`|[比對運算式](match-expressions.md)<br /><br />[Lambda 運算式：有趣的關鍵字](./functions/lambda-expressions-the-fun-keyword.md)|用來作為關鍵字的較短替代， `fun` 以及 `match` 在單一引數上具有模式比對之 lambda 運算式中的運算式。|
|`global`|[命名空間](namespaces.md)|用來參考最上層的 .NET 命名空間。|
|`if`|[條件運算式： `if...then...else`](conditional-expressions-if-then-else.md)|在條件式分支結構中使用。|
|`in`|[迴圈：for...in 運算式](loops-for-in-expression.md)<br /><br />[詳細語法](verbose-syntax.md)|用於順序運算式和（在詳細語法中），以分隔運算式與系結。|
|`inherit`|[繼承](inheritance.md)|用來指定基類或基底介面。|
|`inline`|[函式](./functions/index.md)<br /><br />[內嵌函式](./functions/inline-functions.md)|用來表示應該直接整合至呼叫端程式碼的函式。|
|`interface`|[介面](interfaces.md)|用來宣告和執行介面。|
|`internal`|[存取控制](access-control.md)|用來指定成員可顯示在元件內，但不在其外部。|
|`lazy`|[延遲運算式](lazy-expressions.md)|用來指定只有在需要結果時才會執行的運算式。|
|`let`|[`let` 綁定](./functions/let-bindings.md)|用來將名稱與值或函數系結或系結。|
|`let!`|[非同步工作流程](asynchronous-workflows.md)<br /><br />[計算運算式](computation-expressions.md)|用於非同步工作流程中，以將名稱系結至非同步計算的結果，或在其他計算運算式中用來將名稱系結至計算類型的結果。|
|`match`|[比對運算式](match-expressions.md)|用來將值與模式比較，以進行分支。|
|`match!`|[計算運算式](computation-expressions.md#match)|用來內嵌對計算運算式的呼叫，以及其結果的模式比對。|
|`member`|[成員](./members/index.md)|用來宣告物件型別中的屬性或方法。|
|`module`|[單元](modules.md)|用來將名稱與相關類型、值和函數的群組建立關聯，以邏輯方式將它與其他程式碼分開。|
|`mutable`|[let 繫結](./functions/let-bindings.md)|用來宣告變數，也就是可以變更的值。|
|`namespace`|[命名空間](namespaces.md)|用來將名稱與一組相關類型和模組產生關聯，以邏輯方式將它與其他程式碼分開。|
|`new`|[建構函式](./members/constructors.md)<br /><br />[約束](./generics/constraints.md)|用來宣告、定義或叫用建立或可建立物件的函式。<br /><br />也在泛型參數條件約束中用來指出型別必須有特定的函式。|
|`not`|[符號和運算子參考](./symbol-and-operator-reference/index.md)<br /><br />[約束](./generics/constraints.md)|其實不是關鍵字。 不過， `not struct` 組合會用來做為泛型參數條件約束。|
|`null`|[Null 值](./values/null-values.md)<br /><br />[約束](./generics/constraints.md)|指出物件是否存在。<br /><br />也在泛型參數條件約束中使用。|
|`of`|[已區分的聯集](discriminated-unions.md)<br /><br />[委派](delegates.md)<br /><br />[例外狀況類型](./exception-handling/exception-types.md)|用在區分等位中，表示值的分類類型，以及委派和例外狀況宣告中的型別。|
|`open`|[匯入宣告：`open` 關鍵字](import-declarations-the-open-keyword.md)|用來使命名空間或模組的內容可供使用，而不需限定。|
|`or`|[符號和運算子參考](./symbol-and-operator-reference/index.md)<br /><br />[約束](./generics/constraints.md)|使用布林值條件做為布林值 `or` 運算子。 相當於 `||`。<br /><br />也用於成員條件約束中。|
|`override`|[成員](./members/index.md)|用來執行與基底版本不同之抽象或虛擬方法的版本。|
|`private`|[存取控制](access-control.md)|將成員的存取限制為相同類型或模組中的程式碼。|
|`public`|[存取控制](access-control.md)|允許從類型外部存取成員。|
|`rec`|[函式](./functions/index.md)|用來表示函式是遞迴的。|
|`return`|[非同步工作流程](Asynchronous-Workflows.md)<br /><br />[計算運算式](computation-expressions.md)|用來指出要提供作為計算運算式結果的值。|
|`return!`|[計算運算式](computation-expressions.md)<br /><br />[非同步工作流程](asynchronous-workflows.md)|用來指出計算運算式，在評估時，會提供包含計算運算式的結果。|
|`select`|[查詢運算式](query-expressions.md)|用於查詢運算式中，以指定要解壓縮的欄位或資料行。 請注意，這是內容關鍵字，這表示它實際上不是保留字，而且只適用于適當內容中的關鍵字。|
|`static`|[成員](./members/index.md)|用來表示方法或屬性，該方法或屬性可在沒有類型實例的情況下呼叫，或在類型的所有實例之間共用的值成員。|
|`struct`|[結構](structures.md)<br /><br /> [Tuple](tuples.md)<br/><br/>[約束](./generics/constraints.md)|用來宣告結構類型。<br /><br/>用來指定結構元組。<br/><br />也在泛型參數條件約束中使用。<br /><br />用於模組定義中的 OCaml 相容性。|
|`then`|[條件運算式： `if...then...else`](conditional-expressions-if-then-else.md)<br /><br />[建構函式](./members/constructors.md)|在條件運算式中使用。<br /><br />也用來在物件結構之後執行副作用。|
|`to`|[迴圈：`for...to` 運算式](loops-for-to-expression.md)|在迴圈中用 `for` 來指出範圍。|
|`true`|[基本類型](basic-types.md)|當做布林常值使用。|
|`try`|[例外狀況：try...with 運算式](./exception-handling/the-try-with-expression.md)<br /><br />[例外狀況：try...finally 運算式](./exception-handling/the-try-finally-expression.md)|用來引進可能產生例外狀況的程式碼區塊。 與或一起 `with` 使用 `finally` 。|
|`type`|[F# 類型](fsharp-types.md)<br /><br />[類別](classes.md)<br /><br />[記錄](records.md)<br /><br />[結構](structures.md)<br /><br />[列舉](enumerations.md)<br /><br />[已區分的聯集](discriminated-unions.md)<br /><br />[類型縮寫](type-abbreviations.md)<br /><br />[測量單位](units-of-measure.md)|用來宣告類別、記錄、結構、區分聯集、列舉類型、測量單位或類型縮寫。|
|`upcast`|[轉型和轉換](casting-and-conversions.md)|用來轉換為繼承鏈中較高的類型。|
|`use`|[資源管理：`use` 關鍵字](resource-management-the-use-keyword.md)|用來取代 `let` 需要 `Dispose` 呼叫以釋放資源的值。|
|`use!`|[計算運算式](computation-expressions.md)<br /><br />[非同步工作流程](asynchronous-workflows.md)|`let!`針對需要呼叫以釋出資源的值使用，而不是在非同步工作流程和其他計算運算式中使用 `Dispose` 。|
|`val`|[明確欄位： `val` 關鍵字](./members/explicit-fields-the-val-keyword.md)<br /><br />[簽章](signature-files.md)<br /><br />[成員](./members/index.md)|在有限的情況下，在簽章中用來表示值，或用於宣告成員的類型。|
|`void`|[基本類型](basic-types.md)|指出 .NET `void` 型別。 與其他 .NET 語言交互操作時使用。|
|`when`|[約束](./generics/constraints.md)|用於布林值條件 (*當* 符合模式的) ，以及引入泛型型別參數的條件約束子句時。|
|`while`|[迴圈：`while...do` 運算式](loops-while-do-expression.md)|引進迴圈結構。|
|`with`|[比對運算式](match-expressions.md)<br /><br />[物件運算式](object-expressions.md)<br /><br />[複製和更新記錄運算式](copy-and-update-record-expressions.md)<br /><br />[類型擴充](type-extensions.md)<br /><br />[例外狀況：`try...with` 運算式](./exception-handling/the-try-with-expression.md)|與模式比對 `match` 運算式中的關鍵字一起使用。 也可用於物件運算式、記錄複製運算式和類型延伸模組以引入成員定義，以及引入例外狀況處理常式。|
|`yield`|[清單](lists.md)、 [陣列](arrays.md)、 [序列](sequences.md)|用於清單、陣列或序列運算式中，以產生序列的值。 通常可以省略，因為在大部分情況下都是隱含的。|
|`yield!`|[計算運算式](computation-expressions.md)<br /><br />[非同步工作流程](asynchronous-workflows.md)|用於計算運算式中，以將給定計算運算式的結果附加至包含計算運算式的結果集合。|
|`const`|[型別提供者](../tutorials/type-providers/index.md)| 型別提供者可以使用 `const` 做為關鍵字，將常數常值指定為型別參數引數。|

下列權杖會保留在 F # 中，因為它們是 OCaml 語言中的關鍵字：

- `asr`
- `land`
- `lor`
- `lsl`
- `lsr`
- `lxor`
- `mod`
- `sig`

如果您使用 `--mlcompatibility` 編譯器選項，則可以使用上述關鍵字做為識別碼。

下列權杖會保留為關鍵字，以供未來 F # 語言的擴充之用：

- `atomic`
- `break`
- `checked`
- `component`
- `const`
- `constraint`
- `constructor`
- `continue`
- `eager`
- `event`
- `external`
- `functor`
- `include`
- `method`
- `mixin`
- `object`
- `parallel`
- `process`
- `protected`
- `pure`
- `sealed`
- `tailcall`
- `trait`
- `virtual`
- `volatile`

## <a name="see-also"></a>另請參閱

- [F # 語言參考](index.md)
- [符號和運算子參考](./symbol-and-operator-reference/index.md)
- [編譯器選項](compiler-options.md)
