---
title: Property 語句（Visual Basic）
ms.date: 05/12/2018
f1_keywords:
- vb.PropertySet
- vb.Property
- vb.PropertyGet
helpviewer_keywords:
- Property statement [Visual Basic]
- default modifier
- property procedures [Visual Basic], Property statements
- Property keyword [Visual Basic]
ms.assetid: 3155edaf-8ebd-45c6-9cef-11d5d2dc8d38
ms.openlocfilehash: 2c3e417aad404171a43342dc92773615ec350ef5
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332740"
---
# <a name="property-statement"></a>Property Statement

宣告屬性的名稱，以及用來儲存和取出屬性值的屬性程式。

## <a name="syntax"></a>語法

```vb
[ <attributelist> ] [ Default ] [ accessmodifier ]
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ] [ Iterator ]
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]
    [ <attributelist> ] [ accessmodifier ] Get
        [ statements ]
    End Get
    [ <attributelist> ] [ accessmodifier ] Set ( ByVal value As returntype [, parameterlist ] )
        [ statements ]
    End Set
End Property
- or -
[ <attributelist> ] [ Default ] [ accessmodifier ]
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ]
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]
```

## <a name="parts"></a>組件

- `attributelist`

  選擇性。 套用至這個屬性或 `Get` 或 @no__t 1 程式的屬性清單。 請參閱[屬性清單](attribute-list.md)。

- `Default`

  選擇性。 指定此屬性為其定義所在之類別或結構的預設屬性。 預設屬性必須接受參數，而且可以在不指定屬性名稱的情況下設定和抓取。 如果您將屬性宣告為 `Default`，則不能在屬性或其任何屬性程式上使用 `Private`。

- `accessmodifier`

  選擇性在 `Property` 語句和最多一個 `Get` 和 @no__t 2 語句上。 可以是下列其中一項：

  - [Public](../modifiers/public.md)

  - [Protected](../modifiers/protected.md)

  - [Friend](../modifiers/friend.md)

  - [Private](../modifiers/private.md)

  - [Protected Friend](../modifiers/protected-friend.md)

  - [Private Protected](../modifiers/private-protected.md)

  請參閱 [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md)。

- `propertymodifiers`

  選擇性。 可以是下列其中一項：

  - [多載](../modifiers/overloads.md)

  - [Overrides](../modifiers/overrides.md)

  - [Overridable](../modifiers/overridable.md)

  - [NotOverridable](../modifiers/notoverridable.md)

  - [MustOverride](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  選擇性。 請參閱[共用](../modifiers/shared.md)。

- `Shadows`

  選擇性。 請參閱[Shadows](../modifiers/shadows.md)。

- `ReadOnly`

  選擇性。 請參閱[ReadOnly](../modifiers/readonly.md)。

- `WriteOnly`

  選擇性。 請參閱[WriteOnly](../modifiers/writeonly.md)。

- `Iterator`

  選擇性。 請參閱[Iterator](../modifiers/iterator.md)。

- `name`

  必要項。 屬性的名稱。 請參閱 [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)。

- `parameterlist`

  選擇性。 本機變數名稱的清單，代表這個屬性的參數，以及可能的 `Set` 程式的其他參數。 請參閱[參數清單](parameter-list.md)。

- `returntype`

  如果 `Option Strict` `On` 則為必要。 這個屬性所傳回之值的資料類型。

- `Implements`

  選擇性。 指出此屬性會執行一或多個屬性，每個屬性都是由這個屬性的包含類別或結構所實的介面所定義。 請參閱[Implements 語句](implements-statement.md)。

- `implementslist`

  如果使用 `Implements`，則為必要項。 要實作為屬性的清單。

  `implementedproperty [ , implementedproperty ... ]`

  每個 `implementedproperty` 都具有下列語法和組件：

  `interface.definedname`

  |組件|描述|
  |---|---|
  |`interface`|必要項。 這個屬性的包含類別或結構所實作為介面的名稱。|
  |`definedname`|必要項。 用來定義屬性的名稱 `interface`。|

- `Get`

  選擇性。 如果屬性標示為 `ReadOnly`，則為必要。 啟動用來傳回屬性值的 `Get` 屬性程式。  @No__t-0 語句不會與[自動執行的屬性](../../programming-guide/language-features/procedures/auto-implemented-properties.md)搭配使用。

- `statements`

  選擇性。 要在 `Get` 或 `Set` 程式內執行的語句區塊。

- `End Get`

  終止 `Get` 屬性程式。

- `Set`

  選擇性。 如果屬性標示為 `WriteOnly`，則為必要。 啟動用來儲存屬性值的 `Set` 屬性程式。  @No__t-0 語句不會與[自動執行的屬性](../../programming-guide/language-features/procedures/auto-implemented-properties.md)搭配使用。

- `End Set`

  終止 `Set` 屬性程式。

- `End Property`

  終止這個屬性的定義。

## <a name="remarks"></a>備註

@No__t-0 語句引進了屬性的宣告。 屬性可以有 `Get` 程式（唯讀）、@no__t 1 程式（僅限寫入）或兩者（讀寫）。 使用自動執行的屬性時，您可以省略 `Get` 和 @no__t 1 程式。 如需詳細資訊，請參閱[自動實作的屬性](../../programming-guide/language-features/procedures/auto-implemented-properties.md)。

您只能在類別層級使用 `Property`。 這表示屬性的宣告*內容*必須是類別、結構、模組或介面，而且不能是原始程式檔、命名空間、程式或區塊。 如需詳細資訊，請參閱[宣告內容和預設存取層級](declaration-contexts-and-default-access-levels.md)。

根據預設，屬性會使用公用存取。 您可以使用 `Property` 語句上的存取修飾詞來調整屬性的存取層級，也可以選擇性地將其中一個屬性程式調整為更嚴格的存取層級。

Visual Basic 在屬性指派期間，將參數傳遞給 @no__t 0 程式。 如果您未提供 `Set` 的參數，整合式開發環境（IDE）會使用名為 `value` 的隱含參數。 這個參數會保留要指派給屬性的值。 您通常會將此值儲存在私用區域變數中，並在每次呼叫 @no__t 0 程式時傳回它。

## <a name="rules"></a>規則

- **混合存取層級。** 如果您要定義讀寫屬性，您可以選擇性地為 `Get` 或 `Set` 程式指定不同的存取層級，但不能同時為兩者。 如果您這樣做，程式存取層級必須比屬性的存取層級更嚴格。 例如，如果將屬性宣告 `Friend`，您可以將 `Set` 程式宣告為 `Private`，但不會 `Public`。

  如果您要定義 `ReadOnly` 或 @no__t 1 屬性，則單一屬性程式（分別為 `Get` 或 `Set`）代表所有屬性。 您不能為這類程式宣告不同的存取層級，因為這會為屬性設定兩個存取層級。

- **傳回類型。** @No__t-0 語句可以宣告它所傳回之值的資料類型。 您可以指定任何資料類型，或是列舉、結構、類別或介面的名稱。

  如果您未指定 `returntype`，此屬性會傳回 `Object`。

- **實作.** 如果此屬性使用 `Implements` 關鍵字，則包含的類別或結構必須緊接在其 `Class` 或 `Structure` 語句之後的 `Implements` 語句。 @No__t-0 語句必須包含 `implementslist` 中指定的每個介面。 不過，介面用來定義 `Property` （在 `definedname`）的名稱不一定要與這個屬性的名稱相同（在 `name`）。

## <a name="behavior"></a>行為

- **從屬性程式傳回。** 當 `Get` 或 @no__t 1 程式回到呼叫程式碼時，執行會在叫用它的語句後面繼續進行語句。

  @No__t-0 和 @no__t 1 語句會導致立即離開屬性程式。 任何數目的 `Exit Property` 和 @no__t 1 語句都可以出現在程式中的任何位置，您可以混用 `Exit Property` 和 `Return` 語句。

- **傳回值。** 若要從 `Get` 程式傳回值，您可以將值指派給屬性名稱，或將它包含在 @no__t 1 語句中。 下列範例會將傳回值指派給屬性名稱 `quoteForTheDay`，然後使用 `Exit Property` 語句傳回。

  [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]

  [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]

  如果您使用 `Exit Property`，但未指派值給 `name`，則 @no__t 2 程式會傳回屬性之資料類型的預設值。

  同時 `Return` 語句會指派 `Get` 程式傳回值並結束程式。 下列範例會顯示這種情況。

  [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]

  [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]

## <a name="example"></a>範例

下列範例會在類別中宣告屬性。

[!code-vb[VbVbalrStatements#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#51)]

## <a name="see-also"></a>另請參閱

- [自動實作的屬性](../../programming-guide/language-features/procedures/auto-implemented-properties.md)
- [物件和類別](../../programming-guide/language-features/objects-and-classes/index.md)
- [Get 陳述式](get-statement.md)
- [Set 陳述式](set-statement.md)
- [參數清單](parameter-list.md)
- [Default](../modifiers/default.md)
