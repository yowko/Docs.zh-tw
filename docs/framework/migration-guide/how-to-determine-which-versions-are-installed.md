---
title: 判斷安裝的 .NET Framework 版本
description: 藉由查詢 Windows 登錄，使用程式碼、regedit.exe 或 PowerShell 來偵測電腦上所安裝的 .NET Framework 版本。
ms.date: 02/03/2020
dev_langs:
- csharp
- vb
ms.custom: updateeachrelease
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
ms.openlocfilehash: 122441e9238fd91199aed255b0125f69081c0a8c
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990146"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="7296e-103">如何：判斷安裝的 .NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="7296e-103">How to: Determine which .NET Framework versions are installed</span></span>

<span data-ttu-id="7296e-104">使用者可以在他們的電腦上[安裝](../install/index.md)及執行多個版本的 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="7296e-104">Users can [install](../install/index.md) and run multiple versions of the .NET Framework on their computers.</span></span> <span data-ttu-id="7296e-105">當您開發或部署應用程式時，您可能需要知道使用者電腦上安裝的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="7296e-105">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user’s computer.</span></span> <span data-ttu-id="7296e-106">登錄包含電腦上安裝的 .NET Framework 版本清單。</span><span class="sxs-lookup"><span data-stu-id="7296e-106">The registry contains a list of the .NET Framework versions installed on a computer.</span></span>

<span data-ttu-id="7296e-107">.NET Framework 包含兩個主要元件，各有各的版本控制：</span><span class="sxs-lookup"><span data-stu-id="7296e-107">The .NET Framework consists of two main components, which are versioned separately:</span></span>

- <span data-ttu-id="7296e-108">組件集合，這是為應用程式提供功能的類型與資源集合。</span><span class="sxs-lookup"><span data-stu-id="7296e-108">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="7296e-109">.NET Framework 和組件會共用相同的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="7296e-109">The .NET Framework and assemblies share the same version number.</span></span> <span data-ttu-id="7296e-110">例如，.NET Framework 版本包含 4.5、4.6.1 和 4.7.2。</span><span class="sxs-lookup"><span data-stu-id="7296e-110">For example, .NET Framework versions include 4.5, 4.6.1, and 4.7.2.</span></span>

- <span data-ttu-id="7296e-111">通用語言執行平台 (CLR)，負責管理和執行應用程式的程式碼。</span><span class="sxs-lookup"><span data-stu-id="7296e-111">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="7296e-112">單一的 CLR 版本通常會支援多個 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="7296e-112">A single CLR version typically supports multiple .NET Framework versions.</span></span> <span data-ttu-id="7296e-113">例如，CLR 版本4.0.30319。*xxxxx，其中* *xxxxx*小於42000，支援 .NET Framework 版本4到4.5.2。</span><span class="sxs-lookup"><span data-stu-id="7296e-113">For example, CLR version 4.0.30319.*xxxxx* where *xxxxx* is less than 42000, supports .NET Framework versions 4 through 4.5.2.</span></span> <span data-ttu-id="7296e-114">CLR 版本大於或等於4.0.30319.42000 支援從 .NET Framework 4.6 開始的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="7296e-114">CLR version greater than or equal to 4.0.30319.42000 supports .NET Framework versions starting with .NET Framework 4.6.</span></span>

<span data-ttu-id="7296e-115">有提供社區維護的工具可協助您偵測已安裝的 .NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="7296e-115">Community-maintained tools are available to help detect which .NET Framework versions are installed:</span></span>

- [https://github.com/jmalarcon/DotNetVersions](https://github.com/jmalarcon/DotNetVersions)

  <span data-ttu-id="7296e-116">.NET 2.0 命令列工具。</span><span class="sxs-lookup"><span data-stu-id="7296e-116">A .NET 2.0 command-line tool.</span></span>

- [https://github.com/EliteLoser/DotNetVersionLister](https://github.com/EliteLoser/DotNetVersionLister)

  <span data-ttu-id="7296e-117">PowerShell 2.0 模組。</span><span class="sxs-lookup"><span data-stu-id="7296e-117">A PowerShell 2.0 module.</span></span>

<span data-ttu-id="7296e-118">如需偵測每個 .NET Framework 版本之已安裝更新的詳細資訊，請參閱[如何：判斷已安裝的 .NET Framework 更新](how-to-determine-which-net-framework-updates-are-installed.md)。</span><span class="sxs-lookup"><span data-stu-id="7296e-118">For information about detecting the installed updates for each version of the .NET Framework, see [How to: Determine which .NET Framework updates are installed](how-to-determine-which-net-framework-updates-are-installed.md).</span></span>

## <a name="detect-net-framework-45-and-later-versions"></a><span data-ttu-id="7296e-119">偵測 .NET Framework 4.5 和更新版本</span><span class="sxs-lookup"><span data-stu-id="7296e-119">Detect .NET Framework 4.5 and later versions</span></span>

<span data-ttu-id="7296e-120">安裝在電腦上的 .NET Framework （4.5 和更新版本），會列在**HKEY_LOCAL_MACHINE \\ SOFTWARE \\ Microsoft \\ NET Framework 安裝 \\ NDP \\ v4 \\ Full**的登錄中。</span><span class="sxs-lookup"><span data-stu-id="7296e-120">The version of .NET Framework (4.5 and later) installed on a machine is listed in the registry at **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span></span> <span data-ttu-id="7296e-121">如果遺漏**完整**的子機碼，則不會安裝 .NET Framework 4.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="7296e-121">If the **Full** subkey is missing, then .NET Framework 4.5 or above isn't installed.</span></span>

> [!NOTE]
> <span data-ttu-id="7296e-122">登錄路徑中的**NET Framework 安裝程式**子機碼*不*是以句號開頭。</span><span class="sxs-lookup"><span data-stu-id="7296e-122">The **NET Framework Setup** subkey in the registry path does *not* begin with a period.</span></span>

<span data-ttu-id="7296e-123">登錄中的**Release** REG_DWORD 值代表已安裝 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="7296e-123">The **Release** REG_DWORD value in the registry represents the version of .NET Framework installed.</span></span>

<a name="version_table"></a>

| <span data-ttu-id="7296e-124">.NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="7296e-124">.NET Framework version</span></span> | <span data-ttu-id="7296e-125">**發行**的值</span><span class="sxs-lookup"><span data-stu-id="7296e-125">Value of **Release**</span></span> |
| ---------------------- | -------------------------- |
| <span data-ttu-id="7296e-126">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="7296e-126">.NET Framework 4.5</span></span>     | <span data-ttu-id="7296e-127">所有 Windows 作業系統：378389</span><span class="sxs-lookup"><span data-stu-id="7296e-127">All Windows operating systems: 378389</span></span> |
| <span data-ttu-id="7296e-128">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="7296e-128">.NET Framework 4.5.1</span></span>   | <span data-ttu-id="7296e-129">在 Windows 8.1 和 Windows Server 2012 R2 上：378675</span><span class="sxs-lookup"><span data-stu-id="7296e-129">On Windows 8.1 and Windows Server 2012 R2: 378675</span></span><br /><span data-ttu-id="7296e-130">在其他所有 Windows 作業系統上：378758</span><span class="sxs-lookup"><span data-stu-id="7296e-130">On all other Windows operating systems: 378758</span></span> |
| <span data-ttu-id="7296e-131">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="7296e-131">.NET Framework 4.5.2</span></span>   | <span data-ttu-id="7296e-132">所有 Windows 作業系統：379893</span><span class="sxs-lookup"><span data-stu-id="7296e-132">All Windows operating systems: 379893</span></span> |
| <span data-ttu-id="7296e-133">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="7296e-133">.NET Framework 4.6</span></span>     | <span data-ttu-id="7296e-134">在 Windows 10: 393295 上</span><span class="sxs-lookup"><span data-stu-id="7296e-134">On Windows 10: 393295</span></span><br /><span data-ttu-id="7296e-135">在其他所有 Windows 作業系統上：393297</span><span class="sxs-lookup"><span data-stu-id="7296e-135">On all other Windows operating systems: 393297</span></span> |
| <span data-ttu-id="7296e-136">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="7296e-136">.NET Framework 4.6.1</span></span>   | <span data-ttu-id="7296e-137">Windows 10 11 月更新系統：394254</span><span class="sxs-lookup"><span data-stu-id="7296e-137">On Windows 10 November Update systems: 394254</span></span><br /><span data-ttu-id="7296e-138">在所有其他 Windows 作業系統上（包括 Windows 10）：394271</span><span class="sxs-lookup"><span data-stu-id="7296e-138">On all other Windows operating systems (including Windows 10): 394271</span></span> |
| <span data-ttu-id="7296e-139">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="7296e-139">.NET Framework 4.6.2</span></span>   | <span data-ttu-id="7296e-140">Windows 10 年度更新版及 Windows Server 2016：394802</span><span class="sxs-lookup"><span data-stu-id="7296e-140">On Windows 10 Anniversary Update and Windows Server 2016: 394802</span></span><br /><span data-ttu-id="7296e-141">在所有其他 Windows 作業系統（包括其他 Windows 10 作業系統）上：394806</span><span class="sxs-lookup"><span data-stu-id="7296e-141">On all other Windows operating systems (including other Windows 10 operating systems): 394806</span></span> |
| <span data-ttu-id="7296e-142">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="7296e-142">.NET Framework 4.7</span></span>     | <span data-ttu-id="7296e-143">Windows 10 Creators Update：460798</span><span class="sxs-lookup"><span data-stu-id="7296e-143">On Windows 10 Creators Update: 460798</span></span><br /><span data-ttu-id="7296e-144">在所有其他 Windows 作業系統（包括其他 Windows 10 作業系統）上：460805</span><span class="sxs-lookup"><span data-stu-id="7296e-144">On all other Windows operating systems (including other Windows 10 operating systems): 460805</span></span> |
| <span data-ttu-id="7296e-145">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="7296e-145">.NET Framework 4.7.1</span></span>   | <span data-ttu-id="7296e-146">Windows 10 秋季建立者更新和 Windows Server，版本1709：461308</span><span class="sxs-lookup"><span data-stu-id="7296e-146">On Windows 10 Fall Creators Update and Windows Server, version 1709: 461308</span></span><br/><span data-ttu-id="7296e-147">在所有其他 Windows 作業系統（包括其他 Windows 10 作業系統）上：461310</span><span class="sxs-lookup"><span data-stu-id="7296e-147">On all other Windows operating systems (including other Windows 10 operating systems): 461310</span></span> |
| <span data-ttu-id="7296e-148">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="7296e-148">.NET Framework 4.7.2</span></span>   | <span data-ttu-id="7296e-149">Windows 10 2018 年4月更新和 Windows Server，版本1803：461808</span><span class="sxs-lookup"><span data-stu-id="7296e-149">On Windows 10 April 2018 Update and Windows Server, version 1803: 461808</span></span><br/><span data-ttu-id="7296e-150">在 Windows 10 2018 年4月更新和 Windows Server 的所有 Windows 作業系統上，版本1803：461814</span><span class="sxs-lookup"><span data-stu-id="7296e-150">On all Windows operating systems other than Windows 10 April 2018 Update and Windows Server, version 1803: 461814</span></span> |
| <span data-ttu-id="7296e-151">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="7296e-151">.NET Framework 4.8</span></span>     | <span data-ttu-id="7296e-152">在 Windows 10 5 月2019更新和 Windows 10 十一月2019更新：528040</span><span class="sxs-lookup"><span data-stu-id="7296e-152">On Windows 10 May 2019 Update and Windows 10 November 2019 Update: 528040</span></span><br/><span data-ttu-id="7296e-153">在 Windows 10 5 月2020更新：528372</span><span class="sxs-lookup"><span data-stu-id="7296e-153">On Windows 10 May 2020 Update: 528372</span></span><br/><span data-ttu-id="7296e-154">在所有其他 Windows 作業系統（包括其他 Windows 10 作業系統）上：528049</span><span class="sxs-lookup"><span data-stu-id="7296e-154">On all other Windows operating systems (including other Windows 10 operating systems): 528049</span></span> |

### <a name="minimum-version"></a><span data-ttu-id="7296e-155">最小版本</span><span class="sxs-lookup"><span data-stu-id="7296e-155">Minimum version</span></span>

<span data-ttu-id="7296e-156">若要判斷 .NET Framework 的*最低*版本是否存在，請使用上表中該版本的最小**發行**REG_DWORD 值。</span><span class="sxs-lookup"><span data-stu-id="7296e-156">To determine whether a *minimum* version of the .NET Framework is present, use the smallest **Release** REG_DWORD value for that version from the previous table.</span></span>

<span data-ttu-id="7296e-157">例如，如果您的應用程式是在 .NET Framework 4.8 或更新版本下執行，請測試**版本**REG_DWORD 值是否*大於或等於*528040。</span><span class="sxs-lookup"><span data-stu-id="7296e-157">For example, if your application runs under .NET Framework 4.8 or a later version, test for a **Release** REG_DWORD value that is *greater than or equal to* 528040.</span></span>

| <span data-ttu-id="7296e-158">.NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="7296e-158">.NET Framework version</span></span> | <span data-ttu-id="7296e-159">最小值</span><span class="sxs-lookup"><span data-stu-id="7296e-159">Minimum value</span></span> |
| ---------------------- | ------------- |
| <span data-ttu-id="7296e-160">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="7296e-160">.NET Framework 4.5</span></span>     | <span data-ttu-id="7296e-161">378389</span><span class="sxs-lookup"><span data-stu-id="7296e-161">378389</span></span> |
| <span data-ttu-id="7296e-162">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="7296e-162">.NET Framework 4.5.1</span></span>   | <span data-ttu-id="7296e-163">378675</span><span class="sxs-lookup"><span data-stu-id="7296e-163">378675</span></span> |
| <span data-ttu-id="7296e-164">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="7296e-164">.NET Framework 4.5.2</span></span>   | <span data-ttu-id="7296e-165">379893</span><span class="sxs-lookup"><span data-stu-id="7296e-165">379893</span></span> |
| <span data-ttu-id="7296e-166">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="7296e-166">.NET Framework 4.6</span></span>     | <span data-ttu-id="7296e-167">393295</span><span class="sxs-lookup"><span data-stu-id="7296e-167">393295</span></span> |
| <span data-ttu-id="7296e-168">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="7296e-168">.NET Framework 4.6.1</span></span>   | <span data-ttu-id="7296e-169">394254</span><span class="sxs-lookup"><span data-stu-id="7296e-169">394254</span></span> |
| <span data-ttu-id="7296e-170">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="7296e-170">.NET Framework 4.6.2</span></span>   | <span data-ttu-id="7296e-171">394802</span><span class="sxs-lookup"><span data-stu-id="7296e-171">394802</span></span> |
| <span data-ttu-id="7296e-172">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="7296e-172">.NET Framework 4.7</span></span>     | <span data-ttu-id="7296e-173">460798</span><span class="sxs-lookup"><span data-stu-id="7296e-173">460798</span></span> |
| <span data-ttu-id="7296e-174">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="7296e-174">.NET Framework 4.7.1</span></span>   | <span data-ttu-id="7296e-175">461308</span><span class="sxs-lookup"><span data-stu-id="7296e-175">461308</span></span> |
| <span data-ttu-id="7296e-176">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="7296e-176">.NET Framework 4.7.2</span></span>   | <span data-ttu-id="7296e-177">461808</span><span class="sxs-lookup"><span data-stu-id="7296e-177">461808</span></span> |
| <span data-ttu-id="7296e-178">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="7296e-178">.NET Framework 4.8</span></span>     | <span data-ttu-id="7296e-179">528040</span><span class="sxs-lookup"><span data-stu-id="7296e-179">528040</span></span> |

### <a name="use-registry-editor"></a><span data-ttu-id="7296e-180">使用登錄編輯程式</span><span class="sxs-lookup"><span data-stu-id="7296e-180">Use Registry Editor</span></span>

01. <span data-ttu-id="7296e-181">從 [開始]\*\*\*\* 功能表上，選擇 [執行]\*\*\*\*，輸入 *regedit*，然後選取 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7296e-181">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

    <span data-ttu-id="7296e-182">您必須具有系統管理認證才能執行 regedit。</span><span class="sxs-lookup"><span data-stu-id="7296e-182">You must have administrative credentials to run regedit.</span></span>

01. <span data-ttu-id="7296e-183">在 [登錄編輯程式] 中，開啟下列子機碼： **HKEY_LOCAL_MACHINE \\ SOFTWARE \\ Microsoft \\ NET Framework 安裝 \\ NDP \\ v4 \\ Full**。</span><span class="sxs-lookup"><span data-stu-id="7296e-183">In the Registry Editor, open the following subkey: **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span></span> <span data-ttu-id="7296e-184">如果 **Full** 子機碼不存在，即表示未安裝 .NET Framework 4.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="7296e-184">If the **Full** subkey isn't present, then you don't have the .NET Framework 4.5 or later installed.</span></span>

01. <span data-ttu-id="7296e-185">檢查名為**Release**的 REG_DWORD 專案。</span><span class="sxs-lookup"><span data-stu-id="7296e-185">Check for a REG_DWORD entry named **Release**.</span></span> <span data-ttu-id="7296e-186">如果已存在，則您已安裝 .NET Framework 4.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="7296e-186">If it exists, then you have .NET Framework 4.5 or later installed.</span></span> <span data-ttu-id="7296e-187">其值對應至特定版本的 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="7296e-187">Its value corresponds to a particular version of the .NET Framework.</span></span> <span data-ttu-id="7296e-188">例如，在下圖中， **release**專案的值是528040，也就是 .NET Framework 4.8 的發行金鑰。</span><span class="sxs-lookup"><span data-stu-id="7296e-188">In the following figure, for example, the value of the **Release** entry is 528040, which is the release key for .NET Framework 4.8.</span></span>

    <span data-ttu-id="7296e-189">![.NET Framework 4.5 的登錄專案](./media/clr-installdir.png ".NET Framework 4.5 的登錄專案")</span><span class="sxs-lookup"><span data-stu-id="7296e-189">![Registry entry for the .NET Framework 4.5](./media/clr-installdir.png "Registry entry for the .NET Framework 4.5")</span></span>

### <a name="use-powershell-to-check-for-a-minimum-version"></a><span data-ttu-id="7296e-190">使用 PowerShell 檢查最低版本</span><span class="sxs-lookup"><span data-stu-id="7296e-190">Use PowerShell to check for a minimum version</span></span>

<span data-ttu-id="7296e-191">使用 PowerShell 命令來檢查**HKEY_LOCAL_MACHINE \\ SOFTWARE \\ Microsoft \\ NET Framework 安裝 \\ NDP \\ V4 \\ Full**子機碼的**Release**專案值。</span><span class="sxs-lookup"><span data-stu-id="7296e-191">Use PowerShell commands to check the value of the **Release** entry of the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** subkey.</span></span>

<span data-ttu-id="7296e-192">下列範例會檢查 **Release** 項目值，以判斷是否安裝了 .NET Framework 4.6.2 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="7296e-192">The following examples check the value of the **Release** entry to determine whether the .NET Framework 4.6.2 or later is installed.</span></span> <span data-ttu-id="7296e-193">如已安裝，則此程式碼會傳回 `True`；否則傳回 `False`。</span><span class="sxs-lookup"><span data-stu-id="7296e-193">This code returns `True` if it's installed and `False` otherwise.</span></span>

```PowerShell
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

### <a name="query-the-registry-using-code"></a><span data-ttu-id="7296e-194">使用程式碼查詢登錄</span><span class="sxs-lookup"><span data-stu-id="7296e-194">Query the registry using code</span></span>

01. <span data-ttu-id="7296e-195">使用 <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> 和 <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> 方法來存取 Windows 登錄中的**HKEY_LOCAL_MACHINE \\ SOFTWARE \\ Microsoft \\ NET Framework 安裝 \\ NDP \\ v4 \\ Full**子機碼。</span><span class="sxs-lookup"><span data-stu-id="7296e-195">Use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> methods to access the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** subkey in the Windows registry.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="7296e-196">如果您執行的應用程式是32位且在64位 Windows 中執行，則登錄路徑會與先前所列的不同。</span><span class="sxs-lookup"><span data-stu-id="7296e-196">If the app you're running is 32-bit and running in 64-bit Windows, the registry paths will be different than previously listed.</span></span> <span data-ttu-id="7296e-197">64位登錄可在\*\*HKEY_LOCAL_MACHINE \\ SOFTWARE \\ Wow6432Node \\ \*\*子機碼中使用。</span><span class="sxs-lookup"><span data-stu-id="7296e-197">The 64-bit registry is available in the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** subkey.</span></span> <span data-ttu-id="7296e-198">例如，.NET Framework 4.5 的登錄子機碼為**HKEY_LOCAL_MACHINE \\ SOFTWARE \\ Wow6432Node \\ Microsoft \\ NET Framework 安裝 \\ NDP \\ v4 \\ Full**。</span><span class="sxs-lookup"><span data-stu-id="7296e-198">For example, the registry subkey for .NET Framework 4.5 is **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span></span>

01. <span data-ttu-id="7296e-199">檢查**Release** REG_DWORD 值以判斷已安裝的版本。</span><span class="sxs-lookup"><span data-stu-id="7296e-199">Check the **Release** REG_DWORD value to determine the installed version.</span></span> <span data-ttu-id="7296e-200">若要正向相容，請檢查是否有大於或等於 [.NET Framework 版本表](#version_table)中所列值的值。</span><span class="sxs-lookup"><span data-stu-id="7296e-200">To be forward-compatible, check for a value greater than or equal to the value listed in the [.NET Framework version table](#version_table).</span></span>

<span data-ttu-id="7296e-201">下列範例會檢查登錄中的 **Release** 項目值，尋找已安裝的 .NET Framework 4.5 和更新版本：</span><span class="sxs-lookup"><span data-stu-id="7296e-201">The following example checks the value of the **Release** entry in the registry to find the .NET Framework 4.5 and later versions that are installed:</span></span>

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

<span data-ttu-id="7296e-202">此範例遵循版本檢查的建議做法：</span><span class="sxs-lookup"><span data-stu-id="7296e-202">This example follows the recommended practice for version checking:</span></span>

- <span data-ttu-id="7296e-203">它會檢查 **Release** 項目值是否「大於或等於」\*\* 已知版本機碼的值。</span><span class="sxs-lookup"><span data-stu-id="7296e-203">It checks whether the value of the **Release** entry is *greater than or equal to* the value of the known release keys.</span></span>
- <span data-ttu-id="7296e-204">它會從最新版本依序檢查到最舊版本。</span><span class="sxs-lookup"><span data-stu-id="7296e-204">It checks in order from most recent version to earliest version.</span></span>

## <a name="detect-net-framework-10-through-40"></a><span data-ttu-id="7296e-205">偵測 .NET Framework 1.0 到4。0</span><span class="sxs-lookup"><span data-stu-id="7296e-205">Detect .NET Framework 1.0 through 4.0</span></span>

<span data-ttu-id="7296e-206">從1.1 到4.0 的每個版本 .NET Framework 都會列為**HKEY_LOCAL_MACHINE \\ SOFTWARE \\ Microsoft \\ NET Framework 安裝 \\ NDP**的子機碼。</span><span class="sxs-lookup"><span data-stu-id="7296e-206">Each version of .NET Framework from 1.1 to 4.0 is listed as a subkey at **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP**.</span></span> <span data-ttu-id="7296e-207">下表列出每個 .NET Framework 版本的路徑。</span><span class="sxs-lookup"><span data-stu-id="7296e-207">The following table lists the path to each .NET Framework version.</span></span> <span data-ttu-id="7296e-208">對於大部分版本而言，會有**安裝**REG_DWORD 值， `1` 表示已安裝此版本。</span><span class="sxs-lookup"><span data-stu-id="7296e-208">For most versions, there's a **Install** REG_DWORD value of `1` to indicate this version is installed.</span></span> <span data-ttu-id="7296e-209">在這些子機碼中，還有一個**版本**REG_SZ 值，其中包含版本字串。</span><span class="sxs-lookup"><span data-stu-id="7296e-209">In these subkeys, there's also a **Version** REG_SZ value that contains a version string.</span></span>

> [!NOTE]
> <span data-ttu-id="7296e-210">登錄路徑中的**NET Framework 安裝程式**子機碼*不*是以句號開頭。</span><span class="sxs-lookup"><span data-stu-id="7296e-210">The **NET Framework Setup** subkey in the registry path does *not* begin with a period.</span></span>

| <span data-ttu-id="7296e-211">Framework 版本</span><span class="sxs-lookup"><span data-stu-id="7296e-211">Framework Version</span></span>  | <span data-ttu-id="7296e-212">登錄子機碼</span><span class="sxs-lookup"><span data-stu-id="7296e-212">Registry Subkey</span></span> | <span data-ttu-id="7296e-213">值</span><span class="sxs-lookup"><span data-stu-id="7296e-213">Value</span></span> |
| ------------------ | --------------- | ----- |
| <span data-ttu-id="7296e-214">1.0</span><span class="sxs-lookup"><span data-stu-id="7296e-214">1.0</span></span>                | <span data-ttu-id="7296e-215">**HKLM \\ Software \\ Microsoft \\ 。.Netframework \\ 原則 v1.0 \\ \\ 3705**</span><span class="sxs-lookup"><span data-stu-id="7296e-215">**HKLM\\Software\\Microsoft\\.NETFramework\\Policy\\v1.0\\3705**</span></span>     | <span data-ttu-id="7296e-216">**安裝**REG_SZ 等於`1`</span><span class="sxs-lookup"><span data-stu-id="7296e-216">**Install** REG_SZ equals `1`</span></span> |
| <span data-ttu-id="7296e-217">1.1</span><span class="sxs-lookup"><span data-stu-id="7296e-217">1.1</span></span>                | <span data-ttu-id="7296e-218">**HKLM \\ Software \\ Microsoft \\ NET Framework 安裝 \\ NDP \\ v 1.1.4322**</span><span class="sxs-lookup"><span data-stu-id="7296e-218">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v1.1.4322**</span></span>   | <span data-ttu-id="7296e-219">**安裝**REG_DWORD 等於`1`</span><span class="sxs-lookup"><span data-stu-id="7296e-219">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="7296e-220">2.0</span><span class="sxs-lookup"><span data-stu-id="7296e-220">2.0</span></span>                | <span data-ttu-id="7296e-221">**HKLM \\ Software \\ Microsoft \\ NET Framework 安裝 \\ NDP \\ v 2.0.50727**</span><span class="sxs-lookup"><span data-stu-id="7296e-221">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v2.0.50727**</span></span>  | <span data-ttu-id="7296e-222">**安裝**REG_DWORD 等於`1`</span><span class="sxs-lookup"><span data-stu-id="7296e-222">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="7296e-223">3.0</span><span class="sxs-lookup"><span data-stu-id="7296e-223">3.0</span></span>                | <span data-ttu-id="7296e-224">**HKLM \\ Software \\ Microsoft \\ NET Framework 安裝 \\ NDP \\ v3.0 \\ 安裝程式**</span><span class="sxs-lookup"><span data-stu-id="7296e-224">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v3.0\\Setup**</span></span> | <span data-ttu-id="7296e-225">**InstallSuccess**REG_DWORD 等於`1`</span><span class="sxs-lookup"><span data-stu-id="7296e-225">**InstallSuccess** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="7296e-226">3.5</span><span class="sxs-lookup"><span data-stu-id="7296e-226">3.5</span></span>                | <span data-ttu-id="7296e-227">**HKLM \\ Software \\ Microsoft \\ NET Framework 安裝 \\ NDP \\ v 3。5**</span><span class="sxs-lookup"><span data-stu-id="7296e-227">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v3.5**</span></span>        | <span data-ttu-id="7296e-228">**安裝**REG_DWORD 等於`1`</span><span class="sxs-lookup"><span data-stu-id="7296e-228">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="7296e-229">4.0 用戶端設定檔</span><span class="sxs-lookup"><span data-stu-id="7296e-229">4.0 Client Profile</span></span> | <span data-ttu-id="7296e-230">**HKLM \\ Software \\ Microsoft \\ NET Framework 安裝 \\ NDP \\ v4 \\ 用戶端**</span><span class="sxs-lookup"><span data-stu-id="7296e-230">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Client**</span></span>  | <span data-ttu-id="7296e-231">**安裝**REG_DWORD 等於`1`</span><span class="sxs-lookup"><span data-stu-id="7296e-231">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="7296e-232">4.0 完整設定檔</span><span class="sxs-lookup"><span data-stu-id="7296e-232">4.0 Full Profile</span></span>   | <span data-ttu-id="7296e-233">**HKLM \\ Software \\ Microsoft \\ NET Framework 安裝 \\ NDP \\ v4 \\ Full**</span><span class="sxs-lookup"><span data-stu-id="7296e-233">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**</span></span>    | <span data-ttu-id="7296e-234">**安裝**REG_DWORD 等於`1`</span><span class="sxs-lookup"><span data-stu-id="7296e-234">**Install** REG_DWORD equals `1`</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="7296e-235">如果您執行的應用程式是32位且在64位 Windows 中執行，則登錄路徑會與先前所列的不同。</span><span class="sxs-lookup"><span data-stu-id="7296e-235">If the app you're running is 32-bit and running in 64-bit Windows, the registry paths will be different than previously listed.</span></span> <span data-ttu-id="7296e-236">64位登錄可在\*\*HKEY_LOCAL_MACHINE \\ SOFTWARE \\ Wow6432Node \\ \*\*子機碼中使用。</span><span class="sxs-lookup"><span data-stu-id="7296e-236">The 64-bit registry is available in the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** subkey.</span></span> <span data-ttu-id="7296e-237">例如，.NET Framework 3.5 的登錄子機碼為**HKEY_LOCAL_MACHINE \\ SOFTWARE \\ Wow6432Node \\ Microsoft \\ NET Framework 安裝程式 \\ NDP \\ v 3.5**。</span><span class="sxs-lookup"><span data-stu-id="7296e-237">For example, the registry subkey for .NET Framework 3.5 is **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v3.5**.</span></span>

<span data-ttu-id="7296e-238">請注意，.NET Framework 1.0 子機碼的登錄路徑與其他子機碼不同。</span><span class="sxs-lookup"><span data-stu-id="7296e-238">Notice that the registry path to the .NET Framework 1.0 subkey is different from the others.</span></span>

### <a name="use-registry-editor-older-framework-versions"></a><span data-ttu-id="7296e-239">使用登錄編輯程式（較舊的 framework 版本）</span><span class="sxs-lookup"><span data-stu-id="7296e-239">Use Registry Editor (older framework versions)</span></span>

01. <span data-ttu-id="7296e-240">從 [開始]\*\*\*\* 功能表上，選擇 [執行]\*\*\*\*，輸入 *regedit*，然後選取 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7296e-240">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

    <span data-ttu-id="7296e-241">您必須具有系統管理認證才能執行 regedit。</span><span class="sxs-lookup"><span data-stu-id="7296e-241">You must have administrative credentials to run regedit.</span></span>

01. <span data-ttu-id="7296e-242">開啟與您要檢查之版本相符的子機碼。</span><span class="sxs-lookup"><span data-stu-id="7296e-242">Open the subkey that matches the version you want to check.</span></span> <span data-ttu-id="7296e-243">使用 [偵測[.NET Framework 1.0 到 4.0](#detect-net-framework-10-through-40) ] 區段中的資料表。</span><span class="sxs-lookup"><span data-stu-id="7296e-243">Use the table in the [Detect .NET Framework 1.0 through 4.0](#detect-net-framework-10-through-40) section.</span></span>

    <span data-ttu-id="7296e-244">下圖顯示 .NET Framework 3.5 的子機碼及其**版本**值。</span><span class="sxs-lookup"><span data-stu-id="7296e-244">The following figure shows the subkey and its **Version** value for .NET Framework 3.5.</span></span>

    <span data-ttu-id="7296e-245">![.NET Framework 3.5 的登錄專案。](./media/net-4-and-earlier.png ".NET Framework 3.5 和更早版本")</span><span class="sxs-lookup"><span data-stu-id="7296e-245">![The registry entry for the .NET Framework 3.5.](./media/net-4-and-earlier.png ".NET Framework 3.5 and earlier versions")</span></span>

### <a name="query-the-registry-using-code-older-framework-versions"></a><span data-ttu-id="7296e-246">使用程式碼查詢登錄（較舊的 framework 版本）</span><span class="sxs-lookup"><span data-stu-id="7296e-246">Query the registry using code (older framework versions)</span></span>

<span data-ttu-id="7296e-247">使用 <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> 類別存取 Windows 登錄中的**HKEY_LOCAL_MACHINE \\ SOFTWARE \\ Microsoft \\ NET Framework 安裝 \\ NDP**子機碼。</span><span class="sxs-lookup"><span data-stu-id="7296e-247">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP** subkey in the Windows registry.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7296e-248">如果您執行的應用程式是32位且在64位 Windows 中執行，則登錄路徑會與先前所列的不同。</span><span class="sxs-lookup"><span data-stu-id="7296e-248">If the app you're running is 32-bit and running in 64-bit Windows, the registry paths will be different than previously listed.</span></span> <span data-ttu-id="7296e-249">64位登錄可在\*\*HKEY_LOCAL_MACHINE \\ SOFTWARE \\ Wow6432Node \\ \*\*子機碼中使用。</span><span class="sxs-lookup"><span data-stu-id="7296e-249">The 64-bit registry is available in the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** subkey.</span></span> <span data-ttu-id="7296e-250">例如，.NET Framework 3.5 的登錄子機碼為**HKEY_LOCAL_MACHINE \\ SOFTWARE \\ Wow6432Node \\ Microsoft \\ NET Framework 安裝程式 \\ NDP \\ v 3.5**。</span><span class="sxs-lookup"><span data-stu-id="7296e-250">For example, the registry subkey for .NET Framework 3.5 is **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v3.5**.</span></span>

<span data-ttu-id="7296e-251">下列範例會尋找已安裝的 .NET Framework 1 到4個版本：</span><span class="sxs-lookup"><span data-stu-id="7296e-251">The following example finds the .NET Framework 1 through 4 versions that are installed:</span></span>

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

## <a name="find-clr-versions"></a><span data-ttu-id="7296e-252">尋找 CLR 版本</span><span class="sxs-lookup"><span data-stu-id="7296e-252">Find CLR versions</span></span>

<span data-ttu-id="7296e-253">隨 .NET Framework 安裝的 .NET Framework CLR 會分別進行版本設定。</span><span class="sxs-lookup"><span data-stu-id="7296e-253">The .NET Framework CLR installed with .NET Framework is versioned separately.</span></span> <span data-ttu-id="7296e-254">偵測 .NET Framework CLR 版本的方法有兩種：</span><span class="sxs-lookup"><span data-stu-id="7296e-254">There are two ways to detect the version of the .NET Framework CLR:</span></span>

- <span data-ttu-id="7296e-255">**Clrver.exe 工具**</span><span class="sxs-lookup"><span data-stu-id="7296e-255">**The Clrver.exe tool**</span></span>

  <span data-ttu-id="7296e-256">使用[Clr 版本工具（Clrver.exe）](../tools/clrver-exe-clr-version-tool.md) ，判斷電腦上安裝了哪些 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="7296e-256">Use the [CLR Version tool (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) to determine which versions of the CLR are installed on a computer.</span></span> <span data-ttu-id="7296e-257">開啟[Visual Studio 的開發人員命令提示字元](../tools/developer-command-prompt-for-vs.md)，然後輸入 `clrver` 。</span><span class="sxs-lookup"><span data-stu-id="7296e-257">Open the [Developer Command Prompt for Visual Studio](../tools/developer-command-prompt-for-vs.md) and enter `clrver`.</span></span>

  <span data-ttu-id="7296e-258">範例輸出：</span><span class="sxs-lookup"><span data-stu-id="7296e-258">Sample output:</span></span>

  ```console
  Versions installed on the machine:
  v2.0.50727
  v4.0.30319
  ```

- <span data-ttu-id="7296e-259">**`Environment`類別**</span><span class="sxs-lookup"><span data-stu-id="7296e-259">**The `Environment` class**</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="7296e-260">針對 .NET Framework 4.5 和更新版本，請勿使用 <xref:System.Environment.Version%2A?displayProperty=nameWithType> 屬性來偵測 CLR 的版本。</span><span class="sxs-lookup"><span data-stu-id="7296e-260">For .NET Framework 4.5 and later versions, don't use the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to detect the version of the CLR.</span></span> <span data-ttu-id="7296e-261">請改為查詢登錄，如偵測[.NET Framework 4.5 和更新版本](#detect-net-framework-45-and-later-versions)中所述。</span><span class="sxs-lookup"><span data-stu-id="7296e-261">Instead, query the registry as described in [Detect .NET Framework 4.5 and later versions](#detect-net-framework-45-and-later-versions).</span></span>
  
  01. <span data-ttu-id="7296e-262">查詢 <xref:System.Environment.Version?displayProperty=nameWithType> 屬性以擷取 <xref:System.Version> 物件。</span><span class="sxs-lookup"><span data-stu-id="7296e-262">Query the <xref:System.Environment.Version?displayProperty=nameWithType> property to retrieve a <xref:System.Version> object.</span></span>
  
      <span data-ttu-id="7296e-263">傳回的 `System.Version` 物件可識別目前執行程式碼的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="7296e-263">The returned `System.Version` object identifies the version of the runtime that's currently executing the code.</span></span> <span data-ttu-id="7296e-264">它不會傳回組件版本或已安裝在電腦上的其他執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="7296e-264">It doesn't return assembly versions or other versions of the runtime that may have been installed on the computer.</span></span>
  
      <span data-ttu-id="7296e-265">針對 .NET Framework 版本4、4.5、4.5.1 和4.5.2，傳回物件的字串表示 <xref:System.Version> 具有4.0.30319 格式。*xxxxx*，其中*xxxxx*小於42000。</span><span class="sxs-lookup"><span data-stu-id="7296e-265">For .NET Framework versions 4, 4.5, 4.5.1, and 4.5.2, the string representation of the returned <xref:System.Version> object has the form 4.0.30319.*xxxxx*, where *xxxxx* is less than 42000.</span></span> <span data-ttu-id="7296e-266">針對 .NET Framework 4.6 和更新版本，其格式為4.0.30319.42000。</span><span class="sxs-lookup"><span data-stu-id="7296e-266">For .NET Framework 4.6 and later versions, it has the form 4.0.30319.42000.</span></span>
  
  01. <span data-ttu-id="7296e-267">在您擁有**版本**物件之後，請依照下列方式查詢它：</span><span class="sxs-lookup"><span data-stu-id="7296e-267">After you have the **Version** object, query it as follows:</span></span>
  
      - <span data-ttu-id="7296e-268">針對主要版本識別項 (例如 4.0 版的 *4*)，請使用 <xref:System.Version.Major%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="7296e-268">For the major release identifier (for example, *4* for version 4.0), use the <xref:System.Version.Major%2A?displayProperty=nameWithType> property.</span></span>
  
      - <span data-ttu-id="7296e-269">針對次要版本識別項 (例如 4.0 版的 *0*)，請使用 <xref:System.Version.Minor%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="7296e-269">For the minor release identifier (for example, *0* for version 4.0), use the <xref:System.Version.Minor%2A?displayProperty=nameWithType> property.</span></span>
  
      - <span data-ttu-id="7296e-270">針對整個版本字串 (例如 *4.0.30319.18010*)，請使用 <xref:System.Version.ToString%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="7296e-270">For the entire version string (for example, *4.0.30319.18010*), use the <xref:System.Version.ToString%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="7296e-271">這個方法會傳回單一值，其反映執行程式碼的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="7296e-271">This method returns a single value that reflects the version of the runtime that's executing the code.</span></span> <span data-ttu-id="7296e-272">它不會傳回組件版本或可能已安裝在電腦上的其他執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="7296e-272">It doesn't return assembly versions or other runtime versions that may be installed on the computer.</span></span>

  <span data-ttu-id="7296e-273">下列範例使用 <xref:System.Environment.Version%2A?displayProperty=nameWithType> 屬性來擷取 CLR 版本資訊：</span><span class="sxs-lookup"><span data-stu-id="7296e-273">The following example uses the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to retrieve CLR version information:</span></span>
  
  [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
  [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a><span data-ttu-id="7296e-274">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7296e-274">See also</span></span>

- [<span data-ttu-id="7296e-275">如何：判斷已安裝的 .NET Framework 更新</span><span class="sxs-lookup"><span data-stu-id="7296e-275">How to: Determine which .NET Framework updates are installed</span></span>](how-to-determine-which-net-framework-updates-are-installed.md)
- [<span data-ttu-id="7296e-276">安裝適用於開發人員的 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7296e-276">Install the .NET Framework for developers</span></span>](../install/guide-for-developers.md)
- [<span data-ttu-id="7296e-277">.NET Framework 版本和相依性</span><span class="sxs-lookup"><span data-stu-id="7296e-277">.NET Framework versions and dependencies</span></span>](versions-and-dependencies.md)
