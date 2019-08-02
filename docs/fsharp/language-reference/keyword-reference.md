---
title: 關鍵字參考
description: 尋找所有F#語言關鍵字的相關資訊連結。
ms.date: 05/16/2016
ms.openlocfilehash: 680b270a99eff7aa98652579d2fd31b4b05080ca
ms.sourcegitcommit: 8c6426a3d2adff5fbcbe1fed0f28eda718c15351
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2019
ms.locfileid: "68733488"
---
# <a name="keyword-reference"></a>關鍵字參考

本主題包含所有F#語言關鍵字的相關資訊連結。

## <a name="f-keyword-table"></a>F#關鍵字表

下表以字母順序F#顯示所有關鍵詞, 以及簡短描述和包含詳細資訊的相關主題連結。

|關鍵字|連結|說明|
|-------|----|-----------|
|`abstract`|[成員](./members/index.md)<br /><br />[抽象類別](abstract-classes.md)|表示在宣告或為虛擬且具有預設實作為的類型中, 沒有任何實作的方法。|
|`and`|[`let`關係](./functions/let-bindings.md)<br /><br />[記錄](records.md)<br /><br />[成員](./members/index.md)<br /><br />[條件約束](./generics/constraints.md)|用於相互遞迴系結和記錄、屬性宣告, 以及泛型參數上的多個條件約束。|
|`as`|[類別](classes.md)<br /><br />[模式比對](Pattern-Matching.md)|用來為目前的類別物件指定物件名稱。 也可用來在模式比對中提供完整模式的名稱。|
|`assert`|[判斷提示](assertions.md)|在進行偵錯工具期間用來驗證程式代碼。|
|`base`|[類別](classes.md)<br /><br />[繼承](inheritance.md)|當做基類物件的名稱使用。|
|`begin`|[詳細語法](verbose-syntax.md)|在 verbose 語法中, 表示程式碼區塊的開頭。|
|`class`|[類別](classes.md)|在 verbose 語法中, 表示類別定義的開頭。|
|`default`|[成員](./members/index.md)|表示抽象方法的實值;與抽象方法宣告一起使用, 以建立虛擬方法。|
|`delegate`|[委派](delegates.md)|用來宣告委派。|
|`do`|[do 繫結](./functions/do-bindings.md)<br /><br />[環回`for...to`運算式](loops-for-to-expression.md)<br /><br />[環回`for...in`運算式](loops-for-in-expression.md)<br /><br />[環回`while...do`運算式](loops-while-do-expression.md)|用於迴圈結構中, 或用來執行命令式程式碼。|
|`done`|[詳細語法](verbose-syntax.md)|在 verbose 語法中, 表示迴圈運算式中程式碼區塊的結尾。|
|`downcast`|[轉型和轉換](casting-and-conversions.md)|用來轉換成繼承鏈中較低的類型。|
|`downto`|[環回`for...to`運算式](loops-for-to-expression.md)|`for`在運算式中, 在反向計算時使用。|
|`elif`|[條件運算式：`if...then...else`](conditional-expressions-if-then-else.md)|用於條件式分支。 的簡短形式`else if`。|
|`else`|[條件運算式：`if...then...else`](conditional-expressions-if-then-else.md)|用於條件式分支。|
|`end`|[結構](structures.md)<br /><br />[差別聯集](discriminated-unions.md)<br /><br />[記錄](records.md)<br /><br />[類型延伸模組](type-extensions.md)<br /><br />[詳細語法](verbose-syntax.md)|在 [類型定義] 和 [類型延伸] 中, 表示成員定義區段的結尾。<br /><br />在 verbose 語法中, 用來指定以`begin`關鍵字開頭之程式碼區塊的結尾。|
|`exception`|[例外狀況處理](./exception-handling/index.md)<br /><br />[例外狀況類型](./exception-handling/exception-types.md)|用來宣告例外狀況類型。|
|`extern`|[外部函式](./functions/external-functions.md)|表示已宣告的程式專案是在另一個二進位或元件中定義。|
|`false`|[基本類型](primitive-types.md)|當做布林常值使用。|
|`finally`|[例外狀況：`try...finally`運算式](./exception-handling/the-try-finally-expression.md)|與`try`搭配使用, 以引進不論是否發生例外狀況而執行的程式碼區塊。|
|`fixed`|[固定匯率](fixed.md)|用來「釘選」堆疊上的指標, 以防止它被垃圾收集。|
|`for`|[環回`for...to`運算式](loops-for-to-expression.md)<br /><br />[迴圈：for...in 運算式](loops-for-in-expression.md)|用於迴圈結構中。|
|`fun`|[Lambda 運算式:`fun` 關鍵字](./functions/lambda-expressions-the-fun-keyword.md)|用於 lambda 運算式, 也稱為匿名函式。|
|`function`|[比對運算式](match-expressions.md)<br /><br />[Lambda 運算式:有趣的關鍵字](./functions/lambda-expressions-the-fun-keyword.md)|用來`fun`做為關鍵字的較短替代方法`match` , 以及在具有單一引數之模式比對的 lambda 運算式中的運算式。|
|`global`|[命名空間](namespaces.md)|用來參考頂層 .NET 命名空間。|
|`if`|[條件運算式：`if...then...else`](conditional-expressions-if-then-else.md)|用於條件式分支結構。|
|`in`|[迴圈：for...in 運算式](loops-for-in-expression.md)<br /><br />[詳細語法](verbose-syntax.md)|用於序列運算式, 而在詳細語法中則用來分隔運算式與系結。|
|`inherit`|[繼承](inheritance.md)|用來指定基類或基底介面。|
|`inline`|[函式](./functions/index.md)<br /><br />[內嵌函式](./functions/inline-functions.md)|用來指出應該直接整合到呼叫端程式碼中的函式。|
|`interface`|[介面](interfaces.md)|用來宣告和執行介面。|
|`internal`|[存取控制](access-control.md)|用來指定成員可以在元件內部看到, 而不是在其外部。|
|`lazy`|[延遲運算式](lazy-expressions.md)|用來指定只有在需要結果時才要執行的運算式。|
|`let`|[`let`關係](./functions/let-bindings.md)|用來將名稱與值或函式建立關聯或系結。|
|`let!`|[非同步工作流程](asynchronous-workflows.md)<br /><br />[計算運算式](computation-expressions.md)|用於非同步工作流程, 以將名稱系結至非同步計算的結果, 或在其他計算運算式中用來將名稱系結至計算類型的結果。|
|`match`|[比對運算式](match-expressions.md)|藉由比較值與模式來進行分支。|
|`match!`|[計算運算式](computation-expressions.md#match)|用來以內嵌方式呼叫計算運算式, 並在其結果上進行模式比對。|
|`member`|[成員](./members/index.md)|用來宣告物件類型中的屬性或方法。|
|`module`|[模組](modules.md)|用來將名稱與相關類型、值和函式的群組建立關聯, 以邏輯方式將它與其他程式碼分開。|
|`mutable`|[let 繫結](./functions/let-bindings.md)|用來宣告變數, 也就是可以變更的值。|
|`namespace`|[命名空間](namespaces.md)|用來將名稱與一組相關類型和模組建立關聯, 以邏輯方式將它與其他程式碼分開。|
|`new`|[建構函式](./members/constructors.md)<br /><br />[條件約束](./generics/constraints.md)|用來宣告、定義或叫用建立可建立物件之或的函式。<br /><br />也用於泛型參數條件約束, 以指出類型必須具有特定的函式。|
|`not`|[符號和運算子參考](./symbol-and-operator-reference/index.md)<br /><br />[條件約束](./generics/constraints.md)|實際上並不是關鍵字。 不過, `not struct`組合會當做泛型參數條件約束使用。|
|`null`|[Null 值](./values/null-values.md)<br /><br />[條件約束](./generics/constraints.md)|表示沒有物件。<br /><br />也用於泛型參數條件約束中。|
|`of`|[差別聯集](discriminated-unions.md)<br /><br />[委派](delegates.md)<br /><br />[例外狀況類型](./exception-handling/exception-types.md)|用於區分等位, 表示值的類別目錄類型, 以及委派和例外狀況宣告中。|
|`open`|[匯入宣告：`open` 關鍵字](import-declarations-the-open-keyword.md)|用來讓命名空間或模組的內容可供使用, 而不需要限定。|
|`or`|[符號和運算子參考](./symbol-and-operator-reference/index.md)<br /><br />[條件約束](./generics/constraints.md)|以布林值條件`or`運算子來使用。 相當於 `||`。<br /><br />也用於成員條件約束。|
|`override`|[成員](./members/index.md)|用來執行與基底版本不同的抽象或虛擬方法版本。|
|`private`|[存取控制](access-control.md)|將成員的存取限制為相同類型或模組中的程式碼。|
|`public`|[存取控制](access-control.md)|允許從類型外部存取成員。|
|`rec`|[函式](./functions/index.md)|用來表示函數是遞迴的。|
|`return`|[非同步工作流程](Asynchronous-Workflows.md)<br /><br />[計算運算式](computation-expressions.md)|用來指出要提供做為計算運算式結果的值。|
|`return!`|[計算運算式](computation-expressions.md)<br /><br />[非同步工作流程](asynchronous-workflows.md)|用來表示計算運算式, 在評估時, 會提供包含計算運算式的結果。|
|`select`|[查詢運算式](query-expressions.md)|用於查詢運算式中, 以指定要解壓縮的欄位或資料行。 請注意, 這是內容關鍵字, 這表示它實際上並不是保留字, 而且它的作用就像是適當內容中的關鍵字。|
|`static`|[成員](./members/index.md)|用來表示方法或屬性, 不需要類型的實例就可以呼叫, 或是在類型的所有實例之間共用的值成員。|
|`struct`|[結構](structures.md)<br /><br /> [元組](tuples.md)<br/><br/>[條件約束](./generics/constraints.md)|用來宣告結構類型。<br /><br/>用來指定結構元組。<br/><br />也用於泛型參數條件約束中。<br /><br />用於模組定義中的 OCaml 相容性。|
|`then`|[條件運算式：`if...then...else`](conditional-expressions-if-then-else.md)<br /><br />[建構函式](./members/constructors.md)|在條件運算式中使用。<br /><br />也可用來執行物件結構後的副作用。|
|`to`|[環回`for...to`運算式](loops-for-to-expression.md)|用於迴圈`for`中, 表示範圍。|
|`true`|[基本類型](primitive-types.md)|當做布林常值使用。|
|`try`|[例外狀況：嘗試 .。。with 運算式](./exception-handling/the-try-with-expression.md)<br /><br />[例外狀況：嘗試 .。。finally 運算式](./exception-handling/the-try-finally-expression.md)|用來引進可能會產生例外狀況的程式碼區塊。 與`with` 或`finally`搭配使用。|
|`type`|[F# 類型](fsharp-types.md)<br /><br />[類別](classes.md)<br /><br />[記錄](records.md)<br /><br />[結構](structures.md)<br /><br />[列舉](enumerations.md)<br /><br />[差別聯集](discriminated-unions.md)<br /><br />[類型縮寫](type-abbreviations.md)<br /><br />[測量單位](units-of-measure.md)|用來宣告類別、記錄、結構、區分聯集、列舉類型、量值單位或類型縮寫。|
|`upcast`|[轉型和轉換](casting-and-conversions.md)|用來轉換成繼承鏈中較高的類型。|
|`use`|[資源管理:`use` 關鍵字](resource-management-the-use-keyword.md)|用於, 而`let`不是需要`Dispose`呼叫以釋放資源的值。|
|`use!`|[計算運算式](computation-expressions.md)<br /><br />[非同步工作流程](asynchronous-workflows.md)|`let!`在非同步工作流程和其他計算運算式中使用, 而不是`Dispose`需要呼叫以釋放資源的值。|
|`val`|[明確欄位：`val` 關鍵字](./members/explicit-fields-the-val-keyword.md)<br /><br />[簽章](signatures.md)<br /><br />[成員](./members/index.md)|在有限的情況下, 在簽章中用來表示值, 或在宣告成員的類型中使用。|
|`void`|[基本類型](primitive-types.md)|表示 .net `void`類型。 與其他 .NET 語言交互操作時使用。|
|`when`|[條件約束](./generics/constraints.md)|用於模式比對上的布林值條件 (若有*防護*), 並引進泛型型別參數的條件約束子句。|
|`while`|[環回`while...do`運算式](loops-while-do-expression.md)|引進迴圈結構。|
|`with`|[比對運算式](match-expressions.md)<br /><br />[物件運算式](object-expressions.md)<br /><br />[複製和更新記錄運算式](copy-and-update-record-expressions.md)<br /><br />[類型延伸模組](type-extensions.md)<br /><br />[例外狀況：`try...with`運算式](./exception-handling/the-try-with-expression.md)|與模式比對`match`運算式中的關鍵字一起使用。 也用於物件運算式、記錄複製運算式, 以及引入成員定義的類型延伸, 以及引進例外狀況處理常式。|
|`yield`|[序列](sequences.md)|用於序列運算式中, 以產生序列的值。|
|`yield!`|[計算運算式](computation-expressions.md)<br /><br />[非同步工作流程](asynchronous-workflows.md)|用於計算運算式中, 將指定計算運算式的結果附加至包含計算運算式的結果集合。|

下列標記會保留在中F# , 因為它們是 OCaml 語言中的關鍵字:

* `asr`
* `land`
* `lor`
* `lsl`
* `lsr`
* `lxor`
* `mod`
* `sig`

如果您使用`--mlcompatibility`編譯器選項, 則可以使用上述關鍵字做為識別碼。

下列權杖會保留為關鍵字, 以供未來擴充F#語言之用:

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
- [符號和運算子參考](./symbol-and-operator-reference/index.md)
- [編譯器選項](compiler-options.md)
