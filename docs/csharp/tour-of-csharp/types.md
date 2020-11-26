---
title: 定義類型及其成員-C 的教學課程#
description: '程式的建立要素為類型。 瞭解如何在 c # 中建立類別、結構、介面等等。'
ms.date: 08/06/2020
ms.openlocfilehash: efd353fe8c1e6a57952bcb2586a05ad38ecd52b9
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "88559111"
---
# <a name="types-and-members"></a>類型和成員

## <a name="classes-and-objects"></a>類別與物件

*類別* 是 c # 類型中最基本的一種。 類別是以單一單位結合狀態 (欄位) 和動作 (方法及其他函式成員) 的資料結構。 類別會提供類別 *實例* 的定義，也稱為 *物件*。 類別支援「繼承」和「多型」，這些是可供「衍生類別」將「基底類別」延伸及特製化的機制。

建立新類別時，是使用類別宣告來建立。 類別宣告的開頭是標頭。 標頭會指定：

- 類別的屬性和修飾詞
- 類別的名稱
- 從 [基類](#base-classes) 繼承時，基類 () 
- 類別所執行的介面。

此標頭後面會接著類別主體，此主體是由在 `{` 與 `}` 分隔符號之間撰寫的成員宣告清單所組成。

下列程式碼顯示名為的簡單類別的宣告 `Point` ：

:::code language="csharp" source="./snippets/shared/Types.cs" ID="PointClass":::

建立類別執行個體時，是使用 `new` 運算子來建立，此運算子會為新執行個體配置記憶體、叫用建構函式來將執行個體初始化，然後傳回對執行個體的參考。 下列語句會建立兩個 `Point` 物件，並在兩個變數中儲存這些物件的參考：

:::code language="csharp" source="./snippets/shared/Types.cs" ID="CreatePoints":::

當物件不再可供存取時，系統會自動回收物件所佔用的記憶體。 不需要也不可能在 c # 中明確解除配置物件。

### <a name="type-parameters"></a>型別參數

泛型類別會定義 [ * **類型參數** _](../programming-guide/generics/index.md)。 型別參數是以角括弧括住的型別參數名稱清單。 類型參數會在類別名稱之後。 接著，就可以在類別宣告的主體中使用這些型別參數，來定義類別的成員。 在下列範例中，`Pair` 的型別參數是 `TFirst` 和 `TSecond`：

:::code language="csharp" source="./snippets/shared/Types.cs" ID="DefinePairClass":::

宣告為採用型別參數的類別型別稱為 _generic 類別型別 *。 結構、介面和委派類型也可以是泛型。
使用泛型類別時，必須為每個型別參數提供型別參數：

:::code language="csharp" source="./snippets/shared/Types.cs" ID="CreatePairObject":::

泛型型別若已有提供的型別參數 (如上述的 `Pair<int,string>`)，即稱為「建構的型別」。

### <a name="base-classes"></a>基底類別

類別宣告可指定基類。 請在類別名稱和類型參數後面加上冒號和基類的名稱。 省略基底類別規格即等同於衍生自類型 `object`。 在下列範例中，的基類 `Point3D` 為 `Point` 。 在第一個範例中，的基類 `Point` 為 `object` ：

:::code language="csharp" source="./snippets/shared/Types.cs" ID="Create3DPoint":::

類別會繼承其基底類別的成員。 繼承表示類別會隱含地包含其基類的所有成員。 類別不會繼承實例和靜態的函式，以及完成項。 衍生類別可以將新成員加入至它所繼承的成員，但無法移除繼承成員的定義。 在上述範例中， `Point3D` 繼承的 `X` 和 `Y` 成員 `Point` ，而每個 `Point3D` 實例都包含三個屬性：、 `X` `Y` 和 `Z` 。

在類別型別到其任何基底類別型別之間都存在著隱含轉換。 類別型別的變數可以參考該類別的實例，或任何衍生類別的實例。 例如，以先前的類別宣告為例，`Point` 型別的變數可以參考 `Point` 或 `Point3D`：

:::code language="csharp" source="./snippets/shared/Types.cs" ID="ImplicitCastToBase":::

## <a name="structs"></a>結構

類別會定義支援繼承和多型的類型。 它們可讓您根據衍生類別的階層來建立複雜的行為。 相較之下， [ * **結構** _](../language-reference/builtin-types/struct.md)類型是較簡單的類型，其主要用途是儲存資料值。 結構無法宣告基底類型;它們隱含地衍生自 <xref:System.ValueType?displayProperty=nameWithType> 。 您無法 `struct` 從類型衍生其他類型 `struct` 。 它們是隱含密封的。

:::code language="csharp" source="./snippets/shared/Types.cs" ID="PointStruct":::

## <a name="interfaces"></a>介面

[_*_介面_*_](../programming-guide/interfaces/index.md)會定義可由類別和結構執行的合約。 介面可以包含方法、屬性、事件和索引子。 介面通常不會提供它所定義之成員的實作為，它只會指定必須由執行介面之類別或結構提供的成員。

介面可能採用 _*_多重繼承_*_。 在下列範例中，介面 `IComboBox` 同時繼承自 `ITextBox` 和 `IListBox`。

:::code language="csharp" source="./snippets/shared/Types.cs" ID="FirstInterfaces":::

類別和結構可以實作多個介面。 在下列範例中，類別 `EditBox` 可以實作 `IControl` 與 `IDataBound` 兩者。

:::code language="csharp" source="./snippets/shared/Types.cs" ID="ImplementInterfaces":::

當類別或結構實作特定介面時，可以將該類別或結構的執行個體隱含地轉換為該介面型別。 例如：

:::code language="csharp" source="./snippets/shared/Types.cs" ID="UseInterfaces":::

## <a name="enums"></a>列舉

[_*_列舉_*_](../language-reference/builtin-types/enum.md)型別會定義一組常數值。 以下宣告 `enum` 定義不同根蔬菜的常數：

:::code language="csharp" source="./snippets/shared/Types.cs" ID="EnumDeclaration":::

您也可以定義 `enum` 要用來組合為旗標的。 下列宣告會宣告四個季節的一組旗標。 可能會套用季節的任何組合，包括 `All` 包含所有季節的值：

:::code language="csharp" source="./snippets/shared/Types.cs" ID="FlagsEnumDeclaration":::

下列範例會顯示上述兩個列舉的宣告：

:::code language="csharp" source="./snippets/shared/Types.cs" ID="UsingEnums":::

## <a name="nullable-types"></a>可為 Null 的型別

任何類型的變數都可以宣告為 _*_不可為 null_*_ 或 _*_可為 null_*_。 可為 null 的變數可以保留額外 `null` 值，表示沒有任何值。 可為 null 的實值型別 (結構或列舉) 由表示 <xref:System.Nullable%601?displayProperty=nameWithType> 。 不可為 null 且可為 Null 的參考型別都是以基礎參考型別表示。 差別是由編譯器所讀取的中繼資料和某些程式庫所表示。 如果可為 null 參考進行取值，而未先檢查其值，則編譯器會提供警告 `null` 。 若為不可為 null 的參考指派了可能的值，編譯器也會提供警告 `null` 。 下列範例會宣告 _*_可為 null 的 int_*_，將它初始化為 `null` 。 然後，它會將值設定為 `5` 。 它示範的概念與 _*_可為 null 的字串_*_ 相同。 如需詳細資訊，請參閱[可為 null](../language-reference/builtin-types/nullable-value-types.md)的實值型別及[可為 null 的參考](../nullable-references.md)

:::code language="csharp" source="./snippets/shared/Types.cs" ID="DeclareNullable":::

## <a name="tuples"></a>Tuple

C # 支援 [_ *_元_* *](../language-reference/builtin-types/value-tuples.md)組，可提供簡潔的語法來群組輕量資料結構中的多個資料元素。 您可以藉由宣告和之間成員的類型和名稱來具現化元組 `(` `)` ，如下列範例所示：

:::code language="csharp" source="./snippets/shared/Types.cs" ID="DeclareTuples":::

元組為具有多個成員的資料結構提供替代方式，而不使用下一篇文章中所述的建立區塊。

>[!div class="step-by-step"]
>[上一個](index.md) 
>[下一步](program-building-blocks.md)
