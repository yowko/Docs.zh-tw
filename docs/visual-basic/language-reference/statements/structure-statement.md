---
title: Structure 語句（Visual Basic）
ms.date: 05/12/2018
f1_keywords:
- vb.Structure
- Structure
helpviewer_keywords:
- user-defined types [Visual Basic], Structure statement
- compound data types [Visual Basic]
- Structure keyword [Visual Basic]
- Structure statement [Visual Basic]
- UDT (user-defined types)
- types [Visual Basic], user-defined
ms.assetid: 9bd1deea-2a89-4cdc-812c-6dcbb947c391
ms.openlocfilehash: ac128e257269ca301400bd8b294539d1ec836cab
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2019
ms.locfileid: "73038624"
---
# <a name="structure-statement"></a>Structure 陳述式

宣告結構的名稱，並引進結構所組成之變數、屬性、事件和程式的定義。

## <a name="syntax"></a>語法

```vb
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Partial ] _
Structure name [ ( Of typelist ) ]
    [ Implements interfacenames ]
    [ datamemberdeclarations ]
    [ methodmemberdeclarations ]
End Structure
```

## <a name="parts"></a>組件

|詞彙|定義|
|---|---|
|`attributelist`|選擇項。 請參閱[屬性清單](attribute-list.md)。|
|`accessmodifier`|選擇項。 可以是下列其中一項：<br /><br /> -   [公用](../modifiers/public.md)<br />-   [保護](../modifiers/protected.md)<br />-   [Friend](../modifiers/friend.md)<br />-   [私](../modifiers/private.md)用<br />- [受保護的 Friend](../modifiers/protected-friend.md)<br/>- [私用保護](../modifiers/private-protected.md) <br /><br /> 請參閱 [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md)。|
|`Shadows`|選擇項。 請參閱[Shadows](../modifiers/shadows.md)。|
|`Partial`|選擇項。 表示結構的部分定義。 請參閱[部分](../modifiers/partial.md)。|
|`name`|必要項。 這個結構的名稱。 請參閱 [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)。|
|`Of`|選擇項。 指定這是泛型結構。|
|`typelist`|如果您使用 of 關鍵字，則[為必要項](of-clause.md)。 此結構的類型參數清單。 請參閱[類型清單](type-list.md)。|
|`Implements`|選擇項。 表示此結構會執行一或多個介面的成員。 請參閱[Implements 語句](implements-statement.md)。|
|`interfacenames`|如果您使用 `Implements` 語句，則為必要。 這個結構所實作為介面的名稱。|
|`datamemberdeclarations`|必要項。 零或多個 `Const`、`Dim`、`Enum` 或 `Event` 語句，宣告結構的*資料成員*。|
|`methodmemberdeclarations`|選擇項。 零或多個 `Function`、`Operator`、`Property` 或 `Sub` 程式的宣告，做為結構的*方法成員*。|
|`End Structure`|必要項。 終止 `Structure` 定義。|

## <a name="remarks"></a>備註

`Structure` 語句會定義您可以自訂的複合實數值型別。 「*結構*」（structure）是舊版 Visual Basic 的使用者定義型別（UDT）的一般化。 如需詳細資訊，請參閱[結構](../../programming-guide/language-features/data-types/structures.md)。

結構支援許多與類別相同的功能。 例如，結構可以有屬性和程式，它們可以實作為介面，而且可以有參數化的函式。 不過，繼承、宣告和使用等領域中的結構與類別之間有顯著的差異。 此外，類別是參考型別，而結構是實數值型別。 如需詳細資訊，請參閱[結構和類別](../../programming-guide/language-features/data-types/structures-and-classes.md)。

您只能在命名空間或模組層級使用 `Structure`。 這表示結構的宣告*內容*必須是原始程式檔、命名空間、類別、結構、模組或介面，而且不能是程式或區塊。 如需詳細資訊，請參閱[宣告內容和預設存取層級](declaration-contexts-and-default-access-levels.md)。

結構預設為[Friend](../modifiers/friend.md)存取。 您可以使用存取修飾詞來調整其存取層級。 如需詳細資訊，請參閱[Visual Basic 中的存取層級](../../programming-guide/language-features/declared-elements/access-levels.md)。

## <a name="rules"></a>規則

- **嵌入.** 您可以在另一個中定義一個結構。 外部結構稱為「*包含結構*」，而內部結構稱為「*嵌套結構*」。 但是，您無法透過包含結構存取嵌套結構的成員。 相反地，您必須宣告嵌套結構之資料類型的變數。

- **成員宣告。** 您必須宣告結構的每個成員。 結構成員無法[受到保護](../modifiers/protected.md)或 `Protected Friend`，因為沒有任何可繼承自結構的。 不過，結構本身可以 `Protected` 或 `Protected Friend`。
  
     您可以在結構中宣告零個或多個非共用變數，或非共用、非自訂的事件。 您不能只有常數、屬性和程式，即使其中一些是非共用的。

- **初始.** 您無法初始化結構之任何非共用資料成員的值，做為其宣告的一部分。 您必須在結構上使用參數化的函式來初始化這類資料成員，或是在建立結構的實例之後，將值指派給成員。

- **繼承**： 結構無法繼承自所有結構所繼承之 <xref:System.ValueType> 以外的任何類型。 特別是，一個結構無法繼承自另一個。

     您不能在結構定義中使用[Inherits 語句](inherits-statement.md)，甚至可以指定 <xref:System.ValueType>。

- **實作.** 如果結構使用[Implements 語句](implements-statement.md)，您就必須執行您在 `interfacenames` 中指定的每個介面所定義的每個成員。

- **Default 屬性。** 結構最多可以使用[預設](../modifiers/default.md)的修飾詞，指定一個屬性做為其*預設屬性*。 如需詳細資訊，請參閱[Default](../modifiers/default.md)。

## <a name="behavior"></a>行為

- **存取層級。** 在結構中，您可以使用自己的存取層級來宣告每個成員。 所有結構成員都預設為[公用](../modifiers/public.md)存取。 請注意，如果結構本身有限制較多的存取層級，這會自動限制其成員的存取權，即使您使用存取修飾詞來調整其存取層級也一樣。

- **範圍.** 結構會在其包含的命名空間、類別、結構或模組的範圍內。

     每個結構成員的範圍都是整個結構。

- **期.** 結構本身不會有存留期。 相反地，該結構的每個實例都有與其他所有實例無關的存留期。

     實例的存留期會在[新的 Operator](../operators/new-operator.md)子句建立時開始。 它會在保留該變數的存留期結束時結束。

     您無法擴充結構實例的存留期。 對靜態結構功能的近似值是由模組提供。 如需詳細資訊，請參閱[Module 語句](module-statement.md)。

     結構成員的存留期取決於宣告的方式和位置。 如需詳細資訊，請參閱[Class 語句](class-statement.md)中的「存留期」。

- **加.** 結構外的程式碼必須使用該結構的名稱來限定成員名稱。

     如果嵌套結構內的程式碼會對程式設計項目進行不合格的參考，Visual Basic 會先在嵌套結構中搜尋該專案，然後在其包含結構中，依此類推，直到最外層的包含專案。 如需詳細資訊，請參閱 [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)。

- **記憶體耗用量。** 如同所有複合資料型別，您無法安全地計算結構的總記憶體耗用量，方法是將其成員的名義儲存體配置相加。 此外，您無法安全地假設記憶體中的儲存順序與您的宣告順序相同。 如果您需要控制結構的儲存配置，您可以將 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 屬性套用至 `Structure` 語句。

## <a name="example"></a>範例

下列範例會使用 `Structure` 語句來定義員工的一組相關資料。 它會顯示 `Public`、`Friend` 和 `Private` 成員的使用，以反映資料項目的敏感度。 它也會顯示程式、屬性和事件成員。

[!code-vb[VbVbalrStatements#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#57)]

如需如何使用 `Structure`的詳細資訊，請參閱[結構變數](../../programming-guide/language-features/data-types/structure-variables.md)。

## <a name="see-also"></a>請參閱

- [Class 陳述式](class-statement.md)
- [Interface 陳述式](interface-statement.md)
- [Module 陳述式](module-statement.md)
- [Dim 陳述式](dim-statement.md)
- [Const 陳述式](const-statement.md)
- [Enum 陳述式](enum-statement.md)
- [Event 陳述式](event-statement.md)
- [Operator 陳述式](operator-statement.md)
- [Property 陳述式](property-statement.md)
- [結構和類別](../../programming-guide/language-features/data-types/structures-and-classes.md)
