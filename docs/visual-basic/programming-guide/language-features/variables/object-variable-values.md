---
title: 物件變數值 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], values
- values [Visual Basic], of object variables
- data types [Visual Basic], object variable
- variables [Visual Basic], object
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
ms.openlocfilehash: 728f097b3c084e5292cb2d2bf5a0c1d20bdad922
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004580"
---
# <a name="object-variable-values-visual-basic"></a>物件變數值 (Visual Basic)
[Object 資料類型](../../../../visual-basic/language-reference/data-types/object-data-type.md)的變數可以參考任何類型的資料。 您儲存在 @no__t 0 變數中的值會保留在記憶體中的其他位置，而變數本身則會保存資料的指標。  
  
## <a name="object-classifier-functions"></a>物件分類函數  
 Visual Basic 提供的函式會傳回 `Object` 變數所參考的資訊，如下表所示。  
  
|函數|如果物件變數參考，則傳回 True。|  
|--------------|---------------------------------------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A>|值的陣列，而不是單一值|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A>|[日期資料類型](../../../../visual-basic/language-reference/data-types/date-data-type.md)值，或可解讀為日期和時間值的字串|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|類型為 <xref:System.DBNull> 的物件，代表遺漏或不存在的資料。|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A>|例外狀況物件，衍生自 <xref:System.Exception>|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A>|[沒有，也](../../../../visual-basic/language-reference/nothing.md)就是目前沒有任何物件指派給變數|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|可以解讀為數字的數位或字串|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A>|參考型別（例如字串、陣列、委派或類別型別）|  
  
 您可以使用這些函式來避免將不正確值提交給作業或程式。  
  
## <a name="typeof-operator"></a>TypeOf 運算子  
 您也可以使用[TypeOf 運算子](../../../../visual-basic/language-reference/operators/typeof-operator.md)來判斷物件變數目前是否參考特定的資料類型。 如果運算元的執行時間型別衍生自或會執行指定的型別，則 `TypeOf` ... `Is` 運算式會評估為 `True`。  
  
 下列範例會在參考值和參考型別的物件變數上使用 `TypeOf`。  
  
```vb  
' The following statement puts a value type (Integer) in an Object variable.  
Dim num As Object = 10  
' The following statement puts a reference type (Form) in an Object variable.  
Dim frm As Object = New Form()  
If TypeOf num Is Long Then Debug.WriteLine("num is Long")  
If TypeOf num Is Integer Then Debug.WriteLine("num is Integer")  
If TypeOf num Is Short Then Debug.WriteLine("num is Short")  
If TypeOf num Is Object Then Debug.WriteLine("num is Object")  
If TypeOf frm Is Form Then Debug.WriteLine("frm is Form")  
If TypeOf frm Is Label Then Debug.WriteLine("frm is Label")  
If TypeOf frm Is Object Then Debug.WriteLine("frm is Object")  
```  
  
 上述範例會將下列幾行寫入至 [ **Debug** ] 視窗：  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 物件變數 `num` 會參考 `Integer` 類型的資料，而 `frm` 則是指類別 <xref:System.Windows.Forms.Form> 的物件。  
  
## <a name="object-arrays"></a>物件陣列  
 您可以宣告並使用 `Object` 變數的陣列。 當您需要處理各種不同的資料類型和物件類別時，這會很有用。 陣列中的所有元素都必須具有相同的宣告資料類型。 將此資料類型宣告為 `Object`，可讓您將物件和類別實例與陣列中的其他資料類型一起儲存。  
  
## <a name="see-also"></a>另請參閱

- [物件變數](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [物件變數宣告](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [物件變數指派](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [如何：請參閱物件的目前實例 @ no__t-0
- [如何：判斷物件變數參考 @ no__t-0 的類型
- [如何：判斷兩個物件是否關聯 @ no__t-0
- [如何：判斷兩個物件是否相同 @ no__t-0
- [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
