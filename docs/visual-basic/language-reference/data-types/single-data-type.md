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
ms.openlocfilehash: 98433c0f1d1008664bb994f3b43fe48a753a432c
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44200759"
---
# <a name="single-data-type-visual-basic"></a>字串資料類型 (Visual Basic)
保存帶正負號的 IEEE 32 位元 （4 個位元組） 單精確度浮點數，值範圍從-3.4028235E + 38 到-1.401298E-45 負值，以及從 1.401298E-45 到 3.4028235E + 38 的正數值。 單精確度數字儲存的是實數的近似值。  
  
## <a name="remarks"></a>備註  
 使用`Single`資料類型可包含不需要完整的資料寬度的浮點值`Double`。 在某些情況下的 common language runtime 可能可以將封裝您`Single`緊密合作，並將記憶體耗用量儲存的變數。  
  
 `Single` 的預設值為 0。  
  
## <a name="programming-tips"></a>程式設計提示  
  
-   **有效位數。** 當您使用浮點數時，記住其在記憶體中不一定有精確的表示法。 這可能會導致非預期的結果從某些作業，例如要做數值比較，`Mod`運算子。 如需詳細資訊，請參閱 <<c0> [ 疑難排解資料型別](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)。  
  
-   **擴展。** `Single`資料類型可擴展為`Double`。 這表示您可以將轉換`Single`要`Double`而不會發生<xref:System.OverflowException?displayProperty=nameWithType>時發生錯誤。  
  
-   **尾端零。** 浮點資料類型沒有任何結尾 0 字元的內部表示法。 比方說，它們無法區分 4.2000 與 4.2。 因此，結尾 0 字元時，沒有出現在顯示或列印浮點數的值。  
  
-   **類型字元。** 將常值類型字元 `F` 附加到常值，會強制其成為 `Single` 資料類型。 將識別項類型字元 `!` 附加到任何識別項，會強制其成為 `Single`。  
  
-   **Framework 型別。** 在 .NET Framework 中對應的類型為 <xref:System.Single?displayProperty=nameWithType> 結構。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Single?displayProperty=nameWithType>  
 [資料類型](../../../visual-basic/language-reference/data-types/index.md)  
 [Decimal 資料類型](../../../visual-basic/language-reference/data-types/decimal-data-type.md)  
 [Double 資料類型](../../../visual-basic/language-reference/data-types/double-data-type.md)  
 [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [有效率地使用資料類型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [資料類型的疑難排解](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
