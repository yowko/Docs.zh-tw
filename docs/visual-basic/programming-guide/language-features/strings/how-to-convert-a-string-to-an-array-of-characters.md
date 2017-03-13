---
title: "How to: Convert a String to an Array of Characters in Visual Basic | Microsoft Docs"
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
  - "character arrays, converting strings"
  - "arrays [Visual Basic], converting strings to"
  - "examples [Visual Basic], string conversion"
  - "strings [Visual Basic], converting to arrays"
  - "string conversion [Visual Basic], arrays"
ms.assetid: 1b54b686-ab29-413b-adce-6bd5422376eb
caps.latest.revision: 7
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 7
---
# How to: Convert a String to an Array of Characters in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

某些時候，例如當您在剖析字串時，擁有字串中的字元以及這些字元在字串中位置的資料是非常有用的。  此範例會顯示如何藉由呼叫字串的 <xref:System.String.ToCharArray%2A> 方法，取得字串中的字元陣列。  
  
## 範例  
 此範例會將字串分割為 `Char` 陣列，以及將字串分割為 Unicode 文字字元的 `String` 陣列。  這項區別的原因在於 Unicode 文字字元可以組成兩個以上的 `Char` 字元 \(例如 Surrogate 字組或組合字元順序\)。  如需詳細資訊，請參閱 <xref:System.Globalization.TextElementEnumerator> 和＜Unicode Standard＞，網址為 http:\/\/www.unicode.org。  
  
 [!code-vb[VbVbalrStrings#75](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_1.vb)]  
  
## 範例  
 將字串分割為 Unicode 文字字元較為困難，但如果您需要字串之視覺呈現的相關資訊，就必須這麼做。  此範例會使用 <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> 方法，取得構成字串之 Unicode 文字字元的相關資訊。  
  
 [!code-vb[VbVbalrStrings#76](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_2.vb)]  
  
## 請參閱  
 <xref:System.String.Chars%2A>   
 <xref:System.Globalization.StringInfo?displayProperty=fullName>   
 [How to: Access Characters in Strings](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md)   
 [Converting Between Strings and Other Data Types in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)   
 [Strings](../../../../visual-basic/programming-guide/language-features/strings/index.md)