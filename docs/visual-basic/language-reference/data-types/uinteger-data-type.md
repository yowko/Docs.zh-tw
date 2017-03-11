---
title: "UInteger Data Type | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.uinteger"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "numbers, whole"
  - "UInteger data type"
  - "literal type characters, UI"
  - "whole numbers"
  - "integral data types"
  - "integer numbers"
  - "numbers, integer"
  - "integers, data types"
  - "integers, types"
  - "UI literal type characters"
  - "data types [Visual Basic], integral"
ms.assetid: db7ddd34-4f23-46f5-84dd-8b0f83bb8729
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# UInteger Data Type
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

存放不帶正負號的 32 位元 \(4 位元組\) 整數，其值的範圍是從 0 到 4,294,967,295。  
  
## 備註  
 `UInteger` 資料型別可利用最有效的資料寬度，提供不帶正負號的最大值。  
  
 `UInteger` 的預設值為 0。  
  
## 程式設計提示  
 `UInteger` 和 `Integer` 資料型別在 32 位元處理器上可提供最佳效能，因為其整數型別 \(Integer Type\) 較小 \(`UShort`、`Short`、`Byte` 和 `SByte`\)，即使其使用較少的位元、需要更多載入、儲存和擷取時間。  
  
-   **負數：** 由於 `UInteger` 是不帶正負號的型別，故無法代表負數。  如果您在評估為 `UInteger` 型別的運算式中使用一元 \(Unary\) 減號 \(`-`\) 運算子，則 Visual Basic 會先將運算式轉換為 `Long`。  
  
-   **符合 CLS 標準：** `UInteger` 資料型別不屬於 [語言獨立性以及與語言無關的元件](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\) 的一部分，所以符合 CLS 標準的程式碼不可以採納使用此資料型別的元件。  
  
-   **Interop 考量：** 如果您正在使用不是針對 .NET Framework 所撰寫的元件，例如 Automation 或 COM 物件，請記住，如 `uint` 的型別在其他環境中可以有不同的資料寬度 \(16 位元\)。  如果您要將 16 位元引數傳遞到這類元件，則需將其宣告為 `UShort` 而不是 Managed Visual Basic 程式碼中的 `UInteger`。  
  
-   **擴展：** `UInteger` 資料型別會擴展成 `Long`、`ULong`、`Decimal`、`Single` 和 `Double`。  這表示您可以將 `UInteger` 轉換成這些類型的任何一項，而不會發生 <xref:System.OverflowException?displayProperty=fullName> 錯誤。  
  
-   **型別字元。** 將常值型別字元 `UI` 附加到常值，會強制其成為 `UInteger` 資料型別。  `UInteger` 沒有識別項型別字元。  
  
-   **架構型別。** 在 .NET Framework 中對應的型別為 <xref:System.UInt32?displayProperty=fullName> 結構。  
  
## 請參閱  
 <xref:System.UInt32>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [How to: Call a Windows Function that Takes Unsigned Types](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)