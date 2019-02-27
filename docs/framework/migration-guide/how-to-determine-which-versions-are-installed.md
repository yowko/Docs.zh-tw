---
title: HOW TO：判斷安裝的 .NET Framework 版本
ms.date: 02/20/2019
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
ms.openlocfilehash: d7661b3ebaa8f29d6d3b2adbc56c405c8f0945f3
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56584170"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="1a4b2-102">作法：判斷安裝的 .NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="1a4b2-102">How to: Determine which .NET Framework versions are installed</span></span>

<span data-ttu-id="1a4b2-103">使用者可以在電腦上安裝及執行多個版本的 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-103">Users can install and run multiple versions of the .NET Framework on their computers.</span></span> <span data-ttu-id="1a4b2-104">當您開發或部署應用程式時，您可能需要知道使用者電腦上安裝的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-104">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user’s computer.</span></span> <span data-ttu-id="1a4b2-105">請注意，.NET Framework 包含兩個主要元件，這兩個元件的版本控制會分開處理：</span><span class="sxs-lookup"><span data-stu-id="1a4b2-105">Note that the .NET Framework consists of two main components, which are versioned separately:</span></span>  
  
- <span data-ttu-id="1a4b2-106">組件集合，這是為應用程式提供功能的類型與資源集合。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-106">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="1a4b2-107">.NET Framework 和組件會共用相同的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-107">The .NET Framework and assemblies share the same version number.</span></span>  
  
- <span data-ttu-id="1a4b2-108">通用語言執行平台 (CLR)，負責管理和執行應用程式的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-108">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="1a4b2-109">CLR 是透過自己的版本號碼加以識別 (請參閱[版本和相依性](~/docs/framework/migration-guide/versions-and-dependencies.md))。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-109">The CLR is identified by its own version number (see [Versions and Dependencies](~/docs/framework/migration-guide/versions-and-dependencies.md)).</span></span>  
  
<span data-ttu-id="1a4b2-110">若要取得電腦上安裝之 .NET Framework 版本的正確清單，您可以檢視登錄或查詢程式碼中的登錄：</span><span class="sxs-lookup"><span data-stu-id="1a4b2-110">To get an accurate list of the .NET Framework versions installed on a computer, you can view the registry or query the registry in code:</span></span>  
  
 [<span data-ttu-id="1a4b2-111">在登錄中尋找 .NET Framework 1-4 版</span><span class="sxs-lookup"><span data-stu-id="1a4b2-111">Find .NET Framework versions 1-4 in the registry</span></span>](#net_a)  
 [<span data-ttu-id="1a4b2-112">在登錄中尋找 .NET Framework 4.5 和更新版本</span><span class="sxs-lookup"><span data-stu-id="1a4b2-112">Find .NET Framework versions 4.5 and later in the registry)</span></span>](#net_b)  
 [<span data-ttu-id="1a4b2-113">使用程式碼查詢登錄 (1-4 版)</span><span class="sxs-lookup"><span data-stu-id="1a4b2-113">Using code to query the registry (versions 1-4)</span></span>](#net_c)  
 [<span data-ttu-id="1a4b2-114">使用程式碼查詢登錄 (4.5 版及更新版本)</span><span class="sxs-lookup"><span data-stu-id="1a4b2-114">Using code to query the registry (version 4.5 and later)</span></span>](#net_d)  
 [<span data-ttu-id="1a4b2-115">使用 PowerShell 查詢登錄 (4.5 版及更新版本)</span><span class="sxs-lookup"><span data-stu-id="1a4b2-115">Using PowerShell to query the registry (version 4.5 and later)</span></span>](#ps_a)  

 <span data-ttu-id="1a4b2-116">若要尋找 CLR 版本，您可以使用工具或程式碼：</span><span class="sxs-lookup"><span data-stu-id="1a4b2-116">To find the CLR version, you can use a tool or code:</span></span>  
  
 [<span data-ttu-id="1a4b2-117">使用 Clrver 工具</span><span class="sxs-lookup"><span data-stu-id="1a4b2-117">Using the Clrver tool</span></span>](#clr_a)  
 [<span data-ttu-id="1a4b2-118">使用程式碼查詢 System.Environment 類別</span><span class="sxs-lookup"><span data-stu-id="1a4b2-118">Using code to query the System.Environment class</span></span>](#clr_b)  

> [!NOTE]
> <span data-ttu-id="1a4b2-119">.NET Framework 版本和通用語言執行平台 (CLR) 版本之間有下列差異。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-119">There is a difference between the .NET Framework version and the common language runtime (CLR) version.</span></span> <span data-ttu-id="1a4b2-120">.NET Framework 的版本建立是以構成 .NET Framework Class Library 的組件集為基礎。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-120">The .NET Framework is versioned based on the set of assemblies that form the .NET Framework Class Library.</span></span> <span data-ttu-id="1a4b2-121">例如，.NET Framework 版本包含 4.5、4.6.1 和 4.7.2。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-121">For example, .NET Framework versions include 4.5, 4.6.1, and 4.7.2.</span></span> <span data-ttu-id="1a4b2-122">CLR 的版本建立是以 .NET Framework 應用程式執行的執行階段為依據，且單一 CLR 版本通常可支援多個 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-122">The CLR is versioned based on the runtime on which .NET Framework applications execute, and a single CLR version typically supports multiple .NET Framework versions.</span></span> <span data-ttu-id="1a4b2-123">CLR 4.30319.*xxxxx* 版支援 .NET Framework 4 到 4.5.2 版；CLR 4.30319.42000 版支援從 .NET Framework 4.6 起的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-123">CLR version 4.30319.*xxxxx* supports .NET Framework versions 4 through 4.5.2; CLR version 4.30319.42000 supports .NET Framework versions starting with .NET Framework 4.6.</span></span> <span data-ttu-id="1a4b2-124">如需詳細資訊，請參閱 <xref:System.Environment.Version?displayProperty=nameWithType> 屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-124">For more information, see the <xref:System.Environment.Version?displayProperty=nameWithType> property.</span></span>

 <span data-ttu-id="1a4b2-125">如需偵測每一版 .NET Framework 已安裝更新的資訊，請參閱[如何：判斷安裝的 .NET Framework 更新](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-125">For information about detecting the installed updates for each version of the .NET Framework, see [How to: Determine Which .NET Framework Updates Are Installed](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md).</span></span> <span data-ttu-id="1a4b2-126">如需安裝 .NET Framework 的資訊，請參閱[安裝適用於開發人員的 .NET Framework](../../../docs/framework/install/guide-for-developers.md)。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-126">For information about installing the .NET Framework, see [Install the .NET Framework for developers](../../../docs/framework/install/guide-for-developers.md).</span></span>  
  
<a name="net_a"></a>   
## <a name="find-net-framework-versions-1-4-in-the-registry"></a><span data-ttu-id="1a4b2-127">在登錄中尋找 .NET Framework 1-4 版</span><span class="sxs-lookup"><span data-stu-id="1a4b2-127">Find .NET Framework versions 1-4 in the registry</span></span> 
  
1.  <span data-ttu-id="1a4b2-128">在 [開始] 功能表中選擇 [執行]。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-128">On the **Start** menu, choose **Run**.</span></span>  
  
2.  <span data-ttu-id="1a4b2-129">在 [開啟] 方塊中輸入 **regedit.exe**。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-129">In the **Open** box, enter **regedit.exe**.</span></span>  
  
     <span data-ttu-id="1a4b2-130">您必須具有系統管理認證才能執行 regedit.exe。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-130">You must have administrative credentials to run regedit.exe.</span></span>  
  
3.  <span data-ttu-id="1a4b2-131">在 [登錄編輯程式] 中，開啟下列子機碼：</span><span class="sxs-lookup"><span data-stu-id="1a4b2-131">In the Registry Editor, open the following subkey:</span></span>  
  
     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP`  
  
     <span data-ttu-id="1a4b2-132">若為 .NET Framework 1.1 到 3.5 版，已安裝版本會列為 `NDP` 子機碼下方的子機碼。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-132">For .NET Framework versions 1.1 through 3.5, the installed versions are listed as subkeys under the `NDP` subkey.</span></span> <span data-ttu-id="1a4b2-133">版本號碼儲存在版本子機碼的 **Version** 項目中。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-133">The version number is stored in the version subkey's **Version** entry.</span></span> 
     
     <span data-ttu-id="1a4b2-134">若為 .NET Framework 4，則 **Version** 項目位於 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client` 子機碼下方、`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full` 子機碼下方，或這兩個子機碼下方。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-134">For .NET Framework 4, the **Version** entry is under the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client` subkey, the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full` subkey, or under both subkeys.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1a4b2-135">登錄中的 [NET Framework Setup] 資料夾不是以英文句號開頭。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-135">The "NET Framework Setup" folder in the registry does not begin with a period.</span></span>

    <span data-ttu-id="1a4b2-136">下圖顯示 .NET Framework 3.5 的子機碼與其 **Version** 項目。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-136">The following figure shows that the subkey for the .NET Framework 3.5 along with its **Version** entry.</span></span>

     <span data-ttu-id="1a4b2-137">![.NET Framework 3.5 的登錄項目。](../../../docs/framework/migration-guide/media/net-4-and-earlier.png ".NET framework 4 和更早版本")</span><span class="sxs-lookup"><span data-stu-id="1a4b2-137">![The registry entry for the .NET Framework 3.5.](../../../docs/framework/migration-guide/media/net-4-and-earlier.png ".NET Framework 4 and earlier versions")</span></span>

<a name="net_b"></a> 
## <a name="find-net-framework-versions-45-and-later-in-the-registry"></a><span data-ttu-id="1a4b2-138">在登錄中尋找 .NET Framework 4.5 和更新版本</span><span class="sxs-lookup"><span data-stu-id="1a4b2-138">Find .NET Framework versions 4.5 and later in the registry</span></span>

1. <span data-ttu-id="1a4b2-139">在 [開始] 功能表中選擇 [執行]。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-139">On the **Start** menu, choose **Run**.</span></span>

2. <span data-ttu-id="1a4b2-140">在 [開啟] 方塊中輸入 **regedit.exe**。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-140">In the **Open** box, enter **regedit.exe**.</span></span>

     <span data-ttu-id="1a4b2-141">您必須具有系統管理認證才能執行 regedit.exe。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-141">You must have administrative credentials to run regedit.exe.</span></span>

3. <span data-ttu-id="1a4b2-142">在 [登錄編輯程式] 中，開啟下列子機碼：</span><span class="sxs-lookup"><span data-stu-id="1a4b2-142">In the Registry Editor, open the following subkey:</span></span>

     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`

     <span data-ttu-id="1a4b2-143">請注意，路徑 `Full` 子機碼包含子機碼 `Net Framework` 而非`.NET Framework`。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-143">Note that the path to the `Full` subkey includes the subkey `Net Framework` rather than `.NET Framework`.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1a4b2-144">如果 `Full` 子機碼不存在，則您未安裝 .NET Framework 4.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-144">If the `Full` subkey is not present, then you do not have the .NET Framework 4.5 or later installed.</span></span>

     <span data-ttu-id="1a4b2-145">檢查名為 `Release` 的 DWORD 值。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-145">Check for a DWORD value named `Release`.</span></span> <span data-ttu-id="1a4b2-146">如果 `Release` DWORD 存在，即表示該電腦上已安裝 .NET Framework 4.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-146">The existence of the `Release` DWORD indicates that .NET Framework 4.5 or later has been installed on that computer.</span></span> <span data-ttu-id="1a4b2-147">其值為對應至 .NET Framework 特定版本的版本機碼。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-147">Its value is a release key that corresponds to a particular version of .NET Framework.</span></span> <span data-ttu-id="1a4b2-148">例如，下圖中 `Release` DWORD 的值是 378389，也就是 .NET Framework 4.5 的版本機碼。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-148">In the following figure, for example, the value of the `Release` DWORD is 378389, which is the release key for .NET Framework 4.5.</span></span> 

     <span data-ttu-id="1a4b2-149">![.NET Framework 4.5 的登錄項目。](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")</span><span class="sxs-lookup"><span data-stu-id="1a4b2-149">![The registry entry for the .NET Framework 4.5.](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")</span></span>

<span data-ttu-id="1a4b2-150">下表列出每個 .NET Framework 版本的 `Release` DWORD 最小值。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-150">The following table lists the minimum value of the `Release` DWORD for each .NET Framework version.</span></span> <span data-ttu-id="1a4b2-151">您可以依照下列方式使用這些值：</span><span class="sxs-lookup"><span data-stu-id="1a4b2-151">You can use these values as follows:</span></span>

- <span data-ttu-id="1a4b2-152">若要判斷最低的 .NET Framework 版本是否存在，請測試登錄中找到的 `Release` DWORD 值是否「大於或等於」資料表中所列的值。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-152">To determine whether a minimum .NET Framework version is present, test whether the `Release` DWORD value found in the registry is *greater than or equal to* the value listed in the table.</span></span> <span data-ttu-id="1a4b2-153">例如，如果您的應用程式需要 .NET Framework 4.7 或更新版本，您將進行測試以尋找 460798 的最低版本機碼值。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-153">For example, if your application requires .NET Framework 4.7 or later, you would test for a minimum release key value of 460798.</span></span>

- <span data-ttu-id="1a4b2-154">若要測試多個版本，請從最新的 .NET Framework 版本開始，然後依序回推每個舊版進行測試。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-154">To test for multiple versions, begin with the latest .NET Framework version, and then test for each successive earlier version.</span></span>

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

|<span data-ttu-id="1a4b2-155">.NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="1a4b2-155">.NET Framework Version</span></span>|<span data-ttu-id="1a4b2-156">Release DWORD 的值</span><span class="sxs-lookup"><span data-stu-id="1a4b2-156">Value of the Release DWORD</span></span>|
|--------------------------------|-------------|
|<span data-ttu-id="1a4b2-157">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="1a4b2-157">.NET Framework 4.5</span></span>|<span data-ttu-id="1a4b2-158">378389</span><span class="sxs-lookup"><span data-stu-id="1a4b2-158">378389</span></span>|
|<span data-ttu-id="1a4b2-159">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="1a4b2-159">.NET Framework 4.5.1</span></span>|<span data-ttu-id="1a4b2-160">378675</span><span class="sxs-lookup"><span data-stu-id="1a4b2-160">378675</span></span>|
|<span data-ttu-id="1a4b2-161">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="1a4b2-161">.NET Framework 4.5.2</span></span>|<span data-ttu-id="1a4b2-162">379893</span><span class="sxs-lookup"><span data-stu-id="1a4b2-162">379893</span></span>|
|<span data-ttu-id="1a4b2-163">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="1a4b2-163">.NET Framework 4.6</span></span>|<span data-ttu-id="1a4b2-164">393295</span><span class="sxs-lookup"><span data-stu-id="1a4b2-164">393295</span></span>|
|<span data-ttu-id="1a4b2-165">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="1a4b2-165">.NET Framework 4.6.1</span></span>|<span data-ttu-id="1a4b2-166">394254</span><span class="sxs-lookup"><span data-stu-id="1a4b2-166">394254</span></span>|
|<span data-ttu-id="1a4b2-167">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="1a4b2-167">.NET Framework 4.6.2</span></span>|<span data-ttu-id="1a4b2-168">394802</span><span class="sxs-lookup"><span data-stu-id="1a4b2-168">394802</span></span>|
|<span data-ttu-id="1a4b2-169">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="1a4b2-169">.NET Framework 4.7</span></span>|<span data-ttu-id="1a4b2-170">460798</span><span class="sxs-lookup"><span data-stu-id="1a4b2-170">460798</span></span>|
|<span data-ttu-id="1a4b2-171">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="1a4b2-171">.NET Framework 4.7.1</span></span>|<span data-ttu-id="1a4b2-172">461308</span><span class="sxs-lookup"><span data-stu-id="1a4b2-172">461308</span></span>|
|<span data-ttu-id="1a4b2-173">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="1a4b2-173">.NET Framework 4.7.2</span></span>|<span data-ttu-id="1a4b2-174">461808</span><span class="sxs-lookup"><span data-stu-id="1a4b2-174">461808</span></span>|

<span data-ttu-id="1a4b2-175">如需特定 Windows 作業系統版本的 .NET Framework 版本機碼完整資料表，請參閱 [.NET Framework 版本機碼和 Windows 作業系統版本](release-keys-and-os-versions.md)。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-175">For a complete table of release keys for the .NET Framework for specific Windows operating system versions, see [.NET Framework release keys and Windows operating system versions](release-keys-and-os-versions.md).</span></span>

<a name="net_c"></a> 
## <a name="find-net-framework-versions-1-4-with-code"></a><span data-ttu-id="1a4b2-176">使用程式碼尋找 .NET Framework 1-4 版</span><span class="sxs-lookup"><span data-stu-id="1a4b2-176">Find .NET Framework versions 1-4 with code</span></span>

- <span data-ttu-id="1a4b2-177">使用 <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> 類別來存取 Windows 登錄中 `HKEY_LOCAL_MACHINE` 分支下方的 `Software\Microsoft\NET Framework Setup\NDP\` 子機碼。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-177">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the `Software\Microsoft\NET Framework Setup\NDP\` subkey under `HKEY_LOCAL_MACHINE` branch in the Windows registry.</span></span>

     <span data-ttu-id="1a4b2-178">下列程式碼將示範此查詢的範例。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-178">The following code shows an example of this query.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1a4b2-179">這個程式碼不會示範如何偵測 .NET Framework 4.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-179">This code does not show how to detect .NET Framework 4.5 or later.</span></span> <span data-ttu-id="1a4b2-180">檢查 `Release` DWORD 即可偵測這些版本，如上一節所述。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-180">Check the `Release` DWORD to detect those versions, as described in the previous section.</span></span> <span data-ttu-id="1a4b2-181">如需可偵測 .NET Framework 4.5 或更新版本的程式碼，請參閱本文中的下一節。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-181">For code that detects .NET Framework 4.5 or later versions, see the next section in this article.</span></span>

     [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

<a name="net_d"></a> 
## <a name="find-net-framework-versions-45-and-later-with-code"></a><span data-ttu-id="1a4b2-182">使用程式碼尋找 .NET Framework 4.5 和更新版本</span><span class="sxs-lookup"><span data-stu-id="1a4b2-182">Find .NET Framework versions 4.5 and later with code</span></span>

1. <span data-ttu-id="1a4b2-183">如果 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` 機碼中存在 `Release` DWORD，即表示電腦上已安裝 .NET Framework 4.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-183">The existence of the `Release` DWORD in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key indicates that the .NET Framework 4.5 or later is installed on a computer.</span></span> <span data-ttu-id="1a4b2-184">關鍵字的值表示已安裝的版本。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-184">The value of the keyword indicates the installed version.</span></span> <span data-ttu-id="1a4b2-185">若要檢查此機碼，請使用 <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> 和 <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> 方法來存取 Windows 登錄中的子機碼。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-185">To check this keyword, use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> methods to access the subkey in the Windows registry.</span></span>

2. <span data-ttu-id="1a4b2-186">檢查 `Release` 關鍵字的值，判斷已安裝的版本。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-186">Check the value of the `Release` keyword to determine the installed version.</span></span> <span data-ttu-id="1a4b2-187">若要向前相容，您可以檢查是否有值大於或等於[在登錄中尋找 .NET Framework 4.5 和更新版本](#net_b)一節中資料表所列的值。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-187">To be forward-compatible, you can check for a value greater than or equal to the value listed in the table in the [Find .NET Framework versions 4.5 and later in the registry](#net_b) section.</span></span>

<span data-ttu-id="1a4b2-188">下列範例會檢查登錄中的 `Release` 值來判斷是否已安裝 .NET Framework 4.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-188">The following example checks the `Release` value in the registry to determine whether .NET Framework 4.5 or a later version is installed.</span></span>

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

<span data-ttu-id="1a4b2-189">此範例遵循版本檢查的建議做法：</span><span class="sxs-lookup"><span data-stu-id="1a4b2-189">This example follows the recommended practice for version checking:</span></span>

- <span data-ttu-id="1a4b2-190">它會檢查 `Release` 項目的值「大於或等於」已知版本機碼的值。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-190">It checks whether the value of the `Release` entry is *greater than or equal to* the value of the known release keys.</span></span>

- <span data-ttu-id="1a4b2-191">它會從最新版本依序檢查到最舊版本。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-191">It checks in order from most recent version to earliest version.</span></span>

<a name="ps_a"></a> 
## <a name="check-for-a-minimum-required-net-framework-version-45-and-later-with-powershell"></a><span data-ttu-id="1a4b2-192">使用 PowerShell 檢查 .NET Framework 最低版本需求 (4.5 及更新版本)</span><span class="sxs-lookup"><span data-stu-id="1a4b2-192">Check for a minimum required .NET Framework version (4.5 and later) with PowerShell</span></span>

<span data-ttu-id="1a4b2-193">下列範例會檢查 `Release` 關鍵字的值，判斷是否已安裝 .NET Framework 4.6.2 或更新版本 (如果是，傳回 `True`；否則傳回 `False`)。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-193">The following example checks the value of the `Release` keyword to determine whether .NET Framework 4.6.2 or higher is installed (returning `True` if it is and `False` otherwise).</span></span>

    ```PowerShell
    # PowerShell 5
    Get-ChildItem 'HKLM:\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\' | Get-ItemPropertyValue -Name Release | Foreach-Object { $_ -ge 394802 } 
    ```

    ```PowerShell
    # PowerShell 4
    (Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -gt 394802
    ```

    You can replace `394802` in the previous example with another value from the following table in the [Find .NET Framework versions 4.5 and later in the registry](#net_b) section to check for a different minimum required .NET Framework version.
  
<a name="clr_a"></a> 
## <a name="find-the-current-clr-version-with-clrverexe"></a><span data-ttu-id="1a4b2-194">使用 Clrver.exe 尋找目前的 CLR 版本</span><span class="sxs-lookup"><span data-stu-id="1a4b2-194">Find the current CLR version with Clrver.exe</span></span>

<span data-ttu-id="1a4b2-195">使用 CLR 版本工具 (Clrver.exe) 判斷電腦上安裝了哪些通用語言執行平台 (CLR) 版本。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-195">Use the CLR Version Tool (Clrver.exe) to determine which versions of the common language runtime are installed on a computer.</span></span>

<span data-ttu-id="1a4b2-196">從 Visual Studio 開發人員命令提示字元輸入 `clrver`。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-196">From a Developer Command Prompt for Visual Studio, enter `clrver`.</span></span> <span data-ttu-id="1a4b2-197">這個命令產生的輸出類似下面所述：</span><span class="sxs-lookup"><span data-stu-id="1a4b2-197">This command produces output similar to the following:</span></span>

```console
Versions installed on the machine:
v2.0.50727
v4.0.30319
```

<span data-ttu-id="1a4b2-198">如需使用這項工具的詳細資訊，請參閱 [Clrver.exe (CLR 版本工具)](~/docs/framework/tools/clrver-exe-clr-version-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-198">For more information about using this tool, see [Clrver.exe (CLR Version Tool)](~/docs/framework/tools/clrver-exe-clr-version-tool.md).</span></span>

<a name="clr_b"></a> 
## <a name="find-the-current-clr-version-with-the-environment-class"></a><span data-ttu-id="1a4b2-199">使用環境類別尋找目前的 CLR 版本</span><span class="sxs-lookup"><span data-stu-id="1a4b2-199">Find the current CLR version with the Environment class</span></span>

<span data-ttu-id="1a4b2-200">透過擷取 <xref:System.Environment.Version?displayProperty=nameWithType> 屬性值，您可以擷取 <xref:System.Version> 來識別目前執行程式碼的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-200">You can retrieve the value of the <xref:System.Environment.Version?displayProperty=nameWithType> property to retrieve a <xref:System.Version> object that identifies the version of the runtime that is currently executing the code.</span></span> <span data-ttu-id="1a4b2-201">這個屬性會傳回單一值，以反映出目前執行程式碼的執行階段版本，但是不會傳回電腦上可能已安裝的組件版本或其他執行階段版本。您可以使用 <xref:System.Version.Major%2A?displayProperty=nameWithType> 屬性取得主要版本識別碼 (例如，"4" 代表 4.0 版)、使用 <xref:System.Version.Minor%2A?displayProperty=nameWithType> 屬性取得次要版本識別碼 (例如，"0" 代表 4.0 版)，或使用 <xref:System.Version.ToString%2A?displayProperty=nameWithType> 方法取得整個版本字串 (例如 "4.0.30319.18010"，如下列程式碼所示)。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-201">This property returns a single value that reflects the version of the runtime that is currently executing the code; it does not return assembly versions or other versions of the runtime that may have been installed on the computer.You can use the <xref:System.Version.Major%2A?displayProperty=nameWithType> property to get the major release identifier (for example, "4" for version 4.0), the <xref:System.Version.Minor%2A?displayProperty=nameWithType> property to get the minor release identifier (for example, "0" for version 4.0), or the <xref:System.Version.ToString%2A?displayProperty=nameWithType> method to get the entire version string (for example, "4.0.30319.18010", as shown in the following code).</span></span> 

<span data-ttu-id="1a4b2-202">針對 .NET Framework 4、4.5、4.5.1 和 4.5.2 版，<xref:System.Environment.Version%2A?displayProperty=nameWithType> 屬性會傳回 <xref:System.Version> 物件，其字串表示的格式為 `4.0.30319.xxxxx`。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-202">For the .NET Framework Versions 4, 4.5, 4.5.1, and 4.5.2, the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property returns a <xref:System.Version> object whose string representation has the form `4.0.30319.xxxxx`.</span></span> <span data-ttu-id="1a4b2-203">針對 .NET Framework 4.6 和更新版本，其格式為 `4.0.30319.42000`。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-203">For the .NET Framework 4.6 and later, it has the form `4.0.30319.42000`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1a4b2-204">針對 .NET Framework 4.5 和更新版本，不建議使用 <xref:System.Environment.Version%2A?displayProperty=nameWithType> 屬性來偵測執行階段的版本。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-204">For the .NET Framework 4.5 and later, we do not recommend using the  <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to detect the version of the runtime.</span></span> <span data-ttu-id="1a4b2-205">相反地，建議您查詢登錄，如本文稍早的[藉由查詢程式碼中的登錄尋找 .NET Framework 版本 (.NET Framework 4.5 及更新版本)](#net_d) 一節中所述。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-205">Instead, we recommend that you query the registry, as described in the [To find .NET Framework versions by querying the registry in code (.NET Framework 4.5 and later)](#net_d) section earlier in this article.</span></span>

<span data-ttu-id="1a4b2-206">下列範例使用 <xref:System.Environment.Version%2A?displayProperty=nameWithType> 屬性來擷取執行階段版本資訊：</span><span class="sxs-lookup"><span data-stu-id="1a4b2-206">The following example used the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to retrieve runtime version information:</span></span>

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a><span data-ttu-id="1a4b2-207">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a4b2-207">See also</span></span>

- [<span data-ttu-id="1a4b2-208">如何：判斷安裝的 .NET Framework 更新</span><span class="sxs-lookup"><span data-stu-id="1a4b2-208">How to: Determine Which .NET Framework Updates Are Installed</span></span>](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)
- [<span data-ttu-id="1a4b2-209">安裝適用於開發人員的 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1a4b2-209">Install the .NET Framework for developers</span></span>](../../../docs/framework/install/guide-for-developers.md)
- [<span data-ttu-id="1a4b2-210">版本和相依性</span><span class="sxs-lookup"><span data-stu-id="1a4b2-210">Versions and Dependencies</span></span>](~/docs/framework/migration-guide/versions-and-dependencies.md)
