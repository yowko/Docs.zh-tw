---
title: "XML literals and XML properties are not supported in embedded code within ASP.NET | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31200"
  - "bc31200"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC31200"
ms.assetid: 053e8cba-8584-45cc-9fa0-43d122779772
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# XML literals and XML properties are not supported in embedded code within ASP.NET
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

ASP.NET 中的內嵌式程式碼不支援 XML 常值和 XML 屬性。若要使用 XML 功能，請將程式碼移至程式碼後置 \(Code\-Behind\)。  
  
 ASP.NET 檔案的內嵌式程式碼內 \(`<%= =>`\) 定義了 XML 常值或 XML 軸屬性。  
  
 **錯誤 ID**：BC31200  
  
### 若要更正這個錯誤  
  
-   將包含 XML 常值或 XML 軸屬性的程式碼移至 ASP.NET 程式碼後置 \(Code\-Behind\) 的檔案。  
  
## 請參閱  
 [XML Literals](../../../visual-basic/reference/command-line-compiler/index.md)   
 [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)