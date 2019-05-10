---
title: Double 資料類型 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Double
helpviewer_keywords:
- 'identifier type characters [Visual Basic], #'
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- 0 characters [Visual Basic], trailing
- literal type characters [Visual Basic], R
- data types [Visual Basic], assigning
- Double data type [Visual Basic]
- '# identifier type character'
- double-precision numbers
- floating-point numbers [Visual Basic], Double data type
- R literal type character [Visual Basic]
- zeros, trailing
- Double data type
ms.assetid: 0c5670f7-fcb1-453a-bef1-374730cd38fd
ms.openlocfilehash: 6273f6c9e71f286bdbebc3fe1953988b43de3101
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663210"
---
# <a name="double-data-type-visual-basic"></a>Double 資料類型 (Visual Basic)
保存帶正負號的 IEEE 64 位元 （8 個位元組） 雙精確度浮點數，範圍從-1.79769313486231570 e + 308 到-4.94065645841246544-324 負值進出 4.94065645841246544-324 1.79769313486231570 e + 308 到正的數值。 雙精度數字儲存的是實數的近似值。  
  
## <a name="remarks"></a>備註  
 `Double`資料類型提供許多最大和最小可能的範圍。  
  
 `Double` 的預設值為 0。  
  
## <a name="programming-tips"></a>程式設計提示  
  
- **有效位數。** 當您使用浮點數時，請記得它們在記憶體中不一定有精確的表示法。 這可能會導致非預期的結果從某些作業，例如要做數值比較，`Mod`運算子。 如需詳細資訊，請參閱 <<c0> [ 疑難排解資料型別](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)。  
  
- **尾端零。** 浮點資料類型沒有任何的尾端零個字元的內部表示法。 比方說，它們無法區分 4.2000 與 4.2。 因此，尾端零字元不會出現在顯示或列印的浮點值。  
  
- **類型字元。** 將常值類型字元 `R` 附加到常值，會強制其成為 `Double` 資料類型。 例如，如果整數值，後面跟著`R`的值變更為`Double`。  
  
    ```  
    ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:  
    Dim dub As Double = 4.0R  
    ```  
  
     將識別項類型字元 `#` 附加到任何識別項，會強制其成為 `Double`。 在下列範例中，變數`num`型別為`Double`:  
  
    ```  
    Dim num# = 3  
    ```  
  
- **Framework 型別。** 在 .NET Framework 中對應的類型為 <xref:System.Double?displayProperty=nameWithType> 結構。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Double?displayProperty=nameWithType>
- [資料類型](../../../visual-basic/language-reference/data-types/index.md)
- [Decimal 資料類型](../../../visual-basic/language-reference/data-types/decimal-data-type.md)
- [Single 資料類型](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [有效率地使用資料類型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [資料類型的疑難排解](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [類型字元](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
