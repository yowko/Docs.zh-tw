---
title: 如何：在 Visual Basic 中刪除登錄機碼
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 28
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0cb98c02531bac133b9dc37a92f75d5c0418dc7c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-delete-a-registry-key-in-visual-basic"></a><span data-ttu-id="d956f-102">如何：在 Visual Basic 中刪除登錄機碼</span><span class="sxs-lookup"><span data-stu-id="d956f-102">How to: Delete a Registry Key in Visual Basic</span></span>
<span data-ttu-id="d956f-103"><xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> 和 <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> 方法可用來刪除登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="d956f-103">The <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> and <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> methods can be used to delete registry keys.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="d956f-104">程序</span><span class="sxs-lookup"><span data-stu-id="d956f-104">Procedure</span></span>  
  
#### <a name="to-delete-a-registry-key"></a><span data-ttu-id="d956f-105">刪除登錄機碼</span><span class="sxs-lookup"><span data-stu-id="d956f-105">To delete a registry key</span></span>  
  
-   <span data-ttu-id="d956f-106">使用 `DeleteSubKey` 方法來刪除登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="d956f-106">Use the `DeleteSubKey` method to delete a registry key.</span></span> <span data-ttu-id="d956f-107">這個範例會刪除 CurrentUser Hive 中的 Software/TestApp 機碼。</span><span class="sxs-lookup"><span data-stu-id="d956f-107">This example deletes the key Software/TestApp in the CurrentUser hive.</span></span> <span data-ttu-id="d956f-108">您可以將程式碼中的這個機碼變更為適當的字串，或讓它依賴使用者提供的資訊。</span><span class="sxs-lookup"><span data-stu-id="d956f-108">You can change this in the code to the appropriate string, or have it rely on user-supplied information.</span></span>  
  
     [!code-vb[VbResourceTasks#19](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-delete-a-registry-key_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="d956f-109">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="d956f-109">Robust Programming</span></span>  
 <span data-ttu-id="d956f-110">如果機碼/值組不存在，則 `DeleteSubKey` 方法會傳回空字串。</span><span class="sxs-lookup"><span data-stu-id="d956f-110">The `DeleteSubKey` method returns an empty string if the key/value pair does not exist.</span></span>  
  
 <span data-ttu-id="d956f-111">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="d956f-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="d956f-112">機碼的名稱是 `Nothing` (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="d956f-112">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="d956f-113">使用者沒有權限，無法刪除登錄機碼 (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="d956f-113">The user does not have permissions to delete registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="d956f-114">機碼名稱超過 255 個字元的限制 (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="d956f-114">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="d956f-115">登錄機碼為唯讀 (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="d956f-115">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="d956f-116">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="d956f-116">.NET Framework Security</span></span>  
 <span data-ttu-id="d956f-117">如果未授與足夠的執行階段權限 (<xref:System.Security.Permissions.RegistryPermission>)，或使用者沒有建立或寫入至設定的正確存取權 (透過 ACL 所決定)，則登錄呼叫會失敗。</span><span class="sxs-lookup"><span data-stu-id="d956f-117">Registry calls fail if either sufficient run-time permissions are not granted (<xref:System.Security.Permissions.RegistryPermission>) or if the user does not have the correct access (as determined by the ACLs) for creating or writing to settings.</span></span> <span data-ttu-id="d956f-118">例如，具有程式碼存取安全性權限的本機應用程式，可能不具有作業系統權限。</span><span class="sxs-lookup"><span data-stu-id="d956f-118">For example, a local application that has the code access security permission might not have operating system permission.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d956f-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d956f-119">See Also</span></span>  
 <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>  
 <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>  
 <xref:Microsoft.Win32.RegistryKey>  
 [<span data-ttu-id="d956f-120">安全性和登錄</span><span class="sxs-lookup"><span data-stu-id="d956f-120">Security and the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)  
 [<span data-ttu-id="d956f-121">讀取和寫入登錄</span><span class="sxs-lookup"><span data-stu-id="d956f-121">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
