---
title: "Long Data Type (Visual Basic) | Microsoft Docs"
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
  - "vb.Long"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "identifier type characters, &"
  - "numbers, whole"
  - "whole numbers"
  - "integral data types"
  - "& identifier type character"
  - "integer numbers"
  - "literal type characters, L"
  - "numbers, integer"
  - "integers, data types"
  - "L literal type character"
  - "integers, types"
  - "Long keyword"
  - "data types [Visual Basic], integral"
  - "data types [Visual Basic], assigning"
  - "Long data type"
ms.assetid: b4770c34-1804-4f8c-b512-c10b0893e516
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Long Data Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

存放帶正負號的 64 位元 \(8 位元組\) 整數，範圍從 \-9,223,372,036,854,775,808 到 9,223,372,036,854,775,807 \(9.2...E\+18\)。  
  
## 備註  
 使用 `Long` 資料型別，來包含因過大而無法符合 `Integer` 資料型別的整數。  
  
 `Long` 的預設值為 0。  
  
## 程式設計提示  
  
-   **Interop 考量：** 如果您正在使用的元件不是針對 .NET Framework 所撰寫 \(例如 Automation 或 COM 物件\)，請記住，`Long` 在其他環境中會有不同的資料寬度 \(32 位元\)。  如果正在傳遞 32 位元引數到這類元件，則需將其宣告為 `Integer` 而不是新 Visual Basic 程式碼中的 `Long`。  
  
     此外，自動化不在 Windows 95、Windows 98、Windows ME，或 Windows 2000 支援 64 位元整數。  您不能在這些作業系統上，將 Visual Basic `Long` 引數傳遞到自動化元件。  
  
-   **擴展：** `Long` 資料型別會擴展至 `Decimal`、`Single` 或 `Double`。  這表示您可以將 `Long` 轉換成這些類型的任何一項，而不會發生 <xref:System.OverflowException?displayProperty=fullName> 錯誤。  
  
-   **型別字元。** 將常值型別字元 `L` 附加到常值會強制其成為 `Long` 資料型別。  將識別項型別字元 `&` 附加到任何識別項，會強制其成為 `Long`。  
  
-   **架構型別。** 在 .NET Framework 中對應的型別為 <xref:System.Int64?displayProperty=fullName> 結構。  
  
## 請參閱  
 <xref:System.Int64>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Integer Data Type](../../../visual-basic/language-reference/data-types/integer-data-type.md)   
 [Short Data Type](../../../visual-basic/language-reference/data-types/short-data-type.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)