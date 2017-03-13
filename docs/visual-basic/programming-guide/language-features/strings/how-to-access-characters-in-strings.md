---
title: "How to: Access Characters in Strings in Visual Basic | Microsoft Docs"
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
  - "strings [Visual Basic], accessing characters"
  - "characters [Visual Basic], accessing in strings"
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# How to: Access Characters in Strings in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

此範例會使用 <xref:System.String.Chars%2A> 屬性 \(Property\)，存取字串中指定之位置上的字元。  
  
## 範例  
 有時候擁有字串中的字元，以及這些字元在字串中位置的資料是非常有用的。  您可以將字串想成是字元 \(`Char` 執行個體\) 的陣列。可以透過 <xref:System.String.Chars%2A> 屬性，參考該字元的索引來擷取特定字元。  
  
 [!code-vb[VbVbalrStrings#49](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-access-characters-in-strings_1.vb)]  
  
 <xref:System.String.Chars%2A> 屬性的 `index` 參數是以零起始。  
  
## 穩固程式設計  
 <xref:System.String.Chars%2A> 屬性會傳回指定之位置上的字元。  然而，某些 Unicode 字元會以一個以上的字元來呈現。  如需如何使用 Unicode 字元的相關資訊，請參閱 [How to: Convert a String to an Array of Characters](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)。  
  
 如果 `index` 參數大於或等於字串的長度，或是小於零，則 <xref:System.String.Chars%2A> 屬性會擲回 <xref:System.IndexOutOfRangeException> 例外狀況。  
  
## 請參閱  
 <xref:System.String.Chars%2A>   
 [How to: Convert a String to an Array of Characters](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)   
 [Converting Between Strings and Other Data Types in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)   
 [Strings](../../../../visual-basic/programming-guide/language-features/strings/index.md)