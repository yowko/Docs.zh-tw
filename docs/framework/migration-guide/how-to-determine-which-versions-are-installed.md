---
title: 如何：判斷安裝的 .NET Framework 版本
ms.date: 04/10/2018
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
ms.openlocfilehash: 1874d5512f04f22b9c53bdc9e92d0c96e45d21c8
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47199708"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="fa713-102">如何：判斷安裝的 .NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="fa713-102">How to: Determine which .NET Framework versions are installed</span></span>

<span data-ttu-id="fa713-103">使用者可以在電腦上安裝及執行多個版本的 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="fa713-103">Users can install and run multiple versions of the .NET Framework on their computers.</span></span> <span data-ttu-id="fa713-104">當您開發或部署應用程式時，您可能需要知道使用者電腦上安裝的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="fa713-104">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user’s computer.</span></span> <span data-ttu-id="fa713-105">請注意，.NET Framework 包含兩個主要元件，這兩個元件的版本控制會分開處理：</span><span class="sxs-lookup"><span data-stu-id="fa713-105">Note that the .NET Framework consists of two main components, which are versioned separately:</span></span>  
  
-   <span data-ttu-id="fa713-106">組件集合，這是為應用程式提供功能的類型與資源集合。</span><span class="sxs-lookup"><span data-stu-id="fa713-106">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="fa713-107">.NET Framework 和組件會共用相同的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="fa713-107">The .NET Framework and assemblies share the same version number.</span></span>  
  
-   <span data-ttu-id="fa713-108">通用語言執行平台 (CLR)，負責管理和執行應用程式的程式碼。</span><span class="sxs-lookup"><span data-stu-id="fa713-108">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="fa713-109">CLR 是透過自己的版本號碼加以識別 (請參閱[版本和相依性](~/docs/framework/migration-guide/versions-and-dependencies.md))。</span><span class="sxs-lookup"><span data-stu-id="fa713-109">The CLR is identified by its own version number (see [Versions and Dependencies](~/docs/framework/migration-guide/versions-and-dependencies.md)).</span></span>  
  
 <span data-ttu-id="fa713-110">若要取得電腦上安裝之 .NET Framework 版本的正確清單，您可以檢視登錄或查詢程式碼中的登錄：</span><span class="sxs-lookup"><span data-stu-id="fa713-110">To get an accurate list of the .NET Framework versions installed on a computer, you can view the registry or query the registry in code:</span></span>  
  
 [<span data-ttu-id="fa713-111">檢視登錄 (1-4 版)</span><span class="sxs-lookup"><span data-stu-id="fa713-111">Viewing the registry (versions 1-4)</span></span>](#net_a)  
 [<span data-ttu-id="fa713-112">檢視登錄 (4.5 版及更新版本)</span><span class="sxs-lookup"><span data-stu-id="fa713-112">Viewing the registry (version 4.5 and later)</span></span>](#net_b)  
 [<span data-ttu-id="fa713-113">使用程式碼查詢登錄 (1-4 版)</span><span class="sxs-lookup"><span data-stu-id="fa713-113">Using code to query the registry (versions 1-4)</span></span>](#net_c)  
 [<span data-ttu-id="fa713-114">使用程式碼查詢登錄 (4.5 版及更新版本)</span><span class="sxs-lookup"><span data-stu-id="fa713-114">Using code to query the registry (version 4.5 and later)</span></span>](#net_d)  
 [<span data-ttu-id="fa713-115">使用 PowerShell 查詢登錄 (4.5 版及更新版本)</span><span class="sxs-lookup"><span data-stu-id="fa713-115">Using PowerShell to query the registry (version 4.5 and later)</span></span>](#ps_a)  
  
 <span data-ttu-id="fa713-116">若要尋找 CLR 版本，您可以使用工具或程式碼：</span><span class="sxs-lookup"><span data-stu-id="fa713-116">To find the CLR version, you can use a tool or code:</span></span>  
  
 [<span data-ttu-id="fa713-117">使用 Clrver 工具</span><span class="sxs-lookup"><span data-stu-id="fa713-117">Using the Clrver tool</span></span>](#clr_a)  
 [<span data-ttu-id="fa713-118">使用程式碼查詢 System.Environment 類別</span><span class="sxs-lookup"><span data-stu-id="fa713-118">Using code to query the System.Environment class</span></span>](#clr_b)  
  
 <span data-ttu-id="fa713-119">如需偵測每一版 .NET Framework 已安裝之更新的資訊，請參閱[如何：判斷安裝的 .NET Framework 更新](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)。</span><span class="sxs-lookup"><span data-stu-id="fa713-119">For information about detecting the installed updates for each version of the .NET Framework, see [How to: Determine Which .NET Framework Updates Are Installed](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md).</span></span> <span data-ttu-id="fa713-120">如需安裝 .NET Framework 的資訊，請參閱[安裝適用於開發人員的 .NET Framework](../../../docs/framework/install/guide-for-developers.md)。</span><span class="sxs-lookup"><span data-stu-id="fa713-120">For information about installing the .NET Framework, see [Install the .NET Framework for developers](../../../docs/framework/install/guide-for-developers.md).</span></span>  
  
<a name="net_a"></a>   
## <a name="to-find-net-framework-versions-by-viewing-the-registry-net-framework-1-4"></a><span data-ttu-id="fa713-121">藉由檢視登錄尋找 .NET Framework 版本 (.NET Framework 1-4)</span><span class="sxs-lookup"><span data-stu-id="fa713-121">To find .NET Framework versions by viewing the registry (.NET Framework 1-4)</span></span>  
  
1.  <span data-ttu-id="fa713-122">在 [開始] 功能表中選擇 [執行]。</span><span class="sxs-lookup"><span data-stu-id="fa713-122">On the **Start** menu, choose **Run**.</span></span>  
  
2.  <span data-ttu-id="fa713-123">在 [開啟] 方塊中輸入 **regedit.exe**。</span><span class="sxs-lookup"><span data-stu-id="fa713-123">In the **Open** box, enter **regedit.exe**.</span></span>  
  
     <span data-ttu-id="fa713-124">您必須具有系統管理認證才能執行 regedit.exe。</span><span class="sxs-lookup"><span data-stu-id="fa713-124">You must have administrative credentials to run regedit.exe.</span></span>  
  
3.  <span data-ttu-id="fa713-125">在 [登錄編輯程式] 中，開啟下列子機碼：</span><span class="sxs-lookup"><span data-stu-id="fa713-125">In the Registry Editor, open the following subkey:</span></span>  
  
     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP`  
  
     <span data-ttu-id="fa713-126">安裝的版本會在 [NDP] 子機碼底下列出。</span><span class="sxs-lookup"><span data-stu-id="fa713-126">The installed versions are listed under the NDP subkey.</span></span> <span data-ttu-id="fa713-127">版本號碼是儲存在 [Version] 項目中。</span><span class="sxs-lookup"><span data-stu-id="fa713-127">The version number is stored in the **Version** entry.</span></span> <span data-ttu-id="fa713-128">在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 中，[Version] 項目位於 [Client] 或 [Full] 子機碼底下 (在 [NDP] 底下)，或是同時在這兩個子機碼底下。</span><span class="sxs-lookup"><span data-stu-id="fa713-128">For the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] the **Version** entry is under the Client or Full subkey (under NDP), or under both subkeys.</span></span>  
  

    > [!NOTE]
    > <span data-ttu-id="fa713-129">登錄中的 [NET Framework Setup] 資料夾不是以英文句號開頭。</span><span class="sxs-lookup"><span data-stu-id="fa713-129">The "NET Framework Setup" folder in the registry does not begin with a period.</span></span>

<a name="net_b"></a> 
## <a name="to-find-net-framework-versions-by-viewing-the-registry-net-framework-45-and-later"></a><span data-ttu-id="fa713-130">藉由檢視登錄尋找 .NET Framework 版本 (.NET Framework 4.5 及更新版本)</span><span class="sxs-lookup"><span data-stu-id="fa713-130">To find .NET Framework versions by viewing the registry (.NET Framework 4.5 and later)</span></span>

1. <span data-ttu-id="fa713-131">在 [開始] 功能表中選擇 [執行]。</span><span class="sxs-lookup"><span data-stu-id="fa713-131">On the **Start** menu, choose **Run**.</span></span>

2. <span data-ttu-id="fa713-132">在 [開啟] 方塊中輸入 **regedit.exe**。</span><span class="sxs-lookup"><span data-stu-id="fa713-132">In the **Open** box, enter **regedit.exe**.</span></span>

     <span data-ttu-id="fa713-133">您必須具有系統管理認證才能執行 regedit.exe。</span><span class="sxs-lookup"><span data-stu-id="fa713-133">You must have administrative credentials to run regedit.exe.</span></span>

3. <span data-ttu-id="fa713-134">在 [登錄編輯程式] 中，開啟下列子機碼：</span><span class="sxs-lookup"><span data-stu-id="fa713-134">In the Registry Editor, open the following subkey:</span></span>

     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`

     <span data-ttu-id="fa713-135">請注意，路徑 `Full` 子機碼包含子機碼 `Net Framework` 而非`.NET Framework`。</span><span class="sxs-lookup"><span data-stu-id="fa713-135">Note that the path to the `Full` subkey includes the subkey `Net Framework` rather than `.NET Framework`.</span></span>

    > [!NOTE]
    > <span data-ttu-id="fa713-136">如果 `Full` 子機碼不存在，則您未安裝 .NET Framework 4.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="fa713-136">If the `Full` subkey is not present, then you do not have the .NET Framework 4.5 or later installed.</span></span>

     <span data-ttu-id="fa713-137">檢查名為 `Release` 的 DWORD 值。</span><span class="sxs-lookup"><span data-stu-id="fa713-137">Check for a DWORD value named `Release`.</span></span> <span data-ttu-id="fa713-138">`Release` DWORD 存在即表示 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 或更新版本已安娤在該電腦上。</span><span class="sxs-lookup"><span data-stu-id="fa713-138">The existence of the `Release` DWORD indicates that the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or newer has been installed on that computer.</span></span>

     <span data-ttu-id="fa713-139">![.NET Framework 4.5 的登錄項目。](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")</span><span class="sxs-lookup"><span data-stu-id="fa713-139">![The registry entry for the .NET Framework 4.5.](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")</span></span>

     <span data-ttu-id="fa713-140">`Release` DWORD 的值表示安裝的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="fa713-140">The value of the `Release` DWORD indicates which version of the .NET Framework is installed.</span></span>

    [!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

    |<span data-ttu-id="fa713-141">Release DWORD 的值</span><span class="sxs-lookup"><span data-stu-id="fa713-141">Value of the Release DWORD</span></span>|<span data-ttu-id="fa713-142">版本</span><span class="sxs-lookup"><span data-stu-id="fa713-142">Version</span></span>|
    |--------------------------------|-------------|
    |<span data-ttu-id="fa713-143">378389</span><span class="sxs-lookup"><span data-stu-id="fa713-143">378389</span></span>|<span data-ttu-id="fa713-144">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="fa713-144">.NET Framework 4.5</span></span>|
    |<span data-ttu-id="fa713-145">378675</span><span class="sxs-lookup"><span data-stu-id="fa713-145">378675</span></span>|<span data-ttu-id="fa713-146">隨 Windows 8.1 或 Windows Server 2012 R2 安裝的 .NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="fa713-146">.NET Framework 4.5.1 installed with Windows 8.1 or Windows Server 2012 R2</span></span>|
    |<span data-ttu-id="fa713-147">378758</span><span class="sxs-lookup"><span data-stu-id="fa713-147">378758</span></span>|<span data-ttu-id="fa713-148">Windows 8、Windows 7 SP1 或 Windows Vista SP2 上安裝的 .NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="fa713-148">.NET Framework 4.5.1 installed on Windows 8, Windows 7 SP1, or Windows Vista SP2</span></span>|
    |<span data-ttu-id="fa713-149">379893</span><span class="sxs-lookup"><span data-stu-id="fa713-149">379893</span></span>|<span data-ttu-id="fa713-150">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="fa713-150">.NET Framework 4.5.2</span></span>|
    |<span data-ttu-id="fa713-151">僅限 Windows 10 系統：393295</span><span class="sxs-lookup"><span data-stu-id="fa713-151">On Windows 10 systems only: 393295</span></span><br /><br /> <span data-ttu-id="fa713-152">所有其他作業系統版本：393297</span><span class="sxs-lookup"><span data-stu-id="fa713-152">On all other OS versions: 393297</span></span>|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|
    |<span data-ttu-id="fa713-153">僅限 Windows 10 11 月更新系統：394254</span><span class="sxs-lookup"><span data-stu-id="fa713-153">On Windows 10 November Update systems only: 394254</span></span><br /><br /> <span data-ttu-id="fa713-154">所有其他作業系統版本：394271</span><span class="sxs-lookup"><span data-stu-id="fa713-154">On all other OS versions: 394271</span></span>|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|
    |<span data-ttu-id="fa713-155">Windows 10 年度更新版及 Windows Server 2016：394802</span><span class="sxs-lookup"><span data-stu-id="fa713-155">On Windows 10 Anniversary Update and Windows Server 2016: 394802</span></span><br /><br /> <span data-ttu-id="fa713-156">所有其他作業系統版本：394806</span><span class="sxs-lookup"><span data-stu-id="fa713-156">On all other OS versions: 394806</span></span>|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]| 
    |<span data-ttu-id="fa713-157">僅限 Windows 10 Creators Update：460798</span><span class="sxs-lookup"><span data-stu-id="fa713-157">On Windows 10 Creators Update only: 460798</span></span><br/><br/> <span data-ttu-id="fa713-158">所有其他作業系統版本：460805</span><span class="sxs-lookup"><span data-stu-id="fa713-158">On all other OS versions: 460805</span></span> | <span data-ttu-id="fa713-159">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="fa713-159">.NET Framework 4.7</span></span> |
    |<span data-ttu-id="fa713-160">僅限 Windows 10 Fall Creators Update：461308</span><span class="sxs-lookup"><span data-stu-id="fa713-160">On Windows 10 Fall Creators Update only: 461308</span></span><br/><br/> <span data-ttu-id="fa713-161">所有其他作業系統版本：461310</span><span class="sxs-lookup"><span data-stu-id="fa713-161">On all other OS versions: 461310</span></span> | <span data-ttu-id="fa713-162">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="fa713-162">.NET Framework 4.7.1</span></span> |
    |<span data-ttu-id="fa713-163">僅限 Windows 10 2018 4 月更新：461808</span><span class="sxs-lookup"><span data-stu-id="fa713-163">On Windows 10 April 2018 Update only: 461808</span></span><br/><br/> <span data-ttu-id="fa713-164">所有其他作業系統版本：461814</span><span class="sxs-lookup"><span data-stu-id="fa713-164">On all other OS versions: 461814</span></span>| <span data-ttu-id="fa713-165">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="fa713-165">.NET Framework 4.7.2</span></span> |
    
<a name="net_c"></a> 
## <a name="to-find-net-framework-versions-by-querying-the-registry-in-code-net-framework-1-4"></a><span data-ttu-id="fa713-166">藉由查詢程式碼中的登錄尋找 .NET Framework 版本 (.NET Framework 1-4)</span><span class="sxs-lookup"><span data-stu-id="fa713-166">To find .NET Framework versions by querying the registry in code (.NET Framework 1-4)</span></span>

- <span data-ttu-id="fa713-167">使用 <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> 類別存取 Windows 登錄中，HKEY_LOCAL_MACHINE 底下的 Software\Microsoft\NET Framework Setup\NDP\ 子機碼。</span><span class="sxs-lookup"><span data-stu-id="fa713-167">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the Software\Microsoft\NET Framework Setup\NDP\ subkey under HKEY_LOCAL_MACHINE in the Windows registry.</span></span>

     <span data-ttu-id="fa713-168">下列程式碼將示範此查詢的範例。</span><span class="sxs-lookup"><span data-stu-id="fa713-168">The following code shows an example of this query.</span></span>

    > [!NOTE]
    > <span data-ttu-id="fa713-169">這個程式碼不會顯示如何偵測 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="fa713-169">This code does not show how to detect the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or later.</span></span> <span data-ttu-id="fa713-170">檢查 `Release` DWORD 即可偵測這些版本，如上一節所述。</span><span class="sxs-lookup"><span data-stu-id="fa713-170">Check the `Release` DWORD to detect those versions, as described in the previous section.</span></span> <span data-ttu-id="fa713-171">如需偵測 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 或更新版本的程式碼，請參閱本文中的下一節。</span><span class="sxs-lookup"><span data-stu-id="fa713-171">For code that does detect the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or later versions, see the next section in this article.</span></span>

     [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

     <span data-ttu-id="fa713-172">這個範例產生的輸出類似下面所述：</span><span class="sxs-lookup"><span data-stu-id="fa713-172">The example produces output that's similar to the following:</span></span>

    ```
    v2.0.50727  2.0.50727.4016  SP2
    v3.0  3.0.30729.4037  SP2
    v3.5  3.5.30729.01  SP1
    v4
      Client  4.0.30319
      Full  4.0.30319
    ```

<a name="net_d"></a> 
## <a name="to-find-net-framework-versions-by-querying-the-registry-in-code-net-framework-45-and-later"></a><span data-ttu-id="fa713-173">藉由查詢程式碼中的登錄尋找 .NET Framework 版本 (.NET Framework 4.5 及更新版本)</span><span class="sxs-lookup"><span data-stu-id="fa713-173">To find .NET Framework versions by querying the registry in code (.NET Framework 4.5 and later)</span></span>

1. <span data-ttu-id="fa713-174">`Release` DWORD 存在即表示電腦上已安裝 .NET Framework 4.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="fa713-174">The existence of the `Release` DWORD indicates that the .NET Framework 4.5 or later has been installed on a computer.</span></span> <span data-ttu-id="fa713-175">關鍵字的值表示已安裝的版本。</span><span class="sxs-lookup"><span data-stu-id="fa713-175">The value of the keyword indicates the installed version.</span></span> <span data-ttu-id="fa713-176">若要檢查此關鍵字，請使用 <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> 類別的 <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A> 和 <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> 方法，存取 Windows 登錄中 HKEY_LOCAL_MACHINE 底下的 Software\Microsoft\NET Framework Setup\NDP\v4\Full 子機碼。</span><span class="sxs-lookup"><span data-stu-id="fa713-176">To check this keyword, use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> methods of the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the Software\Microsoft\NET Framework Setup\NDP\v4\Full subkey under HKEY_LOCAL_MACHINE in the Windows registry.</span></span>

2. <span data-ttu-id="fa713-177">檢查 `Release` 關鍵字的值，判斷已安裝的版本。</span><span class="sxs-lookup"><span data-stu-id="fa713-177">Check the value of the `Release` keyword to determine the installed version.</span></span> <span data-ttu-id="fa713-178">若要向前相容，您可以檢查大於或等於表格中所列值的值。</span><span class="sxs-lookup"><span data-stu-id="fa713-178">To be forward-compatible, you can check for a value greater than or equal to the values listed in the table.</span></span> <span data-ttu-id="fa713-179">以下是 .NET Framework 版本及相關聯的 `Release` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="fa713-179">Here are the .NET Framework versions and associated `Release` keywords.</span></span>

    [!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

    |<span data-ttu-id="fa713-180">版本</span><span class="sxs-lookup"><span data-stu-id="fa713-180">Version</span></span>|<span data-ttu-id="fa713-181">Release DWORD 的值</span><span class="sxs-lookup"><span data-stu-id="fa713-181">Value of the Release DWORD</span></span>|
    |-------------|--------------------------------|
    |<span data-ttu-id="fa713-182">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="fa713-182">.NET Framework 4.5</span></span>|<span data-ttu-id="fa713-183">378389</span><span class="sxs-lookup"><span data-stu-id="fa713-183">378389</span></span>|
    |<span data-ttu-id="fa713-184">隨 Windows 8.1 安裝的 .NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="fa713-184">.NET Framework 4.5.1 installed with Windows 8.1</span></span>|<span data-ttu-id="fa713-185">378675</span><span class="sxs-lookup"><span data-stu-id="fa713-185">378675</span></span>|
    |<span data-ttu-id="fa713-186">Windows 8、Windows 7 SP1 或 Windows Vista SP2 上安裝的 .NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="fa713-186">.NET Framework 4.5.1 installed on Windows 8, Windows 7 SP1, or Windows Vista SP2</span></span>|<span data-ttu-id="fa713-187">378758</span><span class="sxs-lookup"><span data-stu-id="fa713-187">378758</span></span>|
    |<span data-ttu-id="fa713-188">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="fa713-188">.NET Framework 4.5.2</span></span>|<span data-ttu-id="fa713-189">379893</span><span class="sxs-lookup"><span data-stu-id="fa713-189">379893</span></span>|
    |<span data-ttu-id="fa713-190">隨 Windows 10 安裝的 .NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="fa713-190">.NET Framework 4.6 installed with Windows 10</span></span>|<span data-ttu-id="fa713-191">393295</span><span class="sxs-lookup"><span data-stu-id="fa713-191">393295</span></span>|
    |<span data-ttu-id="fa713-192">所有其他 Windows 作業系統版本上安裝的 .NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="fa713-192">.NET Framework 4.6 installed on all other Windows OS versions</span></span>|<span data-ttu-id="fa713-193">393297</span><span class="sxs-lookup"><span data-stu-id="fa713-193">393297</span></span>|
    |<span data-ttu-id="fa713-194">Windows 10 上安裝的 .NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="fa713-194">.NET Framework 4.6.1 installed on Windows 10</span></span>|<span data-ttu-id="fa713-195">394254</span><span class="sxs-lookup"><span data-stu-id="fa713-195">394254</span></span>|
    |<span data-ttu-id="fa713-196">所有其他 Windows 作業系統版本上安裝的 .NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="fa713-196">.NET Framework 4.6.1 installed on all other Windows OS versions</span></span>|<span data-ttu-id="fa713-197">394271</span><span class="sxs-lookup"><span data-stu-id="fa713-197">394271</span></span>|
    |<span data-ttu-id="fa713-198">Windows 10 年度更新版上安裝的 .NET Framework 4.6.2 和 Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="fa713-198">.NET Framework 4.6.2 installed on Windows 10 Anniversary Update and Windows Server 2016</span></span>|<span data-ttu-id="fa713-199">394802</span><span class="sxs-lookup"><span data-stu-id="fa713-199">394802</span></span>|
    |<span data-ttu-id="fa713-200">所有其他 Windows 作業系統版本上安裝的 .NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="fa713-200">.NET Framework 4.6.2 installed on all other Windows OS versions</span></span>|<span data-ttu-id="fa713-201">394806</span><span class="sxs-lookup"><span data-stu-id="fa713-201">394806</span></span>|
    |<span data-ttu-id="fa713-202">Windows 10 Creators Update 上安裝的 .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="fa713-202">.NET Framework 4.7 installed on Windows 10 Creators Update</span></span>|<span data-ttu-id="fa713-203">460798</span><span class="sxs-lookup"><span data-stu-id="fa713-203">460798</span></span>|
    |<span data-ttu-id="fa713-204">所有其他 Windows 作業系統版本上安裝的 .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="fa713-204">.NET Framework 4.7 installed on all other Windows OS versions</span></span>|<span data-ttu-id="fa713-205">460805</span><span class="sxs-lookup"><span data-stu-id="fa713-205">460805</span></span>|
    |<span data-ttu-id="fa713-206">.NET Framework 4.7.1 安裝於 Windows 10 Fall Creators Update</span><span class="sxs-lookup"><span data-stu-id="fa713-206">.NET Framework 4.7.1 installed on Windows 10 Fall Creators Update</span></span>|<span data-ttu-id="fa713-207">461308</span><span class="sxs-lookup"><span data-stu-id="fa713-207">461308</span></span>|
    |<span data-ttu-id="fa713-208">所有其他 Windows 作業系統版本上安裝的 .NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="fa713-208">.NET Framework 4.7.1 installed on all other Windows OS versions</span></span>|<span data-ttu-id="fa713-209">461310</span><span class="sxs-lookup"><span data-stu-id="fa713-209">461310</span></span>|
    |<span data-ttu-id="fa713-210">Windows 10 2018 4 月更新上安裝的 .NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="fa713-210">.NET Framework 4.7.2 installed on Windows 10 April 2018 Update</span></span>|<span data-ttu-id="fa713-211">461808</span><span class="sxs-lookup"><span data-stu-id="fa713-211">461808</span></span>|
    |<span data-ttu-id="fa713-212">所有其他 Windows 作業系統版本上安裝的 .NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="fa713-212">.NET Framework 4.7.2 installed on all other Windows OS versions</span></span>|<span data-ttu-id="fa713-213">461814</span><span class="sxs-lookup"><span data-stu-id="fa713-213">461814</span></span>|
    
     <span data-ttu-id="fa713-214">下列範例會檢查登錄中的 `Release` 值，以判斷是否安裝 .NET Framework 的 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="fa713-214">The following example checks the `Release` value in the registry to determine whether the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or a later version of the .NET Framework is installed.</span></span>

     [!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
     [!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

     <span data-ttu-id="fa713-215">此範例遵循版本檢查的建議做法：</span><span class="sxs-lookup"><span data-stu-id="fa713-215">This example follows the recommended practice for version checking:</span></span>

    - <span data-ttu-id="fa713-216">它會檢查 `Release` 項目的值「大於或等於」已知版本機碼的值。</span><span class="sxs-lookup"><span data-stu-id="fa713-216">It checks whether the value of the `Release` entry is *greater than or equal to* the value of the known release keys.</span></span>

    - <span data-ttu-id="fa713-217">它會從最新版本依序檢查到最舊版本。</span><span class="sxs-lookup"><span data-stu-id="fa713-217">It checks in order from most recent version to earliest version.</span></span>

<a name="ps_a"></a> 
## <a name="to-check-for-a-minimum-required-net-framework-version-by-querying-the-registry-in-powershell-net-framework-45-and-later"></a><span data-ttu-id="fa713-218">藉由查詢 PowerShell 的登錄來檢查所需的最低 .NET Framework 版本 (.NET Framework 4.5 及更新版本)</span><span class="sxs-lookup"><span data-stu-id="fa713-218">To check for a minimum-required .NET Framework version by querying the registry in PowerShell (.NET Framework 4.5 and later)</span></span>

- <span data-ttu-id="fa713-219">下列範例會檢查 `Release` 關鍵字的值，判斷是否安裝 .NET Framework 4.6.2 或更高版本，無論 Windows 作業系統版本為何 (如果是，傳回 `True`；否則傳回 `False`)。</span><span class="sxs-lookup"><span data-stu-id="fa713-219">The following example checks the value of the `Release` keyword to determine whether .NET Framework 4.6.2 or higher is installed, regardless of Windows OS version (returning `True` if it is and `False` otherwise).</span></span>

    ```PowerShell
    Get-ChildItem "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\" | Get-ItemPropertyValue -Name Release | ForEach-Object { $_ -ge 394802 } 
    ```

    <span data-ttu-id="fa713-220">您可以使用下表的其他值取代上例中的 `394802` 來檢查是否有不同的所需最低 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="fa713-220">You can replace `394802` in the previous example with another value from the following table to check for a different minimum-required .NET Framework version.</span></span>
  
    |<span data-ttu-id="fa713-221">版本</span><span class="sxs-lookup"><span data-stu-id="fa713-221">Version</span></span>|<span data-ttu-id="fa713-222">DWORD 版本的最低值</span><span class="sxs-lookup"><span data-stu-id="fa713-222">Minimum value of the Release DWORD</span></span>|
    |-------------|--------------------------------|
    |<span data-ttu-id="fa713-223">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="fa713-223">.NET Framework 4.5</span></span>|<span data-ttu-id="fa713-224">378389</span><span class="sxs-lookup"><span data-stu-id="fa713-224">378389</span></span>|
    |<span data-ttu-id="fa713-225">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="fa713-225">.NET Framework 4.5.1</span></span>|<span data-ttu-id="fa713-226">378675</span><span class="sxs-lookup"><span data-stu-id="fa713-226">378675</span></span>|
    |<span data-ttu-id="fa713-227">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="fa713-227">.NET Framework 4.5.2</span></span>|<span data-ttu-id="fa713-228">379893</span><span class="sxs-lookup"><span data-stu-id="fa713-228">379893</span></span>|
    |[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|<span data-ttu-id="fa713-229">393295</span><span class="sxs-lookup"><span data-stu-id="fa713-229">393295</span></span>|
    |[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|<span data-ttu-id="fa713-230">394254</span><span class="sxs-lookup"><span data-stu-id="fa713-230">394254</span></span>|
    |[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]|<span data-ttu-id="fa713-231">394802</span><span class="sxs-lookup"><span data-stu-id="fa713-231">394802</span></span>|
    |<span data-ttu-id="fa713-232">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="fa713-232">.NET Framework 4.7</span></span>|<span data-ttu-id="fa713-233">460798</span><span class="sxs-lookup"><span data-stu-id="fa713-233">460798</span></span>|
    |<span data-ttu-id="fa713-234">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="fa713-234">.NET Framework 4.7.1</span></span>|<span data-ttu-id="fa713-235">461308</span><span class="sxs-lookup"><span data-stu-id="fa713-235">461308</span></span>|
    |<span data-ttu-id="fa713-236">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="fa713-236">.NET Framework 4.7.2</span></span>|<span data-ttu-id="fa713-237">461808</span><span class="sxs-lookup"><span data-stu-id="fa713-237">461808</span></span>|

<a name="clr_a"></a> 
## <a name="to-find-the-current-runtime-version-by-using-the-clrver-tool"></a><span data-ttu-id="fa713-238">使用 Clrver 工具尋找目前的執行階段版本</span><span class="sxs-lookup"><span data-stu-id="fa713-238">To find the current runtime version by using the Clrver tool</span></span>

- <span data-ttu-id="fa713-239">使用 CLR 版本工具 (Clrver.exe) 判斷電腦上安裝了哪些通用語言執行平台 (CLR) 版本。</span><span class="sxs-lookup"><span data-stu-id="fa713-239">Use the CLR Version Tool (Clrver.exe) to determine which versions of the common language runtime are installed on a computer.</span></span>

     <span data-ttu-id="fa713-240">在 Visual Studio 命令提示字元中輸入 `clrver`。</span><span class="sxs-lookup"><span data-stu-id="fa713-240">From a Visual Studio Command Prompt, enter `clrver`.</span></span> <span data-ttu-id="fa713-241">這個命令產生的輸出類似下面所述：</span><span class="sxs-lookup"><span data-stu-id="fa713-241">This command produces output similar to the following:</span></span>

    ```
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

     <span data-ttu-id="fa713-242">如需使用這項工具的詳細資訊，請參閱 [Clrver.exe (CLR 版本工具)](~/docs/framework/tools/clrver-exe-clr-version-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="fa713-242">For more information about using this tool, see [Clrver.exe (CLR Version Tool)](~/docs/framework/tools/clrver-exe-clr-version-tool.md).</span></span>

<a name="clr_b"></a> 
## <a name="to-find-the-current-runtime-version-by-querying-the-environment-class-in-code"></a><span data-ttu-id="fa713-243">若要藉由查詢程式碼中的 Environment 類別尋找目前的執行階段版本</span><span class="sxs-lookup"><span data-stu-id="fa713-243">To find the current runtime version by querying the Environment class in code</span></span>

- <span data-ttu-id="fa713-244">查詢 <xref:System.Environment.Version%2A?displayProperty=nameWithType> 屬性，以擷取可識別目前執行程式碼的執行階段版本的 <xref:System.Version>。</span><span class="sxs-lookup"><span data-stu-id="fa713-244">Query the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to retrieve a <xref:System.Version> object that identifies the version of the runtime that is currently executing the code.</span></span> <span data-ttu-id="fa713-245">您可以使用 <xref:System.Version.Major%2A?displayProperty=nameWithType> 屬性取得主要版本識別項 (例如，"4" 代表 4.0 版)，使用 <xref:System.Version.Minor%2A?displayProperty=nameWithType> 屬性取得次要版本識別項 (例如，"0" 代表 4.0 版)，或者使用 <xref:System.Object.ToString%2A?displayProperty=nameWithType> 方法取得整個版本字串 (例如 "4.0.30319.18010"，如下列程式碼所示)。</span><span class="sxs-lookup"><span data-stu-id="fa713-245">You can use the <xref:System.Version.Major%2A?displayProperty=nameWithType> property to get the major release identifier (for example, "4" for version 4.0), the <xref:System.Version.Minor%2A?displayProperty=nameWithType> property to get the minor release identifier (for example, "0" for version 4.0), or the <xref:System.Object.ToString%2A?displayProperty=nameWithType> method to get the entire version string (for example, "4.0.30319.18010", as shown in the following code).</span></span> <span data-ttu-id="fa713-246">這個屬性會傳回單一值，反映出目前執行程式碼的執行階段版本，但是不會傳回電腦上可能已安裝的組件版本或其他執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="fa713-246">This property returns a single value that reflects the version of the runtime that is currently executing the code; it does not return assembly versions or other versions of the runtime that may have been installed on the computer.</span></span>

     <span data-ttu-id="fa713-247">針對 .NET Framework 4、4.5、4.5.1 和 4.5.2 版，<xref:System.Environment.Version%2A?displayProperty=nameWithType> 屬性會傳回 <xref:System.Version> 物件，其字串表示的格式為 `4.0.30319.xxxxx`。</span><span class="sxs-lookup"><span data-stu-id="fa713-247">For the .NET Framework Versions 4, 4.5, 4.5.1, and 4.5.2, the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property returns a <xref:System.Version> object whose string representation has the form `4.0.30319.xxxxx`.</span></span> <span data-ttu-id="fa713-248">針對 .NET Framework 4.6 和更新版本，其格式為 `4.0.30319.42000`。</span><span class="sxs-lookup"><span data-stu-id="fa713-248">For the .NET Framework 4.6 and later, it has the form `4.0.30319.42000`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="fa713-249">針對 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 和更新版本，不建議使用 <xref:System.Environment.Version%2A?displayProperty=nameWithType> 屬性來偵測執行階段的版本。</span><span class="sxs-lookup"><span data-stu-id="fa713-249">For the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] and later, we do not recommend using the  <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to detect the version of the runtime.</span></span> <span data-ttu-id="fa713-250">相反地，建議您查詢登錄，如本文稍早的[藉由查詢程式碼中的登錄尋找 .NET Framework 版本 (.NET Framework 4.5 及更新版本)](#net_d) 一節中所述。</span><span class="sxs-lookup"><span data-stu-id="fa713-250">Instead, we recommend that you query the registry, as described in the [To find .NET Framework versions by querying the registry in code (.NET Framework 4.5 and later)](#net_d) section earlier in this article.</span></span>

     <span data-ttu-id="fa713-251">以下是查詢 <xref:System.Environment.Version%2A?displayProperty=nameWithType> 屬性取得執行階段版本資訊的範例：</span><span class="sxs-lookup"><span data-stu-id="fa713-251">Here's an example of querying the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property for runtime version information:</span></span>

     [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

     <span data-ttu-id="fa713-252">這個範例產生的輸出類似下面所述：</span><span class="sxs-lookup"><span data-stu-id="fa713-252">The example produces output that's similar to the following:</span></span>

    ```
    Version: 4.0.30319.18010
    ```

## <a name="see-also"></a><span data-ttu-id="fa713-253">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa713-253">See also</span></span>

[<span data-ttu-id="fa713-254">操作說明：判斷安裝的 .NET Framework 更新</span><span class="sxs-lookup"><span data-stu-id="fa713-254">How to: Determine Which .NET Framework Updates Are Installed</span></span>](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)  
[<span data-ttu-id="fa713-255">安裝適用於開發人員的 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fa713-255">Install the .NET Framework for developers</span></span>](../../../docs/framework/install/guide-for-developers.md)  
[<span data-ttu-id="fa713-256">版本和相依性</span><span class="sxs-lookup"><span data-stu-id="fa713-256">Versions and Dependencies</span></span>](~/docs/framework/migration-guide/versions-and-dependencies.md)  
