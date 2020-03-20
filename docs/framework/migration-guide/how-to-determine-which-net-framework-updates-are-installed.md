---
title: 請參閱已安裝的 .NET 框架安全更新和修補程式
description: 了解如何判斷電腦上所安裝的 .NET Framework 安全性更新與 Hotfix。
ms.date: 11/27/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- updates, determining for .NET Framework
- .NET Framework, determining updates
ms.assetid: 53c7b5f7-d47a-402a-b194-7244a696a88b
ms.openlocfilehash: 5c7bf48d5786530a9bcb69fb7cf605ac2c80a4eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181274"
---
# <a name="how-to-determine-which-net-framework-security-updates-and-hotfixes-are-installed"></a><span data-ttu-id="aa9b0-103">如何確定哪些 .NET 框架安全更新和修補程式已安裝</span><span class="sxs-lookup"><span data-stu-id="aa9b0-103">How to determine which .NET Framework security updates and hotfixes are installed</span></span>

<span data-ttu-id="aa9b0-104">本文說明如何找出安裝在電腦上的 .NET Framework 安全性更新與 Hotfix。</span><span class="sxs-lookup"><span data-stu-id="aa9b0-104">This article shows you how to find out which .NET Framework security updates and hotfixes are installed on a computer.</span></span>

> [!NOTE]
> <span data-ttu-id="aa9b0-105">本文中展示的所有技術，皆需要使用具備系統管理權限的帳戶。</span><span class="sxs-lookup"><span data-stu-id="aa9b0-105">All the techniques shown in this article require an account with administrative privileges.</span></span>

## <a name="use-registry-editor"></a><span data-ttu-id="aa9b0-106">使用登錄編輯程式</span><span class="sxs-lookup"><span data-stu-id="aa9b0-106">Use Registry Editor</span></span>

<span data-ttu-id="aa9b0-107">已為電腦上安裝之各版 .NET Framework 所安裝之安全性更新與 Hotfix，都列於 Windows 登錄中。</span><span class="sxs-lookup"><span data-stu-id="aa9b0-107">The installed security updates and hotfixes for each version of the .NET Framework installed on a computer are listed in the Windows registry.</span></span> <span data-ttu-id="aa9b0-108">您可使用登錄編輯程式 (*regedit.exe*) 程式，檢視此資訊。</span><span class="sxs-lookup"><span data-stu-id="aa9b0-108">You can use the Registry Editor (*regedit.exe*) program to view this information.</span></span>

1. <span data-ttu-id="aa9b0-109">開啟 **regedit.exe** 程式。</span><span class="sxs-lookup"><span data-stu-id="aa9b0-109">Open the program **regedit.exe**.</span></span> <span data-ttu-id="aa9b0-110">在 Windows 8 和更高版本中，**按右鍵** ![Windows 金鑰徽標的開始螢幕截圖。，](./media/how-to-determine-which-net-framework-updates-are-installed/windows-keyboard-logo.png "視窗鍵盤logo")然後選擇"**運行**"。</span><span class="sxs-lookup"><span data-stu-id="aa9b0-110">In Windows 8 and later versions, right-click **Start** ![Screenshot of the Windows key logo.](./media/how-to-determine-which-net-framework-updates-are-installed/windows-keyboard-logo.png "Windowskeyboardlogo"), then select **Run**.</span></span> <span data-ttu-id="aa9b0-111">在 [開啟]\*\*\*\* 方塊中，輸入 **regedit**，然後選取 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="aa9b0-111">In the **Open** box, enter **regedit** and select **OK**.</span></span>

2. <span data-ttu-id="aa9b0-112">在 [登錄編輯程式] 中，開啟下列子機碼：</span><span class="sxs-lookup"><span data-stu-id="aa9b0-112">In the Registry Editor, open the following subkey:</span></span>

     <span data-ttu-id="aa9b0-113">**HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates**</span><span class="sxs-lookup"><span data-stu-id="aa9b0-113">**HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates**</span></span>

     <span data-ttu-id="aa9b0-114">已安裝的更新會列於子機碼下，這些子機碼可識別套用更新的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="aa9b0-114">The installed updates are listed under subkeys that identify the .NET Framework version they apply to.</span></span> <span data-ttu-id="aa9b0-115">每個更新都是透過知識庫 (KB) 號碼加以識別。</span><span class="sxs-lookup"><span data-stu-id="aa9b0-115">Each update is identified by a Knowledge Base (KB) number.</span></span>

<span data-ttu-id="aa9b0-116">在登錄編輯程式中，.NET Framework 版本和每一版已安裝的更新會儲存在不同的子機碼中。</span><span class="sxs-lookup"><span data-stu-id="aa9b0-116">In the Registry Editor, the .NET Framework versions and installed updates for each version are stored in different subkeys.</span></span> <span data-ttu-id="aa9b0-117">如需偵測已安裝之版本號碼的相關資訊，請參閱[如何：判斷安裝的 .NET Framework 版本](how-to-determine-which-versions-are-installed.md)。</span><span class="sxs-lookup"><span data-stu-id="aa9b0-117">For information about detecting the installed version numbers, see [How to: Determine which .NET Framework versions are installed](how-to-determine-which-versions-are-installed.md).</span></span>

## <a name="query-the-registry-using-code"></a><span data-ttu-id="aa9b0-118">使用代碼查詢註冊表</span><span class="sxs-lookup"><span data-stu-id="aa9b0-118">Query the registry using code</span></span>

<span data-ttu-id="aa9b0-119">下列範例以程式設計方式判斷電腦上安裝的 .NET Framework 安全性更新與 Hotfix：</span><span class="sxs-lookup"><span data-stu-id="aa9b0-119">The following example programmatically determines the .NET Framework security updates and hotfixes that are installed on a computer:</span></span>

[!code-csharp[ListUpdates](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs)]
[!code-vb[ListUpdates](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb)]

<span data-ttu-id="aa9b0-120">該範例會產生類似如下的輸出：</span><span class="sxs-lookup"><span data-stu-id="aa9b0-120">The example produces an output that's similar to the following one:</span></span>

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

## <a name="use-powershell-to-query-the-registry"></a><span data-ttu-id="aa9b0-121">使用 PowerShell 查詢註冊表</span><span class="sxs-lookup"><span data-stu-id="aa9b0-121">Use PowerShell to query the registry</span></span>

<span data-ttu-id="aa9b0-122">下列範例示範如何使用 PowerShell 判斷電腦上安裝的 .NET Framework 安全性更新與 Hotfix：</span><span class="sxs-lookup"><span data-stu-id="aa9b0-122">The following example shows how to determine the .NET Framework security updates and hotfixes that are installed on a computer using PowerShell:</span></span>

```powershell
$DotNetVersions = Get-ChildItem HKLM:\SOFTWARE\WOW6432Node\Microsoft\Updates | Where-Object {$_.name -like
 "*.NET Framework*"}

ForEach($Version in $DotNetVersions){

   $Updates = Get-ChildItem $Version.PSPath
    $Version.PSChildName
    ForEach ($Update in $Updates){
       $Update.PSChildName
       }
}
```

<span data-ttu-id="aa9b0-123">該範例會產生類似如下的輸出：</span><span class="sxs-lookup"><span data-stu-id="aa9b0-123">The example produces an output that's similar to the following one:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="aa9b0-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aa9b0-124">See also</span></span>

- [<span data-ttu-id="aa9b0-125">如何：確定安裝了哪些 .NET 框架版本</span><span class="sxs-lookup"><span data-stu-id="aa9b0-125">How to: Determine which .NET Framework versions are installed</span></span>](how-to-determine-which-versions-are-installed.md)
- [<span data-ttu-id="aa9b0-126">安裝適用於開發人員的 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="aa9b0-126">Install the .NET Framework for developers</span></span>](../install/guide-for-developers.md)
- [<span data-ttu-id="aa9b0-127">版本和相依性</span><span class="sxs-lookup"><span data-stu-id="aa9b0-127">Versions and dependencies</span></span>](versions-and-dependencies.md)
