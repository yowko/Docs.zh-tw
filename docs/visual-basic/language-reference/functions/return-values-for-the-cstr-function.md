---
title: 傳回 CStr 函式的值
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
ms.openlocfilehash: 6039ba3f6bd1c364db818807604ee0851bc23d50
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406379"
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a>CStr 函式的傳回值 (Visual Basic)
下表描述 `CStr` 適用于之不同資料類型的傳回值 `expression` 。  
  
|如果 `expression` 類型為|`CStr` 傳回|  
|-----------------------------|--------------------|  
|[Boolean 資料類型](../data-types/boolean-data-type.md)|包含 "True" 或 "False" 的字串。|  
|[Date 資料類型](../data-types/date-data-type.md)|字串 `Date` ，包含您系統的簡短日期格式的值（日期和時間）。|  
|[數值資料類型](../../programming-guide/language-features/data-types/numeric-data-types.md)|表示數位的字串。|  
  
## <a name="cstr-and-date"></a>CStr 和 Date  
 `Date`類型一律同時包含日期和時間資訊。 基於類型轉換的目的，Visual Basic 會將1/1/0001 （第1年1月1日）視為日期的*中性值*，而00:00:00 （午夜）則是時間的中性值。 `CStr`不會在產生的字串中包含中性值。 例如，如果您將轉換 `#January 1, 0001 9:30:00#` 成字串，則結果會是 "9:30:00 AM"; 日期資訊會隱藏起來。 不過，日期資訊仍然會出現在原始值中， `Date` 而且可以使用之類的函數來復原 <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> 。  
  
> [!NOTE]
> 函式會根據 `CStr` 應用程式目前的文化特性設定來執行其轉換。 若要取得特定文化特性之數位的字串表示，請使用數位的 `ToString(IFormatProvider)` 方法。 例如，將 <xref:System.Double.ToString%2A?displayProperty=nameWithType> 類型的值轉換為時，請使用 `Double` `String` 。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>
- [Type Conversion Functions](type-conversion-functions.md)
- [Boolean 資料類型](../data-types/boolean-data-type.md)
- [Date 資料類型](../data-types/date-data-type.md)
