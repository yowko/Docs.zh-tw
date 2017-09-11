---
title: "如何：判斷安裝的 .NET Framework 版本"
ms.date: 08/09/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
caps.latest.revision: 62
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 775e4512a5ff31c7059961f6332c6bdc0dc5247a
ms.openlocfilehash: afb01fd47ed2ce3b9c5838f3a8f61c8d34147378
ms.contentlocale: zh-tw
ms.lasthandoff: 08/11/2017

---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="2d546-102">如何：判斷安裝的 .NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="2d546-102">How to: Determine Which .NET Framework Versions Are Installed</span></span>
<span data-ttu-id="2d546-103">使用者可以在電腦上安裝及執行多個版本的 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="2d546-103">Users can install and run multiple versions of the .NET Framework on their computers.</span></span> <span data-ttu-id="2d546-104">當您開發或部署應用程式時，您可能需要知道使用者電腦上安裝的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="2d546-104">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user’s computer.</span></span> <span data-ttu-id="2d546-105">請注意，.NET Framework 包含兩個主要元件，這兩個元件的版本控制會分開處理：</span><span class="sxs-lookup"><span data-stu-id="2d546-105">Note that the .NET Framework consists of two main components, which are versioned separately:</span></span>  
  
-   <span data-ttu-id="2d546-106">組件集合，這是為應用程式提供功能的類型與資源集合。</span><span class="sxs-lookup"><span data-stu-id="2d546-106">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="2d546-107">.NET Framework 和組件會共用相同的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="2d546-107">The .NET Framework and assemblies share the same version number.</span></span>  
  
-   <span data-ttu-id="2d546-108">通用語言執行平台 (CLR)，負責管理和執行應用程式的程式碼。</span><span class="sxs-lookup"><span data-stu-id="2d546-108">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="2d546-109">CLR 是透過自己的版本號碼加以識別 (請參閱[版本和相依性](~/docs/framework/migration-guide/versions-and-dependencies.md))。</span><span class="sxs-lookup"><span data-stu-id="2d546-109">The CLR is identified by its own version number (see [Versions and Dependencies](~/docs/framework/migration-guide/versions-and-dependencies.md)).</span></span>  
  
 <span data-ttu-id="2d546-110">若要取得電腦上安裝之 .NET Framework 版本的正確清單，您可以檢視登錄或查詢程式碼中的登錄：</span><span class="sxs-lookup"><span data-stu-id="2d546-110">To get an accurate list of the .NET Framework versions installed on a computer, you can view the registry or query the registry in code:</span></span>  
  
 [<span data-ttu-id="2d546-111">檢視登錄 (1-4 版)</span><span class="sxs-lookup"><span data-stu-id="2d546-111">Viewing the registry (versions 1-4)</span></span>](#net_a)  
 [<span data-ttu-id="2d546-112">檢視登錄 (4.5 版及更新版本)</span><span class="sxs-lookup"><span data-stu-id="2d546-112">Viewing the registry (version 4.5 and later)</span></span>](#net_b)  
 [<span data-ttu-id="2d546-113">使用程式碼查詢登錄 (1-4 版)</span><span class="sxs-lookup"><span data-stu-id="2d546-113">Using code to query the registry (versions 1-4)</span></span>](#net_c)  
 [<span data-ttu-id="2d546-114">使用程式碼查詢登錄 (4.5 版及更新版本)</span><span class="sxs-lookup"><span data-stu-id="2d546-114">Using code to query the registry (version 4.5 and later)</span></span>](#net_d)  
 [<span data-ttu-id="2d546-115">使用 PowerShell 查詢登錄 (4.5 版及更新版本)</span><span class="sxs-lookup"><span data-stu-id="2d546-115">Using PowerShell to query the registry (version 4.5 and later)</span></span>](#ps_a)  
  
 <span data-ttu-id="2d546-116">若要尋找 CLR 版本，您可以使用工具或程式碼：</span><span class="sxs-lookup"><span data-stu-id="2d546-116">To find the CLR version, you can use a tool or code:</span></span>  
  
 [<span data-ttu-id="2d546-117">使用 Clrver 工具</span><span class="sxs-lookup"><span data-stu-id="2d546-117">Using the Clrver tool</span></span>](#clr_a)  
 [<span data-ttu-id="2d546-118">使用程式碼查詢 System.Environment 類別</span><span class="sxs-lookup"><span data-stu-id="2d546-118">Using code to query the System.Environment class</span></span>](#clr_b)  
  
 <span data-ttu-id="2d546-119">如需偵測每一版 .NET Framework 已安裝之更新的資訊，請參閱[如何：判斷安裝的 .NET Framework 更新](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)。</span><span class="sxs-lookup"><span data-stu-id="2d546-119">For information about detecting the installed updates for each version of the .NET Framework, see [How to: Determine Which .NET Framework Updates Are Installed](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md).</span></span> <span data-ttu-id="2d546-120">如需安裝 .NET Framework 的資訊，請參閱[安裝適用於開發人員的 .NET Framework](../../../docs/framework/install/guide-for-developers.md)。</span><span class="sxs-lookup"><span data-stu-id="2d546-120">For information about installing the .NET Framework, see [Install the .NET Framework for developers](../../../docs/framework/install/guide-for-developers.md).</span></span>  
  
<a name="net_a"></a>   
#### <a name="to-find-net-framework-versions-by-viewing-the-registry-net-framework-1-4"></a><span data-ttu-id="2d546-121">藉由檢視登錄尋找 .NET Framework 版本 (.NET Framework 1-4)</span><span class="sxs-lookup"><span data-stu-id="2d546-121">To find .NET Framework versions by viewing the registry (.NET Framework 1-4)</span></span>  
  
1.  <span data-ttu-id="2d546-122">在 [開始] 功能表中選擇 [執行]。</span><span class="sxs-lookup"><span data-stu-id="2d546-122">On the **Start** menu, choose **Run**.</span></span>  
  
2.  <span data-ttu-id="2d546-123">在 [開啟] 方塊中輸入 **regedit.exe**。</span><span class="sxs-lookup"><span data-stu-id="2d546-123">In the **Open** box, enter **regedit.exe**.</span></span>  
  
     <span data-ttu-id="2d546-124">您必須具有系統管理認證才能執行 regedit.exe。</span><span class="sxs-lookup"><span data-stu-id="2d546-124">You must have administrative credentials to run regedit.exe.</span></span>  
  
3.  <span data-ttu-id="2d546-125">在 [登錄編輯程式] 中，開啟下列子機碼：</span><span class="sxs-lookup"><span data-stu-id="2d546-125">In the Registry Editor, open the following subkey:</span></span>  
  
     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP`  
  
     <span data-ttu-id="2d546-126">安裝的版本會在 [NDP] 子機碼底下列出。</span><span class="sxs-lookup"><span data-stu-id="2d546-126">The installed versions are listed under the NDP subkey.</span></span> <span data-ttu-id="2d546-127">版本號碼是儲存在 [Version] 項目中。</span><span class="sxs-lookup"><span data-stu-id="2d546-127">The version number is stored in the **Version** entry.</span></span> <span data-ttu-id="2d546-128">在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 中，[Version] 項目位於 [Client] 或 [Full] 子機碼底下 (在 [NDP] 底下)，或是同時在這兩個子機碼底下。</span><span class="sxs-lookup"><span data-stu-id="2d546-128">For the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] the **Version** entry is under the Client or Full subkey (under NDP), or under both subkeys.</span></span>  
  

    > [!NOTE]
    > <span data-ttu-id="2d546-129">登錄中的 [NET Framework Setup] 資料夾不是以英文句號開頭。</span><span class="sxs-lookup"><span data-stu-id="2d546-129">The "NET Framework Setup" folder in the registry does not begin with a period.</span></span>

<a name="net_b"></a> 
#### <a name="to-find-net-framework-versions-by-viewing-the-registry-net-framework-45-and-later"></a><span data-ttu-id="2d546-130">藉由檢視登錄尋找 .NET Framework 版本 (.NET Framework 4.5 及更新版本)</span><span class="sxs-lookup"><span data-stu-id="2d546-130">To find .NET Framework versions by viewing the registry (.NET Framework 4.5 and later)</span></span>

1. <span data-ttu-id="2d546-131">在 [開始] 功能表中選擇 [執行]。</span><span class="sxs-lookup"><span data-stu-id="2d546-131">On the **Start** menu, choose **Run**.</span></span>

2. <span data-ttu-id="2d546-132">在 [開啟] 方塊中輸入 **regedit.exe**。</span><span class="sxs-lookup"><span data-stu-id="2d546-132">In the **Open** box, enter **regedit.exe**.</span></span>

     <span data-ttu-id="2d546-133">您必須具有系統管理認證才能執行 regedit.exe。</span><span class="sxs-lookup"><span data-stu-id="2d546-133">You must have administrative credentials to run regedit.exe.</span></span>

3. <span data-ttu-id="2d546-134">在 [登錄編輯程式] 中，開啟下列子機碼：</span><span class="sxs-lookup"><span data-stu-id="2d546-134">In the Registry Editor, open the following subkey:</span></span>

     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`

     <span data-ttu-id="2d546-135">請注意，路徑 `Full` 子機碼包含子機碼 `Net Framework` 而非`.NET Framework`。</span><span class="sxs-lookup"><span data-stu-id="2d546-135">Note that the path to the `Full` subkey includes the subkey `Net Framework` rather than `.NET Framework`.</span></span>

    > [!NOTE]
    > <span data-ttu-id="2d546-136">如果 `Full` 子機碼不存在，則您未安裝 .NET Framework 4.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="2d546-136">If the `Full` subkey is not present, then you do not have the .NET Framework 4.5 or later installed.</span></span>

     <span data-ttu-id="2d546-137">檢查名為 `Release` 的 DWORD 值。</span><span class="sxs-lookup"><span data-stu-id="2d546-137">Check for a DWORD value named `Release`.</span></span> <span data-ttu-id="2d546-138">`Release` DWORD 存在即表示 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 或更新版本已安娤在該電腦上。</span><span class="sxs-lookup"><span data-stu-id="2d546-138">The existence of the `Release` DWORD indicates that the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or newer has been installed on that computer.</span></span>

     <span data-ttu-id="2d546-139">![.NET Framework 4.5 的登錄項目。](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")</span><span class="sxs-lookup"><span data-stu-id="2d546-139">![The registry entry for the .NET Framework 4.5.](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")</span></span>

     <span data-ttu-id="2d546-140">`Release` DWORD 的值表示安裝的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="2d546-140">The value of the `Release` DWORD indicates which version of the .NET Framework is installed.</span></span>

    |<span data-ttu-id="2d546-141">Release DWORD 的值</span><span class="sxs-lookup"><span data-stu-id="2d546-141">Value of the Release DWORD</span></span>|<span data-ttu-id="2d546-142">版本</span><span class="sxs-lookup"><span data-stu-id="2d546-142">Version</span></span>|
    |--------------------------------|-------------|
    |<span data-ttu-id="2d546-143">378389</span><span class="sxs-lookup"><span data-stu-id="2d546-143">378389</span></span>|<span data-ttu-id="2d546-144">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="2d546-144">.NET Framework 4.5</span></span>|
    |<span data-ttu-id="2d546-145">378675</span><span class="sxs-lookup"><span data-stu-id="2d546-145">378675</span></span>|<span data-ttu-id="2d546-146">隨 Windows 8.1 或 Windows Server 2012 R2 安裝的 .NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="2d546-146">.NET Framework 4.5.1 installed with Windows 8.1 or Windows Server 2012 R2</span></span>|
    |<span data-ttu-id="2d546-147">378758</span><span class="sxs-lookup"><span data-stu-id="2d546-147">378758</span></span>|<span data-ttu-id="2d546-148">Windows 8、Windows 7 SP1 或 Windows Vista SP2 上安裝的 .NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="2d546-148">.NET Framework 4.5.1 installed on Windows 8, Windows 7 SP1, or Windows Vista SP2</span></span>|
    |<span data-ttu-id="2d546-149">379893</span><span class="sxs-lookup"><span data-stu-id="2d546-149">379893</span></span>|<span data-ttu-id="2d546-150">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="2d546-150">.NET Framework 4.5.2</span></span>|
    |<span data-ttu-id="2d546-151">Windows 10 系統：393295</span><span class="sxs-lookup"><span data-stu-id="2d546-151">On Windows 10 systems: 393295</span></span><br /><br /> <span data-ttu-id="2d546-152">所有其他作業系統版本：393297</span><span class="sxs-lookup"><span data-stu-id="2d546-152">On all other OS versions: 393297</span></span>|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|
    |<span data-ttu-id="2d546-153">Windows 10 11 月更新系統：394254</span><span class="sxs-lookup"><span data-stu-id="2d546-153">On Windows 10 November Update systems: 394254</span></span><br /><br /> <span data-ttu-id="2d546-154">所有其他作業系統版本：394271</span><span class="sxs-lookup"><span data-stu-id="2d546-154">On all other OS versions: 394271</span></span>|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|
    |<span data-ttu-id="2d546-155">Windows 10 年度更新版：394802</span><span class="sxs-lookup"><span data-stu-id="2d546-155">On Windows 10 Anniversary Update: 394802</span></span><br /><br /> <span data-ttu-id="2d546-156">所有其他作業系統版本：394806</span><span class="sxs-lookup"><span data-stu-id="2d546-156">On all other OS versions: 394806</span></span>|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]| 
    |<span data-ttu-id="2d546-157">Windows 10 Creators Update：460798</span><span class="sxs-lookup"><span data-stu-id="2d546-157">On Windows 10 Creators Update: 460798</span></span><br/><br/> <span data-ttu-id="2d546-158">所有其他作業系統版本：460805</span><span class="sxs-lookup"><span data-stu-id="2d546-158">On all other OS versions: 460805</span></span> | <span data-ttu-id="2d546-159">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="2d546-159">.NET Framework 4.7</span></span> |

<a name="net_c"></a> 
#### <a name="to-find-net-framework-versions-by-querying-the-registry-in-code-net-framework-1-4"></a><span data-ttu-id="2d546-160">藉由查詢程式碼中的登錄尋找 .NET Framework 版本 (.NET Framework 1-4)</span><span class="sxs-lookup"><span data-stu-id="2d546-160">To find .NET Framework versions by querying the registry in code (.NET Framework 1-4)</span></span>

- <span data-ttu-id="2d546-161">使用 <xref:Microsoft.Win32.RegistryKey?displayProperty=fullName> 類別存取 Windows 登錄中，HKEY_LOCAL_MACHINE 底下的 Software\Microsoft\NET Framework Setup\NDP\ 子機碼。</span><span class="sxs-lookup"><span data-stu-id="2d546-161">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=fullName> class to access the Software\Microsoft\NET Framework Setup\NDP\ subkey under HKEY_LOCAL_MACHINE in the Windows registry.</span></span>

     <span data-ttu-id="2d546-162">下列程式碼將示範此查詢的範例。</span><span class="sxs-lookup"><span data-stu-id="2d546-162">The following code shows an example of this query.</span></span>

    > [!NOTE]
    > <span data-ttu-id="2d546-163">這個程式碼不會顯示如何偵測 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="2d546-163">This code does not show how to detect the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or later.</span></span> <span data-ttu-id="2d546-164">檢查 `Release` DWORD 即可偵測這些版本，如上一節所述。</span><span class="sxs-lookup"><span data-stu-id="2d546-164">Check the `Release` DWORD to detect those versions, as described in the previous section.</span></span> <span data-ttu-id="2d546-165">如需偵測 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 或更新版本的程式碼，請參閱本文中的下一節。</span><span class="sxs-lookup"><span data-stu-id="2d546-165">For code that does detect the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or later versions, see the next section in this article.</span></span>

     <span data-ttu-id="2d546-166">[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]    [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]</span><span class="sxs-lookup"><span data-stu-id="2d546-166">[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]    [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]</span></span>

     <span data-ttu-id="2d546-167">這個範例產生的輸出類似下面所述：</span><span class="sxs-lookup"><span data-stu-id="2d546-167">The example produces output that's similar to the following:</span></span>

    ```
    v2.0.50727  2.0.50727.4016  SP2
    v3.0  3.0.30729.4037  SP2
    v3.5  3.5.30729.01  SP1
    v4
      Client  4.0.30319
      Full  4.0.30319
    ```

<a name="net_d"></a> 
#### <a name="to-find-net-framework-versions-by-querying-the-registry-in-code-net-framework-45-and-later"></a><span data-ttu-id="2d546-168">藉由查詢程式碼中的登錄尋找 .NET Framework 版本 (.NET Framework 4.5 及更新版本)</span><span class="sxs-lookup"><span data-stu-id="2d546-168">To find .NET Framework versions by querying the registry in code (.NET Framework 4.5 and later)</span></span>

1. <span data-ttu-id="2d546-169">`Release` DWORD 存在即表示電腦上已安裝 .NET Framework 4.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="2d546-169">The existence of the `Release` DWORD indicates that the .NET Framework 4.5 or later has been installed on a computer.</span></span> <span data-ttu-id="2d546-170">關鍵字的值表示已安裝的版本。</span><span class="sxs-lookup"><span data-stu-id="2d546-170">The value of the keyword indicates the installed version.</span></span> <span data-ttu-id="2d546-171">若要檢查此關鍵字，請使用 <xref:Microsoft.Win32.RegistryKey?displayProperty=fullName> 類別的 <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A> 和 <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> 方法，存取 Windows 登錄中 HKEY_LOCAL_MACHINE 底下的 Software\Microsoft\NET Framework Setup\NDP\v4\Full 子機碼。</span><span class="sxs-lookup"><span data-stu-id="2d546-171">To check this keyword, use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> methods of the <xref:Microsoft.Win32.RegistryKey?displayProperty=fullName> class to access the Software\Microsoft\NET Framework Setup\NDP\v4\Full subkey under HKEY_LOCAL_MACHINE in the Windows registry.</span></span>

2. <span data-ttu-id="2d546-172">檢查 `Release` 關鍵字的值，判斷已安裝的版本。</span><span class="sxs-lookup"><span data-stu-id="2d546-172">Check the value of the `Release` keyword to determine the installed version.</span></span> <span data-ttu-id="2d546-173">若要向前相容，您可以檢查大於或等於表格中所列值的值。</span><span class="sxs-lookup"><span data-stu-id="2d546-173">To be forward-compatible, you can check for a value greater than or equal to the values listed in the table.</span></span> <span data-ttu-id="2d546-174">以下是 .NET Framework 版本及相關聯的 `Release` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="2d546-174">Here are the .NET Framework versions and associated `Release` keywords.</span></span>

    |<span data-ttu-id="2d546-175">版本</span><span class="sxs-lookup"><span data-stu-id="2d546-175">Version</span></span>|<span data-ttu-id="2d546-176">Release DWORD 的值</span><span class="sxs-lookup"><span data-stu-id="2d546-176">Value of the Release DWORD</span></span>|
    |-------------|--------------------------------|
    |<span data-ttu-id="2d546-177">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="2d546-177">.NET Framework 4.5</span></span>|<span data-ttu-id="2d546-178">378389</span><span class="sxs-lookup"><span data-stu-id="2d546-178">378389</span></span>|
    |<span data-ttu-id="2d546-179">隨 Windows 8.1 安裝的 .NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="2d546-179">.NET Framework 4.5.1 installed with Windows 8.1</span></span>|<span data-ttu-id="2d546-180">378675</span><span class="sxs-lookup"><span data-stu-id="2d546-180">378675</span></span>|
    |<span data-ttu-id="2d546-181">Windows 8、Windows 7 SP1 或 Windows Vista SP2 上安裝的 .NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="2d546-181">.NET Framework 4.5.1 installed on Windows 8, Windows 7 SP1, or Windows Vista SP2</span></span>|<span data-ttu-id="2d546-182">378758</span><span class="sxs-lookup"><span data-stu-id="2d546-182">378758</span></span>|
    |<span data-ttu-id="2d546-183">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="2d546-183">.NET Framework 4.5.2</span></span>|<span data-ttu-id="2d546-184">379893</span><span class="sxs-lookup"><span data-stu-id="2d546-184">379893</span></span>|
    |<span data-ttu-id="2d546-185">隨 Windows 8.1 安裝的 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d546-185">[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] installed with Windows 10</span></span>|<span data-ttu-id="2d546-186">393295</span><span class="sxs-lookup"><span data-stu-id="2d546-186">393295</span></span>|
    |<span data-ttu-id="2d546-187">所有其他 Windows 作業系統版本上安裝的 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d546-187">[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] installed on all other Windows OS versions</span></span>|<span data-ttu-id="2d546-188">393297</span><span class="sxs-lookup"><span data-stu-id="2d546-188">393297</span></span>|
    |[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]<span data-ttu-id="2d546-189"> 安裝在 Windows 10</span><span class="sxs-lookup"><span data-stu-id="2d546-189"> installed on Windows 10</span></span>|<span data-ttu-id="2d546-190">394254</span><span class="sxs-lookup"><span data-stu-id="2d546-190">394254</span></span>|
    |<span data-ttu-id="2d546-191">所有其他 Windows 作業系統版本上安裝的 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d546-191">[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] installed on all other Windows OS versions</span></span>|<span data-ttu-id="2d546-192">394271</span><span class="sxs-lookup"><span data-stu-id="2d546-192">394271</span></span>|
    |<span data-ttu-id="2d546-193">Windows 10 年度更新版上安裝的 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d546-193">[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] installed on Windows 10 Anniversary Update</span></span>|<span data-ttu-id="2d546-194">394802</span><span class="sxs-lookup"><span data-stu-id="2d546-194">394802</span></span>|
    |<span data-ttu-id="2d546-195">所有其他 Windows 作業系統版本上安裝的 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d546-195">[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] installed on all other Windows OS versions</span></span>|<span data-ttu-id="2d546-196">394806</span><span class="sxs-lookup"><span data-stu-id="2d546-196">394806</span></span>|
    |<span data-ttu-id="2d546-197">Windows 10 Creators Update 上安裝的 .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="2d546-197">.NET Framework 4.7 installed on Windows 10 Creators Update</span></span>|<span data-ttu-id="2d546-198">460798</span><span class="sxs-lookup"><span data-stu-id="2d546-198">460798</span></span>|
    |<span data-ttu-id="2d546-199">所有其他 Windows 作業系統版本上安裝的 .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="2d546-199">.NET Framework 4.7 installed on all other Windows OS versions</span></span>|<span data-ttu-id="2d546-200">460805</span><span class="sxs-lookup"><span data-stu-id="2d546-200">460805</span></span>|

     <span data-ttu-id="2d546-201">下列範例會檢查登錄中的 `Release` 值，以判斷是否安裝 .NET Framework 的 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="2d546-201">The following example checks the `Release` value in the registry to determine whether the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or a later version of the .NET Framework is installed.</span></span>

     <span data-ttu-id="2d546-202">[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]   [!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]</span><span class="sxs-lookup"><span data-stu-id="2d546-202">[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]   [!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]</span></span>

     <span data-ttu-id="2d546-203">此範例遵循版本檢查的建議做法：</span><span class="sxs-lookup"><span data-stu-id="2d546-203">This example follows the recommended practice for version checking:</span></span>

    - <span data-ttu-id="2d546-204">它會檢查 `Release` 項目的值「大於或等於」已知版本機碼的值。</span><span class="sxs-lookup"><span data-stu-id="2d546-204">It checks whether the value of the `Release` entry is *greater than or equal to* the value of the known release keys.</span></span>

    - <span data-ttu-id="2d546-205">它會從最新版本依序檢查到最舊版本。</span><span class="sxs-lookup"><span data-stu-id="2d546-205">It checks in order from most recent version to earliest version.</span></span>

<a name="ps_a"></a> 
#### <a name="to-check-for-a-minimum-required-net-framework-version-by-querying-the-registry-in-powershell-net-framework-45-and-later"></a><span data-ttu-id="2d546-206">藉由查詢 PowerShell 的登錄來檢查所需的最低 .NET Framework 版本 (.NET Framework 4.5 及更新版本)</span><span class="sxs-lookup"><span data-stu-id="2d546-206">To check for a minimum-required .NET Framework version by querying the registry in PowerShell (.NET Framework 4.5 and later)</span></span>

- <span data-ttu-id="2d546-207">下列範例會檢查 `Release` 關鍵字的值，判斷是否安裝 .NET Framework 4.6.2 或更高版本，無論 Windows 作業系統版本為何 (如果是，傳回 `True`；否則傳回 `False`)。</span><span class="sxs-lookup"><span data-stu-id="2d546-207">The following example checks the value of the `Release` keyword to determine whether .NET Framework 4.6.2 or higher is installed, regardless of Windows OS version (returning `True` if it is and `False` otherwise).</span></span>

    ```PowerShell
    Get-ChildItem "hklm:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\" | Get-ItemPropertyValue -Name Release | % { $_ -ge 394802 } 
    ```

    <span data-ttu-id="2d546-208">您可以使用下表的其他值取代上例中的 `394802` 來檢查是否有不同的所需最低 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="2d546-208">You can replace `394802` in the previous example with another value from the following table to check for a different minimum-required .NET Framework version.</span></span>
  
    |<span data-ttu-id="2d546-209">版本</span><span class="sxs-lookup"><span data-stu-id="2d546-209">Version</span></span>|<span data-ttu-id="2d546-210">DWORD 版本的最低值</span><span class="sxs-lookup"><span data-stu-id="2d546-210">Minimum value of the Release DWORD</span></span>|
    |-------------|--------------------------------|
    |<span data-ttu-id="2d546-211">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="2d546-211">.NET Framework 4.5</span></span>|<span data-ttu-id="2d546-212">378389</span><span class="sxs-lookup"><span data-stu-id="2d546-212">378389</span></span>|
    |<span data-ttu-id="2d546-213">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="2d546-213">.NET Framework 4.5.1</span></span>|<span data-ttu-id="2d546-214">378675</span><span class="sxs-lookup"><span data-stu-id="2d546-214">378675</span></span>|
    |<span data-ttu-id="2d546-215">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="2d546-215">.NET Framework 4.5.2</span></span>|<span data-ttu-id="2d546-216">379893</span><span class="sxs-lookup"><span data-stu-id="2d546-216">379893</span></span>|
    |[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|<span data-ttu-id="2d546-217">393295</span><span class="sxs-lookup"><span data-stu-id="2d546-217">393295</span></span>|
    |[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|<span data-ttu-id="2d546-218">394254</span><span class="sxs-lookup"><span data-stu-id="2d546-218">394254</span></span>|
    |[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]|<span data-ttu-id="2d546-219">394802</span><span class="sxs-lookup"><span data-stu-id="2d546-219">394802</span></span>|
    |<span data-ttu-id="2d546-220">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="2d546-220">.NET Framework 4.7</span></span>|<span data-ttu-id="2d546-221">460798</span><span class="sxs-lookup"><span data-stu-id="2d546-221">460798</span></span>|

<a name="clr_a"></a> 
#### <a name="to-find-the-current-runtime-version-by-using-the-clrver-tool"></a><span data-ttu-id="2d546-222">使用 Clrver 工具尋找目前的執行階段版本</span><span class="sxs-lookup"><span data-stu-id="2d546-222">To find the current runtime version by using the Clrver tool</span></span>

- <span data-ttu-id="2d546-223">使用 CLR 版本工具 (Clrver.exe) 判斷電腦上安裝了哪些通用語言執行平台 (CLR) 版本。</span><span class="sxs-lookup"><span data-stu-id="2d546-223">Use the CLR Version Tool (Clrver.exe) to determine which versions of the common language runtime are installed on a computer.</span></span>

     <span data-ttu-id="2d546-224">在 Visual Studio 命令提示字元中輸入 `clrver`。</span><span class="sxs-lookup"><span data-stu-id="2d546-224">From a Visual Studio Command Prompt, enter `clrver`.</span></span> <span data-ttu-id="2d546-225">這個命令產生的輸出類似下面所述：</span><span class="sxs-lookup"><span data-stu-id="2d546-225">This command produces output similar to the following:</span></span>

    ```
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

     <span data-ttu-id="2d546-226">如需使用這項工具的詳細資訊，請參閱 [Clrver.exe (CLR 版本工具)](~/docs/framework/tools/clrver-exe-clr-version-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="2d546-226">For more information about using this tool, see [Clrver.exe (CLR Version Tool)](~/docs/framework/tools/clrver-exe-clr-version-tool.md).</span></span>

<a name="clr_b"></a> 
#### <a name="to-find-the-current-runtime-version-by-querying-the-environment-class-in-code"></a><span data-ttu-id="2d546-227">若要藉由查詢程式碼中的 Environment 類別尋找目前的執行階段版本</span><span class="sxs-lookup"><span data-stu-id="2d546-227">To find the current runtime version by querying the Environment class in code</span></span>

- <span data-ttu-id="2d546-228">查詢 <xref:System.Environment.Version%2A?displayProperty=fullName> 屬性，以擷取可識別目前執行程式碼的執行階段版本的 <xref:System.Version>。</span><span class="sxs-lookup"><span data-stu-id="2d546-228">Query the <xref:System.Environment.Version%2A?displayProperty=fullName> property to retrieve a <xref:System.Version> object that identifies the version of the runtime that is currently executing the code.</span></span> <span data-ttu-id="2d546-229">您可以使用 <xref:System.Version.Major%2A?displayProperty=fullName> 屬性取得主要版本識別項 (例如，"4" 代表 4.0 版)，使用 <xref:System.Version.Minor%2A?displayProperty=fullName> 屬性取得次要版本識別項 (例如，"0" 代表 4.0 版)，或者使用 <xref:System.Object.ToString%2A?displayProperty=fullName> 方法取得整個版本字串 (例如 "4.0.30319.18010"，如下列程式碼所示)。</span><span class="sxs-lookup"><span data-stu-id="2d546-229">You can use the <xref:System.Version.Major%2A?displayProperty=fullName> property to get the major release identifier (for example, "4" for version 4.0), the <xref:System.Version.Minor%2A?displayProperty=fullName> property to get the minor release identifier (for example, "0" for version 4.0), or the <xref:System.Object.ToString%2A?displayProperty=fullName> method to get the entire version string (for example, "4.0.30319.18010", as shown in the following code).</span></span> <span data-ttu-id="2d546-230">這個屬性會傳回單一值，反映出目前執行程式碼的執行階段版本，但是不會傳回電腦上可能已安裝的組件版本或其他執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="2d546-230">This property returns a single value that reflects the version of the runtime that is currently executing the code; it does not return assembly versions or other versions of the runtime that may have been installed on the computer.</span></span>

     <span data-ttu-id="2d546-231">針對 .NET Framework 4、4.5、4.5.1 和 4.5.2 版，<xref:System.Environment.Version%2A?displayProperty=fullName> 屬性會傳回 <xref:System.Version> 物件，其字串表示的格式為 `4.0.30319.xxxxx`。</span><span class="sxs-lookup"><span data-stu-id="2d546-231">For the .NET Framework Versions 4, 4.5, 4.5.1, and 4.5.2, the <xref:System.Environment.Version%2A?displayProperty=fullName> property returns a <xref:System.Version> object whose string representation has the form `4.0.30319.xxxxx`.</span></span> <span data-ttu-id="2d546-232">針對 .NET Framework 4.6 和更新版本，其格式為 `4.0.30319.42000`。</span><span class="sxs-lookup"><span data-stu-id="2d546-232">For the .NET Framework 4.6 and later, it has the form `4.0.30319.42000`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="2d546-233">針對 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 和更新版本，不建議使用 <xref:System.Environment.Version%2A?displayProperty=fullName> 屬性來偵測執行階段的版本。</span><span class="sxs-lookup"><span data-stu-id="2d546-233">For the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] and later, we do not recommend using the  <xref:System.Environment.Version%2A?displayProperty=fullName> property to detect the version of the runtime.</span></span> <span data-ttu-id="2d546-234">相反地，建議您查詢登錄，如本文稍早的[藉由查詢程式碼中的登錄尋找 .NET Framework 版本 (.NET Framework 4.5 及更新版本)](#net_d) 一節中所述。</span><span class="sxs-lookup"><span data-stu-id="2d546-234">Instead, we recommend that you query the registry, as described in the [To find .NET Framework versions by querying the registry in code (.NET Framework 4.5 and later)](#net_d) section earlier in this article.</span></span>

     <span data-ttu-id="2d546-235">以下是查詢 <xref:System.Environment.Version%2A?displayProperty=fullName> 屬性取得執行階段版本資訊的範例：</span><span class="sxs-lookup"><span data-stu-id="2d546-235">Here's an example of querying the <xref:System.Environment.Version%2A?displayProperty=fullName> property for runtime version information:</span></span>

     <span data-ttu-id="2d546-236">[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]    [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]</span><span class="sxs-lookup"><span data-stu-id="2d546-236">[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]    [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]</span></span>

     <span data-ttu-id="2d546-237">這個範例產生的輸出類似下面所述：</span><span class="sxs-lookup"><span data-stu-id="2d546-237">The example produces output that's similar to the following:</span></span>

    ```
    Version: 4.0.30319.18010
    ```

## <a name="see-also"></a><span data-ttu-id="2d546-238">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d546-238">See Also</span></span>
 <span data-ttu-id="2d546-239">[如何：判斷安裝的 .NET Framework 更新](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md) </span><span class="sxs-lookup"><span data-stu-id="2d546-239">[How to: Determine Which .NET Framework Updates Are Installed](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md) </span></span>  
 <span data-ttu-id="2d546-240">[安裝適用於開發人員的 .NET Framework](../../../docs/framework/install/guide-for-developers.md) </span><span class="sxs-lookup"><span data-stu-id="2d546-240">[Install the .NET Framework for developers](../../../docs/framework/install/guide-for-developers.md) </span></span>  
 [<span data-ttu-id="2d546-241">版本和相依性</span><span class="sxs-lookup"><span data-stu-id="2d546-241">Versions and Dependencies</span></span>](~/docs/framework/migration-guide/versions-and-dependencies.md)

