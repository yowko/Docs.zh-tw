---
title: 關鍵字參考
description: 查找有關所有 F# 語言關鍵字的資訊的連結。
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
dev_langs:
- FSharp
ms.date: 11/04/2019
ms.openlocfilehash: 34959f471406643e85990c2c80a38a684759a7f9
ms.sourcegitcommit: b16eacb6f94a5b601882a861ad17cc5470a8d5d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80352313"
---
# <a name="keyword-reference"></a>關鍵字參考

本主題包含有關所有 F# 語言關鍵字的資訊的連結。

## <a name="f-keyword-table"></a>F# 關鍵字表

下表按字母順序顯示所有 F# 關鍵字，以及包含詳細資訊的相關主題的簡短說明和連結。

|關鍵字|連結|描述|
|-------|----|-----------|
|`abstract`|[成員](./members/index.md)<br /><br />[抽象類別](abstract-classes.md)|指示在聲明該方法的類型中沒有實現的方法，或者它是虛擬的並且具有預設實現的方法。|
|`and`|[`let`綁定](./functions/let-bindings.md)<br /><br />[記錄](records.md)<br /><br />[成員](./members/index.md)<br /><br />[約束](./generics/constraints.md)|用於相互遞迴綁定和記錄、屬性聲明中以及泛型參數的多個約束。|
|`as`|[類別](classes.md)<br /><br />[模式比對](Pattern-Matching.md)|用於為當前類物件指定物件名稱。 還用於在模式匹配中為整個模式指定名稱。|
|`assert`|[判斷提示](assertions.md)|用於在調試期間驗證代碼。|
|`base`|[類別](classes.md)<br /><br />[繼承](inheritance.md)|用作基類物件的名稱。|
|`begin`|[詳細語法](verbose-syntax.md)|在詳細語法中，指示代碼塊的開始。|
|`class`|[類別](classes.md)|在詳細語法中，指示類定義的開始。|
|`default`|[成員](./members/index.md)|指示抽象方法的實現;與抽象方法聲明一起使用以創建虛擬方法。|
|`delegate`|[委派](delegates.md)|用於聲明委託。|
|`do`|[do 繫結](./functions/do-bindings.md)<br /><br />[迴圈：`for...to` 運算式](loops-for-to-expression.md)<br /><br />[迴圈：`for...in` 運算式](loops-for-in-expression.md)<br /><br />[迴圈：`while...do` 運算式](loops-while-do-expression.md)|用於迴圈構造或執行命令代碼。|
|`done`|[詳細語法](verbose-syntax.md)|在詳細語法中，指示迴圈運算式中代碼塊的結束。|
|`downcast`|[轉型和轉換](casting-and-conversions.md)|用於轉換為繼承鏈中較低的類型。|
|`downto`|[迴圈：`for...to` 運算式](loops-for-to-expression.md)|在運算式`for`中，在反向計數時使用。|
|`elif`|[條件運算式：`if...then...else`](conditional-expressions-if-then-else.md)|用於條件分支。 短形式的`else if`.|
|`else`|[條件運算式：`if...then...else`](conditional-expressions-if-then-else.md)|用於條件分支。|
|`end`|[結構](structures.md)<br /><br />[差別聯集](discriminated-unions.md)<br /><br />[記錄](records.md)<br /><br />[類型延伸模組](type-extensions.md)<br /><br />[詳細語法](verbose-syntax.md)|在類型定義和類型擴展中，指示成員定義部分的末尾。<br /><br />在詳細語法中，用於指定以`begin`關鍵字開頭的代碼塊的末尾。|
|`exception`|[例外狀況處理](./exception-handling/index.md)<br /><br />[異常類型](./exception-handling/exception-types.md)|用於聲明異常類型。|
|`extern`|[外部函式](./functions/external-functions.md)|指示聲明的程式元素在另一個二進位或程式集中定義。|
|`false`|[基本類型](basic-types.md)|用作布林文本。|
|`finally`|[例外狀況：`try...finally` 運算式](./exception-handling/the-try-finally-expression.md)|與一起使用`try`，以引入執行的代碼塊，而不考慮是否發生異常。|
|`fixed`|[固定](fixed.md)|用於在堆疊上"固定"指標，以防止其被垃圾回收。|
|`for`|[迴圈：`for...to` 運算式](loops-for-to-expression.md)<br /><br />[迴圈：for...in 運算式](loops-for-in-expression.md)|用於迴圈構造。|
|`fun`|[蘭姆達運算式：關鍵字`fun`](./functions/lambda-expressions-the-fun-keyword.md)|用於 lambda 運算式，也稱為匿名函數。|
|`function`|[比對運算式](match-expressions.md)<br /><br />[蘭姆達運算式：有趣的關鍵字](./functions/lambda-expressions-the-fun-keyword.md)|用作 lambda 運算式中`fun`關鍵字和`match`運算式的較短替代方法，該運算式在單個參數上具有模式匹配。|
|`global`|[命名空間](namespaces.md)|用於引用頂級 .NET 命名空間。|
|`if`|[條件運算式：`if...then...else`](conditional-expressions-if-then-else.md)|用於條件分支構造。|
|`in`|[迴圈：for...in 運算式](loops-for-in-expression.md)<br /><br />[詳細語法](verbose-syntax.md)|用於序列運算式，在詳細語法中用於將運算式與綁定分開。|
|`inherit`|[繼承](inheritance.md)|用於指定基類或基介面。|
|`inline`|[函式](./functions/index.md)<br /><br />[內聯函數](./functions/inline-functions.md)|用於指示應直接集成到調用方代碼中的函數。|
|`interface`|[介面](interfaces.md)|用於聲明和實現介面。|
|`internal`|[存取控制](access-control.md)|用於指定成員在程式集內可見，但不在程式集外部。|
|`lazy`|[延遲運算式](lazy-expressions.md)|用於指定僅在需要結果時執行的運算式。|
|`let`|[`let`綁定](./functions/let-bindings.md)|用於將名稱關聯或綁定到值或函數。|
|`let!`|[非同步工作流程](asynchronous-workflows.md)<br /><br />[計算運算式](computation-expressions.md)|在非同步工作流中用於將名稱綁定到非同步計算的結果，或者在其他計算運算式中用於將名稱綁定到結果（該結果屬於計算類型）。|
|`match`|[比對運算式](match-expressions.md)|用於通過將值與模式進行比較進行分支。|
|`match!`|[計算運算式](computation-expressions.md#match)|用於將調用對計算運算式和模式匹配在其結果上內聯。|
|`member`|[成員](./members/index.md)|用於聲明物件類型中的屬性或方法。|
|`module`|[模組](modules.md)|用於將名稱與一組相關類型、值和函數相關聯，以便從邏輯上將其與其他代碼分開。|
|`mutable`|[let 繫結](./functions/let-bindings.md)|用於聲明變數，即可以更改的值。|
|`namespace`|[命名空間](namespaces.md)|用於將名稱與一組相關類型和模組相關聯，以便從邏輯上將其與其他代碼分開。|
|`new`|[建構函式](./members/constructors.md)<br /><br />[約束](./generics/constraints.md)|用於聲明、定義或調用創建或可以創建物件的建構函式。<br /><br />也用於泛型參數約束，以指示類型必須具有特定的建構函式。|
|`not`|[符號和運算子參考](./symbol-and-operator-reference/index.md)<br /><br />[約束](./generics/constraints.md)|實際上不是關鍵字。 但是，`not struct`組合用作泛型參數約束。|
|`null`|[空值](./values/null-values.md)<br /><br />[約束](./generics/constraints.md)|指示沒有物件。<br /><br />也用於泛型參數約束。|
|`of`|[差別聯集](discriminated-unions.md)<br /><br />[委派](delegates.md)<br /><br />[異常類型](./exception-handling/exception-types.md)|在區分聯合中用於指示值類別的類型，以及委託和例外聲明。|
|`open`|[匯入宣告：`open` 關鍵字](import-declarations-the-open-keyword.md)|用於使命名空間或模組的內容無限定地可用。|
|`or`|[符號和運算子參考](./symbol-and-operator-reference/index.md)<br /><br />[約束](./generics/constraints.md)|與布林條件一起使用，作為布林運算子`or`。 相當於 `||`。<br /><br />也用於成員約束。|
|`override`|[成員](./members/index.md)|用於實現不同于基本版本的抽象或虛擬方法的版本。|
|`private`|[存取控制](access-control.md)|將成員訪問限制為相同類型或模組的代碼。|
|`public`|[存取控制](access-control.md)|允許從類型外部訪問成員。|
|`rec`|[函式](./functions/index.md)|用於指示函數是遞迴的。|
|`return`|[非同步工作流程](Asynchronous-Workflows.md)<br /><br />[計算運算式](computation-expressions.md)|用於指示作為計算運算式的結果提供的值。|
|`return!`|[計算運算式](computation-expressions.md)<br /><br />[非同步工作流程](asynchronous-workflows.md)|用於指示計算運算式，計算運算式在計算時提供包含計算運算式的結果。|
|`select`|[查詢運算式](query-expressions.md)|用於查詢運算式，用於指定要提取的欄位或列。 請注意，這是一個上下文關鍵字，這意味著它實際上不是保留詞，它的作用類似于在適當的上下文中的關鍵字。|
|`static`|[成員](./members/index.md)|用於指示可以在沒有類型實例的情況下調用的方法或屬性，或類型的所有實例之間共用的值成員。|
|`struct`|[結構](structures.md)<br /><br /> [Tuple](tuples.md)<br/><br/>[約束](./generics/constraints.md)|用於聲明結構類型。<br /><br/>用於指定結構元組。<br/><br />也用於泛型參數約束。<br /><br />用於模組定義中的 OCaml 相容性。|
|`then`|[條件運算式：`if...then...else`](conditional-expressions-if-then-else.md)<br /><br />[建構函式](./members/constructors.md)|在條件運算式中使用。<br /><br />還用於在物件構造後執行副作用。|
|`to`|[迴圈：`for...to` 運算式](loops-for-to-expression.md)|在迴圈`for`中使用以指示範圍。|
|`true`|[基本類型](basic-types.md)|用作布林文本。|
|`try`|[例外狀況：try...with 運算式](./exception-handling/the-try-with-expression.md)<br /><br />[例外狀況：try...finally 運算式](./exception-handling/the-try-finally-expression.md)|用於引入可能生成異常的代碼塊。 與`with`或`finally`一起使用。|
|`type`|[F# 類型](fsharp-types.md)<br /><br />[類別](classes.md)<br /><br />[記錄](records.md)<br /><br />[結構](structures.md)<br /><br />[列舉](enumerations.md)<br /><br />[差別聯集](discriminated-unions.md)<br /><br />[類型縮寫](type-abbreviations.md)<br /><br />[度量單位](units-of-measure.md)|用於聲明類、記錄、結構、區分聯合、枚舉類型、度量單位或類型縮寫。|
|`upcast`|[轉型和轉換](casting-and-conversions.md)|用於轉換為繼承鏈中較高的類型。|
|`use`|[資源管理：`use` 關鍵字](resource-management-the-use-keyword.md)|`let`用於需要調用以釋放資源的值`Dispose`。|
|`use!`|[計算運算式](computation-expressions.md)<br /><br />[非同步工作流程](asynchronous-workflows.md)|在非同步`let!`工作流和其他計算運算式中用於需要`Dispose`調用以釋放資源的值。|
|`val`|[明確欄位：`val` 關鍵字](./members/explicit-fields-the-val-keyword.md)<br /><br />[簽章](signature-files.md)<br /><br />[成員](./members/index.md)|在簽名中用於指示值，或在有限的情況下以型別宣告成員。|
|`void`|[基本類型](basic-types.md)|指示 .NET`void`類型。 與其他 .NET 語言交互操作時使用。|
|`when`|[約束](./generics/constraints.md)|用於模式匹配的布林條件 （*當防護*），並為泛型型別參數引入約束子句。|
|`while`|[迴圈：`while...do` 運算式](loops-while-do-expression.md)|引入迴圈構造。|
|`with`|[比對運算式](match-expressions.md)<br /><br />[物件運算式](object-expressions.md)<br /><br />[複製和更新記錄運算式](copy-and-update-record-expressions.md)<br /><br />[類型延伸模組](type-extensions.md)<br /><br />[例外狀況：`try...with` 運算式](./exception-handling/the-try-with-expression.md)|與模式匹配運算式`match`中的關鍵字一起使用。 還用於物件運算式、記錄複製運算式和類型擴展以引入成員定義和引入例外處理常式。|
|`yield`|[清單](lists.md)、[陣列](arrays.md)、[序列](sequences.md)|在清單、陣列或序列運算式中用於生成序列的值。 通常可以省略，因為它在大多數情況下是隱式的。|
|`yield!`|[計算運算式](computation-expressions.md)<br /><br />[非同步工作流程](asynchronous-workflows.md)|在計算運算式中用於將給定計算運算式的結果追加到包含計算運算式的結果集合中。|

以下權杖在 F# 中保留，因為它們是 OCaml 語言中的關鍵字：

- `asr`
- `land`
- `lor`
- `lsl`
- `lsr`
- `lxor`
- `mod`
- `sig`

如果使用`--mlcompatibility`編譯器選項，則上述關鍵字可用於識別碼。

以下權杖保留為關鍵字，以供將來擴展 F# 語言：

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

- [F# 語言參考](index.md)
- [符號和運算子參考](./symbol-and-operator-reference/index.md)
- [編譯器選項](compiler-options.md)
