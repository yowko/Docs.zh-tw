---
title: "Names of Declared XML Elements and Attributes (Visual Basic) | Microsoft Docs"
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
  - "declarations [XML in Visual Basic]"
  - "element names [XML in Visual Basic]"
  - "names in XML literals"
  - "attribute names [XML in Visual Basic]"
  - "XML literals [Visual Basic], element names"
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# Names of Declared XML Elements and Attributes (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

本主題提供命名 XML 常值中之 XML 項目和屬性的 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 方針。在 XML 常值中，您可以指定區域名稱或限定名稱。  限定名稱是由 XML 命名空間前置字元、冒號及區域名稱組成。  如需 XML 命名空間前置字元的詳細資訊，請參閱 [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)。  
  
## 規則  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中項目或屬性的區域名稱必須遵循下列規則。  
  
-   可以用命名空間做為開頭。  必須以字母字元或底線 \(`_`\) 開頭。  
  
-   只能包含字母字元、十進位數字、底線、句點 \(.\) 及連字號 \(\-\)。  
  
-   長度不可超過 1,024 個字元。  
  
-   名稱中顯示的冒號用於區隔命名空間。  因此，您只能將冒號用來指定特定名稱的 XML 命名空間。  
  
 此外，您也應遵循下列方針。  
  
-   XML 1.0 規格保留所有以字串 "xml" 開頭的名稱，包括各種大小寫組合。  因此，請勿使用這些名稱做為項目和屬性名稱。  
  
### 名稱長度方針  
 依實用性而言，名稱應該盡可能簡短，但仍可清楚識別項目。  這可以提升程式碼的可讀性、縮短行的長度和減少原始程式檔 \(Source File\) 大小。  
  
 但是，您的名稱也不可短到無法充分描述項目代表的意義，或它在程式碼中的用途。  這對程式碼的可讀性十分重要。  如果他人嘗試了解您的程式碼，或是您自己在撰寫之後很久再回頭查閱，適當的項目名稱可以節省時間。  
  
## 名稱區分大小寫  
 XML 項目名稱區分大小寫。  這表示當 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 編譯器比較兩個只有大小寫不同的名稱時，會將它們當做不同的名稱來解譯。  例如，編譯器會將 `ABC` 和 `abc` 轉譯為不同的項目。  
  
## XML 命名空間  
 建立 XML 項目常值時，您可以指定項目名稱的 XML 命名空間前置字元。  如需詳細資訊，請參閱 [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)。  
  
## 請參閱  
 [Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)