---
title: 執行階段分析
ms.date: 03/30/2017
helpviewer_keywords:
- performance counters
- common language runtime, profiling
- Perfmon.exe
- System Monitor
- profiling
- runtime, profiling
- profiling applications
- Performance Console
ms.assetid: ccd68284-f3a8-47b8-bc3f-92e5fe3a1640
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7214fa0342d0946044861c4e375c7797ad6a06b1
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833766"
---
# <a name="runtime-profiling"></a><span data-ttu-id="ea2c9-102">執行階段分析</span><span class="sxs-lookup"><span data-stu-id="ea2c9-102">Runtime Profiling</span></span>
<span data-ttu-id="ea2c9-103">分析是在任何開發或部署案例中蒐集效能資料的一種方法。</span><span class="sxs-lookup"><span data-stu-id="ea2c9-103">Profiling is a method of gathering performance data in any development or deployment scenario.</span></span> <span data-ttu-id="ea2c9-104">本節適用對象為想要蒐集應用程式效能資訊的開發人員和系統管理員。</span><span class="sxs-lookup"><span data-stu-id="ea2c9-104">This section is for developers and system administrators who want to gather information about application performance.</span></span>  
  
## <a name="tracking-performance-using-the-performance-monitor-perfmonexe"></a><span data-ttu-id="ea2c9-105">使用效能監視器 (Perfmon.exe) 追蹤效能</span><span class="sxs-lookup"><span data-stu-id="ea2c9-105">Tracking Performance Using the Performance Monitor (Perfmon.exe)</span></span>  
 <span data-ttu-id="ea2c9-106">效能監視器是用來分析您的.NET Framework 應用程式的最簡單的工具。</span><span class="sxs-lookup"><span data-stu-id="ea2c9-106">The Performance Monitor is the easiest tool to use to profile your .NET Framework application.</span></span> <span data-ttu-id="ea2c9-107">效能監視器以圖形表示與通用語言執行平台和 Windows 軟體開發套件 (SDK) 一起安裝的.NET Framework 效能計數器中找到的資料。</span><span class="sxs-lookup"><span data-stu-id="ea2c9-107">The Performance Monitor graphically represents data found in the .NET Framework performance counters that are installed with the common language runtime and the Windows Software Development Kit (SDK).</span></span> <span data-ttu-id="ea2c9-108">這些計數器可用來監視從記憶體管理到 Just-In-Time (JIT) 編譯器效能的一切內容。</span><span class="sxs-lookup"><span data-stu-id="ea2c9-108">These counters can be used to monitor everything from memory management to just-in-time (JIT) compiler performance.</span></span> <span data-ttu-id="ea2c9-109">它會告訴您應用程式使用的資源，這是間接測量應用程式效能的方法。</span><span class="sxs-lookup"><span data-stu-id="ea2c9-109">They tell you about the resources your application uses, which is an indirect measure of your application's performance.</span></span> <span data-ttu-id="ea2c9-110">使用這些計數器可了解應用程式內部運作的方式。</span><span class="sxs-lookup"><span data-stu-id="ea2c9-110">Use these counters to understand how your application works internally.</span></span>  
  
#### <a name="to-run-perfmonexe-on-windows-vista-and-later-versions"></a><span data-ttu-id="ea2c9-111">在 Windows Vista 和更新版本上執行 Perfmon.exe</span><span class="sxs-lookup"><span data-stu-id="ea2c9-111">To run Perfmon.exe on Windows Vista and later versions</span></span>  
  
1. <span data-ttu-id="ea2c9-112">在命令提示字元處，輸入 **perfmon**。</span><span class="sxs-lookup"><span data-stu-id="ea2c9-112">At the command prompt, type **perfmon**.</span></span> <span data-ttu-id="ea2c9-113">[效能監視器]  主控台隨即出現。</span><span class="sxs-lookup"><span data-stu-id="ea2c9-113">The **Performance Monitor** console appears.</span></span>  
  
2. <span data-ttu-id="ea2c9-114">在 [監視工具]  資料夾中，按一下 [效能監視器]  。</span><span class="sxs-lookup"><span data-stu-id="ea2c9-114">In the **Monitoring Tools** folder, click **Performance Monitor**.</span></span>  
  
3. <span data-ttu-id="ea2c9-115">在 [效能監視器] 工具列中，按一下出現的 **加入** 圖示 (加號)。</span><span class="sxs-lookup"><span data-stu-id="ea2c9-115">In the Performance Monitor toolbar, click the **Add** icon (the plus sign), if it is present.</span></span> <span data-ttu-id="ea2c9-116">如果未出現，請以滑鼠右鍵按一下監視器視窗，然後選取 [加入計數器]  選項。</span><span class="sxs-lookup"><span data-stu-id="ea2c9-116">If it is not present, right-click in the monitor window and select the **Add Counters** option.</span></span>  
  
     <span data-ttu-id="ea2c9-117">這會開啟 [加入計數器]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="ea2c9-117">This opens the **Add Counters** dialog box.</span></span> <span data-ttu-id="ea2c9-118">[可用的計數器]  清單方塊顯示可用的效能物件。</span><span class="sxs-lookup"><span data-stu-id="ea2c9-118">The **Available counters** list box displays the available performance objects.</span></span> <span data-ttu-id="ea2c9-119">.NET Framework 應用程式有一些預先定義的物件，包括用於記憶體管理 ( **.NET CLR 記憶體**)、互通性 ( **.NET CLR Interop**)、例外狀況處理 ( **.NET CLR 例外狀況**) 和多執行緒 ( **.NET CLR LocksAndThreads**) 的物件。</span><span class="sxs-lookup"><span data-stu-id="ea2c9-119">There are a number of predefined objects for .NET Framework applications, including those for memory management (**.NET CLR Memory**), interoperability (**.NET CLR Interop**), exception handling (**.NET CLR Exceptions**), and multithreading (**.NET CLR LocksAndThreads**).</span></span> <span data-ttu-id="ea2c9-120">每個效能物件都包含一些個別的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="ea2c9-120">Each performance object includes a number of individual performance counters.</span></span> <span data-ttu-id="ea2c9-121">如需效能監視器中可用的效能計數器清單，請參閱 [Performance Counters](../../../docs/framework/debug-trace-profile/performance-counters.md)隨附之 .NET Framework 效能計數器中找到的資料。</span><span class="sxs-lookup"><span data-stu-id="ea2c9-121">For a list of the performance counters available in Performance Monitor, see [Performance Counters](../../../docs/framework/debug-trace-profile/performance-counters.md).</span></span>  
  
4. <span data-ttu-id="ea2c9-122">選取效能物件名稱旁的核取方塊，以檢視所支援的個別效能計數器清單。</span><span class="sxs-lookup"><span data-stu-id="ea2c9-122">Select the check box next to a performance object's name to view the list of individual performance counters that it supports.</span></span>  
  
5. <span data-ttu-id="ea2c9-123">按一下您要檢視的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="ea2c9-123">Click the performance counter you want to view.</span></span>  
  
6. <span data-ttu-id="ea2c9-124">在 [所選取物件的例項]  清單方塊中，按一下 [\<所有例項>]  ，指定您要全域 (也就是針對整個系統) 監視 Common Language Runtime 的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="ea2c9-124">In the **Instances of selected object** list box, click **\<All instances>** to specify that you want to monitor the performance counter for the common language runtime globally (that is, on a system-wide basis).</span></span>  
  
     <span data-ttu-id="ea2c9-125">-或-</span><span class="sxs-lookup"><span data-stu-id="ea2c9-125">-or-</span></span>  
  
     <span data-ttu-id="ea2c9-126">在 [所選取物件的例項]  清單方塊中，按一下要監視該應用程式之效能計數器的應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="ea2c9-126">In the **Instances of selected object** list box, click an application name to monitor the performance counter for that application.</span></span>  
  
     <span data-ttu-id="ea2c9-127">若要區別多個執行階段版本，或釐清多個同名的應用程式，您也必須修改登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="ea2c9-127">To differentiate multiple versions of the runtime, or to disambiguate multiple applications with the same name, you must also modify a registry key.</span></span> <span data-ttu-id="ea2c9-128">如需詳細資訊，請參閱 [效能計數器與同處理序並存應用程式](../../../docs/framework/debug-trace-profile/performance-counters-and-in-process-side-by-side-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="ea2c9-128">For more information, see [Performance Counters and In-Process Side-By-Side Applications](../../../docs/framework/debug-trace-profile/performance-counters-and-in-process-side-by-side-applications.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ea2c9-129">如果在執行 [效能] 主控台時安裝新的效能計數器，請停止並重新啟動 [效能] 主控台，以顯示新的計數器。</span><span class="sxs-lookup"><span data-stu-id="ea2c9-129">When new performance counters are installed while the Performance console is running, stop and restart the Performance console to make the new counters visible.</span></span>  
  
 <span data-ttu-id="ea2c9-130">如果您想要分析某個區域或遠端共用中的組件，請確定該遠端組件在執行效能計數器的電腦上受到完全信任。</span><span class="sxs-lookup"><span data-stu-id="ea2c9-130">If you want to profile an assembly that exists in a zone or on a remote share, make sure that the remote assembly has full trust on the computer that runs the performance counters.</span></span> <span data-ttu-id="ea2c9-131">如果沒有充分信任該組件，則效能計數器將無法運作。</span><span class="sxs-lookup"><span data-stu-id="ea2c9-131">If the assembly does not have sufficient trust, the performance counters will not work.</span></span> <span data-ttu-id="ea2c9-132">如需將信任授與不同區域的資訊，請參閱 [Caspol.exe (程式碼存取安全性原則工具)](../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="ea2c9-132">For information about granting trust to different zones, see [Caspol.exe (Code Access Security Policy Tool)](../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ea2c9-133">在系統上安裝.NET Framework 4，效能監視器可能不會顯示效能計數器資料某些類別，例如 **.NET CLR Data**並 **.NET CLR 網路**，如使用.NET Framework 1.1 所開發的應用程式。</span><span class="sxs-lookup"><span data-stu-id="ea2c9-133">On systems on which the .NET Framework 4 is installed, the Performance Monitor may not display data for performance counters in some categories, such as **.NET CLR Data** and **.NET CLR Networking**, for applications that were developed using the .NET Framework 1.1.</span></span> <span data-ttu-id="ea2c9-134">如果出現這種情況，只要將 [\<forcePerformanceCounterUniqueSharedMemoryReads>](../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md) 項目新增至應用程式組態檔，就可以設定效能監視器來顯示此資料。</span><span class="sxs-lookup"><span data-stu-id="ea2c9-134">If this is the case, you can configure Performance Monitor to display this data by adding the [\<forcePerformanceCounterUniqueSharedMemoryReads>](../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md) element to the application's configuration file.</span></span>  
  
## <a name="reading-and-creating-performance-counters-programmatically"></a><span data-ttu-id="ea2c9-135">以程式設計方式讀取及建立效能計數器</span><span class="sxs-lookup"><span data-stu-id="ea2c9-135">Reading and Creating Performance Counters Programmatically</span></span>  
 <span data-ttu-id="ea2c9-136">.NET Framework 會提供可用來以程式設計方式存取 [效能] 主控台中使用的相同效能資訊的類別。</span><span class="sxs-lookup"><span data-stu-id="ea2c9-136">The .NET Framework provides classes you can use to programmatically access the same performance information that is available in the Performance console.</span></span> <span data-ttu-id="ea2c9-137">您也可以使用這些類別，建立自訂效能計數器。</span><span class="sxs-lookup"><span data-stu-id="ea2c9-137">You can also use these classes to create custom performance counters.</span></span> <span data-ttu-id="ea2c9-138">下表說明一些效能監視提供.NET Framework 中的類別。</span><span class="sxs-lookup"><span data-stu-id="ea2c9-138">The following table describes some of the performance monitoring classes that are provided in the .NET Framework.</span></span>  
  
|<span data-ttu-id="ea2c9-139">類別</span><span class="sxs-lookup"><span data-stu-id="ea2c9-139">Class</span></span>|<span data-ttu-id="ea2c9-140">描述</span><span class="sxs-lookup"><span data-stu-id="ea2c9-140">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Diagnostics.PerformanceCounter?displayProperty=nameWithType>|<span data-ttu-id="ea2c9-141">代表 Windows NT 效能計數器元件。</span><span class="sxs-lookup"><span data-stu-id="ea2c9-141">Represents a Windows NT performance counter component.</span></span> <span data-ttu-id="ea2c9-142">使用這個類別可讀取現有的預先定義或自訂計數器，並將效能資料發佈 (寫入) 至自訂計數器。</span><span class="sxs-lookup"><span data-stu-id="ea2c9-142">Use this class to read existing predefined or custom counters and publish (write) performance data to custom counters.</span></span>|  
|<xref:System.Diagnostics.PerformanceCounterCategory?displayProperty=nameWithType>|<span data-ttu-id="ea2c9-143">提供與電腦上的計數器和計數器類別互動的幾種方法。</span><span class="sxs-lookup"><span data-stu-id="ea2c9-143">Provides several methods for interacting with counters and categories of counters on the computer.</span></span>|  
|<xref:System.Diagnostics.PerformanceCounterInstaller?displayProperty=nameWithType>|<span data-ttu-id="ea2c9-144">指定 `PerformanceCounter` 元件的安裝程式。</span><span class="sxs-lookup"><span data-stu-id="ea2c9-144">Specifies an installer for the `PerformanceCounter` component.</span></span>|  
|<xref:System.Diagnostics.PerformanceCounterType?displayProperty=nameWithType>|<span data-ttu-id="ea2c9-145">指定用以計算 `NextValue` 之 `PerformanceCounter`方法的公式。</span><span class="sxs-lookup"><span data-stu-id="ea2c9-145">Specifies the formula to calculate the `NextValue` method for a `PerformanceCounter`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ea2c9-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea2c9-146">See also</span></span>

- [<span data-ttu-id="ea2c9-147">效能計數器</span><span class="sxs-lookup"><span data-stu-id="ea2c9-147">Performance Counters</span></span>](../../../docs/framework/debug-trace-profile/performance-counters.md)
