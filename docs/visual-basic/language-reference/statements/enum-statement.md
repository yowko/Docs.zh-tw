---
title: End 陳述式
ms.date: 07/20/2015
f1_keywords:
- vb.Enum
helpviewer_keywords:
- enumerated constants [Visual Basic]
- Enum statement [Visual Basic]
- Private keyword [Visual Basic], Enum statements
- Public keyword [Visual Basic], in Enum statement
- variables [Visual Basic], enumeration
- constants [Visual Basic], enumerated
ms.assetid: a45e51f1-65ff-48e1-bf32-79130f137377
ms.openlocfilehash: 976cc68d67c69ec86918962ab2dd3406d15aed9a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404728"
---
# <a name="enum-statement-visual-basic"></a>Enum 陳述式 (Visual Basic)

宣告列舉，並定義其成員的值。

## <a name="syntax"></a>語法

```vb
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]
Enum enumerationname [ As datatype ]
   memberlist
End Enum
```

## <a name="parts"></a>組件

- `attributelist`

  選擇性。 套用至此列舉的屬性清單。 您必須將[屬性清單](attribute-list.md)放在角括弧（" `<` " 和 " `>` "）中。

  <xref:System.FlagsAttribute>屬性會指出列舉實例的值可以包含多個列舉成員，而且每個成員都代表列舉值中的位欄位。

- `accessmodifier`

  選擇性。 指定哪些程式碼可以存取此列舉。 可以是下列其中一項：

  - [公開](../modifiers/public.md)

  - [免受](../modifiers/protected.md)

  - [給](../modifiers/friend.md)

  - [私用](../modifiers/private.md)

  - [Protected Friend](../modifiers/protected-friend.md)

  - [私用保護](../modifiers/private-protected.md)

- `Shadows`

  選擇性。 指定在基類中，這個列舉會重新宣告並隱藏名稱相同的程式設計項目，或一組多載元素。 您只能在列舉本身（而不是其任何成員）上指定[Shadows](../modifiers/shadows.md) 。

- `enumerationname`

  必要。 列舉的名稱。 如需有效名稱的資訊，請參閱宣告的[元素名稱](../../programming-guide/language-features/declared-elements/declared-element-names.md)。

- `datatype`

  選擇性。 列舉及其所有成員的資料類型。

- `memberlist`

  必要。 在此語句中宣告的成員常數清單。 多個成員會出現在個別的源程式碼上。

  每個 `member` 都有下列語法和部分：`[<attribute list>] member name [ = initializer ]`

  |部分|描述|
  |---|---|
  |`membername`|必要。 這個成員的名稱。|
  |`initializer`|選擇性。 在編譯時期評估並指派給這個成員的運算式。|

- `End` `Enum`

  終止 `Enum` 區塊。

## <a name="remarks"></a>備註

如果您有一組不變的值是以邏輯方式相互關聯，您可以在列舉中將它們定義在一起。 這會為列舉及其成員提供有意義的名稱，這比它們的值更容易記住。 然後您可以在程式碼中的許多地方使用列舉成員。

使用列舉的優點包括下列各項：

- 減少因轉置或錯誤的數位而造成的錯誤。

- 可讓您在未來輕鬆變更值。

- 可讓程式碼更容易閱讀，這表示不太可能會引進錯誤。

- 確保向前相容性。 如果您使用列舉，當未來有人變更對應至成員名稱的值時，您的程式碼較不可能失敗。

列舉具有名稱、基礎資料類型和一組成員。 每個成員都代表一個常數。

在任何程式之外的類別、結構、模組或介面層級宣告的列舉是*成員列舉*。 它是宣告它的類別、結構、模組或介面的成員。

成員列舉可以從其類別、結構、模組或介面中的任何位置存取。 類別、結構或模組之外的程式碼必須使用該類別、結構或模組的名稱來限定成員列舉的名稱。 您可以藉由將[Imports](imports-statement-net-namespace-and-type.md)語句加入至原始程式檔，來避免需要使用完整名稱。

在命名空間層級（在任何類別、結構、模組或介面外）宣告的列舉，是其出現所在之命名空間的成員。

列舉的宣告*內容*必須是原始程式檔、命名空間、類別、結構、模組或介面，而且不能是程式。 如需詳細資訊，請參閱[宣告內容和預設存取層級](declaration-contexts-and-default-access-levels.md)。

您可以將屬性套用至整個列舉，但不能個別套用到其成員。 屬性會將資訊提供給元件的中繼資料。

## <a name="data-type"></a>資料類型

`Enum`語句可以宣告列舉的資料類型。 每個成員都會採用列舉的資料類型。 您可以指定 `Byte` 、 `Integer` 、 `Long` 、 `SByte` 、 `Short` 、 `UInteger` 、 `ULong` 或 `UShort` 。

如果您未指定 `datatype` 列舉的，每個成員都會採用其的資料類型 `initializer` 。 如果您同時指定 `datatype` 和 `initializer` ，則的資料類型 `initializer` 必須可轉換為 `datatype` 。 如果 `datatype` 和 `initializer` 都不存在，資料類型會預設為 `Integer` 。

## <a name="initializing-members"></a>初始化成員

`Enum`語句可以初始化中選取之成員的內容 `memberlist` 。 您可以使用 `initializer` 來提供要指派給成員的運算式。

如果您沒有 `initializer` 為成員指定，Visual Basic 會將它初始化為零（如果它是中的第 `member` 一個 `memberlist` ），或設為大於前面緊接的一個值 `member` 。

在每個中提供的運算式 `initializer` 可以是常值的任何組合、已定義的其他常數，以及已定義的列舉成員，包括此列舉的上一個成員。 您可以使用算術和邏輯運算子來結合這類元素。

您不能在中使用變數或函數 `initializer` 。 不過，您可以使用轉換關鍵字（例如 `CByte` 和） `CShort` 。 `AscW`如果您以常數或引數呼叫它，您也可以使用 `String` `Char` ，因為它可以在編譯時期進行評估。

列舉不能有浮點值。 如果將浮點值指派給成員，並 `Option Strict` 將設定為 on，就會發生編譯器錯誤。 如果 `Option Strict` 已關閉，此值會自動轉換成 `Enum` 類型。

如果成員的值超過基礎資料類型允許的範圍，或是您將任何成員初始化為基礎資料類型所允許的最大值，則編譯器會報告錯誤。

## <a name="modifiers"></a>修飾詞

類別、結構、模組和介面成員列舉預設為公用存取。 您可以使用存取修飾詞來調整其存取層級。 命名空間成員列舉預設為 friend 存取。 您可以將其存取層級調整為 [公用]，而不是 [私人] 或 [受保護]。 如需詳細資訊，請參閱[Visual Basic 中的存取層級](../../programming-guide/language-features/declared-elements/access-levels.md)。

所有列舉成員都具有公用存取權，而且您不能在其上使用任何存取修飾詞。 不過，如果列舉本身具有更受限制的存取層級，則會優先使用指定的列舉存取層級。

根據預設，所有列舉都是類型，而其欄位是常數。 因此，在宣告 `Shared` `Static` `ReadOnly` 列舉或其成員時，不能使用、和關鍵字。

## <a name="assigning-multiple-values"></a>指派多個值

列舉通常代表互斥的值。 藉由在宣告 <xref:System.FlagsAttribute> 中包含屬性 `Enum` ，您可以改為將多個值指派給列舉的實例。 <xref:System.FlagsAttribute>屬性指定將列舉視為位欄位，也就是一組旗標。 這些稱為*位*列舉。

當您使用屬性宣告列舉時 <xref:System.FlagsAttribute> ，我們建議您使用2的乘冪（也就是1、2、4、8、16等等）來取得這些值。 我們也建議 "None" 是值為0的成員名稱。 如需其他指導方針，請參閱 <xref:System.FlagsAttribute> 和 <xref:System.Enum> 。

## <a name="example"></a>範例

下列範例顯示如何使用 `Enum` 陳述式。 請注意，成員稱為 `EggSizeEnum.Medium` ，而不是 `Medium` 。

[!code-vb[VbEnumsTask#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#41)]

## <a name="example"></a>範例

下列範例中的方法是在類別之外 `Egg` 。 因此， `EggSizeEnum` 會完整限定為 `Egg.EggSizeEnum` 。

[!code-vb[VbEnumsTask#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#42)]

## <a name="example"></a>範例

下列範例會使用 `Enum` 語句來定義一組相關的已命名常數值。 在此情況下，這些值是您可能選擇用來設計資料庫之資料輸入表單的色彩。

[!code-vb[VbEnumsTask#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#30)]

## <a name="example"></a>範例

下列範例會顯示包含正數和負數的值。

[!code-vb[VbEnumsTask#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#31)]

## <a name="example"></a>範例

在下列範例中， `As` 子句是用來指定 `datatype` 列舉的。

[!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]

## <a name="example"></a>範例

下列範例顯示如何使用位列舉。 可以將多個值指派給位列舉的實例。 宣告 `Enum` 包含 <xref:System.FlagsAttribute> 屬性，這表示可以將列舉視為一組旗標。

[!code-vb[VbEnumsTask#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#61)]

## <a name="example"></a>範例

下列範例會逐一查看列舉。 它會使用 <xref:System.Enum.GetNames%2A> 方法來抓取列舉中的成員名稱陣列，並 <xref:System.Enum.GetValues%2A> 取得成員值的陣列。

[!code-vb[VbEnumsTask#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#51)]

## <a name="see-also"></a>另請參閱

- <xref:System.Enum>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [Const 陳述式](const-statement.md)
- [Dim 陳述式](dim-statement.md)
- [隱含和明確轉換](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Type Conversion Functions](../functions/type-conversion-functions.md)
- [常數和列舉](../constants-and-enumerations.md)
