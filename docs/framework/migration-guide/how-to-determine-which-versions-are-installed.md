---
title: 判斷安裝的 .NET Framework 版本
description: 使用代碼、regedit.exe 或 PowerShell 通過查詢 Windows 註冊表來檢測電腦上安裝的 .NET Framework 的哪些版本。
ms.date: 02/03/2020
dev_langs:
- csharp
- vb
ms.custom: updateeachrelease
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
ms.openlocfilehash: 8469f977c6ed9691c81a2a8354935557b5c27171
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "77093823"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="806b3-103">如何：判斷安裝的 .NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="806b3-103">How to: Determine which .NET Framework versions are installed</span></span>

<span data-ttu-id="806b3-104">使用者可以在其電腦上[安裝](../install/index.md)和運行多個版本的 .NET 框架。</span><span class="sxs-lookup"><span data-stu-id="806b3-104">Users can [install](../install/index.md) and run multiple versions of the .NET Framework on their computers.</span></span> <span data-ttu-id="806b3-105">當您開發或部署應用程式時，您可能需要知道使用者電腦上安裝的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="806b3-105">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user’s computer.</span></span> <span data-ttu-id="806b3-106">註冊表包含電腦上安裝的 .NET 框架版本的清單。</span><span class="sxs-lookup"><span data-stu-id="806b3-106">The registry contains a list of the .NET Framework versions installed on a computer.</span></span>

<span data-ttu-id="806b3-107">.NET Framework 包含兩個主要元件，各有各的版本控制：</span><span class="sxs-lookup"><span data-stu-id="806b3-107">The .NET Framework consists of two main components, which are versioned separately:</span></span>

- <span data-ttu-id="806b3-108">組件集合，這是為應用程式提供功能的類型與資源集合。</span><span class="sxs-lookup"><span data-stu-id="806b3-108">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="806b3-109">.NET Framework 和組件會共用相同的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="806b3-109">The .NET Framework and assemblies share the same version number.</span></span> <span data-ttu-id="806b3-110">例如，.NET Framework 版本包含 4.5、4.6.1 和 4.7.2。</span><span class="sxs-lookup"><span data-stu-id="806b3-110">For example, .NET Framework versions include 4.5, 4.6.1, and 4.7.2.</span></span>

- <span data-ttu-id="806b3-111">通用語言執行平台 (CLR)，負責管理和執行應用程式的程式碼。</span><span class="sxs-lookup"><span data-stu-id="806b3-111">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="806b3-112">單一的 CLR 版本通常會支援多個 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="806b3-112">A single CLR version typically supports multiple .NET Framework versions.</span></span> <span data-ttu-id="806b3-113">例如，CLR 版本 4.0.30319。*xxxxx* *xxxxxxxxxx*的 xxxxx 小於 42000，支援 .NET 框架版本 4 到 4.5.2。</span><span class="sxs-lookup"><span data-stu-id="806b3-113">For example, CLR version 4.0.30319.*xxxxx* where *xxxxx* is less than 42000, supports .NET Framework versions 4 through 4.5.2.</span></span> <span data-ttu-id="806b3-114">CLR 版本大於或等於 4.0.30319.42000 支援 .NET 框架版本，以 .NET 框架 4.6 開頭。</span><span class="sxs-lookup"><span data-stu-id="806b3-114">CLR version greater than or equal to 4.0.30319.42000 supports .NET Framework versions starting with .NET Framework 4.6.</span></span>

<span data-ttu-id="806b3-115">社區維護的工具可説明檢測安裝了哪些 .NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="806b3-115">Community-maintained tools are available to help detect which .NET Framework versions are installed:</span></span>

- [https://github.com/jmalarcon/DotNetVersions](https://github.com/jmalarcon/DotNetVersions)

  <span data-ttu-id="806b3-116">.NET 2.0 命令列工具。</span><span class="sxs-lookup"><span data-stu-id="806b3-116">A .NET 2.0 command-line tool.</span></span>

- [https://github.com/EliteLoser/DotNetVersionLister](https://github.com/EliteLoser/DotNetVersionLister)

  <span data-ttu-id="806b3-117">PowerShell 2.0 模組。</span><span class="sxs-lookup"><span data-stu-id="806b3-117">A PowerShell 2.0 module.</span></span>

<span data-ttu-id="806b3-118">有關檢測每個版本的 .NET Framework 的已安裝更新的資訊，請參閱[如何：確定安裝了哪些 .NET 框架更新](how-to-determine-which-net-framework-updates-are-installed.md)。</span><span class="sxs-lookup"><span data-stu-id="806b3-118">For information about detecting the installed updates for each version of the .NET Framework, see [How to: Determine which .NET Framework updates are installed](how-to-determine-which-net-framework-updates-are-installed.md).</span></span>

## <a name="detect-net-framework-45-and-later-versions"></a><span data-ttu-id="806b3-119">檢測 .NET 框架 4.5 和更高版本</span><span class="sxs-lookup"><span data-stu-id="806b3-119">Detect .NET Framework 4.5 and later versions</span></span>

<span data-ttu-id="806b3-120">安裝在電腦上的 .NET 框架（4.5 及更高版本）的版本列在**註冊表中，HKEY_LOCAL_MACHINE\\\\軟體 Microsoft\\NET\\框架\\設置\\NDP v4 完整**。</span><span class="sxs-lookup"><span data-stu-id="806b3-120">The version of .NET Framework (4.5 and later) installed on a machine is listed in the registry at **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span></span> <span data-ttu-id="806b3-121">如果缺少**完整**子鍵，則未安裝 .NET 框架 4.5 或以上。</span><span class="sxs-lookup"><span data-stu-id="806b3-121">If the **Full** subkey is missing, then .NET Framework 4.5 or above isn't installed.</span></span>

> [!NOTE]
> <span data-ttu-id="806b3-122">註冊表路徑中的**NET 框架設置**子鍵*不*以句點開頭。</span><span class="sxs-lookup"><span data-stu-id="806b3-122">The **NET Framework Setup** subkey in the registry path does *not* begin with a period.</span></span>

<span data-ttu-id="806b3-123">**註冊表中的"版本**REG_DWORD"值表示已安裝的 .NET 框架的版本。</span><span class="sxs-lookup"><span data-stu-id="806b3-123">The **Release** REG_DWORD value in the registry represents the version of .NET Framework installed.</span></span>

<a name="version_table"></a>

| <span data-ttu-id="806b3-124">.NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="806b3-124">.NET Framework version</span></span> | <span data-ttu-id="806b3-125">**釋放**價值</span><span class="sxs-lookup"><span data-stu-id="806b3-125">Value of **Release**</span></span> |
| ---------------------- | -------------------------- |
| <span data-ttu-id="806b3-126">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="806b3-126">.NET Framework 4.5</span></span>     | <span data-ttu-id="806b3-127">所有 Windows 作業系統： 378389</span><span class="sxs-lookup"><span data-stu-id="806b3-127">All Windows operating systems: 378389</span></span> |
| <span data-ttu-id="806b3-128">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="806b3-128">.NET Framework 4.5.1</span></span>   | <span data-ttu-id="806b3-129">在 Windows 8.1 和 Windows 伺服器 2012 R2： 378675</span><span class="sxs-lookup"><span data-stu-id="806b3-129">On Windows 8.1 and Windows Server 2012 R2: 378675</span></span><br /><span data-ttu-id="806b3-130">在所有其他 Windows 作業系統上： 378758</span><span class="sxs-lookup"><span data-stu-id="806b3-130">On all other Windows operating systems: 378758</span></span> |
| <span data-ttu-id="806b3-131">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="806b3-131">.NET Framework 4.5.2</span></span>   | <span data-ttu-id="806b3-132">所有 Windows 作業系統： 379893</span><span class="sxs-lookup"><span data-stu-id="806b3-132">All Windows operating systems: 379893</span></span> |
| <span data-ttu-id="806b3-133">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="806b3-133">.NET Framework 4.6</span></span>     | <span data-ttu-id="806b3-134">在 Windows 10 上： 393295</span><span class="sxs-lookup"><span data-stu-id="806b3-134">On Windows 10: 393295</span></span><br /><span data-ttu-id="806b3-135">在所有其他 Windows 作業系統上： 393297</span><span class="sxs-lookup"><span data-stu-id="806b3-135">On all other Windows operating systems: 393297</span></span> |
| <span data-ttu-id="806b3-136">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="806b3-136">.NET Framework 4.6.1</span></span>   | <span data-ttu-id="806b3-137">Windows 10 11 月更新系統：394254</span><span class="sxs-lookup"><span data-stu-id="806b3-137">On Windows 10 November Update systems: 394254</span></span><br /><span data-ttu-id="806b3-138">在所有其他 Windows 作業系統（包括 Windows 10）：394271</span><span class="sxs-lookup"><span data-stu-id="806b3-138">On all other Windows operating systems (including Windows 10): 394271</span></span> |
| <span data-ttu-id="806b3-139">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="806b3-139">.NET Framework 4.6.2</span></span>   | <span data-ttu-id="806b3-140">Windows 10 年度更新版及 Windows Server 2016：394802</span><span class="sxs-lookup"><span data-stu-id="806b3-140">On Windows 10 Anniversary Update and Windows Server 2016: 394802</span></span><br /><span data-ttu-id="806b3-141">在所有其他 Windows 作業系統（包括其他 Windows 10 作業系統）：394806</span><span class="sxs-lookup"><span data-stu-id="806b3-141">On all other Windows operating systems (including other Windows 10 operating systems): 394806</span></span> |
| <span data-ttu-id="806b3-142">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="806b3-142">.NET Framework 4.7</span></span>     | <span data-ttu-id="806b3-143">Windows 10 Creators Update：460798</span><span class="sxs-lookup"><span data-stu-id="806b3-143">On Windows 10 Creators Update: 460798</span></span><br /><span data-ttu-id="806b3-144">在所有其他 Windows 作業系統（包括其他 Windows 10 作業系統）：460805</span><span class="sxs-lookup"><span data-stu-id="806b3-144">On all other Windows operating systems (including other Windows 10 operating systems): 460805</span></span> |
| <span data-ttu-id="806b3-145">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="806b3-145">.NET Framework 4.7.1</span></span>   | <span data-ttu-id="806b3-146">在 Windows 10 秋季建立者更新和 Windows 伺服器上，版本 1709： 461308</span><span class="sxs-lookup"><span data-stu-id="806b3-146">On Windows 10 Fall Creators Update and Windows Server, version 1709: 461308</span></span><br/><span data-ttu-id="806b3-147">在所有其他 Windows 作業系統（包括其他 Windows 10 作業系統）：461310</span><span class="sxs-lookup"><span data-stu-id="806b3-147">On all other Windows operating systems (including other Windows 10 operating systems): 461310</span></span> |
| <span data-ttu-id="806b3-148">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="806b3-148">.NET Framework 4.7.2</span></span>   | <span data-ttu-id="806b3-149">在 Windows 10 四月 2018 更新和 Windows 伺服器， 版本 1803： 461808</span><span class="sxs-lookup"><span data-stu-id="806b3-149">On Windows 10 April 2018 Update and Windows Server, version 1803: 461808</span></span><br/><span data-ttu-id="806b3-150">在 Windows 10 2018 更新和 Windows 伺服器以外的所有 Windows 作業系統上，版本 1803： 461814</span><span class="sxs-lookup"><span data-stu-id="806b3-150">On all Windows operating systems other than Windows 10 April 2018 Update and Windows Server, version 1803: 461814</span></span> |
| <span data-ttu-id="806b3-151">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="806b3-151">.NET Framework 4.8</span></span>     | <span data-ttu-id="806b3-152">在 Windows 10 五月 2019 更新和 Windows 10 十一月 2019 更新： 528040</span><span class="sxs-lookup"><span data-stu-id="806b3-152">On Windows 10 May 2019 Update and Windows 10 November 2019 Update: 528040</span></span><br/><span data-ttu-id="806b3-153">在 Windows 10 和 Windows 伺服器上，版本 1909： 528209</span><span class="sxs-lookup"><span data-stu-id="806b3-153">On Windows 10 and Windows Server, version 1909: 528209</span></span><br/><span data-ttu-id="806b3-154">在所有其他 Windows 作業系統（包括其他 Windows 10 作業系統）：528049</span><span class="sxs-lookup"><span data-stu-id="806b3-154">On all other Windows operating systems (including other Windows 10 operating systems): 528049</span></span> |

### <a name="minimum-version"></a><span data-ttu-id="806b3-155">最小版本</span><span class="sxs-lookup"><span data-stu-id="806b3-155">Minimum version</span></span>

<span data-ttu-id="806b3-156">要確定是否存在 .NET 框架*的最小*版本，請使用上表中該版本的最小**版本**REG_DWORD值。</span><span class="sxs-lookup"><span data-stu-id="806b3-156">To determine whether a *minimum* version of the .NET Framework is present, use the smallest **Release** REG_DWORD value for that version from the previous table.</span></span>

<span data-ttu-id="806b3-157">例如，如果應用程式在 .NET Framework 4.8 或更高版本下運行，則測試**版本**REG_DWORD*值大於或等於*528040。</span><span class="sxs-lookup"><span data-stu-id="806b3-157">For example, if your application runs under .NET Framework 4.8 or a later version, test for a **Release** REG_DWORD value that is *greater than or equal to* 528040.</span></span>

| <span data-ttu-id="806b3-158">.NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="806b3-158">.NET Framework version</span></span> | <span data-ttu-id="806b3-159">最小值</span><span class="sxs-lookup"><span data-stu-id="806b3-159">Minimum value</span></span> |
| ---------------------- | ------------- |
| <span data-ttu-id="806b3-160">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="806b3-160">.NET Framework 4.5</span></span>     | <span data-ttu-id="806b3-161">378389</span><span class="sxs-lookup"><span data-stu-id="806b3-161">378389</span></span> |
| <span data-ttu-id="806b3-162">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="806b3-162">.NET Framework 4.5.1</span></span>   | <span data-ttu-id="806b3-163">378675</span><span class="sxs-lookup"><span data-stu-id="806b3-163">378675</span></span> |
| <span data-ttu-id="806b3-164">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="806b3-164">.NET Framework 4.5.2</span></span>   | <span data-ttu-id="806b3-165">379893</span><span class="sxs-lookup"><span data-stu-id="806b3-165">379893</span></span> |
| <span data-ttu-id="806b3-166">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="806b3-166">.NET Framework 4.6</span></span>     | <span data-ttu-id="806b3-167">393295</span><span class="sxs-lookup"><span data-stu-id="806b3-167">393295</span></span> |
| <span data-ttu-id="806b3-168">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="806b3-168">.NET Framework 4.6.1</span></span>   | <span data-ttu-id="806b3-169">394254</span><span class="sxs-lookup"><span data-stu-id="806b3-169">394254</span></span> |
| <span data-ttu-id="806b3-170">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="806b3-170">.NET Framework 4.6.2</span></span>   | <span data-ttu-id="806b3-171">394802</span><span class="sxs-lookup"><span data-stu-id="806b3-171">394802</span></span> |
| <span data-ttu-id="806b3-172">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="806b3-172">.NET Framework 4.7</span></span>     | <span data-ttu-id="806b3-173">460798</span><span class="sxs-lookup"><span data-stu-id="806b3-173">460798</span></span> |
| <span data-ttu-id="806b3-174">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="806b3-174">.NET Framework 4.7.1</span></span>   | <span data-ttu-id="806b3-175">461308</span><span class="sxs-lookup"><span data-stu-id="806b3-175">461308</span></span> |
| <span data-ttu-id="806b3-176">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="806b3-176">.NET Framework 4.7.2</span></span>   | <span data-ttu-id="806b3-177">461808</span><span class="sxs-lookup"><span data-stu-id="806b3-177">461808</span></span> |
| <span data-ttu-id="806b3-178">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="806b3-178">.NET Framework 4.8</span></span>     | <span data-ttu-id="806b3-179">528040</span><span class="sxs-lookup"><span data-stu-id="806b3-179">528040</span></span> |

### <a name="use-registry-editor"></a><span data-ttu-id="806b3-180">使用登錄編輯程式</span><span class="sxs-lookup"><span data-stu-id="806b3-180">Use Registry Editor</span></span>

01. <span data-ttu-id="806b3-181">從 [開始]\*\*\*\* 功能表上，選擇 [執行]\*\*\*\*，輸入 *regedit*，然後選取 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="806b3-181">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

    <span data-ttu-id="806b3-182">您必須具有系統管理認證才能執行 regedit。</span><span class="sxs-lookup"><span data-stu-id="806b3-182">You must have administrative credentials to run regedit.</span></span>

01. <span data-ttu-id="806b3-183">在登錄編輯程式中，打開以下子鍵 **：HKEY_LOCAL_MACHINE\\軟體微軟\\\\NET 框架\\設置\\NDP\\v4 完整**。</span><span class="sxs-lookup"><span data-stu-id="806b3-183">In the Registry Editor, open the following subkey: **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span></span> <span data-ttu-id="806b3-184">如果 **Full** 子機碼不存在，即表示未安裝 .NET Framework 4.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="806b3-184">If the **Full** subkey isn't present, then you don't have the .NET Framework 4.5 or later installed.</span></span>

01. <span data-ttu-id="806b3-185">檢查名為 **"版本**"的REG_DWORD條目。</span><span class="sxs-lookup"><span data-stu-id="806b3-185">Check for a REG_DWORD entry named **Release**.</span></span> <span data-ttu-id="806b3-186">如果存在，則已安裝 .NET 框架 4.5 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="806b3-186">If it exists, then you have .NET Framework 4.5 or later installed.</span></span> <span data-ttu-id="806b3-187">其值對應于 .NET 框架的特定版本。</span><span class="sxs-lookup"><span data-stu-id="806b3-187">Its value corresponds to a particular version of the .NET Framework.</span></span> <span data-ttu-id="806b3-188">例如，在下圖中，**發佈**條目的值為 528040，這是 .NET Framework 4.8 的發佈鍵。</span><span class="sxs-lookup"><span data-stu-id="806b3-188">In the following figure, for example, the value of the **Release** entry is 528040, which is the release key for .NET Framework 4.8.</span></span>

    <span data-ttu-id="806b3-189">![.NET 框架 4.5 的登錄機碼](./media/clr-installdir.png ".NET 框架 4.5 的登錄機碼")</span><span class="sxs-lookup"><span data-stu-id="806b3-189">![Registry entry for the .NET Framework 4.5](./media/clr-installdir.png "Registry entry for the .NET Framework 4.5")</span></span>

### <a name="use-powershell-to-check-for-a-minimum-version"></a><span data-ttu-id="806b3-190">使用 PowerShell 檢查最小版本</span><span class="sxs-lookup"><span data-stu-id="806b3-190">Use PowerShell to check for a minimum version</span></span>

<span data-ttu-id="806b3-191">使用 PowerShell 命令檢查**\\HKEY_LOCAL_MACHINE軟體 Microsoft\\\\NET 框架設置\\NDP\\v4\\完整**子鍵的**發佈**條目的值。</span><span class="sxs-lookup"><span data-stu-id="806b3-191">Use PowerShell commands to check the value of the **Release** entry of the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** subkey.</span></span>

<span data-ttu-id="806b3-192">下列範例會檢查 **Release** 項目值，以判斷是否安裝了 .NET Framework 4.6.2 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="806b3-192">The following examples check the value of the **Release** entry to determine whether the .NET Framework 4.6.2 or later is installed.</span></span> <span data-ttu-id="806b3-193">如已安裝，則此程式碼會傳回 `True`；否則傳回 `False`。</span><span class="sxs-lookup"><span data-stu-id="806b3-193">This code returns `True` if it's installed and `False` otherwise.</span></span>

```PowerShell
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

### <a name="query-the-registry-using-code"></a><span data-ttu-id="806b3-194">使用代碼查詢註冊表</span><span class="sxs-lookup"><span data-stu-id="806b3-194">Query the registry using code</span></span>

01. <span data-ttu-id="806b3-195">使用<xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType>和<xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType>方法訪問**windows\\\\註冊表\\中HKEY_LOCAL_MACHINE軟體\\\\Microsoft\\NET 框架設置 NDP v4 完全**子鍵。</span><span class="sxs-lookup"><span data-stu-id="806b3-195">Use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> methods to access the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** subkey in the Windows registry.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="806b3-196">如果您正在運行的應用為 32 位並在 64 位 Windows 中運行，則註冊表路徑將不同于之前列出的。</span><span class="sxs-lookup"><span data-stu-id="806b3-196">If the app you're running is 32-bit and running in 64-bit Windows, the registry paths will be different than previously listed.</span></span> <span data-ttu-id="806b3-197">64 位註冊表在**HKEY_LOCAL_MACHINE\\軟體\\Wow6432Node\\**子鍵中可用。</span><span class="sxs-lookup"><span data-stu-id="806b3-197">The 64-bit registry is available in the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** subkey.</span></span> <span data-ttu-id="806b3-198">例如，.NET 框架 4.5 的註冊表子項**HKEY_LOCAL_MACHINE\\軟體\\\\Wow6432Node\\微軟\\NET\\框架\\設置 NDP v4 完整**。</span><span class="sxs-lookup"><span data-stu-id="806b3-198">For example, the registry subkey for .NET Framework 4.5 is **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span></span>

01. <span data-ttu-id="806b3-199">檢查 **"發佈**REG_DWORD"值以確定已安裝的版本。</span><span class="sxs-lookup"><span data-stu-id="806b3-199">Check the **Release** REG_DWORD value to determine the installed version.</span></span> <span data-ttu-id="806b3-200">若要正向相容，請檢查是否有大於或等於 [.NET Framework 版本表](#version_table)中所列值的值。</span><span class="sxs-lookup"><span data-stu-id="806b3-200">To be forward-compatible, check for a value greater than or equal to the value listed in the [.NET Framework version table](#version_table).</span></span>

<span data-ttu-id="806b3-201">下列範例會檢查登錄中的 **Release** 項目值，尋找已安裝的 .NET Framework 4.5 和更新版本：</span><span class="sxs-lookup"><span data-stu-id="806b3-201">The following example checks the value of the **Release** entry in the registry to find the .NET Framework 4.5 and later versions that are installed:</span></span>

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

<span data-ttu-id="806b3-202">此範例遵循版本檢查的建議做法：</span><span class="sxs-lookup"><span data-stu-id="806b3-202">This example follows the recommended practice for version checking:</span></span>

- <span data-ttu-id="806b3-203">它會檢查 **Release** 項目值是否「大於或等於」\*\* 已知版本機碼的值。</span><span class="sxs-lookup"><span data-stu-id="806b3-203">It checks whether the value of the **Release** entry is *greater than or equal to* the value of the known release keys.</span></span>
- <span data-ttu-id="806b3-204">它會從最新版本依序檢查到最舊版本。</span><span class="sxs-lookup"><span data-stu-id="806b3-204">It checks in order from most recent version to earliest version.</span></span>

## <a name="detect-net-framework-10-through-40"></a><span data-ttu-id="806b3-205">檢測 .NET 框架 1.0 到 4.0</span><span class="sxs-lookup"><span data-stu-id="806b3-205">Detect .NET Framework 1.0 through 4.0</span></span>

<span data-ttu-id="806b3-206">每個版本的 .NET 框架從 1.1 到 4.0 被列為子**鍵\\在\\\\HKEY_LOCAL_MACHINE軟體微軟\\NET 框架設置 NDP**.</span><span class="sxs-lookup"><span data-stu-id="806b3-206">Each version of .NET Framework from 1.1 to 4.0 is listed as a subkey at **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP**.</span></span> <span data-ttu-id="806b3-207">下表列出了每個 .NET 框架版本的路徑。</span><span class="sxs-lookup"><span data-stu-id="806b3-207">The following table lists the path to each .NET Framework version.</span></span> <span data-ttu-id="806b3-208">對於大多數版本，有一個**安裝**REG_DWORD值`1`，以指示已安裝此版本。</span><span class="sxs-lookup"><span data-stu-id="806b3-208">For most versions, there's a **Install** REG_DWORD value of `1` to indicate this version is installed.</span></span> <span data-ttu-id="806b3-209">在這些子鍵中，還有一個包含版本字串**的版本**REG_SZ值。</span><span class="sxs-lookup"><span data-stu-id="806b3-209">In these subkeys, there's also a **Version** REG_SZ value that contains a version string.</span></span>

> [!NOTE]
> <span data-ttu-id="806b3-210">註冊表路徑中的**NET 框架設置**子鍵*不*以句點開頭。</span><span class="sxs-lookup"><span data-stu-id="806b3-210">The **NET Framework Setup** subkey in the registry path does *not* begin with a period.</span></span>

| <span data-ttu-id="806b3-211">框架版本</span><span class="sxs-lookup"><span data-stu-id="806b3-211">Framework Version</span></span>  | <span data-ttu-id="806b3-212">註冊表子鍵</span><span class="sxs-lookup"><span data-stu-id="806b3-212">Registry Subkey</span></span> | <span data-ttu-id="806b3-213">值</span><span class="sxs-lookup"><span data-stu-id="806b3-213">Value</span></span> |
| ------------------ | --------------- | ----- |
| <span data-ttu-id="806b3-214">1.0</span><span class="sxs-lookup"><span data-stu-id="806b3-214">1.0</span></span>                | <span data-ttu-id="806b3-215">**HKLM\\軟體\\微軟\\。NETFramework\\\\策略 v1.0\\3705**</span><span class="sxs-lookup"><span data-stu-id="806b3-215">**HKLM\\Software\\Microsoft\\.NETFramework\\Policy\\v1.0\\3705**</span></span>     | <span data-ttu-id="806b3-216">**安裝**REG_SZ等於`1`</span><span class="sxs-lookup"><span data-stu-id="806b3-216">**Install** REG_SZ equals `1`</span></span> |
| <span data-ttu-id="806b3-217">1.1</span><span class="sxs-lookup"><span data-stu-id="806b3-217">1.1</span></span>                | <span data-ttu-id="806b3-218">**HKLM\\軟體\\微軟\\NET框架設置\\NDP\\v1.1.4322**</span><span class="sxs-lookup"><span data-stu-id="806b3-218">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v1.1.4322**</span></span>   | <span data-ttu-id="806b3-219">**安裝**REG_DWORD等於`1`</span><span class="sxs-lookup"><span data-stu-id="806b3-219">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="806b3-220">2.0</span><span class="sxs-lookup"><span data-stu-id="806b3-220">2.0</span></span>                | <span data-ttu-id="806b3-221">**HKLM\\軟體\\微軟\\NET框架設置\\NDP\\v2.0.50727**</span><span class="sxs-lookup"><span data-stu-id="806b3-221">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v2.0.50727**</span></span>  | <span data-ttu-id="806b3-222">**安裝**REG_DWORD等於`1`</span><span class="sxs-lookup"><span data-stu-id="806b3-222">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="806b3-223">3.0</span><span class="sxs-lookup"><span data-stu-id="806b3-223">3.0</span></span>                | <span data-ttu-id="806b3-224">**HKLM\\軟體\\微軟\\NET框架設置\\NDP\\v3.0\\設置**</span><span class="sxs-lookup"><span data-stu-id="806b3-224">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v3.0\\Setup**</span></span> | <span data-ttu-id="806b3-225">**安裝成功**REG_DWORD等於`1`</span><span class="sxs-lookup"><span data-stu-id="806b3-225">**InstallSuccess** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="806b3-226">3.5</span><span class="sxs-lookup"><span data-stu-id="806b3-226">3.5</span></span>                | <span data-ttu-id="806b3-227">**HKLM\\軟體\\微軟\\NET框架設置\\NDP\\v3.5**</span><span class="sxs-lookup"><span data-stu-id="806b3-227">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v3.5**</span></span>        | <span data-ttu-id="806b3-228">**安裝**REG_DWORD等於`1`</span><span class="sxs-lookup"><span data-stu-id="806b3-228">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="806b3-229">4.0 用戶端設定檔</span><span class="sxs-lookup"><span data-stu-id="806b3-229">4.0 Client Profile</span></span> | <span data-ttu-id="806b3-230">**HKLM\\軟體\\微軟\\NET框架設置\\NDP\\v4\\用戶端**</span><span class="sxs-lookup"><span data-stu-id="806b3-230">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Client**</span></span>  | <span data-ttu-id="806b3-231">**安裝**REG_DWORD等於`1`</span><span class="sxs-lookup"><span data-stu-id="806b3-231">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="806b3-232">4.0 完整設定檔</span><span class="sxs-lookup"><span data-stu-id="806b3-232">4.0 Full Profile</span></span>   | <span data-ttu-id="806b3-233">**HKLM\\軟體\\微軟\\NET框架設置\\NDP\\v4\\完整**</span><span class="sxs-lookup"><span data-stu-id="806b3-233">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**</span></span>    | <span data-ttu-id="806b3-234">**安裝**REG_DWORD等於`1`</span><span class="sxs-lookup"><span data-stu-id="806b3-234">**Install** REG_DWORD equals `1`</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="806b3-235">如果您正在運行的應用為 32 位並在 64 位 Windows 中運行，則註冊表路徑將不同于之前列出的。</span><span class="sxs-lookup"><span data-stu-id="806b3-235">If the app you're running is 32-bit and running in 64-bit Windows, the registry paths will be different than previously listed.</span></span> <span data-ttu-id="806b3-236">64 位註冊表在**HKEY_LOCAL_MACHINE\\軟體\\Wow6432Node\\**子鍵中可用。</span><span class="sxs-lookup"><span data-stu-id="806b3-236">The 64-bit registry is available in the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** subkey.</span></span> <span data-ttu-id="806b3-237">例如，.NET 框架 3.5 的註冊表子項**HKEY_LOCAL_MACHINE\\軟體\\\\Wow6432Node\\微軟\\NET\\框架設置 NDP v3.5**。</span><span class="sxs-lookup"><span data-stu-id="806b3-237">For example, the registry subkey for .NET Framework 3.5 is **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v3.5**.</span></span>

<span data-ttu-id="806b3-238">請注意，.NET 框架 1.0 子鍵的註冊表路徑與其他子項不同。</span><span class="sxs-lookup"><span data-stu-id="806b3-238">Notice that the registry path to the .NET Framework 1.0 subkey is different from the others.</span></span>

### <a name="use-registry-editor-older-framework-versions"></a><span data-ttu-id="806b3-239">使用登錄編輯程式（較舊的框架版本）</span><span class="sxs-lookup"><span data-stu-id="806b3-239">Use Registry Editor (older framework versions)</span></span>

01. <span data-ttu-id="806b3-240">從 [開始]\*\*\*\* 功能表上，選擇 [執行]\*\*\*\*，輸入 *regedit*，然後選取 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="806b3-240">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

    <span data-ttu-id="806b3-241">您必須具有系統管理認證才能執行 regedit。</span><span class="sxs-lookup"><span data-stu-id="806b3-241">You must have administrative credentials to run regedit.</span></span>

01. <span data-ttu-id="806b3-242">打開與要檢查的版本匹配的子鍵。</span><span class="sxs-lookup"><span data-stu-id="806b3-242">Open the subkey that matches the version you want to check.</span></span> <span data-ttu-id="806b3-243">使用[檢測 .NET 框架 1.0 到 4.0](#detect-net-framework-10-through-40)部分中的表。</span><span class="sxs-lookup"><span data-stu-id="806b3-243">Use the table in the [Detect .NET Framework 1.0 through 4.0](#detect-net-framework-10-through-40) section.</span></span>

    <span data-ttu-id="806b3-244">下圖顯示了 .NET 框架 3.5 的子鍵及其**版本**值。</span><span class="sxs-lookup"><span data-stu-id="806b3-244">The following figure shows the subkey and its **Version** value for .NET Framework 3.5.</span></span>

    <span data-ttu-id="806b3-245">![.NET 框架 3.5 的登錄機碼。](./media/net-4-and-earlier.png ".NET 框架 3.5 及早期版本")</span><span class="sxs-lookup"><span data-stu-id="806b3-245">![The registry entry for the .NET Framework 3.5.](./media/net-4-and-earlier.png ".NET Framework 3.5 and earlier versions")</span></span>

### <a name="query-the-registry-using-code-older-framework-versions"></a><span data-ttu-id="806b3-246">使用代碼查詢註冊表（較舊的框架版本）</span><span class="sxs-lookup"><span data-stu-id="806b3-246">Query the registry using code (older framework versions)</span></span>

<span data-ttu-id="806b3-247">使用<xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType>該類訪問 Windows 註冊表中**HKEY_LOCAL_MACHINE\\軟體\\Microsoft\\NET 框架設置\\NDP**子鍵。</span><span class="sxs-lookup"><span data-stu-id="806b3-247">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP** subkey in the Windows registry.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="806b3-248">如果您正在運行的應用為 32 位並在 64 位 Windows 中運行，則註冊表路徑將不同于之前列出的。</span><span class="sxs-lookup"><span data-stu-id="806b3-248">If the app you're running is 32-bit and running in 64-bit Windows, the registry paths will be different than previously listed.</span></span> <span data-ttu-id="806b3-249">64 位註冊表在**HKEY_LOCAL_MACHINE\\軟體\\Wow6432Node\\**子鍵中可用。</span><span class="sxs-lookup"><span data-stu-id="806b3-249">The 64-bit registry is available in the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** subkey.</span></span> <span data-ttu-id="806b3-250">例如，.NET 框架 3.5 的註冊表子項**HKEY_LOCAL_MACHINE\\軟體\\\\Wow6432Node\\微軟\\NET\\框架設置 NDP v3.5**。</span><span class="sxs-lookup"><span data-stu-id="806b3-250">For example, the registry subkey for .NET Framework 3.5 is **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v3.5**.</span></span>

<span data-ttu-id="806b3-251">下面的示例查找 .NET 框架 1 到 4 個已安裝的版本：</span><span class="sxs-lookup"><span data-stu-id="806b3-251">The following example finds the .NET Framework 1 through 4 versions that are installed:</span></span>

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

## <a name="find-clr-versions"></a><span data-ttu-id="806b3-252">尋找 CLR 版本</span><span class="sxs-lookup"><span data-stu-id="806b3-252">Find CLR versions</span></span>

<span data-ttu-id="806b3-253">與 .NET 框架一起安裝的 .NET 框架 CLR 是單獨版本。</span><span class="sxs-lookup"><span data-stu-id="806b3-253">The .NET Framework CLR installed with .NET Framework is versioned separately.</span></span> <span data-ttu-id="806b3-254">有兩種方法可以檢測 .NET 框架 CLR 的版本：</span><span class="sxs-lookup"><span data-stu-id="806b3-254">There are two ways to detect the version of the .NET Framework CLR:</span></span>

- <span data-ttu-id="806b3-255">**Clrver.exe 工具**</span><span class="sxs-lookup"><span data-stu-id="806b3-255">**The Clrver.exe tool**</span></span>

  <span data-ttu-id="806b3-256">使用[CLR 版本工具 （Clrver.exe）](../tools/clrver-exe-clr-version-tool.md)確定電腦上安裝了 CLR 的哪些版本。</span><span class="sxs-lookup"><span data-stu-id="806b3-256">Use the [CLR Version tool (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) to determine which versions of the CLR are installed on a computer.</span></span> <span data-ttu-id="806b3-257">打開[視覺化工作室的開發人員命令提示符](../tools/developer-command-prompt-for-vs.md)並輸入`clrver`。</span><span class="sxs-lookup"><span data-stu-id="806b3-257">Open the [Developer Command Prompt for Visual Studio](../tools/developer-command-prompt-for-vs.md) and enter `clrver`.</span></span>

  <span data-ttu-id="806b3-258">範例輸出：</span><span class="sxs-lookup"><span data-stu-id="806b3-258">Sample output:</span></span>

  ```console
  Versions installed on the machine:
  v2.0.50727
  v4.0.30319
  ```

- <span data-ttu-id="806b3-259">**類`Environment`**</span><span class="sxs-lookup"><span data-stu-id="806b3-259">**The `Environment` class**</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="806b3-260">對於 .NET 框架 4.5 和更高版本，不要<xref:System.Environment.Version%2A?displayProperty=nameWithType>使用 屬性來檢測 CLR 的版本。</span><span class="sxs-lookup"><span data-stu-id="806b3-260">For .NET Framework 4.5 and later versions, don't use the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to detect the version of the CLR.</span></span> <span data-ttu-id="806b3-261">相反，查詢註冊表，如檢測[.NET 框架 4.5 和更高版本中所述](#detect-net-framework-45-and-later-versions)。</span><span class="sxs-lookup"><span data-stu-id="806b3-261">Instead, query the registry as described in [Detect .NET Framework 4.5 and later versions](#detect-net-framework-45-and-later-versions).</span></span>
  
  01. <span data-ttu-id="806b3-262">查詢 <xref:System.Environment.Version?displayProperty=nameWithType> 屬性以擷取 <xref:System.Version> 物件。</span><span class="sxs-lookup"><span data-stu-id="806b3-262">Query the <xref:System.Environment.Version?displayProperty=nameWithType> property to retrieve a <xref:System.Version> object.</span></span>
  
      <span data-ttu-id="806b3-263">傳回的 `System.Version` 物件可識別目前執行程式碼的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="806b3-263">The returned `System.Version` object identifies the version of the runtime that's currently executing the code.</span></span> <span data-ttu-id="806b3-264">它不會傳回組件版本或已安裝在電腦上的其他執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="806b3-264">It doesn't return assembly versions or other versions of the runtime that may have been installed on the computer.</span></span>
  
      <span data-ttu-id="806b3-265">對於 .NET Framework 版本 4、4.5、4.5.1 和 4.5.2，返回<xref:System.Version>物件的字串表示形式為 4.0.30319。*xxxxx，\*\*其中xxxxx*小於42000。</span><span class="sxs-lookup"><span data-stu-id="806b3-265">For .NET Framework versions 4, 4.5, 4.5.1, and 4.5.2, the string representation of the returned <xref:System.Version> object has the form 4.0.30319.*xxxxx*, where *xxxxx* is less than 42000.</span></span> <span data-ttu-id="806b3-266">對於 .NET 框架 4.6 和更高版本，它有 4.0.30319.42000 的形式。</span><span class="sxs-lookup"><span data-stu-id="806b3-266">For .NET Framework 4.6 and later versions, it has the form 4.0.30319.42000.</span></span>
  
  01. <span data-ttu-id="806b3-267">獲得**Version**物件後，按如下方式查詢它：</span><span class="sxs-lookup"><span data-stu-id="806b3-267">After you have the **Version** object, query it as follows:</span></span>
  
      - <span data-ttu-id="806b3-268">針對主要版本識別項 (例如 4.0 版的 *4*)，請使用 <xref:System.Version.Major%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="806b3-268">For the major release identifier (for example, *4* for version 4.0), use the <xref:System.Version.Major%2A?displayProperty=nameWithType> property.</span></span>
  
      - <span data-ttu-id="806b3-269">針對次要版本識別項 (例如 4.0 版的 *0*)，請使用 <xref:System.Version.Minor%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="806b3-269">For the minor release identifier (for example, *0* for version 4.0), use the <xref:System.Version.Minor%2A?displayProperty=nameWithType> property.</span></span>
  
      - <span data-ttu-id="806b3-270">針對整個版本字串 (例如 *4.0.30319.18010*)，請使用 <xref:System.Version.ToString%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="806b3-270">For the entire version string (for example, *4.0.30319.18010*), use the <xref:System.Version.ToString%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="806b3-271">這個方法會傳回單一值，其反映執行程式碼的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="806b3-271">This method returns a single value that reflects the version of the runtime that's executing the code.</span></span> <span data-ttu-id="806b3-272">它不會傳回組件版本或可能已安裝在電腦上的其他執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="806b3-272">It doesn't return assembly versions or other runtime versions that may be installed on the computer.</span></span>

  <span data-ttu-id="806b3-273">下列範例使用 <xref:System.Environment.Version%2A?displayProperty=nameWithType> 屬性來擷取 CLR 版本資訊：</span><span class="sxs-lookup"><span data-stu-id="806b3-273">The following example uses the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to retrieve CLR version information:</span></span>
  
  [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
  [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a><span data-ttu-id="806b3-274">另請參閱</span><span class="sxs-lookup"><span data-stu-id="806b3-274">See also</span></span>

- [<span data-ttu-id="806b3-275">如何：確定安裝了哪些 .NET 框架更新</span><span class="sxs-lookup"><span data-stu-id="806b3-275">How to: Determine which .NET Framework updates are installed</span></span>](how-to-determine-which-net-framework-updates-are-installed.md)
- [<span data-ttu-id="806b3-276">安裝適用於開發人員的 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="806b3-276">Install the .NET Framework for developers</span></span>](../install/guide-for-developers.md)
- [<span data-ttu-id="806b3-277">.NET 框架版本和依賴項</span><span class="sxs-lookup"><span data-stu-id="806b3-277">.NET Framework versions and dependencies</span></span>](versions-and-dependencies.md)
