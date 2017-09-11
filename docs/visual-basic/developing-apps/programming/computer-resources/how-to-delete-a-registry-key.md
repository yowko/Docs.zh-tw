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
# <a name="how-to-delete-a-registry-key-in-visual-basic"></a><span data-ttu-id="ac71f-102">如何：在 Visual Basic 中刪除登錄機碼</span><span class="sxs-lookup"><span data-stu-id="ac71f-102">How to: Delete a Registry Key in Visual Basic</span></span>
<span data-ttu-id="ac71f-103"><xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> 和 <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> 方法可用來刪除登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="ac71f-103">The <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> and <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> methods can be used to delete registry keys.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="ac71f-104">程序</span><span class="sxs-lookup"><span data-stu-id="ac71f-104">Procedure</span></span>  
  
#### <a name="to-delete-a-registry-key"></a><span data-ttu-id="ac71f-105">刪除登錄機碼</span><span class="sxs-lookup"><span data-stu-id="ac71f-105">To delete a registry key</span></span>  
  
-   <span data-ttu-id="ac71f-106">使用 `DeleteSubKey` 方法來刪除登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="ac71f-106">Use the `DeleteSubKey` method to delete a registry key.</span></span> <span data-ttu-id="ac71f-107">這個範例會刪除 CurrentUser Hive 中的 Software/TestApp 機碼。</span><span class="sxs-lookup"><span data-stu-id="ac71f-107">This example deletes the key Software/TestApp in the CurrentUser hive.</span></span> <span data-ttu-id="ac71f-108">您可以將程式碼中的這個機碼變更為適當的字串，或讓它依賴使用者提供的資訊。</span><span class="sxs-lookup"><span data-stu-id="ac71f-108">You can change this in the code to the appropriate string, or have it rely on user-supplied information.</span></span>  
  
     <span data-ttu-id="ac71f-109">[!code-vb[VbResourceTasks#19](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-delete-a-registry-key_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="ac71f-109">[!code-vb[VbResourceTasks#19](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-delete-a-registry-key_1.vb)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="ac71f-110">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="ac71f-110">Robust Programming</span></span>  
 <span data-ttu-id="ac71f-111">如果機碼/值組不存在，則 `DeleteSubKey` 方法會傳回空字串。</span><span class="sxs-lookup"><span data-stu-id="ac71f-111">The `DeleteSubKey` method returns an empty string if the key/value pair does not exist.</span></span>  
  
 <span data-ttu-id="ac71f-112">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="ac71f-112">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="ac71f-113">機碼的名稱是 `Nothing` (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="ac71f-113">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="ac71f-114">使用者沒有權限，無法刪除登錄機碼 (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="ac71f-114">The user does not have permissions to delete registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="ac71f-115">機碼名稱超過 255 個字元的限制 (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="ac71f-115">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="ac71f-116">登錄機碼為唯讀 (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="ac71f-116">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="ac71f-117">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="ac71f-117">.NET Framework Security</span></span>  
 <span data-ttu-id="ac71f-118">如果未授與足夠的執行階段權限 (<xref:System.Security.Permissions.RegistryPermission>)，或使用者沒有建立或寫入至設定的正確存取權 (透過 ACL 所決定)，則登錄呼叫會失敗。</span><span class="sxs-lookup"><span data-stu-id="ac71f-118">Registry calls fail if either sufficient run-time permissions are not granted (<xref:System.Security.Permissions.RegistryPermission>) or if the user does not have the correct access (as determined by the ACLs) for creating or writing to settings.</span></span> <span data-ttu-id="ac71f-119">例如，具有程式碼存取安全性權限的本機應用程式，可能不具有作業系統權限。</span><span class="sxs-lookup"><span data-stu-id="ac71f-119">For example, a local application that has the code access security permission might not have operating system permission.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac71f-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac71f-120">See Also</span></span>  
 <span data-ttu-id="ac71f-121"><xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A></span><span class="sxs-lookup"><span data-stu-id="ac71f-121"><xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A></span></span>   
 <span data-ttu-id="ac71f-122"><xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A></span><span class="sxs-lookup"><span data-stu-id="ac71f-122"><xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A></span></span>   
 <span data-ttu-id="ac71f-123"><xref:Microsoft.Win32.RegistryKey></span><span class="sxs-lookup"><span data-stu-id="ac71f-123"><xref:Microsoft.Win32.RegistryKey></span></span>   
 <span data-ttu-id="ac71f-124">[安全性和登錄](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md) </span><span class="sxs-lookup"><span data-stu-id="ac71f-124">[Security and the Registry](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md) </span></span>  
 [<span data-ttu-id="ac71f-125">讀取和寫入登錄</span><span class="sxs-lookup"><span data-stu-id="ac71f-125">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)

