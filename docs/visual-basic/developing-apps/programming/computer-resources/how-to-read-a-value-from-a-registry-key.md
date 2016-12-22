---
title: "How to: Read a Value from a Registry Key in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "registry keys, determining if a value exists in"
  - "My.Computer.Registry object, examples"
  - "registry, determining if values exist"
  - "registry keys, reading from"
  - "registry, reading"
ms.assetid: 775d0a57-68c9-464e-8949-9a39bd29cc64
caps.latest.revision: 31
caps.handback.revision: 31
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Read a Value from a Registry Key in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

`My.Computer.Registry` 物件的 `GetValue` 方法，可以用來讀取 Windows 登錄的值。  
  
 如果機碼，在下列範例中，"Software\\MyApp"不存在，則會擲回例外狀況。  如果`ValueName`、 「 名稱 」 在下列範例中，不存在， `Nothing`會傳回。  
  
 `GetValue`方法也可用來判斷指定的值是否存在於特定的登錄機碼。  
  
 程式碼會從 Web 應用程式讀取登錄，目前的使用者由決定的驗證和模擬 Web 應用程式中實作。  
  
### 若要從登錄機碼讀取值  
  
-   請使用 `GetValue` 方法指定路徑和名稱，以從登錄機碼讀取值。  下列範例會從 `HKEY_CURRENT_USER\Software\MyApp` 讀取 `Name` 值，並顯示於訊息方塊中。  
  
     [!CODE [VbResourceTasks#4](../CodeSnippet/VS_Snippets_VBCSharp/VbResourceTasks#4)]  
  
 這個程式碼範例也可做為 IntelliSense 程式碼片段。  在程式碼片段選擇器中，這個程式碼片段位於 \[**Windows 作業系統 \> 登錄**\] 中。  如需詳細資訊，請參閱 [程式碼片段](/visual-studio/ide/code-snippets)。  
  
### 判斷值是否存在於登錄機碼中  
  
-   使用 `GetValue` 方法來擷取值。  下列程式碼會檢查值是否存在，並傳回一則訊息，如果不存在。  
  
     [!CODE [VbResourceTasks#12](../CodeSnippet/VS_Snippets_VBCSharp/VbResourceTasks#12)]  
  
## 穩固程式設計  
 登錄會存放最上層或根目錄機碼，可用來儲存資料。  例如，HKEY\_LOCAL\_MACHINE 根目錄機碼是用來儲存所有使用者使用的電腦層級設定，而 HKEY\_CURRENT\_USER 則用來儲存個別使用者的特定資料。  
  
 下列情形可能會造成例外狀況 \(Exception\)：  
  
-   機碼的名稱為 `Nothing` \(<xref:System.ArgumentNullException>\)。  
  
-   使用者沒有足夠的使用權限可以讀取登錄機碼 \(<xref:System.Security.SecurityException>\)。  
  
-   機碼名稱超過 255 個字元的限制 \(<xref:System.ArgumentException>\)。  
  
## .NET Framework 安全性  
 若要執行這個處理序 \(Process\)，組件需要 <xref:System.Security.Permissions.RegistryPermission> 類別授與的權限層級。  如果您正在部分信任的內容中執行動作，則會因權限不足而導致處理序擲回例外狀況。  同樣地，使用者必須有可以建立或寫入設定的正確存取控制清單 \(ACL\)。  例如，具有程式碼存取安全性權限的本機應用程式，可能不具有作業系統使用權限。  如需詳細資訊，請參閱[Code Access Security Basics](../Topic/Code%20Access%20Security%20Basics.md)。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>   
 <xref:Microsoft.Win32.RegistryHive>   
 [Reading from and Writing to the Registry](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)