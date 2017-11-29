---
title: "F# 語言參考"
description: "找到 F # 語言功能的資訊從這個語言的語彙基元、 概念、 類型、 運算式和編譯器支援建構主題參考。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: b1707be1-7b7c-4fdd-a717-d9c190bc5fb5
ms.openlocfilehash: 0d26d5a6f47ce8a92aefe338ea8c39295d042794
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="f-language-reference"></a>F# 語言參考

此區段是 F # 語言，以.NET 為目標的多典範程式語言的參考。 F# 語言支援函式、物件導向和命令式程式設計語言。


## <a name="f-tokens"></a>F# 語彙基元
下表顯示的參考主題提供作為 F# 語彙基元之關鍵字、符號和常值的表格。



|標題|說明|
|-----|-----------|
|[關鍵字參考](keyword-reference.md)|包含所有 F# 語言關鍵字相關資訊的連結。|
|[符號和運算子參考](symbol-and-operator-reference/index.md)|包含 F# 語言使用之符號和運算子的表格。|
|[常值](literals.md)|描述 F# 常值的語法以及如何指定 F# 常值的類型資訊。|

## <a name="f-language-concepts"></a>F# 語言概念
下表顯示描述語言概念的可用參考主題。



|標題|描述|
|-----|-----------|
|[函式](functions/index.md)|函式是所有程式設計語言的基礎程式執行單位。 如同其他語言，F# 函式有名稱、可以有參數並且接受引數，而且也有主體。 F# 也支援函式程式設計建構，例如將函式視為值、在運算式中使用不具名函式、組合函式以形成新函式、局部調用函式，以及透過部分套用函式引數的隱含定義函式。|
|[F# 類型](fsharp-types.md)|描述 F# 中所使用的類型以及 F# 類型的命名及描述方式。|
|[類型推斷](type-inference.md)|描述 F# 編譯器如何推斷值、變數、參數和傳回值的類型。|
|[自動一般化](generics/automatic-generalization.md)|描述 F# 的泛型建構。|
|[繼承](inheritance.md)|描述繼承，這是用來在物件導向程式設計中建立 "is-a" 關聯性 (或稱子類型) 的模型。|
|[成員](members/index.md)|描述 F# 物件類型的成員。|
|[參數和引數](Parameters-and-Arguments.md)|描述對定義參數以及將引數傳遞至函式、方法和屬性的語言支援， 其中包含如何以參考方式傳遞的詳細資訊。|
|[運算子多載](operator-overloading.md)|描述如何在類別或記錄類型以及共用層多載算術運算子。|
|[轉型和轉換](casting-and-conversions.md)|描述 F# 中對類型轉換的支援。|
|[存取控制](access-control.md)|描述 F# 的存取控制。 存取控制表示宣告哪些用戶端能夠使用特定程式項目，例如類型、方法和函式等等。|
|[模式比對](pattern-matching.md)|描述模式，這是轉換輸入資料的規則，在 F# 語言中用於擷取具有模式的比較資料、將資料分解為構成部分，或是以各種方式從資料擷取資訊。|
|[使用中模式](active-patterns.md)|描述作用中的模式。 作用中的模式可讓您定義可細分輸入資料的具名部分。 您可以使用作用中的模式，以自訂方式分解每個部分的資料。|
|[判斷提示](assertions.md)|描述 `assert` 運算式，這個偵錯功能可用來測試運算式。 當運算式在偵測模式中發生錯誤時，判斷提示會顯示系統錯誤對話方塊。|
|[例外狀況處理](exception-handling/index.md)|包含 F# 語言例外狀況處理支援的資訊。|
|[屬性](attributes.md)|描述可讓中繼資料套用至程式設計建構的屬性。|
|[資源管理：`use` 關鍵字](resource-management-the-use-keyword.md)|描述可控制資源初始設定及解除的關鍵字 `use` 和 `using`。|
|[命名空間](namespaces.md)|描述 F# 的命名空間支援。 命名空間可讓您將名稱附加至程式項目群組，將程式碼依相關功能分類。|
|[模組](modules.md)|描述模組。 F# 模組是 F# 程式碼群組，例如 F# 程式中的值、類型和函式值。 程式碼分組成不同模組有助於將相關程式碼整理到同一處，以及避免程式中發生名稱衝突。|
|[匯入宣告：`open` 關鍵字](import-declarations-the-open-keyword.md)|描述 `open` 的運作方式。 使用匯入宣告指定某個模組或命名空間後，就可以直接參考該模組或命名空間內的項目，而無須使用完整名稱。|
|[簽章](signatures.md)|描述簽章和簽章檔。 簽章檔案包含一組 F# 程式項目的公開金鑰相關資訊，例如類型、命名空間和模組。 它可用來指定這些程式項目的協助工具。|
|[XML 文件](xml-documentation.md)|描述針對 XML 文件註解 (也稱為三斜線註解) 產生文件檔案的支援。 您可以從 F# 的程式碼註解產生文件，就如同其他 .NET 語言一樣。|
|[詳細語法](verbose-syntax.md)|描述未啟用輕量型語法時的 F# 建構語法。 詳細語法是透過程式碼頂端的 `#light "off"` 指示詞所表示。|

## <a name="f-types"></a>F# 類型
下表顯示描述 F# 語言所支援類型的可用參考主題。



|標題|描述|
|-----|-----------|
|[值](values/index.md)|描述值，這是具有特定類型且不可變的數量；值可以是整數或浮點數、字元或文字、清單、序列、陣列、元組、差別聯集、記錄、類別類型或函式值。|
|[基本類型](primitive-types.md)|描述 F# 語言中使用的基本類型。 它也會提供對應的 .NET 類型以及每個類型的最小值和最大值。|
|[單位類型](unit-type.md)|描述 `unit` 類型，這個類型表示缺少特定值；`unit` 類型只有單一值，作為沒有或不需要其他值時的預留位置。|
|[字串](strings.md)|描述 F# 中的字串。 `string` 類型以一連串的 Unicode 字元表示不可變文字。 `string` 是 `System.String` 在 .NET Framework 中的別名。|
|[元組](tuples.md)|描述元組，這是不具名但有序之值 (可能是不同的類型) 的群組。|
|[F# 集合類型](fsharp-collection-types.md)|F # 函式集合類型的概觀，包括陣列、清單、序列 (seq)、對應和集的類型。|
|[清單](lists.md)|描述清單。 F# 的清單是一連串有序且不可變的項目，而所有項目的類型都相同。|
|[選項](options.md)|描述選項類型。 F# 中的選項於不一定有值時使用。 選項有基礎類型，而且可能擁有該類型的值或沒有值。|
|[序列](sequences.md)|描述序列。 序列是一連串的邏輯項目，而所有項目的類型都相同。 個別序列項目只在需要時才會計算，因此表示法可能會比常值項目計數還小。|
|[陣列](arrays.md)|描述陣列。 陣列是一系列固定大小、以零起始、可變的連續資料項目，而所有項目的類型都相同。|
|[記錄](records.md)|描述記錄。 記錄表示具名值的簡單彙總，並選擇性地搭配成員。|
|[差別聯集](discriminated-unions.md)|描述差別聯集，此種類型支援的值可以是各式各樣具名案例的其中任何一種，且每個聯集的值和類型也不一定相同。|
|[列舉](enumerations.md)|描述列舉，這是具有一組已定義之具名值的類型。 列舉可用來取代常值，讓程式碼更容易閱讀及維護。|
|[參考儲存格](reference-cells.md)|描述參考儲存格，這是可讓您以參考語意建立可變變數的儲存位置。|
|[類型縮寫](type-abbreviations.md)|描述類型縮寫，這是類型的替代名稱。|
|[類別](classes.md)|描述類別，這是表示可以有屬性、方法和事件之物件的類型。|
|[結構](structures.md)|描述結構，這是一種比較精簡的物件類型，適用於資料量較少且行為簡單的類型，效率比類別更好。|
|[介面](interfaces.md)|描述介面，介面可指定其他類別應提供實作的一組相關成員。|
|[抽象類別](abstract-classes.md)|描述抽象類別，這種類別不見得會實作出所有或部分成員，而是留待衍生類別各自提供實作。|
|[類型延伸模組](type-extensions.md)|描述類型擴充，可讓您將成員新增至先前定義的物件類型。|
|[彈性類型](flexible-types.md)|描述彈性類型。 彈性類型註解表示參數、變數或值的類型與指定的類型相容，而相容性是由類別或介面的物件導向階層中的位置所決定。|
|[委派](delegates.md)|描述將函式呼叫表示為物件的委派。|
|[測量單位](units-of-measure.md)|描述測量單位。 F# 中的浮點值可以有通常用來表示長度、容量、質量等的關聯測量單位。|
|[類型提供者](../tutorials/type-providers/index.md)|描述型別提供者，並且提供逐步解說如何使用內建的型別提供者來存取資料庫和 Web 服務的連結。|

## <a name="f-expressions"></a>F# 運算式
下表列出描述 F# 運算式的主題。

|標題|說明|
|-----|-----------|
|[條件運算式：`if...then...else`](conditional-expressions-if-then-else.md)|描述 `if...then...else` 運算式，這個運算式會根據指定的布林運算式，執行不同的程式碼分支，也會運算出不同的值。|
|[比對運算式](match-expressions.md)|描述 `match` 運算式，此種運算式提供分支控制，可根據運算式與一組模式的比較結果，決定程式應沿著哪個分支繼續執行。|
|[迴圈：`for...to` 運算式](loops-for-to-expression.md)|描述 `for...to` 運算式，這個運算式會重複執行某段迴圈，重複次數等於迴圈變數的範圍值。|
|[迴圈：`for...in` 運算式](loops-for-in-expression.md)|描述 `for...in` 運算式，這個迴圈建構會使用可列舉集合 (例如範圍運算式、序列、清單、陣列或其他支援列舉的建構) 中符合模式的所有項目，重複執行一段程式碼。|
|[迴圈：`while...do` 運算式](loops-while-do-expression.md)|描述 `while...do` 運算式，當指定的測試條件為 true 時，用來重複執行一次 (迴圈)。|
|[物件運算式](object-expressions.md)|描述物件運算式，這些運算式會根據現有的基底類型、一個介面或一組介面來建立動態建立、匿名物件類型的新執行個體。|
|[延遲運算](lazy-computations.md)|描述延遲計算，這種計算不會立刻進行，而是等到真的需要評估結果時，才進行評估。|
|[計算運算式](computation-expressions.md)|描述 F# 中的計算運算式提供便利的語法，用於撰寫可以使用控制流程建構和繫結進行排序和合併的計算。 它們可以用於提供 *monad* 的便利語法，這是一種函式程式設計功能，可用來管理函式程式中的資料、控制項和副作用。 非同步工作流程是一種計算運算式，支援非同步和平行計算。 如需詳細資訊，請參閱[非同步工作流程](asynchronous-workflows.md)。|
|[非同步工作流程](asynchronous-workflows.md)|描述非同步工作流程，這是一種語言功能，可讓您使用與原本撰寫同步程式碼極為相似的方式，來撰寫非同步程式碼。|
|[程式碼引號](code-quotations.md)|描述程式碼引號，此語言功能可讓您以程式設計方式產生及使用 F# 程式碼運算式。|
|[查詢運算式](query-expressions.md)|描述查詢運算式，這種語言功能可為 F# 實作 LINQ，並且可讓您針對資料來源或可列舉集合撰寫查詢。|

## <a name="compiler-supported-constructs"></a>編譯器支援的建構
下表列出描述編譯器支援之特殊建構的主題。

|主題|說明|
|-----|-----------|
|[編譯器選項](compiler-options.md)|描述 F # 編譯器的命令列選項。|
|[編譯器指示詞](compiler-directives.md)|描述處理器指示詞和編譯器指示詞。|
|[原始碼程式行、檔案與路徑識別項](source-line-file-path-identifiers.md)|描述識別項 `__LINE__`、`__SOURCE_DIRECTORY__` 和 `__SOURCE_FILE__`，這些內建值可讓您存取原始程式碼中的行號、目錄和檔案名稱。|

## <a name="see-also"></a>另請參閱
[Visual F#](../index.md)
