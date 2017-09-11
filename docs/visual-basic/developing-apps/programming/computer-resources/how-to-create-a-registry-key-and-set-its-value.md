---
title: "如何：在 Visual Basic 中建立登錄機碼並設定其值"
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 106a98a1b15c37eb2cac05e1a681bf7dfed3543d
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-create-a-registry-key-and-set-its-value-in-visual-basic"></a><span data-ttu-id="b0c58-102">如何：在 Visual Basic 中建立登錄機碼並設定其值</span><span class="sxs-lookup"><span data-stu-id="b0c58-102">How to: Create a Registry Key and Set Its Value in Visual Basic</span></span>
<span data-ttu-id="b0c58-103">`My.Computer.Registry` 物件的 `CreateSubKey` 方法可以用來建立登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="b0c58-103">The `CreateSubKey` method of the `My.Computer.Registry` object can be used to create a registry key.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="b0c58-104">程序</span><span class="sxs-lookup"><span data-stu-id="b0c58-104">Procedure</span></span>  
  
#### <a name="to-create-a-registry-key"></a><span data-ttu-id="b0c58-105">建立登錄機碼</span><span class="sxs-lookup"><span data-stu-id="b0c58-105">To create a registry key</span></span>  
  
-   <span data-ttu-id="b0c58-106">使用 `CreateSubKey` 方法，並指定要放置機碼和機碼名稱的 Hive。</span><span class="sxs-lookup"><span data-stu-id="b0c58-106">Use the `CreateSubKey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="b0c58-107">`Subkey` 參數不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="b0c58-107">The parameter `Subkey` is not case-sensitive.</span></span> <span data-ttu-id="b0c58-108">這個範例會在 HKEY_CURRENT_USER 下建立 `MyTestKey` 登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="b0c58-108">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>  
  
     <span data-ttu-id="b0c58-109">[!code-vb[VbResourceTasks#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="b0c58-109">[!code-vb[VbResourceTasks#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_1.vb)]</span></span>  
  
#### <a name="to-create-a-registry-key-and-set-a-value-in-it"></a><span data-ttu-id="b0c58-110">建立登錄機碼並設定其值</span><span class="sxs-lookup"><span data-stu-id="b0c58-110">To create a registry key and set a value in it</span></span>  
  
1.  <span data-ttu-id="b0c58-111">使用 `CreateSubkey` 方法，並指定要放置機碼和機碼名稱的 Hive。</span><span class="sxs-lookup"><span data-stu-id="b0c58-111">Use the `CreateSubkey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="b0c58-112">這個範例會在 HKEY_CURRENT_USER 下建立 `MyTestKey` 登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="b0c58-112">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>  
  
     <span data-ttu-id="b0c58-113">[!code-vb[VbResourceTasks#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="b0c58-113">[!code-vb[VbResourceTasks#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_1.vb)]</span></span>  
  
2.  <span data-ttu-id="b0c58-114">使用 `SetValue` 方法來設定值。</span><span class="sxs-lookup"><span data-stu-id="b0c58-114">Set the value with the `SetValue` method.</span></span> <span data-ttu-id="b0c58-115">這個範例會將字串值</span><span class="sxs-lookup"><span data-stu-id="b0c58-115">This example sets the string value.</span></span> <span data-ttu-id="b0c58-116">"MyTestKeyValue" 設定為 "This is a test value"。</span><span class="sxs-lookup"><span data-stu-id="b0c58-116">"MyTestKeyValue" to "This is a test value".</span></span>  
  
     <span data-ttu-id="b0c58-117">[!code-vb[VbResourceTasks#14](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="b0c58-117">[!code-vb[VbResourceTasks#14](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_2.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0c58-118">範例</span><span class="sxs-lookup"><span data-stu-id="b0c58-118">Example</span></span>  
 <span data-ttu-id="b0c58-119">這個範例會在 HKEY_CURRENT_USER 下建立 `MyTestKey` 登錄機碼，然後將字串值 `MyTestKeyValue` 設定為 `This is a test value`。</span><span class="sxs-lookup"><span data-stu-id="b0c58-119">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER and then sets the string value `MyTestKeyValue` to `This is a test value`.</span></span>  
  
 <span data-ttu-id="b0c58-120">[!code-vb[VbResourceTasks#15](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="b0c58-120">[!code-vb[VbResourceTasks#15](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_3.vb)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="b0c58-121">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="b0c58-121">Robust Programming</span></span>  
 <span data-ttu-id="b0c58-122">檢查登錄結構以找出適合索引鍵的位置。</span><span class="sxs-lookup"><span data-stu-id="b0c58-122">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="b0c58-123">例如，您可能想要開啟目前使用者的 HKEY_CURRENT_USER\Software 機碼，並以貴公司的名稱來建立機碼。</span><span class="sxs-lookup"><span data-stu-id="b0c58-123">For example, you may want to open the HKEY_CURRENT_USER\Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="b0c58-124">請將登錄值新增至貴公司的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="b0c58-124">Then add the registry values to your company's key.</span></span>  
  
 <span data-ttu-id="b0c58-125">從 Web 應用程式讀取登錄時，目前使用者取決於 Web 應用程式中所實作的驗證和模擬。</span><span class="sxs-lookup"><span data-stu-id="b0c58-125">When reading the registry from a Web application, the current user depends on the authentication and impersonation implemented in the Web application.</span></span>  
  
 <span data-ttu-id="b0c58-126">將資料寫入使用者資料夾 (<xref:Microsoft.Win32.Registry.CurrentUser>) 比寫入本機電腦 (<xref:Microsoft.Win32.Registry.LocalMachine>) 更安全。</span><span class="sxs-lookup"><span data-stu-id="b0c58-126">It is more secure to write data to the user folder (<xref:Microsoft.Win32.Registry.CurrentUser>) rather than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span></span>  
  
 <span data-ttu-id="b0c58-127">當您建立登錄值時，您需要決定如果該值已經存在該怎麼辦。</span><span class="sxs-lookup"><span data-stu-id="b0c58-127">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="b0c58-128">另一個可能是惡意的處理序，可能已建立值並具有其存取權。</span><span class="sxs-lookup"><span data-stu-id="b0c58-128">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="b0c58-129">當您將資料放在登錄值中時，資料可供其他處理序使用。</span><span class="sxs-lookup"><span data-stu-id="b0c58-129">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="b0c58-130">為避免此問題，請使用 <xref:Microsoft.Win32.RegistryKey.GetValue%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="b0c58-130">To prevent this, use the <xref:Microsoft.Win32.RegistryKey.GetValue%2A> method.</span></span> <span data-ttu-id="b0c58-131">如果機碼尚未存在，則會傳回 `Nothing`。</span><span class="sxs-lookup"><span data-stu-id="b0c58-131">It returns `Nothing` if the key does not already exist.</span></span>  
  
 <span data-ttu-id="b0c58-132">即使使用 ACL (存取控制清單) 來保護登錄機碼，將密碼等機密資料以純文字儲存在登錄中也不安全。</span><span class="sxs-lookup"><span data-stu-id="b0c58-132">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (Access Control Lists).</span></span>  
  
 <span data-ttu-id="b0c58-133">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="b0c58-133">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="b0c58-134">機碼的名稱是 `Nothing` (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="b0c58-134">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="b0c58-135">使用者沒有權限，無法建立登錄機碼 (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="b0c58-135">The user does not have permissions to create registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="b0c58-136">機碼名稱超過 255 個字元的限制 (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="b0c58-136">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="b0c58-137">機碼已關閉 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="b0c58-137">The key is closed (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="b0c58-138">登錄機碼為唯讀 (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="b0c58-138">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="b0c58-139">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="b0c58-139">.NET Framework Security</span></span>  
 <span data-ttu-id="b0c58-140">若要執行此程序，您的組件需要由 <xref:System.Security.Permissions.RegistryPermission> 類別授與的權限層級。</span><span class="sxs-lookup"><span data-stu-id="b0c58-140">To run this process, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.RegistryPermission> class.</span></span> <span data-ttu-id="b0c58-141">若在部分信任內容中執行，程序可能會因為權限不足而擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b0c58-141">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="b0c58-142">同樣地，使用者必須有正確的 ACL，才能建立或寫入設定。</span><span class="sxs-lookup"><span data-stu-id="b0c58-142">Similarly, the user must have the correct ACLs for creating or writing to settings.</span></span> <span data-ttu-id="b0c58-143">例如，具有程式碼存取安全性權限的本機應用程式，可能不具有作業系統權限。</span><span class="sxs-lookup"><span data-stu-id="b0c58-143">For example, a local application that has the code access security permission might not have operating system permission.</span></span> <span data-ttu-id="b0c58-144">如需詳細資訊，請參閱[程式碼存取安全性基本概念](https://msdn.microsoft.com/library/33tceax8)。</span><span class="sxs-lookup"><span data-stu-id="b0c58-144">For more information, see [Code Access Security Basics](https://msdn.microsoft.com/library/33tceax8).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0c58-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0c58-145">See Also</span></span>  
 <span data-ttu-id="b0c58-146"><xref:Microsoft.VisualBasic.MyServices.RegistryProxy></span><span class="sxs-lookup"><span data-stu-id="b0c58-146"><xref:Microsoft.VisualBasic.MyServices.RegistryProxy></span></span>   
 <span data-ttu-id="b0c58-147"><xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A></span><span class="sxs-lookup"><span data-stu-id="b0c58-147"><xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A></span></span>   
 <span data-ttu-id="b0c58-148"><xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A></span><span class="sxs-lookup"><span data-stu-id="b0c58-148"><xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A></span></span>   
 <span data-ttu-id="b0c58-149">[讀取和寫入登錄](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md) </span><span class="sxs-lookup"><span data-stu-id="b0c58-149">[Reading from and Writing to the Registry](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md) </span></span>  
 [<span data-ttu-id="b0c58-150">程式碼存取安全性的基本概念</span><span class="sxs-lookup"><span data-stu-id="b0c58-150">Code Access Security Basics</span></span>](https://msdn.microsoft.com/library/33tceax8)

