---
title: ".NET 效能秘訣 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "C# 語言, 效能"
  - "效能 [C#]"
  - "效能 [Visual Basic]"
  - "Visual Basic, 效能"
ms.assetid: ae275793-857d-4102-9095-b4c2a02d57f4
caps.latest.revision: 36
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
caps.handback.revision: 36
---
# .NET 效能秘訣
「*效能*」\(Performance\) 一詞通常是指程式的執行速度。  有時候您可以在原始程式碼中藉由下列某些基本規則，以提高執行速度。  某些程式中，仔細地檢查程式碼及使用分析工具 \(Profiler\) 來確保程式碼能以最快速度執行，是很重要的。  在其他程式中，您不需要執行這種最佳化工作，因為程式碼會在其撰寫的可接受速度下執行。  本文件列出效能可能會減損的一般區域、改善的提示，以及其他效能主題的連結。  如需規劃和測量效能的詳細資訊，請參閱 [Performance](../../../docs/framework/performance/index.md)。  
  
## Boxing 和 Unboxing  
 在必須多次 Box 處理實值類型 \(Value Type\) 的情況下，例如在 <xref:System.Collections.ArrayList?displayProperty=fullName> 等非泛型集合類別中，最好避免使用實值類型。  您可以使用泛型集合例如 <xref:System.Collections.Generic.List%601?displayProperty=fullName>，避免 Box 處理實值類型。  Box 和 Unbox 處理是大量耗用運算資源的處理序。  當實值類型經 Box 處理時，必須建立全新的物件。  這個過程需要的時間可能是簡單參考指派的 20 倍。  執行 Unbox 處理時，轉換處理序所需的時間可能是指派的四倍。  如需詳細資訊，請參閱 [Boxing 和 Unboxing](../Topic/Boxing%20and%20Unboxing%20\(C%23%20Programming%20Guide\).md)。  
  
## 字串  
 當您串連許多字串變數時 \(例如在緊密迴圈中\)，請使用 <xref:System.Text.StringBuilder?displayProperty=fullName> 代替 C\# [\+ 運算子](../Topic/+%20Operator%20\(C%23%20Reference\).md)或 Visual Basic 的 [串連運算子](../Topic/Concatenation%20Operators%20\(Visual%20Basic\).md)。  如需詳細資訊，請參閱[如何：串連多個字串](../Topic/How%20to:%20Concatenate%20Multiple%20Strings%20\(C%23%20Programming%20Guide\).md)與[Concatenation Operators in Visual Basic](../Topic/Concatenation%20Operators%20in%20Visual%20Basic.md)。  
  
## 解構函式  
 您不應使用空的解構函式。  當類別包含解構函式時，會在 Finalize 佇列中建立一個項目。  當呼叫解構函式時，即會叫用記憶體回收行程處理佇列。  如果解構函式是空的，則只會導致效能損失。  如需詳細資訊，請參閱[解構函式](../Topic/Destructors%20\(C%23%20Programming%20Guide\).md)與[Object Lifetime: How Objects Are Created and Destroyed](../Topic/Object%20Lifetime:%20How%20Objects%20Are%20Created%20and%20Destroyed%20\(Visual%20Basic\).md)。  
  
## 其他資源  
  
-   [撰寫更快速的 Managed 程式碼：了解其中耗時的環節](http://go.microsoft.com/fwlink/?LinkId=99294)  
  
-   [撰寫高效能的 Managed 應用程式：入門](http://go.microsoft.com/fwlink/?LinkId=99295)  
  
-   [記憶體回收行程的基本概念和效能提示](http://go.microsoft.com/fwlink/?LinkId=99296) \(英文\)  
  
-   [.NET 應用程式的效能秘訣和訣竅](http://go.microsoft.com/fwlink/?LinkId=99297) \(英文\)  
  
-   [.NET 診斷工具內部](http://go.microsoft.com/fwlink/?LinkId=112407)  
  
-   [Rico Mariani 的效能趣聞](http://go.microsoft.com/fwlink/?LinkId=115679) \(英文\)  
  
## 請參閱  
 [Performance](../../../docs/framework/performance/index.md)   
 [程式設計概念](../Topic/Programming%20Concepts.md)   
 [Visual Basic Programming Guide](../Topic/Visual%20Basic%20Programming%20Guide.md)   
 [C\# 程式設計手冊](../Topic/C%23%20Programming%20Guide.md)