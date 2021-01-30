---
title: 效能計數器與同處理序並存應用程式
description: 查看 .NET 中的效能計數器和同進程並存應用程式。 使用 Perfmon.exe，以每個執行時間為基礎來區分效能計數器。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- performance counters
- performance counters,and in-process side-by-side applications
- performance,.NET Framework applications
- performance monitoring,counters
ms.assetid: 6888f9be-c65b-4b03-a07b-df7ebdee2436
ms.openlocfilehash: 5cc3951c65a0be37294324c767a00bc7a35634b8
ms.sourcegitcommit: 78eb25647b0c750cd80354ebd6ce83a60668e22c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2021
ms.locfileid: "99065034"
---
# <a name="performance-counters-and-in-process-side-by-side-applications"></a><span data-ttu-id="957f7-104">效能計數器與同處理序並存應用程式</span><span class="sxs-lookup"><span data-stu-id="957f7-104">Performance Counters and In-Process Side-By-Side Applications</span></span>

<span data-ttu-id="957f7-105">使用效能監視器 (Perfmon.exe)，可以區分個別執行階段的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="957f7-105">Using the Performance Monitor (Perfmon.exe), it is possible to differentiate the performance counters on a per-runtime basis.</span></span> <span data-ttu-id="957f7-106">本主題描述啟用這項功能所需的登錄變更。</span><span class="sxs-lookup"><span data-stu-id="957f7-106">This topic describes the registry change needed to enable this functionality.</span></span>  
  
## <a name="the-default-behavior"></a><span data-ttu-id="957f7-107">預設行為</span><span class="sxs-lookup"><span data-stu-id="957f7-107">The Default Behavior</span></span>  

 <span data-ttu-id="957f7-108">根據預設，效能監視器會顯示個別應用程式的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="957f7-108">By default, the Performance Monitor displays performance counters on a per-application basis.</span></span> <span data-ttu-id="957f7-109">不過，這在兩種案例下會發生問題：</span><span class="sxs-lookup"><span data-stu-id="957f7-109">However, there are two scenarios in which this is problematic:</span></span>  
  
- <span data-ttu-id="957f7-110">當您監視兩個同名的應用程式時。</span><span class="sxs-lookup"><span data-stu-id="957f7-110">When you monitor two applications that have the same name.</span></span> <span data-ttu-id="957f7-111">例如，如果兩個應用程式的名稱都是 myapp.exe，則在 [執行個體] 資料行中，一個會顯示為 **myapp**，另一個則會顯示為 **myapp#1**。</span><span class="sxs-lookup"><span data-stu-id="957f7-111">For example, if both applications are named myapp.exe, one will be displayed as **myapp** and the other as **myapp#1** in the **Instance** column.</span></span> <span data-ttu-id="957f7-112">在此情況下，很難符合特定應用程式的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="957f7-112">In this case, it is difficult to match a performance counter to a particular application.</span></span> <span data-ttu-id="957f7-113">不確定針對 **myapp#1** 所收集的資料指的是第一個 myapp.exe 還是第二個 myapp.exe。</span><span class="sxs-lookup"><span data-stu-id="957f7-113">It is not clear whether the data collected for **myapp#1** refers to the first myapp.exe or the second myapp.exe.</span></span>  
  
- <span data-ttu-id="957f7-114">應用程式使用多個 Common Language Runtime 執行個體時。</span><span class="sxs-lookup"><span data-stu-id="957f7-114">When an application uses multiple instances of the common language runtime.</span></span> <span data-ttu-id="957f7-115">.NET Framework 4 支援同進程並存裝載案例;也就是說，單一進程或應用程式可以載入多個 common language runtime 實例。</span><span class="sxs-lookup"><span data-stu-id="957f7-115">The .NET Framework 4 supports in-process side-by-side hosting scenarios; that is, a single process or application can load multiple instances of the common language runtime.</span></span> <span data-ttu-id="957f7-116">如果名為 myapp.exe 的單一應用程式載入兩個執行階段執行個體，則會根據預設在 [執行個體] 資料行中將它們指定為 **myapp** 和 **myapp#1**。</span><span class="sxs-lookup"><span data-stu-id="957f7-116">If a single application named myapp.exe loads two runtime instances, by default, they will be designated in the **Instance** column as **myapp** and **myapp#1**.</span></span> <span data-ttu-id="957f7-117">在此情況下，不確定 **myapp** 和 **myapp#1** 指的是兩個同名的應用程式，還是含有兩個執行階段的相同應用程式。</span><span class="sxs-lookup"><span data-stu-id="957f7-117">In this case, it is not clear whether **myapp** and **myapp#1** refer to two applications with the same name, or to the same application with two runtimes.</span></span> <span data-ttu-id="957f7-118">如果多個同名的應用程式載入多個執行階段，則模稜兩可甚至會更高。</span><span class="sxs-lookup"><span data-stu-id="957f7-118">If multiple applications with the same name load multiple runtimes, the ambiguity is even greater.</span></span>  
  
 <span data-ttu-id="957f7-119">您可以設定登錄機碼，以消除這項模稜兩可。</span><span class="sxs-lookup"><span data-stu-id="957f7-119">You can set a registry key to eliminate this ambiguity.</span></span> <span data-ttu-id="957f7-120">針對使用 .NET Framework 4 開發的應用程式，此登錄變更會在 **實例** 資料行中，將一個進程識別碼加上執行時間實例識別碼加上應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="957f7-120">For applications developed using the .NET Framework 4, this registry change adds a process identifier followed by a runtime instance identifier to the application name in the **Instance** column.</span></span> <span data-ttu-id="957f7-121">應用程式現在會  `p`  \_ `r` 在 **實例** 資料行中識別為應用程式 _ processID runtimeID，而不是應用程式或應用程式 #1。</span><span class="sxs-lookup"><span data-stu-id="957f7-121">Instead of *application* or *application*#1, the application is now identified as *application* _`p`*processID*\_`r`*runtimeID* in the **Instance** column.</span></span> <span data-ttu-id="957f7-122">如果應用程式是使用舊版 common language runtime 開發的，則該實例會表示為 *應用程式 \_* `p` *processID* ，前提是已安裝 .NET Framework 4。</span><span class="sxs-lookup"><span data-stu-id="957f7-122">If an application was developed using a previous version of the common language runtime, that instance is represented as *application\_*`p`*processID* provided that the .NET Framework 4 is installed.</span></span>  
  
## <a name="performance-counters-for-in-process-side-by-side-applications"></a><span data-ttu-id="957f7-123">同處理序並存應用程式的效能計數器</span><span class="sxs-lookup"><span data-stu-id="957f7-123">Performance Counters for In-Process Side-by-Side Applications</span></span>  

 <span data-ttu-id="957f7-124">若要處理單一應用程式中裝載之多個 Common Language Runtime 版本的效能計數器，您必須變更單一登錄機碼設定，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="957f7-124">To handle performance counters for multiple common language runtime versions that are hosted in a single application, you must change a single registry key setting, as shown in the following table.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="957f7-125">索引鍵名稱</span><span class="sxs-lookup"><span data-stu-id="957f7-125">Key name</span></span>|<span data-ttu-id="957f7-126">HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\.NETFramework\Performance</span><span class="sxs-lookup"><span data-stu-id="957f7-126">HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\.NETFramework\Performance</span></span>|  
|<span data-ttu-id="957f7-127">值名稱</span><span class="sxs-lookup"><span data-stu-id="957f7-127">Value name</span></span>|<span data-ttu-id="957f7-128">ProcessNameFormat</span><span class="sxs-lookup"><span data-stu-id="957f7-128">ProcessNameFormat</span></span>|  
|<span data-ttu-id="957f7-129">值類型</span><span class="sxs-lookup"><span data-stu-id="957f7-129">Value type</span></span>|<span data-ttu-id="957f7-130">REG_DWORD</span><span class="sxs-lookup"><span data-stu-id="957f7-130">REG_DWORD</span></span>|  
|<span data-ttu-id="957f7-131">值</span><span class="sxs-lookup"><span data-stu-id="957f7-131">Value</span></span>|<span data-ttu-id="957f7-132">2 (0x00000002) </span><span class="sxs-lookup"><span data-stu-id="957f7-132">2 (0x00000002)</span></span>|
  
 <span data-ttu-id="957f7-133">`ProcessNameFormat` 值 0 指出已啟用預設行為；也就是說，Perfmon.exe 會顯示個別應用程式的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="957f7-133">A value of 0 for `ProcessNameFormat` indicates that the default behavior is enabled; that is, Perfmon.exe displays performance counters on a per-application basis.</span></span> <span data-ttu-id="957f7-134">當您將此值設定為2時，Perfmon.exe 會厘清應用程式的多個版本，並以每個執行時間為基礎提供效能計數器。</span><span class="sxs-lookup"><span data-stu-id="957f7-134">When you set this value to 2, Perfmon.exe disambiguates multiple versions of an application and provides performance counters on a per-runtime basis.</span></span> <span data-ttu-id="957f7-135">`ProcessNameFormat` 登錄機碼設定的任何其他值都不受支援，並保留供未來使用。</span><span class="sxs-lookup"><span data-stu-id="957f7-135">Any other value for the `ProcessNameFormat` registry key setting is unsupported and reserved for future use.</span></span>
  
 <span data-ttu-id="957f7-136">在您更新 `ProcessNameFormat` 登錄機碼設定之後，必須重新啟動 Perfmon.exe 或效能計數器的任何其他消費者，讓新執行個體命名功能正確地運作。</span><span class="sxs-lookup"><span data-stu-id="957f7-136">After you update the `ProcessNameFormat` registry key setting, you must restart Perfmon.exe or any other consumers of performance counters so that the new instance naming feature works correctly.</span></span>  
  
 <span data-ttu-id="957f7-137">下列範例示範如何以程式設計方式變更 `ProcessNameFormat` 值。</span><span class="sxs-lookup"><span data-stu-id="957f7-137">The following example shows how to change the `ProcessNameFormat` value programmatically.</span></span>  
  
 [!code-csharp[Conceptual.PerfCounters.InProSxS#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.perfcounters.inprosxs/cs/regsetting1.cs#1)]
 [!code-vb[Conceptual.PerfCounters.InProSxS#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.perfcounters.inprosxs/vb/regsetting1.vb#1)]  
  
 <span data-ttu-id="957f7-138">當您進行這項登錄變更時，如果已安裝 .NET Framework 4 或更新版本，Perfmon.exe 會將應用程式的名稱顯示為 *應用* 程式 _ `p` *processID*，其中 *應用* 程式是應用程式的名稱，而 *processID* 是應用程式的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="957f7-138">When you make this registry change, and if .NET Framework 4 or later is installed, Perfmon.exe displays the names of applications as *application* _`p`*processID*, where *application* is the name of the application, and *processID* is the application's process identifier.</span></span> <span data-ttu-id="957f7-139">例如，如果名為 myapp.exe 的應用程式載入 common language runtime 的兩個實例，Perfmon.exe 可能會將一個實例識別為 myapp_1416，而第二個則為 myapp_3160。</span><span class="sxs-lookup"><span data-stu-id="957f7-139">For example, if an application named myapp.exe loads two instances of the common language runtime, Perfmon.exe may identify one instance as myapp_1416 and the second as myapp_3160.</span></span>
  
> [!NOTE]
> <span data-ttu-id="957f7-140">如果兩個應用程式同名且使用舊版執行階段，則處理序識別碼可消除解析它們的模稜兩可。</span><span class="sxs-lookup"><span data-stu-id="957f7-140">The process identifier eliminates the ambiguity of resolving two applications with the same name that use earlier versions of the runtime.</span></span> <span data-ttu-id="957f7-141">舊版本不需要執行階段識別碼，因為舊版 Common Language Runtime 不支援並存案例。</span><span class="sxs-lookup"><span data-stu-id="957f7-141">A runtime identifier is not required for previous versions, because previous versions of the common language runtime do not support side-by-side scenarios.</span></span>  
  
 <span data-ttu-id="957f7-142">如果 .NET Framework 4 或更新版本不存在或已卸載，則設定登錄機碼沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="957f7-142">If the .NET Framework 4 or a later version is not present or was uninstalled, setting the registry key has no effect.</span></span> <span data-ttu-id="957f7-143">這表示，兩個同名的應用程式將會繼續在 Perfmon.exe 中顯示為 *application* 和 *application#1* (例如，**myapp** 和 **myapp#1**)。</span><span class="sxs-lookup"><span data-stu-id="957f7-143">This means that two applications with the same name will continue to appear in Perfmon.exe as *application* and *application#1* (for example, as **myapp** and **myapp#1**).</span></span>
