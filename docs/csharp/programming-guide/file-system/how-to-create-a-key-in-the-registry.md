---
title: "如何：在登錄中建立機碼 (Visual C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "索引鍵, 在登錄中建立"
  - "登錄機碼, 建立 [C#]"
  - "登錄, 加入機碼和值 [C#]"
ms.assetid: 8fa475b0-e01f-483a-9327-fd03488fdf5d
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 如何：在登錄中建立機碼 (Visual C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

這個範例將位於機碼 "Names" 下的值組 "Name" 和 "Isabella" 加入至目前使用者的登錄。  
  
## 範例  
  
```  
Microsoft.Win32.RegistryKey key;  
key = Microsoft.Win32.Registry.CurrentUser.CreateSubKey("Names");  
key.SetValue("Name", "Isabella");  
key.Close();  
```  
  
## 編譯程式碼  
  
-   複製程式碼，並貼至主控台應用程式的 `Main` 方法中。  
  
-   使用直接位於登錄的 HKEY\_CURRENT\_USER 節點下的機碼名稱來取代 `Names` 參數。  
  
-   請使用直接位於 Names 節點下的值名稱來取代 `Nam`e 參數。  
  
## 穩固程式設計  
 檢查登錄結構以找出適合機碼 \(Key\) 的位置。  例如，您可能會想要開啟目前使用者的 Software 機碼，並且使用您的公司名稱來建立機碼。  接著將登錄值加入至您的公司機碼。  
  
 下面情況可能會造成例外狀況：  
  
-   機碼名稱為 null。  
  
-   使用者沒有建立登錄機碼的權限。  
  
-   機碼名稱超過 255 個字元的限制。  
  
-   機碼已關閉。  
  
-   登錄機碼是唯讀的。  
  
## .NET Framework 安全性  
 更為安全的做法是將資料寫入至使用者資料夾 \(`Microsoft.Win32.Registry.CurrentUser`\)，而不是寫入至本機電腦 \(`Microsoft.Win32.Registry.LocalMachine`\)。  
  
 當您建立登錄值時，必須先確定該值是否已經存在。  其他處理序 \(也許是惡意的處理序\) 可能已建立該值並且具有其存取權。  當您將資料放入登錄值時，其他處理序就可以使用該資料。  若要預防這個問題，請使用 `Overload:Microsoft.Win32.RegistryKey.GetValue` 方法。  如果機碼不存在，這個方法會傳回 null。  
  
 雖然登錄機碼受到存取控制清單 \(ACL\) 保護，但在登錄中以純文字方式存放機密資料 \(例如密碼\) 仍然是不安全的做法。  
  
## 請參閱  
 <xref:System.IO?displayProperty=fullName>   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [檔案系統和登錄](../../../csharp/programming-guide/file-system/file-system-and-the-registry.md)   
 [使用 C\# 在登錄中進行讀取、寫入和刪除](http://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)