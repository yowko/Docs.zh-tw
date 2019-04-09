---
title: 作法：在 Visual Basic 中讀取登錄機碼的值
ms.date: 07/20/2015
helpviewer_keywords:
- registry keys [Visual Basic], determining if a value exists in
- My.Computer.Registry object, examples
- registry [Visual Basic], determining if values exist
- registry keys [Visual Basic], reading from
- registry [Visual Basic], reading
ms.assetid: 775d0a57-68c9-464e-8949-9a39bd29cc64
ms.openlocfilehash: bc71dd2e3a78454236b2f6f30c2d51aa596e5b8c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58840181"
---
# <a name="how-to-read-a-value-from-a-registry-key-in-visual-basic"></a><span data-ttu-id="779aa-102">作法：在 Visual Basic 中讀取登錄機碼的值</span><span class="sxs-lookup"><span data-stu-id="779aa-102">How to: Read a Value from a Registry Key in Visual Basic</span></span>
<span data-ttu-id="779aa-103">您可以使用 `My.Computer.Registry` 物件的 `GetValue` 方法來讀取 Windows 登錄中的值。</span><span class="sxs-lookup"><span data-stu-id="779aa-103">The `GetValue` method of the `My.Computer.Registry` object can be used to read values in the Windows registry.</span></span>  
  
 <span data-ttu-id="779aa-104">如果下列範例中的機碼 "Software\MyApp" 不存在，則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="779aa-104">If the key, "Software\MyApp" in the following example, does not exist, an exception is thrown.</span></span> <span data-ttu-id="779aa-105">如果下列範例中的 `ValueName` (也就是 "Name") 不存在，則會傳回 `Nothing`。</span><span class="sxs-lookup"><span data-stu-id="779aa-105">If the `ValueName`,  "Name" in the following example, does not exist, `Nothing` is returned.</span></span>  
  
 <span data-ttu-id="779aa-106">`GetValue` 方法也可用來判斷特定登錄機碼中是否有指定的值。</span><span class="sxs-lookup"><span data-stu-id="779aa-106">The `GetValue` method can also be used to determine whether a given value exists in a specific registry key.</span></span>  
  
 <span data-ttu-id="779aa-107">當程式碼從 Web 應用程式讀取登錄時，會由 Web 應用程式中所實作的驗證和模擬來決定目前的使用者。</span><span class="sxs-lookup"><span data-stu-id="779aa-107">When code reads the registry from a Web application, the current user is determined by the authentication and impersonation that is implemented in the Web application.</span></span>  
  
### <a name="to-read-a-value-from-a-registry-key"></a><span data-ttu-id="779aa-108">讀取登錄機碼的值</span><span class="sxs-lookup"><span data-stu-id="779aa-108">To read a value from a registry key</span></span>  
  
-   <span data-ttu-id="779aa-109">使用 `GetValue` 方法，並指定路徑和名稱來讀取登錄機碼的值。</span><span class="sxs-lookup"><span data-stu-id="779aa-109">Use the `GetValue` method, specifying the path and name) to read a value from registry key.</span></span> <span data-ttu-id="779aa-110">下列範例會從 `HKEY_CURRENT_USER\Software\MyApp` 讀取 `Name` 值，並顯示於訊息方塊中。</span><span class="sxs-lookup"><span data-stu-id="779aa-110">The following example reads the value `Name` from `HKEY_CURRENT_USER\Software\MyApp` and displays it in a message box.</span></span>  
  
     [!code-vb[VbResourceTasks#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#4)]  
  
 <span data-ttu-id="779aa-111">這個程式碼範例也可用為 IntelliSense 程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="779aa-111">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="779aa-112">在程式碼片段選擇器中，它位於 [Windows 作業系統] > [登錄] 中。</span><span class="sxs-lookup"><span data-stu-id="779aa-112">In the code snippet picker, it is located in **Windows Operating System > Registry**.</span></span> <span data-ttu-id="779aa-113">如需詳細資訊，請參閱[程式碼片段](/visualstudio/ide/code-snippets)。</span><span class="sxs-lookup"><span data-stu-id="779aa-113">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
### <a name="to-determine-whether-a-value-exists-in-a-registry-key"></a><span data-ttu-id="779aa-114">判斷登錄機碼中是否有一個值</span><span class="sxs-lookup"><span data-stu-id="779aa-114">To determine whether a value exists in a registry key</span></span>  
  
-   <span data-ttu-id="779aa-115">使用 `GetValue` 方法來擷取此值。</span><span class="sxs-lookup"><span data-stu-id="779aa-115">Use the `GetValue` method to retrieve the value.</span></span> <span data-ttu-id="779aa-116">下列程式碼會檢查此值是否存在；如果不存在，則傳回訊息。</span><span class="sxs-lookup"><span data-stu-id="779aa-116">The following code checks whether the value exists and returns a message if it does not.</span></span>  
  
     [!code-vb[VbResourceTasks#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#12)]  
  
## <a name="robust-programming"></a><span data-ttu-id="779aa-117">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="779aa-117">Robust Programming</span></span>  
 <span data-ttu-id="779aa-118">登錄包含可用來儲存資料的最上層或根目錄機碼。</span><span class="sxs-lookup"><span data-stu-id="779aa-118">The registry holds top-level, or root, keys that are used to store data.</span></span> <span data-ttu-id="779aa-119">例如，HKEY_LOCAL_MACHINE 根目錄機碼可用於儲存所有使用者所使用的電腦層級設定，而 HKEY_CURRENT_USER 可用於儲存個別使用者的特定資料。</span><span class="sxs-lookup"><span data-stu-id="779aa-119">For instance, the HKEY_LOCAL_MACHINE root key is used for storing machine-level settings used by all users, while HKEY_CURRENT_USER is used for storing data specific to an individual user.</span></span>  
  
 <span data-ttu-id="779aa-120">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="779aa-120">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="779aa-121">機碼的名稱是 `Nothing` (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="779aa-121">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="779aa-122">使用者沒有讀取登錄機碼的權限 (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="779aa-122">The user does not have permissions to read from registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="779aa-123">機碼名稱超過 255 個字元的限制 (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="779aa-123">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="779aa-124">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="779aa-124">.NET Framework Security</span></span>  
 <span data-ttu-id="779aa-125">若要執行此程序，您的組件需要由 <xref:System.Security.Permissions.RegistryPermission> 類別授與的權限層級。</span><span class="sxs-lookup"><span data-stu-id="779aa-125">To run this process, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.RegistryPermission> class.</span></span> <span data-ttu-id="779aa-126">若在部分信任內容中執行，程序可能會因為權限不足而擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="779aa-126">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="779aa-127">同樣地，使用者必須有正確的 ACL，才能建立或寫入設定。</span><span class="sxs-lookup"><span data-stu-id="779aa-127">Similarly, the user must have the correct ACLs for creating or writing to settings.</span></span> <span data-ttu-id="779aa-128">例如，具有程式碼存取安全性權限的本機應用程式，可能不具有作業系統權限。</span><span class="sxs-lookup"><span data-stu-id="779aa-128">For example, a local application that has the code access security permission might not have operating system permission.</span></span> <span data-ttu-id="779aa-129">如需詳細資訊，請參閱[程式碼存取安全性基本概念](../../../../framework/misc/code-access-security-basics.md)。</span><span class="sxs-lookup"><span data-stu-id="779aa-129">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="779aa-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="779aa-130">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.Win32.RegistryHive>
- [<span data-ttu-id="779aa-131">讀取和寫入登錄</span><span class="sxs-lookup"><span data-stu-id="779aa-131">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
