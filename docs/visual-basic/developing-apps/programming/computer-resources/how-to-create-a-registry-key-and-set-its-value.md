---
title: "How to: Create a Registry Key and Set Its Value in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "RegistryKey.CreateSubKey"
  - "RegistryKey.SetValue"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "registry keys, creating"
  - "registry, adding values"
  - "registry, adding keys"
  - "registry keys, setting values"
  - "examples [Visual Basic], registry"
ms.assetid: d3e40f74-c283-480c-ab18-e5e9052cd814
caps.latest.revision: 30
caps.handback.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Create a Registry Key and Set Its Value in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

`My.Computer.Registry` 物件的 `CreateSubKey` 方法可用來建立登錄機碼 \(Registry Key\)。  
  
## 程序  
  
#### 若要建立登錄機碼  
  
-   請使用 `CreateSubKey` 方法來指定要將機碼及機碼名稱存放在那個登錄區。  參數  `Subkey`  不需區分大小寫。  這個範例是將登錄機碼 `MyTestKey` 建立在 HKEY\_CURRENT\_USER 之下。  
  
     [!CODE [VbResourceTasks#17](../CodeSnippet/VS_Snippets_VBCSharp/VbResourceTasks#17)]  
  
#### 若要建立登錄機碼並設定其值  
  
1.  請使用 `CreateSubkey` 方法來指定要將機碼及機碼名稱存放在那個登錄區。  這個範例是將登錄機碼 `MyTestKey` 建立在 HKEY\_CURRENT\_USER 之下。  
  
     [!CODE [VbResourceTasks#17](../CodeSnippet/VS_Snippets_VBCSharp/VbResourceTasks#17)]  
  
2.  使用 `SetValue` 方法來設定值。  這個範例會設定字串值： 「  MyTestKeyValue" 設為 "This is a test value"。  
  
     [!CODE [VbResourceTasks#14](../CodeSnippet/VS_Snippets_VBCSharp/VbResourceTasks#14)]  
  
## 範例  
 這個範例是將登錄機碼 `MyTestKey` 建立在 HKEY\_CURRENT\_USER 之下，並將字串值 `MyTestKeyValue` 設為 `This is a test value`。  
  
 [!CODE [VbResourceTasks#15](../CodeSnippet/VS_Snippets_VBCSharp/VbResourceTasks#15)]  
  
## 穩固程式設計  
 檢查登錄結構以找出適合機碼 \(Key\) 的位置。  例如，您可能想要開啟目前使用者的 HKEY\_CURRENT\_USER\\Software 機碼，並使用您的公司名稱來建立機碼，  接著將登錄值加入至您的公司機碼。  
  
 當從 Web 應用程式讀取登錄時，目前的使用者會因 Web 應用程式中實作的驗證和模擬而不同。  
  
 更為安全的做法是將資料寫入至使用者資料夾 \(<xref:Microsoft.Win32.Registry.CurrentUser>\)，而不是寫入至本機電腦 \(<xref:Microsoft.Win32.Registry.LocalMachine>\)。  
  
 當您建立登錄值時，必須先確定該值是否已經存在。  其他處理序 \(也許是惡意的處理序\) 可能已建立該值並且具有其存取權。  當您將資料放入登錄值時，其他處理序就可以使用該資料。  若要預防這個問題，請使用 <xref:Microsoft.Win32.RegistryKey.GetValue%2A> 方法。  如果機碼不存在，這個方法會傳回 `Nothing`。  
  
 雖然登錄機碼會受到存取控制清單 \(Access Control List，ACL\) 保護，但是將機密資料 \(例如密碼\) 以純文字儲存在登錄中仍然是不安全的做法。  
  
 下列情形可能會造成例外狀況 \(Exception\)：  
  
-   機碼的名稱為 `Nothing` \(<xref:System.ArgumentNullException>\)。  
  
-   使用者沒有建立登錄機碼的使用權限 \(<xref:System.Security.SecurityException>\)。  
  
-   機碼名稱超過 255 個字元的限制 \(<xref:System.ArgumentException>\)。  
  
-   機碼已關閉 \(<xref:System.IO.IOException>\)。  
  
-   登錄機碼為唯讀 \(<xref:System.UnauthorizedAccessException>\)。  
  
## .NET Framework 安全性  
 若要執行這個處理序 \(Process\)，組件需要 <xref:System.Security.Permissions.RegistryPermission> 類別授與的權限層級。  如果您正在部分信任的內容中執行動作，則會因權限不足而導致處理序擲回例外狀況。  同樣地，使用者必須有可以建立或寫入設定的正確存取控制清單 \(ACL\)。  例如，具有程式碼存取安全性權限的本機應用程式，可能不具有作業系統使用權限。  如需詳細資訊，請參閱[Code Access Security Basics](../Topic/Code%20Access%20Security%20Basics.md)。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>   
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A>   
 <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>   
 [Reading from and Writing to the Registry](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)   
 [Code Access Security Basics](../Topic/Code%20Access%20Security%20Basics.md)