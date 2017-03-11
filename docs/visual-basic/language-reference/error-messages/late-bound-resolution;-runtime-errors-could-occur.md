---
title: "Late bound resolution; runtime errors could occur | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc42017"
  - "BC42017"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC42017"
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# Late bound resolution; runtime errors could occur
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

有一個物件指派給宣告為 [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md)的變數。  
  
 當您將變數宣告為 `Object` 時，編譯器 \(Compiler\) 必須執行「*晚期繫結*」\(Late Binding\)，這會在執行階段導致額外的作業。  它也會讓應用程式更容易發生執行階段錯誤。  例如，如果您指派 <xref:System.Windows.Forms.Form> 給 `Object` 變數，然後嘗試存取 <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=fullName> 屬性，則執行階段會擲回 <xref:System.MemberAccessException>，因為 <xref:System.Windows.Forms.Form> 類別不會公開 \(Expose\) `NameTable` 屬性。  
  
 如果您將變數宣告為特定型別，則編譯器可以在編譯時期執行「*早期繫結*」\(Early Binding\)。  這樣可以改善效能、控制特定型別之成員的存取，以及更容易閱讀程式碼。  
  
 根據預設，這是一個警告訊息。  如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](/visual-studio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID：**BC42017  
  
### 若要更正這個錯誤  
  
-   如果可能，請將變數宣告為特定型別。  
  
## 請參閱  
 [Early and Late Binding](../../../visual-basic/programming-guide/language-features/early-late-binding/early-and-late-binding.md)   
 [Object Variable Declaration](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)