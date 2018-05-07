---
title: 關鍵字參考 (F#)
description: '尋找所有的 F # 語言關鍵字的相關資訊的連結。'
ms.date: 05/16/2016
ms.openlocfilehash: 2cb2fbb3236fcfeebc801b467d657f031b8da55a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="keyword-reference"></a>關鍵字參考

本主題包含所有的 F # 語言關鍵字的相關資訊的連結。

## <a name="f-keyword-table"></a>F # 關鍵字資料表

下表會顯示所有 F # 關鍵字，依字母順序，以及簡短描述和包含的詳細資訊的相關主題連結。

|關鍵字|連結|描述|
|-------|----|-----------|
|`abstract`|[成員](members/index.md)<br /><br />[抽象類別](abstract-classes.md)|表示可以在其中宣告或類型，是虛擬的其預設實作中不具任何實作的方法。|
|`and`|[`let` 繫結](functions/let-bindings.md)<br /><br />[成員](members/index.md)<br /><br />[條件約束](generics/constraints.md)|相互遞迴繫結中使用，在屬性宣告，以及使用泛型參數的多個條件約束。|
|`as`|[類別](classes.md)<br /><br />[模式比對](Pattern-Matching.md)|用來提供目前類別物件的物件名稱。 也可用來為指定整個模式比對模式的名稱。|
|`assert`|[判斷提示](assertions.md)|用來驗證程式碼在偵錯期間。|
|`base`|[類別](classes.md)<br /><br />[繼承](inheritance.md)|做為基底類別物件的名稱。|
|`begin`|[詳細語法](verbose-syntax.md)|在詳細語法，表示程式碼區塊的開頭。|
|`class`|[類別](classes.md)|詳細語法，在指出的類別定義開始。|
|`default`|[成員](members/index.md)|表示抽象方法; 的實作若要建立的虛擬方法搭配抽象方法宣告。|
|`delegate`|[委派](delegates.md)|用來宣告委派。|
|`do`|[do 繫結](functions/do-bindings.md)<br /><br />[迴圈：`for...to` 運算式](loops-for-to-expression.md)<br /><br />[迴圈：`for...in` 運算式](loops-for-in-expression.md)<br /><br />[迴圈：`while...do` 運算式](loops-while-do-expression.md)|用於在迴圈建構或執行命令式程式碼。|
|`done`|[詳細語法](verbose-syntax.md)|在詳細語法，表示在迴圈的運算式中的程式碼區塊的結尾。|
|`downcast`|[轉型和轉換](casting-and-conversions.md)|用來將轉換為類型的繼承鏈結中較低。|
|`downto`|[迴圈：`for...to` 運算式](loops-for-to-expression.md)|在`for`反向計算時所用的運算式。|
|`elif`|[條件運算式：`if...then...else`](conditional-expressions-if-then-else.md)|使用條件式分支。 簡短形式`else if`。|
|`else`|[條件運算式：`if...then...else`](conditional-expressions-if-then-else.md)|使用條件式分支。|
|`end`|[結構](structures.md)<br /><br />[差別聯集](discriminated-unions.md)<br /><br />[記錄](records.md)<br /><br />[類型延伸模組](type-extensions.md)<br /><br />[詳細語法](verbose-syntax.md)|在類型擴充功能和類型定義，表示成員定義區段的結尾。<br /><br />在詳細語法中，用來指定開頭的程式碼區塊的結尾`begin`關鍵字。|
|`exception`|[例外狀況處理](exception-handling/index.md)<br /><br />[例外狀況類型](exception-handling/exception-types.md)|用來宣告例外狀況類型。|
|`extern`|[外部函式](functions/external-functions.md)|表示宣告的程式項目另一個二進位檔或組件中定義。|
|`false`|[基本類型](primitive-types.md)|做為布林常值。|
|`finally`|[例外狀況：`try...finally` 運算式](exception-handling/the-try-finally-expression.md)|搭配`try`導入的執行，不論是否發生例外狀況的程式碼區塊。|
|`fixed`|[修正](fixed.md)|用來 「 釘選 」 以防止它被記憶體回收在堆疊上的指標。|
|`for`|[迴圈：`for...to` 運算式](loops-for-to-expression.md)<br /><br />[迴圈：for...in 運算式](loops-for-in-expression.md)|用於迴圈建構。|
|`fun`|[Lambda 運算式：`fun`關鍵字](functions/lambda-expressions-the-fun-keyword.md)|Lambda 運算式，也稱為匿名函式中使用。|
|`function`|[比對運算式](match-expressions.md)<br /><br />[Lambda 運算式： Fun 關鍵字](functions/lambda-expressions-the-fun-keyword.md)|做為較短的替代方案`fun`關鍵字和`match`具有模式比對單一引數的 lambda 運算式中的運算式。|
|`global`|[命名空間](namespaces.md)|用來參考最上層的.NET 命名空間。|
|`if`|[條件運算式：`if...then...else`](conditional-expressions-if-then-else.md)|使用條件式分支建構。|
|`in`|[迴圈：for...in 運算式](loops-for-in-expression.md)<br /><br />[詳細語法](verbose-syntax.md)|用來循序項運算式以及詳細的語法，分隔從繫結運算式。|
|`inherit`|[繼承](inheritance.md)|用來指定基底類別或基底介面。|
|`inline`|[函式](functions/index.md)<br /><br />[內嵌函式](functions/inline-functions.md)|用來指出應整合至呼叫端的程式碼直接函式。|
|`interface`|[介面](interfaces.md)|用來宣告和實作的介面。|
|`internal`|[存取控制](access-control.md)|用來指定成員的可見組件內，但超出它。|
|`lazy`|[延遲運算](lazy-computations.md)|用來指定只在需要結果時，才要執行的計算。|
|`let`|[`let` 繫結](functions/let-bindings.md)|用來建立關聯，或繫結至值或函式的名稱。|
|`let!`|[非同步工作流程](asynchronous-workflows.md)<br /><br />[計算運算式](computation-expressions.md)|用來繫結的名稱，以非同步的計算結果的非同步工作流程中，或在其他計算運算式中，用來繫結的結果，也就是計算類型的名稱。|
|`match`|[比對運算式](match-expressions.md)|用來比較值 」 模式的分支。|
|`member`|[成員](members/index.md)|用來宣告屬性或方法中的物件類型。|
|`module`|[模組](modules.md)|用來與一群相關的類型、 值和函式，以邏輯方式分隔它與其他程式碼產生關聯的名稱。|
|`mutable`|[let 繫結](functions/let-bindings.md)|用來宣告一個變數，也就是值，這個值可以變更。|
|`namespace`|[命名空間](namespaces.md)|用來與相關的類型和模組，以邏輯方式將它與其他程式碼群組產生關聯的名稱。|
|`new`|[建構函式](members/constructors.md)<br /><br />[條件約束](generics/constraints.md)|用來宣告、 定義，或叫用的建構函式會建立，或者，可以建立物件。<br /><br />在泛型參數條件約束也用來表示的類型必須有特定的建構函式。|
|`not`|[符號和運算子參考](symbol-and-operator-reference/index.md)<br /><br />[條件約束](generics/constraints.md)|實際上並不是關鍵字。 不過，`not struct`在組合做為泛型參數條件約束。|
|`null`|[Null 值](values/null-values.md)<br /><br />[條件約束](generics/constraints.md)|表示物件不存在。<br /><br />也用於泛型參數條件約束。|
|`of`|[差別聯集](discriminated-unions.md)<br /><br />[委派](delegates.md)<br /><br />[例外狀況類型](exception-handling/exception-types.md)|在差別聯集表示的值，類別的類型和委派和例外狀況宣告中使用。|
|`open`|[匯入宣告：`open` 關鍵字](import-declarations-the-open-keyword.md)|用來使命名空間或模組的內容可供使用。|
|`or`|[符號和運算子參考](symbol-and-operator-reference/index.md)<br /><br />[條件約束](generics/constraints.md)|使用布林條件為的布林值`or`運算子。 相當於 '||`.<br /><br />也用於成員條件約束。|
|`override`|[成員](members/index.md)|用來實作的基底版本不同的抽象或虛擬方法的版本。|
|`private`|[存取控制](access-control.md)|限制存取成員，才能在相同的類型或模組中的程式碼。|
|`public`|[存取控制](access-control.md)|可讓您存取型別之外的成員。|
|`rec`|[函式](functions/index.md)|用來表示函式是遞迴。|
|`return`|[非同步工作流程](Asynchronous-Workflows.md)<br /><br />[計算運算式](computation-expressions.md)|用來表示值提供做為計算運算式的結果。|
|`return!`|[計算運算式](computation-expressions.md)<br /><br />[非同步工作流程](asynchronous-workflows.md)|用來指出計算運算式，評估時，提供包含的計算運算式的結果。|
|`select`|[查詢運算式](query-expressions.md)|指定哪些欄位或資料行，以擷取在查詢運算式中使用。 請注意，這是內容關鍵字，這表示它不是實際的保留的字，而且只有像是適當的內容中的關鍵字。|
|`static`|[成員](members/index.md)|用來指出方法或屬性，可呼叫沒有類型的執行個體或值的成員類型的所有執行個體之間共用。|
|`struct`|[結構](structures.md)<br /><br />[條件約束](generics/constraints.md)|用來宣告結構類型。<br /><br />也用於泛型參數條件約束。<br /><br />用於 OCaml 模組定義中的相容性。|
|`then`|[條件運算式：`if...then...else`](conditional-expressions-if-then-else.md)<br /><br />[建構函式](members/constructors.md)|條件式運算式中使用。<br /><br />也用來在物件建構後執行的副作用。|
|`to`|[迴圈：`for...to` 運算式](loops-for-to-expression.md)|用於`for`迴圈，以指示的範圍。|
|`true`|[基本類型](primitive-types.md)|做為布林常值。|
|`try`|[例外狀況： Try...with 運算式](exception-handling/the-try-with-expression.md)<br /><br />[： 例外狀況 try...finally 運算式](exception-handling/the-try-finally-expression.md)|用於介紹可能會產生例外狀況的程式碼區塊。 搭配`with`或`finally`。|
|`type`|[F# 類型](fsharp-types.md)<br /><br />[類別](classes.md)<br /><br />[記錄](records.md)<br /><br />[結構](structures.md)<br /><br />[列舉](enumerations.md)<br /><br />[差別聯集](discriminated-unions.md)<br /><br />[類型縮寫](type-abbreviations.md)<br /><br />[測量單位](units-of-measure.md)|用來宣告類別、 記錄、 結構、 差別等位、 列舉類型、 度量單位，或類型縮寫。|
|`upcast`|[轉型和轉換](casting-and-conversions.md)|用來將轉換的繼承鏈結中較高的型別。|
|`use`|[資源管理：`use` 關鍵字](resource-management-the-use-keyword.md)|而不是使用`let`要求的值為`Dispose`呼叫以釋放資源。|
|`use!`|[計算運算式](computation-expressions.md)<br /><br />[非同步工作流程](asynchronous-workflows.md)|而不是使用`let!`非同步工作流程和其他計算值的運算式需要`Dispose`呼叫以釋放資源。|
|`val`|[明確欄位：`val` 關鍵字](members/explicit-fields-the-val-keyword.md)<br /><br />[簽章](signatures.md)<br /><br />[成員](members/index.md)|使用中的簽章，以指出值，或成員，在有限的情況下宣告的型別。|
|`void`|[基本類型](primitive-types.md)|表示.NET`void`型別。 與其他.NET 語言互通時使用。|
|`when`|[條件約束](generics/constraints.md)|用於布林條件 (*時守衛*) 模式比對，並引用泛型型別參數的條件約束子句。|
|`while`|[迴圈：`while...do` 運算式](loops-while-do-expression.md)|引進的迴圈建構。|
|`with`|[比對運算式](match-expressions.md)<br /><br />[物件運算式](object-expressions.md)<br /><br />[複製和更新記錄運算式](copy-and-update-record-expressions.md)<br /><br />[類型延伸模組](type-extensions.md)<br /><br />[例外狀況：`try...with` 運算式](exception-handling/the-try-with-expression.md)|搭配`match`模式比對運算式中的關鍵字。 也在物件運算式中使用，記錄複製運算式，並輸入擴充功能引進成員定義中，並引用例外狀況處理常式。|
|`yield`|[序列](sequences.md)|用在循序項運算式來產生一連串的值。|
|`yield!`|[計算運算式](computation-expressions.md)<br /><br />[非同步工作流程](asynchronous-workflows.md)|用於計算運算式，以將指定的計算運算式的結果附加至包含的計算運算式結果的集合。|

下列語彙基元已保留在 F # 中，因為它們是 OCaml 語言中的關鍵字：

* `asr`
* `land`
* `lor`
* `lsl`
* `lsr`
* `lxor`
* `mod`
* `sig`

如果您使用`--mlcompatibility`作為識別項編譯器選項時，上述的關鍵字是可供使用。

下列語彙基元被保留供未來擴充的 F # 語言的關鍵字：

* `atomic`
* `break`
* `checked`
* `component`
* `const`
* `constraint`
* `constructor`
* `continue`
* `eager`
* `event`
* `external`
* `fixed`
* `functor`
* `include`
* `method`
* `mixin`
* `object`
* `parallel`
* `process`
* `protected`
* `pure`
* `sealed`
* `tailcall`
* `trait`
* `virtual`
* `volatile`

## <a name="see-also"></a>另請參閱
[F# 語言參考](index.md)

[符號和運算子參考](symbol-and-operator-reference/index.md)

[編譯器選項](compiler-options.md)
