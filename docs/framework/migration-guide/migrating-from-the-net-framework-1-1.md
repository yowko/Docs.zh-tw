---
title: "從 .NET Framework 1.1 移轉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework 4.5, migrating from 1.1
- .NET Framework 1.1, migrating to .NET Framework 4.5
ms.assetid: 7ead0cb3-3b19-414a-8417-a1c1fa198d9e
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5757894a63ed556413147b8ef8c85c2d31ef11a5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="migrating-from-the-net-framework-11"></a><span data-ttu-id="35e20-102">從 .NET Framework 1.1 移轉</span><span class="sxs-lookup"><span data-stu-id="35e20-102">Migrating from the .NET Framework 1.1</span></span>
[!INCLUDE[win7](../../../includes/win7-md.md)]<span data-ttu-id="35e20-103"> 和更新版本的 Windows 作業系統不支援 [!INCLUDE[net_v11_long](../../../includes/net-v11-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="35e20-103"> and later versions of the Windows operating system do not support the [!INCLUDE[net_v11_long](../../../includes/net-v11-long-md.md)].</span></span> <span data-ttu-id="35e20-104">因此，以 [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] 為目標的應用程式一定要在 [!INCLUDE[win7](../../../includes/win7-md.md)] 或更新版本的作業系統上修改才能執行。</span><span class="sxs-lookup"><span data-stu-id="35e20-104">As a result, applications that target the [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] will not run without modification on [!INCLUDE[win7](../../../includes/win7-md.md)] or later operating system versions.</span></span> <span data-ttu-id="35e20-105">本主題討論在 [!INCLUDE[win7](../../../includes/win7-md.md)] 和更新版本的 Windows 作業系統底下執行以 [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] 為目標的應用程式時所需的步驟。</span><span class="sxs-lookup"><span data-stu-id="35e20-105">This topic discusses the steps required to run an application that targets the [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] under [!INCLUDE[win7](../../../includes/win7-md.md)] and later versions of the Windows operating system.</span></span> <span data-ttu-id="35e20-106">如需有關 [!INCLUDE[net_v11_long](../../../includes/net-v11-long-md.md)] 和 [!INCLUDE[win8](../../../includes/win8-md.md)] 的詳細資訊，請參閱[在 Windows 8 及更新版本上執行 .NET Framework 1.1 應用程式](../../../docs/framework/install/run-net-framework-1-1-apps.md)。</span><span class="sxs-lookup"><span data-stu-id="35e20-106">For more information about the [!INCLUDE[net_v11_long](../../../includes/net-v11-long-md.md)] and [!INCLUDE[win8](../../../includes/win8-md.md)], see [Running .NET Framework 1.1 Apps on Windows 8 and later versions](../../../docs/framework/install/run-net-framework-1-1-apps.md).</span></span>  
  
## <a name="retargeting-or-recompiling"></a><span data-ttu-id="35e20-107">重定目標或重新編譯</span><span class="sxs-lookup"><span data-stu-id="35e20-107">Retargeting or Recompiling</span></span>  
 <span data-ttu-id="35e20-108">有兩種方式可取得之前使用 [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] 所編譯的應用程式，使其在 [!INCLUDE[win7](../../../includes/win7-md.md)] 和更新版本的 Windows 作業系統上執行：</span><span class="sxs-lookup"><span data-stu-id="35e20-108">There are two ways to get an application that was compiled using the [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] to run on [!INCLUDE[win7](../../../includes/win7-md.md)] or a later Windows operating system:</span></span>  
  
-   <span data-ttu-id="35e20-109">您可以重新設定應用程式的目標，使其在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 底下執行。</span><span class="sxs-lookup"><span data-stu-id="35e20-109">You can retarget the application to run under [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="35e20-110">重新設定目標需要您將 [\<supportedRuntime>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) 元素加入至應用程式的組態檔，使它可以在 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 之下執行。</span><span class="sxs-lookup"><span data-stu-id="35e20-110">Retargeting requires that you add a [\<supportedRuntime>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) element to the application's configuration file that allows it to run under [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].</span></span> <span data-ttu-id="35e20-111">這類組態檔的形式如下：</span><span class="sxs-lookup"><span data-stu-id="35e20-111">Such a configuration file takes the following form:</span></span>  
  
    ```xml  
    <configuration>   
       <startup>  
          <supportedRuntime version="v4.0"/>  
       </startup>  
    </configuration>  
    ```  
  
-   <span data-ttu-id="35e20-112">您可以使用以 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]為目標的編譯器來重新編譯應用程式。</span><span class="sxs-lookup"><span data-stu-id="35e20-112">You can recompile the application with a compiler that targets the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].</span></span> <span data-ttu-id="35e20-113">如果您原本使用 Visual Studio 2003 來開發及編譯您的方案，您可以在 [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)] 中開啟此方案，並且使用 [ **專案相容性** ] 對話方塊來將此方案和專案檔從 Visual Studio 2003 使用的格式轉換成 [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)]使用的 Microsoft Build Engine (MSBuild) 格式。</span><span class="sxs-lookup"><span data-stu-id="35e20-113">If you originally used Visual Studio 2003 to develop and compile your solution, you can open the solution in [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)] and use the **Project Compatibility** dialog box to convert the solution and project files from the formats used by Visual Studio 2003 to the Microsoft Build Engine (MSBuild) format used by [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)].</span></span>  
  
 <span data-ttu-id="35e20-114">不論您偏好重新編譯應用程式還是重新設定應用程式的目標，您都必須決定您的應用程式是否會受到較新 .NET Framework 版本中引入的任何變更所影響。</span><span class="sxs-lookup"><span data-stu-id="35e20-114">Regardless of whether you prefer to recompile or retarget your application, you must determine whether your application is affected by any changes introduced in later versions of the .NET Framework.</span></span> <span data-ttu-id="35e20-115">這些變更有兩種：</span><span class="sxs-lookup"><span data-stu-id="35e20-115">These changes are of two kinds:</span></span>  
  
-   <span data-ttu-id="35e20-116">在 [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] 與較新版 .NET Framework 之間發生的重大變更。</span><span class="sxs-lookup"><span data-stu-id="35e20-116">Breaking changes that occurred between the [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] and later versions of the .NET Framework.</span></span>  
  
-   <span data-ttu-id="35e20-117">在 [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] 與較新版 .NET Framework 之間，標示為已被取代或已過時的型別與型別成員。</span><span class="sxs-lookup"><span data-stu-id="35e20-117">Types and type members that have been marked as deprecated or obsolete between the [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] and later versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="35e20-118">當您重新設定應用程式的目標或重新編譯時，您應該針對 [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)]之後發行的每一個 .NET Framework 版本來檢閱重大變更及過時的型別和成員。</span><span class="sxs-lookup"><span data-stu-id="35e20-118">Whether you retarget your application or recompile it, you should review both the breaking changes and the obsolete types and members for each version of the .NET Framework that was released after [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)].</span></span>  
  
## <a name="breaking-changes"></a><span data-ttu-id="35e20-119">重大變更</span><span class="sxs-lookup"><span data-stu-id="35e20-119">Breaking Changes</span></span>  
 <span data-ttu-id="35e20-120">當發生重大變更時，重新設定目標及重新編譯的應用程式可能會有替代解決辦法可用 (視特定變更而定)。</span><span class="sxs-lookup"><span data-stu-id="35e20-120">When a breaking change occurs, depending on the specific change, a workaround may be available both for retargeted and recompiled applications.</span></span> <span data-ttu-id="35e20-121">在某些情況下，您可以將子元素加入至應用程式組態檔的 [\<runtime>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) 元素，以還原舊版的行為。</span><span class="sxs-lookup"><span data-stu-id="35e20-121">In some cases, you can add a child element to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) element of your application's configuration file to restore the previous behavior.</span></span> <span data-ttu-id="35e20-122">例如，下列組態檔會還原 [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] 中使用的字串排序和比較行為，而且可以搭配重新設定目標或重新編譯的應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="35e20-122">For example, the following configuration file restores the string sorting and comparison behavior used in the [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] and can be used either with a retargeted or a recompiled application.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="35e20-123">但是在某些情況下，您可能必須修改原始程式碼及重新編譯應用程式。</span><span class="sxs-lookup"><span data-stu-id="35e20-123">However, in some cases, you may have to modify your source code and recompile your application.</span></span>  
  
 <span data-ttu-id="35e20-124">若要評估可能的重大變更對您的應用程式的影響，您必須檢閱以下變更清單：</span><span class="sxs-lookup"><span data-stu-id="35e20-124">To assess the impact of possible breaking changes on your application, you must review the following lists of changes:</span></span>  
  
-   <span data-ttu-id="35e20-125">[.NET Framework 2.0 中的重大變更](http://go.microsoft.com/fwlink/?LinkId=125263) 記錄可能會影響以 [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] 為目標之應用程式的 [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)]變更。</span><span class="sxs-lookup"><span data-stu-id="35e20-125">[Breaking Changes in .NET Framework 2.0](http://go.microsoft.com/fwlink/?LinkId=125263) documents changes in [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] that can affect an application that targets [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)].</span></span>  
  
-   <span data-ttu-id="35e20-126">[.NET Framework 3.5 SP1 中的變更](http://go.microsoft.com/fwlink/?LinkID=186989) 記錄在 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] 和 [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)]之間的變更。</span><span class="sxs-lookup"><span data-stu-id="35e20-126">[Changes in .NET Framework 3.5 SP1](http://go.microsoft.com/fwlink/?LinkID=186989) documents changes between the [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] and the [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)].</span></span>  
  
-   <span data-ttu-id="35e20-127">[.NET Framework 4 移轉問題](../../../docs/framework/migration-guide/net-framework-4-migration-issues.md) 記錄在 [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] 和 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 之間的變更。</span><span class="sxs-lookup"><span data-stu-id="35e20-127">[.NET Framework 4 Migration Issues](../../../docs/framework/migration-guide/net-framework-4-migration-issues.md) documents changes between the [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] and the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].</span></span>  
  
## <a name="obsolete-types-and-members"></a><span data-ttu-id="35e20-128">過時的型別和成員</span><span class="sxs-lookup"><span data-stu-id="35e20-128">Obsolete Types and Members</span></span>  
 <span data-ttu-id="35e20-129">對於重新設定目標的應用程式和重新編譯的應用程式而言，已被取代的型別和成員的影響有些不同。</span><span class="sxs-lookup"><span data-stu-id="35e20-129">The impact of deprecated types and members is somewhat different for retargeted applications and recompiled applications.</span></span> <span data-ttu-id="35e20-130">使用過時的型別和成員將不會影響重新設定目標的應用程式，除非已經從其組件中實際移除過時的型別或成員。</span><span class="sxs-lookup"><span data-stu-id="35e20-130">The use of obsolete types and members will not affect a retargeted application unless the obsolete type or member has been physically removed from its assembly.</span></span> <span data-ttu-id="35e20-131">重新編譯使用過時型別或成員的應用程式通常會產生編譯器警告，而不是編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="35e20-131">Recompiling an application that uses obsolete types or members usually produces a compiler warning rather than a compiler error.</span></span> <span data-ttu-id="35e20-132">但是在某些情況下，它會產生編譯器錯誤，而且使用過時型別或成員的程式碼無法成功編譯。</span><span class="sxs-lookup"><span data-stu-id="35e20-132">However, in some cases, it produces a compiler error, and code that uses the obsolete type or member does not compile successfully.</span></span> <span data-ttu-id="35e20-133">在此情況下，您必須重新撰寫呼叫過時型別或成員的原始程式碼，然後重新編譯應用程式。</span><span class="sxs-lookup"><span data-stu-id="35e20-133">In this case, you must rewrite the source code that calls the obsolete type or member before you recompile your application.</span></span> <span data-ttu-id="35e20-134">如需過時類型和成員的詳細資訊，請參閱[類別庫中的過時功能](../../../docs/framework/whats-new/whats-obsolete.md)。</span><span class="sxs-lookup"><span data-stu-id="35e20-134">For more information about obsolete types and members, see [What's Obsolete in the Class Library](../../../docs/framework/whats-new/whats-obsolete.md).</span></span>  
  
 <span data-ttu-id="35e20-135">若要評估自從 [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] 發行之後已被取代之類型和成員的影響，請參閱[類別庫中的過時功能](../../../docs/framework/whats-new/whats-obsolete.md)。</span><span class="sxs-lookup"><span data-stu-id="35e20-135">To assess the impact of types and members that have been deprecated since the release of the [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)], see [What's Obsolete in the Class Library](../../../docs/framework/whats-new/whats-obsolete.md).</span></span> <span data-ttu-id="35e20-136">針對 [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)]、[!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] 和 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 檢閱過時的型別和成員清單。</span><span class="sxs-lookup"><span data-stu-id="35e20-136">Review the lists of obsolete types and member for the [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)], the [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)], and the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].</span></span>
