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
ms.openlocfilehash: cc5e5cc437175e9aebfba559488ca74283faa9ad
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870149"
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a>CStr 函式的傳回值 (Visual Basic)

下表描述的 `CStr` 不同資料類型的傳回值 `expression` 。  
  
|如果 `expression` 類型為|`CStr` 傳回|  
|-----------------------------|--------------------|  
|[Boolean 資料類型](../data-types/boolean-data-type.md)|包含 "True" 或 "False" 的字串。|  
|[Date 資料類型](../data-types/date-data-type.md)|字串，包含 `Date` 以您系統的簡短日期格式)  (日期和時間的值。|  
|[數值資料類型](../../programming-guide/language-features/data-types/numeric-data-types.md)|表示數位的字串。|  
  
## <a name="cstr-and-date"></a>CStr 和日期  

 `Date`類型一律包含日期和時間資訊。 基於類型轉換的目的，Visual Basic 會將 1/1/0001 (年1月1日) 為日期的 *中性值* ，而 00:00:00 (午夜) 會是時間的中性值。 `CStr` 未在產生的字串中包含中性值。 例如，如果您轉換 `#January 1, 0001 9:30:00#` 成字串，結果會是 "9:30:00 AM"; 會隱藏日期資訊。 但是，日期資訊仍會存在於原始值中 `Date` ，而且可以使用之類的函數復原 <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> 。  
  
> [!NOTE]
> `CStr`函數會根據應用程式目前的文化特性設定來執行其轉換。 若要取得特定文化特性中數位的字串表示，請使用數位的 `ToString(IFormatProvider)` 方法。 例如，將 <xref:System.Double.ToString%2A?displayProperty=nameWithType> 類型的值轉換為時，請使用 `Double` `String` 。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>
- [Type Conversion Functions](type-conversion-functions.md)
- [Boolean 資料類型](../data-types/boolean-data-type.md)
- [Date 資料類型](../data-types/date-data-type.md)
