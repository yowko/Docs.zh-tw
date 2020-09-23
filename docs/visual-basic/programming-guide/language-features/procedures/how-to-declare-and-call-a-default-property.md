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
ms.openlocfilehash: 21aa6e6a9bba23d767b9d1fac610eaac3265550d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91087449"
---
# <a name="how-to-declare-and-call-a-default-property-in-visual-basic"></a>如何：在 Visual Basic 中宣告及呼叫預設屬性

*預設屬性*為類別或結構屬性，您的程式碼可以存取，而不需要指定它。 當呼叫程式碼命名類別或結構，但不允許存取屬性時，Visual Basic 會解析該類別或結構的預設屬性（如果有的話）的存取權。  
  
 類別或結構最多隻能有一個預設屬性。 不過，您可以多載預設屬性，並擁有一個以上的版本。  
  
 如需詳細資訊，請參閱 [Default](../../../language-reference/modifiers/default.md)。  
  
### <a name="to-declare-a-default-property"></a>宣告預設屬性  
  
1. 以正常方式宣告屬性。 請勿指定 `Shared` 或 `Private` 關鍵字。  
  
2. `Default`在屬性宣告中包含關鍵字。  
  
3. 至少為屬性指定一個參數。 您無法定義未採用至少一個引數的預設屬性。  
  
     [!code-vb[VbVbcnProcedures#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#17)]  
  
### <a name="to-call-a-default-property"></a>若要呼叫預設屬性  
  
1. 宣告包含類別或結構類型的變數。  
  
     [!code-vb[VbVbcnProcedures#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#16)]  
  
2. 在您通常會包含屬性名稱的運算式中單獨使用變數名稱。  
  
     [!code-vb[VbVbcnProcedures#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#21)]  
  
3. 在變數名稱後面加上括弧中的引數清單。 預設屬性必須採用至少一個引數。  
  
     [!code-vb[VbVbcnProcedures#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#20)]  
  
4. 若要取出預設屬性值，請在運算式中使用變數名稱，並使用引數清單，或遵循相等的 (`=`) 登入指派語句。  
  
     [!code-vb[VbVbcnProcedures#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#15)]  
  
5. 若要設定預設屬性值，請在指派語句的左側使用變數名稱和引數清單。  
  
     [!code-vb[VbVbcnProcedures#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#14)]  
  
6. 您一律可以使用變數名稱來指定預設的屬性名稱，就像存取任何其他屬性一樣。  
  
     [!code-vb[VbVbcnProcedures#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#19)]  
  
## <a name="example"></a>範例  

 下列範例會宣告類別的預設屬性。  
  
 [!code-vb[VbVbcnProcedures#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#12)]  
  
## <a name="example"></a>範例  

 下列範例示範如何呼叫類別上的預設屬性 `myProperty` `class1` 。 這三個指派語句會在中儲存值 `myProperty` ，而 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 呼叫會讀取這些值。  
  
 [!code-vb[VbVbcnProcedures#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#13)]  
  
 預設屬性最常見的用法是 <xref:Microsoft.VisualBasic.Collection.Item%2A> 各種集合類別上的屬性。  
  
## <a name="robust-programming"></a>穩固程式設計  

 預設屬性可能會減少原始程式碼字元，但可以讓您的程式碼更難以讀取。 如果呼叫程式碼不熟悉您的類別或結構，則在參考類別或結構名稱時，如果該參考存取類別或結構本身或預設屬性，則無法確定。 這可能會導致編譯器錯誤或微妙的執行時間邏輯錯誤。  
  
 您可以使用 [Option Strict 語句](../../../language-reference/statements/option-strict-statement.md) 將編譯器類型檢查設定為，以稍微減少預設屬性錯誤的機率 `On` 。  
  
 如果您打算在程式碼中使用預先定義的類別或結構，就必須判斷它是否有預設屬性，如果是，它的名稱就是。  
  
 因為這些缺點，您應該考慮不要定義預設屬性。 為了讓程式碼更容易閱讀，您也應該考慮一律明確參考所有屬性，甚至是預設屬性。  
  
## <a name="see-also"></a>另請參閱

- [屬性程序](./property-procedures.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [Property Statement](../../../language-reference/statements/property-statement.md)
- [預設值](../../../language-reference/modifiers/default.md)
- [Visual Basic 中屬性和變數的差異](./differences-between-properties-and-variables.md)
- [如何：建立屬性](./how-to-create-a-property.md)
- [如何：宣告混合存取層級的屬性](./how-to-declare-a-property-with-mixed-access-levels.md)
- [如何：呼叫屬性程序](./how-to-call-a-property-procedure.md)
- [如何：將值置入屬性](./how-to-put-a-value-in-a-property.md)
- [如何：取得屬性值](./how-to-get-a-value-from-a-property.md)
