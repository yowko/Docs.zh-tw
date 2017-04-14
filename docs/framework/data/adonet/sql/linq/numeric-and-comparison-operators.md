---
title: "數值和比較運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 數值和比較運算子
除了下列幾點以外，在 Common Language Runtime \(CLR\) 中算術和比較運算子都會如預期運作：  
  
-   SQL 不支援浮點數值 \(Floating\-Point Number\) 的模數運算子。  
  
-   SQL 不支援不檢查的算術。  
  
-   當您在無法於 SQL 中複寫因而不受支援的運算式中使用遞增和遞減運算子時，這些運算子會造成副作用。  
  
## 支援的運算子  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 支援下列運算子。  
  
-   基本算術運算子：  
  
    -   `+`  
  
    -   `-` \(減法\)  
  
    -   `*`  
  
    -   `/`  
  
    -   Visual Basic 整數除法 \(`\`\)  
  
    -   `%` \(Visual Basic `Mod`\)  
  
    -   `<<`  
  
    -   `>>`  
  
    -   `-` \(一元否定運算\)  
  
-   基本比較運算子：  
  
    -   Visual Basic `=` 和 C\# `==`  
  
    -   Visual Basic `<>` 和 C\# `!=`  
  
    -   Visual Basic `Is/IsNot`  
  
    -   `<`  
  
    -   `<=`  
  
    -   `>`  
  
    -   `>=`  
  
## 請參閱  
 [資料型別和函式](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)   
 [C\# 運算子](../Topic/C%23%20Operators.md)   
 [Operators](../Topic/Operators%20\(Visual%20Basic\).md)