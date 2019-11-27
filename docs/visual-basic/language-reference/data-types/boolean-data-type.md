---
title: Boolean 資料類型
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
ms.openlocfilehash: 5d05514207c5d07e81aab897f40f728570f6bd87
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347852"
---
# <a name="boolean-data-type-visual-basic"></a>Boolean 資料類型 (Visual Basic)

保留只能 `True` 或 `False`的值。 `True` 和 `False` 的關鍵字會對應到 `Boolean` 變數的兩種狀態。  
  
## <a name="remarks"></a>備註  

 使用[布林資料類型（Visual Basic）](../../../visual-basic/language-reference/data-types/boolean-data-type.md)來包含兩個狀態值： true/false、yes/no 或 on/off。  
  
 `Boolean` 的預設值為 `False`。  
  
 `Boolean` 值不會儲存為數字，而且儲存的值不會等同于數位。 您絕對不應該撰寫依賴對等數值進行 `True` 和 `False`的程式碼。 可能的話，您應該將 `Boolean` 變數的使用限制為其設計的邏輯值。  
  
## <a name="type-conversions"></a>類型轉換  

 當 Visual Basic 將數值資料類型值轉換成 `Boolean`時，0會變成 `False`，而所有其他值會變成 `True`。 當 Visual Basic 將 `Boolean` 值轉換為數數值型別時，`False` 會變成0，而 `True` 會變成-1。  
  
 當您在 `Boolean` 值和數值資料類型之間進行轉換時，請記住，.NET Framework 轉換方法不一定會產生與 Visual Basic 轉換關鍵字相同的結果。 這是因為 Visual Basic 轉換會保留與先前版本相容的行為。 如需詳細資訊，請參閱[疑難排解資料類型](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)中的「布林值類型未正確轉換為數數值型別」。  
  
## <a name="programming-tips"></a>程式設計提示  
  
- **負數。** `Boolean` 不是數數值型別，而且不能代表負值。 在任何情況下，您不應該使用 `Boolean` 來保存數值。  
  
- **輸入字元。** `Boolean` 沒有常數值型別字元或識別項型別字元。  
  
- **架構類型。** 在 .NET Framework 中對應的類型為 <xref:System.Boolean?displayProperty=nameWithType> 結構。  
  
## <a name="example"></a>範例  

 在下列範例中，`runningVB` 是 `Boolean` 變數，它會儲存簡單的 [是/否] 設定。  
  
```vb  
Dim runningVB As Boolean  
' Check to see if program is running on Visual Basic engine.  
If scriptEngine = "VB" Then  
    runningVB = True  
End If  
```  
  
## <a name="see-also"></a>請參閱

- <xref:System.Boolean?displayProperty=nameWithType>
- [資料類型](../../../visual-basic/language-reference/data-types/index.md)
- [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [有效率地使用資料類型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [資料類型的疑難排解](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [CType 函式](../../../visual-basic/language-reference/functions/ctype-function.md)
