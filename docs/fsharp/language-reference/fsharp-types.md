---
title: F# 類型
description: '深入了解 F # 和 F # 型別如何命名及描述中使用的類型。'
ms.date: 05/16/2016
ms.openlocfilehash: bdbb89dc751970ac31fe102df009f0bff6388e52
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565578"
---
# <a name="f-types"></a>F# 類型

本主題描述 F # 和 F # 型別如何命名及描述中使用的類型。


## <a name="summary-of-f-types"></a>F # 類型的摘要
某些類型被視為*基本型別*，例如布林類型`bool`和包含的位元組和字元類型中的各種大小的整數和浮點點類型。 這些類型詳述於[基本型別](primitive-types.md)。

其他語言內建的型別包含元組、 清單、 陣列、 時序、 記錄和差別等位。 如果您使用其他.NET 語言的經驗，而且不了解 F #，您應該閱讀主題的每個類型。 中包含這些類型的相關資訊的連結[相關主題](https://msdn.microsoft.com/library/#rel)本主題一節。 這些 F #-特定類型支援功能的程式設計語言通用的程式設計樣式。 許多這些型別有關聯的 F # 程式庫中支援這些型別上的一般作業的模組。

函式的型別包含的參數類型的相關資訊，並傳回型別。

.NET Framework 是物件類型、 介面類型、 委派類型，等等的來源。 就如同您可以在任何其他.NET 語言中，您可以定義您自己的物件類型。

此外，F # 程式碼可以在其中定義了名為的別名*類型縮寫*，屬於類型的替代名稱。 當型別可能會在未來變更，而且您想要避免變更的程式碼的類型而定，您可以使用類型縮寫。 或者，您可以使用類型縮寫成的型別，可讓您更輕鬆地閱讀並了解的程式碼的好記名稱。

F # 提供有用的集合型別與記住的功能性程式設計所設計。 使用這些集合類型，可協助您撰寫多運作樣式中的程式碼。 如需詳細資訊，請參閱[F # 集合類型](fsharp-collection-types.md)。


## <a name="syntax-for-types"></a>類型的語法
在 F # 程式碼，您經常會有輸出類型的名稱。 每個類型具有語法形式，而且您使用這些型別附註、 抽象方法宣告中，委派宣告、 簽章和其他建構中的語法形式。 每當您宣告中，解譯器的新程式建構，解譯器會列印其類型的建構和語法的名稱。 這個語法可能只是使用者定義類型的識別項或內建識別碼這類與`int`或`string`，但更複雜的類型，則語法就是更複雜。

下表顯示 F # 類型的類型語法的層面。



|類型|類型語法|範例|
|----|-----------|--------|
|基本類型|*type-name*|`int`<br /><br />`float`<br /><br />`string`|
|彙總類型 （類別、 結構、 等位、 記錄、 列舉，等等）|*type-name*|`System.DateTime`<br /><br />`Color`|
|類型縮寫|*類型縮寫名稱*|`bigint`|
|完整的類型|*namespaces.type 名稱*<br /><br />或<br /><br />*modules.type 名稱*<br /><br />或<br /><br />*namespaces.modules.type 名稱*|`System.IO.StreamWriter`|
|array|*型別名稱*[] 或<br /><br />*型別名稱*陣列|`int[]`<br /><br />`array<int>`<br /><br />`int array`|
|二維陣列|*型別名稱*[、]|`int[,]`<br /><br />`float[,]`|
|三維陣列|*型別名稱*[、]|`float[,,]`|
|tuple|*型別 name1* &#42; *類型 name2* ...|例如，`(1,'b',3)`類型 `int * char * int`|
|Generic Type - 泛型類型|*型別參數**泛型型別名稱*<br /><br />或<br /><br />*泛型型別名稱*&lt;*型別參數清單*&gt;|`'a list`<br /><br />`list<'a>`<br /><br />`Dictionary<'key, 'value>`|
|建構的型別 （已提供的特定型別引數的泛型類型）|*型別引數**泛型型別名稱*<br /><br />或<br /><br />*泛型型別名稱*&lt;*型別引數清單*&gt;|`int option`<br /><br />`string list`<br /><br />`int ref`<br /><br />`option<int>`<br /><br />`list<string>`<br /><br />`ref<int>`<br /><br />`Dictionary<int, string>`|
|具有單一參數的函式類型|*參數 type1*  - &gt; *傳回型別*|使用的函式`int`並傳回`string`類型 `int -> string`|
|具有多個參數的函式類型|*參數 type1*  - &gt; *參數 type2*  - &gt; ...-&gt; *傳回型別*|使用的函式`int`和`float`並傳回`string`類型 `int -> float -> string`|
|做為參數的較高順序函式|(*函式類型*)|`List.map` 具有型別 `('a -> 'b) -> 'a list -> 'b list`|
|Delegate - 委派|委派的*函式類型*|`delegate of unit -> int`|
|彈性類型|#*型別名稱*|`#System.Windows.Forms.Control`<br /><br />`#seq<int>`|

## <a name="related-topics"></a>相關主題


|主題|描述|
|-----|-----------|
|[基本類型](primitive-types.md)|說明內建的簡單類型，例如整數類資料類型的布林類型和字元類型。|
|[單位類型](unit-type.md)|描述`unit`類型、 類型具有一個值，且會以 （）; 相當於`void`在 C# 和`Nothing`在 Visual Basic 中。|
|[元組](tuples.md)|描述元組型別，分組組、 三合一、 quadruples，以及其他任何類型的相關聯的值所組成的型別。|
|[選項](options.md)|描述的選項類型，可以有一個值，或者可以是空的類型。|
|[清單](lists.md)|描述清單，也就是已排序、 不可變的序列的項目全為相同的類型。|
|[陣列](arrays.md)|描述已排序集合的可變動的項目相同的型別，佔用連續記憶體區塊，而且為固定大小的陣列。|
|[序列](sequences.md)|描述時序類型，代表邏輯的一連串的值;必要時，才需要計算個別值。|
|[記錄](records.md)|描述記錄類型，以小的彙總的具名值。|
|[差別聯集](discriminated-unions.md)|描述差別等位型別，其值可以是任何一個的一組可能的型別類型。|
|[函式](functions/index.md)|描述函式值。|
|[類別](classes.md)|描述類別類型，對應至.NET 參考類型的物件類型。 類別類型可以包含成員、 屬性、 實作的介面和基底型別。|
|[結構](structures.md)|描述`struct`類型、 對應至.NET 實值類型的物件類型。 `struct`類型通常代表小型的彙總的資料。|
|[介面](interfaces.md)|描述介面型別，也就是代表一組成員，提供特定功能，但會包含任何資料類型。 介面型別必須實作才能發揮作用的物件類型。|
|[委派](delegates.md)|描述委派類型，表示為物件的函式。|
|[列舉](enumerations.md)|描述列舉型別，其值屬於一組具名的值。|
|[屬性](attributes.md)|說明用來指定另一個類型的中繼資料的屬性。|
|[例外狀況類型](exception-handling/exception-types.md)|描述例外狀況，指定錯誤的資訊。|
