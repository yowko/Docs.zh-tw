---
title: "Security and the Registry (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "security [Visual Basic], registry"
  - "registry, security issues"
ms.assetid: 9980aff7-2f69-492b-8f66-29a9a76d3df5
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# Security and the Registry (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

本頁面討論在登錄中儲存資料的安全性相關事項。  
  
## 使用權限  
 雖然登錄機碼受到 ACL \(存取控制清單，Access Control List\) 保護，但將機密資料 \(例如密碼\) 以純文字儲存在登錄中仍然是不安全的做法。  
  
 使用登錄會允許不適當存取系統資源或受保護的資訊，因此可能危害安全性。  若要使用這些屬性 \(Property\)，您必須要有 <xref:System.Security.Permissions.RegistryPermissionAccess> 列舉型別的讀寫權限，這是用於控制對登錄變數的存取。  任何以完全信任方式執行的程式碼 \(依據預設的安全性原則，這是指安裝在使用者本機硬碟上的任何程式碼\)，都具有存取登錄的必要權限。  如需詳細資訊，請參閱 <xref:System.Security.Permissions.RegistryPermission> 類別。  
  
 不應該將登錄變數儲存於記憶體位置中，因為不具 <xref:System.Security.Permissions.RegistryPermission> 的程式碼才能存取這些位置。  同樣地，授與權限時請授與完成工作所需的最低權限。  
  
 登錄使用權限存取值是由 <xref:System.Security.Permissions.RegistryPermissionAccess> 列舉型別定義。  下表詳細說明其成員。  
  
|值|登錄變數的存取權|  
|-------|--------------|  
|`AllAccess`|建立、讀取和寫入|  
|`Create`|Create|  
|`NoAccess`|沒有存取權|  
|`Read`|讀取|  
|`Write`|Write|  
  
## 檢查登錄機碼值  
 當您建立登錄值時，必須先確定該值是否已經存在。  其他處理序 \(也許是惡意的處理序\) 可能已建立該值並且具有其存取權。  當您將資料放入登錄值時，其他處理序就可以使用該資料。  若要預防這個問題，請使用 `GetValue` 方法。  如果機碼不存在，這個方法會傳回 `Nothing`。  
  
> [!IMPORTANT]
>  當從 Web 應用程式讀取登錄時，目前的使用者身分會因 Web 應用程式中實作的驗證和模擬而不同。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>   
 [Reading from and Writing to the Registry](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)