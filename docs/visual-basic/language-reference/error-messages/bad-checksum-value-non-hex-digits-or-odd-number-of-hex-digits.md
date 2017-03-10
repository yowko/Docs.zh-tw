---
title: "Bad checksum value, non hex digits or odd number of hex digits | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc42033"
  - "vbc42033"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC42033"
ms.assetid: 4575554d-3615-46e4-9c6a-18e9c338e4ed
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# Bad checksum value, non hex digits or odd number of hex digits
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

總和檢查碼值包含無效的十六進位數字，或是有奇數個數字。  
  
 當 ASP.NET 產生 Visual Basic 原始程式檔 \(副檔名為 .vb\) 時，它會計算總和檢查碼並將它放在 `#externalchecksum` 所識別的隱藏原始程式檔中。  使用者產生 .vb 檔案也可能這麼做，但這個流程最好留供內部使用。  
  
 根據預設，這個訊息是一個警告。  如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](/visual-studio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID︰**BC42033  
  
### 更正這個錯誤  
  
1.  如果 ASP.NET 正在產生 Visual Basic 原始程式檔，請重新啟動專案建置。  
  
2.  如果這個警告在重新啟動之後持續發生，請重新安裝 ASP.NET 然後重試建置。  
  
3.  如果警告仍然持續發生，或您未使用 ASP.NET，請收集情況的相關資訊，並通知 Microsoft 產品支援服務。  
  
## 請參閱  
 [ASP.NET Overview](../Topic/ASP.NET%20Overview.md)   
 [告訴我們](/visual-studio/ide/talk-to-us)