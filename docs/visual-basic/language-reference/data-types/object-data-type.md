---
title: Object 資料型別 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Object
- vb.Variant
helpviewer_keywords:
- object variables [Visual Basic], Object type
- data types [Visual Basic], assigning
- Object data type
- Object data type [Visual Basic], reference
ms.assetid: 61ea4a7c-3b3d-48d4-adc4-eacfa91779b2
ms.openlocfilehash: 616110145db2796e05509094b1c023daacd68f03
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61751668"
---
# <a name="object-data-type"></a>Object Data Type
包含參考物件的位址。 您可以將任何參考型別 （字串、 陣列、 類別或介面） 指派給`Object`變數。 `Object`變數也可以參考資料的任何實值類型 (數字`Boolean`， `Char`， `Date`、 結構或列舉)。  
  
## <a name="remarks"></a>備註  
 `Object`資料型別可以指向任何資料類型，包括您的應用程式可辨識的任何物件執行個體的資料。 使用`Object`當您在編譯時期不知道何種資料類型的變數可能指向。  
  
 預設值`Object`是`Nothing`（null 參考）。  
  
## <a name="data-types"></a>資料類型  
 您可以指派變數、 常數或運算式的任何資料型別`Object`變數。 若要判斷資料型別`Object`目前參考變數，您可以使用<xref:System.Type.GetTypeCode%2A>方法<xref:System.Type?displayProperty=nameWithType>類別。 下列範例將說明這點。  
  
```  
Dim myObject As Object  
' Suppose myObject has now had something assigned to it.  
Dim datTyp As Integer  
datTyp = Type.GetTypeCode(myObject.GetType())  
```  
  
 `Object`資料型別是參考類型。 不過，Visual Basic 會將`Object`變數設定為當它是指資料的實值類型的實值型別。  
  
## <a name="storage"></a>存放裝置  
 它是指，任何資料型別`Object`變數本身，但而不是值的指標不包含資料值。 它會在電腦記憶體中，一律使用四個位元組，但這不包括表示變數值的資料的儲存體。 因為找到的資料，使用滑鼠指標的程式碼`Object`含有實值型別變數會稍微慢一點，來存取比明確具類型的變數。  
  
## <a name="programming-tips"></a>程式設計提示  
  
- **Interop 考量。** 如果您要使用的元件不是撰寫.NET framework，例如 Automation 或 COM 物件，請記住，在其他環境中的指標類型不相容於 Visual Basic`Object`型別。  
  
- **效能。** 您使用宣告的變數`Object`型別是有足夠的彈性，以包含任何物件的參考。 不過，當您叫用方法或屬性，這類的變數上，您一定會產生*晚期繫結*（在執行階段）。 若要強制*早期繫結*（在編譯時期） 和較佳的效能、 宣告的變數，以特定的類別名稱，或將它轉換成特定資料類型。  
  
     當您宣告物件變數時，嘗試使用特定類別類型，例如<xref:System.OperatingSystem>，而不是 一般化`Object`型別。 您也應該使用最特定的類別使用，例如<xref:System.Windows.Forms.TextBox>而不是<xref:System.Windows.Forms.Control>，如此一來，您可以存取其屬性和方法。 您通常可以使用**類別**列入**物件瀏覽器**來尋找可用的類別名稱。  
  
- **擴展。** 所有的資料類型和所有參考型別會擴展為`Object`資料型別。 這表示您可以將任何類型轉換`Object`而不會發生<xref:System.OverflowException?displayProperty=nameWithType>時發生錯誤。  
  
     不過，如果您實值型別之間進行轉換並`Object`，Visual Basic 執行呼叫的作業*boxing*並*unboxing*，如此一來讓執行速度變慢。  
  
- **類型字元。** `Object` 沒有任何常值類型字元或識別項類型字元。  
  
- **Framework 型別。** .NET Framework 中對應的型別是<xref:System.Object?displayProperty=nameWithType>類別。  
  
## <a name="example"></a>範例  
 下列範例說明`Object`變數指向的物件執行個體。  
  
```  
Dim objDb As Object  
Dim myCollection As New Collection()  
' Suppose myCollection has now been populated.  
objDb = myCollection.Item(1)  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Object>
- [資料類型](../../../visual-basic/language-reference/data-types/index.md)
- [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [有效率地使用資料類型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [如何：判斷兩個物件是否關聯](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [如何：判斷兩個物件是否相同](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
