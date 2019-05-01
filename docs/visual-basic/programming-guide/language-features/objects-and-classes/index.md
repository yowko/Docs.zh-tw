---
title: Visual Basic 中的物件和類別
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic]
- objects [Visual Basic]
ms.assetid: c68c5752-1006-46e1-975a-6717b62a42fc
ms.openlocfilehash: ec5825dacaf67ee2544302f4f95a1b341ecf1bf7
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63807854"
---
# <a name="objects-and-classes-in-visual-basic"></a>Visual Basic 中的物件和類別

「物件」是可視為一個單位的程式碼和資料組合。 物件可以是應用程式的一部分，例如控制項或表單。 整個應用程式也可以是一個物件。

當您在 Visual Basic 中建立應用程式時，您經常會使用物件。 您可以使用 Visual Basic 中，所提供，例如控制項、 表單和資料存取物件的物件。 您也可以在 Visual Basic 應用程式內使用從其他應用程式的物件。 您甚至可以建立自己的物件，並為其定義其他屬性和方法。 物件的作用類似針對程式預製的建置組塊 - 它們可讓您撰寫一段程式碼一次，然後不斷地重複使用。

本主題會詳細討論物件。

## <a name="objects-and-classes"></a>物件和類別

在 Visual Basic 中的每個物件所定義*類別*。 類別會描述物件的變數、屬性、程序及事件。 物件是類別的執行個體；當您定義類別之後，就能視需要建立最多的物件。

若要了解物件和其類別之間的關聯性，請想像餅乾壓模與餅乾。 餅乾壓模是類別。 它會定義每塊餅乾的特性，例如大小和形狀。 類別可用來建立物件。 物件則是餅乾。

您必須先建立物件，然後才能存取它的成員。

#### <a name="to-create-an-object-from-a-class"></a>從類別建立物件

1. 決定您要從哪一個類別建立物件。

2. 撰寫 [Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)來建立變數，而您可以將類別執行個體指派給該變數。 變數必須是所需類別的型別。

   ```vb
   Dim nextCustomer As customer
   ```

3. 新增 [New 運算子](../../../../visual-basic/language-reference/operators/new-operator.md)關鍵字，將變數初始化為類別的新執行個體。

   ```vb
   Dim nextCustomer As New customer
   ```

4. 您現在可以透過物件變數存取類別的成員。

   ```vb
   nextCustomer.accountNumber = lastAccountNumber + 1
   ```

> [!NOTE]
> 可能的話，您應該將變數宣告為您想要指派給它的類別型別。 這稱為「早期繫結」。 如果您在編譯時期不知道類別類型，可藉由將變數宣告為 [Object 資料類型](../../../../visual-basic/language-reference/data-types/object-data-type.md)來叫用「晚期繫結」。 不過，晚期繫結會讓效能降低，並限制存取執行階段物件的成員。 如需詳細資訊，請參閱[物件變數宣告](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)。

### <a name="multiple-instances"></a>多重執行個體

從類別新建的物件通常是彼此相同的。 不過，當它們以個別物件存在之後，就能個別變更其變數和屬性，而與其他執行個體無關。 例如，如果您在表單中新增三個核取方塊，每個核取方塊物件都是 <xref:System.Windows.Forms.CheckBox> 類別的執行個體。 個別的 <xref:System.Windows.Forms.CheckBox> 物件會共用一組由類別所定義的通用特性和功能 (屬性、變數、程序及事件)。 但是，每個物件都有自己的名稱、可個別啟用及停用，而且可以放在表單的不同位置。

## <a name="object-members"></a>物件成員

物件是應用程式的元素，代表類別的「執行個體」。 欄位、屬性、方法及事件都是物件的建置組塊，並構成它們的「成員」。

### <a name="member-access"></a>成員存取

您可以存取物件的成員，方法是依序指定物件變數的名稱、句點 (`.`) 及成員的名稱。 下列範例會設定 <xref:System.Windows.Forms.Label> 物件的 <xref:System.Windows.Forms.Control.Text%2A> 屬性。

```vb
warningLabel.Text = "Data not saved"
```

#### <a name="intellisense-listing-of-members"></a>成員的 IntelliSense 清單

當您叫用 IntelliSense 的 [列出成員] 選項時 (例如，當您輸入句號 (`.`) 做為成員存取運算子時)，它會列出類別的成員。 如果您在宣告為該類別執行個體的變數名稱後面輸入句點，IntelliSense 會列出所有執行個體成員，而不會列出任何共用的成員。 如果您在類別名稱本身後面輸入句點，則 IntelliSense 會列出所有共用的成員，但不會列出任何執行個體成員。 如需詳細資訊，請參閱[使用 IntelliSense](/visualstudio/ide/using-intellisense)。

### <a name="fields-and-properties"></a>欄位和屬性

「欄位」和「屬性」表示物件中所儲存的資訊。 您可以利用在程序中擷取和設定區域變數的相同方式，使用指派陳述式來擷取和設定它們的值。 下列範例會擷取 <xref:System.Windows.Forms.Label> 物件的 <xref:System.Windows.Forms.Control.Width%2A> 屬性，並設定 <xref:System.Windows.Forms.Control.ForeColor%2A> 屬性。

```vb
Dim warningWidth As Integer = warningLabel.Width
warningLabel.ForeColor = System.Drawing.Color.Red
```

請注意，也會呼叫欄位做為「成員變數」。

使用屬性程序的時機：

- 您需要控制何時以及如何設定或擷取值。

- 屬性具有一組定義明確且需要驗證的值。

- 設定值會導致一些可察覺的物件狀態變更，例如 `IsVisible` 屬性。

- 設定此屬性會導致其他內部變數的變更，或其他屬性值的變更。

- 您必須先執行一組步驟，才能設定或擷取此屬性。

使用欄位的時機：

- 值為自我驗證的型別。 例如，如果將 `True` 或 `False` 以外的值指派給 `Boolean` 變數，就會發生錯誤或自動資料轉換。

- 位於資料型別所支援範圍內的任何值都是有效的。 這適用許多型別為 `Single` 或 `Double` 的屬性。

- 屬性是 `String` 資料型別，而且對於字串的大小或值沒有任何限制。

- 如需詳細資訊，請參閱[屬性程序](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)。

### <a name="methods"></a>方法

「方法」是物件可執行的動作。 例如，<xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> 是 <xref:System.Windows.Forms.ComboBox> 物件的方法，可新增項目至下拉式方塊。

下列範例示範 <xref:System.Windows.Forms.Timer> 物件的 <xref:System.Windows.Forms.Timer.Start%2A> 方法。

```vb
Dim safetyTimer As New System.Windows.Forms.Timer
safetyTimer.Start()
```

請注意，方法只是物件所公開的「程序」。

如需詳細資訊，請參閱[程序](../../../../visual-basic/programming-guide/language-features/procedures/index.md)。

### <a name="events"></a>事件

事件是物件所識別的動作 (例如按一下滑鼠按鈕或按下按鍵)，而您可以撰寫程式碼來回應。 事件可能因使用者動作或程式碼而發生，或由系統所導致。 您可以將對事件發出訊號的程式碼視為「引發」事件，而將回應事件的程式碼視為「處理」它。

您也可以開發自己的自訂事件，透過您的物件來引發並由其他物件來處理。 如需詳細資訊，請參閱[事件](../../../../visual-basic/programming-guide/language-features/events/index.md)。

### <a name="instance-members-and-shared-members"></a>執行個體成員和共用的成員

當您從類別建立物件時，會產生該類別的執行個體。 未使用 [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) 關鍵字宣告的成員是「執行個體成員」，它們完全屬於該特定執行個體。 一個執行個體中的執行個體成員，與同一個類別的另一個執行個體中相同的成員無關。 例如，執行個體成員變數可以在不同執行個體中具有不同的值。

使用 `Shared` 關鍵字宣告的成員是「共用的成員」，它們屬於整個類別，而不屬於任何特定執行個體。 共用的成員只會存在一次，而不論您為它的類別建立了多少個執行個體，或者，即使您未建立任何執行個體也一樣。 例如，共用的成員變數只有一個值，可供可存取該類別的所有程式碼使用。

#### <a name="accessing-nonshared-members"></a>存取非共用的成員

###### <a name="to-access-a-nonshared-member-of-an-object"></a>存取物件的非共用成員

1. 確定物件是從它的類別所建立，並將它指派給物件變數。

   ```vb
   Dim secondForm As New System.Windows.Forms.Form
   ```

2. 在存取成員的陳述式中，在物件變數名稱後面加上「成員存取運算子」(`.`)，然後是成員名稱。

   ```vb
   secondForm.Show()
   ```

#### <a name="accessing-shared-members"></a>存取共用的成員

###### <a name="to-access-a-shared-member-of-an-object"></a>存取物件的共用成員

- 在類別名稱後面加上「成員存取運算子」 (`.`)，然後是成員名稱。 您應一律透過類別名稱直接存取物件的 `Shared` 成員。

   ```vb
   MsgBox("This computer is called " & Environment.MachineName)
   ```

- 如果您已經從類別建立物件，也可以透過物件的變數存取 `Shared` 成員。

### <a name="differences-between-classes-and-modules"></a>類別和模組之間的差異

類別和模組的主要差異是，類別可以具現化為物件，而標準模組不行。 因為只有一個標準模組資料的複本，所以，當您程式的某一部分變更了標準模組中的公用變數時，如果該程式的任何其他部分接著讀取該變數，則會取得相同的值 。 相較之下，每個具現化物件適用的物件資料會個別存在。 另一個差異是，不同於標準模組，類別可以實作介面。

> [!NOTE]
> 將 `Shared` 修飾詞套用到類別成員時，它會與類別本身而不是類別的特定執行個體相關聯。 使用類別名稱直接存取成員，相同方式可用來存取模組成員。

類別和模組也會針對它們的成員使用不同的範圍。 在類別內定義的成員範圍會在類別的特定執行個體內，而且只存在於物件的存留期。 若要從類別外部存取類別成員，您必須使用 *Object*.*Member* 格式的完整名稱。

另一方面，在模組內宣告的成員預設是可公開存取的，而且可由任何可存取該模組的程式碼存取。 這表示，標準模組中的變數是有效的全域變數 (因為您可以在專案中的任何位置看見它們)，並存在於程式的存留期。

## <a name="reusing-classes-and-objects"></a>重複使用類別和物件

物件可讓您宣告變數和程序一次，接著就能在需要時重複使用它們。 例如，如果您想要在應用程式中加入拼字檢查程式，您可以定義所有變數和支援函式來提供拼字檢查功能。 如果您以類別形式建立拼字檢查程式，接著就能藉由加入對已編譯組件的參考，在其他應用程式中重複使用它。 更棒的是，您或許能夠使用其他人已經開發的拼字檢查程式類別來簡化您的一些工作。

[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 提供許多可供使用的元件範例。 下列範例使用 <xref:System> 命名空間中的 <xref:System.TimeZone> 類別。 <xref:System.TimeZone> 提供可讓您擷取目前電腦系統時區相關資訊的成員。

```vb
Public Sub examineTimeZone()
    Dim tz As System.TimeZone = System.TimeZone.CurrentTimeZone
    Dim s As String = "Current time zone is "
    s &= CStr(tz.GetUtcOffset(Now).Hours) & " hours and "
    s &= CStr(tz.GetUtcOffset(Now).Minutes) & " minutes "
    s &= "different from UTC (coordinated universal time)"
    s &= vbCrLf & "and is currently "
    If tz.IsDaylightSavingTime(Now) = False Then s &= "not "
    s &= "on ""summer time""."
    MsgBox(s)
End Sub
```

在上述範例中，第一個 [Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)會宣告 <xref:System.TimeZone> 類型的物件變數，並將 <xref:System.TimeZone.CurrentTimeZone%2A> 屬性所傳回的 <xref:System.TimeZone> 物件指派給它。

## <a name="relationships-among-objects"></a>物件之間的關聯性

物件可以透過數種方式彼此相關。 主要的關聯性種類是「階層式」和「內含項目」。

### <a name="hierarchical-relationship"></a>階層式關聯性

當類別衍生自更基本的類別時，即表示它們具有「階層式關聯性」。 在描述屬於更一般類別的子型別的項目時，類別階層架構就很實用。

在下列範例中，假設您想要定義一種特殊的 <xref:System.Windows.Forms.Button>，其作用就像一般的 <xref:System.Windows.Forms.Button>，但也會公開可反轉前景和背景色彩的方法。

##### <a name="to-define-a-class-is-derived-from-an-already-existing-class"></a>定義衍生自已經存在之類別的類別

1. 使用 [Class 陳述式](../../../../visual-basic/language-reference/statements/class-statement.md)來定義您需要從中建立物件的類別。

   ```vb
   Public Class reversibleButton
   ```

   請確定 `End Class` 陳述式會接在類別中程式碼最後一行的後面。 根據預設，當您輸入 `Class` 陳述式時，整合式開發環境 (IDE) 會自動產生 `End Class`。

2. 在 `Class` 陳述式正後方加上 [Inherits 陳述式](../../../../visual-basic/language-reference/statements/inherits-statement.md)。 指定要從中衍生新類別的類別。

   ```vb
   Inherits System.Windows.Forms.Button
   ```

   您的新類別會繼承由基底類別定義的所有成員。

3. 加入衍生類別所公開之其他成員適用的程式碼。 例如，您可以加入 `reverseColors` 方法，而您的衍生類別可能看起來如下：

   ```vb
   Public Class reversibleButton
       Inherits System.Windows.Forms.Button
           Public Sub reverseColors()
               Dim saveColor As System.Drawing.Color = Me.BackColor
               Me.BackColor = Me.ForeColor
               Me.ForeColor = saveColor
          End Sub
   End Class
   ```

   如果您從 `reversibleButton` 類別建立物件，則它可存取 <xref:System.Windows.Forms.Button> 類別的所有成員，以及 `reverseColors` 方法和您在 `reversibleButton` 上定義的任何其他新成員。

衍生的類別會繼承來自其基礎類別的成員，可讓您在類別階層中進行時增加複雜度。 如需詳細資訊，請參閱[繼承的基本概念](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)。

#### <a name="compiling-the-code"></a>編譯程式碼

確定編譯器可以存取您想要從中衍生新類別的類別。 這可能表示要提供它的完整名稱，如同在上述範例中，或在 [Imports 陳述式 (.NET 命名空間和型別)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)中識別它的命名空間。 如果類別位於不同專案，則您可能需要加入對該專案的參考。 如需詳細資訊，請參閱[管理專案中的參考](/visualstudio/ide/managing-references-in-a-project)。

### <a name="containment-relationship"></a>內含項目關聯性

另一個可讓物件相關聯的方法是「內含項目關係」。 容器物件邏輯上會封裝其他物件。 例如，<xref:System.OperatingSystem> 物件在邏輯上會包含 <xref:System.Version> 物件，這會透過其 <xref:System.OperatingSystem.Version%2A> 屬性傳回。 請注意，容器物件實際上不會包含任何其他物件。

#### <a name="collections"></a>集合

物件內含項目的一個特定型別是由「集合」來代表。 集合是一組可列舉的相似物件。 Visual Basic 支援中的特定語法[每個...下一個陳述式](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)，可讓您逐一查看集合的項目。 此外，集合通常可讓您使用 <xref:Microsoft.VisualBasic.Collection.Item%2A>，依其索引來擷取項目，或者將它們關聯至唯一字串來擷取項目。 比起陣列，集合更容易使用，因為它們讓您不需使用索引，就能新增或移除項目。 由於集合易於使用，因此，通常會用來儲存表單和控制項。

## <a name="related-topics"></a>相關主題

[逐步解說：定義類別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)\
提供如何建立類別的逐步說明。

[多載的屬性和方法](../../../../visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods.md)\
多載屬性和方法

[繼承的基本概念](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)\
涵蓋繼承修飾詞，覆寫方法和屬性、MyClass 及 MyBase。

[物件存留期：如何建立和終結物件](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)\
討論類別執行個體的建立與處置。

[匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)\
描述如何建立和使用匿名型別，讓您不需撰寫資料型別的類別定義，就能建立物件。

[物件初始設定式：具名和匿名類型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)\
討論物件初始設定式，它們可用於透過使用單一運算式來建立具名和匿名型別的執行個體。

[如何：推斷屬性名稱和匿名類型宣告中的類型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)\
說明如何在匿名型別宣告中推斷屬性名稱和型別。 提供成功和失敗的推斷範例。
