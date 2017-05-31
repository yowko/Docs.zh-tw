---
title: "如何：在 Visual Basic 中建立登錄機碼並設定其值 | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- RegistryKey.CreateSubKey
- RegistryKey.SetValue
dev_langs:
- VB
helpviewer_keywords:
- registry keys, creating
- registry, adding values
- registry, adding keys
- registry keys, setting values
- examples [Visual Basic], registry
ms.assetid: d3e40f74-c283-480c-ab18-e5e9052cd814
caps.latest.revision: 30
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
ms.openlocfilehash: 28a01911dc715483aee8191972387781a6f1933e
ms.contentlocale: zh-tw
ms.lasthandoff: 05/22/2017

---
# <a name="how-to-create-a-registry-key-and-set-its-value-in-visual-basic"></a>如何：在 Visual Basic 中建立登錄機碼並設定其值
`My.Computer.Registry` 物件的 `CreateSubKey` 方法可以用來建立登錄機碼。  
  
## <a name="procedure"></a>程序  
  
#### <a name="to-create-a-registry-key"></a>建立登錄機碼  
  
-   使用 `CreateSubKey` 方法，並指定要放置機碼和機碼名稱的 Hive。 `Subkey` 參數不區分大小寫。 這個範例會在 HKEY_CURRENT_USER 下建立 `MyTestKey` 登錄機碼。  
  
     [!code-vb[VbResourceTasks#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_1.vb)]  
  
#### <a name="to-create-a-registry-key-and-set-a-value-in-it"></a>建立登錄機碼並設定其值  
  
1.  使用 `CreateSubkey` 方法，並指定要放置機碼和機碼名稱的 Hive。 這個範例會在 HKEY_CURRENT_USER 下建立 `MyTestKey` 登錄機碼。  
  
     [!code-vb[VbResourceTasks#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_1.vb)]  
  
2.  使用 `SetValue` 方法來設定值。 這個範例會將字串值 "MyTestKeyValue" 設定為 "This is a test value"。  
  
     [!code-vb[VbResourceTasks#14](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_2.vb)]  
  
## <a name="example"></a>範例  
 這個範例會在 HKEY_CURRENT_USER 下建立 `MyTestKey` 登錄機碼，然後將字串值 `MyTestKeyValue` 設定為 `This is a test value`。  
  
 [!code-vb[VbResourceTasks#15](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_3.vb)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 檢查登錄結構以找出適合索引鍵的位置。 例如，您可能想要開啟目前使用者的 HKEY_CURRENT_USER\Software 機碼，並以貴公司的名稱來建立機碼。 請將登錄值新增至貴公司的索引鍵。  
  
 從 Web 應用程式讀取登錄時，目前使用者取決於 Web 應用程式中所實作的驗證和模擬。  
  
 將資料寫入使用者資料夾 (<xref:Microsoft.Win32.Registry.CurrentUser>)，會比寫入本機電腦 (<xref:Microsoft.Win32.Registry.LocalMachine>) 更為安全。  
  
 當您建立登錄值時，您需要決定如果該值已經存在該怎麼辦。 另一個可能是惡意的處理序，可能已建立值並具有其存取權。 當您將資料放在登錄值中時，資料可供其他處理序使用。 若要避免這個問題，請使用 <xref:Microsoft.Win32.RegistryKey.GetValue%2A> 方法。 如果機碼尚未存在，則會傳回 `Nothing`。  
  
 即使使用 ACL (存取控制清單) 來保護登錄機碼，將密碼等機密資料以純文字儲存在登錄中也不安全。  
  
 以下條件可能會造成例外狀況：  
  
-   機碼的名稱為 `Nothing` (<xref:System.ArgumentNullException>)。  
  
-   使用者無權建立登錄機碼 (<xref:System.Security.SecurityException>)。  
  
-   機碼名稱超過 255 個字元的限制 (<xref:System.ArgumentException>)。  
  
-   已關閉機碼 (<xref:System.IO.IOException>)。  
  
-   登錄機碼為唯讀 (<xref:System.UnauthorizedAccessException>)。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 若要執行此程序，您的組件需要 <xref:System.Security.Permissions.RegistryPermission> 類別所授與的權限等級。 若在部分信任內容中執行，程序可能會因為權限不足而擲回例外狀況。 同樣地，使用者必須有正確的 ACL，才能建立或寫入設定。 例如，具有程式碼存取安全性權限的本機應用程式，可能不具有作業系統權限。 如需詳細資訊，請參閱[程式碼存取安全性基本概念](https://msdn.microsoft.com/library/33tceax8)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>   
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A>   
 <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>   
 [讀取和寫入登錄](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)   
 [程式碼存取安全性的基本概念](https://msdn.microsoft.com/library/33tceax8)
