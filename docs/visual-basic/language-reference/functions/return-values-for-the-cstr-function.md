---
title: "Return Values for the CStr Function (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "times, CStr Function return values"
  - "type conversion"
  - "dates [Visual Basic], CStr Function return values"
  - "CStr function"
  - "strings [Visual Basic], return value"
  - "Date data type, converting"
  - "dates [Visual Basic]"
  - "String data type, converting"
ms.assetid: 3aa744e7-1419-45d5-85e3-e5abc2953673
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Return Values for the CStr Function (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

下表說明 `CStr` 針對不同資料型別之 `expression` 所傳回的值：  
  
|如果 `expression` 型別是|`CStr` 傳回|  
|-------------------------|---------------|  
|[Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|包含「True」或「False」的字串。|  
|[Date Data Type](../../../visual-basic/language-reference/data-types/date-data-type.md)|包含以系統簡短日期格式表示之 `Date` 數值 \(日期和時間\) 的字串。|  
|[Numeric Data Types](../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)|表示數字的字串。|  
  
## CStr 和 Date  
 `Date` 型別一律會包含日期和時間資訊。  為了方便進行型別轉換，Visual Basic 將 1\/1\/0001 \(1 年 1 月 1 日\) 視為日期的「*中性值*」\(Neutral Value\)，將 00:00:00 \(午夜\) 視為時間的中性值。  `CStr` 不包括所產生字串中的中性值。  例如，如果您將 `#January 1, 0001 9:30:00#` 轉換為字串，結果會是 "9:30:00 AM"；日期資訊會隱藏。  不過，原始 `Date` 值中還是保留日期資訊，您可使用如 <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> 的函式來復原它。  
  
> [!NOTE]
>  `CStr` 函式會根據應用程式的目前文化特性設定來執行其轉換。  若要在特定文化特性中取得數字的字串表示，請使用數字的 `ToString(IFormatProvider)` 方法。  例如，將型別 `Double` 的值轉換成 `String` 時，請使用 <xref:System.Double.ToString%2A?displayProperty=fullName>。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md)   
 [Date Data Type](../../../visual-basic/language-reference/data-types/date-data-type.md)