---
title: "An unexpected error has occurred because an operating system resource required for single instance startup cannot be acquired | Microsoft Docs"
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
  - "vbrAppModel_CantGetMemoryMappedFile"
dev_langs: 
  - "VB"
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# An unexpected error has occurred because an operating system resource required for single instance startup cannot be acquired
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

應用程式無法取得必要的作業系統資源。  此問題的部分可能原因包括：  
  
-   應用程式沒有權限可建立具名的作業系統物件。  
  
-   通用語言執行平台沒有權限可建立記憶體對應檔案。  
  
-   應用程式需要存取作業系統物件，但另一個處理序正在使用它。  
  
### 更正這個錯誤  
  
1.  檢查應用程式有足夠的權限可建立指名的作業系統物件。  
  
2.  檢查通用語言執行平台有足夠的權限可建立記憶體對應檔案。  
  
3.  重新啟動電腦，以清除可能正在使用連接到原始執行個體應用程式之所需資源的任何處理序。  
  
4.  記下錯誤發生時的情況，並致電 Microsoft 產品支援服務  
  
## 請參閱  
 [應用程式頁面，專案設計工具 \(Visual Basic\)](/visual-studio/ide/reference/application-page-project-designer-visual-basic)   
 [偵錯工具基礎](/visual-studio/debugger/debugger-basics)   
 [告訴我們](/visual-studio/ide/talk-to-us)