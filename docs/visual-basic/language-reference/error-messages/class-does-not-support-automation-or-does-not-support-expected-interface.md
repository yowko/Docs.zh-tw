---
title: "Class does not support Automation or does not support expected interface | Microsoft Docs"
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
  - "vbrID430"
dev_langs: 
  - "VB"
ms.assetid: d985bb7e-e48e-443e-86f2-ddb86758757c
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Class does not support Automation or does not support expected interface
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

您在 `GetObject` 或 `CreateObject` 函式呼叫中指定的類別沒有公開撰寫程式介面，或是您將專案從 .dll 變更為 .exe \(反之亦然\)。  
  
### 更正這個錯誤  
  
1.  查看建立物件的應用程式文件，以取得此物件類別的自動化使用限制。  
  
2.  如果您將專案從 .dll 變更為 .exe \(反之亦然\)，則必須手動移除舊 .dll 或 .exe 的註冊。  
  
## 請參閱  
 [Error Types](../../../visual-basic/programming-guide/language-features/error-types.md)   
 [告訴我們](/visual-studio/ide/talk-to-us)