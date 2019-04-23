---
title: 常數必須是內建或列舉類型，而不是類別、結構、型別參數或陣列類型
ms.date: 07/20/2015
f1_keywords:
- vbc30424
- bc30424
helpviewer_keywords:
- BC30424
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
ms.openlocfilehash: 88bbab2005b464ee97d647f2b4b9be6ff81e2d82
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59299107"
---
# <a name="constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a>常數必須是內建或列舉類型，而不是類別、結構、型別參數或陣列類型
您已嘗試宣告為類別、 結構或陣列類型或型別參數所包含的泛型類型定義的常數。  
  
 常數必須是內建類型 (`Boolean`， `Byte`， `Date`， `Decimal`， `Double`， `Integer`， `Long`， `Object`， `SByte`， `Short`， `Single`， `String`， `UInteger`， `ULong`，或`UShort`)，或有`Enum`以其中一種整數類資料類型為基礎類型。  
  
 **錯誤 ID:** BC30424  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 宣告作為內建常數或`Enum`型別。  
  
2. 常數，也可以是特殊值，例如`True`， `False`，或`Nothing`。 編譯器會考慮這些預先定義的值必須是適當的內建類型。  
  
## <a name="see-also"></a>另請參閱

- [常數和列舉](../../../visual-basic/language-reference/constants-and-enumerations.md)
- [資料類型](../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [資料類型](../../../visual-basic/language-reference/data-types/index.md)
