---
title: "UShort Data Type (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.ushort"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "numbers, whole"
  - "literal type characters, US"
  - "whole numbers"
  - "integral data types"
  - "integer numbers"
  - "numbers, integer"
  - "integers, data types"
  - "integers, types"
  - "data types [Visual Basic], integral"
  - "UShort data type"
  - "US literal type characters"
ms.assetid: 138db892-665d-4ba8-9cae-d8d91c4a8f39
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# UShort Data Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

存放不帶正負號的 16 位元 \(2 位元組\) 整數，其值的範圍是從 0 到 65,535。  
  
## 備註  
 使用 `UShort` 資料型別，包含對 `Byte` 而言太大的二進位資料。  
  
 `UShort` 的預設值為 0。  
  
## 程式設計提示  
  
-   **負數：** 由於 `UShort` 是不帶正負號的型別，故無法代表負數。  如果您在評估為 `UShort` 型別的運算式中使用一元 \(Unary\) 減號 \(`-`\) 運算子，則 Visual Basic 會先將運算式轉換為 `Integer`。  
  
-   **符合 CLS 標準：** `UShort` 資料型別不屬於 [語言獨立性以及與語言無關的元件](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\) 的一部分，所以符合 CLS 標準的程式碼不可以採納使用此資料型別的元件。  
  
-   **擴展：** `UShort` 資料型別會擴展至 `Integer`、`UInteger`、`Long`、`ULong`、`Decimal`、`Single` 和 `Double`。  這表示您可以將 `UShort` 轉換成這些類型的任何一項，而不會發生 <xref:System.OverflowException?displayProperty=fullName> 錯誤。  
  
-   **型別字元。** 將常值型別字元 `US` 附加到常值，會強制其成為 `UShort` 資料型別。  `UShort` 沒有識別項型別字元。  
  
-   **架構型別。** 在 .NET Framework 中對應的型別為 <xref:System.UInt16?displayProperty=fullName> 結構。  
  
## 請參閱  
 <xref:System.UInt16>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [How to: Call a Windows Function that Takes Unsigned Types](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)