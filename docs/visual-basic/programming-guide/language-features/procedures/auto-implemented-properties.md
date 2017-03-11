---
title: "Auto-Implemented Properties (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.AutoProperty"
  - "vb.AutoImplementedProperty"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "properties [Visual Basic], auto-implemented"
  - "properties, auto-implemented [Visual Basic]"
  - "auto-implemented properties [Visual Basic]"
ms.assetid: 5c669f0b-cf95-4b4e-ae84-9cc55212ca87
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 20
---
# Auto-Implemented Properties (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

*自動實作屬性*可讓您快速指定類別的屬性，而不需要撰寫程式碼來 `Get` 和 `Set` 屬性。  當您撰寫自動實作屬性之程式碼時，Visual Basic 編譯器會自動建立私用欄位，來存放建立關聯的 `Get` 和 `Set` 程序外，另外存放屬性變數。  
  
 使用自動實作屬性、屬性 \(包括預設值\)，可以在單行中宣告。  下列範例顯示三個屬性宣告。  
  
 [!code-vb[VbVbalrAutoImplementedProperties#1](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/auto-implemented-propert_1_1.vb)]  
  
 自動實作屬性相當於屬性值儲存在私用欄位的屬性。  下列程式碼範例顯示自動實作屬性。  
  
 [!code-vb[VbVbalrAutoImplementedProperties#5](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/auto-implemented-propert_1_2.vb)]  
  
 下列程式碼範例顯示先前的自動實作屬性範例的對等程式碼。  
  
 [!code-vb[VbVbalrAutoImplementedProperties#2](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/auto-implemented-propert_1_3.vb)]  
  
 下列程式碼會示範唯讀屬性實作：  
  
```vb  
Class Customer  
   Public ReadOnly Property Tags As New List(Of String)  
   Public ReadOnly Property Name As String = ""  
   Public ReadOnly Property File As String  
  
   Sub New(file As String)  
      Me.File = file  
   End Sub  
End Class  
  
```  
  
 如範例所示，您可以使用初始化運算式指派給屬性，或在包含類型的建構函式中指派給屬性。  您可以在任何時間指派給唯讀屬性的支援欄位。  
  
## 支援欄位  
 當您宣告自動實作屬性時，Visual Basic 會自動建立稱為 *支援欄位*的隱藏私用欄位來包含屬性值。  支援欄位名稱是自動實作屬性名稱前面加上底線 \(\_\)。  例如，如果您宣告名為 `ID` 的自動實作屬性，會將支援欄位命名為 `_ID`。  如果包含也命名為 `_ID` 的成員類別，則會產生名稱衝突，且 Visual Basic 將報告編譯器錯誤。  
  
 支援欄位也具有下列特性：  
  
-   支援欄位的存取修飾詞一律為 `Private`，即使屬性本身有不同的存取層級，例如 `Public`。  
  
-   如果屬性標記為 `Shared`，支援欄位也會共用。  
  
-   為屬性所指定的屬性並不適用於支援欄位。  
  
-   可從類別內的程式碼，和從偵錯工具 \(例如 \[監看式\] 視窗\) 中存取的支援欄位。  不過，支援欄位不會顯示在 IntelliSense 文字自動完成清單中。  
  
## 初始化自動實作屬性  
 任何可以用來初始化欄位的運算式，對初始化自動實作屬性都是有效的。  當您初始化自動實作屬性時，會評估運算式，並傳遞給屬性的 `Set` 程序。  下列程式碼範例會顯示一些包括起始值的自動實作屬性。  
  
 [!code-vb[VbVbalrAutoImplementedProperties#3](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/auto-implemented-propert_1_4.vb)]  
  
 無法初始化 `Interface`，或標示為 `MustOverride` 的自動實作屬性。  
  
 當您將自動實作屬性宣告為 `Structure` 的成員時，如果它標示為 `Shared`，您只能初始化自動實作屬性。  
  
 當您將自動實作屬性宣告為陣列時，您無法指定明確的陣列界限。  不過，您可以使用陣列初始設定式來提供值，如下列範例所示。  
  
 [!code-vb[VbVbalrAutoImplementedProperties#4](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/auto-implemented-propert_1_5.vb)]  
  
## 需要標準語法的屬性定義  
 自動實作屬性很方便，並且支援許多程式設計案例。  不過，有很多情況下您不能使用自動實作屬性，並且必須改為使用標準或*已展開*屬性語法。  
  
 如果您想要執行下列任何一項，您必須使用已展開屬性定義語法：  
  
-   將程式碼新增至屬性的 `Get` 或 `Set` 程序，例如在 `Set` 程序中用來驗證傳入值的程式碼。  比方說，您可能想要先確認代表電話號碼的字串包含必要的數字，再設定屬性值。  
  
-   指定 `Get` 和 `Set` 程序的不同協助工具。  比方說，您可能想要製作 `Set` 程序 `Private` 和 `Get` 程序 `Public`。  
  
-   建立 `WriteOnly` 屬性。  
  
-   使用參數化屬性 \(包括 `Default` 屬性\)。  若要指定屬性的參數，或指定 `Set` 程序的其他參數，您必須宣告已展開屬性。  
  
-   將屬性放在支援欄位，或變更支援欄位的存取層級。  
  
-   提供支援欄位的 XML 註解。  
  
## 展開自動實作屬性  
 如果您必須將自動實作屬性轉換為包含 `Get` 或 `Set` 程序的已展開屬性，Visual Basic 程式碼編輯器可以自動產生屬性的 `Get` 和 `Set` 程序和 `End Property` 陳述式。  如果您將游標置於 `Property` 陳述式後的空白列，請鍵入 `G` \(適用於 `Get`\) 或 `S` \(適用於 `Set`\)，再按下 ENTER 以產生程式碼。  當您在 `Property` 陳述式結束時按下 ENTER，Visual Basic 程式碼編輯器會自動產生唯讀和唯寫屬性的 `Get` 或 `Set` 程序。  
  
## 請參閱  
 [How to: Declare and Call a Default Property in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)   
 [How to: Declare a Property with Mixed Access Levels](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)   
 [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md)   
 [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md)   
 [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)   
 [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)