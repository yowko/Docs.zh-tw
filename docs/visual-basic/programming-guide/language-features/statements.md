---
title: "Statements in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "variables [Visual Basic], declaring"
  - "colons (:)"
  - "constants, defining"
  - "underlines"
  - "constants, statements"
  - "blue underline"
  - "procedures, statements"
  - "variables [Visual Basic], assigning"
  - "line breaks, in code"
  - "executable statements"
  - "variables [Visual Basic], defining"
  - "statements [Visual Basic], about statements"
ms.assetid: fcfdee1a-82b7-4846-98f7-9ca3f5160089
caps.latest.revision: 30
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 30
---
# Statements in Visual Basic
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中的陳述式是完整的指令。  它可包含關鍵字、運算子、變數、常數及運算式。  每個陳述式分別屬於下列分類的其中一種：  
  
-   **宣告陳述式**：用以命名變數、常數或程序，並且也可以指定資料型別。  
  
-   **可執行的陳述式**：負責啟始動作。  這些陳述式可以呼叫方法或函式，並且可以在整個程式碼區塊內執行迴圈或分支的動作。  可執行的陳述式包括**指派陳述式** \(Assignment Statement\)，用以將值或運算式指派給變數或常數。  
  
 本主題說明每一種分類。  此外，本主題還說明如何將多個陳述式合併到一行，以及如何在多行繼續一個陳述式。  
  
## 宣告陳述式  
 您可以使用宣告陳述式，進行程序、變數、屬性 \(Property\)、陣列及常數的命名和定義。  當您宣告程式設計項目時，也可以定義資料型別、存取層級及範圍。  如需詳細資訊，請參閱[Declared Element Characteristics](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)。  
  
 下列範例包含三種宣告。  
  
 [!code-vb[VbVbalrStatements#80](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/statements_1.vb)]  
  
 第一種宣告為 `Sub` 陳述式。  它會和對應的 `End Sub` 陳述式一起宣告名為 `applyFormat` 的程序。  它也會指定 `applyFormat` 為 `Public`，這表示所有可以參考它的程式碼都可以呼叫它。  
  
 第二種宣告為 `Const` 陳述式，它會宣告常數 `limit`，指定 `Integer` 資料型別及值 33。  
  
 第三種宣告為 `Dim` 陳述式，它會宣告變數 `thisWidget`。  資料型別為特定物件，也就是從 `Widget` 類別建立的物件。  您可以將變數宣告為任何基礎資料型別 \(Elementary Data Type\)，或所使用之應用程式中公開 \(Expose\) 的任何物件型別。  
  
### 初始值  
 執行包含宣告陳述式的程式碼時，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會保留宣告項目所需的記憶體。  如果項目會儲存值，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 就會將該項目初始化為資料型別的預設值。  如需詳細資訊，請參閱 [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md) 中的＜行為＞一節。  
  
 您可以將初始值指派給變數做為宣告的一部分，如下列範例所示。  
  
 [!code-vb[VbVbalrStatements#81](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/statements_2.vb)]  
  
 如果變數是物件變數，當您使用 [New Operator](../../../visual-basic/language-reference/operators/new-operator.md) 關鍵字進行宣告時，可以明確建立物件的類別執行個體，如下列範例所示。  
  
 [!code-vb[VbVbalrStatements#82](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/statements_3.vb)]  
  
 請注意，您在宣告陳述式中所指定的初始值要在執行到宣告陳述式之後，才會指派給變數。  在那之前，變數會包含資料型別的預設值。  
  
## 可執行的陳述式  
 可執行的陳述式會執行動作。  它可以呼叫程序、分支至程式碼中的另一個位置、對數個陳述式執行迴圈，或評估運算式。  指派陳述式 \(Assignment Statement\) 是可執行的陳述式的特殊案例。  
  
 下列範例會使用 `If...Then...Else` 控制結構，依據變數值執行不同的程式碼區塊。  在每一個程式碼區塊內，`For...Next` 迴圈會執行指定的次數。  
  
 [!code-vb[VbVbalrStatements#83](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/statements_4.vb)]  
  
 上述範例中的 `If` 陳述式會檢查參數 `clockwise` 的值。  如果值為 `True`，它會呼叫 `aWidget` 的 `spinClockwise` 方法。  如果值為 `False`，它會呼叫 `aWidget` 的 `spinCounterClockwise` 方法。  `If...Then...Else` 控制結構會以 `End If` 結束。  
  
 每一個區塊內的 `For...Next` 迴圈會呼叫適當的方法數次 \(等於 `revolutions` 參數值\)。  
  
## 指派陳述式  
 指派陳述式會執行指派作業，此作業包含取得指派運算子 \(`=`\) 右邊的值，然後將此值存放在左邊的項目中，如下列範例所示。  
  
 [!code-vb[VbVbalrStatements#73](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/statements_5.vb)]  
  
 在上述範例中，指派陳述式會在變數 `v` 中存放常值 42。  
  
### 適合的程式設計項目  
 指派運算子左邊的程式設計項目必須可以接受和存放值。  這表示此項目必須是非 [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md) 的變數或屬性 \(Property\)，或者必須是陣列元素。  在指派陳述式的內容中，這類項目有時會稱為 *lvalue*，代表「左邊的值」。  
  
 指派運算子右邊的值是由運算式所產生，這個值可以由常值 \(Literal\)、常數、變數、屬性、陣列元素、其他運算式或函式呼叫的任何一項組合所組成。  下列範例將說明這點。  
  
 [!code-vb[VbVbalrStatements#74](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/statements_6.vb)]  
  
 上述範例會將在變數 `y` 中保留的值加入在變數 `z` 中保留的值，再將呼叫傳回的值加入函式 `findResult`。  然後，這個運算式的總值會存放在變數 `x` 中。  
  
### 指派陳述式中的資料型別  
 除了數值以外，指派運算子還會指定 `String` 值，如下列範例所示。  
  
 [!code-vb[VbVbalrStatements#75](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/statements_7.vb)]  
  
 您也可以使用 `Boolean` 常值或 `Boolean` 運算式指定 `Boolean` 值，如下列範例所示。  
  
 [!code-vb[VbVbalrStatements#76](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/statements_8.vb)]  
  
 同樣地，可以將適當的值指定給 `Char`、`Date` 或 `Object` 資料型別的程式設計項目。  也可以將物件執行個體 \(Instance\) 指定給項目，該項目會宣告為從中建立該執行個體的類別。  
  
### 複合指派陳述式  
 「*複合指派陳述式*」\(Compound Assignment Statement\) 在將運算式指定給程式設計項目之前，會先在運算式上執行作業。  下列範例會說明其中一個運算子 `+=`，藉由右邊運算式的值遞增運算子左邊的變數值。  
  
 [!code-vb[VbVbalrStatements#77](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/statements_9.vb)]  
  
 上述範例會加 1 至 `n` 值，然後在 `n` 中存放該新值。  它是與下列陳述式相等的速寫法：  
  
 [!code-vb[VbVbalrStatements#78](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/statements_10.vb)]  
  
 可使用此類型的運算子來執行各種複合式指派運算。  如需這些運算子的清單和它們的詳細資訊，請參閱[Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md)。  
  
 串連指派運算子 \(`&=`\) 對於將字串加入已存在字串的結尾來說非常有用，如下列範例所示。  
  
 [!code-vb[VbVbalrStatements#79](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/statements_11.vb)]  
  
### 指派陳述式中的型別轉換  
 指定給變數、屬性或陣列元素的值必須是適合該目的項目中的資料型別。  一般而言，您應該嘗試產生與該目的項目相同之資料型別的值。  不過，某些型別可在指派期間轉換為其他型別。  
  
 如需在資料型別之間轉換的詳細資訊，請參閱 [Type Conversions in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)。  簡單地說，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會自動將提供的型別值轉換為它擴展的其他型別。  「*擴展轉換*」\(Widening Conversion\) 一定會在執行階段順利完成，並且不會遺失任何資料。  例如，因為 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 將 `Integer` 擴展至 `Double`，因此會在適用時將 `Integer` 值轉換為 `Double`。  如需詳細資訊，請參閱[Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。  
  
 「*縮小轉換*」\(Narrowing Conversion\) \(不是擴展的轉換\) 在執行階段會帶來失敗的風險，或造成資料遺失。  您可以使用型別轉換函式明確地執行縮小轉換，或者設定 `Option Strict Off`，將編譯器 \(Compiler\) 導向為隱含地執行所有轉換。  如需詳細資訊，請參閱[Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)。  
  
## 在一行上放置多個陳述式  
 您可以用冒號 \(`:`\) 字元分隔，在單行上撰寫多個陳述式。  下列範例將說明這點。  
  
 [!code-vb[VbVbalrStatements#70](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/statements_12.vb)]  
  
 儘管有時候很方便，但是此形式的語法會使您的程式碼難以閱讀及維護。  因此，建議您維持一行一個陳述式。  
  
## 在多行上繼續一個陳述式  
 陳述式通常會撰寫在一行上，但是當太長時，您可以使用行接續字元 \(Line\-Continuation Character\) 在下一行繼續該陳述式，行接續字元是由底線字元 \(`_`\) 之後接著歸位字元 \(Carriage Return\) 所組成。  在下列範例中，會在兩行上繼續 `MsgBox` 可執行的陳述式。  
  
 [!code-vb[VbVbalrStatements#71](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/statements_13.vb)]  
  
### 隱含行接續  
 在許多情況下，您可以將陳述式接續到下一個連續行而不必使用底線字元 \(\_\)。  下表列出將陳述式隱含接續到下一行程式碼的語法項目。  
  
|||  
|-|-|  
|語法項目|範例|  
|在逗號 \(`,`\) 之後。|[!code-vb[VbVbalrLineContinuation#1](../../../visual-basic/programming-guide/language-features/codesnippet/visualbasic/statements_14.vb)]|  
|在左括號 \(`(`\) 之後，或在右括號 \(`)`\) 之前。|[!code-vb[VbVbalrLineContinuation#2](../../../visual-basic/programming-guide/language-features/codesnippet/visualbasic/statements_15.vb)]|  
|在左大括號 \(`{`\) 之後，或在右大括號 \(`}`\) 之前。|[!code-vb[VbVbalrLineContinuation#3](../../../visual-basic/programming-guide/language-features/codesnippet/visualbasic/statements_16.vb)]<br /><br /> 如需詳細資訊，請參閱[Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)或[Collection Initializers](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)。|  
|於 XML 常值內，在左內嵌運算式 \(`<%=`\) 之後，或在右內嵌運算式 \(`%>`\) 之前。|[!code-vb[VbVbalrLineContinuation#4](../../../visual-basic/programming-guide/language-features/codesnippet/visualbasic/statements_17.vb)]<br /><br /> 如需詳細資訊，請參閱 [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)。|  
|在串連運算子 \(`&`\) 之後。|[!code-vb[VbVbcnConventions#9](../../../visual-basic/programming-guide/language-features/codesnippet/visualbasic/statements_18.vb)]<br /><br /> 如需詳細資訊，請參閱[Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)。|  
|在指派運算子 \(`=`、`&=`、`:=`、`+=`、`-=`、`*=`、`/=`、`\=`、`^=`、`<<=`、`>>=`\) 之後。|[!code-vb[VbVbalrLineContinuation#5](../../../visual-basic/programming-guide/language-features/codesnippet/visualbasic/statements_19.vb)]<br /><br /> 如需詳細資訊，請參閱[Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)。|  
|於運算式內，在二元運算子 \(`+`, `-`、`/`、`*`、`Mod`、`<>`、`<`、`>`、`<=`、`>=`、`^`、`>>`、`<<`、`And`、`AndAlso`、`Or`、`OrElse`、`Like`、`Xor`\) 之後。|[!code-vb[VbVbalrLineContinuation#7](../../../visual-basic/programming-guide/language-features/codesnippet/visualbasic/statements_20.vb)]<br /><br /> 如需詳細資訊，請參閱[Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)。|  
|在 `Is` 和 `IsNot` 運算子之後。|[!code-vb[VbVbalrLineContinuation#8](../../../visual-basic/programming-guide/language-features/codesnippet/visualbasic/statements_21.vb)]<br /><br /> 如需詳細資訊，請參閱[Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)。|  
|在成員限定詞字元 \(`.`\) 之後以及在成員名稱之前。  不過，當您使用 `With` 陳述式或在初始設定清單中提供型別的值時，必須包含行接續字元 \(\_\)，後面接著成員限定詞字元。  使用 `With` 陳述式或物件初始設定清單時，可以考慮在指派 \(Assignment\) 運算子 \(例如，`=`\) 之後分行。|[!code-vb[VbVbalrLineContinuation#5](../../../visual-basic/programming-guide/language-features/codesnippet/visualbasic/statements_19.vb)]<br />[!code-vb[VbVbalrLineContinuation#14](../../../visual-basic/programming-guide/language-features/codesnippet/visualbasic/statements_22.vb)]<br /><br /> 如需詳細資訊，請參閱 [With...End With Statement](../../../visual-basic/language-reference/statements/with-end-with-statement.md) 或[Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)。|  
|在 XML 軸屬性限定詞 \(`.` 或 `.@` 或 `...`\) 之後。  不過，當您使用 `With` 關鍵字時，如果指定成員限定詞，則必須包含行接續字元 \(\_\)。|[!code-vb[VbVbalrLineContinuation#9](../../../visual-basic/programming-guide/language-features/codesnippet/visualbasic/statements_23.vb)]<br /><br /> 如需詳細資訊，請參閱 [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)。|  
|指定屬性時，在小於符號 \(\<\) 之後，或者在大於符號 \(`>`\) 之前。  也可以在您指定屬性時，在大於符號 \(`>`\) 之後。  不過，當您指定組件層級或模組層級的屬性時，必須包括行接續字元 \(\_\)。|[!code-vb[VbVbalrLineContinuation#10](../../../visual-basic/programming-guide/language-features/codesnippet/visualbasic/statements_24.vb)]<br /><br /> 如需詳細資訊，請參閱 [屬性](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)。|  
|在查詢運算子 \(`Aggregate`、`Distinct`、`From`、`Group By`、`Group Join`、`Join`、`Let`、`Order By`、`Select`、`Skip`、`Skip While`、`Take`、`Take While`、`Where`、`In`、`Into`、`On`、`Ascending` 和 `Descending`\) 之前和之後。  您不可以在由多個關鍵字組成之查詢運算子的關鍵字 \(`Order By`、`Group Join`、`Take While` 和 `Skip While`\) 之間分行。|[!code-vb[VbVbalrLineContinuation#11](../../../visual-basic/programming-guide/language-features/codesnippet/visualbasic/statements_25.vb)]<br /><br /> 如需詳細資訊，請參閱[Queries](../../../visual-basic/language-reference/queries/queries.md)。|  
|於 `For Each` 陳述式中，在 `In` 關鍵字之後。|[!code-vb[VbVbalrLineContinuation#12](../../../visual-basic/programming-guide/language-features/codesnippet/visualbasic/statements_26.vb)]<br /><br /> 如需詳細資訊，請參閱 [For Each...Next 陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md)。|  
|於集合初始設定式中，在 `From` 關鍵字之後。|[!code-vb[VbVbalrLineContinuation#13](../../../visual-basic/programming-guide/language-features/codesnippet/visualbasic/statements_27.vb)]<br /><br /> 如需詳細資訊，請參閱 [Collection Initializers](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)。|  
  
## 加入註解  
 來源程式碼不一定是自我闡明的，甚至於對撰寫來源程式碼的程式設計人員而言亦是如此。  因此，為了協助記錄程式碼文件，大部分的程式設計人員都會大量利用內嵌註解。  程式碼中的註解可以為稍後要閱讀或編寫程序或特定指令的使用者，提供說明。  由於編譯期間 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會忽略註解，因此註解並不會影響編譯的程式碼。  
  
 註解行是以所有格符號 \(`'`\) 或 `REM` 做為開頭，後面接著一個空格。  它們可以加在程式碼的任何一處，但字串除外。  若要將註解附加至陳述式，請在陳述式之後插入所有格符號 \(Apostrophe\) 或在 `REM`，之後接著註解。  註解也可出現在自己的分隔行中。  下列範例為這些可能情況。  
  
 [!code-vb[VbVbalrStatements#72](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/statements_28.vb)]  
  
## 檢查編譯錯誤  
 在輸入一行程式碼之後，如果此行與藍色波浪底線一起出現 \(也會顯示錯誤訊息\)，則表示陳述式中有語法錯誤。  您必須找出陳述式的錯誤 \(例如，藉由查看工作清單，或將滑鼠指標移到錯誤上並閱讀錯誤訊息\) 並更正錯誤。  除非您已修正了程式碼中所有的語法錯誤，否則您的程式將無法正確地編譯成功。  
  
## 相關章節  
  
|||  
|-|-|  
|詞彙|定義|  
|[Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md)|提供涵蓋指派運算子 \(例如，`=`、`*=` 和 `&=`\) 的語言參考網頁連結。|  
|[Operators and Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)|說明如何使用運算子結合項目來產生新的值。|  
|[如何：在程式碼中中斷和合併陳述式](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)|顯示如何將單一陳述式分成多行，以及如何將多個陳述式放置在同一行。|  
|[How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)|顯示如何標記一行程式碼。|