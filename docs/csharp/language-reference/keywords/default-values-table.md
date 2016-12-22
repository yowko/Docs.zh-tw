---
title: "預設值表 (C# 參考) | Microsoft Docs"
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
  - "建構函式 [C#]，傳回值"
  - "關鍵字 [C#]，新"
  - "預設建構函式 [C#]"
  - "預設值 [C#]"
  - "實值類型 [C#]，初始化"
  - "變數 [C#]，實值類型"
  - "建構函式 [C#]，預設建構函式"
  - "類型 [C#]，預設建構函式傳回值"
ms.assetid: 4af2c1df-9e3a-48c1-83ac-b192986fc5bc
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 預設值表 (C# 參考)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

下表顯示了預設建構函式所傳回的實值型別預設值。  使用 `new` 運算子時會叫用預設建構函式，如下所示：  
  
```  
int myInt = new int();  
```  
  
 上述陳述式與下列陳述式有相同的效果：  
  
```  
int myInt = 0;  
```  
  
 記住 C\# 裡不允許使用未初始化的變數。  
  
|實值型別|預設值|  
|----------|---------|  
|[bool](../../../csharp/language-reference/keywords/bool.md)|`false`|  
|[byte](../../../csharp/language-reference/keywords/byte.md)|0|  
|[char](../../../csharp/language-reference/keywords/char.md)|'\\0'|  
|[decimal](../../../csharp/language-reference/keywords/decimal.md)|0.0M|  
|[double](../../../csharp/language-reference/keywords/double.md)|0.0D|  
|[enum](../../../csharp/language-reference/keywords/enum.md)|由運算式 \(E\)0 所產生的值，而 E 是列舉識別項|  
|[float](../../../csharp/language-reference/keywords/float.md)|0.0F|  
|[int](../../../csharp/language-reference/keywords/int.md)|0|  
|[long](../../../csharp/language-reference/keywords/long.md)|0L|  
|[sbyte](../../../csharp/language-reference/keywords/sbyte.md)|0|  
|[short](../../../csharp/language-reference/keywords/short.md)|0|  
|[struct](../../../csharp/language-reference/keywords/struct.md)|這個值是由將所有實值型別欄位設定為其預設值，且所有參考型別欄位設定為 `null` 所產生|  
|[uint](../../../csharp/language-reference/keywords/uint.md)|0|  
|[ulong](../../../csharp/language-reference/keywords/ulong.md)|0|  
|[ushort](../../../csharp/language-reference/keywords/ushort.md)|0|  
  
## 請參閱  
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [實值類型表](../../../csharp/language-reference/keywords/value-types-table.md)   
 [實值類型](../../../csharp/language-reference/keywords/value-types.md)   
 [內建類型資料表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [類型的參考表](../../../csharp/language-reference/keywords/reference-tables-for-types.md)