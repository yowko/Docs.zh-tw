---
title: "Short Data Type (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Short"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "numbers, whole"
  - "whole numbers"
  - "integral data types"
  - "integer numbers"
  - "numbers, integer"
  - "integers, data types"
  - "integers, types"
  - "data types [Visual Basic], integral"
  - "S literal type character"
  - "Short data type"
  - "literal type characters, S"
ms.assetid: 65fcbcf3-a841-400e-885e-301497729a8b
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# Short Data Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

存放帶正負號的 16 位元 \(2 位元組\) 整數，範圍從 \-32,768 到 32,767。  
  
## 備註  
 使用 `Short` 資料型別，以包含不需要 `Integer` 之完整資料寬度的整數值。  在某些情況下，Common Language Runtime 可以將您的 `Short` 變數緊緊疊在一起，避免耗用記憶體。  
  
 `Short` 的預設值為 0。  
  
## 程式設計提示  
  
-   **擴展：** `Short` 資料型別可擴展至 `Integer`、`Long`、`Decimal`、`Single` 或 `Double`。  這表示您可以將 `Short` 轉換成這些類型的任何一項，而不會發生 <xref:System.OverflowException?displayProperty=fullName> 錯誤。  
  
-   **型別字元。** 將常值型別字元 `S` 附加到常值會強制其成為 `Short` 資料型別。  `Short` 沒有識別項型別字元。  
  
-   **架構型別。** 在 .NET Framework 中對應的型別為 <xref:System.Int16?displayProperty=fullName> 結構。  
  
## 請參閱  
 <xref:System.Int16?displayProperty=fullName>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Integer Data Type](../../../visual-basic/language-reference/data-types/integer-data-type.md)   
 [Long Data Type](../../../visual-basic/language-reference/data-types/long-data-type.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)