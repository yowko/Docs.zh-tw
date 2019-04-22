---
title: Boolean 資料類型 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.FALSE
- vb.TRUE
- vb.Boolean
helpviewer_keywords:
- Boolean data type
- Boolean values [Visual Basic], False keyword
- False keyword [Visual Basic]
- True keyword [Visual Basic]
- Boolean values [Visual Basic], True keyword
ms.assetid: 4858e630-4813-4216-a55e-f4d0feb884e4
ms.openlocfilehash: 7b64302d801a08f976de0ec969983c821f7a8471
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58841211"
---
# <a name="boolean-data-type-visual-basic"></a>Boolean 資料類型 (Visual Basic)
可以只保留值`True`或`False`。 關鍵字`True`並`False`對應至兩個狀態的`Boolean`變數。  
  
## <a name="remarks"></a>備註  
 使用[布林資料類型 (Visual Basic)](../../../visual-basic/language-reference/data-types/boolean-data-type.md)是/否或是開/關包含兩個狀態的值，例如 true/false。  
  
 `Boolean` 的預設值為 `False`。  
  
 `Boolean` 值不會儲存為 數字，並儲存的值並非為等同於數字。 您不需撰寫程式碼，以針對對等數值`True`和`False`。 可能的話，您應該限制的使用方式`Boolean`它們設計的邏輯值的變數。  
  
## <a name="type-conversions"></a>類型轉換  
 當 Visual Basic 數值資料型別將值轉換成`Boolean`，0 會變成`False`和所有其他值會變成`True`。 當 Visual Basic 會將轉換`Boolean`為數字類型，值`False`會變成 0 和`True`變成-1。  
  
 當您將轉換之間`Boolean`值和數值資料類型，請記住，.NET Framework 轉換方法不一定會產生與 Visual Basic 轉換關鍵字相同的結果。 這是因為 Visual Basic 轉換會保留與舊版相容的行為。 如需詳細資訊，請參閱"布林類型不會無法轉換以數值類型正確 」 中[疑難排解資料型別](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)。  
  
## <a name="programming-tips"></a>程式設計提示  
  
-   **負數的數字。** `Boolean` 不是數值類型，因此無法表示為負數值。 在任何情況下，您不應該使用`Boolean`來保存數字值。  
  
-   **類型字元。** `Boolean` 沒有任何常值類型字元或識別項類型字元。  
  
-   **Framework 型別。** 在 .NET Framework 中對應的類型為 <xref:System.Boolean?displayProperty=nameWithType> 結構。  
  
## <a name="example"></a>範例  
 在下列範例中，`runningVB`是`Boolean`儲存是/否設定簡單的變數。  
  
```  
Dim runningVB As Boolean  
' Check to see if program is running on Visual Basic engine.  
If scriptEngine = "VB" Then  
    runningVB = True  
End If  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Boolean?displayProperty=nameWithType>
- [資料類型](../../../visual-basic/language-reference/data-types/index.md)
- [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [有效率地使用資料類型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [資料類型的疑難排解](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [CType 函式](../../../visual-basic/language-reference/functions/ctype-function.md)
