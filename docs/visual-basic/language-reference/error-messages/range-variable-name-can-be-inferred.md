---
title: "Range variable name can be inferred only from a simple or qualified name with no arguments | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc36599"
  - "bc36599"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC36599"
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
caps.latest.revision: 6
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 6
---
# Range variable name can be inferred only from a simple or qualified name with no arguments
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

LINQ 查詢中含有接受一個或多個引數的程式設計項目。  編譯器無法從該程式設計項目推斷範圍變數。  
  
 **錯誤 ID**：BC36599  
  
### 若要更正這個錯誤  
  
1.  為程式設計項目提供明確變數名稱，如下列程式碼所述：  
  
```  
Dim query = From var1 In collection1   
            Select VariableAlias = SampleFunction(var1), var1  
```  
  
## 請參閱  
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md)