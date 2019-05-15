---
title: 作法：在 Visual Basic 中刪除登錄機碼
ms.date: 07/20/2015
f1_keywords:
- vb.DeleteSetting
helpviewer_keywords:
- GetSetting function [Visual Basic]
- registry [Visual Basic], deleting values
- GetAllSettings function
- registry keys [Visual Basic], deleting
- registry [Visual Basic], deleting keys
- examples [Visual Basic], registry
ms.assetid: ab9aca0e-42b0-4ff7-8ff9-845a4bfdf9f2
ms.openlocfilehash: 2e0c8990fcc55bc4208b1c23690ff748b7167002
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662762"
---
# <a name="how-to-delete-a-registry-key-in-visual-basic"></a>作法：在 Visual Basic 中刪除登錄機碼
<xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> 和 <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> 方法可用來刪除登錄機碼。  
  
## <a name="procedure"></a>程序  
  
#### <a name="to-delete-a-registry-key"></a>刪除登錄機碼  
  
- 使用 `DeleteSubKey` 方法來刪除登錄機碼。 這個範例會刪除 CurrentUser Hive 中的 Software/TestApp 機碼。 您可以將程式碼中的這個機碼變更為適當的字串，或讓它依賴使用者提供的資訊。  
  
     [!code-vb[VbResourceTasks#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#19)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 如果機碼/值組不存在，則 `DeleteSubKey` 方法會傳回空字串。  
  
 以下條件可能會造成例外狀況：  
  
- 機碼的名稱是 `Nothing` (<xref:System.ArgumentNullException>)。  
  
- 使用者沒有權限，無法刪除登錄機碼 (<xref:System.Security.SecurityException>)。  
  
- 機碼名稱超過 255 個字元的限制 (<xref:System.ArgumentException>)。  
  
- 登錄機碼為唯讀 (<xref:System.UnauthorizedAccessException>)。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 如果未授與足夠的執行階段權限 (<xref:System.Security.Permissions.RegistryPermission>)，或使用者沒有建立或寫入至設定的正確存取權 (透過 ACL 所決定)，則登錄呼叫會失敗。 例如，具有程式碼存取安全性權限的本機應用程式，可能不具有作業系統權限。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>
- <xref:Microsoft.Win32.RegistryKey>
- [安全性和登錄](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)
- [讀取和寫入登錄](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
