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
ms.openlocfilehash: 3b1c4ad0ab4fd8d2897aff6ad9097cdc81272455
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410640"
---
# <a name="determining-object-type-visual-basic"></a>決定物件類型 (Visual Basic)
泛型物件變數（也就是您宣告為的變數 `Object` ）可以保存任何類別中的物件。 使用類型的變數時 `Object` ，您可能需要根據物件的類別採取不同的動作; 例如，某些物件可能不支援特定的屬性或方法。 Visual Basic 提供兩個方法來決定要將哪一種類型的物件儲存在物件變數中： `TypeName` 函式和 `TypeOf...Is` 運算子。  
  
## <a name="typename-and-typeofis"></a>TypeName 和 TypeOf .。。均  
 `TypeName`當您需要儲存或顯示物件的類別名稱時，函數會傳回字串，而且是最佳選擇，如下列程式碼片段所示：  
  
 [!code-vb[VbVbalrOOP#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#92)]  
  
 `TypeOf...Is`運算子是測試物件類型的最佳選擇，因為它比使用的對等字串比較快很多 `TypeName` 。 下列程式碼片段會 `TypeOf...Is` 在語句內使用 `If...Then...Else` ：  
  
 [!code-vb[VbVbalrOOP#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#93)]  
  
 請注意，這裡有一個注意事項。 `TypeOf...Is` `True` 如果物件屬於特定型別，或衍生自特定型別，則運算子會傳回。 幾乎所有您使用 Visual Basic 執行的工作都牽涉到物件，其中包括一些通常不會被視為物件的元素，例如字串和整數。 這些物件衍生自，並繼承自的方法 <xref:System.Object> 。 當傳遞 `Integer` 並以評估時 `Object` ，運算子會傳回 `TypeOf...Is` `True` 。 下列範例會報告參數 `InParam` 同時為 `Object` 和 `Integer` ：  
  
 [!code-vb[VbVbalrOOP#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#94)]  
  
 下列範例會使用 `TypeOf...Is` 和 `TypeName` 來判斷在引數中傳遞給它的物件類型 `Ctrl` 。 程式會 `TestObject` 呼叫 `ShowType` 三種不同類型的控制項。  
  
#### <a name="to-run-the-example"></a>執行範例  
  
1. 建立新的 Windows 應用程式專案，並將控制項 <xref:System.Windows.Forms.Button> 、 <xref:System.Windows.Forms.CheckBox> 控制項和控制項新增 <xref:System.Windows.Forms.RadioButton> 至表單。  
  
2. 從表單上的按鈕，呼叫程式 `TestObject` 。  
  
3. 將下列程式碼新增至您的表單：  
  
     [!code-vb[VbVbalrOOP#95](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#95)]  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Information.TypeName%2A>
- [使用字串名稱呼叫屬性或方法](calling-a-property-or-method-using-a-string-name.md)
- [Object Data Type](../../../language-reference/data-types/object-data-type.md)
- [If...Then...Else 陳述式](../../../language-reference/statements/if-then-else-statement.md)
- [String 資料類型](../../../language-reference/data-types/string-data-type.md)
- [Integer 資料類型](../../../language-reference/data-types/integer-data-type.md)
