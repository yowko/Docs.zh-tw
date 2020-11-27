---
title: 執行階段分析
description: 探索 .NET 中的執行時間分析，這是在任何開發或部署案例中收集效能資料的方法。
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
ms.openlocfilehash: 5d1542c7f6afa2d683240d6d5cca837b961eb3be
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267100"
---
# <a name="runtime-profiling"></a><span data-ttu-id="e7412-103">執行階段分析</span><span class="sxs-lookup"><span data-stu-id="e7412-103">Runtime Profiling</span></span>

<span data-ttu-id="e7412-104">分析是在任何開發或部署案例中蒐集效能資料的一種方法。</span><span class="sxs-lookup"><span data-stu-id="e7412-104">Profiling is a method of gathering performance data in any development or deployment scenario.</span></span> <span data-ttu-id="e7412-105">本節適用對象為想要蒐集應用程式效能資訊的開發人員和系統管理員。</span><span class="sxs-lookup"><span data-stu-id="e7412-105">This section is for developers and system administrators who want to gather information about application performance.</span></span>  
  
## <a name="tracking-performance-using-the-performance-monitor-perfmonexe"></a><span data-ttu-id="e7412-106">使用效能監視器 (Perfmon.exe) 追蹤效能</span><span class="sxs-lookup"><span data-stu-id="e7412-106">Tracking Performance Using the Performance Monitor (Perfmon.exe)</span></span>  

 <span data-ttu-id="e7412-107">效能監視器是最簡單的工具，可用來分析您的 .NET Framework 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e7412-107">The Performance Monitor is the easiest tool to use to profile your .NET Framework application.</span></span> <span data-ttu-id="e7412-108">效能監視器會以圖形方式呈現與 common language runtime 和 Windows SDK 一起安裝的 .NET Framework 效能計數器中的資料。</span><span class="sxs-lookup"><span data-stu-id="e7412-108">The Performance Monitor graphically represents data found in the .NET Framework performance counters that are installed with the common language runtime and the Windows SDK.</span></span> <span data-ttu-id="e7412-109">這些計數器可用來監視從記憶體管理到 Just-In-Time (JIT) 編譯器效能的一切內容。</span><span class="sxs-lookup"><span data-stu-id="e7412-109">These counters can be used to monitor everything from memory management to just-in-time (JIT) compiler performance.</span></span> <span data-ttu-id="e7412-110">它會告訴您應用程式使用的資源，這是間接測量應用程式效能的方法。</span><span class="sxs-lookup"><span data-stu-id="e7412-110">They tell you about the resources your application uses, which is an indirect measure of your application's performance.</span></span> <span data-ttu-id="e7412-111">使用這些計數器可了解應用程式內部運作的方式。</span><span class="sxs-lookup"><span data-stu-id="e7412-111">Use these counters to understand how your application works internally.</span></span>  
  
#### <a name="to-run-perfmonexe-on-windows-vista-and-later-versions"></a><span data-ttu-id="e7412-112">在 Windows Vista 和更新版本上執行 Perfmon.exe</span><span class="sxs-lookup"><span data-stu-id="e7412-112">To run Perfmon.exe on Windows Vista and later versions</span></span>  
  
1. <span data-ttu-id="e7412-113">在命令提示字元處，輸入 **perfmon**。</span><span class="sxs-lookup"><span data-stu-id="e7412-113">At the command prompt, type **perfmon**.</span></span> <span data-ttu-id="e7412-114">[效能監視器]  主控台隨即出現。</span><span class="sxs-lookup"><span data-stu-id="e7412-114">The **Performance Monitor** console appears.</span></span>  
  
2. <span data-ttu-id="e7412-115">在 [監視工具]  資料夾中，按一下 [效能監視器] 。</span><span class="sxs-lookup"><span data-stu-id="e7412-115">In the **Monitoring Tools** folder, click **Performance Monitor**.</span></span>  
  
3. <span data-ttu-id="e7412-116">在 [效能監視器] 工具列中，按一下出現的 **加入** 圖示 (加號)。</span><span class="sxs-lookup"><span data-stu-id="e7412-116">In the Performance Monitor toolbar, click the **Add** icon (the plus sign), if it is present.</span></span> <span data-ttu-id="e7412-117">如果未出現，請以滑鼠右鍵按一下監視器視窗，然後選取 [加入計數器]  選項。</span><span class="sxs-lookup"><span data-stu-id="e7412-117">If it is not present, right-click in the monitor window and select the **Add Counters** option.</span></span>  
  
     <span data-ttu-id="e7412-118">這會開啟 [加入計數器]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e7412-118">This opens the **Add Counters** dialog box.</span></span> <span data-ttu-id="e7412-119">[可用的計數器]  清單方塊顯示可用的效能物件。</span><span class="sxs-lookup"><span data-stu-id="e7412-119">The **Available counters** list box displays the available performance objects.</span></span> <span data-ttu-id="e7412-120">.NET Framework 應用程式有一些預先定義的物件，包括用於記憶體管理 (**.NET CLR 記憶體**)、互通性 (**.NET CLR Interop**)、例外狀況處理 (**.NET CLR 例外狀況**) 和多執行緒 (**.NET CLR LocksAndThreads**) 的物件。</span><span class="sxs-lookup"><span data-stu-id="e7412-120">There are a number of predefined objects for .NET Framework applications, including those for memory management (**.NET CLR Memory**), interoperability (**.NET CLR Interop**), exception handling (**.NET CLR Exceptions**), and multithreading (**.NET CLR LocksAndThreads**).</span></span> <span data-ttu-id="e7412-121">每個效能物件都包含一些個別的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="e7412-121">Each performance object includes a number of individual performance counters.</span></span> <span data-ttu-id="e7412-122">如需效能監視器中可用的效能計數器清單，請參閱 [Performance Counters](performance-counters.md)隨附之 .NET Framework 效能計數器中找到的資料。</span><span class="sxs-lookup"><span data-stu-id="e7412-122">For a list of the performance counters available in Performance Monitor, see [Performance Counters](performance-counters.md).</span></span>  
  
4. <span data-ttu-id="e7412-123">選取效能物件名稱旁的核取方塊，以檢視所支援的個別效能計數器清單。</span><span class="sxs-lookup"><span data-stu-id="e7412-123">Select the check box next to a performance object's name to view the list of individual performance counters that it supports.</span></span>  
  
5. <span data-ttu-id="e7412-124">按一下您要檢視的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="e7412-124">Click the performance counter you want to view.</span></span>  
  
6. <span data-ttu-id="e7412-125">在 [ **選取的物件** ] 清單方塊中，按一下 **\<All instances>** 以指定您要監視通用語言執行平臺的效能計數器全域 (也就是以全系統為基礎的) 。</span><span class="sxs-lookup"><span data-stu-id="e7412-125">In the **Instances of selected object** list box, click **\<All instances>** to specify that you want to monitor the performance counter for the common language runtime globally (that is, on a system-wide basis).</span></span>  
  
     <span data-ttu-id="e7412-126">-或-</span><span class="sxs-lookup"><span data-stu-id="e7412-126">-or-</span></span>  
  
     <span data-ttu-id="e7412-127">在 [所選取物件的例項]  清單方塊中，按一下要監視該應用程式之效能計數器的應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="e7412-127">In the **Instances of selected object** list box, click an application name to monitor the performance counter for that application.</span></span>  
  
     <span data-ttu-id="e7412-128">若要區別多個執行階段版本，或釐清多個同名的應用程式，您也必須修改登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="e7412-128">To differentiate multiple versions of the runtime, or to disambiguate multiple applications with the same name, you must also modify a registry key.</span></span> <span data-ttu-id="e7412-129">如需詳細資訊，請參閱 [Performance Counters and In-Process Side-By-Side Applications](performance-counters-and-in-process-side-by-side-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="e7412-129">For more information, see [Performance Counters and In-Process Side-By-Side Applications](performance-counters-and-in-process-side-by-side-applications.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e7412-130">如果在執行 [效能] 主控台時安裝新的效能計數器，請停止並重新啟動 [效能] 主控台，以顯示新的計數器。</span><span class="sxs-lookup"><span data-stu-id="e7412-130">When new performance counters are installed while the Performance console is running, stop and restart the Performance console to make the new counters visible.</span></span>  
  
 <span data-ttu-id="e7412-131">如果您想要分析某個區域或遠端共用中的組件，請確定該遠端組件在執行效能計數器的電腦上受到完全信任。</span><span class="sxs-lookup"><span data-stu-id="e7412-131">If you want to profile an assembly that exists in a zone or on a remote share, make sure that the remote assembly has full trust on the computer that runs the performance counters.</span></span> <span data-ttu-id="e7412-132">如果沒有充分信任該組件，則效能計數器將無法運作。</span><span class="sxs-lookup"><span data-stu-id="e7412-132">If the assembly does not have sufficient trust, the performance counters will not work.</span></span> <span data-ttu-id="e7412-133">如需將信任授與不同區域的資訊，請參閱 [Caspol.exe (程式碼存取安全性原則工具)](../tools/caspol-exe-code-access-security-policy-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="e7412-133">For information about granting trust to different zones, see [Caspol.exe (Code Access Security Policy Tool)](../tools/caspol-exe-code-access-security-policy-tool.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e7412-134">在安裝 .NET Framework 4 的系統上，效能監視器可能不會針對使用 .NET Framework 1.1 開發的應用程式，顯示某些類別中的效能計數器資料，例如 **.NET Clr 資料** 和 **.net clr 網路**。</span><span class="sxs-lookup"><span data-stu-id="e7412-134">On systems on which the .NET Framework 4 is installed, the Performance Monitor may not display data for performance counters in some categories, such as **.NET CLR Data** and **.NET CLR Networking**, for applications that were developed using the .NET Framework 1.1.</span></span> <span data-ttu-id="e7412-135">如果是這種情況，您可以將專案加入 [\<forcePerformanceCounterUniqueSharedMemoryReads>](../configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md) 至應用程式的設定檔，以設定效能監視器來顯示此資料。</span><span class="sxs-lookup"><span data-stu-id="e7412-135">If this is the case, you can configure Performance Monitor to display this data by adding the [\<forcePerformanceCounterUniqueSharedMemoryReads>](../configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md) element to the application's configuration file.</span></span>  
  
## <a name="reading-and-creating-performance-counters-programmatically"></a><span data-ttu-id="e7412-136">以程式設計方式讀取及建立效能計數器</span><span class="sxs-lookup"><span data-stu-id="e7412-136">Reading and Creating Performance Counters Programmatically</span></span>  

 <span data-ttu-id="e7412-137">.NET Framework 提供可讓您用來以程式設計方式存取效能主控台中可用之相同效能資訊的類別。</span><span class="sxs-lookup"><span data-stu-id="e7412-137">The .NET Framework provides classes you can use to programmatically access the same performance information that is available in the Performance console.</span></span> <span data-ttu-id="e7412-138">您也可以使用這些類別，建立自訂效能計數器。</span><span class="sxs-lookup"><span data-stu-id="e7412-138">You can also use these classes to create custom performance counters.</span></span> <span data-ttu-id="e7412-139">下表說明 .NET Framework 中提供的一些效能監視類別。</span><span class="sxs-lookup"><span data-stu-id="e7412-139">The following table describes some of the performance monitoring classes that are provided in the .NET Framework.</span></span>  
  
|<span data-ttu-id="e7412-140">類別</span><span class="sxs-lookup"><span data-stu-id="e7412-140">Class</span></span>|<span data-ttu-id="e7412-141">描述</span><span class="sxs-lookup"><span data-stu-id="e7412-141">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Diagnostics.PerformanceCounter?displayProperty=nameWithType>|<span data-ttu-id="e7412-142">代表 Windows NT 效能計數器元件。</span><span class="sxs-lookup"><span data-stu-id="e7412-142">Represents a Windows NT performance counter component.</span></span> <span data-ttu-id="e7412-143">使用這個類別可讀取現有的預先定義或自訂計數器，並將效能資料發佈 (寫入) 至自訂計數器。</span><span class="sxs-lookup"><span data-stu-id="e7412-143">Use this class to read existing predefined or custom counters and publish (write) performance data to custom counters.</span></span>|  
|<xref:System.Diagnostics.PerformanceCounterCategory?displayProperty=nameWithType>|<span data-ttu-id="e7412-144">提供與電腦上的計數器和計數器類別互動的幾種方法。</span><span class="sxs-lookup"><span data-stu-id="e7412-144">Provides several methods for interacting with counters and categories of counters on the computer.</span></span>|  
|<xref:System.Diagnostics.PerformanceCounterInstaller?displayProperty=nameWithType>|<span data-ttu-id="e7412-145">指定 `PerformanceCounter` 元件的安裝程式。</span><span class="sxs-lookup"><span data-stu-id="e7412-145">Specifies an installer for the `PerformanceCounter` component.</span></span>|  
|<xref:System.Diagnostics.PerformanceCounterType?displayProperty=nameWithType>|<span data-ttu-id="e7412-146">指定用以計算 `NextValue` 之 `PerformanceCounter`方法的公式。</span><span class="sxs-lookup"><span data-stu-id="e7412-146">Specifies the formula to calculate the `NextValue` method for a `PerformanceCounter`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e7412-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7412-147">See also</span></span>

- [<span data-ttu-id="e7412-148">效能計數器</span><span class="sxs-lookup"><span data-stu-id="e7412-148">Performance Counters</span></span>](performance-counters.md)
