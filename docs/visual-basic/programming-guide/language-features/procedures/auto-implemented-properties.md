---
title: 自動實作的屬性 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AutoProperty
- vb.AutoImplementedProperty
helpviewer_keywords:
- properties [Visual Basic], auto-implemented
- properties [Visual Basic], auto-implemented
- auto-implemented properties [Visual Basic]
ms.assetid: 5c669f0b-cf95-4b4e-ae84-9cc55212ca87
ms.openlocfilehash: bc83163a024bd50d3e256b4eb49861669f8c02c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="auto-implemented-properties-visual-basic"></a>自動實作的屬性 (Visual Basic)
*自動實作屬性*可讓您快速指定類別的屬性，而不需要撰寫程式碼以`Get`和`Set`屬性。 當您撰寫自動實作屬性之程式碼時，Visual Basic 編譯器會自動建立私用欄位，來存放建立關聯的 `Get` 和 `Set` 程序外，另外存放屬性變數。  
  
 使用自動實作屬性、屬性 (包括預設值)，可以在單行中宣告。 下列範例顯示三個屬性宣告。  
  
 [!code-vb[VbVbalrAutoImplementedProperties#1](./codesnippet/VisualBasic/auto-implemented-properties_1.vb)]  
  
 自動實作屬性相當於屬性值儲存在私用欄位的屬性。 下列程式碼範例顯示自動實作屬性。  
  
 [!code-vb[VbVbalrAutoImplementedProperties#5](./codesnippet/VisualBasic/auto-implemented-properties_2.vb)]  
  
 下列程式碼範例顯示先前的自動實作屬性範例的對等程式碼。  
  
 [!code-vb[VbVbalrAutoImplementedProperties#2](./codesnippet/VisualBasic/auto-implemented-properties_3.vb)]  
  
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
  
## <a name="backing-field"></a>支援欄位  
 當您宣告自動實作屬性時，Visual Basic 會自動建立名為的隱藏私用欄位*支援欄位*包含屬性值。 支援欄位名稱是自動實作屬性名稱前面加上底線 (_)。 例如，如果您宣告名為 `ID` 的自動實作屬性，會將支援欄位命名為 `_ID`。 如果包含也命名為 `_ID` 的成員類別，則會產生名稱衝突，且 Visual Basic 將報告編譯器錯誤。  
  
 支援欄位也具有下列特性：  
  
-   支援欄位的存取修飾詞一律為 `Private`，即使屬性本身有不同的存取層級，例如 `Public`。  
  
-   如果屬性標記為 `Shared`，支援欄位也會共用。  
  
-   為屬性所指定的屬性並不適用於支援欄位。  
  
-   可從類別內的程式碼，和從偵錯工具 (例如 [監看式] 視窗) 中存取的支援欄位。 不過，支援欄位不會顯示在 IntelliSense 文字自動完成清單中。  
  
## <a name="initializing-an-auto-implemented-property"></a>初始化自動實作屬性  
 任何可以用來初始化欄位的運算式，對初始化自動實作屬性都是有效的。 當您初始化自動實作屬性時，會評估運算式，並傳遞給屬性的 `Set` 程序。 下列程式碼範例會顯示一些包括起始值的自動實作屬性。  
  
 [!code-vb[VbVbalrAutoImplementedProperties#3](./codesnippet/VisualBasic/auto-implemented-properties_4.vb)]  
  
 無法初始化 `Interface`，或標示為 `MustOverride` 的自動實作屬性。  
  
 當您將自動實作屬性宣告為 `Structure` 的成員時，如果它標示為 `Shared`，您只能初始化自動實作屬性。  
  
 當您將自動實作屬性宣告為陣列時，您無法指定明確的陣列界限。 不過，您可以使用陣列初始設定式來提供值，如下列範例所示。  
  
 [!code-vb[VbVbalrAutoImplementedProperties#4](./codesnippet/VisualBasic/auto-implemented-properties_5.vb)]  
  
## <a name="property-definitions-that-require-standard-syntax"></a>需要標準語法的屬性定義  
 自動實作屬性很方便，並且支援許多程式設計案例。 不過，有很多情況下您不能使用自動實作的屬性並必須改為使用標準或*展開*，屬性的語法。  
  
 如果您想要執行下列任何一項，您必須使用已展開屬性定義語法：  
  
-   將程式碼新增至屬性的 `Get` 或 `Set` 程序，例如在 `Set` 程序中用來驗證傳入值的程式碼。 比方說，您可能想要先確認代表電話號碼的字串包含必要的數字，再設定屬性值。  
  
-   指定 `Get` 和 `Set` 程序的不同協助工具。 比方說，您可能想要製作 `Set` 程序 `Private` 和 `Get` 程序 `Public`。  
  
-   建立 `WriteOnly` 屬性。  
  
-   使用參數化屬性 (包括 `Default` 屬性)。 若要指定屬性的參數，或指定 `Set` 程序的其他參數，您必須宣告已展開屬性。  
  
-   將屬性放在支援欄位，或變更支援欄位的存取層級。  
  
-   提供支援欄位的 XML 註解。  
  
## <a name="expanding-an-auto-implemented-property"></a>展開自動實作屬性  
 如果您必須將自動實作屬性轉換為包含 `Get` 或 `Set` 程序的已展開屬性，Visual Basic 程式碼編輯器可以自動產生屬性的 `Get` 和 `Set` 程序和 `End Property` 陳述式。 如果您將游標置於後的空白列，產生的程式碼`Property`陳述式中，輸入`G`(如`Get`) 或`S`(如`Set`) 然後按 ENTER。 當您在 `Property` 陳述式結束時按下 ENTER，Visual Basic 程式碼編輯器會自動產生唯讀和唯寫屬性的 `Get` 或 `Set` 程序。  
  
## <a name="see-also"></a>另請參閱  
 [如何： 宣告及呼叫在 Visual Basic 中的預設屬性](./how-to-declare-and-call-a-default-property.md)  
 [如何：宣告混合存取層級的屬性](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [Property 陳述式](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md)  
 [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)  
 [物件和類別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
