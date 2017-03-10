---
title: "&#39;Dir&#39; function must first be called with a &#39;PathName&#39; argument | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrDIR_IllegalCall"
dev_langs: 
  - "VB"
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
caps.latest.revision: 7
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 7
---
# &#39;Dir&#39; function must first be called with a &#39;PathName&#39; argument
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

`Dir` 函式的初始呼叫並不包含 `PathName` 引數。  第一次呼叫 `Dir` 時必須包含 `PathName`，但是接下來呼叫 `Dir` 時則不需要包含參數即可擷取下一個項目。  
  
### 若要更正這個錯誤  
  
1.  請在函式呼叫中提供 `PathName` 引數。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>