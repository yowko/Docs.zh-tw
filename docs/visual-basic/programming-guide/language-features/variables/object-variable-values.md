---
title: 物件變數值 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], values
- values [Visual Basic], of object variables
- data types [Visual Basic], object variable
- variables [Visual Basic], object
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
ms.openlocfilehash: a5152ad0e5e5ac876783c2b191ee13e845593df8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="object-variable-values-visual-basic"></a>物件變數值 (Visual Basic)
變數的[物件資料類型](../../../../visual-basic/language-reference/data-types/object-data-type.md)可以指向任何類型的資料。 您將儲存的值`Object`變數保留其他地方在記憶體中，而變數本身會保留資料指標。  
  
## <a name="object-classifier-functions"></a>物件的分類函數  
 Visual Basic 提供傳回什麼的相關資訊的函式`Object`變數參考至下, 表所示。  
  
|功能|如果物件變數參考，則傳回 True|  
|--------------|---------------------------------------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A>|值，而非單一值的陣列|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A>|A[日期資料型別](../../../../visual-basic/language-reference/data-types/date-data-type.md)值或可以解譯為日期和時間值的字串|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|型別的物件<xref:System.DBNull>，用來表示資料遺漏或不存在|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A>|例外狀況物件，衍生自 <xref:System.Exception>|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A>|[執行任何動作](../../../../visual-basic/language-reference/nothing.md)，也就是沒有物件目前指派給變數|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|數字或可以解譯為數字的字串|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A>|參考類型 （例如字串、 陣列、 委派或類別類型）|  
  
 您可以使用這些函式，以避免送出至作業或程序無效的值。  
  
## <a name="typeof-operator"></a>TypeOf 運算子  
 您也可以使用[TypeOf 運算子](../../../../visual-basic/language-reference/operators/typeof-operator.md)來判斷是否為特定的資料類型目前參考的物件變數。 `TypeOf`...`Is`運算式評估為`True`如果運算元的執行階段類型衍生自或實作指定的型別。  
  
 下列範例會使用`TypeOf`物件變數參考值和參考型別。  
  
```  
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
  
 上述範例會將下列行以**偵錯**視窗：  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 物件變數`num`類型的資料是指`Integer`，和`frm`類別的物件是指<xref:System.Windows.Forms.Form>。  
  
## <a name="object-arrays"></a>物件陣列  
 您可以宣告和使用的陣列`Object`變數。 當您需要處理各種資料類型和物件的類別時，這非常有用。 陣列中的所有元素必須都有相同的宣告的資料類型。 宣告為此資料型別`Object`可讓您儲存物件和類別以及陣列中其他資料類型的執行個體。  
  
## <a name="see-also"></a>另請參閱  
 [物件變數](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [物件變數宣告](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [物件變數指派](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [如何：參考物件目前的執行個體](../../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)  
 [如何：決定物件變數參考的型別](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)  
 [如何：判斷兩個物件是否關聯](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)  
 [如何：判斷兩個物件是否相同](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)  
 [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
