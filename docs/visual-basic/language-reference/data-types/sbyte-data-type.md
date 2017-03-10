---
title: "SByte Data Type (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.sbyte"
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
  - "SByte data type"
ms.assetid: 5c38374a-18a1-4cc2-b493-299e3dcaa60f
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# SByte Data Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

存放帶正負號的 8 位元 \(1 位元組\) 整數，範圍從 \-128 到 127。  
  
## 備註  
 使用 `SByte` 資料型別所包含的整數值，不需要 `Integer` 的完整資料寬度或甚至 `Short` 的一半資料寬度。  在某些情況下，Common Language Runtime 也許能夠將您的 `SByte` 變數緊緊疊在一起，避免耗用記憶體。  
  
 `SByte` 的預設值為 0。  
  
## 程式設計提示  
  
-   **符合 CLS 標準：** `SByte` 資料型別不屬於 [語言獨立性以及與語言無關的元件](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\) 的一部分，所以符合 CLS 標準的程式碼不可以採納使用此資料型別的元件。  
  
-   **擴展：** `SByte` 資料型別會擴展成 `Short`、`Integer`、`Long`、`Decimal`、`Single` 和 `Double`。  這表示您可以將 `SByte` 轉換成這些類型的任何一項，而不會發生 <xref:System.OverflowException?displayProperty=fullName> 錯誤。  
  
-   **型別字元：** `SByte` 沒有常值 \(Literal\) 型別字元或識別項型別字元。  
  
-   **架構型別。** 在 .NET Framework 中對應的型別為 <xref:System.SByte?displayProperty=fullName> 結構。  
  
## 請參閱  
 <xref:System.SByte?displayProperty=fullName>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Short Data Type](../../../visual-basic/language-reference/data-types/short-data-type.md)   
 [Integer Data Type](../../../visual-basic/language-reference/data-types/integer-data-type.md)   
 [Long Data Type](../../../visual-basic/language-reference/data-types/long-data-type.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)