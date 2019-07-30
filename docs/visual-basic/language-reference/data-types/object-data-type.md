---
title: 物件資料類型 (Visual Basic)
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
ms.openlocfilehash: 1ac906494c49810e3d389591b1044f412e7320bc
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/26/2019
ms.locfileid: "68513053"
---
# <a name="object-data-type"></a>Object Data Type

保留參考物件的位址。 您可以將任何參考型別 (字串、陣列、類別或介面) 指派給`Object`變數。 變數也可以參考任何實數值型別 (數值、 `Boolean`、 `Char`、 `Date`、結構或列舉) 的資料。 `Object`

## <a name="remarks"></a>備註

`Object`資料類型可以指向任何資料類型的資料, 包括您的應用程式可辨識的任何物件實例。 當`Object`您在編譯時期不知道變數可能指向的資料類型時, 請使用。

的預設值`Object`為`Nothing` (null 參考)。

## <a name="data-types"></a>資料類型

您可以將任何資料類型的變數、常數或運算式指派給`Object`變數。 若要判斷`Object`變數目前所參考的資料類型, 您可以<xref:System.Type.GetTypeCode%2A>使用<xref:System.Type?displayProperty=nameWithType>類別的方法。 下列範例將說明這點。

```vb
Dim myObject As Object
' Suppose myObject has now had something assigned to it.
Dim datTyp As Integer
datTyp = Type.GetTypeCode(myObject.GetType())
```

`Object`資料類型是參考型別。 不過, 當參考實`Object`數值型別的資料時, Visual Basic 會將變數視為實數值型別。

## <a name="storage"></a>存放裝置

無論它參考的資料類型為何, `Object`變數不會包含資料值本身, 而是值的指標。 它一律會在電腦記憶體中使用四個位元組, 但這不會包含代表變數值之資料的儲存體。 由於使用指標來尋找資料的程式碼, 因此, `Object`存取數值型別的變數會比明確類型的變數稍微慢一點。

## <a name="programming-tips"></a>程式設計提示

- **Interop 考慮。** 如果您要使用的元件不是針對 .NET Framework 所撰寫 (例如 Automation 或 COM 物件), 請記住, 其他環境中的指標類型與 Visual Basic `Object`類型不相容。

- **效能。** 您使用`Object`類型宣告的變數具有足夠的彈性, 可包含任何物件的參考。 不過, 當您在這類變數上叫用方法或屬性時, 一律會產生*晚期繫結*(在執行時間)。 若要強制*早期繫結*(在編譯時期) 和更好的效能, 請使用特定類別名稱宣告變數, 或將它轉換成特定的資料類型。

  當您宣告物件變數時, 請嘗試使用特定的類別類型, <xref:System.OperatingSystem>例如, 而不是一般化`Object`類型。 您也應該使用可用的最特定類別 (例如<xref:System.Windows.Forms.TextBox> <xref:System.Windows.Forms.Control>, 而不是), 以便存取其屬性和方法。 您通常可以使用 **物件瀏覽器**中的 **類別** 清單來尋找可用的類別名稱。

- **加寬.** 所有的資料類型和所有參考類型都會擴大`Object`至資料類型。 這表示您可以將任何類型轉換`Object`成, 而<xref:System.OverflowException?displayProperty=nameWithType>不會遇到錯誤。

  不過, 如果您在實數值型別和`Object`之間進行轉換, Visual Basic 會執行稱為「*裝箱*和*取消裝箱*」的作業, 使執行速度變慢。

- **輸入字元。** `Object`沒有常數值型別字元或識別項型別字元。

- **架構類型。** .NET Framework 中的對應類型是<xref:System.Object?displayProperty=nameWithType>類別。

## <a name="example"></a>範例

下列範例說明`Object`指向物件實例的變數。

```vb
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
- [如何：判斷兩個物件是否相關](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [如何：判斷兩個物件是否相同](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
