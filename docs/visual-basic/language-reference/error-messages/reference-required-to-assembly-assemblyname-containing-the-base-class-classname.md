---
title: "需要組件 &#39;&lt;assemblyname&gt;&#39; (包含基底類別 &#39;&lt;classname&gt;&#39;) 的參考 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30007"
  - "vbc30007"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30007"
ms.assetid: 5f34cf47-6c6e-4954-bd8e-d6b020b75fb7
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 需要組件 &#39;&lt;assemblyname&gt;&#39; (包含基底類別 &#39;&lt;classname&gt;&#39;) 的參考
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

需要組件 '\<assemblyname\>' \(包含基底類別 '\<classname\>'\) 的參考。 請在專案中加入一個參考。  
  
 此類別是在專案中未直接參考的動態連結程式庫 \(DLL\) 或組件中所定義。[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 編譯器需要參考，以避免當類別在多個 DLL 或組件中定義時所發生的模稜兩可情況。  
  
 **錯誤 ID︰**BC30007  
  
### 更正這個錯誤  
  
-   在您的專案參考中包含未參考之 DLL 或組件的名稱。  
  
## 請參閱  
 [NIB 如何：使用加入參考對話方塊以加入或移除參考](http://msdn.microsoft.com/zh-tw/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [管理專案中的參考](/visual-studio/ide/managing-references-in-a-project)   
 [中斷參考的疑難排解](/visual-studio/ide/troubleshooting-broken-references)