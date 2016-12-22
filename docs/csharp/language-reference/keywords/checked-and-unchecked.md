---
title: "Checked 與 Unchecked (C# 參考) | Microsoft Docs"
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
  - "已核對的陳述式 [C#]"
  - "例外狀況 [C#], 溢位檢查"
  - "運算子 [C#], 已核對及未核對"
  - "溢位檢查 [C#]"
  - "陳述式 [C#], 已核對及未核對"
  - "未核對的陳述式 [C#]"
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Checked 與 Unchecked (C# 參考)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

C\# 陳述式可在 checked 或 unchecked 內容中執行。  在 checked 內容中，算術溢位會引發例外狀況。  在 unchecked 內容中，會忽略算術溢位並截斷結果。  
  
-   [checked](../../../csharp/language-reference/keywords/checked.md)：指定 checked 內容。  
  
-   [unchecked](../../../csharp/language-reference/keywords/unchecked.md)：指定 unchecked 內容。  
  
 如果未指定 `checked` 或 `unchecked`，預設內容會取決於編譯器選項等外部因素。  
  
 溢位檢查會影響下列作業：  
  
-   在整數類型上使用下列預先定義之運算子的運算式：  
  
     `++`  `--` \- \(一元\)   `+` \-   `*` `/`  
  
-   整數類型之間的明確數值轉換。  
  
 [\/checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md) 編譯器選項可讓您針對明確不在 `checked` 或 `unchecked` 關鍵字範圍中的所有整數算術陳述式，指定 checked 或 unchecked 內容。  
  
## 請參閱  
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [陳述式關鍵字](../../../csharp/language-reference/keywords/statement-keywords.md)