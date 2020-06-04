---
title: 陳述式
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], declaring
- colons (:) [Visual Basic]
- constants [Visual Basic], defining
- underlines
- constants [Visual Basic], statements
- blue underline [Visual Basic]
- procedures [Visual Basic], statements
- variables [Visual Basic], assigning
- line breaks [Visual Basic], in code
- executable statements [Visual Basic]
- variables [Visual Basic], defining
- statements [Visual Basic], about statements
ms.assetid: fcfdee1a-82b7-4846-98f7-9ca3f5160089
ms.openlocfilehash: 09fe53f4bc2b6d025b762c6595c5337263456bae
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401975"
---
# <a name="statements-in-visual-basic"></a>Visual Basic 中的陳述式

Visual Basic 中的語句是完整的指示。 它可以包含關鍵字、運算子、變數、常數和運算式。 每個語句屬於下列其中一個類別：

- 宣告**語句**，它會將變數、常數或程式命名為，而且也可以指定資料類型。

- **可執行檔語句**，會起始動作。 這些語句可以呼叫方法或函式，也可以透過程式碼區塊來迴圈或分支。 可執行檔語句包含指派**語句**，可將值或運算式指派給變數或常數。

本主題描述每個類別目錄。 此外，本主題描述如何將多個語句結合在同一行上，以及如何繼續執行多行語句。

## <a name="declaration-statements"></a>宣告陳述式

您可以使用宣告語句來命名和定義程式、變數、屬性、陣列和常數。 當您宣告程式設計項目時，您也可以定義其資料類型、存取層級和範圍。 如需詳細資訊，請參閱宣告的[元素特性](./declared-elements/declared-element-characteristics.md)。

下列範例包含三個宣告。

[!code-vb[VbVbalrStatements#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#80)]

第一個宣告是 `Sub` 語句。 它與其相符的 `End Sub` 語句一起宣告一個名為的程式 `applyFormat` 。 它也會指定 `applyFormat` 為 `Public` ，這表示任何可以參考它的程式碼都可以呼叫它。

第二個宣告是 `Const` 語句，它會宣告常數 `limit` ，並指定 `Integer` 資料類型和值33。

第三個宣告是 `Dim` 聲明變數的語句 `thisWidget` 。 資料類型是特定的物件，亦即從類別建立的物件 `Widget` 。 您可以將變數宣告為任何基本資料類型或任何在您所使用之應用程式中公開的物件類型。

### <a name="initial-values"></a>初始值

當包含宣告語句的程式碼執行時，Visual Basic 會保留所宣告元素所需的記憶體。 如果元素包含值，Visual Basic 會將它初始化為其資料類型的預設值。 如需詳細資訊，請參閱[Dim 語句](../../language-reference/statements/dim-statement.md)中的「行為」。

您可以將初始值指派給變數，做為其宣告的一部分，如下列範例所示。

[!code-vb[VbVbalrStatements#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#81)]

如果變數是物件變數，當您使用[New Operator](../../language-reference/operators/new-operator.md)關鍵字來宣告它時，可以明確建立其類別的實例，如下列範例所示。

[!code-vb[VbVbalrStatements#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#82)]

請注意，您在宣告語句中指定的初始值不會指派給變數，直到執行達到其宣告語句為止。 在該時間之前，變數會包含其資料類型的預設值。

## <a name="executable-statements"></a>可執行語句

可執行檔語句會執行動作。 它可以呼叫程式、分支至程式碼中的另一個位置、迴圈執行數個語句，或評估運算式。 指派語句是可執行語句的特殊案例。

下列範例會根據 `If...Then...Else` 變數的值，使用控制結構來執行不同的程式碼區塊。 在每個程式碼區塊中， `For...Next` 迴圈會執行指定的次數。

[!code-vb[VbVbalrStatements#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#83)]

`If`上述範例中的語句會檢查參數的值 `clockwise` 。 如果值為 `True` ，則會呼叫的 `spinClockwise` 方法 `aWidget` 。 如果值為 `False` ，則會呼叫的 `spinCounterClockwise` 方法 `aWidget` 。 `If...Then...Else`控制結構的結尾為 `End If` 。

`For...Next`每個區塊內的迴圈會呼叫適當的方法，其次數等於參數的值 `revolutions` 。

## <a name="assignment-statements"></a>指派語句

指派語句會執行指派作業，其中包括接受指派運算子右邊的值（ `=` ），並將其儲存在左側的元素中，如下列範例所示。

[!code-vb[VbVbalrStatements#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#73)]

在上述範例中，指派語句會將常值42儲存在變數中 `v` 。

### <a name="eligible-programming-elements"></a>合格的程式設計項目

指派運算子左邊的程式設計項目必須能夠接受並儲存值。 這表示它必須是不是[唯讀](../../language-reference/modifiers/readonly.md)的變數或屬性，或者必須是陣列元素。 在指派語句的內容中，這類專案有時*稱為左值，適用*于 "left value"。

指派運算子右邊的值是由運算式所產生，它可以包含常值、常數、變數、屬性、陣列元素、其他運算式或函式呼叫的任意組合。 下列範例將說明這點。

[!code-vb[VbVbalrStatements#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#74)]

上述範例會將保留在變數中的值新增 `y` 至變數中所保留的值 `z` ，然後將呼叫所傳回的值加入至函數 `findResult` 。 此運算式的總計值會儲存在變數中 `x` 。

### <a name="data-types-in-assignment-statements"></a>指派語句中的資料類型

除了數值以外，指派運算子也可以指派 `String` 值，如下列範例所示。

[!code-vb[VbVbalrStatements#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#75)]

您也可以 `Boolean` 使用常值或運算式來指派值， `Boolean` `Boolean` 如下列範例所示。

[!code-vb[VbVbalrStatements#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#76)]

同樣地，您可以將適當的值指派給 `Char` 、 `Date` 或 `Object` 資料類型的程式設計項目。 您也可以將物件實例指派給宣告為的專案，而該專案是建立該實例的類別。

### <a name="compound-assignment-statements"></a>複合指派語句

*複合指派語句*會先對運算式執行運算，再將它指派給程式設計項目。 下列範例說明其中一個運算子，這會將 `+=` 運算子左邊的變數值，以右邊運算式的值遞增。

[!code-vb[VbVbalrStatements#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#77)]

上述範例會將1加到的值 `n` ，然後將新的值儲存在中 `n` 。 它是下列語句的簡寫對應項：

[!code-vb[VbVbalrStatements#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#78)]

您可以使用此類型的運算子來執行各種複合指派運算。 如需這些運算子的清單和相關的詳細資訊，請參閱[指派運算子](../../language-reference/operators/assignment-operators.md)。

串連指派運算子（ `&=` ）適用于將字串新增至已經存在的字串結尾，如下列範例所示。

[!code-vb[VbVbalrStatements#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#79)]

### <a name="type-conversions-in-assignment-statements"></a>指派語句中的類型轉換

您指派給變數、屬性或陣列元素的值，必須是適合該目的地元素的資料類型。 一般來說，您應該嘗試產生與目的地元素相同之資料類型的值。 不過，某些類型可在指派期間轉換成其他類型。

如需在資料類型之間轉換的詳細資訊，請參閱[Visual Basic 中的類型轉換](./data-types/type-conversions.md)。 簡單地說，Visual Basic 會自動將指定型別的值轉換成它所擴展的任何其他型別。 *擴輾轉換*是中的一項，在執行時間一律會成功，而且不會遺失任何資料。 例如，Visual Basic 會 `Integer` 在適當時將值轉換為 `Double` ，因為會 `Integer` 擴大為 `Double` 。 如需詳細資訊，請參閱 [Widening and Narrowing Conversions](./data-types/widening-and-narrowing-conversions.md)。

*縮小轉換*（不是擴展的）會在執行時間發生失敗或資料遺失的風險。 您可以使用類型轉換函式來明確地執行縮小轉換，也可以指示編譯器透過設定，以隱含方式執行所有轉換 `Option Strict Off` 。 如需詳細資訊，請參閱[隱含和明確轉換](./data-types/implicit-and-explicit-conversions.md)。

## <a name="putting-multiple-statements-on-one-line"></a>將多個語句放在同一行上

您可以在單一行上有多個語句，並以冒號（ `:` ）字元分隔。 下列範例將說明這點。

[!code-vb[VbVbalrStatements#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#70)]

雖然偶爾很方便，但這種形式的語法會使您的程式碼難以閱讀和維護。 因此，建議您將一個語句保留在一行。

## <a name="continuing-a-statement-over-multiple-lines"></a>繼續執行多行語句

語句通常會放在一行上，但如果太長，您可以使用行接續序列將它繼續放在下一行，這是由空格後面接著底線字元（）後面接著 `_` 一個回車。 在下列範例中， `MsgBox` 可執行檔語句會延續兩行。

[!code-vb[VbVbalrStatements#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#71)]

### <a name="implicit-line-continuation"></a>隱含行接續

在許多情況下，您可以在下一個連續行繼續執行語句，而不需要使用底線字元（ `_` ）。 下列語法元素會隱含地繼續下一行程式碼上的語句。

- 在逗號（ `,` ）之後。 例如：

   [!code-vb[VbVbalrLineContinuation#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#1)]

- 在左括弧（ `(` ）之後或右括弧（）前面 `)` 。 例如：

   [!code-vb[VbVbalrLineContinuation#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#2)]

- 在左大括弧（）之後， `{` 或在右大括弧（ `}` ）之前。 例如：

    [!code-vb[VbVbalrLineContinuation#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#3)]

    如需詳細資訊，請參閱[物件初始化運算式：名稱和匿名型別](./objects-and-classes/object-initializers-named-and-anonymous-types.md)或[集合初始化運算式](./collection-initializers/index.md)。

- 在開啟的內嵌運算式（ `<%=` ）之後，或在 XML 常值中的內嵌運算式（）的結尾之前 `%>` 。 例如：

   [!code-vb[VbVbalrLineContinuation#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#4)]

   如需詳細資訊，請參閱[XML 中的內嵌運算式](./xml/embedded-expressions-in-xml.md)。

- 在串連運算子（ `&` ）之後。 例如：

   [!code-vb[VbVbcnConventions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/vb/Class1.vb#9)]

   如需詳細資訊，請參閱[依功能列出的運算子](../../language-reference/operators/operators-listed-by-functionality.md)。

- 指派運算子之後（ `=` 、、、、、、、、、 `&=` `:=` `+=` `-=` `*=` `/=` `\=` `^=` `<<=` 、 `>>=` ）。 例如：

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   如需詳細資訊，請參閱[依功能列出的運算子](../../language-reference/operators/operators-listed-by-functionality.md)。

- 在二元運算子（、、、、、、、、、、、、、、、、、、 `+` `-` `/` `*` `Mod` `<>` `<` `>` `<=` ）之後 `>=` `^` `>>` `<<` `And` `AndAlso` `Or` `OrElse` `Like` `Xor` 的運算式中。 例如：

   [!code-vb[VbVbalrLineContinuation#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#7)]

   如需詳細資訊，請參閱[依功能列出的運算子](../../language-reference/operators/operators-listed-by-functionality.md)。

- 在 `Is` 和 `IsNot` 運算子之後。 例如：

   [!code-vb[VbVbalrLineContinuation#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#8)]

   如需詳細資訊，請參閱[依功能列出的運算子](../../language-reference/operators/operators-listed-by-functionality.md)。

- 在成員辨識符號字元（ `.` ）之後和成員名稱之前。 例如：

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   不過， `_` 當您使用 `With` 語句或在類型的初始化清單中提供值時，您必須在成員限定詞字元後面加上行接續字元（）。 `=`當您使用 `With` 語句或物件初始化清單時，請考慮中斷指派運算子後面的那一行（例如，）。 例如：

   [!code-vb[VbVbalrLineContinuation#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#14)]

   如需詳細資訊，請參閱[With .。。結尾為語句](../../language-reference/statements/with-end-with-statement.md)或[物件初始化運算式：名稱和匿名型別](./objects-and-classes/object-initializers-named-and-anonymous-types.md)。

- 在 XML 軸屬性辨識符號（ `.` 或 `.@` 或 `...` ）之後。 不過，當您 `_` 使用關鍵字時，當您指定成員限定詞時，必須包含行接續字元（） `With` 。 例如：

   [!code-vb[VbVbalrLineContinuation#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#9)]

   如需詳細資訊，請參閱[XML 軸屬性](../../language-reference/xml-axis/index.md)。

- 當您指定屬性時，小於符號（<）或大於符號（）的前面 `>` 。 `>`當您指定屬性時，也會在大於符號（）之後。 不過， `_` 當您指定元件層級或模組層級的屬性時，必須包含行接續字元（）。 例如：

   [!code-vb[VbVbalrLineContinuation#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#10)]

   如需詳細資訊，請參閱[屬性總覽](../concepts/attributes/index.md)。

- 在查詢運算子之前和之後（、、、、、、、、、、、、、、、、、 `Aggregate` `Distinct` `From` `Group By` `Group Join` `Join` `Let` `Order By` `Select` `Skip` `Skip While` `Take` `Take While` `Where` `In` `Into` `On` `Ascending` 和 `Descending` ）。 您不能在由多個關鍵字（ `Order By` 、 `Group Join` 、 `Take While` 和）組成之查詢運算子的關鍵字之間分隔一行 `Skip While` 。 例如：

   [!code-vb[VbVbalrLineContinuation#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#11)]

   如需詳細資訊，請參閱[查詢](../../language-reference/queries/index.md)。

- `In`語句中的關鍵字之後 `For Each` 。 例如：

   [!code-vb[VbVbalrLineContinuation#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#12)]

   如需詳細資訊，請參閱[For Each .。。下一個語句](../../language-reference/statements/for-each-next-statement.md)。

- `From`在集合初始化運算式中的關鍵字之後。 例如：

   [!code-vb[VbVbalrLineContinuation#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#13)]

   如需詳細資訊，請參閱[集合初始設定式](collection-initializers/index.md)。

## <a name="adding-comments"></a>新增註解

原始程式碼並不一定一目了然，即使是撰寫程式碼的程式設計人員也一樣。 為了協助記錄其程式碼，大部分程式設計人員會大量使用內嵌的批註。 程式碼中的批註可以向稍後閱讀或使用的任何人解釋程式或特定指示。 Visual Basic 會在編譯期間忽略批註，而不會影響已編譯的程式碼。

批註行開頭為單引號（ `'` ）或 `REM` 後面接著一個空格。 它們可以加入程式碼中的任何位置，但不包括在字串中。 若要將批註附加至語句，請在語句後面插入一個單引號或 `REM` 之後，然後再加上批註。 批註也可以單獨放在自己的一行。 下列範例示範這些可能性。

[!code-vb[VbVbalrStatements#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#72)]

## <a name="checking-compilation-errors"></a>檢查編譯錯誤

如果您在輸入一行程式碼之後，以波浪式藍色底線顯示行（也可能出現錯誤訊息），則語句中會發生語法錯誤。 您必須找出語句的問題（方法是在 [工作清單] 中查看，或將滑鼠指標停留在錯誤上方並閱讀錯誤訊息）並加以更正。 在您已修正程式碼中的所有語法錯誤之前，您的程式將無法正確編譯。

## <a name="related-sections"></a>相關章節

|詞彙|定義|
|---|---|
|[指派運算子](../../language-reference/operators/assignment-operators.md)|提供涵蓋指派運算子（例如、和）之語言參考頁面的連結 `=` `*=` `&=` 。|
|[運算子和運算式](./operators-and-expressions/index.md)|示範如何結合元素與運算子來產生新的值。|
|[作法：程式碼中的 Break 及 Combine 陳述式](../program-structure/how-to-break-and-combine-statements-in-code.md)|說明如何將單一語句分成多行，以及如何將多個語句放在同一行。|
|[作法：Label 陳述式](../program-structure/how-to-label-statements.md)|示範如何為程式程式碼加上標籤。|
