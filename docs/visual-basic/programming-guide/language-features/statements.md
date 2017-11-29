---
title: "Visual Basic 中的陳述式"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 210637105e54244ba829dabd73feab0b43ec7c6c
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="statements-in-visual-basic"></a>Visual Basic 中的陳述式
中的陳述式[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]是完整的指示。 它可以包含關鍵字、 運算子、 變數、 常數和運算式。 每個陳述式屬於下列類別之一：  
  
-   **宣告陳述式**，命名變數、 常數或程序，以及也可以指定資料類型。  
  
-   **可執行陳述式**，其中起始動作。 這些陳述式可以呼叫的方法或函式，也可以執行迴圈或分支執行的程式碼區塊。 可執行的陳述式包含**指派陳述式**，其指派給變數或常數的值或運算式。  
  
 本主題描述每個類別目錄。 此外，本主題說明如何結合在單一行的多個陳述式，以及如何繼續於多行陳述式。  
  
## <a name="declaration-statements"></a>宣告陳述式  
 您可以使用宣告陳述式即可命名和程序、 變數、 屬性、 陣列和常數定義。 當您宣告程式設計項目時，您也可以定義其資料類型、 存取層級，以及範圍。 如需詳細資訊，請參閱[宣告項目特性](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)。  
  
 下列範例包含三個宣告。  
  
 [!code-vb[VbVbalrStatements#80](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_1.vb)]  
  
 第一個宣告為`Sub`陳述式。 連同其比對`End Sub`陳述式，它會宣告名為程序`applyFormat`。 它也會指定`applyFormat`是`Public`，這表示它可以參考任何程式碼可以呼叫它。  
  
 第二個宣告都是`Const`陳述式，宣告常數`limit`，並指定`Integer`資料類型和值為 33。  
  
 第三個宣告都是`Dim`陳述式，宣告變數`thisWidget`。 資料類型的特定物件，也就是從建立物件`Widget`類別。 您可以宣告為任何基礎資料類型或公開應用程式會將任何物件類型的變數。  
  
### <a name="initial-values"></a>初始值  
 包含宣告陳述式的程式碼執行時，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]會保留宣告的項目所需的記憶體。 如果項目會保存一個值，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]其初始化為其資料類型的預設值。 如需詳細資訊，請參閱 「 行為 」 [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)。  
  
 如下列範例所示，您可以指派一個初始值做為其宣告，一部分的變數。  
  
 [!code-vb[VbVbalrStatements#81](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_2.vb)]  
  
 如果變數是物件變數，您可以明確地建立其類別的執行個體時將它宣告使用[New 運算子](../../../visual-basic/language-reference/operators/new-operator.md)關鍵字，如下列範例說明。  
  
 [!code-vb[VbVbalrStatements#82](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_3.vb)]  
  
 請注意，您在宣告陳述式中指定的起始值未指派給變數之前執行到它的宣告陳述式。 這段時間，直到變數會包含其資料類型的預設值。  
  
## <a name="executable-statements"></a>可執行陳述式  
 可執行的陳述式執行的動作。 它可以呼叫的程序程式碼中，數個陳述式，透過迴圈中的其他位置的分支，或評估運算式。 指派陳述式是可執行的陳述式的特殊案例。  
  
 下列範例會使用`If...Then...Else`控制結構來執行不同的變數的值為基礎的程式碼區塊。 中的程式碼中，每個區塊`For...Next`迴圈就會執行指定的次數。  
  
 [!code-vb[VbVbalrStatements#83](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_4.vb)]  
  
 `If`在上述範例中的陳述式會檢查參數的值`clockwise`。 如果值為`True`，它會呼叫`spinClockwise`方法`aWidget`。 如果值為`False`，它會呼叫`spinCounterClockwise`方法`aWidget`。 `If...Then...Else`控制結構結尾`End If`。  
  
 `For...Next`迴圈內每個區塊呼叫適當的方法數次的值等於`revolutions`參數。  
  
## <a name="assignment-statements"></a>指派陳述式  
 指派陳述式執行設定作業，包括進行設定運算子右邊的值 (`=`) 並將其儲存在左邊，如下列範例所示的項目中。  
  
 [!code-vb[VbVbalrStatements#73](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_5.vb)]  
  
 在上述範例中，指派陳述式會儲存在變數中的常值 42 `v`。  
  
### <a name="eligible-programming-elements"></a>合格的程式設計項目  
 指派運算子左邊的程式設計項目必須是可以接受和儲存的值。 這表示它必須是變數或屬性不是[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)，或必須是陣列項目。 在指派陳述式的內容，這類項目有時稱為*左值*，如 「 左值 」。  
  
 指派運算子右邊的值是運算式，這個運算式可以包含常值、 常數、 變數、 屬性、 陣列元素、 其他運算式或函式呼叫的任何組合所產生的。 下列範例將說明這點。  
  
 [!code-vb[VbVbalrStatements#74](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_6.vb)]  
  
 上述範例中將保留在變數中的值加入`y`保留在變數中的值`z`，然後將函數呼叫所傳回的值`findResult`。 此運算式的合計值會儲存在變數中`x`。  
  
### <a name="data-types-in-assignment-statements"></a>指派陳述式中的資料類型  
 除了數字的值，指派運算子也可以指派`String`值，如下列範例所示。  
  
 [!code-vb[VbVbalrStatements#75](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_7.vb)]  
  
 您也可以指派`Boolean`值，使用`Boolean`常值或`Boolean`運算式，如下列範例說明。  
  
 [!code-vb[VbVbalrStatements#76](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_8.vb)]  
  
 同樣地，您可以指派適當的值的程式設計項目`Char`， `Date`，或`Object`資料型別。 您也可以為該執行個體建立的類別宣告的項目指派物件執行個體。  
  
### <a name="compound-assignment-statements"></a>複合指派陳述式  
 *複合指派陳述式*第一次執行作業之前將其指派至程式設計項目運算式上的。 下列範例說明其中一個運算子，`+=`的遞增運算子左邊的變數值，右運算式的值。  
  
 [!code-vb[VbVbalrStatements#77](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_9.vb)]  
  
 上述範例中將值加 1 `n`，然後將儲存在該新值`n`。 它是速記相當於下列陳述式：  
  
 [!code-vb[VbVbalrStatements#78](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_10.vb)]  
  
 使用此類型的運算子可以執行各種不同的複合指派作業。 如需這些運算子的詳細資訊，請參閱[指派運算子](../../../visual-basic/language-reference/operators/assignment-operators.md)。  
  
 串連指派運算子 (`&=`) 可用於將字串新增至現有的結尾字串，如下列範例所示。  
  
 [!code-vb[VbVbalrStatements#79](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_11.vb)]  
  
### <a name="type-conversions-in-assignment-statements"></a>在指派陳述式的型別轉換  
 您指派給變數、 屬性或陣列元素的值必須是適用於該目的項目資料類型。 一般情況下，您應該嘗試產生相同的資料類型的目的地元素的值。 不過，某些型別可以在指派期間轉換成其他類型。  
  
 如需轉換資料類型資訊，請參閱[在 Visual Basic 中的型別轉換](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)。 簡單地說，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]會自動將特定類型的值轉換為它所擴展的其他任何類型。 A*擴展轉換*是中，一律會在執行階段會成功，而不會遺失任何資料。 例如，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]轉換`Integer`值設定為`Double`適合的因為`Integer`可擴展為`Double`。 如需詳細資訊，請參閱 [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。  
  
 *縮小轉換*（即未擴展） 執行的執行階段失敗或資料遺失的風險。 您可以使用類型轉換函式，明確地執行縮小轉換，或您可以指示編譯器隱含地執行所有轉換，藉由設定`Option Strict Off`。 如需詳細資訊，請參閱[隱含和明確轉換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)。  
  
## <a name="putting-multiple-statements-on-one-line"></a>將多個陳述式放在同一行  
 您可以在單一行，以冒號分隔多個陳述式 (`:`) 字元。 下列範例將說明這點。  
  
 [!code-vb[VbVbalrStatements#70](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_12.vb)]  
  
 有時候很方便，但這種形式的語法可讓您的程式碼難以讀取與維護。 因此，建議您保持為一行一個陳述式。  
  
## <a name="continuing-a-statement-over-multiple-lines"></a>繼續透過多行陳述式  
 陳述式通常是適合在同一行，但太長時，可以繼續到下一行使用行接續序列，其中包含空格，後面接著底線字元 (`_`) 後面接著歸位字元。 在下列範例中，`MsgBox`可執行陳述式會繼續在兩行。  
  
 [!code-vb[VbVbalrStatements#71](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_13.vb)]  
  
### <a name="implicit-line-continuation"></a>隱含行接續符號  
 在許多情況下，您可以繼續在下一個連續行陳述式而不使用底線字元 (_)。 下表列出以隱含方式繼續下一行程式碼中的 陳述式的語法元素。  
  
|語法元素|範例|  
|---|---|  
|在逗號之後 (`,`)。|[!code-vb[VbVbalrLineContinuation#1](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_14.vb)]|  
|在左括號之後 (`(`) 或右括號之前 (`)`)。|[!code-vb[VbVbalrLineContinuation#2](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_15.vb)]|  
|在左大括號之後 (`{`) 或右大括號之前 (`}`)。|[!code-vb[VbVbalrLineContinuation#3](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_16.vb)]<br /><br /> 如需詳細資訊，請參閱[物件初始設定式： 具名和匿名類型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)或[集合初始設定式](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)。|  
|在開啟之後內嵌運算式 (`<%=`) 或內嵌運算式的關閉之前 (`%>`) 內 XML 常值。|[!code-vb[VbVbalrLineContinuation#4](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_17.vb)]<br /><br /> 如需詳細資訊，請參閱[XML 中內嵌的運算式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)。|  
|串連運算子後面 (`&`)。|[!code-vb[VbVbcnConventions#9](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_18.vb)]<br /><br /> 如需詳細資訊，請參閱[功能所列出運算子](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)。|  
|在指派運算子之後 (`=`， `&=`， `:=`， `+=`， `-=`， `*=`， `/=`， `\=`， `^=`， `<<=`， `>>=`)。|[!code-vb[VbVbalrLineContinuation#5](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_19.vb)]<br /><br /> 如需詳細資訊，請參閱[功能所列出運算子](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)。|  
|二元運算子之後 (`+`， `-`， `/`， `*`， `Mod`， `<>`， `<`， `>`， `<=`， `>=`， `^`， `>>`，`<<`， `And`， `AndAlso`， `Or`， `OrElse`， `Like`， `Xor`) 在運算式中。|[!code-vb[VbVbalrLineContinuation#7](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_20.vb)]<br /><br /> 如需詳細資訊，請參閱[功能所列出運算子](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)。|  
|之後`Is`和`IsNot`運算子。|[!code-vb[VbVbalrLineContinuation#8](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_21.vb)]<br /><br /> 如需詳細資訊，請參閱[功能所列出運算子](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)。|  
|成員的辨識符號字元之後 (`.`) 和成員名稱前面。 不過，您必須包含下列成員限定詞字元，當您使用行接續字元 (_)`With`陳述式或提供的類型初始設定清單中的值。 請考慮將行之後，指派運算子 (例如， `=`) 當您使用`With`陳述式或物件初始設定清單。|[!code-vb[VbVbalrLineContinuation#5](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_19.vb)]<br />[!code-vb[VbVbalrLineContinuation#14](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_22.vb)]<br /><br /> 如需詳細資訊，請參閱[與...With 陳述式](../../../visual-basic/language-reference/statements/with-end-with-statement.md)或[物件初始設定式： 具名和匿名類型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)。|  
|XML 軸屬性辨識符號之後 (`.`或`.@`或`...`)。 不過，您必須包含行接續字元 (_) 當您使用時，指定成員限定詞`With`關鍵字。|[!code-vb[VbVbalrLineContinuation#9](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_23.vb)]<br /><br /> 如需詳細資訊，請參閱[XML 軸屬性](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)。|  
|之後小於-符號 (<) 或大於之前-符號 (`>`) 時，您可指定屬性。 也之後大於-符號 (`>`) 時，您可指定屬性。 不過，您必須在指定組件層級或模組層級屬性時，包含行接續字元 (_)。|[!code-vb[VbVbalrLineContinuation#10](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_24.vb)]<br /><br /> 如需詳細資訊，請參閱[屬性概觀](../../../visual-basic/programming-guide/concepts/attributes/index.md)。|  
|查詢運算子的前後 (`Aggregate`， `Distinct`， `From`， `Group By`， `Group Join`， `Join`， `Let`， `Order By`， `Select`， `Skip`， `Skip While`， `Take`， `Take While`， `Where`， `In`， `Into`， `On`， `Ascending`，和`Descending`)。 您無法中斷組成的多個關鍵字的查詢運算子關鍵字之間的分隔線 (`Order By`， `Group Join`， `Take While`，和`Skip While`)。|[!code-vb[VbVbalrLineContinuation#11](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_25.vb)]<br /><br /> 如需詳細資訊，請參閱[查詢](../../../visual-basic/language-reference/queries/queries.md)。|  
|之後`In`關鍵字`For Each`陳述式。|[!code-vb[VbVbalrLineContinuation#12](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_26.vb)]<br /><br /> 如需詳細資訊，請參閱[每個...下一個陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md)。|  
|之後`From`集合初始設定式中的關鍵字。|[!code-vb[VbVbalrLineContinuation#13](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_27.vb)]<br /><br /> 如需詳細資訊，請參閱[集合初始設定式](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)。|  
  
## <a name="adding-comments"></a>加入註解  
 原始碼不一定一目了然，甚至將它撰寫的程式設計人員。 若要協助說明其程式碼，因此，大部分的程式設計人員請盡量使用內嵌的註解。 在程式碼中的註解可以說明的程序或特定的指令，以便讀取或更新版本使用它的任何人。 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]在編譯期間，會忽略註解，並不會影響已編譯的程式碼。  
  
 以單引號開始註解行 (`'`) 或`REM`後接空格。 能夠新增任何位置中的程式碼，除了在字串內。 若要將註解附加至陳述式中，插入一個單引號或`REM`之後的陳述式，後面接著註解。 註解也可以自己的個別行上移。 下列範例會示範這些可能性。  
  
 [!code-vb[VbVbalrStatements#72](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_28.vb)]  
  
## <a name="checking-compilation-errors"></a>檢查編譯錯誤  
 如果在輸入一行程式碼之後，藍色波浪底線 （可能會出現錯誤訊息以及） 就會顯示線條、 陳述式中沒有語法錯誤。 您必須了解有哪些陳述式的錯誤 （藉由查看工作清單中，或將滑鼠游標停留於滑鼠指標的錯誤並讀取錯誤訊息），並加以更正。 直到您在程式碼中修正所有的語法錯誤，您的程式將無法正確編譯。  
  
## <a name="related-sections"></a>相關章節  
  
|詞彙|定義|  
|---|---|  
|[指派運算子](../../../visual-basic/language-reference/operators/assignment-operators.md)|提供了涵蓋指派運算子，例如語言參考頁面連結`=`， `*=`，和`&=`。|  
|[運算子和運算式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)|示範如何使用以產生新值的運算子結合項目。|  
|[操作說明：在程式碼內中斷和合併陳述式](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)|示範如何在單一陳述式分成多行，以及如何將多個陳述式放在同一行。|  
|[操作說明：標記陳述式](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)|示範如何標示程式碼行。|
