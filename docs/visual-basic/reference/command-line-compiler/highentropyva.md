---
title: "/highentropyva (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "highentropyva compiler option (Visual Basic)"
  - "/highentropyva compiler option (Visual Basic)"
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /highentropyva (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

表示是否將 64 位元可執行檔或標記的程式碼的可執行檔 [\/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) 編譯器選項支援高熵位址空間配置隨機 \(ASLR\)。  
  
## 語法  
  
```  
/highentropyva[+ | -]  
```  
  
## 引數  
 `+` &#124; `-`  
 選擇項。  根據預設值\] 選項已關閉，或如果您指定`/highentropyva-`。  此選項為開啟如果您指定`/highentropyva`或`/highentropyva+`。  
  
## 備註  
 如果您指定這個選項，因為相容版本的 Windows 核心核心隨機放置個處理程序的位址空間配置 ASLR 的一部分時可以使用更高程度的亂度。  如果核心使用更高程度的亂度，例如堆疊和堆積的記憶體區域可以配置數量龐大的地址。  如此一來，很難猜出特定的記憶體區域的位置。  
  
 在選項開啟時，目標可執行檔和任何的模組上須用該值必須能夠處理這些模組以 64 位元處理程序執行時，會大於 4 gb 的指標值。  
  
 如需有關 ASLR 的詳細資訊，請參閱[緩和軟體漏洞](http://go.microsoft.com/fwlink/?LinkId=226234)。  
  
## 請參閱  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)