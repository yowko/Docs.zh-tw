---
title: "類型 (C# 參考) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "資料類型 [C#], 類型系統"
  - "類型 [C#]"
ms.assetid: 16b984df-f417-4e02-b1e6-4589d4a614ea
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 類型 (C# 參考)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

C\# 的型別系統包含下列類別：  
  
-   [實值型別](../../../csharp/language-reference/keywords/value-types.md)  
  
-   [參考型別](../../../csharp/language-reference/keywords/reference-types.md)  
  
-   [指標型別](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
  
 實值型別 \(Value Type\) 的變數會儲存資料，而參考型別 \(Reference Type\) 的變數則儲存實際資料的參考。  參考型別也可視為物件。  指標型別 \(Pointer Type\) 只能用於 [unsafe](../../../csharp/language-reference/keywords/unsafe.md) 模式。  
  
 使用 [boxing 和 unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md)，可以將實值型別轉換成參考型別，反之亦可。  如果有 boxed 實值型別的例外狀況，您就不能將參考型別轉換成實值型別。  
  
 本章節內容也會介紹 [void](../../../csharp/language-reference/keywords/void.md) 型別。  
  
 實值型別也是可為 Null 的型別，也就是說它們可以儲存其他非實值的狀態。  如需詳細資訊，請參閱[可為 Null 的型別](../../../visual-basic/reference/command-line-compiler/index.md)。  
  
## 請參閱  
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [類型的參考表](../../../csharp/language-reference/keywords/reference-tables-for-types.md)   
 [轉型和類型轉換](../../../csharp/programming-guide/types/casting-and-type-conversions.md)   
 [類型](../../../csharp/programming-guide/types/index.md)