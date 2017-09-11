---
title: "如何：在登錄中建立機碼 (Visual C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- registry, adding keys and values [C#]
- registry keys, creating [C#]
- keys, creating in registry
ms.assetid: 8fa475b0-e01f-483a-9327-fd03488fdf5d
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
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
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3a377a85acdc31b426171ab6583bff92b24889b3
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-a-key-in-the-registry-visual-c"></a><span data-ttu-id="35989-102">如何：在登錄中建立機碼 (Visual C#)</span><span class="sxs-lookup"><span data-stu-id="35989-102">How to: Create a Key In the Registry (Visual C#)</span></span>
<span data-ttu-id="35989-103">本範例會將 "Name" 和 "Isabella" 的值組新增至目前使用者之登錄的 "Names" 索引鍵下。</span><span class="sxs-lookup"><span data-stu-id="35989-103">This example adds the value pair, "Name" and "Isabella", to the current user's registry, under the key "Names".</span></span>  
  
## <a name="example"></a><span data-ttu-id="35989-104">範例</span><span class="sxs-lookup"><span data-stu-id="35989-104">Example</span></span>  
  
```  
Microsoft.Win32.RegistryKey key;  
key = Microsoft.Win32.Registry.CurrentUser.CreateSubKey("Names");  
key.SetValue("Name", "Isabella");  
key.Close();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="35989-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="35989-105">Compiling the Code</span></span>  
  
-   <span data-ttu-id="35989-106">將程式碼複製並貼入主控台應用程式的 `Main` 方法中。</span><span class="sxs-lookup"><span data-stu-id="35989-106">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
-   <span data-ttu-id="35989-107">以直接位在登錄的 HKEY_CURRENT_USER 節點下的索引鍵名稱取代 `Names` 參數。</span><span class="sxs-lookup"><span data-stu-id="35989-107">Replace the `Names` parameter with the name of a key that exists directly under the HKEY_CURRENT_USER node of the registry.</span></span>  
  
-   <span data-ttu-id="35989-108">以直接位在 Names 節點下的值名稱取代 `Nam`e 參數。</span><span class="sxs-lookup"><span data-stu-id="35989-108">Replace the `Nam`e parameter with the name of a value that exists directly under the Names node.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="35989-109">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="35989-109">Robust Programming</span></span>  
 <span data-ttu-id="35989-110">檢查登錄結構以找出適合索引鍵的位置。</span><span class="sxs-lookup"><span data-stu-id="35989-110">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="35989-111">例如，您可能想要開啟目前使用者的軟體金鑰，並以貴公司的名稱建立金鑰。</span><span class="sxs-lookup"><span data-stu-id="35989-111">For example, you might want to open the Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="35989-112">請將登錄值新增至貴公司的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="35989-112">Then add the registry values to your company's key.</span></span>  
  
 <span data-ttu-id="35989-113">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="35989-113">The following conditions might cause an exception:</span></span>  
  
-   <span data-ttu-id="35989-114">索引鍵名稱是 Null。</span><span class="sxs-lookup"><span data-stu-id="35989-114">The name of the key is null.</span></span>  
  
-   <span data-ttu-id="35989-115">使用者沒有權限，無法建立登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="35989-115">The user does not have permissions to create registry keys.</span></span>  
  
-   <span data-ttu-id="35989-116">索引鍵名稱超過 255 個字元的限制。</span><span class="sxs-lookup"><span data-stu-id="35989-116">The key name exceeds the 255-character limit.</span></span>  
  
-   <span data-ttu-id="35989-117">機碼已關閉。</span><span class="sxs-lookup"><span data-stu-id="35989-117">The key is closed.</span></span>  
  
-   <span data-ttu-id="35989-118">登錄機碼為唯讀。</span><span class="sxs-lookup"><span data-stu-id="35989-118">The registry key is read-only.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="35989-119">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="35989-119">.NET Framework Security</span></span>  
 <span data-ttu-id="35989-120">將資料寫入使用者資料夾 `Microsoft.Win32.Registry.CurrentUser` 比寫入本機電腦 `Microsoft.Win32.Registry.LocalMachine` 更安全。</span><span class="sxs-lookup"><span data-stu-id="35989-120">It is more secure to write data to the user folder — `Microsoft.Win32.Registry.CurrentUser` — rather than to the local computer — `Microsoft.Win32.Registry.LocalMachine`.</span></span>  
  
 <span data-ttu-id="35989-121">當您建立登錄值時，您需要決定如果該值已經存在該怎麼辦。</span><span class="sxs-lookup"><span data-stu-id="35989-121">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="35989-122">另一個可能是惡意的處理序，可能已建立值並具有其存取權。</span><span class="sxs-lookup"><span data-stu-id="35989-122">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="35989-123">當您將資料放在登錄值中時，資料可供其他處理序使用。</span><span class="sxs-lookup"><span data-stu-id="35989-123">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="35989-124">為避免此問題，請使用 `Overload:Microsoft.Win32.RegistryKey.GetValue`。</span><span class="sxs-lookup"><span data-stu-id="35989-124">To prevent this, use the.`Overload:Microsoft.Win32.RegistryKey.GetValue`</span></span> <span data-ttu-id="35989-125">方法。</span><span class="sxs-lookup"><span data-stu-id="35989-125">method.</span></span> <span data-ttu-id="35989-126">如果沒有索引鍵，則傳回 Null。</span><span class="sxs-lookup"><span data-stu-id="35989-126">It returns null if the key does not already exist.</span></span>  
  
 <span data-ttu-id="35989-127">即使使用存取控制清單 (ACL) 來保護登錄機碼，將密碼等機密資料以純文字儲存在登錄中也不安全。</span><span class="sxs-lookup"><span data-stu-id="35989-127">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by access control lists (ACL).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35989-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35989-128">See Also</span></span>  
 <span data-ttu-id="35989-129"><xref:System.IO?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="35989-129"><xref:System.IO?displayProperty=fullName></span></span>   
<span data-ttu-id="35989-130"> [C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="35989-130"> [C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
<span data-ttu-id="35989-131"> [檔案系統和登錄 (C# 程式設計手冊)](../../../csharp/programming-guide/file-system/index.md) </span><span class="sxs-lookup"><span data-stu-id="35989-131"> [File System and the Registry (C# Programming Guide)](../../../csharp/programming-guide/file-system/index.md) </span></span>  
<span data-ttu-id="35989-132"> [使用 C# 從登錄進行讀取、寫入和刪除](http://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)</span><span class="sxs-lookup"><span data-stu-id="35989-132"> [Read, write and delete from the registry with C#](http://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)</span></span>
