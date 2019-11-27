---
title: 如何：宣告及呼叫預設屬性
ms.date: 07/20/2015
helpviewer_keywords:
- defaults [Visual Basic], properties
- properties [Visual Basic], default
- procedures [Visual Basic], defining
- default properties [Visual Basic], in Visual Basic
- Visual Basic code, procedures
- Visual Basic code, properties
- default properties
ms.assetid: 68b4026e-09ef-4613-808e-f6287494ff63
ms.openlocfilehash: b01188ed8a9ff4da95a6975dcac3509625fdffb2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349674"
---
# <a name="how-to-declare-and-call-a-default-property-in-visual-basic"></a>如何：在 Visual Basic 中宣告及呼叫預設屬性
*預設屬性*是您的程式碼可以存取而不需要指定的類別或結構屬性。 呼叫程式碼時，會將類別或結構命名為，而不是屬性，而內容則允許存取屬性，Visual Basic 解析對該類別或結構的預設屬性的存取（如果有的話）。  
  
 類別或結構最多隻能有一個預設屬性。 不過，您可以多載預設屬性，並擁有一個以上的版本。  
  
 如需詳細資訊，請參閱[Default](../../../../visual-basic/language-reference/modifiers/default.md)。  
  
### <a name="to-declare-a-default-property"></a>若要宣告預設屬性  
  
1. 以一般方式宣告屬性。 請勿指定 `Shared` 或 `Private` 關鍵字。  
  
2. 在屬性宣告中包含 `Default` 關鍵字。  
  
3. 請為屬性指定至少一個參數。 您不能定義不接受至少一個引數的預設屬性。  
  
     [!code-vb[VbVbcnProcedures#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#17)]  
  
### <a name="to-call-a-default-property"></a>呼叫預設屬性  
  
1. 宣告包含類別或結構類型的變數。  
  
     [!code-vb[VbVbcnProcedures#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#16)]  
  
2. 在通常會包含屬性名稱的運算式中單獨使用變數名稱。  
  
     [!code-vb[VbVbcnProcedures#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#21)]  
  
3. 請在括弧中的變數名稱後面加上引數清單。 預設屬性至少必須接受一個引數。  
  
     [!code-vb[VbVbcnProcedures#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#20)]  
  
4. 若要抓取預設屬性值，請在運算式中使用變數名稱，並以引數清單或在指派語句中後面加上等號（`=`）登入。  
  
     [!code-vb[VbVbcnProcedures#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#15)]  
  
5. 若要設定預設屬性值，請在指派語句的左邊使用變數名稱，以及引數清單。  
  
     [!code-vb[VbVbcnProcedures#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#14)]  
  
6. 您一律可以將預設屬性名稱與變數名稱一起指定，就像存取任何其他屬性一樣。  
  
     [!code-vb[VbVbcnProcedures#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#19)]  
  
## <a name="example"></a>範例  
 下列範例會宣告類別的預設屬性。  
  
 [!code-vb[VbVbcnProcedures#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#12)]  
  
## <a name="example"></a>範例  
 下列範例示範如何在類別 `class1`上呼叫預設屬性 `myProperty`。 三個指派語句會將值儲存在 `myProperty`中，而 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 呼叫則會讀取這些值。  
  
 [!code-vb[VbVbcnProcedures#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#13)]  
  
 預設屬性最常見的用法是各種集合類別上的 <xref:Microsoft.VisualBasic.Collection.Item%2A> 屬性。  
  
## <a name="robust-programming"></a>穩固程式設計  
 預設屬性可能會減少原始碼字元數，但它們可能會使您的程式碼更容易閱讀。 如果呼叫程式碼不熟悉您的類別或結構，當它對類別或結構名稱進行參考時，就無法確定該參考是要存取類別或結構本身，還是預設屬性。 這可能會導致編譯器錯誤或細微的執行時間邏輯錯誤。  
  
 您可以一律使用[Option Strict 語句](../../../../visual-basic/language-reference/statements/option-strict-statement.md)，將編譯器類型檢查設定為 `On`，藉此減少預設屬性錯誤的機率。  
  
 如果您打算在程式碼中使用預先定義的類別或結構，就必須判斷它是否有預設屬性，如果是，它的名稱為何。  
  
 由於這些缺點，您應該考慮不要定義預設屬性。 為了讓程式碼更容易閱讀，您也應該考慮明確參考所有屬性，甚至是預設屬性。  
  
## <a name="see-also"></a>請參閱

- [屬性程序](./property-procedures.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [Property 陳述式](../../../../visual-basic/language-reference/statements/property-statement.md)
- [預設值](../../../../visual-basic/language-reference/modifiers/default.md)
- [Visual Basic 中的屬性和變數之間的差異](./differences-between-properties-and-variables.md)
- [如何：建立屬性](./how-to-create-a-property.md)
- [如何：宣告混合存取層級的屬性](./how-to-declare-a-property-with-mixed-access-levels.md)
- [如何：呼叫屬性程序](./how-to-call-a-property-procedure.md)
- [如何：將值置入屬性](./how-to-put-a-value-in-a-property.md)
- [如何：取得屬性值](./how-to-get-a-value-from-a-property.md)
