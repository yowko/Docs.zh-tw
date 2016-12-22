---
title: "Integer Data Type (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Integer"
  - "Integer"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "numbers, whole"
  - "enumerated values"
  - "whole numbers"
  - "integral data types"
  - "integer numbers"
  - "numbers, integer"
  - "integers, data types"
  - "literal type characters, I"
  - "integers, types"
  - "data types [Visual Basic], integral"
  - "% identifier type character"
  - "data types [Visual Basic], assigning"
  - "identifier type characters, %"
  - "I literal type character"
  - "Integer data type"
ms.assetid: a8f233b4-4be3-455c-861b-05af2fbb6c60
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Integer Data Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

保存帶正負號的 32 位元 \(4 位元組\) 整數，值的範圍從 \-2,147,483,648 到 2,147,483,647。  
  
## 備註  
 `Integer` 資料類型可對 32 位元處理器提供最佳效能。  其他整數類資料類型在記憶體中載入和儲存的速度較慢。  
  
 `Integer` 的預設值為 0。  
  
## 程式設計提示  
  
-   **Interop 考量：**如果您要使用的元件不是針對 .NET Framework 所撰寫 \(例如 Automation 或 COM 物件\)，請記住，`Integer` 在其他環境中會有不同的資料寬度 \(16 位元\)。  如果您要將 16 位元引數傳遞至這類元件，請在新的 Visual Basic 程式碼中將它宣告為 `Short`，而不是 `Integer`。  
  
-   **擴展：** `Integer` 資料類型可擴展為 `Long`、`Decimal`、`Single` 或 `Double`。  這表示，您可以將 `Integer` 轉換成這些類型的任何一種，而不會發生 <xref:System.OverflowException?displayProperty=fullName> 錯誤。  
  
-   **類型字元：**將常值類型字元 `I` 附加到常值，會強制其成為 `Integer` 資料類型。  將識別項類型字元 `%` 附加到任何識別項，會強制其成為 `Integer`。  
  
-   **架構類型：**在 .NET Framework 中對應的類型為 <xref:System.Int32?displayProperty=fullName> 結構。  
  
## 範圍  
 如果您嘗試將整數類資料類型的變數設定為超出該類型範圍的數字，則會發生錯誤。  如果您嘗試將它設定為分數，則數字就會四捨五入為最接近的整數值。  如果數字與兩個整數值同樣接近，則該直將會四捨五入為最接近的雙數。  這種行為會將一致四捨五入單向中點值得出的四捨五入錯誤降至最低。  下列程式碼將示範四捨五入的範例。  
  
```  
' The valid range of an Integer variable is -2147483648 through +2147483647.  
Dim k As Integer  
' The following statement causes an error because the value is too large.  
k = 2147483648  
' The following statement sets k to 6.  
k = 5.9  
' The following statement sets k to 4  
k = 4.5  
' The following statement sets k to 6  
' Note, Visual Basic uses banker’s rounding (toward nearest even number)  
k = 5.5  
```  
  
## 請參閱  
 <xref:System.Int32?displayProperty=fullName>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Long Data Type](../../../visual-basic/language-reference/data-types/long-data-type.md)   
 [Short Data Type](../../../visual-basic/language-reference/data-types/short-data-type.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)