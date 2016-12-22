---
title: "Auto (Visual Basic) | Microsoft Docs"
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
  - "vb.Auto"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Auto keyword, external references"
  - "Declare statement, marshaling strings"
  - "Auto keyword"
  - "Auto keyword, marshaling strings"
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Auto (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

指定 Visual Basic 應該根據 .NET Framework 規則 \(Rule\) 封送處理字串 \(String\)，這些規則是所宣告之外部程序的外部名稱為基礎。  
  
 呼叫在專案以外定義的程序時，Visual Basic 編譯器並未擁有所需資訊的存取權，無法正確呼叫該程序。  本資訊包含程序所在位置、如何識別此程序、其呼叫順序 \(Calling Sequence\) 和傳回型別，以及所使用的字串字元集。  [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)會建立外部程序的參考，並提供這項必要資訊。  
  
 呼叫外部程序時，`Declare` 陳述式中的 `charsetmodifier` 部分會提供封送處理字串的字元集資訊。  它也會影響 Visual Basic 搜尋外部檔案，找出外部程序名稱的方式。  `Auto` 修飾詞 \(Modifier\) 會指定 Visual Basic 應該根據 .NET Framework 規則封送處理字串，也應該判斷執行階段平台的基本字元集 \(Character Set\)，並在初始搜尋失敗時可能會修改外部程序。  如需詳細資訊，請參閱 [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)中「字元集」的部分。  
  
 如果未指定字元集 \(Character Set\) 修飾詞，則 `Ansi` 為預設值。  
  
## 備註  
 `Auto` 修飾詞可用於以下內容中：  
  
 [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## 智慧型裝置開發人員注意事項  
 不支援這個關鍵字。  
  
## 請參閱  
 [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)   
 [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)   
 [關鍵字](../../../visual-basic/reference/command-line-compiler/index.md)