---
title: 作法：判斷安裝的 .NET Framework 版本
ms.date: 03/18/2019
dev_langs:
- csharp
- vb
ms.custom: updateeachrelease
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8b7c7704c4f417ef16d3a79fa6d955265e42cf14
ms.sourcegitcommit: e994e47d3582bf09ae487ecbd53c0dac30aebaf7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2019
ms.locfileid: "58262444"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="2dc72-102">作法：判斷安裝的 .NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="2dc72-102">How to: Determine which .NET Framework versions are installed</span></span>

<span data-ttu-id="2dc72-103">使用者可以在電腦上[安裝](https://docs.microsoft.com/dotnet/framework/install)及執行多個版本的 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="2dc72-103">Users can [install](https://docs.microsoft.com/dotnet/framework/install) and run multiple versions of the .NET Framework on their computers.</span></span> <span data-ttu-id="2dc72-104">當您開發或部署應用程式時，您可能需要知道使用者電腦上安裝的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="2dc72-104">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user’s computer.</span></span> 

<span data-ttu-id="2dc72-105">.NET Framework 包含兩個主要元件，各有各的版本控制：</span><span class="sxs-lookup"><span data-stu-id="2dc72-105">The .NET Framework consists of two main components, which are versioned separately:</span></span>  
  
- <span data-ttu-id="2dc72-106">組件集合，這是為應用程式提供功能的類型與資源集合。</span><span class="sxs-lookup"><span data-stu-id="2dc72-106">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="2dc72-107">.NET Framework 和組件會共用相同的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="2dc72-107">The .NET Framework and assemblies share the same version number.</span></span>  
  
- <span data-ttu-id="2dc72-108">通用語言執行平台 (CLR)，負責管理和執行應用程式的程式碼。</span><span class="sxs-lookup"><span data-stu-id="2dc72-108">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="2dc72-109">CLR 是透過自己的版本號碼加以識別 (請參閱[版本和相依性](~/docs/framework/migration-guide/versions-and-dependencies.md))。</span><span class="sxs-lookup"><span data-stu-id="2dc72-109">The CLR is identified by its own version number (see [Versions and Dependencies](~/docs/framework/migration-guide/versions-and-dependencies.md)).</span></span>  

> [!NOTE]
> <span data-ttu-id="2dc72-110">每一個新的 .NET Framework 版本都會保留舊版的功能並增加新的功能。</span><span class="sxs-lookup"><span data-stu-id="2dc72-110">Each new version of the .NET Framework retains features from the previous versions and adds new features.</span></span> <span data-ttu-id="2dc72-111">您可同時在一部電腦上載入多個版本的 .NET Framework，這表示您可以安裝 .NET Framework，卻不必解除安裝舊版。</span><span class="sxs-lookup"><span data-stu-id="2dc72-111">You can load multiple versions of the .NET Framework on a single computer at the same time, which means that you can install the .NET Framework without having to uninstall previous versions.</span></span> <span data-ttu-id="2dc72-112">一般而言，您不應該解除安裝舊版的 .NET Framework，因為您使用的應用程式可能依賴某個特定版本，而若移除該版本則應用程式可能會中斷。</span><span class="sxs-lookup"><span data-stu-id="2dc72-112">In general, you shouldn't uninstall previous versions of the .NET Framework, because an application you use may depend on a specific version and may break if that version is removed.</span></span>
>
> <span data-ttu-id="2dc72-113">.NET Framework 版本和 CLR 版本之間有差異：</span><span class="sxs-lookup"><span data-stu-id="2dc72-113">There is a difference between the .NET Framework version and the CLR version:</span></span> 
> - <span data-ttu-id="2dc72-114">.NET Framework 版本是以構成 .NET Framework Class Library 的組件集為基礎。</span><span class="sxs-lookup"><span data-stu-id="2dc72-114">The .NET Framework version is based on the set of assemblies that form the .NET Framework class library.</span></span> <span data-ttu-id="2dc72-115">例如，.NET Framework 版本包含 4.5、4.6.1 和 4.7.2。</span><span class="sxs-lookup"><span data-stu-id="2dc72-115">For example, .NET Framework versions include 4.5, 4.6.1, and 4.7.2.</span></span> 
>- <span data-ttu-id="2dc72-116">CLR 版本是以 .NET Framework 應用程式執行所在的執行階段為基礎。</span><span class="sxs-lookup"><span data-stu-id="2dc72-116">The CLR version is based on the runtime on which .NET Framework applications execute.</span></span> <span data-ttu-id="2dc72-117">單一的 CLR 版本通常會支援多個 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="2dc72-117">A single CLR version typically supports multiple .NET Framework versions.</span></span> <span data-ttu-id="2dc72-118">例如，CLR 4.0.30319.*xxxxx* 版支援 .NET Framework 4 到 4.5.2 版，而 CLR 4.0.30319.42000 版支援從 .NET Framework 4.6 起的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="2dc72-118">For example, CLR version 4.0.30319.*xxxxx* supports .NET Framework versions 4 through 4.5.2 and CLR version 4.0.30319.42000 supports .NET Framework versions starting with .NET Framework 4.6.</span></span> 
>
> <span data-ttu-id="2dc72-119">如需版本的詳細資訊，請參閱 [.NET Framework 版本和相依性](versions-and-dependencies.md)。</span><span class="sxs-lookup"><span data-stu-id="2dc72-119">For more information about versions, see [.NET Framework versions and dependencies](versions-and-dependencies.md).</span></span>


<span data-ttu-id="2dc72-120">您可以存取登錄來取得電腦上安裝的 .NET Framework 版本清單。</span><span class="sxs-lookup"><span data-stu-id="2dc72-120">To get a list of the .NET Framework versions installed on a computer, you access the registry.</span></span> <span data-ttu-id="2dc72-121">您可以使用登錄編輯程式來檢視登錄，或使用程式碼來查詢登錄：</span><span class="sxs-lookup"><span data-stu-id="2dc72-121">You can either use the Registry Editor to view the registry or use code to query it:</span></span>
 
- <span data-ttu-id="2dc72-122">尋找新版的 .NET Framework (4.5 和更新版本)：</span><span class="sxs-lookup"><span data-stu-id="2dc72-122">Find newer .NET Framework versions (4.5 and later):</span></span> 
     - [<span data-ttu-id="2dc72-123">使用登錄編輯程式尋找 .NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="2dc72-123">Use the Registry Editor to find .NET Framework versions</span></span>](#net_b)  
     - [<span data-ttu-id="2dc72-124">使用程式碼查詢登錄以取得 .NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="2dc72-124">Use code to query the registry for .NET Framework versions</span></span>](#net_d)  
     - [<span data-ttu-id="2dc72-125">使用 PowerShell 查詢登錄以取得 .NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="2dc72-125">Use PowerShell to query the registry for .NET Framework versions</span></span>](#ps_a)
 - <span data-ttu-id="2dc72-126">尋找舊版的 .NET Framework (1&#8211;4)：</span><span class="sxs-lookup"><span data-stu-id="2dc72-126">Find older .NET Framework versions (1&#8211;4):</span></span>
     - [<span data-ttu-id="2dc72-127">使用登錄編輯程式尋找 .NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="2dc72-127">Use the Registry Editor to find .NET Framework versions</span></span>](#net_a)
     - [<span data-ttu-id="2dc72-128">使用程式碼查詢登錄以取得 .NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="2dc72-128">Use code to query the registry for .NET Framework versions</span></span>](#net_c)   

<span data-ttu-id="2dc72-129">使用工具或程式碼取得安裝在電腦上的 CLR 版本清單：</span><span class="sxs-lookup"><span data-stu-id="2dc72-129">To get a list of the CLR versions installed on a computer, use a tool or code:</span></span>  
  
 - [<span data-ttu-id="2dc72-130">使用 Clrver 工具</span><span class="sxs-lookup"><span data-stu-id="2dc72-130">Use the Clrver tool</span></span>](#clr_a)  
 - [<span data-ttu-id="2dc72-131">使用程式碼查詢 Environment 類別</span><span class="sxs-lookup"><span data-stu-id="2dc72-131">Use code to query the Environment class</span></span>](#clr_b)  

<span data-ttu-id="2dc72-132">如需偵測每一版 .NET Framework 已安裝更新的資訊，請參閱[如何：判斷已安裝的 .NET Framework 更新](how-to-determine-which-net-framework-updates-are-installed.md)。</span><span class="sxs-lookup"><span data-stu-id="2dc72-132">For information about detecting the installed updates for each version of the .NET Framework, see [How to: Determine which .NET Framework updates are installed](how-to-determine-which-net-framework-updates-are-installed.md).</span></span> 
  

## <a name="find-newer-net-framework-versions-45-and-later"></a><span data-ttu-id="2dc72-133">尋找新版的 .NET Framework (4.5 和更新版本)</span><span class="sxs-lookup"><span data-stu-id="2dc72-133">Find newer .NET Framework versions (4.5 and later)</span></span>

<a name="net_b"></a> 
### <a name="find-net-framework-versions-45-and-later-in-the-registry"></a><span data-ttu-id="2dc72-134">在登錄中尋找 .NET Framework 4.5 和更新版本</span><span class="sxs-lookup"><span data-stu-id="2dc72-134">Find .NET Framework versions 4.5 and later in the registry</span></span>

1. <span data-ttu-id="2dc72-135">從 [開始] 功能表上，選擇 [執行]，輸入 *regedit*，然後選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="2dc72-135">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

     <span data-ttu-id="2dc72-136">您必須具有系統管理認證才能執行 regedit。</span><span class="sxs-lookup"><span data-stu-id="2dc72-136">You must have administrative credentials to run regedit.</span></span>

2. <span data-ttu-id="2dc72-137">在 [登錄編輯程式] 中，開啟下列子機碼：**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full**。</span><span class="sxs-lookup"><span data-stu-id="2dc72-137">In the Registry Editor, open the following subkey: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full**.</span></span> <span data-ttu-id="2dc72-138">如果 **Full** 子機碼不存在，即表示未安裝 .NET Framework 4.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="2dc72-138">If the **Full** subkey isn't present, then you don't have the .NET Framework 4.5 or later installed.</span></span>

    > [!NOTE]
    > <span data-ttu-id="2dc72-139">登錄中的 **NET Framework Setup** 資料夾不是以英文句號開頭。</span><span class="sxs-lookup"><span data-stu-id="2dc72-139">The **NET Framework Setup** folder in the registry does not begin with a period.</span></span>

3. <span data-ttu-id="2dc72-140">檢查是否有名為 **Release** 的 DWORD 項目。</span><span class="sxs-lookup"><span data-stu-id="2dc72-140">Check for a DWORD entry named **Release**.</span></span> <span data-ttu-id="2dc72-141">若有，則表示已安裝 .NET Framework 4.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="2dc72-141">If it exists, then you have .NET Framework 4.5 or later versions installed.</span></span> <span data-ttu-id="2dc72-142">其值為對應至 .NET Framework 特定版本的版本機碼。</span><span class="sxs-lookup"><span data-stu-id="2dc72-142">Its value is a release key that corresponds to a particular version of the .NET Framework.</span></span> <span data-ttu-id="2dc72-143">例如，下圖中 **Release** 項目的值是 *378389*，也就是 .NET Framework 4.5 的版本機碼。</span><span class="sxs-lookup"><span data-stu-id="2dc72-143">In the following figure, for example, the value of the **Release** entry is *378389*, which is the release key for .NET Framework 4.5.</span></span> 

     <span data-ttu-id="2dc72-144">![.NET Framework 4.5 的登錄項目](media/clr-installdir.png ".NET Framework 4.5 的登錄項目")</span><span class="sxs-lookup"><span data-stu-id="2dc72-144">![Registry entry for the .NET Framework 4.5](media/clr-installdir.png "Registry entry for the .NET Framework 4.5")</span></span>

<span data-ttu-id="2dc72-145">下表列出每個 .NET Framework 版本 **Release** 項目的最小值。</span><span class="sxs-lookup"><span data-stu-id="2dc72-145">The following table lists the minimum value of the **Release** entry for each .NET Framework version.</span></span> <span data-ttu-id="2dc72-146">您可以依照下列方式使用這些值：</span><span class="sxs-lookup"><span data-stu-id="2dc72-146">You can use these values as follows:</span></span>

- <span data-ttu-id="2dc72-147">若要判斷最低的 .NET Framework 版本是否存在，請測試登錄中所找到 **Release** DWORD 值是否「大於或等於」資料表中所列的值。</span><span class="sxs-lookup"><span data-stu-id="2dc72-147">To determine whether a minimum .NET Framework version is present, test whether the **Release** DWORD value found in the registry is *greater than or equal to* the value listed in the table.</span></span> <span data-ttu-id="2dc72-148">例如，如果您的應用程式需要 .NET Framework 4.7 或更新版本，您要測試是否有 *460798* 的最低版本機碼值。</span><span class="sxs-lookup"><span data-stu-id="2dc72-148">For example, if your application requires the .NET Framework 4.7 or later, you test for a minimum release key value of *460798*.</span></span>

- <span data-ttu-id="2dc72-149">若要測試多個版本，請從最新的 .NET Framework 版本開始，然後依序回推每個舊版進行測試。</span><span class="sxs-lookup"><span data-stu-id="2dc72-149">To test for multiple versions, begin with the latest .NET Framework version, and then test for each successive earlier version.</span></span>

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

<a name="version_table"></a>

|<span data-ttu-id="2dc72-150">.NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="2dc72-150">.NET Framework version</span></span>|<span data-ttu-id="2dc72-151">Release DWORD 的值</span><span class="sxs-lookup"><span data-stu-id="2dc72-151">Value of the Release DWORD</span></span>|
|--------------------------------|-------------|
|<span data-ttu-id="2dc72-152">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="2dc72-152">.NET Framework 4.5</span></span>|<span data-ttu-id="2dc72-153">378389</span><span class="sxs-lookup"><span data-stu-id="2dc72-153">378389</span></span>|
|<span data-ttu-id="2dc72-154">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="2dc72-154">.NET Framework 4.5.1</span></span>|<span data-ttu-id="2dc72-155">378675</span><span class="sxs-lookup"><span data-stu-id="2dc72-155">378675</span></span>|
|<span data-ttu-id="2dc72-156">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="2dc72-156">.NET Framework 4.5.2</span></span>|<span data-ttu-id="2dc72-157">379893</span><span class="sxs-lookup"><span data-stu-id="2dc72-157">379893</span></span>|
|<span data-ttu-id="2dc72-158">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="2dc72-158">.NET Framework 4.6</span></span>|<span data-ttu-id="2dc72-159">393295</span><span class="sxs-lookup"><span data-stu-id="2dc72-159">393295</span></span>|
|<span data-ttu-id="2dc72-160">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="2dc72-160">.NET Framework 4.6.1</span></span>|<span data-ttu-id="2dc72-161">394254</span><span class="sxs-lookup"><span data-stu-id="2dc72-161">394254</span></span>|
|<span data-ttu-id="2dc72-162">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="2dc72-162">.NET Framework 4.6.2</span></span>|<span data-ttu-id="2dc72-163">394802</span><span class="sxs-lookup"><span data-stu-id="2dc72-163">394802</span></span>|
|<span data-ttu-id="2dc72-164">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="2dc72-164">.NET Framework 4.7</span></span>|<span data-ttu-id="2dc72-165">460798</span><span class="sxs-lookup"><span data-stu-id="2dc72-165">460798</span></span>|
|<span data-ttu-id="2dc72-166">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="2dc72-166">.NET Framework 4.7.1</span></span>|<span data-ttu-id="2dc72-167">461308</span><span class="sxs-lookup"><span data-stu-id="2dc72-167">461308</span></span>|
|<span data-ttu-id="2dc72-168">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="2dc72-168">.NET Framework 4.7.2</span></span>|<span data-ttu-id="2dc72-169">461808</span><span class="sxs-lookup"><span data-stu-id="2dc72-169">461808</span></span>|

<span data-ttu-id="2dc72-170">如需特定 Windows 作業系統版本的 .NET Framework 版本機碼完整資料表，請參閱 [.NET Framework 版本機碼和 Windows 作業系統版本](release-keys-and-os-versions.md)。</span><span class="sxs-lookup"><span data-stu-id="2dc72-170">For a complete table of release keys for the .NET Framework for specific Windows operating system versions, see [.NET Framework release keys and Windows operating system versions](release-keys-and-os-versions.md).</span></span>


<a name="net_d"></a> 
### <a name="find-net-framework-versions-45-and-later-with-code"></a><span data-ttu-id="2dc72-171">使用程式碼尋找 .NET Framework 4.5 和更新版本</span><span class="sxs-lookup"><span data-stu-id="2dc72-171">Find .NET Framework versions 4.5 and later with code</span></span>

1. <span data-ttu-id="2dc72-172">使用 <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> 和 <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> 方法存取 Windows 登錄中的 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** 子機碼。</span><span class="sxs-lookup"><span data-stu-id="2dc72-172">Use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> methods to access the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** subkey in the Windows registry.</span></span>

    <span data-ttu-id="2dc72-173">**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** 子機碼中存在 **Release** DWORD 項目表示 .NET Framework 4.5 或更新版本已安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="2dc72-173">The existence of the **Release** DWORD entry in the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** subkey indicates that the .NET Framework 4.5 or a later version is installed on a computer.</span></span> 

2. <span data-ttu-id="2dc72-174">檢查 **Release** 項目的值，判斷已安裝的版本。</span><span class="sxs-lookup"><span data-stu-id="2dc72-174">Check the value of the **Release** entry to determine the installed version.</span></span> <span data-ttu-id="2dc72-175">若要正向相容，請檢查是否有大於或等於 [.NET Framework 版本表](#version_table)中所列值的值。</span><span class="sxs-lookup"><span data-stu-id="2dc72-175">To be forward-compatible, check for a value greater than or equal to the value listed in the [.NET Framework version table](#version_table).</span></span>

<span data-ttu-id="2dc72-176">下列範例會檢查登錄中的 **Release** 項目值，尋找已安裝的 .NET Framework 4.5 和更新版本：</span><span class="sxs-lookup"><span data-stu-id="2dc72-176">The following example checks the value of the **Release** entry in the registry to find the .NET Framework 4.5 and later versions that are installed:</span></span>

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

<span data-ttu-id="2dc72-177">此範例遵循版本檢查的建議做法：</span><span class="sxs-lookup"><span data-stu-id="2dc72-177">This example follows the recommended practice for version checking:</span></span>

- <span data-ttu-id="2dc72-178">它會檢查 **Release** 項目值是否「大於或等於」已知版本機碼的值。</span><span class="sxs-lookup"><span data-stu-id="2dc72-178">It checks whether the value of the **Release** entry is *greater than or equal to* the value of the known release keys.</span></span>

- <span data-ttu-id="2dc72-179">它會從最新版本依序檢查到最舊版本。</span><span class="sxs-lookup"><span data-stu-id="2dc72-179">It checks in order from most recent version to earliest version.</span></span>

<a name="ps_a"></a> 
### <a name="check-for-a-minimum-required-net-framework-version-45-and-later-with-powershell"></a><span data-ttu-id="2dc72-180">使用 PowerShell 檢查 .NET Framework 最低版本需求 (4.5 及更新版本)</span><span class="sxs-lookup"><span data-stu-id="2dc72-180">Check for a minimum-required .NET Framework version (4.5 and later) with PowerShell</span></span>

- <span data-ttu-id="2dc72-181">使用 PowerShell 命令檢查 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** 子機碼的 **Release** 項目值。</span><span class="sxs-lookup"><span data-stu-id="2dc72-181">Use PowerShell commands to check the value of the **Release** entry of the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** subkey.</span></span>

<span data-ttu-id="2dc72-182">下列範例會檢查 **Release** 項目值，以判斷是否安裝了 .NET Framework 4.6.2 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="2dc72-182">The following examples check the value of the **Release** entry to determine whether the .NET Framework 4.6.2 or later is installed.</span></span> <span data-ttu-id="2dc72-183">如已安裝，則此程式碼會傳回 `True`；否則傳回 `False`。</span><span class="sxs-lookup"><span data-stu-id="2dc72-183">This code returns `True` if it's installed and `False` otherwise.</span></span>

```PowerShell
# PowerShell 5
 Get-ChildItem 'HKLM:\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\' |  Get-ItemPropertyValue -Name Release | Foreach-Object { $_ -ge 394802 } 
 ```

```PowerShell
# PowerShell 4
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -gt 394802
```

<span data-ttu-id="2dc72-184">若要檢查不同的所需 .NET Framework 最低版本，請以 [.NET Framework 版本表](#version_table)的 **Release** 值取代這些範例中的 *394802*。</span><span class="sxs-lookup"><span data-stu-id="2dc72-184">To check for a different minimum-required .NET Framework version, replace *394802* in these examples with a **Release** value from the [.NET Framework version table](#version_table).</span></span>

## <a name="find-older-net-framework-versions-182114"></a><span data-ttu-id="2dc72-185">尋找舊版的 .NET Framework (1&#8211;4)</span><span class="sxs-lookup"><span data-stu-id="2dc72-185">Find older .NET Framework versions (1&#8211;4)</span></span>

<a name="net_a"></a>
### <a name="find-net-framework-versions-182114-in-the-registry"></a><span data-ttu-id="2dc72-186">在登錄中尋找 .NET Framework 1&#8211;4 版</span><span class="sxs-lookup"><span data-stu-id="2dc72-186">Find .NET Framework versions 1&#8211;4 in the registry</span></span> 
  
1. <span data-ttu-id="2dc72-187">從 [開始] 功能表上，選擇 [執行]，輸入 *regedit*，然後選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="2dc72-187">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>
  
    <span data-ttu-id="2dc72-188">您必須具有系統管理認證才能執行 regedit。</span><span class="sxs-lookup"><span data-stu-id="2dc72-188">You must have administrative credentials to run regedit.</span></span>  

2. <span data-ttu-id="2dc72-189">在 [登錄編輯程式] 中，開啟下列子機碼：**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP**：</span><span class="sxs-lookup"><span data-stu-id="2dc72-189">In the Registry Editor, open the following subkey: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP**:</span></span>  

    - <span data-ttu-id="2dc72-190">針對 .NET Framework 1.1 到 3.5 版，每個安裝的版本都會列為 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP** 子機碼下的子機碼。</span><span class="sxs-lookup"><span data-stu-id="2dc72-190">For .NET Framework versions 1.1 through 3.5, each installed version is listed as a subkey under the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP** subkey.</span></span> <span data-ttu-id="2dc72-191">例如，**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.5**。</span><span class="sxs-lookup"><span data-stu-id="2dc72-191">For example, **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.5**.</span></span> <span data-ttu-id="2dc72-192">版本號碼儲存為版本子機碼 **Version** 項目中的值。</span><span class="sxs-lookup"><span data-stu-id="2dc72-192">The version number is stored as a value in the version subkey's **Version** entry.</span></span> 
     
    - <span data-ttu-id="2dc72-193">以 .NET Framework 4 為例，**Version** 項目位在 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client** 及/或 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full** 子機碼下。</span><span class="sxs-lookup"><span data-stu-id="2dc72-193">For .NET Framework 4, the **Version** entry is under the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client** subkey, the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full** subkey, or under both subkeys.</span></span>

    > [!NOTE]
    > <span data-ttu-id="2dc72-194">登錄中的 **NET Framework Setup** 資料夾不是以英文句號開頭。</span><span class="sxs-lookup"><span data-stu-id="2dc72-194">The **NET Framework Setup** folder in the registry does not begin with a period.</span></span>

    <span data-ttu-id="2dc72-195">下圖顯示 .NET Framework 3.5 的子機碼及其 **Version** 項目。</span><span class="sxs-lookup"><span data-stu-id="2dc72-195">The following figure shows the subkey and its **Version** entry for the .NET Framework 3.5.</span></span>

    <span data-ttu-id="2dc72-196">![.NET Framework 3.5 的登錄項目。](media/net-4-and-earlier.png ".NET framework 3.5 和舊版")</span><span class="sxs-lookup"><span data-stu-id="2dc72-196">![The registry entry for the .NET Framework 3.5.](media/net-4-and-earlier.png ".NET Framework 3.5 and earlier versions")</span></span>

<a name="net_c"></a> 
### <a name="find-net-framework-versions-182114-with-code"></a><span data-ttu-id="2dc72-197">使用程式碼尋找 .NET Framework 1&#8211;4 版</span><span class="sxs-lookup"><span data-stu-id="2dc72-197">Find .NET Framework versions 1&#8211;4 with code</span></span>

- <span data-ttu-id="2dc72-198">使用 <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> 類別存取 Windows 登錄中的 **HKEY_LOCAL_MACHINE\Software\Microsoft\NET Framework Setup\NDP** 子機碼。</span><span class="sxs-lookup"><span data-stu-id="2dc72-198">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the **HKEY_LOCAL_MACHINE\Software\Microsoft\NET Framework Setup\NDP** subkey in the Windows registry.</span></span>

<span data-ttu-id="2dc72-199">下列範例會尋找已安裝的 .NET Framework 1&#8211;4 版：</span><span class="sxs-lookup"><span data-stu-id="2dc72-199">The following example finds the .NET Framework 1&#8211;4 versions that are installed:</span></span>

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]


## <a name="find-clr-versions"></a><span data-ttu-id="2dc72-200">尋找 CLR 版本</span><span class="sxs-lookup"><span data-stu-id="2dc72-200">Find CLR versions</span></span>
  
<a name="clr_a"></a> 
### <a name="find-the-current-clr-version-with-clrverexe"></a><span data-ttu-id="2dc72-201">使用 Clrver.exe 尋找目前的 CLR 版本</span><span class="sxs-lookup"><span data-stu-id="2dc72-201">Find the current CLR version with Clrver.exe</span></span>

<span data-ttu-id="2dc72-202">使用 [CLR 版本工具 (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) 以判斷電腦上安裝了哪些 CLR 版本：</span><span class="sxs-lookup"><span data-stu-id="2dc72-202">Use the [CLR Version tool (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) to determine which versions of the CLR are installed on a computer:</span></span>

- <span data-ttu-id="2dc72-203">從 [Visual Studio 的開發人員命令提示字元](https://docs.microsoft.com/dotnet/framework/tools/developer-command-prompt-for-vs)輸入 `clrver`。</span><span class="sxs-lookup"><span data-stu-id="2dc72-203">From a [Developer Command Prompt for Visual Studio](https://docs.microsoft.com/dotnet/framework/tools/developer-command-prompt-for-vs), enter `clrver`.</span></span>

    <span data-ttu-id="2dc72-204">範例輸出：</span><span class="sxs-lookup"><span data-stu-id="2dc72-204">Sample output:</span></span>

    ```console
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

<a name="clr_b"></a> 
### <a name="find-the-current-clr-version-with-the-environment-class"></a><span data-ttu-id="2dc72-205">使用環境類別尋找目前的 CLR 版本</span><span class="sxs-lookup"><span data-stu-id="2dc72-205">Find the current CLR version with the Environment class</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2dc72-206">針對 .NET Framework 4.5 和更新版本，請不要使用 <xref:System.Environment.Version%2A?displayProperty=nameWithType> 屬性偵測 CLR 的版本。</span><span class="sxs-lookup"><span data-stu-id="2dc72-206">For the .NET Framework 4.5 and later versions, don't use the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to detect the version of the CLR.</span></span> <span data-ttu-id="2dc72-207">請依[使用程式碼尋找 .NET Framework 4.5 和更新版本](#net_d)中所述，改查詢登錄。</span><span class="sxs-lookup"><span data-stu-id="2dc72-207">Instead, query the registry as described in [Find .NET Framework versions 4.5 and later with code](#net_d).</span></span>

1. <span data-ttu-id="2dc72-208">查詢 <xref:System.Environment.Version?displayProperty=nameWithType> 屬性以擷取 <xref:System.Version> 物件。</span><span class="sxs-lookup"><span data-stu-id="2dc72-208">Query the <xref:System.Environment.Version?displayProperty=nameWithType> property to retrieve a <xref:System.Version> object.</span></span> 

    <span data-ttu-id="2dc72-209">傳回的 `System.Version` 物件可識別目前執行程式碼的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="2dc72-209">The returned `System.Version` object identifies the version of the runtime that's currently executing the code.</span></span> <span data-ttu-id="2dc72-210">它不會傳回組件版本或已安裝在電腦上的其他執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="2dc72-210">It doesn't return assembly versions or other versions of the runtime that may have been installed on the computer.</span></span>

    <span data-ttu-id="2dc72-211">針對 .NET Framework 4、4.5、4.5.1 和 4.5.2 版，所傳回 <xref:System.Version> 物件的字串表示格式為 4.0.30319.*xxxxx*。</span><span class="sxs-lookup"><span data-stu-id="2dc72-211">For the .NET Framework versions 4, 4.5, 4.5.1, and 4.5.2, the string representation of the returned <xref:System.Version> object has the form 4.0.30319.*xxxxx*.</span></span> <span data-ttu-id="2dc72-212">針對 .NET Framework 4.6 和更新版本，其格式為 4.0.30319.42000。</span><span class="sxs-lookup"><span data-stu-id="2dc72-212">For the .NET Framework 4.6 and later versions, it has the form 4.0.30319.42000.</span></span>    

2. <span data-ttu-id="2dc72-213">取得 `Version` 物件之後，如下所示來加以查詢：</span><span class="sxs-lookup"><span data-stu-id="2dc72-213">After you have the `Version` object, query it as follows:</span></span>

   - <span data-ttu-id="2dc72-214">針對主要版本識別項 (例如 4.0 版的 *4*)，請使用 <xref:System.Version.Major%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="2dc72-214">For the major release identifier (for example, *4* for version 4.0), use the <xref:System.Version.Major%2A?displayProperty=nameWithType> property.</span></span>

   - <span data-ttu-id="2dc72-215">針對次要版本識別項 (例如 4.0 版的 *0*)，請使用 <xref:System.Version.Minor%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="2dc72-215">For the minor release identifier (for example, *0* for version 4.0), use the <xref:System.Version.Minor%2A?displayProperty=nameWithType> property.</span></span>

   - <span data-ttu-id="2dc72-216">針對整個版本字串 (例如 *4.0.30319.18010*)，請使用 <xref:System.Version.ToString%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="2dc72-216">For the entire version string (for example, *4.0.30319.18010*), use the <xref:System.Version.ToString%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="2dc72-217">這個方法會傳回單一值，其反映執行程式碼的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="2dc72-217">This method returns a single value that reflects the version of the runtime that's executing the code.</span></span> <span data-ttu-id="2dc72-218">它不會傳回組件版本或可能已安裝在電腦上的其他執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="2dc72-218">It doesn't return assembly versions or other runtime versions that may be installed on the computer.</span></span>



<span data-ttu-id="2dc72-219">下列範例使用 <xref:System.Environment.Version%2A?displayProperty=nameWithType> 屬性來擷取 CLR 版本資訊：</span><span class="sxs-lookup"><span data-stu-id="2dc72-219">The following example uses the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to retrieve CLR version information:</span></span>

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a><span data-ttu-id="2dc72-220">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2dc72-220">See also</span></span>

- [<span data-ttu-id="2dc72-221">如何：判斷安裝的 .NET Framework 更新</span><span class="sxs-lookup"><span data-stu-id="2dc72-221">How to: Determine which .NET Framework updates are installed</span></span>](how-to-determine-which-net-framework-updates-are-installed.md)
- [<span data-ttu-id="2dc72-222">安裝適用於開發人員的 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2dc72-222">Install the .NET Framework for developers</span></span>](../install/guide-for-developers.md)
- [<span data-ttu-id="2dc72-223">.NET Framework 版本和相依性</span><span class="sxs-lookup"><span data-stu-id="2dc72-223">.NET Framework versions and dependencies</span></span>](versions-and-dependencies.md)
