---
title: "Types of String Manipulation Methods in Visual Basic | Microsoft Docs"
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
  - "strings [Visual Basic], manipulating [Visual Basic]"
  - "string manipulation"
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# Types of String Manipulation Methods in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

有數種不同的方法可以分析和管理字串。  其中某些方法是 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 語言的一部分，其他則是 `String` 類別的固有方法。  
  
## Visual Basic 語言和 .NET Framework  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 方法可當做語言本身的函式使用。  它們可以在程式碼中使用，沒有任何限制。  下列範例是 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 字串管理命令的典型使用方式：  
  
 [!code-vb[VbVbalrStrings#44](../../../../visual-basic/language-reference/functions/codesnippet/visualbasic/types-of-string-manipula_1.vb)]  
  
 在此範例中，`Mid` 函式會對 `aString` 執行指向作業，並將值指派給 `bString`。  
  
 如需 Visual Basic 字串管理方法的清單，請參閱[String Manipulation Summary](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md)。  
  
### 共用方法與執行個體方法  
 您也可以利用 `String` 類別的方法操作字串。  `String` 中有兩種方法：「*共用*」\(Shared\) 方法和「*執行個體*」\(Instance\) 方法。  
  
#### 共用方法  
 共用方法是源自於 `String` 類別本身的方法，使用時不需要有此類別的執行個體。  這些方法可以用類別 \(`String`\) 的名稱加以限定，而不是用 `String` 類別的執行個體加以限定。  例如：  
  
 [!code-vb[VbVbalrStrings#45](../../../../visual-basic/language-reference/functions/codesnippet/visualbasic/types-of-string-manipula_2.vb)]  
  
 在上述範例中，<xref:System.String.Copy%2A?displayProperty=fullName> 方法是靜態方法，它會作用於指定的運算式並將結果值指派給 `bString`。  
  
#### 執行個體方法  
 相對地，執行個體方法則源自於 `String` 的特定執行個體，必須用執行個體名稱加以限定。  例如：  
  
 [!code-vb[VbVbalrStrings#46](../../../../visual-basic/language-reference/functions/codesnippet/visualbasic/types-of-string-manipula_3.vb)]  
  
 在此範例中，<xref:System.String.Substring%2A?displayProperty=fullName> 方法是 `String` \(也就是 `aString`\) 的執行個體方法。  它會對 `aString` 執行作業並將值指派給 `bString`。  
  
 如需詳細資訊，請參閱 <xref:System.String> 類別的文件。  
  
## 請參閱  
 [Introduction to Strings in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)