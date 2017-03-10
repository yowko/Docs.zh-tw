---
title: "Zero-based vs. One-based String Access in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "strings [Visual Basic], indexing"
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# Zero-based vs. One-based String Access in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

這個主題會比較 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 與 [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] 如何對字串中的字元提供存取權。  [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] 一律對字串中的字元提供以零起始的存取權，而 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 則提供以零起始與以一起始的存取權，視函式而定。  
  
## 以一起始  
 若為以一起始的 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 函式範例，考慮使用 `Mid` 函式。  它會採用一個引數，表示子字串將要起始的字元位置 \(起始位置為 1\)。  [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] <xref:System.String.Substring%2A?displayProperty=fullName> 方法會採用子字串在字串中起始的字元索引 \(起始位置為 0\)。  因此，如果您有字串 "ABCDE"，則個別的字元會編號為 1、2、3、4、5 以便用於 `Mid` 函式，但 0、1、2、3、4 則用於 <xref:System.String.Substring%2A?displayProperty=fullName> 方法。  
  
## 以零起始  
 若為以零起始的 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 函式範例，考慮使用 `Split` 函式。  此函式會分隔字串，並傳回包含子字串的陣列。  [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] <xref:System.String.Split%2A?displayProperty=fullName> 方法也會分隔子串，並傳回包含子字串的陣列。  因為 `Split` 函式與 <xref:System.String.Split%2A> 方法都會傳回 [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] 陣列，因此它們必須是以零起始。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A>   
 <xref:Microsoft.VisualBasic.Strings.Split%2A>   
 <xref:System.String.Substring%2A>   
 <xref:System.String.Split%2A>   
 [Introduction to Strings in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)