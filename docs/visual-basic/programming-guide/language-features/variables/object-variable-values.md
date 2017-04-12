---
title: "物件變數值 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- object variables, values
- values, of object variables
- data types [Visual Basic], object variable
- variables [Visual Basic], object
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ff219571de9c76802d3f8d3046cf6b6f9d5be9d5
ms.lasthandoff: 03/13/2017

---
# <a name="object-variable-values-visual-basic"></a>物件變數值 (Visual Basic)
變數的[Object 資料型別](../../../../visual-basic/language-reference/data-types/object-data-type.md)可指向任何類型的資料。 您將存放的值`Object`變數保存在其他地方在記憶體中，同時在本身的變數存放資料的指標。  
  
## <a name="object-classifier-functions"></a>物件分類函數  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]提供函式會傳回什麼資訊`Object`變數參考到下, 表所示。  
  
|函式|如果物件變數參考，則傳回 True|  
|--------------|---------------------------------------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A></xref:Microsoft.VisualBasic.Information.IsArray%2A>|值，而不是單一值的陣列|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A></xref:Microsoft.VisualBasic.Information.IsDate%2A>|A[日期資料型別](../../../../visual-basic/language-reference/data-types/date-data-type.md)值或可以解譯為日期和時間值的字串|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A></xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|物件的型別<xref:System.DBNull>，用來表示資料遺失或不存在</xref:System.DBNull>|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A></xref:Microsoft.VisualBasic.Information.IsError%2A>|例外狀況物件，它是衍生自<xref:System.Exception></xref:System.Exception>|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A></xref:Microsoft.VisualBasic.Information.IsNothing%2A>|[Nothing](../../../../visual-basic/language-reference/nothing.md)，也就是沒有物件目前指派給變數|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A></xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|數字或可以解譯為數字的字串|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A></xref:Microsoft.VisualBasic.Information.IsReference%2A>|參考型別 （例如字串、 陣列、 委派或類別類型）|  
  
 您可以使用這些函式，以避免送出至操作或程序無效的值。  
  
## <a name="typeof-operator"></a>TypeOf 運算子  
 您也可以使用[TypeOf 運算子](../../../../visual-basic/language-reference/operators/typeof-operator.md)來決定物件變數是否目前參考特定資料型別。 The `TypeOf`...`Is`運算式評估為`True`如果運算元的執行階段型別衍生自或實作指定的型別。  
  
 下列範例會使用`TypeOf`上物件變數值和參考型別參考。  
  
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
  
 上述範例會將下列幾行以**偵錯**視窗︰  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 物件變數`num`指的是資料型別的`Integer`，和`frm` <xref:System.Windows.Forms.Form>.</xref:System.Windows.Forms.Form>類別的物件參考  
  
## <a name="object-arrays"></a>物件陣列  
 您可以宣告和使用的陣列`Object`變數。 當您需要處理各種資料型別和物件類別時，這非常有用。 陣列中的所有項目必須具有相同的宣告的資料型別。 宣告為此資料型別`Object`可讓您儲存物件和類別與陣列中其他資料類型的執行個體。  
  
## <a name="see-also"></a>另請參閱  
 [物件變數](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [物件變數宣告](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)   
 [物件變數指派](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)   
 [如何︰ 參考物件的目前執行個體](../../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)   
 [如何︰ 決定物件變數參考的類型](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)   
 [如何︰ 判斷兩個物件是否關聯](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)   
 [如何︰ 判斷兩個物件是否相同](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)   
 [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
