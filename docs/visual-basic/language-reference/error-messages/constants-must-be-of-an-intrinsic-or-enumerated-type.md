---
title: 常數必須是內建或列舉類型，而不是類別、結構、型別參數或陣列類型
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30424
- bc30424
helpviewer_keywords:
- BC30424
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 702472751810c2d2bd08ece944ef0ffafc2049b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a>常數必須是內建或列舉類型，而不是類別、結構、型別參數或陣列類型
您嘗試將常數宣告為類別、 結構或陣列型別，或包含泛型類型定義的型別參數。  
  
 常數必須是內建類型 (`Boolean`， `Byte`， `Date`， `Decimal`， `Double`， `Integer`， `Long`， `Object`， `SByte`， `Short`， `Single`， `String`， `UInteger`， `ULong`，或`UShort`)，或`Enum`類型根據其中一個整數類資料類型。  
  
 **錯誤 ID:** BC30424  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  宣告常數作為內建或`Enum`型別。  
  
2.  常數也可以是特殊值，例如`True`， `False`，或`Nothing`。 編譯器會考慮這些預先定義的值是適當的內建類型。  
  
## <a name="see-also"></a>另請參閱  
 [常數和列舉](../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [資料類型](../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [資料類型](../../../visual-basic/language-reference/data-types/data-type-summary.md)
