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
# <a name="security-and-the-registry-visual-basic"></a><span data-ttu-id="b95f8-102">安全性和登錄 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b95f8-102">Security and the Registry (Visual Basic)</span></span>
<span data-ttu-id="b95f8-103">此頁面說明將資料儲存在登錄中的安全隱憂。</span><span class="sxs-lookup"><span data-stu-id="b95f8-103">This page discusses the security implications of storing data in the registry.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="b95f8-104">權限</span><span class="sxs-lookup"><span data-stu-id="b95f8-104">Permissions</span></span>  
 <span data-ttu-id="b95f8-105">即使使用 ACL (存取控制清單) 來保護登錄機碼，將密碼等機密資料以純文字儲存在登錄中也不安全。</span><span class="sxs-lookup"><span data-stu-id="b95f8-105">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (access control lists).</span></span>  
  
 <span data-ttu-id="b95f8-106">如果允許不適當地存取系統資源或受保護資訊，則使用登錄可能會危及安全性。</span><span class="sxs-lookup"><span data-stu-id="b95f8-106">Working with the registry may compromise security by allowing inappropriate access to system resources or protected information.</span></span> <span data-ttu-id="b95f8-107">若要使用這些屬性，您必須擁有讀取及寫入 <xref:System.Security.Permissions.RegistryPermissionAccess> 列舉的權限，以便控制登錄變數的存取。</span><span class="sxs-lookup"><span data-stu-id="b95f8-107">To use these properties, you must have read and write permissions from the <xref:System.Security.Permissions.RegistryPermissionAccess> enumeration, which controls access to registry variables.</span></span> <span data-ttu-id="b95f8-108">任何以完全信任條件來執行的程式碼 (以預設安全性原則來看，即為安裝在使用者本機硬碟上的任何程式碼)，都具有存取登錄的必要權限。</span><span class="sxs-lookup"><span data-stu-id="b95f8-108">Any code running with full trust (under the default security policy, this is any code installed on the user's local hard disk) has the necessary permissions to access the registry.</span></span> <span data-ttu-id="b95f8-109">如需詳細資訊，請參閱 <xref:System.Security.Permissions.RegistryPermission> 類別。</span><span class="sxs-lookup"><span data-stu-id="b95f8-109">For more information, see <xref:System.Security.Permissions.RegistryPermission> class.</span></span>  
  
 <span data-ttu-id="b95f8-110">您不應將登錄變數儲存在記憶體位置，因為不具備 <xref:System.Security.Permissions.RegistryPermission> 的程式碼亦可存取這個位置。</span><span class="sxs-lookup"><span data-stu-id="b95f8-110">Registry variables should not be stored in memory locations where code without <xref:System.Security.Permissions.RegistryPermission> can access them.</span></span> <span data-ttu-id="b95f8-111">同樣地，當授與權限時，請授與完成工作所需的最低權限。</span><span class="sxs-lookup"><span data-stu-id="b95f8-111">Similarly, when granting permissions, grant the minimum privileges necessary to get the job done.</span></span>  
  
 <span data-ttu-id="b95f8-112">登錄權限存取值是由 <xref:System.Security.Permissions.RegistryPermissionAccess> 列舉定義。</span><span class="sxs-lookup"><span data-stu-id="b95f8-112">Registry permission access values are defined by the <xref:System.Security.Permissions.RegistryPermissionAccess> enumeration.</span></span> <span data-ttu-id="b95f8-113">下表會詳細說明其成員。</span><span class="sxs-lookup"><span data-stu-id="b95f8-113">The following table details its members.</span></span>  
  
|<span data-ttu-id="b95f8-114">值</span><span class="sxs-lookup"><span data-stu-id="b95f8-114">Value</span></span>|<span data-ttu-id="b95f8-115">登錄變數的存取權</span><span class="sxs-lookup"><span data-stu-id="b95f8-115">Access to Registry Variables</span></span>|  
|-----------|----------------------------------|  
|`AllAccess`|<span data-ttu-id="b95f8-116">建立、讀取和寫入</span><span class="sxs-lookup"><span data-stu-id="b95f8-116">Create, read, and write</span></span>|  
|`Create`|<span data-ttu-id="b95f8-117">建立</span><span class="sxs-lookup"><span data-stu-id="b95f8-117">Create</span></span>|  
|`NoAccess`|<span data-ttu-id="b95f8-118">沒有存取權</span><span class="sxs-lookup"><span data-stu-id="b95f8-118">No access</span></span>|  
|`Read`|<span data-ttu-id="b95f8-119">讀取</span><span class="sxs-lookup"><span data-stu-id="b95f8-119">Read</span></span>|  
|`Write`|<span data-ttu-id="b95f8-120">Write</span><span class="sxs-lookup"><span data-stu-id="b95f8-120">Write</span></span>|  
  
## <a name="checking-values-in-registry-keys"></a><span data-ttu-id="b95f8-121">檢查登錄機碼值</span><span class="sxs-lookup"><span data-stu-id="b95f8-121">Checking Values in Registry Keys</span></span>  
 <span data-ttu-id="b95f8-122">當您建立登錄值時，您需要決定如果該值已經存在該怎麼辦。</span><span class="sxs-lookup"><span data-stu-id="b95f8-122">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="b95f8-123">另一個可能是惡意的處理序，可能已建立值並具有其存取權。</span><span class="sxs-lookup"><span data-stu-id="b95f8-123">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="b95f8-124">當您將資料放在登錄值中時，資料可供其他處理序使用。</span><span class="sxs-lookup"><span data-stu-id="b95f8-124">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="b95f8-125">為避免此問題，請使用 `GetValue` 方法。</span><span class="sxs-lookup"><span data-stu-id="b95f8-125">To prevent this, use the `GetValue` method.</span></span> <span data-ttu-id="b95f8-126">如果機碼尚未存在，則會傳回 `Nothing`。</span><span class="sxs-lookup"><span data-stu-id="b95f8-126">It returns `Nothing` if the key does not already exist.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b95f8-127">從 Web 應用程式讀取登錄時，目前使用者的身分識別取決於 Web 應用程式中所實作的驗證和模擬。</span><span class="sxs-lookup"><span data-stu-id="b95f8-127">When reading the registry from a Web application, the identity of current user depends on the authentication and impersonation implemented in the Web application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b95f8-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b95f8-128">See Also</span></span>  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 [<span data-ttu-id="b95f8-129">讀取和寫入登錄</span><span class="sxs-lookup"><span data-stu-id="b95f8-129">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
