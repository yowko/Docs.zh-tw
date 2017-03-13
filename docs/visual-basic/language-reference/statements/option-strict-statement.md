---
title: "Option Strict Statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Strict"
  - "vb.OptionStrict"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Strict keyword"
  - "Option Strict statement"
  - "conversions, implicit"
  - "late binding"
  - "implicit conversions"
ms.assetid: 5883e0c1-a920-4274-8e46-b0ff047eaee5
caps.latest.revision: 49
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 49
---
# Option Strict Statement
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

限制隱含資料類型轉換，只擴大轉換，不允許後期繫結，也不允許導致 `Object`類型的隱含類型化。  
  
## 語法  
  
```  
Option Strict { On | Off }  
```  
  
## 組件  
  
|||  
|-|-|  
|詞彙|定義|  
|`On`|選擇項。  啟用 `Option Strict` 檢查。|  
|`Off`|選擇項。  停用 `Option Strict` 檢查。|  
  
## 備註  
 當 `Option Strict On` 或 `Option Strict` 在檔案中出現時，下列情況將造成編譯時期錯誤：  
  
-   隱含 Narrowing 轉換  
  
-   晚期繫結  
  
-   造成 `Object`類型的隱含類型化  
  
> [!NOTE]
>  在您可以於 [專案設計工具、編譯頁 \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic) 設定的警告組態中，有三種設定對應三個條件，會導致編譯時期錯誤。  如需關於如何使用這些設定的資訊，請參閱本主題後續的[若要在 IDE 中設定警告組態](../../../visual-basic/language-reference/statements/option-strict-statement.md#conditions)。  
  
 `Option Strict Off` 陳述式會關閉全部三個條件的錯誤和警告檢查，即使相關聯的 IDE 設定指定要開啟這些錯誤或警告，也是如此。  `Option Strict On`陳述式開啟錯誤及警告檢查所有的三個條件，即使相關聯的 IDE 設定可指定要關閉這些錯誤或警告。  
  
 如果使用，則 `Option Strict` 陳述式必須出現在檔案中的任何其他程式碼陳述式之前。  
  
 當您設定`Option Strict`到`On`，Visual Basic檢查資料型別所指定的所有程式設計項目。  指定明確的或是使用區域別推斷來指定資料型別。  指定的所有程式設計項目資料型別建議，原因如下：  
  
-   讓 IntelliSense 能夠支援變數和參數。  這能讓您在輸入程式碼時看到其屬性及其他成員。  
  
-   讓編譯器能夠執行型別檢查。  型別檢查將協助您找到可能會在執行階段因為型別轉換錯誤而失敗的陳述式。  這也能夠識別在不支援這些方法的物件上所進行的方法呼叫。  
  
-   它能加速程式碼執行。  一個理由是如果您未指定資料類型程式設計項目的，Visual Basic的編譯器將`Object`型別。   已編譯的程式碼可能要轉換前或往後之間`Object`及其他資料型別，這會降低效能。  
  
## 隱含 Narrowing 轉換錯誤  
 隱含資料類型轉換是 Narrowing 轉換時，會發生隱含 Narrowing 轉換錯誤。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 可以將許多資料型別轉換為其他資料型別。  當某個資料型別的值轉換為精確度較差或容量較小的資料型別時，可能會發生資料流失。  如果這類「縮小轉換」 失敗，就會發生執行階段錯誤。  `Option Strict` 確保這些縮小轉換的編譯時期通知，這樣即可避免這些轉換。  如需詳細資訊，請參閱 [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)和 [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。  
  
 可能導致錯誤的轉換包括發生於在運算式中的隱含轉換。  如需詳細資訊，請參閱下列主題：  
  
-   [\+ Operator](../../../visual-basic/language-reference/operators/addition-operator.md)  
  
-   [\+\= Operator](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
  
-   [\\ Operator](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
  
-   [\/\= Operator](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
  
-   [Char Data Type](../../../visual-basic/language-reference/data-types/char-data-type.md)  
  
 當您使用 [& Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md) 串連字串時，對字串的所有轉換都被視為擴展轉換。  因此，這些轉換不會產生隱含 Narrowing 轉換錯誤，即使開啟 `Option Strict` 也一樣。  
  
 當您呼叫引數資料型別與對應參數不同的方法時，如果 `Option Strict` 為開啟狀態，則縮小轉換會造成編譯時期錯誤。  您可以使用擴展轉換或明確轉換，避免編譯時期錯誤。  
  
 從 `For Each…Next` 集合中的項目轉換至迴圈控制變數時，會在轉換編譯時隱藏 Narrowing 轉換錯誤。  即使 `Option Strict` 為開啟狀態，還是會發生這種情況。  如需詳細資訊，請參閱[For Each...Next 陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md)中的〈Narrowing 轉換〉一節。  
  
## 後期繫結錯誤  
 物件被指派給宣告類型為 `Object` 之變數的屬性或方法時，為晚期繫結物件。  如需詳細資訊，請參閱 [Early and Late Binding](../../../visual-basic/programming-guide/language-features/early-late-binding/early-and-late-binding.md)。  
  
## 隱含物件類型錯誤  
 無法推斷宣告變數的適當類型，因此推斷`Object`類型時，會發生隱含物件類型錯誤。  這主要是發生在您使用 `Dim` 陳述式宣告變數而未使用 `As` 子句，並且 `Option Infer` 已設為關閉的時候。  如需詳細資訊，請參閱[Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md)和 [Visual Basic Language Specification](../../../visual-basic/reference/language-specification.md)。  
  
 若為方法參數，如果 `Option Strict` 是 off，則 `As` 子句是選擇性的。  然而，如果任一參數會使用 `As` 子句，則所有參數就必須使用它。  如果`Option Strict` 是 on，則每個參數定義都要有 `As`子句。  
  
 如果您宣告變數而未使用`As`子句，並且將其設定為`Nothing`，則該變數的類型會是`Object`.  `Option Strict` 和`Option Infer`皆為 on 時，沒有發生編譯時期錯誤。  其中一個範例是`Dim something = Nothing`。  
  
### 預設資料型別及值  
 下表說明各種在 [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md) 中指定資料型別與初始設定式之組合的結果。  
  
|||||  
|-|-|-|-|  
|資料型別已指定？|是否已指定初始設定式？|範例|結果|  
|否|否|`Dim qty`|如果 `Option Strict` 關閉 \(預設值\)，則變數會設定為 `Nothing`。<br /><br /> 如果 `Option Strict` 開啟，則會發生編譯時期錯誤。|  
|否|是|`Dim qty = 5`|如果 `Option Infer` 開啟 \(預設值\)，則變數會使用初始設定式的資料型別。  請參閱 [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。<br /><br /> 如果 `Option Infer` 關閉且 `Option Strict` 關閉，則變數會使用 `Object` 的資料型別。<br /><br /> 如果 `Option Infer` 關閉而 `Option Strict` 開啟，則會發生編譯時期錯誤。|  
|是|否|`Dim qty As Integer`|變數會初始化為資料型別的預設值。  如需詳細資訊，請參閱 [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)。|  
|是|是|`Dim qty  As Integer = 5`|如果初始設定式的資料型別無法轉換為指定的資料型別，就會發生編譯時期錯誤。|  
  
## 當 Option Strict 陳述式不存在時  
 如果原始程式碼不包含 `Option Strict` 陳述式，則會使用 [專案設計工具、編譯頁 \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic) 上的 \[**Option Strict**\] 設定。  \[**編譯頁**\] 含有的設定可在產生錯誤的條件之外提供其他控制項。  
  
 如果您使用命令列編譯器，則可以使用[\/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)編譯器選項指定`Option Strict`的設定。  
  
### 若要在 IDE 中設定 Option Strict  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
1.  在 \[**方案總管**\] 中選取專案。  在 \[**專案**\] 功能表上，按一下 \[**屬性**\]。  如需詳細資訊，請參閱[Introduction to the Project Designer](http://msdn.microsoft.com/zh-tw/898dd854-c98d-430c-ba1b-a913ce3c73d7)。  
  
2.  在 \[**編譯**\] 索引標籤上，設定 \[**Option Strict**\] 方塊中的值。  
  
###  <a name="conditions"></a> 若要在 IDE 中設定警告組態  
 當您使用[專案設計工具、編譯頁 \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic) 而不是 `Option Strict` 陳述式時，您也可以對產生錯誤的條件進行其他控制。  \[**編譯**\] 頁的 \[**警告組態**\] 區段中所包含的設定對應三個會在 `Option Strict` 設為開啟時導致編譯時期錯誤的條件。  以下是這些設定：  
  
-   **隱含轉換**  
  
-   **後期繫結；叫用可能會在執行階段失敗**  
  
-   **隱含類型；假定物件**  
  
 當您將 \[**Option Strict**\] 設定為 \[**開啟**\] 時，這三個警告組態設定都會設定為 \[**錯誤**\]。  當您將 \[**Option Strict**\] 設定為 \[**關閉**\] 時，所有三個設定都會設定為 \[**無**\]。  
  
 您可以將每個警告組態個別變更為 \[**無**\]、\[**警告**\] 或 \[**錯誤**\]。  如果三個警告組態設定皆設為 \[**錯誤**\]，`On`會出現在`Option strict`方塊中。  如果三個都設為 \[**無**\]，此方塊中會出現  `Off`。  若為這些設定的其他任何組合，會出現 \[**\(自訂\)**\]。  
  
### 若要設定新專案的 Option Strict 預設設定  
 當您建立專案時，\[**編譯**\] 索引標籤上的 \[**Option Strict**\] 設定會設定為 \[**選項**\] 對話方塊中的 \[**Option Strict**\] 設定。  
  
 若要在這個對話方塊中設定 `Option Strict`，請按一下 \[**工具**\] 功能表上的 \[**選項**\]。  在 \[**選項**\] 對話方塊中，展開 \[**專案和方案**\]，然後按一下 \[**VB 預設值**\]。  \[**VB 預設值**\] 中的初始預設設定是 `Off`。  
  
### 若要在命令列上設定 Option Strict  
 在 **vbc** 命令中包含 [\/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) 編譯器選項。  
  
## 範例  
 下列範例示範縮小轉換的隱含型別轉換所造成的編譯時期錯誤。  這個錯誤分類對應至 \[**編譯**\] 頁上的 \[**隱含轉換**\] 條件。  
  
 [!code-vb[VbVbalrStatements#161](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_1.vb)]  
  
## 範例  
 下列範例示範晚期繫結造成的編譯時期錯誤。  這個錯誤分類對應至 \[**編譯**\] 頁上的 \[**晚期繫結，執行階段時呼叫可能失敗**\] 條件。  
  
 [!code-vb[VbVbalrStatements#162](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_2.vb)]  
  
## 範例  
 下列範例示範由 `Object` 隱含型別宣告的變數所造成的錯誤。  這個錯誤分類對應至 \[**編譯**\] 頁上的 \[**隱含型別，假設是 Object**\] 條件。  
  
 [!code-vb[VbVbalrStatements#163](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_3.vb)]  
  
 [!code-vb[VbVbalrStatements#164](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_4.vb)]  
  
## 請參閱  
 [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [專案設計工具、編譯頁 \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic)   
 [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [How to: Access Members of an Object](../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)   
 [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)   
 [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)   
 [Office 方案中的晚期繫結](/office-dev/office-dev/late-binding-in-office-solutions)   
 [\/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)   
 [選項對話方塊、專案、Visual Basic 預設值](/visual-studio/ide/reference/visual-basic-defaults-projects-options-dialog-box)