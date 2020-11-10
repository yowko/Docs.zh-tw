---
title: 判斷安裝的 .NET Framework 版本
description: 藉由查詢 Windows 登錄，使用程式碼、regedit.exe 或 PowerShell 來偵測電腦上所安裝的 .NET Framework 版本。
ms.date: 02/03/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
ms.openlocfilehash: 79c60c8dbc29d8985f3cfb2ffc2436539155c555
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440141"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="9b0e7-103">如何：判斷安裝的 .NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="9b0e7-103">How to: Determine which .NET Framework versions are installed</span></span>

<span data-ttu-id="9b0e7-104">使用者可以在其電腦上 [安裝](../install/index.md) 及執行多個版本的 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-104">Users can [install](../install/index.md) and run multiple versions of .NET Framework on their computers.</span></span> <span data-ttu-id="9b0e7-105">當您開發或部署應用程式時，您可能需要知道使用者電腦上安裝的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-105">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user's computer.</span></span> <span data-ttu-id="9b0e7-106">登錄包含電腦上所安裝 .NET Framework 版本的清單。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-106">The registry contains a list of the versions of .NET Framework installed on the computer.</span></span>

<span data-ttu-id="9b0e7-107">.NET Framework 是由兩個主要元件所組成，這些元件分別設定版本：</span><span class="sxs-lookup"><span data-stu-id="9b0e7-107">.NET Framework consists of two main components, which are versioned separately:</span></span>

- <span data-ttu-id="9b0e7-108">組件集合，這是為應用程式提供功能的類型與資源集合。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-108">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="9b0e7-109">.NET Framework，且元件共用相同的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-109">.NET Framework and the assemblies share the same version number.</span></span> <span data-ttu-id="9b0e7-110">例如，.NET Framework 版本包含 4.5、4.6.1 和 4.7.2。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-110">For example, .NET Framework versions include 4.5, 4.6.1, and 4.7.2.</span></span>

- <span data-ttu-id="9b0e7-111">通用語言執行平台 (CLR)，負責管理和執行應用程式的程式碼。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-111">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="9b0e7-112">單一的 CLR 版本通常會支援多個 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-112">A single CLR version typically supports multiple .NET Framework versions.</span></span> <span data-ttu-id="9b0e7-113">例如，CLR 版本4.0.30319。 *xxxxx 小於* 42000 的 *xxxxx* 支援 .NET Framework 版本4到4.5.2。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-113">For example, CLR version 4.0.30319. *xxxxx* where *xxxxx* is less than 42000, supports .NET Framework versions 4 through 4.5.2.</span></span> <span data-ttu-id="9b0e7-114">大於或等於4.0.30319.42000 版的 CLR 版本支援從 .NET Framework 4.6 開始的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-114">CLR version greater than or equal to 4.0.30319.42000 supports .NET Framework versions starting with .NET Framework 4.6.</span></span>

<span data-ttu-id="9b0e7-115">您可以使用由社區維護的工具，來協助偵測已安裝哪些 .NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="9b0e7-115">Community-maintained tools are available to help detect which .NET Framework versions are installed:</span></span>

- [https://github.com/jmalarcon/DotNetVersions](https://github.com/jmalarcon/DotNetVersions)

  <span data-ttu-id="9b0e7-116">.NET 2.0 命令列工具。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-116">A .NET 2.0 command-line tool.</span></span>

- [https://github.com/EliteLoser/DotNetVersionLister](https://github.com/EliteLoser/DotNetVersionLister)

  <span data-ttu-id="9b0e7-117">PowerShell 2.0 模組。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-117">A PowerShell 2.0 module.</span></span>

<span data-ttu-id="9b0e7-118">如需有關針對每個 .NET Framework 版本偵測已安裝之更新的詳細資訊，請參閱 [如何：判斷已安裝哪些 .NET Framework 更新](how-to-determine-which-net-framework-updates-are-installed.md)。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-118">For information about detecting the installed updates for each version of .NET Framework, see [How to: Determine which .NET Framework updates are installed](how-to-determine-which-net-framework-updates-are-installed.md).</span></span>

## <a name="detect-net-framework-45-and-later-versions"></a><span data-ttu-id="9b0e7-119">偵測 .NET Framework 4.5 和更新版本</span><span class="sxs-lookup"><span data-stu-id="9b0e7-119">Detect .NET Framework 4.5 and later versions</span></span>

<span data-ttu-id="9b0e7-120">電腦上安裝的 .NET Framework (4.5 和更新版本) 會列在 **HKEY_LOCAL_MACHINE \\ SOFTWARE \\ Microsoft \\ NET Framework Setup \\ NDP \\ v4 \\ Full** 的登錄中。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-120">The version of .NET Framework (4.5 and later) installed on a machine is listed in the registry at **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span></span> <span data-ttu-id="9b0e7-121">如果遺失 **完整** 子機碼，則不會安裝 .NET Framework 4.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-121">If the **Full** subkey is missing, then .NET Framework 4.5 or above isn't installed.</span></span>

> [!NOTE]
> <span data-ttu-id="9b0e7-122">登錄路徑中的 **NET Framework Setup** 子機碼開頭 *不* 是句點。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-122">The **NET Framework Setup** subkey in the registry path does *not* begin with a period.</span></span>

<span data-ttu-id="9b0e7-123">登錄中的 **版本 REG_DWORD 值** 代表安裝的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-123">The **Release** REG_DWORD value in the registry represents the version of .NET Framework installed.</span></span>

<a name="version_table"></a>

| <span data-ttu-id="9b0e7-124">.NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="9b0e7-124">.NET Framework version</span></span> | <span data-ttu-id="9b0e7-125">**發行** 的值</span><span class="sxs-lookup"><span data-stu-id="9b0e7-125">Value of **Release**</span></span> |
| ---------------------- | -------------------------- |
| <span data-ttu-id="9b0e7-126">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="9b0e7-126">.NET Framework 4.5</span></span>     | <span data-ttu-id="9b0e7-127">所有 Windows 作業系統：378389</span><span class="sxs-lookup"><span data-stu-id="9b0e7-127">All Windows operating systems: 378389</span></span> |
| <span data-ttu-id="9b0e7-128">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="9b0e7-128">.NET Framework 4.5.1</span></span>   | <span data-ttu-id="9b0e7-129">在 Windows 8.1 和 Windows Server 2012 R2：378675</span><span class="sxs-lookup"><span data-stu-id="9b0e7-129">On Windows 8.1 and Windows Server 2012 R2: 378675</span></span><br /><span data-ttu-id="9b0e7-130">在所有其他 Windows 作業系統上：378758</span><span class="sxs-lookup"><span data-stu-id="9b0e7-130">On all other Windows operating systems: 378758</span></span> |
| <span data-ttu-id="9b0e7-131">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="9b0e7-131">.NET Framework 4.5.2</span></span>   | <span data-ttu-id="9b0e7-132">所有 Windows 作業系統：379893</span><span class="sxs-lookup"><span data-stu-id="9b0e7-132">All Windows operating systems: 379893</span></span> |
| <span data-ttu-id="9b0e7-133">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="9b0e7-133">.NET Framework 4.6</span></span>     | <span data-ttu-id="9b0e7-134">在 Windows 10: 393295 上</span><span class="sxs-lookup"><span data-stu-id="9b0e7-134">On Windows 10: 393295</span></span><br /><span data-ttu-id="9b0e7-135">在所有其他 Windows 作業系統上：393297</span><span class="sxs-lookup"><span data-stu-id="9b0e7-135">On all other Windows operating systems: 393297</span></span> |
| <span data-ttu-id="9b0e7-136">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="9b0e7-136">.NET Framework 4.6.1</span></span>   | <span data-ttu-id="9b0e7-137">Windows 10 11 月更新系統：394254</span><span class="sxs-lookup"><span data-stu-id="9b0e7-137">On Windows 10 November Update systems: 394254</span></span><br /><span data-ttu-id="9b0e7-138">在所有其他 Windows 作業系統上 (包括 Windows 10) ：394271</span><span class="sxs-lookup"><span data-stu-id="9b0e7-138">On all other Windows operating systems (including Windows 10): 394271</span></span> |
| <span data-ttu-id="9b0e7-139">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="9b0e7-139">.NET Framework 4.6.2</span></span>   | <span data-ttu-id="9b0e7-140">Windows 10 年度更新版及 Windows Server 2016：394802</span><span class="sxs-lookup"><span data-stu-id="9b0e7-140">On Windows 10 Anniversary Update and Windows Server 2016: 394802</span></span><br /><span data-ttu-id="9b0e7-141">在所有其他 Windows 作業系統上 (包括其他 Windows 10 作業系統) ：394806</span><span class="sxs-lookup"><span data-stu-id="9b0e7-141">On all other Windows operating systems (including other Windows 10 operating systems): 394806</span></span> |
| <span data-ttu-id="9b0e7-142">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="9b0e7-142">.NET Framework 4.7</span></span>     | <span data-ttu-id="9b0e7-143">Windows 10 Creators Update：460798</span><span class="sxs-lookup"><span data-stu-id="9b0e7-143">On Windows 10 Creators Update: 460798</span></span><br /><span data-ttu-id="9b0e7-144">在所有其他 Windows 作業系統上 (包括其他 Windows 10 作業系統) ：460805</span><span class="sxs-lookup"><span data-stu-id="9b0e7-144">On all other Windows operating systems (including other Windows 10 operating systems): 460805</span></span> |
| <span data-ttu-id="9b0e7-145">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="9b0e7-145">.NET Framework 4.7.1</span></span>   | <span data-ttu-id="9b0e7-146">在 Windows 10 Fall Creators Update 和 Windows Server 上，版本1709：461308</span><span class="sxs-lookup"><span data-stu-id="9b0e7-146">On Windows 10 Fall Creators Update and Windows Server, version 1709: 461308</span></span><br/><span data-ttu-id="9b0e7-147">在所有其他 Windows 作業系統上 (包括其他 Windows 10 作業系統) ：461310</span><span class="sxs-lookup"><span data-stu-id="9b0e7-147">On all other Windows operating systems (including other Windows 10 operating systems): 461310</span></span> |
| <span data-ttu-id="9b0e7-148">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="9b0e7-148">.NET Framework 4.7.2</span></span>   | <span data-ttu-id="9b0e7-149">在 Windows 10 2018 年4月更新和 Windows Server 上，版本1803：461808</span><span class="sxs-lookup"><span data-stu-id="9b0e7-149">On Windows 10 April 2018 Update and Windows Server, version 1803: 461808</span></span><br/><span data-ttu-id="9b0e7-150">在 Windows 10 2018 年4月更新和 Windows Server 以外的所有 Windows 作業系統上，版本1803：461814</span><span class="sxs-lookup"><span data-stu-id="9b0e7-150">On all Windows operating systems other than Windows 10 April 2018 Update and Windows Server, version 1803: 461814</span></span> |
| <span data-ttu-id="9b0e7-151">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="9b0e7-151">.NET Framework 4.8</span></span>     | <span data-ttu-id="9b0e7-152">在 Windows 10 2019 年5月更新和 Windows 10 2019 年11月更新：528040</span><span class="sxs-lookup"><span data-stu-id="9b0e7-152">On Windows 10 May 2019 Update and Windows 10 November 2019 Update: 528040</span></span><br/><span data-ttu-id="9b0e7-153">在 Windows 10 2020 年5月更新：528372</span><span class="sxs-lookup"><span data-stu-id="9b0e7-153">On Windows 10 May 2020 Update: 528372</span></span><br/><span data-ttu-id="9b0e7-154">在所有其他 Windows 作業系統上 (包括其他 Windows 10 作業系統) ：528049</span><span class="sxs-lookup"><span data-stu-id="9b0e7-154">On all other Windows operating systems (including other Windows 10 operating systems): 528049</span></span> |

### <a name="minimum-version"></a><span data-ttu-id="9b0e7-155">最小版本</span><span class="sxs-lookup"><span data-stu-id="9b0e7-155">Minimum version</span></span>

<span data-ttu-id="9b0e7-156">若要判斷 .NET Framework 的 *最小* 版本是否存在，請檢查是否有大於或等於下表所列對應值的 **發行** REG_DWORD 值。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-156">To determine whether a *minimum* version of .NET Framework is present, check for a **Release** REG_DWORD value that's greater than or equal to the corresponding value listed in the following table.</span></span> <span data-ttu-id="9b0e7-157">例如，如果您的應用程式在 .NET Framework 4.8 或更新版本下執行，請測試 *大於或等於* 528040 的 **發行** REG_DWORD 值。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-157">For example, if your application runs under .NET Framework 4.8 or a later version, test for a **Release** REG_DWORD value that's *greater than or equal to* 528040.</span></span>

| <span data-ttu-id="9b0e7-158">.NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="9b0e7-158">.NET Framework version</span></span> | <span data-ttu-id="9b0e7-159">最小值</span><span class="sxs-lookup"><span data-stu-id="9b0e7-159">Minimum value</span></span> |
| ---------------------- | ------------- |
| <span data-ttu-id="9b0e7-160">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="9b0e7-160">.NET Framework 4.5</span></span>     | <span data-ttu-id="9b0e7-161">378389</span><span class="sxs-lookup"><span data-stu-id="9b0e7-161">378389</span></span> |
| <span data-ttu-id="9b0e7-162">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="9b0e7-162">.NET Framework 4.5.1</span></span>   | <span data-ttu-id="9b0e7-163">378675</span><span class="sxs-lookup"><span data-stu-id="9b0e7-163">378675</span></span> |
| <span data-ttu-id="9b0e7-164">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="9b0e7-164">.NET Framework 4.5.2</span></span>   | <span data-ttu-id="9b0e7-165">379893</span><span class="sxs-lookup"><span data-stu-id="9b0e7-165">379893</span></span> |
| <span data-ttu-id="9b0e7-166">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="9b0e7-166">.NET Framework 4.6</span></span>     | <span data-ttu-id="9b0e7-167">393295</span><span class="sxs-lookup"><span data-stu-id="9b0e7-167">393295</span></span> |
| <span data-ttu-id="9b0e7-168">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="9b0e7-168">.NET Framework 4.6.1</span></span>   | <span data-ttu-id="9b0e7-169">394254</span><span class="sxs-lookup"><span data-stu-id="9b0e7-169">394254</span></span> |
| <span data-ttu-id="9b0e7-170">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="9b0e7-170">.NET Framework 4.6.2</span></span>   | <span data-ttu-id="9b0e7-171">394802</span><span class="sxs-lookup"><span data-stu-id="9b0e7-171">394802</span></span> |
| <span data-ttu-id="9b0e7-172">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="9b0e7-172">.NET Framework 4.7</span></span>     | <span data-ttu-id="9b0e7-173">460798</span><span class="sxs-lookup"><span data-stu-id="9b0e7-173">460798</span></span> |
| <span data-ttu-id="9b0e7-174">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="9b0e7-174">.NET Framework 4.7.1</span></span>   | <span data-ttu-id="9b0e7-175">461308</span><span class="sxs-lookup"><span data-stu-id="9b0e7-175">461308</span></span> |
| <span data-ttu-id="9b0e7-176">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="9b0e7-176">.NET Framework 4.7.2</span></span>   | <span data-ttu-id="9b0e7-177">461808</span><span class="sxs-lookup"><span data-stu-id="9b0e7-177">461808</span></span> |
| <span data-ttu-id="9b0e7-178">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="9b0e7-178">.NET Framework 4.8</span></span>     | <span data-ttu-id="9b0e7-179">528040</span><span class="sxs-lookup"><span data-stu-id="9b0e7-179">528040</span></span> |

### <a name="use-registry-editor"></a><span data-ttu-id="9b0e7-180">使用登錄編輯程式</span><span class="sxs-lookup"><span data-stu-id="9b0e7-180">Use Registry Editor</span></span>

01. <span data-ttu-id="9b0e7-181">從 [開始] 功能表上，選擇 [執行]，輸入 *regedit* ，然後選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-181">From the **Start** menu, choose **Run** , enter *regedit* , and then select **OK**.</span></span>

   <span data-ttu-id="9b0e7-182"> (您必須擁有系統管理認證才能執行 regedit。 ) </span><span class="sxs-lookup"><span data-stu-id="9b0e7-182">(You must have administrative credentials to run regedit.)</span></span>

01. <span data-ttu-id="9b0e7-183">在 [登錄編輯程式] 中，開啟下列子機碼： **HKEY_LOCAL_MACHINE \\ SOFTWARE \\ Microsoft \\ NET Framework Setup \\ NDP \\ v4 \\ Full** 。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-183">In the Registry Editor, open the following subkey: **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span></span> <span data-ttu-id="9b0e7-184">如果 **完整** 的子機碼不存在，您就不會安裝 .NET Framework 4.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-184">If the **Full** subkey isn't present, then you don't have .NET Framework 4.5 or later installed.</span></span>

01. <span data-ttu-id="9b0e7-185">檢查名為 **Release** 的 REG_DWORD 專案。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-185">Check for a REG_DWORD entry named **Release**.</span></span> <span data-ttu-id="9b0e7-186">如果存在，表示您已安裝 .NET Framework 4.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-186">If it exists, then you have .NET Framework 4.5 or later installed.</span></span> <span data-ttu-id="9b0e7-187">其值會對應至特定版本的 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-187">Its value corresponds to a particular version of .NET Framework.</span></span> <span data-ttu-id="9b0e7-188">例如，在下圖中， **發行** 專案的值是528040，也就是 .NET Framework 4.8 的發行金鑰。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-188">In the following figure, for example, the value of the **Release** entry is 528040, which is the release key for .NET Framework 4.8.</span></span>

   ![.NET Framework 4.5 的登錄專案](./media/clr-installdir.png )

### <a name="use-powershell-to-check-for-a-minimum-version"></a><span data-ttu-id="9b0e7-190">使用 PowerShell 檢查最低版本</span><span class="sxs-lookup"><span data-stu-id="9b0e7-190">Use PowerShell to check for a minimum version</span></span>

<span data-ttu-id="9b0e7-191">使用 PowerShell 命令來檢查 **HKEY_LOCAL_MACHINE \\ SOFTWARE \\ Microsoft \\ NET Framework Setup \\ NDP \\ V4 \\ Full** 子機碼的 **發行** 專案值。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-191">Use PowerShell commands to check the value of the **Release** entry of the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** subkey.</span></span>

<span data-ttu-id="9b0e7-192">下列範例會檢查 **發行** 專案的值，以判斷是否已安裝 .NET Framework 4.6.2 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-192">The following examples check the value of the **Release** entry to determine whether .NET Framework 4.6.2 or later is installed.</span></span> <span data-ttu-id="9b0e7-193">如已安裝，則此程式碼會傳回 `True`；否則傳回 `False`。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-193">This code returns `True` if it's installed and `False` otherwise.</span></span>

```powershell
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

### <a name="query-the-registry-using-code"></a><span data-ttu-id="9b0e7-194">使用程式碼查詢登錄</span><span class="sxs-lookup"><span data-stu-id="9b0e7-194">Query the registry using code</span></span>

01. <span data-ttu-id="9b0e7-195">使用 <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> 和 <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> 方法來存取 Windows 登錄中的 **HKEY_LOCAL_MACHINE \\ SOFTWARE \\ Microsoft \\ NET Framework Setup \\ NDP \\ v4 \\ Full** 子機碼。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-195">Use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> methods to access the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** subkey in the Windows registry.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="9b0e7-196">如果您正在執行的應用程式是32位並在64位 Windows 中執行，則登錄路徑會與先前所列的不同。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-196">If the app you're running is 32-bit and running in 64-bit Windows, the registry paths will be different than previously listed.</span></span> <span data-ttu-id="9b0e7-197">您可以在 **HKEY_LOCAL_MACHINE \\ SOFTWARE \\ Wow6432Node \\** 子機碼中找到64位登錄。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-197">The 64-bit registry is available in the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** subkey.</span></span> <span data-ttu-id="9b0e7-198">例如，.NET Framework 4.5 的登錄子機碼是 **HKEY_LOCAL_MACHINE \\ SOFTWARE \\ Wow6432Node \\ Microsoft \\ NET Framework Setup \\ NDP \\ v4 \\ Full** 。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-198">For example, the registry subkey for .NET Framework 4.5 is **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span></span>

01. <span data-ttu-id="9b0e7-199">檢查 **發行** REG_DWORD 值，以判斷已安裝的版本。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-199">Check the **Release** REG_DWORD value to determine the installed version.</span></span> <span data-ttu-id="9b0e7-200">若要正向相容，請檢查是否有大於或等於 [.NET Framework 版本表](#version_table)中所列值的值。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-200">To be forward-compatible, check for a value greater than or equal to the value listed in the [.NET Framework version table](#version_table).</span></span>

<span data-ttu-id="9b0e7-201">下列範例會檢查登錄中 **發行** 專案的值，以尋找已安裝 .NET Framework 4.5-4.8 的版本：</span><span class="sxs-lookup"><span data-stu-id="9b0e7-201">The following example checks the value of the **Release** entry in the registry to find the versions of .NET Framework 4.5-4.8 that are installed:</span></span>

:::code language="csharp" source="snippets/csharp/versions-installed.cs" id="2":::

:::code language="vb" source="snippets/visual-basic/versions-installed.vb" id="2":::

<span data-ttu-id="9b0e7-202">此範例會顯示如下所示的輸出：</span><span class="sxs-lookup"><span data-stu-id="9b0e7-202">The example displays output like the following:</span></span>

```output
.NET Framework Version: 4.6.1
```

<span data-ttu-id="9b0e7-203">此範例遵循版本檢查的建議做法：</span><span class="sxs-lookup"><span data-stu-id="9b0e7-203">This example follows the recommended practice for version checking:</span></span>

- <span data-ttu-id="9b0e7-204">它會檢查 **Release** 項目值是否「大於或等於」已知版本機碼的值。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-204">It checks whether the value of the **Release** entry is *greater than or equal to* the value of the known release keys.</span></span>
- <span data-ttu-id="9b0e7-205">它會從最新版本依序檢查到最舊版本。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-205">It checks in order from most recent version to earliest version.</span></span>

## <a name="detect-net-framework-10-through-40"></a><span data-ttu-id="9b0e7-206">偵測 .NET Framework 1.0 至4。0</span><span class="sxs-lookup"><span data-stu-id="9b0e7-206">Detect .NET Framework 1.0 through 4.0</span></span>

<span data-ttu-id="9b0e7-207">從1.1 到 4.0 .NET Framework 的每個版本都會在 **HKEY_LOCAL_MACHINE \\ SOFTWARE \\ Microsoft \\ .net Framework 安裝 \\ NDP** 中列為子機碼。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-207">Each version of .NET Framework from 1.1 to 4.0 is listed as a subkey at **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP**.</span></span> <span data-ttu-id="9b0e7-208">下表列出每個 .NET Framework 版本的路徑。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-208">The following table lists the path to each .NET Framework version.</span></span> <span data-ttu-id="9b0e7-209">大部分的版本都有 **安裝** REG_DWORD 值，表示已 `1` 安裝此版本。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-209">For most versions, there's an **Install** REG_DWORD value of `1` to indicate this version is installed.</span></span> <span data-ttu-id="9b0e7-210">在這些子機碼中，也有包含版本字串的 REG_SZ 值 **版本** 。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-210">In these subkeys, there's also a **Version** REG_SZ value that contains a version string.</span></span>

> [!NOTE]
> <span data-ttu-id="9b0e7-211">登錄路徑中的 **NET Framework Setup** 子機碼開頭 *不* 是句點。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-211">The **NET Framework Setup** subkey in the registry path does *not* begin with a period.</span></span>

| <span data-ttu-id="9b0e7-212">Framework 版本</span><span class="sxs-lookup"><span data-stu-id="9b0e7-212">Framework Version</span></span>  | <span data-ttu-id="9b0e7-213">登錄子機碼</span><span class="sxs-lookup"><span data-stu-id="9b0e7-213">Registry Subkey</span></span> | <span data-ttu-id="9b0e7-214">值</span><span class="sxs-lookup"><span data-stu-id="9b0e7-214">Value</span></span> |
| ------------------ | --------------- | ----- |
| <span data-ttu-id="9b0e7-215">1.0</span><span class="sxs-lookup"><span data-stu-id="9b0e7-215">1.0</span></span>                | <span data-ttu-id="9b0e7-216">**HKLM \\ Software \\ Microsoft \\ 。.Netframework \\ 原則 \\ 1.0 版 \\ 3705**</span><span class="sxs-lookup"><span data-stu-id="9b0e7-216">**HKLM\\Software\\Microsoft\\.NETFramework\\Policy\\v1.0\\3705**</span></span>     | <span data-ttu-id="9b0e7-217">**安裝** REG_SZ equals `1`</span><span class="sxs-lookup"><span data-stu-id="9b0e7-217">**Install** REG_SZ equals `1`</span></span> |
| <span data-ttu-id="9b0e7-218">1.1</span><span class="sxs-lookup"><span data-stu-id="9b0e7-218">1.1</span></span>                | <span data-ttu-id="9b0e7-219">**HKLM \\ Software \\ Microsoft \\ NET Framework Setup \\ NDP \\ v 1.1.4322**</span><span class="sxs-lookup"><span data-stu-id="9b0e7-219">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v1.1.4322**</span></span>   | <span data-ttu-id="9b0e7-220">**安裝** REG_DWORD equals `1`</span><span class="sxs-lookup"><span data-stu-id="9b0e7-220">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="9b0e7-221">2.0</span><span class="sxs-lookup"><span data-stu-id="9b0e7-221">2.0</span></span>                | <span data-ttu-id="9b0e7-222">**HKLM \\ Software \\ Microsoft \\ NET Framework Setup \\ NDP \\ v 2.0.50727**</span><span class="sxs-lookup"><span data-stu-id="9b0e7-222">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v2.0.50727**</span></span>  | <span data-ttu-id="9b0e7-223">**安裝** REG_DWORD equals `1`</span><span class="sxs-lookup"><span data-stu-id="9b0e7-223">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="9b0e7-224">3.0</span><span class="sxs-lookup"><span data-stu-id="9b0e7-224">3.0</span></span>                | <span data-ttu-id="9b0e7-225">**HKLM \\ Software \\ Microsoft \\ NET Framework setup \\ NDP \\ v3.0 \\ 設定**</span><span class="sxs-lookup"><span data-stu-id="9b0e7-225">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v3.0\\Setup**</span></span> | <span data-ttu-id="9b0e7-226">**InstallSuccess** REG_DWORD equals `1`</span><span class="sxs-lookup"><span data-stu-id="9b0e7-226">**InstallSuccess** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="9b0e7-227">3.5</span><span class="sxs-lookup"><span data-stu-id="9b0e7-227">3.5</span></span>                | <span data-ttu-id="9b0e7-228">**HKLM \\ Software \\ Microsoft \\ NET Framework Setup \\ NDP \\ v 3。5**</span><span class="sxs-lookup"><span data-stu-id="9b0e7-228">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v3.5**</span></span>        | <span data-ttu-id="9b0e7-229">**安裝** REG_DWORD equals `1`</span><span class="sxs-lookup"><span data-stu-id="9b0e7-229">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="9b0e7-230">4.0 用戶端設定檔</span><span class="sxs-lookup"><span data-stu-id="9b0e7-230">4.0 Client Profile</span></span> | <span data-ttu-id="9b0e7-231">**HKLM \\ Software \\ Microsoft \\ NET Framework 設定 \\ NDP \\ v4 \\ 用戶端**</span><span class="sxs-lookup"><span data-stu-id="9b0e7-231">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Client**</span></span>  | <span data-ttu-id="9b0e7-232">**安裝** REG_DWORD equals `1`</span><span class="sxs-lookup"><span data-stu-id="9b0e7-232">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="9b0e7-233">4.0 完整設定檔</span><span class="sxs-lookup"><span data-stu-id="9b0e7-233">4.0 Full Profile</span></span>   | <span data-ttu-id="9b0e7-234">**HKLM \\ Software \\ Microsoft \\ NET Framework Setup \\ NDP \\ v4 \\ Full**</span><span class="sxs-lookup"><span data-stu-id="9b0e7-234">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**</span></span>    | <span data-ttu-id="9b0e7-235">**安裝** REG_DWORD equals `1`</span><span class="sxs-lookup"><span data-stu-id="9b0e7-235">**Install** REG_DWORD equals `1`</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="9b0e7-236">如果您正在執行的應用程式是32位並在64位 Windows 中執行，則登錄路徑會與先前所列的不同。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-236">If the app you're running is 32-bit and running in 64-bit Windows, the registry paths will be different than previously listed.</span></span> <span data-ttu-id="9b0e7-237">您可以在 **HKEY_LOCAL_MACHINE \\ SOFTWARE \\ Wow6432Node \\** 子機碼中找到64位登錄。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-237">The 64-bit registry is available in the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** subkey.</span></span> <span data-ttu-id="9b0e7-238">例如，.NET Framework 3.5 的登錄子機碼是 **HKEY_LOCAL_MACHINE \\ SOFTWARE \\ Wow6432Node \\ Microsoft \\ NET Framework Setup \\ NDP \\ v 3.5** 。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-238">For example, the registry subkey for .NET Framework 3.5 is **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v3.5**.</span></span>

<span data-ttu-id="9b0e7-239">請注意，.NET Framework 1.0 子機碼的登錄路徑與其他子機碼不同。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-239">Notice that the registry path to the .NET Framework 1.0 subkey is different from the others.</span></span>

### <a name="use-registry-editor-older-framework-versions"></a><span data-ttu-id="9b0e7-240">使用 (舊版 framework 的登錄編輯程式) </span><span class="sxs-lookup"><span data-stu-id="9b0e7-240">Use Registry Editor (older framework versions)</span></span>

01. <span data-ttu-id="9b0e7-241">從 [開始] 功能表上，選擇 [執行]，輸入 *regedit* ，然後選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-241">From the **Start** menu, choose **Run** , enter *regedit* , and then select **OK**.</span></span>

    <span data-ttu-id="9b0e7-242">您必須具有系統管理認證才能執行 regedit。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-242">You must have administrative credentials to run regedit.</span></span>

01. <span data-ttu-id="9b0e7-243">開啟符合您要檢查之版本的子機碼。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-243">Open the subkey that matches the version you want to check.</span></span> <span data-ttu-id="9b0e7-244">使用「偵測 [.NET Framework 1.0 至 4.0](#detect-net-framework-10-through-40) 」一節中的表格。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-244">Use the table in the [Detect .NET Framework 1.0 through 4.0](#detect-net-framework-10-through-40) section.</span></span>

    <span data-ttu-id="9b0e7-245">下圖顯示 .NET Framework 3.5 的子機碼及其 **版本** 值。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-245">The following figure shows the subkey and its **Version** value for .NET Framework 3.5.</span></span>

    <span data-ttu-id="9b0e7-246">![.NET Framework 3.5 的登錄專案。](./media/net-4-and-earlier.png ".NET Framework 3.5 及更早版本")</span><span class="sxs-lookup"><span data-stu-id="9b0e7-246">![The registry entry for .NET Framework 3.5.](./media/net-4-and-earlier.png ".NET Framework 3.5 and earlier versions")</span></span>

### <a name="query-the-registry-using-code-older-framework-versions"></a><span data-ttu-id="9b0e7-247">使用 (舊版 framework 的程式碼查詢登錄) </span><span class="sxs-lookup"><span data-stu-id="9b0e7-247">Query the registry using code (older framework versions)</span></span>

<span data-ttu-id="9b0e7-248">使用 <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> 類別存取 Windows 登錄中的 **HKEY_LOCAL_MACHINE \\ SOFTWARE \\ Microsoft \\ .net Framework 安裝 \\ NDP** 子機碼。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-248">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP** subkey in the Windows registry.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9b0e7-249">如果您正在執行的應用程式是32位並在64位 Windows 中執行，則登錄路徑會與先前所列的不同。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-249">If the app you're running is 32-bit and running in 64-bit Windows, the registry paths will be different than previously listed.</span></span> <span data-ttu-id="9b0e7-250">您可以在 **HKEY_LOCAL_MACHINE \\ SOFTWARE \\ Wow6432Node \\** 子機碼中找到64位登錄。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-250">The 64-bit registry is available in the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** subkey.</span></span> <span data-ttu-id="9b0e7-251">例如，.NET Framework 3.5 的登錄子機碼是 **HKEY_LOCAL_MACHINE \\ SOFTWARE \\ Wow6432Node \\ Microsoft \\ NET Framework Setup \\ NDP \\ v 3.5** 。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-251">For example, the registry subkey for .NET Framework 3.5 is **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v3.5**.</span></span>

<span data-ttu-id="9b0e7-252">下列範例會尋找已安裝的 .NET Framework 1-4 版本：</span><span class="sxs-lookup"><span data-stu-id="9b0e7-252">The following example finds the versions of .NET Framework 1-4 that are installed:</span></span>

:::code language="csharp" source="snippets/csharp/versions-installed.cs" id="1":::

:::code language="vb" source="snippets/visual-basic/versions-installed.vb" id="1":::

<span data-ttu-id="9b0e7-253">此範例會顯示如下所示的輸出：</span><span class="sxs-lookup"><span data-stu-id="9b0e7-253">The example displays output similar to the following:</span></span>

```output
v2.0.50727  2.0.50727.4927  SP2
v3.0  3.0.30729.4926  SP2
v3.5  3.5.30729.4926  SP1
v4.0
  Client  4.0.0.0
```

## <a name="find-clr-versions"></a><span data-ttu-id="9b0e7-254">尋找 CLR 版本</span><span class="sxs-lookup"><span data-stu-id="9b0e7-254">Find CLR versions</span></span>

<span data-ttu-id="9b0e7-255">隨 .NET Framework 安裝的 .NET Framework CLR 會分開建立版本。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-255">The .NET Framework CLR installed with .NET Framework is versioned separately.</span></span> <span data-ttu-id="9b0e7-256">有兩種方式可以偵測 .NET Framework CLR 的版本：</span><span class="sxs-lookup"><span data-stu-id="9b0e7-256">There are two ways to detect the version of the .NET Framework CLR:</span></span>

- <span data-ttu-id="9b0e7-257">**Clrver.exe 工具**</span><span class="sxs-lookup"><span data-stu-id="9b0e7-257">**The Clrver.exe tool**</span></span>

  <span data-ttu-id="9b0e7-258">使用 [Clr 版本工具 ( # A0) ](../tools/clrver-exe-clr-version-tool.md) 來判斷電腦上安裝的 clr 版本。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-258">Use the [CLR Version tool (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) to determine which versions of the CLR are installed on a computer.</span></span> <span data-ttu-id="9b0e7-259">開啟 [Visual Studio 的開發人員命令提示字元](../tools/developer-command-prompt-for-vs.md) ，然後輸入 `clrver` 。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-259">Open the [Developer Command Prompt for Visual Studio](../tools/developer-command-prompt-for-vs.md) and enter `clrver`.</span></span>

  <span data-ttu-id="9b0e7-260">範例輸出：</span><span class="sxs-lookup"><span data-stu-id="9b0e7-260">Sample output:</span></span>

  ```console
  Versions installed on the machine:
  v2.0.50727
  v4.0.30319
  ```

- <span data-ttu-id="9b0e7-261">**`Environment`類別**</span><span class="sxs-lookup"><span data-stu-id="9b0e7-261">**The `Environment` class**</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="9b0e7-262">針對 .NET Framework 4.5 和更新版本，請不要使用 <xref:System.Environment.Version%2A?displayProperty=nameWithType> 屬性來偵測 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-262">For .NET Framework 4.5 and later versions, don't use the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to detect the version of the CLR.</span></span> <span data-ttu-id="9b0e7-263">請改為查詢登錄，如偵測 [.NET Framework 4.5 和更新版本](#detect-net-framework-45-and-later-versions)中所述。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-263">Instead, query the registry as described in [Detect .NET Framework 4.5 and later versions](#detect-net-framework-45-and-later-versions).</span></span>

  1. <span data-ttu-id="9b0e7-264">查詢 <xref:System.Environment.Version?displayProperty=nameWithType> 屬性以擷取 <xref:System.Version> 物件。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-264">Query the <xref:System.Environment.Version?displayProperty=nameWithType> property to retrieve a <xref:System.Version> object.</span></span>

     <span data-ttu-id="9b0e7-265">傳回的 `System.Version` 物件可識別目前執行程式碼的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-265">The returned `System.Version` object identifies the version of the runtime that's currently executing the code.</span></span> <span data-ttu-id="9b0e7-266">它不會傳回組件版本或已安裝在電腦上的其他執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-266">It doesn't return assembly versions or other versions of the runtime that may have been installed on the computer.</span></span>

     <span data-ttu-id="9b0e7-267">針對 .NET Framework 4、4.5、4.5.1 和4.5.2 版，所傳回物件的字串表示 <xref:System.Version> 格式為4.0.30319。 *xxxxx* ，其中 *xxxxx* 小於42000。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-267">For .NET Framework versions 4, 4.5, 4.5.1, and 4.5.2, the string representation of the returned <xref:System.Version> object has the form 4.0.30319. *xxxxx* , where *xxxxx* is less than 42000.</span></span> <span data-ttu-id="9b0e7-268">針對 .NET Framework 4.6 和更新版本，其格式為4.0.30319.42000 版。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-268">For .NET Framework 4.6 and later versions, it has the form 4.0.30319.42000.</span></span>

  1. <span data-ttu-id="9b0e7-269">取得 **版本** 物件之後，請依照下列方式進行查詢：</span><span class="sxs-lookup"><span data-stu-id="9b0e7-269">After you have the **Version** object, query it as follows:</span></span>

     - <span data-ttu-id="9b0e7-270">針對主要版本識別項 (例如 4.0 版的 *4* )，請使用 <xref:System.Version.Major%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-270">For the major release identifier (for example, *4* for version 4.0), use the <xref:System.Version.Major%2A?displayProperty=nameWithType> property.</span></span>

     - <span data-ttu-id="9b0e7-271">針對次要版本識別項 (例如 4.0 版的 *0* )，請使用 <xref:System.Version.Minor%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-271">For the minor release identifier (for example, *0* for version 4.0), use the <xref:System.Version.Minor%2A?displayProperty=nameWithType> property.</span></span>

     - <span data-ttu-id="9b0e7-272">針對整個版本字串 (例如 *4.0.30319.18010* )，請使用 <xref:System.Version.ToString%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-272">For the entire version string (for example, *4.0.30319.18010* ), use the <xref:System.Version.ToString%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="9b0e7-273">這個方法會傳回單一值，其反映執行程式碼的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-273">This method returns a single value that reflects the version of the runtime that's executing the code.</span></span> <span data-ttu-id="9b0e7-274">它不會傳回組件版本或可能已安裝在電腦上的其他執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="9b0e7-274">It doesn't return assembly versions or other runtime versions that may be installed on the computer.</span></span>

  <span data-ttu-id="9b0e7-275">下列範例使用 <xref:System.Environment.Version%2A?displayProperty=nameWithType> 屬性來擷取 CLR 版本資訊：</span><span class="sxs-lookup"><span data-stu-id="9b0e7-275">The following example uses the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to retrieve CLR version information:</span></span>

  ```csharp
  Console.WriteLine($"Version: {Environment.Version}");
  ```

  ```vb
  Console.WriteLine($"Version: {Environment.Version}")
  ```

  <span data-ttu-id="9b0e7-276">此範例會顯示如下所示的輸出：</span><span class="sxs-lookup"><span data-stu-id="9b0e7-276">The example displays output similar to the following:</span></span>

  ```output
  Version: 4.0.30319.18010
  ```

## <a name="see-also"></a><span data-ttu-id="9b0e7-277">請參閱</span><span class="sxs-lookup"><span data-stu-id="9b0e7-277">See also</span></span>

- [<span data-ttu-id="9b0e7-278">如何：判斷安裝的 .NET Framework 更新</span><span class="sxs-lookup"><span data-stu-id="9b0e7-278">How to: Determine which .NET Framework updates are installed</span></span>](how-to-determine-which-net-framework-updates-are-installed.md)
- [<span data-ttu-id="9b0e7-279">安裝適用于開發人員的 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9b0e7-279">Install .NET Framework for developers</span></span>](../install/guide-for-developers.md)
- [<span data-ttu-id="9b0e7-280">.NET Framework 版本和相依性</span><span class="sxs-lookup"><span data-stu-id="9b0e7-280">.NET Framework versions and dependencies</span></span>](versions-and-dependencies.md)
