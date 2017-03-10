---
title: "Value of type &#39;type1&#39; cannot be converted to &#39;type2&#39; | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc31194"
  - "bc31194"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC31194"
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
caps.latest.revision: 5
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 5
---
# Value of type &#39;type1&#39; cannot be converted to &#39;type2&#39;
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

型別 'type1' 的值無法轉換為 'type2'。您可以使用 'Value' 屬性取得 '\<parentElement\>' 之第一個項目的字串值。  
  
 已嘗試將 XML 常值 \(Literal\) 隱含轉換為特定型別。  XML 常值無法隱含轉換為指定的型別。  
  
 **錯誤 ID**︰BC31194  
  
### 若要更正這個錯誤  
  
-   使用 XML 常值的 `Value` 屬性，將其值當做 `String` 來參考。  使用 `CType` 函式、另一個型別轉換函式或 <xref:System.Convert> 類別，將值轉換為指定的型別。  
  
## 請參閱  
 <xref:System.Convert>   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md)   
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)