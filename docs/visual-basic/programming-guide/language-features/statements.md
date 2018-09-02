---
title: Visual Basic 中的陳述式
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
ms.openlocfilehash: e66acae5e98d561883f4ad59853dfd862c8ebfee
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43462392"
---
# <a name="statements-in-visual-basic"></a>Visual Basic 中的陳述式

在 Visual Basic 中的陳述式是完整的指示。 它可以包含關鍵字、 運算子、 變數、 常數和運算式。 每個陳述式屬於下列類別之一：

- **宣告陳述式**，其中命名變數、 常數或程序，並也可以指定資料型別。

- **可執行陳述式**，這會起始動作。 這些陳述式可以呼叫方法或函式，並在迴圈或分支的程式碼區塊中。 可執行的陳述式包含**指派陳述式**，其指派給變數或常數的值或運算式。

本主題描述每個類別目錄。 此外，本主題說明如何結合在單一行的多個陳述式以及如何繼續多個線路上的陳述式。

## <a name="declaration-statements"></a>宣告陳述式

您可以使用宣告陳述式命名並定義程序、 變數、 屬性、 陣列和常數。 當您宣告的程式設計項目時，您也可以定義其資料型別、 存取層級和範圍。 如需詳細資訊，請參閱 <<c0> [ 宣告的項目特性](./declared-elements/declared-element-characteristics.md)。

下列範例包含三個宣告。

[!code-vb[VbVbalrStatements#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#80)]

第一個宣告是`Sub`陳述式。 連同其比對`End Sub`陳述式，它會宣告名為的程序`applyFormat`。 它也會指定`applyFormat`是`Public`，這表示它可以參考的任何程式碼可以呼叫它。

第二個宣告都`Const`陳述式，宣告常數`limit`，並指定`Integer`資料型別與 33 的值。

第三個宣告都`Dim`陳述式，宣告變數`thisWidget`。 資料類型的特定物件，也就是從建立物件`Widget`類別。 您可以宣告為任何基礎資料類型，或公開應用程式會將任何物件類型的變數。

### <a name="initial-values"></a>初始值

包含宣告陳述式的程式碼執行時，Visual Basic 會保留宣告的項目所需的記憶體。 如果項目包含的值時，Visual Basic 它初始化為其資料類型的預設值。 如需詳細資訊，請參閱 「 行為 」 中[Dim 陳述式](../../language-reference/statements/dim-statement.md)。

您可以做為其宣告，一部分的變數指派初始值，如下列範例所示。

[!code-vb[VbVbalrStatements#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#81)]

如果變數是物件變數，您可以明確地建立其類別的執行個體時將它宣告使用[New 運算子](../../../visual-basic/language-reference/operators/new-operator.md)關鍵字，如下列範例說明。

[!code-vb[VbVbalrStatements#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#82)]

請注意，您在宣告陳述式中指定的起始值未指派給變數之前執行達到宣告陳述式。 屆時，變數會包含其資料類型的預設值。

## <a name="executable-statements"></a>可執行陳述式

可執行的陳述式執行的動作。 它可以呼叫的程序的程式碼，透過多個陳述式，迴圈中的其他位置的分支，或評估運算式。 在指派陳述式是特殊形式的可執行的陳述式。

下列範例會使用`If...Then...Else`控制結構來執行不同的變數的值為基礎的程式碼區塊。 在程式碼中，每個區塊`For...Next`迴圈執行指定的次數。

[!code-vb[VbVbalrStatements#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#83)]

`If`在上述範例中的陳述式會檢查參數的值`clockwise`。 如果值為`True`，它會呼叫`spinClockwise`方法`aWidget`。 如果值為`False`，它會呼叫`spinCounterClockwise`方法`aWidget`。 `If...Then...Else`控制結構結尾`End If`。

`For...Next`迴圈內每個區塊會呼叫適當的方法數次的值相等`revolutions`參數。

## <a name="assignment-statements"></a>指派陳述式

指派陳述式執行指派作業，包括進行指派運算子右邊的值 (`=`) 並將其儲存在左邊，如下列範例所示的項目中。

[!code-vb[VbVbalrStatements#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#73)]

在上述範例中，指派陳述式會儲存在變數中的常值 42 `v`。

### <a name="eligible-programming-elements"></a>符合資格的程式設計項目

指派運算子左邊的程式設計項目必須能夠接受並儲存值。 這表示它必須是變數或屬性不是[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)，或者它必須是陣列元素。 在指派陳述式的內容，這類項目有時稱為*左值*，如 「 左值 」。

運算式，其中可包含的任何組合的常值、 常數、 變數、 屬性、 陣列元素、 其他運算式或函式呼叫會產生指派運算子右邊的值。 下列範例將說明這點。

[!code-vb[VbVbalrStatements#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#74)]

上述範例會將變數的值`y`保留在變數中的值`z`，然後將函式的呼叫所傳回的值`findResult`。 此運算式的合計值接著會儲存在變數`x`。

### <a name="data-types-in-assignment-statements"></a>指派陳述式中的資料類型

除了數字的值，指派運算子也可以指派`String`值，如下列範例所示。

[!code-vb[VbVbalrStatements#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#75)]

您也可以指派`Boolean`值，使用`Boolean`常值或`Boolean`運算式，如下列範例說明。

[!code-vb[VbVbalrStatements#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#76)]

同樣地，您可以將適當的值指派的程式設計項目`Char`， `Date`，或`Object`資料型別。 您也可以宣告為該執行個體建立類別的項目指派物件執行個體。

### <a name="compound-assignment-statements"></a>複合指派陳述式

*複合指派陳述式*第一次執行的運算式，再將它指派至程式設計項目上的作業。 下列範例說明其中一個運算子， `+=`，其中遞增運算子的左邊變數的值，右邊的運算式的值。

[!code-vb[VbVbalrStatements#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#77)]

上述範例中的值增加 1 `n`，然後將儲存在該新值`n`。 它是速記相當於下列陳述式：

[!code-vb[VbVbalrStatements#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#78)]

使用此類型的運算子可以執行各種不同的複合指派運算。 如需這些運算子和其相關的詳細資訊，請參閱[指派運算子](../../../visual-basic/language-reference/operators/assignment-operators.md)。

串連指派運算子 (`&=`) 可用於將字串新增至已有的結束字串，如下列範例所示。

[!code-vb[VbVbalrStatements#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#79)]

### <a name="type-conversions-in-assignment-statements"></a>在指派陳述式的類型轉換

您將指派給變數、 屬性或陣列元素的值必須是適用於該目的項目資料型別。 一般情況下，您應該嘗試產生相同的資料類型的目的地元素的值。 不過，某些型別可以在指派期間轉換成其他類型。

如需有關資料類型之間轉換，請參閱[Visual Basic 中的型別轉換](./data-types/type-conversions.md)。 簡單地說，Visual Basic 會自動將指定型別的值轉換成它所擴展的任何其他類型。 A*擴展轉換*是一種，總是在執行階段成功，而且不會遺失任何資料。 例如，轉換 Visual Basic`Integer`值加入`Double`適當的時候，因為`Integer`可擴展為`Double`。 如需詳細資訊，請參閱 [Widening and Narrowing Conversions](./data-types/widening-and-narrowing-conversions.md)。

*縮小轉換*（其會未擴展） 執行的執行階段失敗或資料遺失的風險。 您可以使用類型轉換函式，明確地執行縮小轉換，或您可以指示編譯器會隱含地執行所有轉換，藉由設定`Option Strict Off`。 如需詳細資訊，請參閱 <<c0> [ 隱含和明確轉換](./data-types/implicit-and-explicit-conversions.md)。

## <a name="putting-multiple-statements-on-one-line"></a>將多個陳述式放在同一行

您可以有多個陳述式以分號分隔的單行 (`:`) 字元。 下列範例將說明這點。

[!code-vb[VbVbalrStatements#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#70)]

雖然有時候很方便，這種形式的語法可讓您的程式碼難以閱讀和維護。 因此，建議您保留至行的一個陳述式。

## <a name="continuing-a-statement-over-multiple-lines"></a>多個線路上繼續陳述式

陳述式通常適合在同一行，但它太長時，可以繼續到下一行使用行接續序列，其中包含空格，後面接著底線字元 (`_`) 後面接著歸位字元。 在下列範例中，`MsgBox`超過兩行繼續執行可執行的陳述式。

[!code-vb[VbVbalrStatements#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#71)]

### <a name="implicit-line-continuation"></a>隱含行接續符號

在許多情況下，您可以繼續陳述式在下一步 的連續行不使用底線字元 (`_`)。 下列語法元素會隱含地繼續下一行程式碼陳述式。

- 在逗號之後 (`,`)。 例如: 

   [!code-vb[VbVbalrLineContinuation#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#1)]

- 之後的左括號 (`(`) 或右括弧之前 (`)`)。 例如: 

   [!code-vb[VbVbalrLineContinuation#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#2)]

- 在開啟的大括號之後 (`{`) 或右大括號之前 (`}`)。 例如: 

    [!code-vb[VbVbalrLineContinuation#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#3)]

    如需詳細資訊，請參閱 <<c0> [ 物件初始設定式： 具名和匿名型別](./objects-and-classes/object-initializers-named-and-anonymous-types.md)或是[集合初始設定式](./collection-initializers/index.md)。

- 在開啟之後內嵌運算式 (`<%=`) 或內嵌運算式的結束前 (`%>`) 在 XML 常值。 例如: 

   [!code-vb[VbVbalrLineContinuation#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#4)]

   如需詳細資訊，請參閱 < [XML 中內嵌的運算式](./xml/embedded-expressions-in-xml.md)。

- 串連運算子後面 (`&`)。 例如: 

   [!code-vb[VbVbcnConventions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/vb/Class1.vb#9)]

   如需詳細資訊，請參閱 <<c0> [ 依功能排列運算子](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)。

- 之後指派運算子 (`=`， `&=`， `:=`， `+=`， `-=`， `*=`， `/=`， `\=`， `^=`， `<<=`， `>>=`)。 例如: 

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   如需詳細資訊，請參閱 <<c0> [ 依功能排列運算子](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)。

- 在二元運算子 (`+`， `-`， `/`， `*`， `Mod`， `<>`， `<`， `>`， `<=`， `>=`， `^`， `>>`，`<<`， `And`， `AndAlso`， `Or`， `OrElse`， `Like`， `Xor`) 在運算式內。 例如: 

   [!code-vb[VbVbalrLineContinuation#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#7)]

   如需詳細資訊，請參閱 <<c0> [ 依功能排列運算子](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)。

- 在後`Is`和`IsNot`運算子。 例如: 

   [!code-vb[VbVbalrLineContinuation#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#8)]

   如需詳細資訊，請參閱 <<c0> [ 依功能排列運算子](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)。

- 成員的限定詞字元之後 (`.`) 和成員名稱前面。 例如: 

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   不過，您必須包含行接續字元 (`_`) 下列成員的限定詞字元，當您使用`With`陳述式，或提供類型的初始化清單中的值。 請考慮將該行之後指派運算子 (例如`=`) 當您使用`With`陳述式或物件初始設定清單。 例如: 

   [!code-vb[VbVbalrLineContinuation#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#14)]

   如需詳細資訊，請參閱[與...With...end With 陳述式](../../../visual-basic/language-reference/statements/with-end-with-statement.md)或是[物件初始設定式： 具名和匿名型別](./objects-and-classes/object-initializers-named-and-anonymous-types.md)。

- XML 軸屬性辨識符號之後 (`.`或是`.@`或`...`)。 不過，您必須包含行接續字元 (`_`) 當您指定成員的限定詞當您使用`With`關鍵字。 例如: 

   [!code-vb[VbVbalrLineContinuation#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#9)]

   如需詳細資訊，請參閱 < [XML 軸屬性](../../../visual-basic/language-reference/xml-axis/index.md)。

- 之後較低位符號 (<) 或大於之前-符號 (`>`) 時，您可指定屬性。 也之後大於-符號 (`>`) 時，您可指定屬性。 不過，您必須包含行接續字元 (`_`) 時，您可指定組件層級或模組層級的屬性。 例如: 

   [!code-vb[VbVbalrLineContinuation#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#10)]

   如需詳細資訊，請參閱 <<c0> [ 屬性概觀](../../../visual-basic/programming-guide/concepts/attributes/index.md)。

- 之前和之後的查詢運算子 (`Aggregate`， `Distinct`， `From`， `Group By`， `Group Join`， `Join`， `Let`， `Order By`， `Select`， `Skip`， `Skip While`， `Take`， `Take While`， `Where`， `In`， `Into`， `On`， `Ascending`，及`Descending`)。 您無法中斷程式之間的多個關鍵字的查詢運算子關鍵字 (`Order By`， `Group Join`， `Take While`，和`Skip While`)。 例如: 

   [!code-vb[VbVbalrLineContinuation#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#11)]

   如需詳細資訊，請參閱 <<c0> [ 查詢](../../../visual-basic/language-reference/queries/index.md)。

- 在後`In`中的關鍵字`For Each`陳述式。 例如: 

   [!code-vb[VbVbalrLineContinuation#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#12)]

   如需詳細資訊，請參閱[每個...下一個陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md)。

- 之後`From`集合初始設定式中的關鍵字。 例如: 

   [!code-vb[VbVbalrLineContinuation#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#13)]

   如需詳細資訊，請參閱[集合初始設定式](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)。

## <a name="adding-comments"></a>加入註解

原始程式碼並不一定一目了然，甚至進行的程式設計人員撰寫它。 因此，為了幫助他們的程式碼的文件，大部分的程式設計人員請自由使用內嵌的註解。 在程式碼中的註解可以說明的程序或任何人都能讀取或更新版本使用的特定指示。 Visual Basic 會忽略註解在編譯期間，並不會影響已編譯的程式碼。

註解行開頭所有格符號 (`'`) 或`REM`後接空格。 它們可以是在任一處加入程式碼中，除了字串內。 若要將註解附加至陳述式中，插入一個單引號或`REM`之後的陳述式，後面接著註解。 註解也可以在自己的個別行上移。 下列範例會示範這些可能性。

[!code-vb[VbVbalrStatements#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#72)]

## <a name="checking-compilation-errors"></a>檢查的編譯錯誤

如果在輸入程式碼行之後，列會顯示藍色波浪底線 （可能會出現錯誤訊息以及），則陳述式中有語法錯誤。 您必須了解的陳述式的錯誤 （藉由查看工作清單中，或將滑鼠游標停留於滑鼠指標的錯誤和讀取的錯誤訊息），並加以更正。 直到您修正所有的語法錯誤程式碼中，您的程式將無法正確編譯。

## <a name="related-sections"></a>相關章節

|詞彙|定義|
|---|---|
|[指派運算子](../../../visual-basic/language-reference/operators/assignment-operators.md)|提供涵蓋指派運算子，例如語言參考頁面連結`=`， `*=`，和`&=`。|
|[運算子和運算式](./operators-and-expressions/index.md)|示範如何結合以產生新值的運算子中的項目。|
|[操作說明：在程式碼內中斷和合併陳述式](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)|示範如何在單一陳述式分成多行，以及如何將多個陳述式放在同一行。|
|[操作說明：標記陳述式](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)|示範如何標記一行程式碼。|
