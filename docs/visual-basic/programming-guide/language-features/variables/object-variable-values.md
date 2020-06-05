---
title: 物件變數值
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], values
- values [Visual Basic], of object variables
- data types [Visual Basic], object variable
- variables [Visual Basic], object
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
ms.openlocfilehash: 1dd3e8cd68086fe116daf0678a1a19881f1ae9c3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410344"
---
# <a name="object-variable-values-visual-basic"></a>物件變數值 (Visual Basic)
[Object 資料類型](../../../language-reference/data-types/object-data-type.md)的變數可以參考任何類型的資料。 您儲存在變數中的值 `Object` 會保留在記憶體中的其他位置，而變數本身則會保存資料的指標。  
  
## <a name="object-classifier-functions"></a>物件分類函數  
 Visual Basic 提供的函式會傳回變數所 `Object` 參考的資訊，如下表所示。  
  
|函式|如果物件變數參考，則傳回 True。|  
|--------------|---------------------------------------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A>|值的陣列，而不是單一值|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A>|[日期資料類型](../../../language-reference/data-types/date-data-type.md)值，或可解讀為日期和時間值的字串|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|類型的物件 <xref:System.DBNull> ，代表遺漏或不存在的資料|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A>|例外狀況物件，其衍生自<xref:System.Exception>|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A>|[沒有，也](../../../language-reference/nothing.md)就是目前沒有任何物件指派給變數|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|可以解讀為數字的數位或字串|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A>|參考型別（例如字串、陣列、委派或類別型別）|  
  
 您可以使用這些函式來避免將不正確值提交給作業或程式。  
  
## <a name="typeof-operator"></a>TypeOf 運算子  
 您也可以使用[TypeOf 運算子](../../../language-reference/operators/typeof-operator.md)來判斷物件變數目前是否參考特定的資料類型。 `TypeOf` `Is` `True` 如果運算元的執行時間類型衍生自或會執行指定的類型，則 ... 運算式會評估為。  
  
 下列範例會 `TypeOf` 在參考值和參考型別的物件變數上使用。  
  
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
  
 物件變數會 `num` 參考型別的資料 `Integer` ，而則 `frm` 是指類別的物件 <xref:System.Windows.Forms.Form> 。  
  
## <a name="object-arrays"></a>物件陣列  
 您可以宣告和使用 `Object` 變數陣列。 當您需要處理各種不同的資料類型和物件類別時，這會很有用。 陣列中的所有元素都必須具有相同的宣告資料類型。 將此資料類型宣告為，可 `Object` 讓您將物件和類別實例與陣列中的其他資料類型一起儲存。  
  
## <a name="see-also"></a>另請參閱

- [物件變數](object-variables.md)
- [物件變數宣告](object-variable-declaration.md)
- [物件變數指派](object-variable-assignment.md)
- [如何：參考物件目前的執行個體](how-to-refer-to-the-current-instance-of-an-object.md)
- [如何：決定物件變數參考的型別](how-to-determine-what-type-an-object-variable-refers-to.md)
- [如何：判斷兩個物件是否關聯](how-to-determine-whether-two-objects-are-related.md)
- [如何：判斷兩個物件是否相同](how-to-determine-whether-two-objects-are-identical.md)
- [資料類型](../data-types/index.md)
