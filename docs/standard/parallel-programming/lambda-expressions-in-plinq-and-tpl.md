---
title: "Lambda Expressions in PLINQ and TPL | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Func delegate, creating with lambda expression"
  - "Action delegate, creating with lambda expression"
  - "lambda expressions, with Action and Func"
ms.assetid: 645b2c17-29d0-4ffa-8684-430743cc2f2d
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# Lambda Expressions in PLINQ and TPL
工作平行程式庫 \(TPL\) 包含許多採用委派的其中一個 <xref:System.Func%601?displayProperty=fullName> 或 <xref:System.Action?displayProperty=fullName> 系列做為輸入參數的方法。  您可以使用這些委派，將您的自訂程式邏輯傳遞至平行迴圈、工作或查詢。  TPL 和 PLINQ 的程式碼範例會使用 Lambda 運算式，將這些委派的執行個體建立為內嵌程式碼區塊。  本主題將簡單介紹 Func 和 Action，並說明如何在工作平行程式庫和 PLINQ 中使用 Lambda 運算式。  
  
 **注意**：如需一般委派的詳細資訊，請參閱[委派](../Topic/Delegates%20\(C%23%20Programming%20Guide\).md) 和 [Delegates](../Topic/Delegates%20\(Visual%20Basic\).md)。  如需如何在 C\# 和 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 中使用 Lambda 運算式的詳細資訊，請參閱 [Lambda 運算式](../Topic/Lambda%20Expressions%20\(C%23%20Programming%20Guide\).md) 和 [Lambda Expressions](../Topic/Lambda%20Expressions%20\(Visual%20Basic\).md)。  
  
## Func 委派  
 `Func` 委派封裝了會傳回值的方法。  在 Func 簽章中，最後一個或最右側的型別參數一律會指定傳回型別。  編譯器錯誤的一個常見原因是嘗試將兩個輸入參數傳入 <xref:System.Func%602?displayProperty=fullName>；事實上這個型別只接受一個輸入參數。  Framework 類別庫定義了 17 種版本的 `Func`：<xref:System.Func%601?displayProperty=fullName>、<xref:System.Func%602?displayProperty=fullName>、<xref:System.Func%603?displayProperty=fullName> 乃至於 <xref:System.Func%6017?displayProperty=fullName>。  
  
## Action 委派  
 <xref:System.Action?displayProperty=fullName> 委派會封裝不會傳回值的方法 \(在 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 中為 Sub\)，或會傳回 [void](../Topic/void%20\(C%23%20Reference\).md) 的方法。  在 Action 型別簽章中，型別參數僅代表輸入參數。  如同 Func，Framework 類別庫定義了 17 種版本的 Action，從不具任何型別參數的版本，乃至於具有 16 個型別參數的版本。  
  
## 範例  
 <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=fullName> 方法的下列範例示範如何使用 Lambda 運算式來表示 Func 和 Action 委派。  
  
 [!code-csharp[System.Threading.Tasks.Parallel#02](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.parallel/cs/parallelforeach.cs#02)]
 [!code-vb[System.Threading.Tasks.Parallel#02](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.parallel/vb/parallelforeach.vb#02)]  
  
## 請參閱  
 [Parallel Programming](../../../docs/standard/parallel-programming/index.md)