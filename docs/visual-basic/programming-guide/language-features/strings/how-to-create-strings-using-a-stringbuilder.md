---
title: "How to: Create Strings Using a StringBuilder in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "StringBuilder class"
  - "strings [Visual Basic], using StringBuilder"
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# How to: Create Strings Using a StringBuilder in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

這個範例可使用 <xref:System.Text.StringBuilder> 類別，從許多較小的字串建構長字串。  對串連許多字串而言，<xref:System.Text.StringBuilder> 類別比 `&=` 運算子更有效率。  
  
## 範例  
 下列範例會建立 <xref:System.Text.StringBuilder> 類別的執行個體，將 1,000 個字串附加至該執行個體，然後傳回其字串表示。  
  
 [!code-vb[VbVbalrStrings#70](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-strings-using-a-stringbuilder_1.vb)]  
  
## 請參閱  
 [使用 StringBuilder 類別](../Topic/Using%20the%20StringBuilder%20Class%20in%20the%20.NET%20Framework.md)   
 [&\= Operator](../../../../visual-basic/language-reference/operators/and-assignment-operator.md)   
 [Strings](../../../../visual-basic/programming-guide/language-features/strings/index.md)   
 [建立新字串](../Topic/Creating%20New%20Strings%20in%20the%20.NET%20Framework.md)   
 [操作字串](../Topic/Manipulating%20Strings%20in%20the%20.NET%20Framework.md)   
 [Strings Sample](http://msdn.microsoft.com/zh-tw/be9e82a3-dc95-4aaa-9396-61b66e467e02)