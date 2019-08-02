---
title: F# 類型
description: 瞭解在中F#使用的類型, 以及如何F#命名和描述類型。
ms.date: 05/16/2016
ms.openlocfilehash: 826bcb56aad3b50fbfcf8f807bb34e9cdcdecaf7
ms.sourcegitcommit: 8c6426a3d2adff5fbcbe1fed0f28eda718c15351
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2019
ms.locfileid: "68733493"
---
# <a name="f-types"></a>F# 類型

本主題描述在中F#使用的類型, 以及如何F#命名和描述類型。

## <a name="summary-of-f-types"></a>F#類型摘要
某些類型會視為基本型別, 例如各種大小的布林`bool`數值型別和整數和浮點類型, 其中包括位元組和字元的類型。 這些類型會在[基本類型](primitive-types.md)中說明。

語言內建的其他類型包括元組、清單、陣列、序列、記錄和區分等位。 如果您有其他 .NET 語言的經驗, 而且正在F#學習, 您應該閱讀每一種類型的主題。 本主題的[相關主題](https://msdn.microsoft.com/library/#rel)一節包含這些類型的詳細資訊連結。 這些F#特定型別支援功能性程式設計語言通用的程式設計樣式。 其中許多類型在連結F#庫中都有相關聯的模組, 可支援這些類型的一般作業。

函數的類型包含參數類型和傳回類型的相關資訊。

.NET Framework 是物件類型、介面類別型、委派類型和其他專案的來源。 您可以像在任何其他 .NET 語言一樣, 定義自己的物件類型。

此外, F#程式碼也可以定義別名 (命名為*類型縮寫*), 這是類型的替代名稱。 當類型可能會在未來變更, 而且您想要避免變更相依于該類型的程式碼時, 您可以使用類型縮寫。 或者, 您可以使用類型縮寫作為類型的易記名稱, 讓程式碼更容易閱讀和瞭解。

F#提供有用的集合型別, 並以功能程式設計為考慮。 使用這些集合類型可協助您撰寫更能以樣式運作的程式碼。 如需詳細資訊, 請參閱[ F#集合類型](fsharp-collection-types.md)。

## <a name="syntax-for-types"></a>類型的語法
在F#程式碼中, 您通常必須寫出類型的名稱。 每個型別都有一個語法形式, 而且您會在型別注釋、抽象方法宣告、委派宣告、簽章和其他結構中使用這些語法形式。 每當您在解譯器中宣告新的程式結構時, 解譯器就會列印結構的名稱和其類型的語法。 這個語法可能只是使用者定義型別的識別碼, 或是內建的識別碼, 例如適用于`int`或`string`, 但對於更複雜的類型, 語法更為複雜。

下表顯示類型的類型語法F#層面。

|類型|類型語法|範例|
|----|-----------|--------|
|基本類型|*type-name*|`int`<br /><br />`float`<br /><br />`string`|
|匯總類型 (類別、結構、等位、記錄、列舉等等)|*type-name*|`System.DateTime`<br /><br />`Color`|
|類型縮寫|*type-abbreviation-name*|`bigint`|
|完整限定類型|*namespaces.type-name*<br /><br />或<br /><br />*modules.type-name*<br /><br />或<br /><br />*namespaces.modules.type-name*|`System.IO.StreamWriter`|
|array|*類型-名稱*[] 或<br /><br />*類型名稱*陣列|`int[]`<br /><br />`array<int>`<br /><br />`int array`|
|二維陣列|*type-name*[,]|`int[,]`<br /><br />`float[,]`|
|三維陣列|*type-name*[,,]|`float[,,]`|
|tuple|*類型-name1*&#42; *類型-name2* 。|例如, `(1,'b',3)`具有類型`int * char * int`|
|Generic Type - 泛型類型|*型別參數* *泛型型別名稱*<br /><br />或<br /><br />*generic-type-name*&lt;*type-parameter-list*&gt;|`'a list`<br /><br />`list<'a>`<br /><br />`Dictionary<'key, 'value>`|
|結構化型別 (提供特定型別引數的泛型型別)|*型別引數* *泛型型別名稱*<br /><br />或<br /><br />*generic-type-name*&lt;*type-argument-list*&gt;|`int option`<br /><br />`string list`<br /><br />`int ref`<br /><br />`option<int>`<br /><br />`list<string>`<br /><br />`ref<int>`<br /><br />`Dictionary<int, string>`|
|具有單一參數的函數類型|*parameter-type1* -&gt; *return-type*|採用並`int` `string`傳回具有類型的函式`int -> string`|
|具有多個參數的函數類型|*參數-type1*  - *參數-type2*  - ...-&gt;傳回類型&gt; &gt;|接受`int` 和並`string`傳回具有類型的函式`float``int -> float -> string`|
|高階函式做為參數|(*函數類型*)|`List.map`具有類型`('a -> 'b) -> 'a list -> 'b list`|
|Delegate - 委派|函*式類型*的委派|`delegate of unit -> int`|
|彈性類型|#*type-name*|`#System.Windows.Forms.Control`<br /><br />`#seq<int>`|

## <a name="related-topics"></a>相關主題

|主題|描述|
|-----|-----------|
|[基本類型](primitive-types.md)|描述內建的簡單類型, 例如整數類型、布林類型和字元類型。|
|[單位類型](unit-type.md)|描述類型, 這是具有一個值且以 () 表示的類型, `void`相當C#于和`Nothing`中的 Visual Basic。 `unit`|
|[元組](tuples.md)|描述元組類型, 這是一種類型, 其中包含分組、三個、時等的任何類型之相關聯的值。|
|[選項](options.md)|描述選項類型, 也就是可能具有值或空白的類型。|
|[清單](lists.md)|描述所有相同類型的已排序、不可變系列元素的清單。|
|[陣列](arrays.md)|描述陣列, 這是相同類型的可變元素的已排序集合, 其佔用連續的記憶體區塊, 而且是固定大小。|
|[序列](sequences.md)|描述代表邏輯數列值的序列類型。個別值只會在必要時計算。|
|[記錄](records.md)|描述記錄類型, 這是一個小型的已命名值匯總。|
|[差別聯集](discriminated-unions.md)|描述區分聯集類型, 其值可以是一組可能類型的任何一種類型。|
|[函式](./functions/index.md)|描述函數值。|
|[類別](classes.md)|描述類別類型, 這是對應于 .NET 參考型別的物件類型。 類別類型可以包含成員、屬性、實介面和基底類型。|
|[結構](structures.md)|`struct`描述類型, 這是對應于 .net 實數值型別的物件類型。 此`struct`類型通常代表小型的資料匯總。|
|[介面](interfaces.md)|描述介面類別型, 這是代表一組提供特定功能但不包含任何資料之成員的類型。 介面類別型必須由物件類型執行, 才能發揮效用。|
|[委派](delegates.md)|描述委派類型, 其代表當做物件的函式。|
|[列舉](enumerations.md)|描述列舉類型, 其值屬於一組已命名的值。|
|[屬性](attributes.md)|描述用來指定另一個類型之中繼資料的屬性。|
|[例外狀況類型](./exception-handling/exception-types.md)|描述指定錯誤資訊的例外狀況。|
