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
ms.openlocfilehash: f63f0f0212913f95baab2a8a43c4b7f25a859cd9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400887"
---
# <a name="statements-in-visual-basic"></a>Visual Basic 中的陳述式

Visual Basic 中的語句是一個完整的指令。 它可以包含關鍵字、運算子、變數、常量和運算式。 每個語句都屬於以下類別之一：

- **聲明語句**，用於命名變數、常量或過程，也可以指定資料類型。

- **可執行語句**，啟動操作。 這些語句可以調用方法或函數，並且它們可以迴圈或分支代碼塊。 可執行語句包括**設定陳述式**，用於將值或運算式分配給變數或常量。

本主題介紹每個類別。 此外，本主題還介紹如何在一行上組合多個語句，以及如何在多行上繼續語句。

## <a name="declaration-statements"></a>宣告陳述式

使用聲明語句命名和定義過程、變數、屬性、陣列和常量。 聲明程式設計元素時，還可以定義其資料類型、存取層級和範圍。 有關詳細資訊，請參閱[聲明的元素特徵](./declared-elements/declared-element-characteristics.md)。

下面的示例包含三個聲明。

[!code-vb[VbVbalrStatements#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#80)]

第一個聲明是`Sub`語句。 與其匹配`End Sub`語句一起，它聲明名為 的過程`applyFormat`。 它還指定 是`applyFormat``Public`，這意味著任何可以引用它的代碼都可以調用它。

第二個聲明是`Const`語句，它聲明常量`limit`，指定`Integer`資料類型和值 33。

第三個聲明是`Dim`語句，它聲明變數`thisWidget`。 資料類型是特定物件，即從`Widget`類創建的物件。 可以將變數聲明為任何基本資料類型或正在使用的應用程式中公開的任何物件類型。

### <a name="initial-values"></a>初始值

當包含聲明語句的代碼運行時，Visual Basic 保留聲明元素所需的記憶體。 如果元素包含一個值，Visual Basic 會將其初始化為其資料類型的預設值。 有關詳細資訊，請參閱[Dim 語句](../../language-reference/statements/dim-statement.md)中的"行為"。

您可以為其聲明的一部分為變數分配初始值，如下例所示。

[!code-vb[VbVbalrStatements#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#81)]

如果變數是物件變數，則可以在使用[New 運算子](../../../visual-basic/language-reference/operators/new-operator.md)關鍵字聲明其類時顯式創建其類的實例，如下例所示。

[!code-vb[VbVbalrStatements#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#82)]

請注意，在執行到達其聲明語句之前，聲明語句中指定的初始值不會分配給變數。 在此之前，變數包含其資料類型的預設值。

## <a name="executable-statements"></a>可執行語句

可執行語句執行操作。 它可以調用過程、分支到代碼中的另一個位置、逐一查看多個語句或計算運算式。 設定陳述式是可執行語句的特殊情況。

下面的示例使用`If...Then...Else`控制項結構根據變數的值運行不同的代碼塊。 在每個代碼塊中，迴圈`For...Next`運行指定的次數。

[!code-vb[VbVbalrStatements#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#83)]

上`If`例中的語句檢查 參數`clockwise`的值 。 如果值為`True`，則調用`spinClockwise`方法`aWidget`。 如果值為`False`，則調用`spinCounterClockwise`方法`aWidget`。 控制`If...Then...Else`結構以`End If`結尾。

每個`For...Next`塊中的迴圈調用適當的方法的次數等於`revolutions`參數的值。

## <a name="assignment-statements"></a>分配語句

分配語句執行賦值操作，其中包括獲取指派運算子 （`=`） 右側的值並將其存儲在左側的元素中，如以下示例所示。

[!code-vb[VbVbalrStatements#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#73)]

在前面的示例中，設定陳述式在變數`v`中存儲文本值 42。

### <a name="eligible-programming-elements"></a>合格的程式設計元素

指派運算子左側的程式設計元素必須能夠接受並存儲值。 這意味著它必須是一個變數或屬性，它不是[ReadOnly，](../../../visual-basic/language-reference/modifiers/readonly.md)或者它必須是陣列元素。 在設定陳述式的上下文中，此類元素有時稱為*lvalue，* 表示為"左值"。

指派運算子右側的值由運算式生成，運算式可以由文本、常量、變數、屬性、陣列元素、其他運算式或函式呼叫的任意組合組成。 下列範例將說明這點。

[!code-vb[VbVbalrStatements#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#74)]

前面的示例將變數`y`中持有的值添加到變數`z`中的值，然後添加調用 函數 返回的值。 `findResult` 然後，此運算式的總值存儲在變數`x`中。

### <a name="data-types-in-assignment-statements"></a>設定陳述式中的資料類型

除了數值之外，指派運算子還可以分配`String`值，如下例所示。

[!code-vb[VbVbalrStatements#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#75)]

您還可以使用`Boolean`文本或`Boolean`運算式`Boolean`分配值，如下例所示。

[!code-vb[VbVbalrStatements#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#76)]

同樣，您可以為`Char`的程式設計元素分配適當的值，`Date`或`Object`資料類型的程式設計元素。 還可以將物件實例分配給聲明為創建該實例的類的元素。

### <a name="compound-assignment-statements"></a>複合設定陳述式

*複合設定陳述式*首先對運算式執行操作，然後再將其分配給程式設計元素。 下面的示例說明了這些運算子之一 ，`+=`該運算子將運算子左側變數的值由右側運算式的值遞增。

[!code-vb[VbVbalrStatements#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#77)]

前面的示例將 1 添加到`n`的值，然後將新值存儲在 中。 `n` 它是以下語句的速記等效項：

[!code-vb[VbVbalrStatements#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#78)]

可以使用此類運算子執行各種複合賦值操作。 有關這些運算子的清單及其的詳細資訊，請參閱[分配運算子](../../../visual-basic/language-reference/operators/assignment-operators.md)。

串聯指派運算子 （`&=`） 可用於將字串添加到現有字串的末尾，如下例所示。

[!code-vb[VbVbalrStatements#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#79)]

### <a name="type-conversions-in-assignment-statements"></a>在分配語句中鍵入轉換

分配給變數、屬性或陣列元素的值必須為適合該目標元素的資料類型。 通常，應嘗試生成與目標元素相同的資料類型的值。 但是，某些類型可以在分配期間轉換為其他類型的類型。

有關資料類型之間轉換的資訊，請參閱[視覺化基本 中的"類型轉換](./data-types/type-conversions.md)"。 簡而言之，Visual Basic 會自動將給定類型的值轉換為它擴展到的任何其他類型。 *加寬轉換*是始終在運行時成功且不會丟失任何資料的轉換。 例如，Visual `Integer` Basic 將值轉換為適當`Double`值，因為`Integer`範圍將擴大為`Double`。 如需詳細資訊，請參閱 [Widening and Narrowing Conversions](./data-types/widening-and-narrowing-conversions.md)。

*縮小轉換*（未擴大的轉換）有在運行時失敗或資料丟失的風險。 您可以使用類型轉換函數顯式執行縮小轉換，也可以通過設置`Option Strict Off`來指示編譯器隱式執行所有轉換。 有關詳細資訊，請參閱[隱式和顯式轉換](./data-types/implicit-and-explicit-conversions.md)。

## <a name="putting-multiple-statements-on-one-line"></a>將多個語句放在一行上

單行上的多個語句由冒號 （`:`） 字元分隔。 下列範例將說明這點。

[!code-vb[VbVbalrStatements#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#70)]

雖然偶爾方便，但這種語法形式使代碼難以閱讀和維護。 因此，建議您將一個語句保留為一行。

## <a name="continuing-a-statement-over-multiple-lines"></a>在多行上繼續語句

語句通常適合一行，但當太長時，可以使用行延續序列將其延續到下一行上，該序列由空格後跟底線 （`_`） 後跟回車符組成。 在下面的示例中，`MsgBox`可執行語句在兩行上繼續。

[!code-vb[VbVbalrStatements#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#71)]

### <a name="implicit-line-continuation"></a>隱式行延續

在許多情況下，您可以在下一條連續行上繼續語句，而無需使用底線 （`_`。 以下語法元素隱式地繼續下一行代碼上的語句。

- 逗號後 （`,`。 例如：

   [!code-vb[VbVbalrLineContinuation#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#1)]

- 開放括弧後 （`(`） 或關閉括弧之前 （`)`） 例如：

   [!code-vb[VbVbalrLineContinuation#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#2)]

- 打開大括弧 （`{`） 後或關閉大括弧 （`}`） 之前。 例如：

    [!code-vb[VbVbalrLineContinuation#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#3)]

    有關詳細資訊，請參閱[物件初始化器：命名和匿名型別](./objects-and-classes/object-initializers-named-and-anonymous-types.md)或[集合初始化器](./collection-initializers/index.md)。

- 在 XML 文本中`<%=`打開的嵌入運算式 （ ） 之後`%>`或嵌入運算式 （ ） 關閉之前。 例如：

   [!code-vb[VbVbalrLineContinuation#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#4)]

   有關詳細資訊，請參閱[XML 中的嵌入式運算式](./xml/embedded-expressions-in-xml.md)。

- 串聯運算子後 （`&`。 例如：

   [!code-vb[VbVbcnConventions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/vb/Class1.vb#9)]

   有關詳細資訊，請參閱[按功能列出的運算子](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)。

- 分配運算子後`=`（、 `:=` `&=` `+=`、 `-=` `*=`、 `/=` `\=`、 `^=` `<<=`、 `>>=`、 、 、 、 、 、 、 、 例如：

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   有關詳細資訊，請參閱[按功能列出的運算子](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)。

- After binary operators (`+`, `-`, `/`, `*`, `Mod`, `<>`, `<`, `>`, `<=`, `>=`, `^`, `>>`, `<<`, `And`, `AndAlso`, `Or`, `OrElse`, `Like`, `Xor`) within an expression. 例如：

   [!code-vb[VbVbalrLineContinuation#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#7)]

   有關詳細資訊，請參閱[按功能列出的運算子](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)。

- 和`Is``IsNot`運算子之後。 例如：

   [!code-vb[VbVbalrLineContinuation#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#8)]

   有關詳細資訊，請參閱[按功能列出的運算子](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)。

- 在成員限定詞之後`.`（ ） 和成員名稱之前。 例如：

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   但是，當您在類型的初始化清單中使用語句或`_`提供值時，`With`必須在成員限定詞字元之後包含行延續字元 （ ）。 使用`=``With`語句或物件初始化清單時，請考慮在指派運算子（例如）之後中斷行。 例如：

   [!code-vb[VbVbalrLineContinuation#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#14)]

   有關詳細資訊，請參閱[...結尾與語句](../../../visual-basic/language-reference/statements/with-end-with-statement.md)或[物件初始化器：命名和匿名型別](./objects-and-classes/object-initializers-named-and-anonymous-types.md)。

- 在 XML 軸屬性限定`.`符`.@` `...`（ 或 ） 之後。 但是，在使用 關鍵字時指定成員限定詞`_`時，`With`必須包含行延續字元 （ ）。 例如：

   [!code-vb[VbVbalrLineContinuation#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#9)]

   有關詳細資訊，請參閱[XML 軸屬性](../../../visual-basic/language-reference/xml-axis/index.md)。

- 指定屬性時，小於符號 （<） 後或大於符號 （`>`） 之前。 指定屬性時，在大於符號`>`（ ） 之後。 但是，在指定裝配體級或模組層級屬性`_`時，必須包含一個線延續字元 （ 。 例如：

   [!code-vb[VbVbalrLineContinuation#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#10)]

   有關詳細資訊，請參閱[屬性概述](../../../visual-basic/programming-guide/concepts/attributes/index.md)。

- 查詢運算子（、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、`Aggregate` `Distinct` `From` `Group By` `Group Join` `Join` `Let` `Order By` `Select` `Skip` `Skip While` `Take` `Take While` `Where` `In` `Into` `On` `Ascending` `Descending` 不能在`Order By`由多個關鍵字 （、、`Group Join``Take While`和`Skip While`） 組成的查詢運算子的關鍵字之間換行。 例如：

   [!code-vb[VbVbalrLineContinuation#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#11)]

   有關詳細資訊，請參閱[查詢](../../../visual-basic/language-reference/queries/index.md)。

- 語句中的`In``For Each`關鍵字之後。 例如：

   [!code-vb[VbVbalrLineContinuation#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#12)]

   有關詳細資訊，請參閱[每個...下一個語句](../../../visual-basic/language-reference/statements/for-each-next-statement.md).

- 在`From`集合初始化器中的關鍵字之後。 例如：

   [!code-vb[VbVbalrLineContinuation#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#13)]

   如需詳細資訊，請參閱[集合初始設定式](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)。

## <a name="adding-comments"></a>添加注釋

原始程式碼並不總是不言自明的，即使是編寫原始程式碼的程式師也是如此。 因此，為了説明記錄他們的代碼，大多數程式師都自由使用嵌入式注釋。 代碼中的注釋可以向以後閱讀或使用它的人解釋過程或特定指令。 Visual Basic 在編譯過程中忽略注釋，它們不會影響編譯的代碼。

注釋行以撇號開頭或`'``REM`後跟空格。 它們可以添加到代碼中的任意位置，但字串中除外。 若要在語句上附加注釋，請插入撇號或`REM`語句後，然後插入注釋。 注釋也可以單獨行。 下面的示例演示了這些可能性。

[!code-vb[VbVbalrStatements#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#72)]

## <a name="checking-compilation-errors"></a>檢查編譯錯誤

如果在鍵入一行代碼後，行以波浪藍色底線顯示（也可能顯示錯誤訊息），則語句中存在語法錯誤。 您必須找出該語句的問題所在（通過查看工作清單，或用滑鼠指標懸停在錯誤上並讀取錯誤消息），並更正它。 在修復代碼中的所有語法錯誤之前，程式將無法正確編譯。

## <a name="related-sections"></a>相關章節

|詞彙|定義|
|---|---|
|[指派運算子](../../../visual-basic/language-reference/operators/assignment-operators.md)|提供指向語言參考頁的連結，這些頁涵蓋賦`=`值`*=`運算子（`&=`如 ）和 。|
|[運算子和運算式](./operators-and-expressions/index.md)|演示如何將元素與運算子組合以生成新值。|
|[操作說明：在程式碼內中斷和合併陳述式](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)|演示如何將單個語句分成多行，以及如何在同一行上放置多個語句。|
|[操作說明：標記陳述式](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)|演示如何標記程式碼。|
