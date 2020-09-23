---
title: 決定物件類型
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables [Visual Basic], testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
ms.openlocfilehash: ae338bc9bad9646abc045a652d4ef33a8863354b
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086058"
---
# <a name="determining-object-type-visual-basic"></a>決定物件類型 (Visual Basic)

泛型物件變數 (也就是說，您宣告為) 的變數 `Object` 可以保存任何類別的物件。 使用類型的變數時 `Object` ，您可能需要根據物件的類別來採取不同的動作; 例如，某些物件可能不支援特定的屬性或方法。 Visual Basic 提供兩種方式來決定要在物件變數中儲存哪種類型的物件： `TypeName` 函數和 `TypeOf...Is` 運算子。  
  
## <a name="typename-and-typeofis"></a>TypeName 和 TypeOf .。。是  

 `TypeName`當您需要儲存或顯示物件的類別名稱時，函式會傳回字串，而這是最好的選擇，如下列程式碼片段所示：  
  
 [!code-vb[VbVbalrOOP#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#92)]  
  
 `TypeOf...Is`運算子是測試物件類型的最佳選擇，因為它的速度比使用的對等字串比較快許多 `TypeName` 。 下列程式碼片段會 `TypeOf...Is` 在語句中使用 `If...Then...Else` ：  
  
 [!code-vb[VbVbalrOOP#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#93)]  
  
 有一點要特別注意。 `TypeOf...Is` `True` 如果物件是特定型別，或衍生自特定型別，則運算子會傳回。 幾乎您使用 Visual Basic 所做的一切都牽涉到物件，包括通常不視為物件的一些元素，例如字串和整數。 這些物件是衍生自，而且會繼承方法 <xref:System.Object> 。 當傳遞 `Integer` 和評估時 `Object` ，運算子會傳回 `TypeOf...Is` `True` 。 下列範例會報告參數 `InParam` 同時是 `Object` 和 `Integer` ：  
  
 [!code-vb[VbVbalrOOP#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#94)]  
  
 下列範例會使用 `TypeOf...Is` 和 `TypeName` 來判斷在引數中傳遞給它的物件類型 `Ctrl` 。 程式會 `TestObject` `ShowType` 使用三種不同的控制項來呼叫。  
  
#### <a name="to-run-the-example"></a>執行範例  
  
1. 建立新的 Windows 應用程式專案，並將控制項 <xref:System.Windows.Forms.Button> 、 <xref:System.Windows.Forms.CheckBox> 控制項和控制項加入 <xref:System.Windows.Forms.RadioButton> 表單中。  
  
2. 從表單上的按鈕，呼叫程式 `TestObject` 。  
  
3. 將下列程式碼新增至您的表單：  
  
     [!code-vb[VbVbalrOOP#95](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#95)]  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Information.TypeName%2A>
- [使用字串名稱呼叫屬性或方法](calling-a-property-or-method-using-a-string-name.md)
- [Object Data Type](../../../language-reference/data-types/object-data-type.md)
- [If...Then...Else 陳述式](../../../language-reference/statements/if-then-else-statement.md)
- [String 資料類型](../../../language-reference/data-types/string-data-type.md)
- [整數資料類型](../../../language-reference/data-types/integer-data-type.md)
