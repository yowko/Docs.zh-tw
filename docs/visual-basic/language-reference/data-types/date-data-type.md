---
title: Date 資料類型 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Date
helpviewer_keywords:
- Date data type
- dates [Visual Basic], Visual Basic data types
- times [Visual Basic], Date data type
- Date literals [Visual Basic]
- data values [Visual Basic]
- times [Visual Basic], Visual Basic data types
- dates [Visual Basic], Date data type
- data types [Visual Basic], assigning
- literals [Visual Basic], Date
- '# specifier for Date literals'
ms.assetid: d9edf5b0-e85e-438b-a1cf-1f321e7c831b
ms.openlocfilehash: b7827206d6e145b559d9716df5ec4a98ac4ea0b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="date-data-type-visual-basic"></a>Date 資料類型 (Visual Basic)
具有 IEEE 64 位元 (8 位元組) 值，以代表從 0001 年 1 月 1 日到 9999 年 12 月 31 日的日期，以及從上午 (午夜) 12:00:00 到下午 11:59:59.9999999 的時間。 每個增量代表西曆日曆 1 年 1 月 1 日開始之後經過 100 奈秒的時間。 最大值代表 10000 年 1 月 1 開始之前的 100 奈秒。  
  
## <a name="remarks"></a>備註  
 使用 `Date` 資料類型可包含日期值、時間值或日期和時間值。  
  
 `Date` 的預設值為 0001 年 1 月 1 日的 0:00:00 (午夜)。  
  
 您可以從 <xref:Microsoft.VisualBasic.DateAndTime> 取得目前的日期和時間。  
  
## <a name="format-requirements"></a>格式需求  
 您必須將 `Date` 常值包含在數字符號 (`# #`) 中。 您必須指定 M/d/yyyy 格式 (例如 `#5/31/1993#`) 或 yyyy-MM-dd (例如 `#1993-5-31#`) 的日期值。 先指定年份時可以使用斜線。  這項需求與您的地區設定和電腦的日期和時間格式設定無關。  
  
 之所以有這項限制，是因為您程式碼的意義絕不應根據您的應用程式執行所在的地區設定而變更。 假設您對 `#3/4/1998#` 的 `Date` 常值進行硬式編碼，並想要讓它代表 1998 年 3 月 4 日。 在使用 mm/dd/yyyy 的地區設定中，3/4/1998 會依照您的需求進行編譯。 但假設您在許多國家 (地區) 部署應用程式。 在使用 dd/mm/yyyy 的地區設定中，您硬式編碼的常值會編譯為 1998 年 4 月 3 日。 在使用 yyyy/mm/dd 的地區設定中，常值將是無效的 (0003 年 4 月 1998 日)，而且會導致編譯器錯誤。  
  
## <a name="workarounds"></a>替代解決辦法  
 若要將 `Date` 常值轉換為您的地區設定或自訂格式，請將常值提供給 <xref:Microsoft.VisualBasic.Strings.Format%2A> 函式，以指定預先定義或使用者定義的日期格式。 下列範例為其示範。  
  
```  
MsgBox("The formatted date is " & Format(#5/31/1993#, "dddd, d MMM yyyy"))  
```  
  
 或者，您可以使用 <xref:System.DateTime> 結構的其中一個多載建構函式，以組合日期和時間值。 下列範例會建立一個值來代表 1993 年 5 月 31 日下午 12:14。  
  
```  
Dim dateInMay As New System.DateTime(1993, 5, 31, 12, 14, 0)  
```  
  
## <a name="hour-format"></a>小時格式  
 您可以指定 12 小時或 24 小時格式的時間值，例如 `#1:15:30 PM#` 或 `#13:15:30#`。 不過，若未指定分或秒，您必須指定 AM 或 PM。  
  
## <a name="date-and-time-defaults"></a>日期和時間預設值  
 如果您未在日期/時間常值中包含日期，Visual Basic 會將值的日期部分設為 0001 年 1 月 1 日。 如果您未在日期/時間常值中包含時間，Visual Basic 會將值的時間部分設為一天的開始，即午夜 (0:00:00)。  
  
## <a name="type-conversions"></a>類型轉換  
 如果您將 `Date` 值轉換為 `String` 類型，Visual Basic 會根據執行階段地區設定所指定的簡短日期格式呈現日期，並根據執行階段地區設定所指定的時間格式 (12 小時制或 24 小時制) 呈現時間。  
  
## <a name="programming-tips"></a>程式設計提示  
  
-   **Interop 考量。** 如果您要使用的元件不是針對 .NET Framework 所撰寫 (例如 Automation 或 COM 物件)，請記住，其他環境中的日期/時間類型與 Visual Basic `Date` 類型並不相融。 如果您要將日期/時間引數傳遞至這類元件，請在新的 Visual Basic 程式碼中將它宣告為 `Double` (而不是 `Date`)，並使用轉換方法 <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> 和 <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType>。  
  
-   **類型字元。** `Date` 沒有任何常值類型字元或識別項類型字元。 不過，編譯器會將包含在數字符號 (`# #`) 內的常值視為 `Date`。  
  
-   **架構類型。** 在 .NET Framework 中對應的類型為 <xref:System.DateTime?displayProperty=nameWithType> 結構。  
  
## <a name="example"></a>範例  
 `Date` 資料類型的變數或常數會同時包含日期和時間。 下列範例將說明這點。  
  
```  
Dim someDateAndTime As Date = #8/13/2002 12:14 PM#  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.DateTime?displayProperty=nameWithType>  
 [資料類型](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [標準日期和時間格式字串](../../../standard/base-types/standard-date-and-time-format-strings.md)  
 [自訂日期和時間格式字串](../../../standard/base-types/custom-date-and-time-format-strings.md)  
 [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [有效率地使用資料類型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
