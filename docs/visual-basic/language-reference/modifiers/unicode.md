---
title: "Unicode (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Unicode"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Unicode, external references"
  - "Declare statement, marshaling strings"
  - "Unicode keyword"
  - "Unicode, marshaling strings"
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# Unicode (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

不管所宣告的外部程序名稱為何，指定 Visual Basic 都應該將所有字串封送處理 \(Marshal\) 為 Unicode 值。  
  
 呼叫在專案以外定義的程序時，Visual Basic 編譯器並未擁有所需資訊的存取權限，無法正確呼叫該程序。  本資訊包含程序所在位置、如何識別此程序、其呼叫順序 \(Calling Sequence\) 和傳回型別，以及所使用的字串字元集。  [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)會建立外部程序的參考，並提供這項必要資訊。  
  
 呼叫外部程序時，`Declare` 陳述式中的 `charsetmodifier` 部分會提供封送處理字串的字元集資訊。  它也會影響 Visual Basic 搜尋外部檔案，找出外部程序名稱的方式。  `Unicode` 修飾詞 \(Modifier\) 會指定 Visual Basic 應將所有字串封送處理為 Unicode 值，且應查閱程序而不需在搜尋期間修改其名稱。  
  
 如果未指定字元集 \(Character Set\) 修飾詞，則 `Ansi` 為預設值。  
  
## 備註  
 `Unicode` 修飾詞可用於以下內容中：  
  
 [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## 智慧型裝置開發人員注意事項  
 不支援這個關鍵字。  
  
## 請參閱  
 [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)   
 [Auto](../../../visual-basic/language-reference/modifiers/auto.md)   
 [關鍵字](../../../visual-basic/language-reference/keywords/index.md)