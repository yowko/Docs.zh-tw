---
title: "決定物件類型 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables [Visual Basic], testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9a63b5cf5941deb4dcc7518880b4dc7d0545803c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="determining-object-type-visual-basic"></a>決定物件類型 (Visual Basic)
泛型物件變數 (也就是變數宣告為`Object`) 可以保存任何類別的物件。 使用類型的變數時`Object`，您可能需要不同依據採取動作的物件類別; 例如，有些物件可能不支援的特定屬性或方法。 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]提供兩種決定物件變數中儲存的物件類型：`TypeName`函式和`TypeOf...Is`運算子。  
  
## <a name="typename-and-typeofis"></a>TypeName 和 TypeOf...是  
 `TypeName`函式傳回的字串，是最佳選擇，當您需要儲存或顯示類別物件的名稱，如下列程式碼片段所示：  
  
 [!code-vb[VbVbalrOOP#92](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_1.vb)]  
  
 `TypeOf...Is`運算子會測試的物件類型的最佳選擇，因為它的速度比對等字串比較使用`TypeName`。 下列程式碼片段使用`TypeOf...Is`內`If...Then...Else`陳述式：  
  
 [!code-vb[VbVbalrOOP#93](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_2.vb)]  
  
 注意這裡會到期。 `TypeOf...Is`運算子會傳回`True`如果物件是特定型別，或衍生自特定型別。 幾乎所有項目中所做的[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]牽涉到物件，其中包含通常不會視為物件，例如字串和整數的某些項目。 這些物件衍生自和繼承方法從<xref:System.Object>。 當傳遞`Integer`和評估與`Object`、`TypeOf...Is`運算子會傳回`True`。 下列範例會報告參數`InParam`同時為`Object`和`Integer`:  
  
 [!code-vb[VbVbalrOOP#94](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_3.vb)]  
  
 下列範例會使用這兩者`TypeOf...Is`和`TypeName`判斷物件傳遞給該型別`Ctrl`引數。 `TestObject`程序呼叫`ShowType`含有三種不同的控制項。  
  
#### <a name="to-run-the-example"></a>執行範例  
  
1.  建立新的 Windows 應用程式專案，加入<xref:System.Windows.Forms.Button>控制項，<xref:System.Windows.Forms.CheckBox>控制項和<xref:System.Windows.Forms.RadioButton>控制項加入表單。  
  
2.  您的表單上的按鈕，從呼叫`TestObject`程序。  
  
3.  將下列程式碼加入至表單：  
  
     [!code-vb[VbVbalrOOP#95](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_4.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.Information.TypeName%2A>  
 [使用字串名稱呼叫屬性或方法](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md)  
 [Object 資料類型](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [If...Then...Else 陳述式](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [String 資料類型](../../../../visual-basic/language-reference/data-types/string-data-type.md)  
 [Integer 資料類型](../../../../visual-basic/language-reference/data-types/integer-data-type.md)
