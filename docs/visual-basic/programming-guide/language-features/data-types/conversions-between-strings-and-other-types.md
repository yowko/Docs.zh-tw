---
title: "Conversions Between Strings and Other Types (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "data type conversion, string"
  - "conversions, type"
  - "string conversion"
  - "conversions, data type"
  - "type conversion, string"
  - "regional options"
ms.assetid: c3a99596-f09a-44a5-81dd-1b89a094f1df
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Conversions Between Strings and Other Types (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

您可以將數值、`Boolean` 或日期\/時間值轉換為 `String`。  如果字串內容可解譯為目的資料型別的有效值，您也可以進行反方向轉換，也就是從字串值轉換為數字、`Boolean` 或 `Date`。  若不是有效值的話，就會發生執行階段錯誤。  
  
 無論方向為何，所有這些指派的轉換都是縮小轉換。  您應使用型別轉換關鍵字 \(`CBool`、`CByte`、`CDate`、`CDbl`、`CDec`、`CInt`、`CLng`、`CSByte`、`CShort`、`CSng`、`CStr`、`CUInt`、`CULng`、`CUShort` 和 `CType`\)。  <xref:Microsoft.VisualBasic.Strings.Format%2A> 和 <xref:Microsoft.VisualBasic.Conversion.Val%2A> 函式讓您更能夠控制字串與數字之間的轉換。  
  
 若您已定義類別或結構，則可定義 `String` 和類別或結構型別之間的型別轉換運算子。  如需詳細資訊，請參閱 [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)。  
  
## 從數字轉換為字串  
 您可以使用 `Format` 函式，將數字轉換為格式化字串，其中不只可包含適當的數字及格式化符號，例如貨幣符號 \(例如 `$`\)、千位分隔符號或「*數字分位符號*」\(Digit Grouping Symbol\) \(例如 `,`\)，以及十進位分隔符號 \(例如 `.`\)。  `Format` 會自動依據 Windows \[**控制台**\] 中指定的 \[**地區選項**\] 設定來使用適當的符號。  
  
 請注意串連 \(`&`\) 運算子 \(Concatenation Operator\) 會將數字隱含地轉換為字串，如下列範例所示：  
  
```  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## 從字串轉換為數字  
 您可以使用 `Val` 函式將字串中數字明確地轉換為數字。  `Val` 會讀取字串，直至找到非數字、空白、標籤、換行或句號的字元為止。  循序項 "&O" 及 "&H" 會更改數字系統的基底並結束掃描。  在停止讀取之後，`Val` 會將所有適當字元轉換為數值。  例如，下列陳述式傳回值 `141.825`。  
  
 `Val("   14   1.825 miles")`  
  
 當 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 將字串轉換為數值時，會使用 Windows \[**控制台**\] 所指定的 \[**地區選項**\] 設定來解譯千分位分隔符號、小數點分隔符及貨幣符號。  這表示轉換在某個設定下會成功，但在另一個設定下則不一定。  例如，英語 \(美國\) 地區設定可接受 `"$14.20"`，但法文地區設定就不接受。  
  
## 請參閱  
 [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Implicit and Explicit Conversions](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [How to: Convert an Object to Another Type in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)   
 [Array Conversions](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)   
 [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [以 .NET Framework 為基礎的國際應用程式簡介](/visual-studio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)