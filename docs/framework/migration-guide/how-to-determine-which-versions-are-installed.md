---
title: 判斷安裝的 .NET Framework 版本
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
ms.custom: updateeachrelease
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
ms.openlocfilehash: b860aac01780acb67c53e822eff478b78198996b
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738198"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="0692c-102">如何：判斷安裝的 .NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="0692c-102">How to: Determine which .NET Framework versions are installed</span></span>

<span data-ttu-id="0692c-103">使用者可以在電腦上[安裝](../install/index.md)及執行多個版本的 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="0692c-103">Users can [install](../install/index.md) and run multiple versions of the .NET Framework on their computers.</span></span> <span data-ttu-id="0692c-104">當您開發或部署應用程式時，您可能需要知道使用者電腦上安裝的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="0692c-104">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user’s computer.</span></span>

<span data-ttu-id="0692c-105">.NET Framework 包含兩個主要元件，各有各的版本控制：</span><span class="sxs-lookup"><span data-stu-id="0692c-105">The .NET Framework consists of two main components, which are versioned separately:</span></span>

- <span data-ttu-id="0692c-106">組件集合，這是為應用程式提供功能的類型與資源集合。</span><span class="sxs-lookup"><span data-stu-id="0692c-106">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="0692c-107">.NET Framework 和組件會共用相同的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="0692c-107">The .NET Framework and assemblies share the same version number.</span></span>

- <span data-ttu-id="0692c-108">通用語言執行平台 (CLR)，負責管理和執行應用程式的程式碼。</span><span class="sxs-lookup"><span data-stu-id="0692c-108">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="0692c-109">CLR 是透過自己的版本號碼加以識別（請參閱[版本和](versions-and-dependencies.md)相依性）。</span><span class="sxs-lookup"><span data-stu-id="0692c-109">The CLR is identified by its own version number (see [Versions and dependencies](versions-and-dependencies.md)).</span></span>

> [!NOTE]
> <span data-ttu-id="0692c-110">每一個新的 .NET Framework 版本都會保留舊版的功能並增加新的功能。</span><span class="sxs-lookup"><span data-stu-id="0692c-110">Each new version of the .NET Framework retains features from the previous versions and adds new features.</span></span> <span data-ttu-id="0692c-111">您可同時在一部電腦上載入多個版本的 .NET Framework，這表示您可以安裝 .NET Framework，卻不必解除安裝舊版。</span><span class="sxs-lookup"><span data-stu-id="0692c-111">You can load multiple versions of the .NET Framework on a single computer at the same time, which means that you can install the .NET Framework without having to uninstall previous versions.</span></span> <span data-ttu-id="0692c-112">一般而言，您不應該解除安裝舊版的 .NET Framework，因為您使用的應用程式可能依賴某個特定版本，而若移除該版本則應用程式可能會中斷。</span><span class="sxs-lookup"><span data-stu-id="0692c-112">In general, you shouldn't uninstall previous versions of the .NET Framework, because an application you use may depend on a specific version and may break if that version is removed.</span></span>
>
> <span data-ttu-id="0692c-113">.NET Framework 版本和 CLR 版本之間有差異：</span><span class="sxs-lookup"><span data-stu-id="0692c-113">There is a difference between the .NET Framework version and the CLR version:</span></span>
>
> - <span data-ttu-id="0692c-114">.NET Framework 版本是以構成 .NET Framework Class Library 的組件集為基礎。</span><span class="sxs-lookup"><span data-stu-id="0692c-114">The .NET Framework version is based on the set of assemblies that form the .NET Framework class library.</span></span> <span data-ttu-id="0692c-115">例如，.NET Framework 版本包含 4.5、4.6.1 和 4.7.2。</span><span class="sxs-lookup"><span data-stu-id="0692c-115">For example, .NET Framework versions include 4.5, 4.6.1, and 4.7.2.</span></span>
> - <span data-ttu-id="0692c-116">CLR 版本是以 .NET Framework 應用程式執行所在的執行階段為基礎。</span><span class="sxs-lookup"><span data-stu-id="0692c-116">The CLR version is based on the runtime on which .NET Framework applications execute.</span></span> <span data-ttu-id="0692c-117">單一的 CLR 版本通常會支援多個 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="0692c-117">A single CLR version typically supports multiple .NET Framework versions.</span></span> <span data-ttu-id="0692c-118">例如，CLR 4.0.30319.*xxxxx* 版支援 .NET Framework 4 到 4.5.2 版，其中 *xxxxx* 會小於 42000，而 CLR 4.0.30319.42000 版支援從 .NET Framework 4.6 起的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="0692c-118">For example, CLR version 4.0.30319.*xxxxx* supports .NET Framework versions 4 through 4.5.2, where *xxxxx* is less than 42000, and CLR version 4.0.30319.42000 supports .NET Framework versions starting with .NET Framework 4.6.</span></span>
>
> <span data-ttu-id="0692c-119">如需版本的詳細資訊，請參閱 [.NET Framework 版本和相依性](versions-and-dependencies.md)。</span><span class="sxs-lookup"><span data-stu-id="0692c-119">For more information about versions, see [.NET Framework versions and dependencies](versions-and-dependencies.md).</span></span>

<span data-ttu-id="0692c-120">登錄包含電腦上安裝的 .NET Framework 版本清單。</span><span class="sxs-lookup"><span data-stu-id="0692c-120">The registry contains a list of the .NET Framework versions installed on a computer.</span></span> <span data-ttu-id="0692c-121">您可以使用 [登錄編輯程式] 來查看登錄，或利用程式碼查詢它：</span><span class="sxs-lookup"><span data-stu-id="0692c-121">You can either use the Registry Editor to view the registry or query it with code:</span></span>

- <span data-ttu-id="0692c-122">尋找新版的 .NET Framework (4.5 和更新版本)：</span><span class="sxs-lookup"><span data-stu-id="0692c-122">Find newer .NET Framework versions (4.5 and later):</span></span>

  - [<span data-ttu-id="0692c-123">使用登錄編輯程式尋找 .NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="0692c-123">Use the Registry Editor to find .NET Framework versions</span></span>](#net_b)
  - [<span data-ttu-id="0692c-124">使用程式碼查詢登錄以取得 .NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="0692c-124">Use code to query the registry for .NET Framework versions</span></span>](#net_d)
  - [<span data-ttu-id="0692c-125">使用 PowerShell 查詢登錄以取得 .NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="0692c-125">Use PowerShell to query the registry for .NET Framework versions</span></span>](#ps_a)

- <span data-ttu-id="0692c-126">尋找較舊的 .NET Framework 版本（1到4）：</span><span class="sxs-lookup"><span data-stu-id="0692c-126">Find older .NET Framework versions (1 through 4):</span></span>

  - [<span data-ttu-id="0692c-127">使用登錄編輯程式尋找 .NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="0692c-127">Use the Registry Editor to find .NET Framework versions</span></span>](#net_a)
  - [<span data-ttu-id="0692c-128">使用程式碼查詢登錄以取得 .NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="0692c-128">Use code to query the registry for .NET Framework versions</span></span>](#net_c)

<span data-ttu-id="0692c-129">使用工具或程式碼取得安裝在電腦上的 CLR 版本清單：</span><span class="sxs-lookup"><span data-stu-id="0692c-129">To get a list of the CLR versions installed on a computer, use a tool or code:</span></span>

- [<span data-ttu-id="0692c-130">使用 Clrver 工具</span><span class="sxs-lookup"><span data-stu-id="0692c-130">Use the Clrver tool</span></span>](#clr_a)
- [<span data-ttu-id="0692c-131">使用程式碼查詢 Environment 類別</span><span class="sxs-lookup"><span data-stu-id="0692c-131">Use code to query the Environment class</span></span>](#clr_b)

<span data-ttu-id="0692c-132">如需偵測每個 .NET Framework 版本之已安裝更新的詳細資訊，請參閱[如何：判斷已安裝的 .NET Framework 更新](how-to-determine-which-net-framework-updates-are-installed.md)。</span><span class="sxs-lookup"><span data-stu-id="0692c-132">For information about detecting the installed updates for each version of the .NET Framework, see [How to: Determine which .NET Framework updates are installed](how-to-determine-which-net-framework-updates-are-installed.md).</span></span>

## <a name="find-newer-net-framework-versions-45-and-later"></a><span data-ttu-id="0692c-133">尋找新版的 .NET Framework (4.5 和更新版本)</span><span class="sxs-lookup"><span data-stu-id="0692c-133">Find newer .NET Framework versions (4.5 and later)</span></span>

<span data-ttu-id="0692c-134">您可以使用登錄編輯程式來尋找登錄中的版本資訊，或是以程式設計方式來查詢登錄。</span><span class="sxs-lookup"><span data-stu-id="0692c-134">You can use Registry Editor to find version information in the registry, or you can query the registry programmatically.</span></span>

<a name="net_b"></a>

### <a name="use-registry-editor"></a><span data-ttu-id="0692c-135">使用登錄編輯程式</span><span class="sxs-lookup"><span data-stu-id="0692c-135">Use Registry Editor</span></span>

1. <span data-ttu-id="0692c-136">從 [開始] 功能表上，選擇 [執行]，輸入 *regedit*，然後選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="0692c-136">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

     <span data-ttu-id="0692c-137">您必須具有系統管理認證才能執行 regedit。</span><span class="sxs-lookup"><span data-stu-id="0692c-137">You must have administrative credentials to run regedit.</span></span>

2. <span data-ttu-id="0692c-138">在 [登錄編輯程式] 中，開啟下列子機碼： **HKEY_LOCAL_MACHINE \Software\microsoft\net Framework Setup\NDP\v4\Full**。</span><span class="sxs-lookup"><span data-stu-id="0692c-138">In the Registry Editor, open the following subkey: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full**.</span></span> <span data-ttu-id="0692c-139">如果 **Full** 子機碼不存在，即表示未安裝 .NET Framework 4.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="0692c-139">If the **Full** subkey isn't present, then you don't have the .NET Framework 4.5 or later installed.</span></span>

    > [!NOTE]
    > <span data-ttu-id="0692c-140">登錄中的 **NET Framework Setup** 資料夾「不是」以英文句號開頭。</span><span class="sxs-lookup"><span data-stu-id="0692c-140">The **NET Framework Setup** folder in the registry does *not* begin with a period.</span></span>

3. <span data-ttu-id="0692c-141">檢查是否有名為 **Release** 的 DWORD 項目。</span><span class="sxs-lookup"><span data-stu-id="0692c-141">Check for a DWORD entry named **Release**.</span></span> <span data-ttu-id="0692c-142">如果已存在，則您已安裝 .NET Framework 4.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="0692c-142">If it exists, then you have .NET Framework 4.5 or later installed.</span></span> <span data-ttu-id="0692c-143">其值為對應至 .NET Framework 特定版本的版本機碼。</span><span class="sxs-lookup"><span data-stu-id="0692c-143">Its value is a release key that corresponds to a particular version of the .NET Framework.</span></span> <span data-ttu-id="0692c-144">例如，在下圖中， **release**專案的值是378389，也就是 .NET Framework 4.5 的發行金鑰。</span><span class="sxs-lookup"><span data-stu-id="0692c-144">In the following figure, for example, the value of the **Release** entry is 378389, which is the release key for .NET Framework 4.5.</span></span>

   <span data-ttu-id="0692c-145">![.NET Framework 4.5 的登錄專案](./media/clr-installdir.png ".NET Framework 4.5 的登錄專案")</span><span class="sxs-lookup"><span data-stu-id="0692c-145">![Registry entry for the .NET Framework 4.5](./media/clr-installdir.png "Registry entry for the .NET Framework 4.5")</span></span>

<span data-ttu-id="0692c-146">下表列出 .NET Framework 4.5 及更新版本個別作業系統上 **Release** DWORD 的值。</span><span class="sxs-lookup"><span data-stu-id="0692c-146">The following table lists the value of the **Release** DWORD on individual operating systems for .NET Framework 4.5 and later versions.</span></span>

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

<a name="version_table"></a>

|<span data-ttu-id="0692c-147">.NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="0692c-147">.NET Framework version</span></span>|<span data-ttu-id="0692c-148">Release DWORD 的值</span><span class="sxs-lookup"><span data-stu-id="0692c-148">Value of the Release DWORD</span></span>|
|--------------------------------|-------------|
|<span data-ttu-id="0692c-149">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="0692c-149">.NET Framework 4.5</span></span>|<span data-ttu-id="0692c-150">所有 Windows 作業系統：378389</span><span class="sxs-lookup"><span data-stu-id="0692c-150">All Windows operating systems: 378389</span></span>|
|<span data-ttu-id="0692c-151">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="0692c-151">.NET Framework 4.5.1</span></span>|<span data-ttu-id="0692c-152">在 Windows 8.1 和 Windows Server 2012 R2 上：378675</span><span class="sxs-lookup"><span data-stu-id="0692c-152">On Windows 8.1 and Windows Server 2012 R2: 378675</span></span><br /><span data-ttu-id="0692c-153">在其他所有 Windows 作業系統上：378758</span><span class="sxs-lookup"><span data-stu-id="0692c-153">On all other Windows operating systems: 378758</span></span>|
|<span data-ttu-id="0692c-154">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="0692c-154">.NET Framework 4.5.2</span></span>|<span data-ttu-id="0692c-155">所有 Windows 作業系統：379893</span><span class="sxs-lookup"><span data-stu-id="0692c-155">All Windows operating systems: 379893</span></span>|
|<span data-ttu-id="0692c-156">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="0692c-156">.NET Framework 4.6</span></span>|<span data-ttu-id="0692c-157">在 Windows 10: 393295 上</span><span class="sxs-lookup"><span data-stu-id="0692c-157">On Windows 10: 393295</span></span><br /><span data-ttu-id="0692c-158">在其他所有 Windows 作業系統上：393297</span><span class="sxs-lookup"><span data-stu-id="0692c-158">On all other Windows operating systems: 393297</span></span>|
|<span data-ttu-id="0692c-159">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="0692c-159">.NET Framework 4.6.1</span></span>|<span data-ttu-id="0692c-160">Windows 10 11 月更新系統：394254</span><span class="sxs-lookup"><span data-stu-id="0692c-160">On Windows 10 November Update systems: 394254</span></span><br /><span data-ttu-id="0692c-161">在所有其他 Windows 作業系統上（包括 Windows 10）：394271</span><span class="sxs-lookup"><span data-stu-id="0692c-161">On all other Windows operating systems (including Windows 10): 394271</span></span>|
|<span data-ttu-id="0692c-162">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="0692c-162">.NET Framework 4.6.2</span></span>|<span data-ttu-id="0692c-163">Windows 10 年度更新版及 Windows Server 2016：394802</span><span class="sxs-lookup"><span data-stu-id="0692c-163">On Windows 10 Anniversary Update and Windows Server 2016: 394802</span></span><br /><span data-ttu-id="0692c-164">在所有其他 Windows 作業系統（包括其他 Windows 10 作業系統）上：394806</span><span class="sxs-lookup"><span data-stu-id="0692c-164">On all other Windows operating systems (including other Windows 10 operating systems): 394806</span></span>|
|<span data-ttu-id="0692c-165">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="0692c-165">.NET Framework 4.7</span></span>|<span data-ttu-id="0692c-166">Windows 10 Creators Update：460798</span><span class="sxs-lookup"><span data-stu-id="0692c-166">On Windows 10 Creators Update: 460798</span></span><br /><span data-ttu-id="0692c-167">在所有其他 Windows 作業系統（包括其他 Windows 10 作業系統）上：460805</span><span class="sxs-lookup"><span data-stu-id="0692c-167">On all other Windows operating systems (including other Windows 10 operating systems): 460805</span></span>|
|<span data-ttu-id="0692c-168">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="0692c-168">.NET Framework 4.7.1</span></span>|<span data-ttu-id="0692c-169">Windows 10 秋季建立者更新和 Windows Server，版本1709：461308</span><span class="sxs-lookup"><span data-stu-id="0692c-169">On Windows 10 Fall Creators Update and Windows Server, version 1709: 461308</span></span><br/><span data-ttu-id="0692c-170">在所有其他 Windows 作業系統（包括其他 Windows 10 作業系統）上：461310</span><span class="sxs-lookup"><span data-stu-id="0692c-170">On all other Windows operating systems (including other Windows 10 operating systems): 461310</span></span>|
|<span data-ttu-id="0692c-171">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="0692c-171">.NET Framework 4.7.2</span></span>|<span data-ttu-id="0692c-172">Windows 10 2018 年4月更新和 Windows Server，版本1803：461808</span><span class="sxs-lookup"><span data-stu-id="0692c-172">On Windows 10 April 2018 Update and Windows Server, version 1803: 461808</span></span><br/><span data-ttu-id="0692c-173">在 Windows 10 2018 年4月更新和 Windows Server 的所有 Windows 作業系統上，版本1803：461814</span><span class="sxs-lookup"><span data-stu-id="0692c-173">On all Windows operating systems other than Windows 10 April 2018 Update and Windows Server, version 1803: 461814</span></span>|
|<span data-ttu-id="0692c-174">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="0692c-174">.NET Framework 4.8</span></span>|<span data-ttu-id="0692c-175">在 Windows 10 5 月2019更新和 Windows 10 十一月2019更新：528040</span><span class="sxs-lookup"><span data-stu-id="0692c-175">On Windows 10 May 2019 Update and Windows 10 November 2019 Update: 528040</span></span><br/><span data-ttu-id="0692c-176">在所有其他 Windows 作業系統（包括其他 Windows 10 作業系統）上：528049</span><span class="sxs-lookup"><span data-stu-id="0692c-176">On all other Windows operating systems (including other Windows 10 operating systems): 528049</span></span>|

#### <a name="specific-version"></a><span data-ttu-id="0692c-177">特定版本</span><span class="sxs-lookup"><span data-stu-id="0692c-177">Specific version</span></span>

<span data-ttu-id="0692c-178">若要判斷特定版本的 Windows 作業系統是否已安裝*特定*版本的 .NET Framework，請測試**Release** DWORD 值是否*等於*資料表中所列的值。</span><span class="sxs-lookup"><span data-stu-id="0692c-178">To determine whether a *specific* version of the .NET Framework is installed on a particular version of the Windows operating system, test whether the **Release** DWORD value is *equal to* the value listed in the table.</span></span> <span data-ttu-id="0692c-179">例如，若要判斷 Windows 10 系統上是否有 .NET Framework 4.6，請測試「等於」393295 的 **Release** 值。</span><span class="sxs-lookup"><span data-stu-id="0692c-179">For example, to determine whether .NET Framework 4.6 is present on a Windows 10 system, test for the a **Release** value that is *equal to* 393295.</span></span>

#### <a name="minimum-version"></a><span data-ttu-id="0692c-180">最小版本</span><span class="sxs-lookup"><span data-stu-id="0692c-180">Minimum version</span></span>

<span data-ttu-id="0692c-181">若要判斷 .NET Framework 的*最低*版本是否存在，請使用上表中該版本的最小**RELEASE** DWORD 值。</span><span class="sxs-lookup"><span data-stu-id="0692c-181">To determine whether a *minimum* version of the .NET Framework is present, use the smallest **RELEASE** DWORD value for that version from the previous table.</span></span> <span data-ttu-id="0692c-182">（為了方便起見，最小值也會列在下表中）。</span><span class="sxs-lookup"><span data-stu-id="0692c-182">(For convenience, the minimum values are also listed in the table that follows.)</span></span>

<span data-ttu-id="0692c-183">例如，如果您的應用程式是在 .NET Framework 4.8 或更新版本下執行，請測試*大於或等於*528040 的**RELEASE** DWORD 值。</span><span class="sxs-lookup"><span data-stu-id="0692c-183">For example, if your application runs under .NET Framework 4.8 or a later version, test for a **RELEASE** DWORD value that is *greater than or equal to* 528040.</span></span>

|<span data-ttu-id="0692c-184">.NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="0692c-184">.NET Framework version</span></span>|<span data-ttu-id="0692c-185">DWORD 版本的最低值</span><span class="sxs-lookup"><span data-stu-id="0692c-185">Minimum value of the Release DWORD</span></span>|
|--------------------------------|-------------|
|<span data-ttu-id="0692c-186">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="0692c-186">.NET Framework 4.5</span></span>|<span data-ttu-id="0692c-187">378389</span><span class="sxs-lookup"><span data-stu-id="0692c-187">378389</span></span>|
|<span data-ttu-id="0692c-188">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="0692c-188">.NET Framework 4.5.1</span></span>|<span data-ttu-id="0692c-189">378675</span><span class="sxs-lookup"><span data-stu-id="0692c-189">378675</span></span>|
|<span data-ttu-id="0692c-190">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="0692c-190">.NET Framework 4.5.2</span></span>|<span data-ttu-id="0692c-191">379893</span><span class="sxs-lookup"><span data-stu-id="0692c-191">379893</span></span>|
|<span data-ttu-id="0692c-192">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="0692c-192">.NET Framework 4.6</span></span>|<span data-ttu-id="0692c-193">393295</span><span class="sxs-lookup"><span data-stu-id="0692c-193">393295</span></span>|
|<span data-ttu-id="0692c-194">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="0692c-194">.NET Framework 4.6.1</span></span>|<span data-ttu-id="0692c-195">394254</span><span class="sxs-lookup"><span data-stu-id="0692c-195">394254</span></span>|
|<span data-ttu-id="0692c-196">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="0692c-196">.NET Framework 4.6.2</span></span>|<span data-ttu-id="0692c-197">394802</span><span class="sxs-lookup"><span data-stu-id="0692c-197">394802</span></span>|
|<span data-ttu-id="0692c-198">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="0692c-198">.NET Framework 4.7</span></span>|<span data-ttu-id="0692c-199">460798</span><span class="sxs-lookup"><span data-stu-id="0692c-199">460798</span></span>|
|<span data-ttu-id="0692c-200">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="0692c-200">.NET Framework 4.7.1</span></span>|<span data-ttu-id="0692c-201">461308</span><span class="sxs-lookup"><span data-stu-id="0692c-201">461308</span></span>|
|<span data-ttu-id="0692c-202">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="0692c-202">.NET Framework 4.7.2</span></span>|<span data-ttu-id="0692c-203">461808</span><span class="sxs-lookup"><span data-stu-id="0692c-203">461808</span></span>|
|<span data-ttu-id="0692c-204">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="0692c-204">.NET Framework 4.8</span></span>|<span data-ttu-id="0692c-205">528040</span><span class="sxs-lookup"><span data-stu-id="0692c-205">528040</span></span>|

#### <a name="multiple-versions"></a><span data-ttu-id="0692c-206">多個版本</span><span class="sxs-lookup"><span data-stu-id="0692c-206">Multiple versions</span></span>

<span data-ttu-id="0692c-207">若要測試多個版本，請從測試「大於或等於」最新版 .NET Framework 的較小 DWORD 值開始，然後將值與每一後續較早版本的較小 DWORD 值進行比較。</span><span class="sxs-lookup"><span data-stu-id="0692c-207">To test for multiple versions, begin by testing for a value that is *greater than or equal to* the smaller DWORD value for the latest .NET Framework version, and then compare the value with the smaller DWORD value for each successive earlier version.</span></span> <span data-ttu-id="0692c-208">例如，如果應用程式需要 .NET Framework 4.7 或更新版本，而且您想要判斷現有 .NET Framework 的特定版本，請從測試「大於或等於」461808 (.NET Framework 4.7.2 的較小 DWORD 值) 的 **RELEASE** DWORD 值開始。</span><span class="sxs-lookup"><span data-stu-id="0692c-208">For example, if your application requires .NET Framework 4.7 or later and you want to determine the specific version of .NET Framework present, start by testing for a **RELEASE** DWORD value that is *great than or equal to* to 461808 (the smaller DWORD value for .NET Framework 4.7.2).</span></span> <span data-ttu-id="0692c-209">然後將 **RELEASE** DWORD 值與每一更新版本 .NET Framework 的較小值進行比較。</span><span class="sxs-lookup"><span data-stu-id="0692c-209">Then compare the **RELEASE** DWORD value with the smaller value for each later .NET Framework version.</span></span>

<a name="net_d"></a>

### <a name="query-the-registry-using-code"></a><span data-ttu-id="0692c-210">使用程式碼查詢登錄</span><span class="sxs-lookup"><span data-stu-id="0692c-210">Query the registry using code</span></span>

1. <span data-ttu-id="0692c-211">使用 <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> 和 <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> 方法存取 Windows 登錄中的 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** 子機碼。</span><span class="sxs-lookup"><span data-stu-id="0692c-211">Use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> methods to access the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** subkey in the Windows registry.</span></span>

   <span data-ttu-id="0692c-212">**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** 子機碼中存在 **Release** DWORD 項目表示 .NET Framework 4.5 或更新版本已安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="0692c-212">The existence of the **Release** DWORD entry in the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** subkey indicates that the .NET Framework 4.5 or a later version is installed on a computer.</span></span>

2. <span data-ttu-id="0692c-213">檢查 **Release** 項目的值，判斷已安裝的版本。</span><span class="sxs-lookup"><span data-stu-id="0692c-213">Check the value of the **Release** entry to determine the installed version.</span></span> <span data-ttu-id="0692c-214">若要正向相容，請檢查是否有大於或等於 [.NET Framework 版本表](#version_table)中所列值的值。</span><span class="sxs-lookup"><span data-stu-id="0692c-214">To be forward-compatible, check for a value greater than or equal to the value listed in the [.NET Framework version table](#version_table).</span></span>

<span data-ttu-id="0692c-215">下列範例會檢查登錄中的 **Release** 項目值，尋找已安裝的 .NET Framework 4.5 和更新版本：</span><span class="sxs-lookup"><span data-stu-id="0692c-215">The following example checks the value of the **Release** entry in the registry to find the .NET Framework 4.5 and later versions that are installed:</span></span>

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

<span data-ttu-id="0692c-216">此範例遵循版本檢查的建議做法：</span><span class="sxs-lookup"><span data-stu-id="0692c-216">This example follows the recommended practice for version checking:</span></span>

- <span data-ttu-id="0692c-217">它會檢查 **Release** 項目值是否「大於或等於」已知版本機碼的值。</span><span class="sxs-lookup"><span data-stu-id="0692c-217">It checks whether the value of the **Release** entry is *greater than or equal to* the value of the known release keys.</span></span>

- <span data-ttu-id="0692c-218">它會從最新版本依序檢查到最舊版本。</span><span class="sxs-lookup"><span data-stu-id="0692c-218">It checks in order from most recent version to earliest version.</span></span>

<a name="ps_a"></a>

### <a name="use-powershell-to-check-for-a-minimum-required-version"></a><span data-ttu-id="0692c-219">使用 PowerShell 檢查是否有最小必要版本</span><span class="sxs-lookup"><span data-stu-id="0692c-219">Use PowerShell to check for a minimum-required version</span></span>

<span data-ttu-id="0692c-220">使用 PowerShell 命令檢查 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** 子機碼的 **Release** 項目值。</span><span class="sxs-lookup"><span data-stu-id="0692c-220">Use PowerShell commands to check the value of the **Release** entry of the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** subkey.</span></span>

<span data-ttu-id="0692c-221">下列範例會檢查 **Release** 項目值，以判斷是否安裝了 .NET Framework 4.6.2 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="0692c-221">The following examples check the value of the **Release** entry to determine whether the .NET Framework 4.6.2 or later is installed.</span></span> <span data-ttu-id="0692c-222">如已安裝，則此程式碼會傳回 `True`；否則傳回 `False`。</span><span class="sxs-lookup"><span data-stu-id="0692c-222">This code returns `True` if it's installed and `False` otherwise.</span></span>

```PowerShell
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

<span data-ttu-id="0692c-223">若要檢查是否有不同的最低需求 .NET Framework 版本，請將範例中的 `394802` 取代為[.NET Framework 版本資料表](#version_table)中的值。</span><span class="sxs-lookup"><span data-stu-id="0692c-223">To check for a different minimum-required .NET Framework version, replace `394802` in the example with a value from the [.NET Framework version table](#version_table).</span></span> <span data-ttu-id="0692c-224">使用針對該版本所顯示的最小值。</span><span class="sxs-lookup"><span data-stu-id="0692c-224">Use the smallest value shown for that version.</span></span>

## <a name="find-older-net-framework-versions-1-through-4"></a><span data-ttu-id="0692c-225">尋找較舊的 .NET Framework 版本（1到4）</span><span class="sxs-lookup"><span data-stu-id="0692c-225">Find older .NET Framework versions (1 through 4)</span></span>

<a name="net_a"></a>

### <a name="use-registry-editor-older-framework-versions"></a><span data-ttu-id="0692c-226">使用登錄編輯程式（較舊的 framework 版本）</span><span class="sxs-lookup"><span data-stu-id="0692c-226">Use Registry Editor (older framework versions)</span></span>

1. <span data-ttu-id="0692c-227">從 [開始] 功能表上，選擇 [執行]，輸入 *regedit*，然後選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="0692c-227">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

    <span data-ttu-id="0692c-228">您必須具有系統管理認證才能執行 regedit。</span><span class="sxs-lookup"><span data-stu-id="0692c-228">You must have administrative credentials to run regedit.</span></span>

2. <span data-ttu-id="0692c-229">在 [登錄編輯程式] 中，開啟下列子機碼： **HKEY_LOCAL_MACHINE \Software\microsoft\net Framework Setup\NDP**：</span><span class="sxs-lookup"><span data-stu-id="0692c-229">In the Registry Editor, open the following subkey: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP**:</span></span>

    - <span data-ttu-id="0692c-230">針對 .NET Framework 1.1 到 3.5 版，每個安裝的版本都會列為 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP** 子機碼下的子機碼。</span><span class="sxs-lookup"><span data-stu-id="0692c-230">For .NET Framework versions 1.1 through 3.5, each installed version is listed as a subkey under the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP** subkey.</span></span> <span data-ttu-id="0692c-231">例如，**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.5**。</span><span class="sxs-lookup"><span data-stu-id="0692c-231">For example, **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.5**.</span></span> <span data-ttu-id="0692c-232">版本號碼儲存為版本子機碼 **Version** 項目中的值。</span><span class="sxs-lookup"><span data-stu-id="0692c-232">The version number is stored as a value in the version subkey's **Version** entry.</span></span>

    - <span data-ttu-id="0692c-233">以 .NET Framework 4 為例，**Version** 項目位在 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client** 及/或 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full** 子機碼下。</span><span class="sxs-lookup"><span data-stu-id="0692c-233">For .NET Framework 4, the **Version** entry is under the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client** subkey, the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full** subkey, or under both subkeys.</span></span>

    > [!NOTE]
    > <span data-ttu-id="0692c-234">登錄中的 **NET Framework Setup** 資料夾不是以英文句號開頭。</span><span class="sxs-lookup"><span data-stu-id="0692c-234">The **NET Framework Setup** folder in the registry does not begin with a period.</span></span>

    <span data-ttu-id="0692c-235">下圖顯示 .NET Framework 3.5 的子機碼及其 **Version** 項目。</span><span class="sxs-lookup"><span data-stu-id="0692c-235">The following figure shows the subkey and its **Version** entry for the .NET Framework 3.5.</span></span>

    <span data-ttu-id="0692c-236">![.NET Framework 3.5 的登錄專案。](./media/net-4-and-earlier.png ".NET Framework 3.5 和更早版本")</span><span class="sxs-lookup"><span data-stu-id="0692c-236">![The registry entry for the .NET Framework 3.5.](./media/net-4-and-earlier.png ".NET Framework 3.5 and earlier versions")</span></span>

<a name="net_c"></a>

### <a name="query-the-registry-using-code-older-framework-versions"></a><span data-ttu-id="0692c-237">使用程式碼查詢登錄（較舊的 framework 版本）</span><span class="sxs-lookup"><span data-stu-id="0692c-237">Query the registry using code (older framework versions)</span></span>

<span data-ttu-id="0692c-238">使用 <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> 類別存取 Windows 登錄中的 **HKEY_LOCAL_MACHINE\Software\Microsoft\NET Framework Setup\NDP** 子機碼。</span><span class="sxs-lookup"><span data-stu-id="0692c-238">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the **HKEY_LOCAL_MACHINE\Software\Microsoft\NET Framework Setup\NDP** subkey in the Windows registry.</span></span>

<span data-ttu-id="0692c-239">下列範例會尋找已安裝的 .NET Framework 1 到4個版本：</span><span class="sxs-lookup"><span data-stu-id="0692c-239">The following example finds the .NET Framework 1 through 4 versions that are installed:</span></span>

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

## <a name="find-clr-versions"></a><span data-ttu-id="0692c-240">尋找 CLR 版本</span><span class="sxs-lookup"><span data-stu-id="0692c-240">Find CLR versions</span></span>

<a name="clr_a"></a>

### <a name="use-clrverexe"></a><span data-ttu-id="0692c-241">使用 Clrver</span><span class="sxs-lookup"><span data-stu-id="0692c-241">Use Clrver.exe</span></span>

<span data-ttu-id="0692c-242">使用 [CLR 版本工具 (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) 以判斷電腦上安裝了哪些 CLR 版本：</span><span class="sxs-lookup"><span data-stu-id="0692c-242">Use the [CLR Version tool (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) to determine which versions of the CLR are installed on a computer:</span></span>

- <span data-ttu-id="0692c-243">從 [Visual Studio 的開發人員命令提示字元](../tools/developer-command-prompt-for-vs.md)輸入 `clrver`。</span><span class="sxs-lookup"><span data-stu-id="0692c-243">From a [Developer Command Prompt for Visual Studio](../tools/developer-command-prompt-for-vs.md), enter `clrver`.</span></span>

    <span data-ttu-id="0692c-244">範例輸出：</span><span class="sxs-lookup"><span data-stu-id="0692c-244">Sample output:</span></span>

    ```console
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

<a name="clr_b"></a>

### <a name="use-the-environment-class"></a><span data-ttu-id="0692c-245">使用環境類別</span><span class="sxs-lookup"><span data-stu-id="0692c-245">Use the Environment class</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0692c-246">針對 .NET Framework 4.5 和更新版本，請不要使用 <xref:System.Environment.Version%2A?displayProperty=nameWithType> 屬性偵測 CLR 的版本。</span><span class="sxs-lookup"><span data-stu-id="0692c-246">For the .NET Framework 4.5 and later versions, don't use the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to detect the version of the CLR.</span></span> <span data-ttu-id="0692c-247">請依[使用程式碼尋找 .NET Framework 4.5 和更新版本](#net_d)中所述，改查詢登錄。</span><span class="sxs-lookup"><span data-stu-id="0692c-247">Instead, query the registry as described in [Find .NET Framework versions 4.5 and later with code](#net_d).</span></span>

1. <span data-ttu-id="0692c-248">查詢 <xref:System.Environment.Version?displayProperty=nameWithType> 屬性以擷取 <xref:System.Version> 物件。</span><span class="sxs-lookup"><span data-stu-id="0692c-248">Query the <xref:System.Environment.Version?displayProperty=nameWithType> property to retrieve a <xref:System.Version> object.</span></span>

    <span data-ttu-id="0692c-249">傳回的 `System.Version` 物件可識別目前執行程式碼的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="0692c-249">The returned `System.Version` object identifies the version of the runtime that's currently executing the code.</span></span> <span data-ttu-id="0692c-250">它不會傳回組件版本或已安裝在電腦上的其他執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="0692c-250">It doesn't return assembly versions or other versions of the runtime that may have been installed on the computer.</span></span>

    <span data-ttu-id="0692c-251">針對 .NET Framework 4、4.5、4.5.1 和 4.5.2 版，所傳回 <xref:System.Version> 物件的字串表示格式為 4.0.30319.*xxxxx*，其中 *xxxxx* 會小於 42000。</span><span class="sxs-lookup"><span data-stu-id="0692c-251">For the .NET Framework versions 4, 4.5, 4.5.1, and 4.5.2, the string representation of the returned <xref:System.Version> object has the form 4.0.30319.*xxxxx*, where *xxxxx* is less than 42000.</span></span> <span data-ttu-id="0692c-252">針對 .NET Framework 4.6 和更新版本，其格式為 4.0.30319.42000。</span><span class="sxs-lookup"><span data-stu-id="0692c-252">For the .NET Framework 4.6 and later versions, it has the form 4.0.30319.42000.</span></span>

2. <span data-ttu-id="0692c-253">取得 `Version` 物件之後，如下所示來加以查詢：</span><span class="sxs-lookup"><span data-stu-id="0692c-253">After you have the `Version` object, query it as follows:</span></span>

   - <span data-ttu-id="0692c-254">針對主要版本識別項 (例如 4.0 版的 *4*)，請使用 <xref:System.Version.Major%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="0692c-254">For the major release identifier (for example, *4* for version 4.0), use the <xref:System.Version.Major%2A?displayProperty=nameWithType> property.</span></span>

   - <span data-ttu-id="0692c-255">針對次要版本識別項 (例如 4.0 版的 *0*)，請使用 <xref:System.Version.Minor%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="0692c-255">For the minor release identifier (for example, *0* for version 4.0), use the <xref:System.Version.Minor%2A?displayProperty=nameWithType> property.</span></span>

   - <span data-ttu-id="0692c-256">針對整個版本字串 (例如 *4.0.30319.18010*)，請使用 <xref:System.Version.ToString%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="0692c-256">For the entire version string (for example, *4.0.30319.18010*), use the <xref:System.Version.ToString%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0692c-257">這個方法會傳回單一值，其反映執行程式碼的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="0692c-257">This method returns a single value that reflects the version of the runtime that's executing the code.</span></span> <span data-ttu-id="0692c-258">它不會傳回組件版本或可能已安裝在電腦上的其他執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="0692c-258">It doesn't return assembly versions or other runtime versions that may be installed on the computer.</span></span>

<span data-ttu-id="0692c-259">下列範例使用 <xref:System.Environment.Version%2A?displayProperty=nameWithType> 屬性來擷取 CLR 版本資訊：</span><span class="sxs-lookup"><span data-stu-id="0692c-259">The following example uses the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to retrieve CLR version information:</span></span>

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a><span data-ttu-id="0692c-260">請參閱</span><span class="sxs-lookup"><span data-stu-id="0692c-260">See also</span></span>

- [<span data-ttu-id="0692c-261">如何：判斷已安裝的 .NET Framework 更新</span><span class="sxs-lookup"><span data-stu-id="0692c-261">How to: Determine which .NET Framework updates are installed</span></span>](how-to-determine-which-net-framework-updates-are-installed.md)
- [<span data-ttu-id="0692c-262">安裝適用於開發人員的 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0692c-262">Install the .NET Framework for developers</span></span>](../install/guide-for-developers.md)
- [<span data-ttu-id="0692c-263">.NET Framework 版本和相依性</span><span class="sxs-lookup"><span data-stu-id="0692c-263">.NET Framework versions and dependencies</span></span>](versions-and-dependencies.md)
