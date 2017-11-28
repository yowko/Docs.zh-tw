---
title: "安全性和登錄 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- security [Visual Basic], registry
- registry [Visual Basic], security issues
ms.assetid: 9980aff7-2f69-492b-8f66-29a9a76d3df5
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0961d21417cbb5efcd9f38112c4e8ecb393faccd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="security-and-the-registry-visual-basic"></a>安全性和登錄 (Visual Basic)
此頁面說明將資料儲存在登錄中的安全隱憂。  
  
## <a name="permissions"></a>權限  
 即使使用 ACL (存取控制清單) 來保護登錄機碼，將密碼等機密資料以純文字儲存在登錄中也不安全。  
  
 如果允許不適當地存取系統資源或受保護資訊，則使用登錄可能會危及安全性。 若要使用這些屬性，您必須擁有讀取及寫入 <xref:System.Security.Permissions.RegistryPermissionAccess> 列舉的權限，以便控制登錄變數的存取。 任何以完全信任條件來執行的程式碼 (以預設安全性原則來看，即為安裝在使用者本機硬碟上的任何程式碼)，都具有存取登錄的必要權限。 如需詳細資訊，請參閱 <xref:System.Security.Permissions.RegistryPermission> 類別。  
  
 您不應將登錄變數儲存在記憶體位置，因為不具備 <xref:System.Security.Permissions.RegistryPermission> 的程式碼亦可存取這個位置。 同樣地，當授與權限時，請授與完成工作所需的最低權限。  
  
 登錄權限存取值是由 <xref:System.Security.Permissions.RegistryPermissionAccess> 列舉定義。 下表會詳細說明其成員。  
  
|值|登錄變數的存取權|  
|-----------|----------------------------------|  
|`AllAccess`|建立、讀取和寫入|  
|`Create`|建立|  
|`NoAccess`|沒有存取權|  
|`Read`|讀取|  
|`Write`|Write|  
  
## <a name="checking-values-in-registry-keys"></a>檢查登錄機碼值  
 當您建立登錄值時，您需要決定如果該值已經存在該怎麼辦。 另一個可能是惡意的處理序，可能已建立值並具有其存取權。 當您將資料放在登錄值中時，資料可供其他處理序使用。 為避免此問題，請使用 `GetValue` 方法。 如果機碼尚未存在，則會傳回 `Nothing`。  
  
> [!IMPORTANT]
>  從 Web 應用程式讀取登錄時，目前使用者的身分識別取決於 Web 應用程式中所實作的驗證和模擬。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 [讀取和寫入登錄](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
