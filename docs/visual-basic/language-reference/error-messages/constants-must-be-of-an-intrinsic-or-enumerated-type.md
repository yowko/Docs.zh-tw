---
title: "Constants must be of an intrinsic or enumerated type, not a class, structure, type parameter, or array type | Microsoft Docs"
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
  - "vbc30424"
  - "bc30424"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30424"
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Constants must be of an intrinsic or enumerated type, not a class, structure, type parameter, or array type
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

您嘗試將常數宣告為類別、結構或陣列型別 \(Array Type\)，或是包含泛型型別所定義的型別參數。  
  
 常數必須是內建型別 \(`Boolean`、`Byte`、`Date`、`Decimal`、`Double`、`Integer`、`Long`、`Object`、`SByte`、`Short`、`Single`、`String`、`UInteger`、`ULong` 或 `UShort`\)，或是以其中一個整數類資料型別為主的 `Enum` 型別。  
  
 **錯誤 ID**︰BC30424  
  
### 若要更正這個錯誤  
  
1.  請將常數宣告為內建或 `Enum` 型別。  
  
2.  常數也可以是特殊值，例如 `True`、`False` 或 `Nothing`。  編譯器會將這些預先定義的值視為屬於適當的內建型別。  
  
## 請參閱  
 [Constants and Enumerations](../../../visual-basic/language-reference/constants-and-enumerations.md)   
 [資料類型](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)