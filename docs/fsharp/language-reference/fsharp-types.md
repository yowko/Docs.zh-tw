---
title: 類型
description: '瞭解 F # 中使用的類型，以及 F # 類型的命名和描述方式。'
ms.date: 08/15/2020
ms.openlocfilehash: a86d8e8f672d8399b02bb193ae04e1f0d46720b6
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812064"
---
# <a name="f-types"></a>F# 類型

本主題描述 F # 中使用的類型，以及 F # 類型的命名和描述方式。

## <a name="summary-of-f-types"></a>F # 類型摘要

某些類型會被視為 *基本類型*，例如各種大小的布林型別 `bool` 和整數和浮點數類型，包括位元組和字元的類型。 這些類型會在 [基本類型](basic-types.md)中描述。

語言內建的其他類型包括元組、清單、陣列、序列、記錄和區分等位。 如果您有使用其他 .NET 語言的經驗，且正在學習 F #，則應該閱讀每一種類型的相關主題。 這些 F # 特定類型支援函式程式設計語言常見的程式設計樣式。 其中許多型別在 F # 程式庫中都有相關聯的模組，可支援這些類型上的一般作業。

函數的類型包含參數類型和傳回類型的相關資訊。

.NET Framework 是物件類型、介面類別型、委派類型和其他專案的來源。 您可以定義自己的物件類型，就像在任何其他 .NET 語言中一樣。

此外，F # 程式碼可以定義別名（名稱為「 *類型縮寫*」），這是類型的替代名稱。 當類型未來可能會變更，而且您想要避免變更相依于型別的程式碼時，您可以使用類型縮寫。 或者，您可以使用類型縮寫做為類型的易記名稱，使程式碼更容易閱讀和瞭解。

F # 提供實用的集合型別，這些型別是以功能程式設計為考慮而設計的。 使用這些集合類型，可協助您撰寫更能以樣式運作的程式碼。 如需詳細資訊，請參閱 [F # 集合類型](fsharp-collection-types.md)。

## <a name="syntax-for-types"></a>類型的語法

在 F # 程式碼中，您通常必須寫出類型的名稱。 每個類型都有一個語法形式，而您可以在類型批註、抽象方法宣告、委派宣告、簽章和其他結構中使用這些語法形式。 每當您在解譯器中宣告新的程式結構時，解譯器就會列印結構的名稱和其類型的語法。 這個語法可能只是使用者自訂類型的識別碼，也可能是內建的識別碼（例如 `int` 或 `string` ），但對於更複雜的型別來說，語法較複雜。

下表顯示 F # 型別語法的各個層面。

|類型|類型語法|範例|
|----|-----------|--------|
|基本類型|*類型名稱*|`int`<br /><br />`float`<br /><br />`string`|
|匯總類型 (類別、結構、等位、記錄、列舉等等) |*類型名稱*|`System.DateTime`<br /><br />`Color`|
|類型縮寫|*類型縮寫-名稱*|`bigint`|
|完整型別|*命名空間。類型名稱*<br /><br />或<br /><br />*模組。類型名稱*<br /><br />或<br /><br />*命名空間。模組。類型名稱*|`System.IO.StreamWriter`|
|array|*類型名稱*[] 或<br /><br />*類型名稱* 陣列|`int[]`<br /><br />`array<int>`<br /><br />`int array`|
|二維陣列|*類型名稱*[，]|`int[,]`<br /><br />`float[,]`|
|三維陣列|*類型名稱*[，，]|`float[,,]`|
|Tuple|*類型-name1* &#42; *類型-name2* .。。|例如， `(1,'b',3)` 具有類型 `int * char * int`|
|Generic Type - 泛型類型|*類型參數**泛型型別名稱*<br /><br />或<br /><br />*泛型型別名稱* &lt;*類型參數-清單*&gt;|`'a list`<br /><br />`list<'a>`<br /><br />`Dictionary<'key, 'value>`|
|結構化類型 (提供特定型別引數的泛型型別) |*類型-引數**泛型型別名稱*<br /><br />或<br /><br />*泛型型別名稱* &lt;*類型-引數-清單*&gt;|`int option`<br /><br />`string list`<br /><br />`int ref`<br /><br />`option<int>`<br /><br />`list<string>`<br /><br />`ref<int>`<br /><br />`Dictionary<int, string>`|
|具有單一參數的函數類型|*參數-type1*  - &gt;傳回*類型*|接受 `int` 並傳回具有類型的函式 `string``int -> string`|
|具有多個參數的函數類型|*參數-type1*  - &gt;*參數-type2*  - &gt;...-傳回 &gt; *類型*|接受和的函式， `int` `float` 並傳回 `string` 具有類型的 `int -> float -> string`|
|較高的 order 函數作為參數| (*函數類型*) |`List.map` 具有類型 `('a -> 'b) -> 'a list -> 'b list`|
|Delegate - 委派|函*式類型*的委派|`delegate of unit -> int`|
|彈性類型|#*類型名稱*|`#System.Windows.Forms.Control`<br /><br />`#seq<int>`|

## <a name="related-topics"></a>[相關主題]

|主題|描述|
|-----|-----------|
|[基本類型](basic-types.md)|描述內建的簡單類型，例如整數類資料類型、布林值類型和字元類型。|
|[單位類型](unit-type.md)|描述 `unit` 類型、具有一個值的型別，以及由 ( # A1; 表示的類型，相當於 `void` c # 中和 `Nothing` Visual Basic。|
|[元組](tuples.md)|描述元組類型，這個類型是由任何類型的關聯值（以配對、三合一、時等分組）所組成。|
|[選項](options.md)|描述選項類型，此類型可能具有值或為空白。|
|[清單](lists.md)|描述清單，也就是已排序的專案，這是所有相同類型的不可變元素系列。|
|[陣列](arrays.md)|描述陣列，這些陣列是相同類型之可變動專案的已排序集合，且這些元素佔用連續的記憶體區塊，且大小為固定大小。|
|[序列](sequences.md)|描述代表邏輯序列值的序列類型。個別的值只會在必要時計算。|
|[記錄](records.md)|描述記錄類型，這是一個小型的命名值匯總。|
|[已區分的聯集](discriminated-unions.md)|描述差異聯集類型，此類型的值可以是一組可能類型的任一個。|
|[函式](./functions/index.md)|描述函數值。|
|[類別](classes.md)|描述類別類型，這是對應至 .NET 參考型別的物件類型。 類別類型可以包含成員、屬性、實介面和基底類型。|
|[結構](structures.md)|描述 `struct` 型別，這是對應至 .net 值型別的物件類型。 此 `struct` 類型通常代表較小的資料匯總。|
|[介面](interfaces.md)|描述介面型別，這些類型代表一組提供特定功能但未包含任何資料的成員。 介面型別必須由物件型別實作為有用。|
|[委派](delegates.md)|描述表示函式做為物件的委派類型。|
|[列舉](enumerations.md)|描述列舉型別，其值屬於一組命名值。|
|[屬性](attributes.md)|描述用來指定另一種類型之中繼資料的屬性。|
|[例外狀況類型](./exception-handling/exception-types.md)|描述指定錯誤資訊的例外狀況。|
