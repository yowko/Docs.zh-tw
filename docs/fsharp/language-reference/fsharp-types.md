---
title: F# 類型
description: 了解中所使用的類型F#以及F#型別是名為和所述。
ms.date: 05/16/2016
ms.openlocfilehash: bdbb89dc751970ac31fe102df009f0bff6388e52
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "33565578"
---
# <a name="f-types"></a>F# 類型

本主題說明中所使用的型別F#以及F#型別是名為和所述。


## <a name="summary-of-f-types"></a>摘要的F#類型
某些類型會被視為*基本型別*，例如布林類型`bool`和整數和浮點類型的各種不同的大小，包括位元組和字元類型。 這些類型所述[基本型別](primitive-types.md)。

其他語言內建的型別包含 tuple、 清單、 陣列、 序列、 記錄和差別聯集。 如果您使用其他.NET 語言的經驗，並學習F#，您應該閱讀的主題針對每一種類型。 中包含這些類型的詳細資訊的連結[相關主題](https://msdn.microsoft.com/library/#rel)本主題一節。 這些F#-特定型別支援共通功能的程式設計語言的程式設計樣式。 多數這些類型具有相關聯的模組，在F#支援這些型別上的一般作業的程式庫。

函式的類型包含的參數類型的相關資訊，並傳回型別。

.NET Framework 是物件型別、 介面類型、 委派類型，和其他人的來源。 正如同您可以在任何其他.NET 語言中，您可以定義自己的物件型別。

此外，F#程式碼可以定義名為的別名*類型縮寫*，屬於類型的替代名稱。 型別可能會在未來變更，和您想要避免變更類型而定的程式碼時，您可以使用類型縮寫。 或者，您可以使用類型縮寫作為一種類型，可以讓您更輕鬆地閱讀並了解的程式碼的好記名稱。

F#提供在心的功能性程式設計所設計的實用的集合型別。 使用這些集合類型，可協助您撰寫更具功能性樣式中的程式碼。 如需詳細資訊，請參閱 < [ F#集合型別](fsharp-collection-types.md)。


## <a name="syntax-for-types"></a>型別的語法
在F#程式碼中，您通常必須寫出的型別名稱。 每個型別語法的形式，而且您使用這些型別註釋、 抽象方法宣告、 委派宣告、 簽章和其他建構中的語法形式。 每當您宣告新的程式建構，解譯器中，解譯器會列印其類型名稱的建構和語法。 此語法可能只是使用者定義的型別識別項或內建識別碼與此`int`或`string`，但是對於更複雜的型別，語法就更加複雜。

下表顯示層面的型別語法F#類型。



|類型|類型語法|範例|
|----|-----------|--------|
|基本類型|*type-name*|`int`<br /><br />`float`<br /><br />`string`|
|彙總類型 （類別、 結構、 等位、 記錄、 列舉，等等）|*type-name*|`System.DateTime`<br /><br />`Color`|
|類型縮寫|*類型縮寫名稱*|`bigint`|
|完整的類型|*namespaces.type 名稱*<br /><br />或<br /><br />*modules.type 名稱*<br /><br />或<br /><br />*namespaces.modules.type 名稱*|`System.IO.StreamWriter`|
|array|*型別名稱*[] 或<br /><br />*型別名稱*陣列|`int[]`<br /><br />`array<int>`<br /><br />`int array`|
|二維陣列|*型別名稱*[、]|`int[,]`<br /><br />`float[,]`|
|三維陣列|*型別名稱*[、]|`float[,,]`|
|tuple|*型別 name1* &#42; *型別-name2* ...|比方說，`(1,'b',3)`類型 `int * char * int`|
|Generic Type - 泛型類型|*型別參數**泛型型別名稱*<br /><br />或<br /><br />*泛型型別名稱*&lt;*型別參數清單*&gt;|`'a list`<br /><br />`list<'a>`<br /><br />`Dictionary<'key, 'value>`|
|建構的型別 （已提供的特定類型引數的泛型類型）|*型別引數**泛型型別名稱*<br /><br />或<br /><br />*泛型型別名稱*&lt;*類型引數清單*&gt;|`int option`<br /><br />`string list`<br /><br />`int ref`<br /><br />`option<int>`<br /><br />`list<string>`<br /><br />`ref<int>`<br /><br />`Dictionary<int, string>`|
|具有單一參數的函式類型|*參數 type1*  - &gt; *傳回型別*|使用的函式`int`，並傳回`string`類型 `int -> string`|
|具有多個參數的函式類型|*參數 type1*  - &gt; *參數 type2*  - &gt; ...-&gt; *傳回型別*|使用的函式`int`並`float`，並傳回`string`類型 `int -> float -> string`|
|做為參數的較高順序函式|(*函式型別*)|`List.map` 具有類型 `('a -> 'b) -> 'a list -> 'b list`|
|Delegate - 委派|委派的*函式類型*|`delegate of unit -> int`|
|彈性類型|#*類型名稱*|`#System.Windows.Forms.Control`<br /><br />`#seq<int>`|

## <a name="related-topics"></a>相關主題


|主題|描述|
|-----|-----------|
|[基本類型](primitive-types.md)|描述之內建簡單型別，例如整數類資料類型、 布林值的型別和字元類型。|
|[單位類型](unit-type.md)|描述`unit`類型、 類型，有一個值，也會指出由 （）; 相當於`void`在C#並`Nothing`Visual Basic 中。|
|[元組](tuples.md)|描述的 tuple 型別，分組組、 三合一、 quadruples，等任何類型的相關聯的值所組成的型別。|
|[選項](options.md)|描述選項類型，可能會有值，或可以是空的類型。|
|[清單](lists.md)|描述清單，也就是已排序、 不可變的系列的項目所有相同的型別。|
|[陣列](arrays.md)|描述陣列，且已排序集合的可變動的項目相同的型別，會佔用連續記憶體區塊，並有固定的大小。|
|[序列](sequences.md)|描述序列類型、 表示邏輯的一連串的值;必要時，才需要計算個別的值。|
|[記錄](records.md)|描述記錄類型，而具名值的小型彙總。|
|[差別聯集](discriminated-unions.md)|描述差別聯集類型，而類型，其值可以是任何一種可能型別的組。|
|[函式](functions/index.md)|描述函式值。|
|[類別](classes.md)|描述類別類型，對應至.NET 參考類型的物件類型。 類別類型可以包含成員、 屬性、 實作的介面和基底型別。|
|[結構](structures.md)|描述`struct`類型，對應至.NET 實值類型的物件類型。 `struct`類型通常代表小型的彙總的資料。|
|[介面](interfaces.md)|描述介面類型，也就是代表一組提供特定功能，但不包含任何資料成員的類型。 介面型別必須實作才能發揮作用的物件類型。|
|[委派](delegates.md)|說明委派的型別，表示為物件的函式。|
|[列舉](enumerations.md)|描述列舉型別，其值屬於一組具名的值。|
|[屬性](attributes.md)|描述用來指定另一種類型的中繼資料的屬性。|
|[例外狀況類型](exception-handling/exception-types.md)|描述例外狀況，指定錯誤的資訊。|
