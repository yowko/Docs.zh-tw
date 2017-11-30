---
title: "如何： 判斷已安裝哪些.NET Framework 安全性更新和 hotfix"
description: "了解如何判斷電腦上已安裝哪些.NET Framework 安全性更新和 hotfix。"
ms.date: 11/21/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- updates, determining for .NET Framework
- .NET Framework, determining updates
ms.assetid: 53c7b5f7-d47a-402a-b194-7244a696a88b
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c35705470a8e1b553eca2ca0c68d3b8b9b3f6fa6
ms.sourcegitcommit: a3ba258f7a8cab5c6d19a3743dd95e904ecebc44
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/27/2017
---
# <a name="how-to-determine-which-net-framework-security-updates-and-hotfixes-are-installed"></a><span data-ttu-id="8d11d-103">如何： 判斷已安裝哪些.NET Framework 安全性更新和 hotfix</span><span class="sxs-lookup"><span data-stu-id="8d11d-103">How to: Determine which .NET Framework security updates and hotfixes are installed</span></span>

<span data-ttu-id="8d11d-104">本文將說明如何找出哪些.NET Framework 安全性更新，並在電腦上已安裝 hotfix。</span><span class="sxs-lookup"><span data-stu-id="8d11d-104">This article shows you how to find out which .NET Framework security updates and hotfixes are installed on a computer.</span></span>

> [!NOTE]
> <span data-ttu-id="8d11d-105">本文中所顯示的所有技術都需要具有系統管理權限的帳戶。</span><span class="sxs-lookup"><span data-stu-id="8d11d-105">All the techniques shown in this article require an account with administrative privileges.</span></span>

## <a name="to-find-installed-updates-using-the-registry"></a><span data-ttu-id="8d11d-106">尋找已安裝的更新登錄</span><span class="sxs-lookup"><span data-stu-id="8d11d-106">To find installed updates using the registry</span></span>

<span data-ttu-id="8d11d-107">Windows 登錄中列出的已安裝的安全性更新和 hotfix 的電腦上安裝的.NET Framework 的每個版本。</span><span class="sxs-lookup"><span data-stu-id="8d11d-107">The installed security updates and hotfixes for each version of the .NET Framework installed on a computer are listed in the Windows registry.</span></span> <span data-ttu-id="8d11d-108">您可以使用登錄編輯程式 (*regedit.exe*) 若要檢視這項資訊的程式。</span><span class="sxs-lookup"><span data-stu-id="8d11d-108">You can use the Registry Editor (*regedit.exe*) program to view this information.</span></span>

1. <span data-ttu-id="8d11d-109">開啟 **regedit.exe** 程式。</span><span class="sxs-lookup"><span data-stu-id="8d11d-109">Open the program **regedit.exe**.</span></span> <span data-ttu-id="8d11d-110">在 Windows 8 和更新版本中，以滑鼠右鍵按一下**啟動** ![Windows 標誌](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo")，然後選取**執行**。</span><span class="sxs-lookup"><span data-stu-id="8d11d-110">In Windows 8 and later versions, right-click **Start** ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo"), then select **Run**.</span></span> <span data-ttu-id="8d11d-111">在**開啟**方塊中，輸入**regedit**選取**確定**。</span><span class="sxs-lookup"><span data-stu-id="8d11d-111">In the **Open** box, enter **regedit** and select **OK**.</span></span>

2. <span data-ttu-id="8d11d-112">在 [登錄編輯程式] 中，開啟下列子機碼：</span><span class="sxs-lookup"><span data-stu-id="8d11d-112">In the Registry Editor, open the following subkey:</span></span>

     `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates`

     <span data-ttu-id="8d11d-113">已安裝的更新會列於子機碼下，這些子機碼可識別套用更新的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="8d11d-113">The installed updates are listed under subkeys that identify the .NET Framework version they apply to.</span></span> <span data-ttu-id="8d11d-114">每個更新都是透過知識庫 (KB) 號碼加以識別。</span><span class="sxs-lookup"><span data-stu-id="8d11d-114">Each update is identified by a Knowledge Base (KB) number.</span></span>

<span data-ttu-id="8d11d-115">在登錄編輯程式中，.NET Framework 版本和每一版已安裝的更新會儲存在不同的子機碼中。</span><span class="sxs-lookup"><span data-stu-id="8d11d-115">In the Registry Editor, the .NET Framework versions and installed updates for each version are stored in different subkeys.</span></span> <span data-ttu-id="8d11d-116">如需偵測已安裝的版本號碼相關的資訊，請參閱[How to： 判斷已安裝哪些.NET Framework 版本](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)。</span><span class="sxs-lookup"><span data-stu-id="8d11d-116">For information about detecting the installed version numbers, see [How to: Determine which .NET Framework versions are installed](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span></span>

## <a name="to-find-installed-updates-by-querying-the-registry-in-code"></a><span data-ttu-id="8d11d-117">若要尋找安裝的更新藉由查詢程式碼中登錄</span><span class="sxs-lookup"><span data-stu-id="8d11d-117">To find installed updates by querying the registry in code</span></span>

<span data-ttu-id="8d11d-118">下列範例以程式設計方式判斷.NET Framework 安全性更新和 hotfix 安裝在電腦上：</span><span class="sxs-lookup"><span data-stu-id="8d11d-118">The following example programmatically determines the .NET Framework security updates and hotfixes that are installed on a computer:</span></span>

[!code-csharp[ListUpdates](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs)]
[!code-vb[ListUpdates](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb)]

<span data-ttu-id="8d11d-119">這個範例會產生類似下列的輸出：</span><span class="sxs-lookup"><span data-stu-id="8d11d-119">The example produces an output that's similar to the following one:</span></span>

```console
Microsoft .NET Framework 4 Client Profile
  KB2468871
  KB2468871v2
  KB2478063
  KB2533523
  KB2544514
  KB2600211
  KB2600217
Microsoft .NET Framework 4 Extended
  KB2468871
  KB2468871v2
  KB2478063
  KB2533523
  KB2544514
  KB2600211
  KB2600217
```

## <a name="to-find-installed-updates-by-querying-the-registry-in-powershell"></a><span data-ttu-id="8d11d-120">若要尋找安裝的更新藉由查詢在 PowerShell 中登錄</span><span class="sxs-lookup"><span data-stu-id="8d11d-120">To find installed updates by querying the registry in PowerShell</span></span>

<span data-ttu-id="8d11d-121">下列範例會示範如何判斷.NET Framework 安全性更新和 hotfix 安裝在電腦上使用 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="8d11d-121">The following example shows how to determine the .NET Framework security updates and hotfixes that are installed on a computer using PowerShell:</span></span>

```powershell
 Get-ChildItem "HKLM:SOFTWARE\Wow6432Node\Microsoft\Updates\*" -Recurse | Where-Object {$_.name -like
 "*.NET Framework*"}
```

<span data-ttu-id="8d11d-122">這個範例會產生類似下列的輸出：</span><span class="sxs-lookup"><span data-stu-id="8d11d-122">The example produces an output that's similar to the following one:</span></span>

```console
    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates\Microsoft .NET Framework 4 Client Profile


Name                           Property
----                           --------
KB2468871                      ThisVersionInstalled : Y
KB2468871v2                    ThisVersionInstalled : Y
KB2478063                      ThisVersionInstalled : Y
KB2533523                      ThisVersionInstalled : Y
KB2544514                      ThisVersionInstalled : Y
KB2600211                      ThisVersionInstalled : Y
KB2600217                      ThisVersionInstalled : Y


    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates\Microsoft .NET Framework 4 Extended


Name                           Property
----                           --------
KB2468871                      ThisVersionInstalled : Y
KB2468871v2                    ThisVersionInstalled : Y
KB2478063                      ThisVersionInstalled : Y
KB2533523                      ThisVersionInstalled : Y
KB2544514                      ThisVersionInstalled : Y
KB2600211                      ThisVersionInstalled : Y
KB2600217                      ThisVersionInstalled : Y
```

## <a name="see-also"></a><span data-ttu-id="8d11d-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="8d11d-123">See also</span></span>

[<span data-ttu-id="8d11d-124">如何： 判斷已安裝哪些.NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="8d11d-124">How to: Determine which .NET Framework versions are installed</span></span>](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)  
[<span data-ttu-id="8d11d-125">安裝.NET Framework 開發人員</span><span class="sxs-lookup"><span data-stu-id="8d11d-125">Install the .NET Framework for developers</span></span>](../../../docs/framework/install/guide-for-developers.md)  
[<span data-ttu-id="8d11d-126">版本和相依性</span><span class="sxs-lookup"><span data-stu-id="8d11d-126">Versions and dependencies</span></span>](../../../docs/framework/migration-guide/versions-and-dependencies.md)
