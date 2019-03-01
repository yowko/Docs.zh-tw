---
title: 決定物件類型 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables [Visual Basic], testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
ms.openlocfilehash: becbbef008e8a474db198748d45f260fcb90c758
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966767"
---
# <a name="determining-object-type-visual-basic"></a>決定物件類型 (Visual Basic)
泛型的物件變數 (也就是變數宣告為`Object`) 可以保留任何類別的物件。 使用型別的變數時`Object`，您可能需要採取不同的物件類別為基礎的動作; 例如，某些物件可能不支援的特定屬性或方法。 Visual Basic 提供兩種決定物件變數中儲存的物件類型：`TypeName`函式和`TypeOf...Is`運算子。  
  
## <a name="typename-and-typeofis"></a>類型名稱，TypeOf...是  
 `TypeName`函式傳回字串，是最佳選擇，當您需要儲存或顯示類別物件的名稱，如下列程式碼片段所示：  
  
 [!code-vb[VbVbalrOOP#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#92)]  
  
 `TypeOf...Is`運算子會測試物件的類型的最佳選擇，因為它的速度比對等字串比較使用`TypeName`。 下列程式碼片段會使用`TypeOf...Is`內`If...Then...Else`陳述式：  
  
 [!code-vb[VbVbalrOOP#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#93)]  
  
 注意這裡會到期。 `TypeOf...Is`運算子會傳回`True`如果物件是特定的類型，或衍生自特定的型別。 幾乎所有項目中所做的 Visual Basic 牽涉到物件，其中包含一些通常不會視為物件，例如字串和整數的項目。 這些物件衍生自和繼承方法<xref:System.Object>。 當傳遞`Integer`和評估與`Object`，則`TypeOf...Is`運算子會傳回`True`。 下列範例會報告的參數`InParam`兼具`Object`和`Integer`:  
  
 [!code-vb[VbVbalrOOP#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#94)]  
  
 下列範例會使用這兩者`TypeOf...Is`並`TypeName`來判斷物件傳遞至該型別`Ctrl`引數。 `TestObject`程序呼叫`ShowType`使用三種不同的控制項。  
  
#### <a name="to-run-the-example"></a>執行範例  
  
1.  建立新的 Windows 應用程式專案並加入<xref:System.Windows.Forms.Button>控制<xref:System.Windows.Forms.CheckBox>控制項，和<xref:System.Windows.Forms.RadioButton>控制項加入表單。  
  
2.  從您的表單上的按鈕，呼叫`TestObject`程序。  
  
3.  將下列程式碼新增至您的表單：  
  
     [!code-vb[VbVbalrOOP#95](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#95)]  
  
## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualBasic.Information.TypeName%2A>
- [使用字串名稱呼叫屬性或方法](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md)
- [Object 資料類型](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [If...Then...Else 陳述式](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [String 資料類型](../../../../visual-basic/language-reference/data-types/string-data-type.md)
- [Integer 資料類型](../../../../visual-basic/language-reference/data-types/integer-data-type.md)
