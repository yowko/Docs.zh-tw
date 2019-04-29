---
title: Enum 陳述式 (Visual Basic)
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
ms.openlocfilehash: fa97a374d4570e014222bf44844271b3394453da
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638125"
---
# <a name="enum-statement-visual-basic"></a>Enum 陳述式 (Visual Basic)

宣告列舉，並定義其成員的值。

## <a name="syntax"></a>語法

```
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]
Enum enumerationname [ As datatype ]
   memberlist
End Enum
```

## <a name="parts"></a>組件

- `attributelist`

  選擇性。 這個列舉型別所套用的屬性清單。 您必須將括[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)角括弧 ("`<`"和"`>`")。

  <xref:System.FlagsAttribute>屬性表示列舉型別的執行個體的值可以包含多個列舉成員，而且每個成員，代表在列舉值的位元欄位。

- `accessmodifier`

  選擇性。 指定哪些程式碼可以存取此列舉型別。 可以是下列其中一項：

  - [Public](../../../visual-basic/language-reference/modifiers/public.md)

  - [Protected](../../../visual-basic/language-reference/modifiers/protected.md)

  - [Friend](../../../visual-basic/language-reference/modifiers/friend.md)

  - [Private](../../../visual-basic/language-reference/modifiers/private.md)

  - [Protected Friend](../../language-reference/modifiers/protected-friend.md)

  - [Private Protected](../../language-reference/modifiers/private-protected.md)

- `Shadows`

  選擇性。 指定此列舉型別重新宣告，並隱藏的名稱相同的程式設計項目或一組多載的項目，基底類別中。 您可以指定[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)只在列舉型別本身，而不是在它的任何成員。

- `enumerationname`

  必要項。 列舉型別的名稱。 如需有效的名稱，請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。

- `datatype`

  選擇性。 列舉型別及其所有成員的資料型別。

- `memberlist`

  必要項。 此陳述式所宣告的成員常數的清單。 多個成員會出現在個別的原始程式碼行。

  每個`member`具有下列語法和組成部分： `[<attribute list>] member name [ = initializer ]`

  |組件|描述|
  |---|---|
  |`membername`|必要項。 這個成員的名稱。|
  |`initializer`|選擇性。 在編譯時期評估，以及指派給這個成員的運算式。|

- `End` `Enum`

  終止 `Enum` 區塊。

## <a name="remarks"></a>備註

如果您有一組彼此邏輯相關的不變值時，可以在列舉型別一起定義它們。 這會提供有意義的名稱，列舉型別和其成員，也就是容易記住它們的值。 然後，您可以使用在許多地方列舉型別成員在您的程式碼。

使用列舉的優點包括：

- 減少調換，或輸入數字的錯誤所造成的錯誤。

- 可讓您輕鬆地在未來變更的值。

- 讓程式碼更方便閱讀，這表示它不太可能會導入錯誤。

- 可確保往後相容性。 如果您使用列舉型別時，您的程式碼是比較不可能失敗，如果有人在未來變更為成員名稱的對應值。

列舉型別具有名稱、 基礎資料類型和一組的成員。 每一個成員代表的常數。

在類別、 結構、 模組或介面層級，任何程序中，外部宣告的列舉型別是*成員的列舉型別*。 它是類別、 結構、 模組或介面會宣告它的成員。

成員的列舉型別可以從任何位置內存取他們的類別、 結構、 模組或介面。 程式碼類別之外，結構或模組必須限定成員列舉型別的名稱，該類別、 結構或模組的名稱。 您可以避免需要使用完整限定的名稱加上[匯入](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)原始程式檔陳述式。

在命名空間層級，任何類別、 結構、 模組或介面外部宣告的列舉型別是在出現的命名空間的成員。

*宣告內容*列舉型別必須是原始程式檔、 命名空間、 類別、 結構、 模組或介面，並不是程序。 如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。

您可以將屬性套用至整個列舉型別而非其成員個別。 屬性會提供資訊給組件的中繼資料。

## <a name="data-type"></a>資料類型

`Enum`陳述式可以宣告列舉的資料類型。 每個成員會在列舉的資料類型。 您可以指定`Byte`， `Integer`， `Long`， `SByte`， `Short`， `UInteger`， `ULong`，或`UShort`。

如果您未指定`datatype`列舉中，每個成員都會採用的資料型別其`initializer`。 如果您同時指定`datatype`並`initializer`的資料類型`initializer`必須可轉換成`datatype`。 如果既未`datatype`也`initializer`已存在，將資料類型會預設為`Integer`。

## <a name="initializing-members"></a>初始化成員

`Enum`陳述式可以初始化中的所選成員的內容`memberlist`。 您使用`initializer`提供要指派給成員的運算式。

如果您未指定`initializer`成員，Visual Basic 將它初始化為零 (如果它是第一個`member`中`memberlist`)，或值比前一大`member`。

在每個所提供的運算式`initializer`可以是常值、 已定義，其他常數和列舉成員已定義，包括先前的成員，這個列舉型別的任何組合。 您可以使用算術和邏輯運算子來結合這類項目。

您無法使用變數或函式中的`initializer`。 不過，您可以使用轉換關鍵字這類`CByte`和`CShort`。 您也可以使用`AscW`如果您呼叫它具有常數`String`或`Char`引數，因為，可以在編譯時期評估。

列舉型別不能有浮點值。 如果將成員指派為浮點數值和`Option Strict`設定為 on，就會發生編譯器錯誤。 如果`Option Strict`已關閉，值會自動轉換為`Enum`型別。

如果成員的值超過允許的範圍為基礎的資料類型，或如果您初始化任何成員為基礎的資料類型所允許的最大值時，編譯器會回報錯誤。

## <a name="modifiers"></a>修飾詞

類別、 結構、 模組和介面成員列舉型別的預設值為公用存取。 您可以調整它們的存取層級，使用存取修飾詞。 命名空間成員列舉型別預設為 friend 存取權限。 您可以調整其存取層級 public，但不是屬於私用或受保護。 如需詳細資訊，請參閱 <<c0> [ 存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。

所有的列舉型別成員具有公用存取，而且您無法使用任何存取修飾詞在其上。 不過，如果列舉型別本身具有更具限制性的存取層級，指定的列舉存取層級會優先。

根據預設，所有列舉都是型別，而且其欄位都是常數。 因此`Shared`， `Static`，和`ReadOnly`宣告列舉型別或其成員時，就無法使用關鍵字。

## <a name="assigning-multiple-values"></a>指派多個值

列舉型別通常代表互斥的值。 加<xref:System.FlagsAttribute>屬性中`Enum`宣告中，您可以改為將指派多個值給列舉型別的執行個體。 <xref:System.FlagsAttribute>屬性會指定列舉型別視為位元欄位，也就是一組旗標。 這些稱為*位元*列舉型別。

當您使用宣告列舉<xref:System.FlagsAttribute>屬性，我們建議您使用 2，可為、 1、 2、 4、 8、 16，並依此類推的次方的值。 我們也建議 「 無 」 是的成員，其值為 0 的名稱。 如需其他指導方針，請參閱<xref:System.FlagsAttribute>和<xref:System.Enum>。

## <a name="example"></a>範例

下列範例顯示如何使用 `Enum` 陳述式。 請注意，成員指`EggSizeEnum.Medium`，而不是`Medium`。

[!code-vb[VbEnumsTask#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#41)]

## <a name="example"></a>範例

下列範例中的方法將會超出`Egg`類別。 因此，`EggSizeEnum`完整限定為`Egg.EggSizeEnum`。

[!code-vb[VbEnumsTask#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#42)]

## <a name="example"></a>範例

下列範例會使用`Enum`陳述式來定義一組相關的具名常數的值。 在此情況下，值會是您可能會選擇設計資料庫的資料輸入表單的色彩。

[!code-vb[VbEnumsTask#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#30)]

## <a name="example"></a>範例

下列範例顯示包含正數和負數數字的值。

[!code-vb[VbEnumsTask#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#31)]

## <a name="example"></a>範例

在下列範例中，`As`子句來指定`datatype`的列舉型別。

[!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]

## <a name="example"></a>範例

下列範例示範如何使用的位元列舉。 多個值可以指派給位元的列舉型別的執行個體。 `Enum`宣告包含<xref:System.FlagsAttribute>屬性，表示列舉型別，可以視為一組旗標。

[!code-vb[VbEnumsTask#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#61)]

## <a name="example"></a>範例

下列範例會逐一列舉型別。 它會使用<xref:System.Enum.GetNames%2A>方法來擷取列舉的成員名稱的陣列和<xref:System.Enum.GetValues%2A>擷取成員值的陣列。

[!code-vb[VbEnumsTask#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#51)]

## <a name="see-also"></a>另請參閱

- <xref:System.Enum>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [Const 陳述式](../../../visual-basic/language-reference/statements/const-statement.md)
- [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)
- [隱含和明確轉換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [常數和列舉](../../../visual-basic/language-reference/constants-and-enumerations.md)
