---
title: Dim 陳述式 (Visual Basic)
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
ms.openlocfilehash: cab1cc07d23a44e57bdb0962a323b014308cb1e5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638210"
---
# <a name="dim-statement-visual-basic"></a>Dim 陳述式 (Visual Basic)

宣告，並針對一或多個變數配置儲存空間。

## <a name="syntax"></a>語法

```
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

選擇性。 指定這些是可以引發事件的類別執行個體參考的物件變數。 請參閱[WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)。

- `variablelist`

  必要項。 此陳述式所宣告的變數清單。

  `variable [ , variable ... ]`

  每個 `variable` 都具有下列語法和組件：

  `variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`

  |組件|描述|
  |---|---|
  |`variablename`|必要項。 變數的名稱。 請參閱 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。|
  |`boundslist`|選擇性。 每個維度的陣列變數的範圍的清單。|
  |`New`|選擇性。 建立類別的新執行個體時`Dim`陳述式執行。|
  |`datatype`|選擇性。 變數的資料類型。|
  |`With`|選擇性。 導入了物件初始設定式清單。|
  |`propertyname`|選擇性。 在類別中屬性的名稱，您要進行執行的個體。|
  |`propinitializer`|後需要`propertyname`=。 運算式評估，以及指派給屬性名稱。|
  |`initializer`|選擇性如果`New`未指定。 運算式評估，以及建立時指派給變數。|

## <a name="remarks"></a>備註

Visual Basic 編譯器使用`Dim`陳述式來判斷變數的資料類型和其他資訊，例如哪些程式碼可以存取的變數。 下列範例會宣告變數，以保留`Integer`值。

```vb
Dim numberOfStudents As Integer
```

您可以指定任何資料類型或列舉、 結構、 類別或介面的名稱。

```vb
Dim finished As Boolean
Dim monitorBox As System.Windows.Forms.Form
```

對於參考型別，您使用`New`關鍵字來建立類別的新執行個體，或結構，指定資料型別。 如果您使用`New`，您不使用初始設定式運算式。 相反地，您提供引數，如有必要，建立變數類別的建構函式。

```vb
Dim bottomLabel As New System.Windows.Forms.Label
```

您可以宣告程序、 區塊、 類別、 結構或模組中的變數。 您無法宣告的原始程式檔、 命名空間或介面中的變數。 如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。

在模組層級，任何程序中，外部宣告的變數是*成員變數*或是*欄位*。 成員變數會在其類別、 結構或模組的範圍中。 程序層級宣告的變數是*區域變數*。 本機變數是在範圍內，只在他們的程序或區塊內。

下列存取修飾詞用來宣告變數的程序之外： `Public`， `Protected`， `Friend`， `Protected Friend`，和`Private`。 如需詳細資訊，請參閱 <<c0> [ 存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。

`Dim`關鍵字是選擇性，而且通常省略 如果您指定任何下列修飾詞： `Public`， `Protected`， `Friend`， `Protected Friend`， `Private`， `Shared`， `Shadows`， `Static`，`ReadOnly`，或`WithEvents`。

```vb
Public maximumAllowed As Double
Protected Friend currentUserName As String
Private salary As Decimal
Static runningTotal As Integer
```

如果`Option Explicit`是 on （預設值），編譯器會需要的宣告的每個您所使用的變數。 如需詳細資訊，請參閱 < [Option Explicit 陳述式](../../../visual-basic/language-reference/statements/option-explicit-statement.md)。

## <a name="specifying-an-initial-value"></a>指定的初始值

建立時，您可以指派值給變數。 在您使用實值類型，如*初始設定式*提供要指派給變數的運算式。 運算式必須評估為常數，可以在編譯時期計算。

```vb
Dim quantity As Integer = 10
Dim message As String = "Just started"
```

如果已指定初始設定式，而且中未指定資料型別`As`子句*型別推斷*用來推斷資料型別，從初始設定式。 在下列範例中，同時`num1`和`num2`強型別為整數。 在第二個宣告中，型別推斷會推斷值 3 的類型。

```vb
' Use explicit typing.
Dim num1 As Integer = 3

' Use local type inference.
Dim num2 = 3
```

型別推斷會套用在程序層級。 它不適用於外部類別、 結構、 模組或介面中的程序。 如需型別推斷的詳細資訊，請參閱[Option Infer 陳述式](../../../visual-basic/language-reference/statements/option-infer-statement.md)並[區域型別推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。

如未指定資料型別或初始設定式時，會發生什麼情況的相關資訊，請參閱 <<c0> [ 預設資料類型和值](../../../visual-basic/language-reference/statements/dim-statement.md#default)本主題稍後的。

您可以使用*物件初始設定式*宣告具名和匿名型別的執行個體。 下列程式碼建立的執行個體`Student`類別，並使用物件初始設定式初始化的屬性。

```vb
Dim student1 As New Student With {.First = "Michael",
                                  .Last = "Tucker"}
```

如需物件初始設定式的詳細資訊，請參閱[How to:使用物件初始設定式宣告物件](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)，[物件初始設定式：具名和匿名型別](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)，並[匿名型別](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。

## <a name="declaring-multiple-variables"></a>宣告多個變數

您可以宣告一個宣告陳述式中的數個變數使用括號指定針對每個與下列每個陣列名稱的變數名稱。 以逗號分隔多個變數。

```vb
Dim lastTime, nextTime, allTimes() As Date
```

如果您宣告多個變數具有一個`As`子句中，您無法提供該變數群組的初始設定式。

您可以指定不同的變數的不同資料類型使用個別`As`子句宣告每個變數。 每個變數會在第一個指定的資料類型`As`子句後發生其`variablename`組件。

```vb
Dim a, b, c As Single, x, y As Double, i As Integer
' a, b, and c are all Single; x and y are both Double
```

## <a name="arrays"></a>陣列

您可以宣告的變數來保存*陣列*，其中可包含多個值。 若要指定變數會保留一個陣列，請遵循其`variablename`立即使用括號。 如需陣列的詳細資訊，請參閱[陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)。

您可以指定的下限與上限的每個維度的陣列。 若要這樣做，請包含`boundslist`在括號內。 每個維度，`boundslist`指定上限以及選擇性的下限。 下限一律為零，是否您不指定。 每個索引從 0 到上限值而有所不同。

下列兩個陳述式是相等的。 每個陳述式會宣告陣列的 21`Integer`項目。 當您存取陣列時，索引有所不同從 0 到 20。

```vb
Dim totals(20) As Integer
Dim totals(0 To 20) As Integer
```

下列陳述式會宣告類型的二維陣列`Double`。 陣列中有 4 個資料列 (3 + 1) 的 6 個資料行 (5 + 1) 每個。 請注意上限，代表索引，而不是維度的長度最大的可能值。 維度的長度是上限加 1。

```vb
Dim matrix2(3, 5) As Double
```

陣列可以有 1 到 32 個維度。

您可以將所有範圍都保留為空白陣列宣告中。 如果您這麼做時，陣列中有指定，維度的數目，但它未初始化。 它的值為`Nothing`直到您至少初始化其項目部分。 `Dim`陳述式必須指定所有的維度或的任何維度的界限。

```vb
' Declare an array with blank array bounds.
Dim messages() As String
' Initialize the array.
ReDim messages(4)
```

如果陣列中有多個維度，您必須包含括號來表示的維度數目之間的逗號。

```vb
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte
```

您可以宣告*長度零的陣列*藉由宣告一個陣列的維度，以便是-1。 此變數會保存的長度為零的陣列沒有值`Nothing`。 特定的 common language runtime 函數所需長度為零的陣列。 如果您嘗試存取這類陣列時，就會發生執行階段例外狀況。 如需詳細資訊，請參閱 <<c0> [ 陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)。

您可以使用陣列常值來初始化陣列的值。 若要這樣做，括住的初始設定值，以大括弧 (`{}`)。

```vb
Dim longArray() As Long = {0, 1, 2, 3}
```

對於多維度陣列，初始化的每個個別的維度會包含在外部維度中的大括號。 項目是以列為主要順序指定。

```vb
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}
```

如需有關陣列常值的詳細資訊，請參閱[陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)。

## <a name="default"></a> 預設資料類型和值

下表說明在 `Dim` 陳述式中指定資料類型和初始設定式的各種組合結果。

|指定了資料類型？|指定了初始設定式？|範例|結果|
|---|---|---|---|
|否|否|`Dim qty`|如果[Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)會將變數設為 off （預設值）， `Nothing`。<br /><br /> 如果 `Option Strict` 已開啟，就會發生編譯時間錯誤。|
|否|是|`Dim qty = 5`|如果[Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md)是 on （預設值），此變數會採用資料類型的初始設定式。 請參閱[區域型別推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。<br /><br /> 如果 `Option Infer` 已關閉，且 `Option Strict` 也已關閉，此變數會採用 `Object` 的資料類型。<br /><br /> 如果 `Option Infer` 已關閉，但是 `Option Strict` 已開啟，就會發生編譯時間錯誤。|
|是|否|`Dim qty As Integer`|變數會初始化為資料類型的預設值。 請參閱本節稍後的表格。|
|是|是|`Dim qty  As Integer = 5`|如果初始設定式的資料類型無法轉換成指定的資料類型，就會發生編譯時期錯誤。|

如果您指定的資料類型，但未指定初始設定式，Visual Basic 變數初始化為其資料類型的預設值。 下表顯示的預設初始化值。

|資料類型|預設值|
|---|---|
|所有數字類型 (包括`Byte`和`SByte`)|0|
|`Char`|二進位的 0|
|所有參考型別 (包括`Object`， `String`，和所有陣列)|`Nothing`|
|`Boolean`|`False`|
|`Date`|1 年 1 月 12:00 AM (01/01/0001 12:00:00 AM)|

結構的每個項目都會被視為個別的變數它初始化。 如果您宣告陣列的長度，但未初始化其項目，如同個別的變數，會初始化每個項目。

## <a name="static-local-variable-lifetime"></a>靜態的本機變數存留期

A`Static`區域變數有較長的存留期比宣告它的程序。 變數的存留期的範圍取決於宣告程序的位置，以及它是否`Shared`。

|程序宣告|初始化變數|變數會停止現有的|
|---|---|---|
|在模組中|第一次呼叫程序|當您的程式停止執行|
|程序是在類別或結構中， `Shared`|第一次呼叫程序的特定執行個體或類別或結構本身|當您的程式停止執行|
|在類別或結構中，程序不是 `Shared`|第一次在特定的執行個體上呼叫程序|執行個體進行記憶體回收 (GC) 的發行時|

## <a name="attributes-and-modifiers"></a>屬性和修飾詞

您可以套用屬性，只以成員變數，而非區域變數。 屬性會提供資訊給組件的中繼資料，不是暫時的儲存體，例如本機變數才有意義。

在模組層級，您無法使用`Static`修飾詞來宣告成員變數。 在程序層級，您無法使用`Shared`， `Shadows`， `ReadOnly`， `WithEvents`，或任何存取修飾詞來宣告本機變數。

您可以指定哪些程式碼可以存取的變數，藉由提供`accessmodifier`。 類別和模組成員 （以外的任何程序） 的變數預設為私用存取，而結構成員變數預設為公用存取。 您可以調整它們的存取層級，使用存取修飾詞。 您無法使用存取修飾詞 （在程序） 的本機變數。

您可以指定`WithEvents`只對成員變數，而不是在程序內的本機變數。 如果您指定`WithEvents`，變數的資料類型必須是特定類別類型時，不`Object`。 您無法宣告陣列`WithEvents`。 如需有關事件的詳細資訊，請參閱[事件](../../../visual-basic/programming-guide/language-features/events/index.md)。

> [!NOTE]
> 程式碼類別之外，結構或模組必須限定成員變數的名稱，該類別、 結構或模組的名稱。 程序或區塊不能參考該程序或區塊內任何區域變數的外的程式碼。

## <a name="releasing-managed-resources"></a>釋放 Managed 的資源

.NET Framework 記憶體回收行程會處置 managed 資源而不需要任何額外的程式碼，就在您的組件。 不過，您可以強制受管理的資源，而不是等待記憶體回收行程的處置。

如果類別是由特別重要，且很少資源 （例如資料庫連接或檔案控制代碼） 所佔用，您可能不想等到下一個記憶體回收以清除不再使用中的類別執行個體。 類別可以實作<xref:System.IDisposable>介面，以提供方法來釋放資源之前進行記憶體回收。 類別若實作該介面會公開`Dispose`可以強制寶貴的資源可立即釋放呼叫的方法。

`Using`陳述式自動化程序取得資源、 執行一組陳述式，和然後處置的資源。 不過，資源必須實作<xref:System.IDisposable>介面。 如需詳細資訊，請參閱 [Using 陳述式](../../../visual-basic/language-reference/statements/using-statement.md)。

## <a name="example"></a>範例

下列範例會藉由宣告變數`Dim`搭配各種選項的陳述式。

[!code-vb[VbVbalrStatements#141](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#141)]

## <a name="example"></a>範例

下列範例會列出介於 1 到 30 之間的質數。 程式碼註解說明本機變數的範圍。

[!code-vb[VbVbalrStatements#142](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#142)]

## <a name="example"></a>範例

在下列範例中，`speedValue`在類別層級中宣告變數。 `Private`關鍵字用來宣告變數。 中的任何程序可以存取該變數`Car`類別。

[!code-vb[VbVbalrStatements#144](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#144)]

[!code-vb[VbVbalrStatements#145](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#145)]

## <a name="see-also"></a>另請參閱

- [Const 陳述式](../../../visual-basic/language-reference/statements/const-statement.md)
- [ReDim 陳述式](../../../visual-basic/language-reference/statements/redim-statement.md)
- [Option Explicit 陳述式](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Option Infer 陳述式](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [專案設計工具、編譯頁面 (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [變數宣告](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [物件初始設定式：具名和匿名類型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [匿名類型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [物件初始設定式：具名和匿名類型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [如何：使用物件初始設定式宣告物件](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
- [區域類型推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
