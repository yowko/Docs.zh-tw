---
title: "Ansi (Visual Basic) | Microsoft Docs"
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
  - "vb.Ansi"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Declare statement, marshaling strings"
  - "ANSI, Visual Basic"
  - "ANSI"
ms.assetid: 4f1fa6ff-5557-41ab-b6da-90baf4c15917
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ansi (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

指定無論所宣告的外部程序名稱為何，Visual Basic 都應將所有字串 \(String\) 封送處理 \(Marshal\) 成美國國家標準局 \(ANSI\) 的值。  
  
 呼叫在專案以外定義的程序時，Visual Basic 編譯器並未擁有所需資訊的存取權，無法正確呼叫該程序。  本資訊包含程序所在位置、如何識別此程序、其呼叫順序 \(Calling Sequence\) 和傳回型別，以及所使用的字串字元集。  [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)會建立外部程序的參考，並提供這項必要資訊。  
  
 呼叫外部程序時，`Declare` 陳述式中的 `charsetmodifier` 部分會提供封送處理字串的字元集資訊。  它也會影響 Visual Basic 搜尋外部檔案，找出外部程序名稱的方式。  `Ansi` 修飾詞 \(Modifier\) 指定 Visual Basic 應將所有字串封送處理成 ANSI 值，且應查詢程序而不需在搜尋期間修改其名稱。  
  
 如果未指定字元集 \(Character Set\) 修飾詞，則 `Ansi` 為預設值。  
  
## 備註  
 `Ansi` 修飾詞可用於以下內容中：  
  
 [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## 智慧型裝置開發人員注意事項  
 不支援這個關鍵字。  
  
## 請參閱  
 [Auto](../../../visual-basic/language-reference/modifiers/auto.md)   
 [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)   
 [關鍵字](../../../visual-basic/reference/command-line-compiler/index.md)