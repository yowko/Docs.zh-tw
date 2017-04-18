---
title: "決定物件類型 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables, testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
caps.latest.revision: 13
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
ms.openlocfilehash: 2486d989801fc4866a50747aa963b509a627994d
ms.lasthandoff: 03/13/2017

---
# <a name="determining-object-type-visual-basic"></a>決定物件類型 (Visual Basic)
泛型物件變數 (也就是變數宣告為`Object`) 可以保存任何類別的物件。 使用型別的變數時`Object`，您可能需要採取不同的物件類別為基礎的動作; 例如，有些物件可能不支援特定的屬性或方法。 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]提供兩種方法可判斷哪一種物件會儲存在物件變數︰`TypeName`函式和`TypeOf...Is`運算子。  
  
## <a name="typename-and-typeofis"></a>TypeName 和 TypeOf...是  
 `TypeName`函式會傳回 string，而是最佳選擇，當您需要儲存或顯示類別物件的名稱，如下列程式碼片段所示︰  
  
 [!code-vb[VbVbalrOOP #&92;](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_1.vb)]  
  
 `TypeOf...Is`運算子是測試的物件類型的最佳選擇，因為它是速度比對等的字串比較使用`TypeName`。 下列程式碼片段使用`TypeOf...Is`內`If...Then...Else`陳述式︰  
  
 [!code-vb[VbVbalrOOP #&93;](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_2.vb)]  
  
 注意在此到期。 `TypeOf...Is`運算子會傳回`True`如果物件是特定型別，或衍生自特定型別。 幾乎所有項目中所做的[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]牽涉到物件，包括一些通常不會被視為物件，例如字串和整數的項目。 這些物件衍生自與繼承來自<xref:System.Object>.</xref:System.Object>方法 當傳遞`Integer`和評估與`Object`、`TypeOf...Is`運算子會傳回`True`。 下列範例會報告參數`InParam`同時為`Object`和`Integer`:  
  
 [!code-vb[VbVbalrOOP #&94;](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_3.vb)]  
  
 下列範例使用`TypeOf...Is`和`TypeName`判斷傳遞給它的物件型別`Ctrl`引數。 `TestObject`程序呼叫`ShowType`有三種不同的控制項。  
  
#### <a name="to-run-the-example"></a>執行範例  
  
1.  建立新的 Windows 應用程式專案並加入<xref:System.Windows.Forms.Button>控制項，<xref:System.Windows.Forms.CheckBox>控制項，以及<xref:System.Windows.Forms.RadioButton>控制項加入表單。</xref:System.Windows.Forms.RadioButton> </xref:System.Windows.Forms.CheckBox> </xref:System.Windows.Forms.Button>  
  
2.  在表單上按鈕中，呼叫`TestObject`程序。  
  
3.  將下列程式碼加入至表單︰  
  
     [!code-vb[VbVbalrOOP #&95;](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_4.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.Information.TypeName%2A></xref:Microsoft.VisualBasic.Information.TypeName%2A>   
 [使用字串名稱呼叫屬性或方法](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md)   
 [Object 資料型別](../../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [如果...然後...Else 陳述式](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)   
 [字串資料類型](../../../../visual-basic/language-reference/data-types/string-data-type.md)   
 [Integer 資料類型](../../../../visual-basic/language-reference/data-types/integer-data-type.md)
