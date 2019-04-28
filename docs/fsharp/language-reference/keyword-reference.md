---
title: 關鍵字參考
description: 尋找所有的相關資訊的連結F#語言關鍵字。
ms.date: 05/16/2016
ms.openlocfilehash: d55846fe7c8d31454b6bc8684de75546800df7d6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61904094"
---
# <a name="keyword-reference"></a>關鍵字參考

本主題包含所有相關資訊的連結F#語言關鍵字。

## <a name="f-keyword-table"></a>F#關鍵字資料表

下表顯示所有F#依字母順序，以及簡短說明和連結包含的詳細資訊的相關主題的關鍵字。

|關鍵字|連結|描述|
|-------|----|-----------|
|`abstract`|[成員](members/index.md)<br /><br />[抽象類別](abstract-classes.md)|表示的類型中宣告它，或者是虛擬和其預設實作中有沒有實作的方法。|
|`and`|[`let` Bindings](functions/let-bindings.md)<br /><br />[記錄](records.md)<br /><br />[成員](members/index.md)<br /><br />[條件約束](generics/constraints.md)|用於相互遞迴繫結和記錄，在屬性宣告，以及使用泛型參數上的多個條件約束。|
|`as`|[類別](classes.md)<br /><br />[模式比對](Pattern-Matching.md)|用來提供目前類別物件的物件名稱。 也可用來為指定的名稱模式比對整個模式。|
|`assert`|[判斷提示](assertions.md)|用來驗證程式碼在偵錯期間。|
|`base`|[類別](classes.md)<br /><br />[繼承](inheritance.md)|做為基底類別物件的名稱。|
|`begin`|[詳細語法](verbose-syntax.md)|在詳細的語法，表示程式碼區塊的開頭。|
|`class`|[類別](classes.md)|在詳細的語法，表示類別定義的開頭。|
|`default`|[成員](members/index.md)|表示抽象的方法; 的實作若要建立的虛擬方法搭配抽象方法宣告。|
|`delegate`|[委派](delegates.md)|用來宣告委派。|
|`do`|[do 繫結](functions/do-bindings.md)<br /><br />[迴圈：`for...to` 運算式](loops-for-to-expression.md)<br /><br />[迴圈：`for...in` 運算式](loops-for-in-expression.md)<br /><br />[迴圈：`while...do` 運算式](loops-while-do-expression.md)|用在迴圈建構，或執行命令式的程式碼。|
|`done`|[詳細語法](verbose-syntax.md)|在詳細的語法，表示在迴圈的運算式中的程式碼區塊的結尾。|
|`downcast`|[轉型和轉換](casting-and-conversions.md)|用來轉換到繼承鏈結中較低的類型。|
|`downto`|[迴圈：`for...to` 運算式](loops-for-to-expression.md)|在 `for`反向計算時所用的運算式。|
|`elif`|[條件運算式：`if...then...else`](conditional-expressions-if-then-else.md)|使用條件式分支。 簡短形式`else if`。|
|`else`|[條件運算式：`if...then...else`](conditional-expressions-if-then-else.md)|使用條件式分支。|
|`end`|[結構](structures.md)<br /><br />[差別聯集](discriminated-unions.md)<br /><br />[記錄](records.md)<br /><br />[類型延伸模組](type-extensions.md)<br /><br />[詳細語法](verbose-syntax.md)|在類型定義和類型的副檔名，表示成員定義的一個區段的結尾。<br /><br />在 詳細資訊，用來指定語法開頭的程式碼區塊的結尾`begin`關鍵字。|
|`exception`|[例外狀況處理](exception-handling/index.md)<br /><br />[例外狀況類型](exception-handling/exception-types.md)|用來宣告例外狀況類型。|
|`extern`|[外部函式](functions/external-functions.md)|表示宣告的程式項目另一個二進位檔或組件中定義。|
|`false`|[基本類型](primitive-types.md)|做為布林常值。|
|`finally`|[例外狀況：`try...finally`運算式](exception-handling/the-try-finally-expression.md)|可搭配使用`try`導入的執行，不論是否發生例外狀況的程式碼區塊。|
|`fixed`|[已修正](fixed.md)|用來 「 釘選 」 以防止它被記憶體回收在堆疊上的指標。|
|`for`|[迴圈：`for...to` 運算式](loops-for-to-expression.md)<br /><br />[迴圈：for...in 運算式](loops-for-in-expression.md)|用於迴圈建構。|
|`fun`|[Lambda 運算式：`fun` 關鍵字](functions/lambda-expressions-the-fun-keyword.md)|Lambda 運算式，也就是匿名函式中使用。|
|`function`|[比對運算式](match-expressions.md)<br /><br />[Lambda 運算式：Fun 關鍵字](functions/lambda-expressions-the-fun-keyword.md)|做為較短的替代方案`fun`關鍵字和`match`具有模式比對單一引數的 lambda 運算式中的運算式。|
|`global`|[命名空間](namespaces.md)|用來參考最上層的.NET 命名空間。|
|`if`|[條件運算式：`if...then...else`](conditional-expressions-if-then-else.md)|使用條件式分支建構。|
|`in`|[迴圈：for...in 運算式](loops-for-in-expression.md)<br /><br />[詳細語法](verbose-syntax.md)|用來循序項運算式，並在冗長的語法，分隔從繫結的運算式。|
|`inherit`|[繼承](inheritance.md)|用來指定基底類別或基底介面。|
|`inline`|[函式](functions/index.md)<br /><br />[內嵌函式](functions/inline-functions.md)|用來指出應該會直接整合至呼叫端的程式碼的函式。|
|`interface`|[介面](interfaces.md)|用來宣告和實作介面。|
|`internal`|[存取控制](access-control.md)|用來指定成員可見組件內，但超出它。|
|`lazy`|[延遲運算式](lazy-expressions.md)|用來指定只在需要結果時，才要執行的運算式。|
|`let`|[`let` Bindings](functions/let-bindings.md)|用來建立關聯，或繫結至值或函式的名稱。|
|`let!`|[非同步工作流程](asynchronous-workflows.md)<br /><br />[計算運算式](computation-expressions.md)|若要將名稱繫結的非同步計算，結果的非同步工作流程中，或在其他計算運算式中，用來將名稱繫結至結果，也就是計算類型的使用。|
|`match`|[比對運算式](match-expressions.md)|用來分支藉由比較模式的值。|
|`match!`|[計算運算式](computation-expressions.md#match)|用來內嵌呼叫計算運算式和模式比對其結果。|
|`member`|[成員](members/index.md)|用來宣告的屬性或方法中的物件類型。|
|`module`|[模組](modules.md)|用來建立名稱與一群相關的類型、 值和函式，以邏輯方式分隔它與其他程式碼的關聯。|
|`mutable`|[let 繫結](functions/let-bindings.md)|用來宣告變數，也就是值，這個值可以變更。|
|`namespace`|[命名空間](namespaces.md)|用來與相關的類型和模組，以邏輯方式分隔它與其他程式碼群組產生關聯的名稱。|
|`new`|[建構函式](members/constructors.md)<br /><br />[條件約束](generics/constraints.md)|用來宣告、 定義，或叫用的建構函式來建立，或者，可以建立物件。<br /><br />在泛型參數條件約束也用來表示型別必須有特定的建構函式。|
|`not`|[符號和運算子參考](symbol-and-operator-reference/index.md)<br /><br />[條件約束](generics/constraints.md)|實際上並不是關鍵字。 不過，`not struct`組合中用做為泛型參數條件約束。|
|`null`|[Null 值](values/null-values.md)<br /><br />[條件約束](generics/constraints.md)|表示物件不存在。<br /><br />也用於泛型參數條件約束。|
|`of`|[差別聯集](discriminated-unions.md)<br /><br />[委派](delegates.md)<br /><br />[例外狀況類型](exception-handling/exception-types.md)|使用委派和例外狀況的宣告和差別聯集來表示的值，類別的型別中。|
|`open`|[匯入宣告：`open` 關鍵字](import-declarations-the-open-keyword.md)|用來使命名空間或模組的內容可供使用。|
|`or`|[符號和運算子參考](symbol-and-operator-reference/index.md)<br /><br />[條件約束](generics/constraints.md)|使用布林值條件做為布林值`or`運算子。 相當於 `||`。<br /><br />也用於成員條件約束。|
|`override`|[成員](members/index.md)|用來實作的基底的版本不同抽象或虛擬方法的版本。|
|`private`|[存取控制](access-control.md)|限制存取成員，才能在相同的類型或模組中的程式碼。|
|`public`|[存取控制](access-control.md)|允許的成員型別之外存取。|
|`rec`|[函式](functions/index.md)|用來表示函式是遞迴。|
|`return`|[非同步工作流程](Asynchronous-Workflows.md)<br /><br />[計算運算式](computation-expressions.md)|用來表示要提供的計算運算式結果的值。|
|`return!`|[計算運算式](computation-expressions.md)<br /><br />[非同步工作流程](asynchronous-workflows.md)|用來表示計算運算式，評估時，提供包含的計算運算式的結果。|
|`select`|[查詢運算式](query-expressions.md)|用於查詢運算式，以指定哪些欄位或擷取的資料行。 請注意，這是內容關鍵字，這表示它不是實際的保留的字，而且它只會像適當的內容中的關鍵字。|
|`static`|[成員](members/index.md)|用來指出方法或屬性，可以呼叫沒有類型的執行個體或共用類型的所有執行個體之間的值成員。|
|`struct`|[結構](structures.md)<br /><br /> [元組](tuples.md)<br/><br/>[條件約束](generics/constraints.md)|用來宣告結構類型。<br /><br/>用來指定的結構元組。<br/><br />也用於泛型參數條件約束。<br /><br />用於 OCaml 模組定義中的相容性。|
|`then`|[條件運算式：`if...then...else`](conditional-expressions-if-then-else.md)<br /><br />[建構函式](members/constructors.md)|條件式運算式中使用。<br /><br />也用來在物件建構後執行副作用。|
|`to`|[迴圈：`for...to` 運算式](loops-for-to-expression.md)|用於`for`表示某個範圍的迴圈。|
|`true`|[基本類型](primitive-types.md)|做為布林常值。|
|`try`|[例外狀況：Try...with 運算式](exception-handling/the-try-with-expression.md)<br /><br />[例外狀況：Try...try...finally 運算式](exception-handling/the-try-finally-expression.md)|用來介紹可能會產生例外狀況的程式碼區塊。 可搭配使用`with`或`finally`。|
|`type`|[F# 類型](fsharp-types.md)<br /><br />[類別](classes.md)<br /><br />[記錄](records.md)<br /><br />[結構](structures.md)<br /><br />[列舉](enumerations.md)<br /><br />[差別聯集](discriminated-unions.md)<br /><br />[類型縮寫](type-abbreviations.md)<br /><br />[測量單位](units-of-measure.md)|用來宣告類別、 記錄、 結構、 差別等位、 列舉型別、 度量單位，或類型縮寫。|
|`upcast`|[轉型和轉換](casting-and-conversions.md)|用來轉換到較高的繼承鏈結中的類型。|
|`use`|[資源管理：`use` 關鍵字](resource-management-the-use-keyword.md)|用來取代`let`需要的值`Dispose`呼叫以釋放資源。|
|`use!`|[計算運算式](computation-expressions.md)<br /><br />[非同步工作流程](asynchronous-workflows.md)|用來取代`let!`非同步工作流程和其他計算值的運算式需要`Dispose`呼叫以釋放資源。|
|`val`|[明確欄位：`val` 關鍵字](members/explicit-fields-the-val-keyword.md)<br /><br />[簽章](signatures.md)<br /><br />[成員](members/index.md)|使用中的簽章可指定一個值或成員，在有限的情況下宣告的型別。|
|`void`|[基本類型](primitive-types.md)|表示.NET`void`型別。 與其他.NET 語言交互操作時，會使用它。|
|`when`|[條件約束](generics/constraints.md)|使用布林值條件 (*時成立條件*) 模式比對，並導入泛型類型參數的條件約束子句。|
|`while`|[迴圈：`while...do` 運算式](loops-while-do-expression.md)|Uvozuje konstruktor cyklu。|
|`with`|[比對運算式](match-expressions.md)<br /><br />[物件運算式](object-expressions.md)<br /><br />[複製和更新記錄運算式](copy-and-update-record-expressions.md)<br /><br />[類型延伸模組](type-extensions.md)<br /><br />[例外狀況：`try...with`運算式](exception-handling/the-try-with-expression.md)|可搭配使用`match`模式比對運算式中的關鍵字。 也用來在物件運算式中，記錄複製的運算式，並輸入擴充功能引進成員定義，並造成例外狀況處理常式。|
|`yield`|[序列](sequences.md)|序列運算式中使用，以產生一連串的值。|
|`yield!`|[計算運算式](computation-expressions.md)<br /><br />[非同步工作流程](asynchronous-workflows.md)|用於計算運算式，以將指定的計算運算式的結果附加至包含的計算運算式結果的集合。|

下列語彙基元已保留在F#因為它們是 OCaml 語言的關鍵字：

* `asr`
* `land`
* `lor`
* `lsl`
* `lsr`
* `lxor`
* `mod`
* `sig`

如果您使用`--mlcompatibility`做為識別項編譯器選項時，上述的關鍵字是可供使用。

下列語彙基元保留關鍵字的未來擴充F#語言：

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

- [F# 語言參考](index.md)
- [符號和運算子參考](symbol-and-operator-reference/index.md)
- [編譯器選項](compiler-options.md)
