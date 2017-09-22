---
title: "如何：在 Visual Basic 中刪除登錄機碼"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.DeleteSetting
dev_langs:
- VB
helpviewer_keywords:
- GetSetting function
- registry, deleting values
- GetAllSettings function
- registry keys, deleting
- registry, deleting keys
- examples [Visual Basic], registry
ms.assetid: ab9aca0e-42b0-4ff7-8ff9-845a4bfdf9f2
caps.latest.revision: 28
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 0fc37aff9f6a0ae3a7953377ebf95179d01bb693
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# How to: Delete a Registry Key in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

<xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> 和 <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> 方法可以用來刪除登錄機碼 \(Registry Key\)。  
  
## 程序  
  
#### 若要刪除登錄機碼  
  
-   使用 `DeleteSubKey` 方法來刪除登錄機碼。  此範例刪除了 CurrentUser 登錄區中的機碼 Software\/TestApp。  您可以在程式碼中，將此機碼變更成適當的字串，或採用使用者提供的資訊。  
  
     [!code-vb[VbResourceTasks#19](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-delete-a-registry-key_1.vb)]  
  
## 穩固程式設計  
 如果機碼\/值組不存在，則 `DeleteSubKey` 方法會傳回空字串。  
  
 下列情形可能會造成例外狀況 \(Exception\)：  
  
-   機碼的名稱為 `Nothing` \(<xref:System.ArgumentNullException>\)。  
  
-   使用者沒有刪除登錄機碼 \(<xref:System.Security.SecurityException>\) 的使用權限。  
  
-   機碼名稱超過 255 個字元的限制 \(<xref:System.ArgumentException>\)。  
  
-   登錄機碼為唯讀 \(<xref:System.UnauthorizedAccessException>\)。  
  
## .NET Framework 安全性  
 如果未授與足夠的執行階段使用權限 \(<xref:System.Security.Permissions.RegistryPermission>\)，或使用者不具有正確的建立或寫入存取權 \(由 ACL 判斷\)，則登錄呼叫會失敗。  例如，具有程式碼存取安全性權限的本機應用程式，可能不具有作業系統使用權限。  
  
## 請參閱  
 <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>   
 <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>   
 <xref:Microsoft.Win32.RegistryKey>   
 [安全性和登錄](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)   
 [讀取和寫入登錄](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)

