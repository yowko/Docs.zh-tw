---
title: "CStr 函式的傳回值 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b498c9b1b7916467c96ed2c645c7131192a5e8b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a>CStr 函式的傳回值 (Visual Basic)
下表描述的傳回值`CStr`不同的資料類型的`expression`。  
  
|如果`expression`型別|`CStr`傳回|  
|-----------------------------|--------------------|  
|[Boolean 資料類型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|字串，包含"True"或者"False"。|  
|[Date 資料類型](../../../visual-basic/language-reference/data-types/date-data-type.md)|字串，包含`Date`系統的簡短日期格式的值 （日期和時間）。|  
|[數值資料類型](../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)|表示數字的字串。|  
  
## <a name="cstr-and-date"></a>CStr 和日期  
 `Date`類型一定會包含日期和時間資訊。 類型轉換的目的而言，Visual Basic 視為 1/1/0001 (1 年的 1 年)*中性值*日期，和 00:00:00 （午夜） 是中性值的時間。 `CStr`不產生的字串中包含相關的值。 例如，如果您要轉換`#January 1, 0001 9:30:00#`為字串，結果會是 「 上午 9:30:00"; 隱藏日期資訊。 不過，將日期資訊是仍會出現在原始`Date`值，並可以復原與函式例如<xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>。  
  
> [!NOTE]
>  `CStr`函式會執行轉換取決於應用程式的目前文化特性設定。 若要取得特定文化特性中的數字的字串表示，使用數字的`ToString(IFormatProvider)`方法。 例如，使用<xref:System.Double.ToString%2A?displayProperty=nameWithType>轉換類型的值時`Double`至`String`。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>  
 [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Boolean 資料類型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)  
 [Date 資料類型](../../../visual-basic/language-reference/data-types/date-data-type.md)
