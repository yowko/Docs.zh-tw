---
title: "如何：在 Visual Basic 中刪除登錄機碼 | Microsoft Docs"
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: a50ee5a0853e6209c3bf5d5224d536f4cc6bbe11
ms.contentlocale: zh-tw
ms.lasthandoff: 05/22/2017

---
# <a name="how-to-delete-a-registry-key-in-visual-basic"></a>如何：在 Visual Basic 中刪除登錄機碼
<xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> 和 <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> 方法可以用來刪除登錄機碼。  
  
## <a name="procedure"></a>程序  
  
#### <a name="to-delete-a-registry-key"></a>刪除登錄機碼  
  
-   使用 `DeleteSubKey` 方法來刪除登錄機碼。 這個範例會刪除 CurrentUser Hive 中的 Software/TestApp 機碼。 您可以將程式碼中的這個機碼變更為適當的字串，或讓它依賴使用者提供的資訊。  
  
     [!code-vb[VbResourceTasks#19](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-delete-a-registry-key_1.vb)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 如果機碼/值組不存在，則 `DeleteSubKey` 方法會傳回空字串。  
  
 以下條件可能會造成例外狀況：  
  
-   機碼的名稱為 `Nothing` (<xref:System.ArgumentNullException>)。  
  
-   使用者無權刪除登錄機碼 (<xref:System.Security.SecurityException>)。  
  
-   機碼名稱超過 255 個字元的限制 (<xref:System.ArgumentException>)。  
  
-   登錄機碼為唯讀 (<xref:System.UnauthorizedAccessException>)。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 如果未授與足夠的執行階段權限 (<xref:System.Security.Permissions.RegistryPermission>)，或使用者沒有建立或寫入至設定的正確存取權 (透過 ACL 所決定)，則登錄呼叫會失敗。 例如，具有程式碼存取安全性權限的本機應用程式，可能不具有作業系統權限。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>   
 <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>   
 <xref:Microsoft.Win32.RegistryKey>   
 [安全性和登錄](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)   
 [讀取和寫入登錄](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
