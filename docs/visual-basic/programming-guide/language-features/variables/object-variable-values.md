---
title: "Object Variable Values (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "object variables, values"
  - "values, of object variables"
  - "data types [Visual Basic], object variable"
  - "variables [Visual Basic], object"
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# Object Variable Values (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

[Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)的變數可以參考任何型別的資料。  您儲存在 `Object` 變數中的值會保留在記憶體的其他地方，而該變數本身會保留該資料的指標。  
  
## 物件 Classifier 函式  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會提供可以傳回 `Object` 變數所參考內容相關資訊的函式，如下表所示。  
  
|Function|如果物件變數有參考則傳回 True|  
|--------------|-----------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A>|值的陣列，而不是單一值|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A>|[Date Data Type](../../../../visual-basic/language-reference/data-types/date-data-type.md) 值，或可解譯為日期和時間值的字串|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|型別 <xref:System.DBNull> 的物件，代表遺失或不存在的資料|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A>|例外狀況 \(Exception\) 物件，衍生自 <xref:System.Exception>|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A>|[Nothing](../../../../visual-basic/language-reference/nothing.md)，也就是目前並無物件指派給變數|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|數字或可解譯為數字的字串|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A>|參考型別 \(Reference Type\) \(例如字串、陣列、委派 \(Delegate\) 或類別型別\)|  
  
 您可使用這些函式以避免送出無效的值至運算或程序。  
  
## TypeOf 運算子  
 您也可以使用 [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) 判斷物件變數目前是否參考特定的資料型別。  如果運算元的執行階段型別是衍生自特定型別 \(或會實作特定型別\)，`TypeOf`...`Is` 運算式會評估為 `True`。  
  
 下列範例會在參考實值和參考型別 \(Reference Type\) 的物件變數上使用 `TypeOf`。  
  
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
  
 上述範例會將下列幾行寫入 \[**偵錯**\] 視窗：  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 `num` 物件變數會參考 `Integer` 型別的資料，而 `frm` 參考 <xref:System.Windows.Forms.Form> 類別的物件。  
  
## Object 陣列  
 您可以宣告和使用 `Object` 變數的陣列。  當您需要處理多種資料型別和物件類別時，這麼做非常有用。  陣列中的所有元素必須有相同的宣告資料型別。  將這個資料型別宣告為 `Object` 可讓您儲存與陣列中其他資料型別並列的物件和類別執行個體。  
  
## 請參閱  
 [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Object Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)   
 [Object Variable Assignment](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)   
 [How to: Refer to the Current Instance of an Object](../../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)   
 [How to: Determine What Type an Object Variable Refers To](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)   
 [How to: Determine Whether Two Objects Are Related](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)   
 [How to: Determine Whether Two Objects Are Identical](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)   
 [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)