---
title: "Single Data Type (Visual Basic) | Microsoft Docs"
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
  - "vb.Single"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Single data type"
  - "F literal type character"
  - "trailing zeros"
  - "real numbers"
  - "literal type characters, F"
  - "trailing 0 characters"
  - "identifier type characters, !"
  - "single-precision numbers"
  - "! identifier type character"
  - "0 characters, trailing"
  - "data types [Visual Basic], assigning"
  - "floating-point numbers, Single data type"
  - "numbers, real"
  - "zeros, trailing"
  - "numbers, floating point"
ms.assetid: 224a2795-4cd5-496c-8f7a-a4f05a06d45d
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Single Data Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

存放帶正負號的 IEEE 32 位元 \(4 個位元組\) 的單精確度浮點數 \(Floating\-Point Number\)，其值範圍在負值方面是從 \-3.4028235E\+38 至 \-1.401298E\-45，在正值方面則是從 1.401298E\-45 至 3.4028235E\+38。  單精確度數字會儲存實數的近似值。  
  
## 備註  
 使用 `Single` 資料型別，包含不需要 `Double` 完整資料寬度的浮點值。  在某些情況下，Common Language Runtime 也許能夠將您的 `Single` 變數緊緊疊在一起，避免耗用記憶體。  
  
 `Single` 的預設值為 0。  
  
## 程式設計提示  
  
-   **精確度：** 當您使用浮點數值時，請記住它們在記憶體中並非永遠有精確的表示。  這樣可能會因為某些作業，例如值比較和 `Mod` 運算子，而導致無法預期的結果。  如需詳細資訊，請參閱 [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)。  
  
-   **擴展：** `Single` 資料型別會擴大至 `Double`。  這表示您可以將 `Single` 轉換成 `Double`，而不會發生 <xref:System.OverflowException?displayProperty=fullName> 錯誤。  
  
-   **結尾的零：** 浮點資料型別沒有結尾 0 字元的內部表示。  例如，它們無法區分 4.2000 與 4.2。  因此，當您顯示或列印浮點數值時，結尾 0 字元不會出現。  
  
-   **型別字元。** 將常值型別字元 `F` 附加到常值會強制其成為 `Single` 資料型別。  將識別項型別字元 `!` 附加到任何識別項，會強制其成為 `Single`。  
  
-   **架構型別。** 在 .NET Framework 中對應的型別為 <xref:System.Single?displayProperty=fullName> 結構。  
  
## 請參閱  
 <xref:System.Single?displayProperty=fullName>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Decimal Data Type](../../../visual-basic/language-reference/data-types/decimal-data-type.md)   
 [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)   
 [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)