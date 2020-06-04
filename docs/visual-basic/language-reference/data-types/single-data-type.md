---
title: Single 資料類型
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
ms.openlocfilehash: ecb0f5f6416a2dd4ddd6888cb80ed3ac11ee58df
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415527"
---
# <a name="single-data-type-visual-basic"></a>字串資料類型 (Visual Basic)

保存已簽署的 IEEE 32 位（4個位元組）單精確度浮點數，範圍介於-3.4028235 E + 38 到-1.401298 E-45 的值中，負值和從 1.401298 E-45 到 3.4028235 E + 38 的正值。 單精確度浮點數會儲存實數的近似值。  
  
## <a name="remarks"></a>備註  

 使用 `Single` 資料類型來包含不需要完整資料寬度的浮點值 `Double` 。 在某些情況下，通用語言執行時間可能可以將您的 `Single` 變數緊密地結合在一起，並節省記憶體耗用量。  
  
 `Single` 的預設值為 0。  
  
## <a name="programming-tips"></a>程式設計提示  
  
- **精密.** 當您使用浮點數時，請記住它們不一定會在記憶體中有精確的標記法。 這可能會導致某些作業產生非預期的結果，例如值比較和 `Mod` 運算子。 如需詳細資訊，請參閱針對[資料類型進行疑難排解](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)。  
  
- **加寬.** `Single`資料類型會擴大為 `Double` 。 這表示您可以將轉換 `Single` 成， `Double` 而不會 <xref:System.OverflowException?displayProperty=nameWithType> 發生錯誤。  
  
- **尾端零。** 浮點資料類型沒有尾端0字元的任何內部標記法。 例如，它們不會區分4.2000 和4.2。 因此，當您顯示或列印浮點值時，不會顯示尾端的0個字元。  
  
- **輸入字元。** 將常值類型字元 `F` 附加到常值，會強制其成為 `Single` 資料類型。 將識別項類型字元 `!` 附加到任何識別項，會強制其成為 `Single`。  
  
- **架構類型：** 在 .NET Framework 中對應的類型為 <xref:System.Single?displayProperty=nameWithType> 結構。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Single?displayProperty=nameWithType>
- [資料類型](index.md)
- [Decimal 資料類型](decimal-data-type.md)
- [Double 資料類型](double-data-type.md)
- [Type Conversion Functions](../functions/type-conversion-functions.md)
- [轉換摘要](../keywords/conversion-summary.md)
- [有效率地使用資料類型](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [疑難排解資料類型的問題](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
