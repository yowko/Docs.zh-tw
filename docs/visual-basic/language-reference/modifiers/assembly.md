---
title: "Assembly (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Assembly"
  - "vb.AssemblyAttribute"
  - "Assembly"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Assembly modifier"
  - "Assembly keyword"
  - "attribute blocks, Assembly keyword"
ms.assetid: 925e7471-3bdf-4b51-bb93-cbcfc6efc52f
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# Assembly (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

指定原始程式檔開頭處的屬性套用於整個組件。  
  
## 備註  
 許多屬性 \(Attribute\) 會屬於個別程式設計項目 \(例如類別或屬性 \(Property\)\)。  將角括弧 \(`< >`\) 內的屬性區塊直接附加至宣告陳述式 \(Declaration Statement\)，即可套用這類屬性。  
  
 如果屬性不只屬於下列項目，也屬於整個組件，則可將屬性區塊放在原始程式檔的開頭，並使用 `Assembly` 關鍵字來識別該屬性。  如果它套用至目前的組件模組，則使用 [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md) 關鍵字。  
  
 您也可以將屬性套用至 AssemblyInfo.vb 檔案中的組件，在這種情況下，則不需在主要原始程式碼檔案中使用屬性區塊。  
  
## 請參閱  
 [Module \<keyword\>](../../../visual-basic/language-reference/modifiers/module-keyword.md)   
 [屬性](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)