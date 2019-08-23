---
title: CStr 函式的傳回值 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- times [Visual Basic], CStr Function return values
- type conversion [Visual Basic]
- dates [Visual Basic], CStr Function return values
- CStr function
- strings [Visual Basic], return value
- Date data type [Visual Basic], converting
- dates [Visual Basic]
- String data type [Visual Basic], converting
ms.assetid: 3aa744e7-1419-45d5-85e3-e5abc2953673
ms.openlocfilehash: cd525ea5a295411e509f3bc37285675d15a8c4f4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930042"
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a>CStr 函式的傳回值 (Visual Basic)
下表描述`CStr`適用于之`expression`不同資料類型的傳回值。  
  
|如果`expression`類型為|`CStr` 傳回|  
|-----------------------------|--------------------|  
|[Boolean 資料類型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|包含 "True" 或 "False" 的字串。|  
|[Date 資料類型](../../../visual-basic/language-reference/data-types/date-data-type.md)|字串, 包含`Date`您系統的簡短日期格式的值 (日期和時間)。|  
|[數值資料類型](../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)|表示數位的字串。|  
  
## <a name="cstr-and-date"></a>CStr 和 Date  
 `Date`類型一律同時包含日期和時間資訊。 基於類型轉換的目的, Visual Basic 會將 1/1/0001 (第1年1月1日) 視為日期的*中性值*, 而 00:00:00 (午夜) 則是時間的中性值。 `CStr`不會在產生的字串中包含中性值。 例如, 如果您將轉換`#January 1, 0001 9:30:00#`成字串, 則結果會是 "9:30:00 AM"; 日期資訊會隱藏起來。 不過, 日期資訊仍然會出現在原始`Date`值中, 而且可以使用<xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>之類的函數來復原。  
  
> [!NOTE]
> `CStr`函式會根據應用程式目前的文化特性設定來執行其轉換。 若要取得特定文化特性之數位的字串表示, 請使用數位的`ToString(IFormatProvider)`方法。 例如, 將類型<xref:System.Double.ToString%2A?displayProperty=nameWithType> `Double`的值轉換為`String`時, 請使用。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>
- [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Boolean 資料類型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [Date 資料類型](../../../visual-basic/language-reference/data-types/date-data-type.md)
