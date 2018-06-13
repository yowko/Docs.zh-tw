---
title: 字串資料類型 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Single
helpviewer_keywords:
- Single data type
- F literal type character [Visual Basic]
- trailing zeros
- real numbers
- literal type characters [Visual Basic], F
- trailing 0 characters [Visual Basic]
- identifier type characters [Visual Basic], !
- single-precision numbers
- '! identifier type character'
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- floating-point numbers [Visual Basic], Single data type
- numbers [Visual Basic], real
- zeros, trailing
- numbers [Visual Basic], floating point
ms.assetid: 224a2795-4cd5-496c-8f7a-a4f05a06d45d
ms.openlocfilehash: 770961f225b139aaddf34b42327bca63638c725d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590767"
---
# <a name="single-data-type-visual-basic"></a>字串資料類型 (Visual Basic)
保存帶正負號的 IEEE 32 位元 （4 個位元組） 單精確度浮點數值範圍從-3.4028235 e + 38 到-1.401298-45 負值，並從 1.401298-45 到 3.4028235 e + 38 的正數值。 單精確度數字會儲存實際數字的近似值。  
  
## <a name="remarks"></a>備註  
 使用`Single`資料類型可包含不需要完整的資料寬度的浮點值`Double`。 在某些情況下 common language runtime 可以 pack 您`Single`緊密，並將記憶體耗用量儲存變數。  
  
 `Single` 的預設值為 0。  
  
## <a name="programming-tips"></a>程式設計提示  
  
-   **有效位數。** 當您使用浮點數值，請記住它們在記憶體中不一定有精確的表示。 這可能會導致非預期的結果從某些作業，例如值比較而`Mod`運算子。 如需詳細資訊，請參閱[疑難排解資料型別](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)。  
  
-   **擴展。** `Single`資料類型可擴展成`Double`。 這表示您可以將轉換`Single`至`Double`而不會發生<xref:System.OverflowException?displayProperty=nameWithType>錯誤。  
  
-   **尾端零。** 浮點資料類型沒有任何結尾 0 字元的內部表示法。 例如，它們不會區分 4.2000 與 4.2。 因此，結尾 0 字元並不會顯示當您顯示或列印浮點數的值。  
  
-   **類型字元。** 將常值類型字元 `F` 附加到常值，會強制其成為 `Single` 資料類型。 將識別項類型字元 `!` 附加到任何識別項，會強制其成為 `Single`。  
  
-   **架構類型。** 在 .NET Framework 中對應的類型為 <xref:System.Single?displayProperty=nameWithType> 結構。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Single?displayProperty=nameWithType>  
 [資料類型](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Decimal 資料類型](../../../visual-basic/language-reference/data-types/decimal-data-type.md)  
 [Double 資料類型](../../../visual-basic/language-reference/data-types/double-data-type.md)  
 [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [有效率地使用資料類型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [資料類型的疑難排解](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
