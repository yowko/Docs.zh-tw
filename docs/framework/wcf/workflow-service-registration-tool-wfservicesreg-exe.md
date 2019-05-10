---
title: WorkFlow 服務登錄工具 (WFServicesReg.exe)
ms.date: 03/30/2017
ms.assetid: 9e92c87b-99c5-4e8d-9d53-7944cc2b47d3
ms.openlocfilehash: da377e865258169bdca16cfb0db3f8612d4e0f0d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64613043"
---
# <a name="workflow-service-registration-tool-wfservicesregexe"></a><span data-ttu-id="9d736-102">WorkFlow 服務登錄工具 (WFServicesReg.exe)</span><span class="sxs-lookup"><span data-stu-id="9d736-102">WorkFlow Service Registration Tool (WFServicesReg.exe)</span></span>
<span data-ttu-id="9d736-103">Workflow 服務登錄工具 (WFServicesReg.exe) 是一個獨立工具，可用於新增、移除或修復 Windows Workflow Foundation (WF) 服務的組態項目。</span><span class="sxs-lookup"><span data-stu-id="9d736-103">Workflow Services Registration tool (WFServicesReg.exe) is a stand-alone tool that can be used to add, remove, or repair the configuration elements for Windows Workflow Foundation (WF) services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d736-104">語法</span><span class="sxs-lookup"><span data-stu-id="9d736-104">Syntax</span></span>  
  
```  
WFServicesReg.exe [-c | -r | -v | -m | -i]  
```  
  
## <a name="remarks"></a><span data-ttu-id="9d736-105">備註</span><span class="sxs-lookup"><span data-stu-id="9d736-105">Remarks</span></span>  
 <span data-ttu-id="9d736-106">此工具可以在 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] 安裝位置中找到，也就是 %windir%\Microsoft.NET\Framework\v3.5 或 64 位元電腦中的 %windir%\Microsoft.NET\Framework64\v3.5。</span><span class="sxs-lookup"><span data-stu-id="9d736-106">The tool can be found at the [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] installation location, specifically, %windir%\Microsoft.NET\Framework\v3.5, or at %windir%\Microsoft.NET\Framework64\v3.5 in 64-bit machines.</span></span>  
  
 <span data-ttu-id="9d736-107">下表描述可與 Workflow 服務登錄工具 (WFServicesReg.exe) 搭配使用的選項。</span><span class="sxs-lookup"><span data-stu-id="9d736-107">The following tables describe the options that can be used with the Workflow Services Registration tool (WFServicesReg.exe).</span></span>  
  
|<span data-ttu-id="9d736-108">選項</span><span class="sxs-lookup"><span data-stu-id="9d736-108">Option</span></span>|<span data-ttu-id="9d736-109">描述</span><span class="sxs-lookup"><span data-stu-id="9d736-109">Description</span></span>|  
|------------|-----------------|  
|`/c`|<span data-ttu-id="9d736-110">設定 Windows 工作流程服務。</span><span class="sxs-lookup"><span data-stu-id="9d736-110">Configures Windows Workflow Services.</span></span> <span data-ttu-id="9d736-111">用於安裝和修復案例中。</span><span class="sxs-lookup"><span data-stu-id="9d736-111">Used in install and repair scenarios.</span></span>|  
|`/r`|<span data-ttu-id="9d736-112">移除 Windows 工作流程服務組態。</span><span class="sxs-lookup"><span data-stu-id="9d736-112">Removes Windows Workflow Services Configuration.</span></span>|  
|`/v`|<span data-ttu-id="9d736-113">列印詳細資訊 (適用於設定或移除)。</span><span class="sxs-lookup"><span data-stu-id="9d736-113">Print verbose information (for either configuration or removal).</span></span>|  
|`/m`|<span data-ttu-id="9d736-114">啟用 MSI 記錄格式。</span><span class="sxs-lookup"><span data-stu-id="9d736-114">Enables MSI logging format.</span></span>|  
|`/i`|<span data-ttu-id="9d736-115">應用程式執行時，最小化視窗。</span><span class="sxs-lookup"><span data-stu-id="9d736-115">Minimizes the window when the application runs.</span></span>|  
  
## <a name="registration"></a><span data-ttu-id="9d736-116">註冊</span><span class="sxs-lookup"><span data-stu-id="9d736-116">Registration</span></span>  
 <span data-ttu-id="9d736-117">工具會檢查 Web.config 檔案並註冊下列項目：</span><span class="sxs-lookup"><span data-stu-id="9d736-117">The tool inspects the Web.config file and registers the following:</span></span>  
  
- [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] <span data-ttu-id="9d736-118">參考組件。</span><span class="sxs-lookup"><span data-stu-id="9d736-118">reference assemblies.</span></span>  
  
- <span data-ttu-id="9d736-119">.xoml 檔案的組建提供者。</span><span class="sxs-lookup"><span data-stu-id="9d736-119">A build provider for .xoml files.</span></span>  
  
- <span data-ttu-id="9d736-120">.xoml 和 .rules 檔案的 HTTP 處理常式。</span><span class="sxs-lookup"><span data-stu-id="9d736-120">HTTP handlers for .xoml and .rules files.</span></span>  
  
 <span data-ttu-id="9d736-121">工具會檢查 Machine.config 檔案並註冊下列延伸項目：</span><span class="sxs-lookup"><span data-stu-id="9d736-121">The tool inspects the Machine.config file and registers the following extensions:</span></span>  
  
- <span data-ttu-id="9d736-122">behaviorExtensions</span><span class="sxs-lookup"><span data-stu-id="9d736-122">behaviorExtensions</span></span>  
  
- <span data-ttu-id="9d736-123">bindingElementExtensions</span><span class="sxs-lookup"><span data-stu-id="9d736-123">bindingElementExtensions</span></span>  
  
- <span data-ttu-id="9d736-124">bindingExtensions</span><span class="sxs-lookup"><span data-stu-id="9d736-124">bindingExtensions</span></span>  
  
 <span data-ttu-id="9d736-125">工具也會註冊下列用戶端中繼資料匯入工具：</span><span class="sxs-lookup"><span data-stu-id="9d736-125">The tool also registers the following client metadata importers:</span></span>  
  
- <span data-ttu-id="9d736-126">policyImporters</span><span class="sxs-lookup"><span data-stu-id="9d736-126">policyImporters</span></span>  
  
- <span data-ttu-id="9d736-127">wsdlImporters</span><span class="sxs-lookup"><span data-stu-id="9d736-127">wsdlImporters</span></span>  
  
 <span data-ttu-id="9d736-128">工具也會在 IIS Metabase 中註冊 .xoml 和 .rules Scriptmap 與處理常式。</span><span class="sxs-lookup"><span data-stu-id="9d736-128">The tool also registers .xoml and .rules scriptmaps and handlers in the IIS metabase.</span></span>  
  
 <span data-ttu-id="9d736-129">在 [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] 和 [!INCLUDE[wxp](../../../includes/wxp-md.md)] 電腦上 (IIS 5.1 和 [!INCLUDE[iis601](../../../includes/iis601-md.md)])，會註冊一組 .xoml 和 .rules Scriptmap。</span><span class="sxs-lookup"><span data-stu-id="9d736-129">On [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] and [!INCLUDE[wxp](../../../includes/wxp-md.md)] machines (IIS 5.1 and [!INCLUDE[iis601](../../../includes/iis601-md.md)]), one set of .xoml and .rules scriptmaps are registered.</span></span>  
  
 <span data-ttu-id="9d736-130">在 64 位元電腦上，如果已啟用 `Enable32BitAppOnWin64` 參數，此工具就會註冊 WOW 模式 Scriptmap，如果已停用 `Enable32BitAppOnWin64` 參數，則會註冊原生 64 位元 Scriptmap。</span><span class="sxs-lookup"><span data-stu-id="9d736-130">On 64-bit machines, the tool registers WOW mode scriptmaps if the `Enable32BitAppOnWin64` switch is enabled, or native 64-bit scriptmaps if the `Enable32BitAppOnWin64` switch is disabled.</span></span>  
  
 <span data-ttu-id="9d736-131">在 [!INCLUDE[wv](../../../includes/wv-md.md)]和 Windows Server 2008 (IIS 7.0 和更新版本) 電腦，兩組.xoml 和.rules 處理常式的註冊： 一個用於整合模式下，一個用於傳統模式。</span><span class="sxs-lookup"><span data-stu-id="9d736-131">On [!INCLUDE[wv](../../../includes/wv-md.md)] and Windows Server 2008 (IIS 7.0 and above) machines, two sets of .xoml and .rules handlers are registered: one for Integrated mode and one for Classic mode.</span></span>  
  
 <span data-ttu-id="9d736-132">在 64 位元電腦上，會註冊三組處理常式 (無論 `Enable32BitAppOnWin64` 參數的狀態為何)：一組用於整合模式，一組用於 WOW 傳統模式，一組用於原生 64 位元傳統模式。</span><span class="sxs-lookup"><span data-stu-id="9d736-132">On 64-bit machines, three sets of handlers are registered (regardless of the state of the `Enable32BitAppOnWin64` switch): one for Integrated mode, one for WOW Classic mode and one for native 64-bit Classic mode.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9d736-133">與 ServiceModelreg.exe 不同的是，WFServicesReg.exe 不允許新增、移除或修復用於特定網站的 Scriptmap 或處理常式。</span><span class="sxs-lookup"><span data-stu-id="9d736-133">Unlike ServiceModelreg.exe, WFServicesReg.exe does not allow adding, removing, or repairing scriptmaps or handlers for a particular Web site.</span></span> <span data-ttu-id="9d736-134">如需這個問題的解決方法，請參閱「修復 Scriptmap」一節。</span><span class="sxs-lookup"><span data-stu-id="9d736-134">For a workaround to this issue, see the "Repairing the Scriptmaps" section.</span></span>  
  
## <a name="usage-scenarios"></a><span data-ttu-id="9d736-135">使用案例</span><span class="sxs-lookup"><span data-stu-id="9d736-135">Usage Scenarios</span></span>  
  
### <a name="installing-iis-after-net-framework-35-is-installed"></a><span data-ttu-id="9d736-136">在安裝 .NET Framework 3.5 之後安裝 IIS</span><span class="sxs-lookup"><span data-stu-id="9d736-136">Installing IIS after .NET Framework 3.5 is installed</span></span>  
 <span data-ttu-id="9d736-137">在 [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] 電腦上安裝 IIS 之前，先安裝 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9d736-137">On a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] is installed prior to IIS installation.</span></span> <span data-ttu-id="9d736-138">由於無法使用 IIS Metabase，因此能夠在未安裝 .xoml 和 .rules Scriptmap 的情況下成功安裝 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9d736-138">Due to the unavailability of the IIS metabase, installation of [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] succeeds without installing .xoml and .rules scriptmaps.</span></span>  
  
 <span data-ttu-id="9d736-139">安裝 IIS 之後，您可以使用 WFServicesReg.exe 工具搭配 `/c` 參數來安裝這些特定 Scriptmap。</span><span class="sxs-lookup"><span data-stu-id="9d736-139">After IIS is installed, you can use the WFServicesReg.exe tool with the `/c` switch to install these specific scriptmaps.</span></span>  
  
### <a name="repairing-the-scriptmaps"></a><span data-ttu-id="9d736-140">修復 Scriptmap</span><span class="sxs-lookup"><span data-stu-id="9d736-140">Repairing the Scriptmaps</span></span>  
  
#### <a name="scriptmap-deleted-under-web-sites-node"></a><span data-ttu-id="9d736-141">在網站節點下刪除的 Scriptmap</span><span class="sxs-lookup"><span data-stu-id="9d736-141">Scriptmap deleted under Web Sites node</span></span>  
 <span data-ttu-id="9d736-142">在 [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] 電腦上，從 [網站] 節點意外刪除了 .xoml 或 .rules。</span><span class="sxs-lookup"><span data-stu-id="9d736-142">On a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, .xoml or .rules is accidentally deleted from the Web Sites node.</span></span> <span data-ttu-id="9d736-143">您可以使用 `/c` 參數執行 WFServicesReg.exe 工具修復這種情況。</span><span class="sxs-lookup"><span data-stu-id="9d736-143">This can be repaired by running the WFServicesReg.exe tool with the `/c` switch.</span></span>  
  
#### <a name="scriptmap-deleted-under-a-particular-web-site"></a><span data-ttu-id="9d736-144">在特定網站下刪除的 Scriptmap</span><span class="sxs-lookup"><span data-stu-id="9d736-144">Scriptmap deleted under a particular Web site</span></span>  
 <span data-ttu-id="9d736-145">在 [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] 電腦上，從特定網站 (例如 [預設的網站]，而不是從 [網站] 節點) 意外刪除了 .xoml 或 .rules。</span><span class="sxs-lookup"><span data-stu-id="9d736-145">On a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, .xoml or .rules is accidentally deleted from a particular Web site (for example, the Default Web Site) rather than from the Web Sites node.</span></span>  
  
 <span data-ttu-id="9d736-146">若要修復特定網站的已刪除處理常式，您應該執行"WFServicesReg.exe r"以移除所有網站中的處理常式，然後執行"WFServicesReg.exe c"的所有網站中建立適當的處理常式。</span><span class="sxs-lookup"><span data-stu-id="9d736-146">To repair deleted handlers for a particular Web site, you should run "WFServicesReg.exe /r" to remove handlers from all Web sites, then run "WFServicesReg.exe /c" to create the appropriate handlers for all Web sites.</span></span>  
  
### <a name="configuring-handlers-after-switching-iis-mode"></a><span data-ttu-id="9d736-147">在切換 IIS 模式之後設定處理常式</span><span class="sxs-lookup"><span data-stu-id="9d736-147">Configuring handlers after switching IIS mode</span></span>  
 <span data-ttu-id="9d736-148">當 IIS 處於共用組態模式，並且已安裝 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] 時，便會在共用位置下設定 IIS Metabase。</span><span class="sxs-lookup"><span data-stu-id="9d736-148">When IIS is in shared configuration mode and [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] is installed, the IIS metabase is configured under a shared location.</span></span> <span data-ttu-id="9d736-149">如果將 IIS 切換為非共用組態模式，本機 Metabase 將不會包含所需的處理常式。</span><span class="sxs-lookup"><span data-stu-id="9d736-149">If you switch IIS to non-shared configuration mode, the local metabase will not contain the required handlers.</span></span> <span data-ttu-id="9d736-150">若要正確地設定本機 metabase，您可以匯入共用的 metabase 至本機，或執行"WFServicesReg.exe /c"，也就是設定本機 metabase。</span><span class="sxs-lookup"><span data-stu-id="9d736-150">To configure the local metabase properly, you can either import the shared metabase to local, or run "WFServicesReg.exe /c", which configures the local metabase.</span></span>
