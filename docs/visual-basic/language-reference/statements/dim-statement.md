---
title: Dim 陳述式
ms.date: 05/12/2018
f1_keywords:
- vb.Dim
- Dim
helpviewer_keywords:
- Public keyword [Visual Basic], in Dim statement
- Dim statement [Visual Basic]
- fixed-length strings [Visual Basic], declaring
- variables [Visual Basic], declaring
- WithEvents keyword [Visual Basic], Dim statement
- dynamic arrays [Visual Basic], Dim statement
- variables [Visual Basic], initializing
- '{} braces'
- fields [Visual Basic], as member variables
- declarations [Visual Basic], dynamic arrays
- member variables [Visual Basic]
- default values [Visual Basic]
- data types [Visual Basic], assigning
- braces {}
- As keyword [Visual Basic], in Dim statement
- arrays [Visual Basic], declaring
- New keyword [Visual Basic], Dim statement
- To keyword [Visual Basic], in Dim statement
- storage [Visual Basic], allocating
- local variables [Visual Basic]
- declaration statements [Visual Basic]
- Dim statement [Visual Basic], syntax
- variables [Visual Basic], member and local
ms.assetid: fae3eca1-f0b2-4400-994b-7aa58a848448
ms.openlocfilehash: ac66ffdba622673ef42017d147c05b2a2733dede
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343760"
---
# <a name="dim-statement-visual-basic"></a>Dim 陳述式 (Visual Basic)

宣告並配置一或多個變數的儲存空間。

## <a name="syntax"></a>語法

```vb
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]
Dim [ WithEvents ] variablelist
```

## <a name="parts"></a>組件

- `attributelist`

  選擇性。 請參閱[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)。

- `accessmodifier`

  選擇性。 可以是下列其中一項：

  - [Public](../../../visual-basic/language-reference/modifiers/public.md)

  - [Protected](../../../visual-basic/language-reference/modifiers/protected.md)

  - [Friend](../../../visual-basic/language-reference/modifiers/friend.md)

  - [Private](../../../visual-basic/language-reference/modifiers/private.md)

  - [Protected Friend](../../language-reference/modifiers/protected-friend.md)

  - [Private Protected](../../language-reference/modifiers/private-protected.md)

  請參閱 [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。

- `Shared`

  選擇性。 請參閱[共用](../../../visual-basic/language-reference/modifiers/shared.md)。

- `Shadows`

  選擇性。 請參閱[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)。

- `Static`

  選擇性。 請參閱[靜態](../../../visual-basic/language-reference/modifiers/static.md)。

- `ReadOnly`

  選擇性。 請參閱[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。

- `WithEvents`

選擇性。 指定這些是參考可引發事件之類別實例的物件變數。 請參閱[WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)。

- `variablelist`

  必要。 在此語句中宣告的變數清單。

  `variable [ , variable ... ]`

  每個 `variable` 都具有下列語法和組件：

  `variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`

  |組件|描述|
  |---|---|
  |`variablename`|必要。 變數的名稱。 請參閱 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。|
  |`boundslist`|選擇性。 陣列變數的每個維度的界限清單。|
  |`New`|選擇性。 當 `Dim` 語句執行時，建立類別的新實例。|
  |`datatype`|選擇性。 變數的資料類型。|
  |`With`|選擇性。 引進物件初始化運算式清單。|
  |`propertyname`|選擇性。 您要做為實例之類別中的屬性名稱。|
  |`propinitializer`|`propertyname` = 之後才需要。 評估並指派給屬性名稱的運算式。|
  |`initializer`|如果未指定 `New`，則為選擇性。 建立時，評估並指派給變數的運算式。|

## <a name="remarks"></a>備註

Visual Basic 編譯器會使用 `Dim` 語句來判斷變數的資料類型和其他資訊，例如可存取變數的程式碼。 下列範例會宣告用來保存 `Integer` 值的變數。

```vb
Dim numberOfStudents As Integer
```

您可以指定任何資料類型，或是列舉、結構、類別或介面的名稱。

```vb
Dim finished As Boolean
Dim monitorBox As System.Windows.Forms.Form
```

對於參考型別，您可以使用 `New` 關鍵字來建立由資料類型所指定之類別或結構的新實例。 如果您使用 `New`，就不會使用初始化運算式運算式。 相反地，您會提供引數（如有需要）到您要在其中建立變數之類別的函式。

```vb
Dim bottomLabel As New System.Windows.Forms.Label
```

您可以在程式、區塊、類別、結構或模組中宣告變數。 您無法在原始檔、命名空間或介面中宣告變數。 如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。

在任何程式之外，于模組層級宣告的變數是*成員變數*或*欄位*。 成員變數在其類別、結構或模組的範圍內。 在程式層級宣告的變數是*本機變數*。 區域變數僅限於其程式或區塊內的範圍。

下列存取修飾詞是用來在程式之外宣告變數： `Public`、`Protected`、`Friend`、`Protected Friend`和 `Private`。 如需詳細資訊，請參閱[Visual Basic 中的存取層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。

`Dim` 關鍵字是選擇性的，而且如果您指定下列任何修飾詞，通常會省略： `Public`、`Protected`、`Friend`、`Protected Friend`、`Private`、`Shared`、`Shadows`、`Static`、`ReadOnly`或 `WithEvents`。

```vb
Public maximumAllowed As Double
Protected Friend currentUserName As String
Private salary As Decimal
Static runningTotal As Integer
```

如果 `Option Explicit` 是 on （預設值），則編譯器需要您所使用之每個變數的宣告。 如需詳細資訊，請參閱[Option Explicit 語句](../../../visual-basic/language-reference/statements/option-explicit-statement.md)。

## <a name="specifying-an-initial-value"></a>指定初始值

建立變數時，您可以將值指派給它。 對於實值型別，您可以使用*初始化*運算式來提供要指派給變數的運算式。 運算式必須評估為可在編譯時期計算的常數。

```vb
Dim quantity As Integer = 10
Dim message As String = "Just started"
```

如果指定了初始化運算式，而且未在 `As` 子句中指定資料類型，則會使用*型別推斷*來推斷初始化運算式的資料型別。 在下列範例中，`num1` 和 `num2` 都是強型別做為整數。 在第二個宣告中，型別推斷會從值3推斷型別。

```vb
' Use explicit typing.
Dim num1 As Integer = 3

' Use local type inference.
Dim num2 = 3
```

型別推斷適用于程式層級。 不適用於類別、結構、模組或介面中的程式之外。 如需型別推斷的詳細資訊，請參閱[Option 推斷語句](../../../visual-basic/language-reference/statements/option-infer-statement.md)和[區欄位型別推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。

如需未指定資料類型或初始化運算式時，會發生什麼情況的詳細資訊，請參閱本主題稍後的[預設資料類型和值](../../../visual-basic/language-reference/statements/dim-statement.md#default)。

您可以使用*物件初始化運算式*，宣告名為和匿名型別的實例。 下列程式碼會建立 `Student` 類別的實例，並使用物件初始化運算式來初始化屬性。

```vb
Dim student1 As New Student With {.First = "Michael",
                                  .Last = "Tucker"}
```

如需物件初始化運算式的詳細資訊，請參閱[如何：使用物件初始化運算式宣告物件](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)、[物件初始化運算式：命名和匿名型別](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)和[匿名型別](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。

## <a name="declaring-multiple-variables"></a>宣告多個變數

您可以在一個宣告語句中宣告數個變數，為每一個宣告指定變數名稱，並在每個陣列名稱稱後面加上括弧。 以逗號分隔多個變數。

```vb
Dim lastTime, nextTime, allTimes() As Date
```

如果您使用一個 `As` 子句來宣告一個以上的變數，就無法為該變數群組提供初始化運算式。

您可以針對您所宣告的每個變數使用個別的 `As` 子句，為不同的變數指定不同的資料類型。 每個變數都會接受在其 `variablename` 部分之後遇到的第一個 `As` 子句中指定的資料類型。

```vb
Dim a, b, c As Single, x, y As Double, i As Integer
' a, b, and c are all Single; x and y are both Double
```

## <a name="arrays"></a>陣列

您可以宣告變數來保存*陣列*，其中可以保留多個值。 若要指定變數保存陣列，請在其後面加上括弧的 `variablename`。 如需陣列的詳細資訊，請參閱[陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)。

您可以指定陣列的每個維度的下限和上限。 若要這麼做，請在括弧內包含 `boundslist`。 `boundslist` 指定每個維度的上限和下限。 下限一律為零，不論您是否指定。 每個索引的上限值可能會從零開始。

下列兩個語句是相等的。 每個語句都會宣告21個 `Integer` 元素的陣列。 當您存取陣列時，索引可能會從0到20。

```vb
Dim totals(20) As Integer
Dim totals(0 To 20) As Integer
```

下列語句會宣告 `Double`類型的二維陣列。 陣列有4個數據列（3 + 1），分別為6個數據行（5 + 1）。 請注意，上限代表索引的最大可能值，而不是維度的長度。 維度的長度是上限加一。

```vb
Dim matrix2(3, 5) As Double
```

陣列可以有1到32個維度。

您可以在陣列宣告中將所有界限保留空白。 如果您這樣做，陣列就會包含您指定的維度數目，但它是未初始化的。 它的值為 `Nothing`，直到您至少初始化其中的部分元素為止。 `Dim` 語句必須為所有維度或沒有維度指定界限。

```vb
' Declare an array with blank array bounds.
Dim messages() As String
' Initialize the array.
ReDim messages(4)
```

如果陣列有多個維度，您必須在括弧之間包含逗號，以指示維度的數目。

```vb
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte
```

您可以宣告陣列的其中一個維度為-1，以宣告*長度為零的陣列*。 持有長度為零之陣列的變數沒有值 `Nothing`。 特定的 common language runtime 函式需要長度為零的陣列。 如果您嘗試存取這類陣列，就會發生執行時間例外狀況。 如需詳細資訊，請參閱[陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)。

您可以使用陣列常值來初始化陣列的值。 若要這麼做，請使用大括弧（`{}`）來括住初始化值。

```vb
Dim longArray() As Long = {0, 1, 2, 3}
```

若是多維陣列，每個不同維度的初始化都會以大括弧括住在外部維度中。 元素會以資料列主要順序來指定。

```vb
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}
```

如需陣列常值的詳細資訊，請參閱[陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)。

## <a name="default"></a>預設資料類型和值

下表說明在 `Dim` 陳述式中指定資料類型和初始設定式的各種組合結果。

|指定了資料類型？|指定了初始設定式？|範例|結果|
|---|---|---|---|
|否|否|`Dim qty`|如果[Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)為 off （預設值），則變數會設定為 `Nothing`。<br /><br /> 如果 `Option Strict` 已開啟，就會發生編譯時間錯誤。|
|否|是|`Dim qty = 5`|如果[Option 推斷](../../../visual-basic/language-reference/statements/option-infer-statement.md)為 on （預設值），則變數會採用初始化運算式的資料類型。 請參閱[區欄位型別推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。<br /><br /> 如果 `Option Infer` 已關閉，且 `Option Strict` 也已關閉，此變數會採用 `Object` 的資料類型。<br /><br /> 如果 `Option Infer` 已關閉，但是 `Option Strict` 已開啟，就會發生編譯時間錯誤。|
|是|否|`Dim qty As Integer`|變數會初始化為資料類型的預設值。 請參閱本節稍後的表格。|
|是|是|`Dim qty  As Integer = 5`|如果初始設定式的資料類型無法轉換成指定的資料類型，就會發生編譯時期錯誤。|

如果您指定資料類型，但未指定初始化運算式，Visual Basic 會將變數初始化為其資料類型的預設值。 下表顯示預設的初始化值。

|資料類型|預設值|
|---|---|
|所有數數值型別（包括 `Byte` 和 `SByte`）|0|
|`Char`|二進位0|
|所有參考型別（包括 `Object`、`String`和所有陣列）|`Nothing`|
|`Boolean`|`False`|
|`Date`|每年1月1日上午12:00 （01/01/0001 12:00:00 AM）|

結構的每個元素都會初始化為另一個變數。 如果您宣告陣列的長度，但不初始化其元素，則每個專案都會初始化為個別的變數。

## <a name="static-local-variable-lifetime"></a>靜態區域變數存留期

`Static` 本機變數的存留期比宣告它的程式還長。 變數存留期的界限取決於程式的宣告位置，以及是否 `Shared`。

|過程聲明|變數已初始化|變數停止現有的|
|---|---|---|
|在模組中|第一次呼叫程式時|當程式停止執行時|
|在類別或結構中，程式是 `Shared`|第一次在特定實例或類別或結構本身上呼叫程式時|當程式停止執行時|
|在類別或結構中，程式不 `Shared`|第一次在特定實例上呼叫程式時|釋放實例以進行垃圾收集（GC）時|

## <a name="attributes-and-modifiers"></a>屬性和修飾詞

您只能將屬性套用至成員變數，而不能套用至本機變數。 屬性會將資訊提供給元件的中繼資料，這對暫存儲存體（例如區域變數）沒有意義。

在模組層級，您無法使用 `Static` 修飾詞來宣告成員變數。 在程式層級上，您不能使用 `Shared`、`Shadows`、`ReadOnly`、`WithEvents`或任何存取修飾詞來宣告本機變數。

您可以藉由提供 `accessmodifier`，指定可以存取變數的程式碼。 類別和模組成員變數（在任何程式之外）預設為私用存取，而結構成員變數預設為公用存取。 您可以使用存取修飾詞來調整其存取層級。 您不能在本機變數上使用存取修飾詞（在程式內）。

您只能在成員變數上指定 `WithEvents`，而不是在程式內的區域變數上指定。 如果您指定 `WithEvents`，變數的資料類型必須是特定的類別類型，而不是 `Object`。 您無法使用 `WithEvents`宣告陣列。 如需事件的詳細資訊，請參閱[事件](../../../visual-basic/programming-guide/language-features/events/index.md)。

> [!NOTE]
> 類別、結構或模組之外的程式碼必須使用該類別、結構或模組的名稱來限定成員變數的名稱。 程式或區塊外的程式碼無法參考該程式或區塊中的任何區域變數。

## <a name="releasing-managed-resources"></a>釋放受控資源

.NET Framework 垃圾收集行程會處置受控資源，而不需任何額外的程式碼。 不過，您可以強制處置受管理的資源，而不是等候垃圾收集行程。

如果類別持有特別寶貴的資源（例如資料庫連接或檔案控制代碼），您可能不想要等到下一次垃圾收集，就能清除不再使用的類別實例。 類別可以執行 <xref:System.IDisposable> 介面，以提供在垃圾收集之前釋放資源的方式。 實作為介面的類別會公開可呼叫的 `Dispose` 方法，以強制立即釋放寶貴的資源。

`Using` 語句會自動化取得資源、執行一組語句，然後處置資源的程式。 不過，資源必須執行 <xref:System.IDisposable> 介面。 如需詳細資訊，請參閱 [Using 陳述式](../../../visual-basic/language-reference/statements/using-statement.md)。

## <a name="example"></a>範例

下列範例會使用 `Dim` 語句搭配各種選項來宣告變數。

[!code-vb[VbVbalrStatements#141](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#141)]

## <a name="example"></a>範例

下列範例會列出介於1到30之間的質數。 本機變數的範圍會在程式碼批註中說明。

[!code-vb[VbVbalrStatements#142](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#142)]

## <a name="example"></a>範例

在下列範例中，會在類別層級宣告 `speedValue` 變數。 `Private` 關鍵字是用來宣告變數。 `Car` 類別中的任何程式都可以存取變數。

[!code-vb[VbVbalrStatements#144](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#144)]

[!code-vb[VbVbalrStatements#145](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#145)]

## <a name="see-also"></a>另請參閱

- [Const 陳述式](../../../visual-basic/language-reference/statements/const-statement.md)
- [ReDim 陳述式](../../../visual-basic/language-reference/statements/redim-statement.md)
- [Option Explicit 陳述式](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Option Infer 陳述式](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [專案設計工具、編譯頁 (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [變數宣告](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [物件初始設定式：具名和匿名類型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [匿名類型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [物件初始設定式：具名和匿名類型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [如何：使用物件初始設定式宣告物件](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
- [區域類型推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
