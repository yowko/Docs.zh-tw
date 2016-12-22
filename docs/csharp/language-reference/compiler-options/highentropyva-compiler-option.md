---
title: "/highentropyva (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/highentropyva"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/highentropyva compiler option [C#]"
  - "-highentropyva compiler option [C#]"
  - "highentropyva compiler option [C#]"
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /highentropyva (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

**\/highentropyva** 編譯器選項會通知視窗核心特定可執行檔是否支援高熵位址空間隨機載入 \(ASLR\)。  
  
## 語法  
  
```  
/highentropyva[+ | -]  
```  
  
## Arguments  
 `+` &#124; `-`  
 這個選項指定一個 64 位元的可執行檔或由 [\/platform: anycpu](../../../csharp/language-reference/compiler-options/platform-compiler-option.md) 編譯器選項所指示的可執行檔，支援一個高熵虛擬位址空間。  此選項預設為停用。  使用 **\/highentropyva\+** 或 **\/highentropyva** 啟用它。  
  
## 備註  
 當隨機化處理序的位址空間配置做為 ASLR 一部分時， **\/highentropyva** 選項可讓視窗核心的相容版本使用高度 Entropy。  使用 Height Entropy 表示位址的數目可配置給記憶體區域，例如堆疊和堆積。  因此，猜測特定記憶體區域的位置更是困難。  
  
 當指定 **\/highentropyva** 編譯器選項、以 64 位元處理序執行時時，目標可執行檔和它所依賴的任何模組必須能夠處理大於 4 GB 的指標值 \(GB\)。  
  
 如需要ASLR的詳細資訊，請參閱 [緩和軟體漏洞](http://go.microsoft.com/fwlink/?LinkId=226234)。