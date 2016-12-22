---
title: "Byte Data Type (Visual Basic) | Microsoft Docs"
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
  - "vb.Byte"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Byte data type"
  - "data types [Visual Basic], assigning"
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Byte Data Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

存放不帶正負號的 8 位元 \(1 位元組\) 整數，範圍從 0 到 255。  
  
## 備註  
 使用 `Byte` 資料型別來包含二進位資料。  
  
 `Byte` 的預設值為 0。  
  
## 程式設計提示  
  
-   **負數：** 由於 `Byte` 是不帶正負號的型別，故無法代表負數。  如果您在評估為 `Byte` 型別的運算式中使用一元 \(Unary\) 減號 \(`-`\) 運算子，則 Visual Basic 會先將運算式轉換為 `Short`。  
  
-   **格式轉換** ：當 Visual Basic 讀取或寫入檔案，或呼叫 DLL、方法和屬性時，它可以在資料格式之間自動轉換。  儲存在 `Byte` 變數及陣列的二進位資料會在格式轉換時保留。  二進位資料不應使用 `String` 變數，因為資料內容可能會在 ANSI 和 Unicode 格式之間轉換時損毀。  
  
-   **擴展：** `Byte` 資料型別可擴展至 `Short`、`UShort`、`Integer`、`UInteger`、`Long`、`ULong`、`Decimal`、`Single` 或 `Double`。  這表示您可以將 `Byte` 轉換成這些類型的任何一項，而不會發生 <xref:System.OverflowException?displayProperty=fullName> 錯誤。  
  
-   **型別字元**：`Byte` 沒有常值型別字元或識別項型別字元。  
  
-   **架構型別。** 在 .NET Framework 中對應的型別為 <xref:System.Byte?displayProperty=fullName> 結構。  
  
## 範例  
 下列範例中的 `b` 是 `Byte` 變數：  陳述式會說明變數的範圍，以及應用的位元移位運算子。  
  
 [!code-vb[VbVbalrDataTypes#16](../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/byte-data-type_1.vb)]  
  
## 請參閱  
 <xref:System.Byte?displayProperty=fullName>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)