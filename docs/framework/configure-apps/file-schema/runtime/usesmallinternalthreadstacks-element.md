---
title: "&lt;UseSmallInternalThreadStacks&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c96537cad59034578d1284f7dc432e5775f3730b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltusesmallinternalthreadstacksgt-element"></a><span data-ttu-id="4e03e-102">&lt;UseSmallInternalThreadStacks&gt;項目</span><span class="sxs-lookup"><span data-stu-id="4e03e-102">&lt;UseSmallInternalThreadStacks&gt; Element</span></span>
<span data-ttu-id="4e03e-103">藉由指定明確的堆疊大小，它會建立特定的執行緒，它會在內部使用，而不是使用預設堆疊大小，這些執行緒時，使用 common language runtime (CLR)，減少記憶體的要求。</span><span class="sxs-lookup"><span data-stu-id="4e03e-103">Requests that the common language runtime (CLR) reduce memory use by specifying explicit stack sizes when it creates certain threads that it uses internally, instead of using the default stack size for those threads.</span></span>  
  
 <span data-ttu-id="4e03e-104">\<設定 > 項目</span><span class="sxs-lookup"><span data-stu-id="4e03e-104">\<configuration> Element</span></span>  
<span data-ttu-id="4e03e-105">\<runtime > 項目</span><span class="sxs-lookup"><span data-stu-id="4e03e-105">\<runtime> Element</span></span>  
<span data-ttu-id="4e03e-106">\<UseSmallInternalThreadStacks > 項目</span><span class="sxs-lookup"><span data-stu-id="4e03e-106">\<UseSmallInternalThreadStacks> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e03e-107">語法</span><span class="sxs-lookup"><span data-stu-id="4e03e-107">Syntax</span></span>  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4e03e-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4e03e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4e03e-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="4e03e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4e03e-110">屬性</span><span class="sxs-lookup"><span data-stu-id="4e03e-110">Attributes</span></span>  
  
|<span data-ttu-id="4e03e-111">屬性</span><span class="sxs-lookup"><span data-stu-id="4e03e-111">Attribute</span></span>|<span data-ttu-id="4e03e-112">描述</span><span class="sxs-lookup"><span data-stu-id="4e03e-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4e03e-113">enabled</span><span class="sxs-lookup"><span data-stu-id="4e03e-113">enabled</span></span>|<span data-ttu-id="4e03e-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="4e03e-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="4e03e-115">指定是否要求 CLR 使用明確的堆疊大小，而不是預設堆疊大小時它會建立特定的執行緒，它會在內部使用。</span><span class="sxs-lookup"><span data-stu-id="4e03e-115">Specifies whether to request that the CLR use explicit stack sizes instead of the default stack size when it creates certain threads that it uses internally.</span></span> <span data-ttu-id="4e03e-116">明確的堆疊大小會小於 1 MB 的預設堆疊大小。</span><span class="sxs-lookup"><span data-stu-id="4e03e-116">The explicit stack sizes are smaller than the default stack size of 1 MB.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="4e03e-117">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="4e03e-117">enabled Attribute</span></span>  
  
|<span data-ttu-id="4e03e-118">值</span><span class="sxs-lookup"><span data-stu-id="4e03e-118">Value</span></span>|<span data-ttu-id="4e03e-119">描述</span><span class="sxs-lookup"><span data-stu-id="4e03e-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4e03e-120">true</span><span class="sxs-lookup"><span data-stu-id="4e03e-120">true</span></span>|<span data-ttu-id="4e03e-121">要求明確的堆疊大小。</span><span class="sxs-lookup"><span data-stu-id="4e03e-121">Request explicit stack sizes.</span></span>|  
|<span data-ttu-id="4e03e-122">false</span><span class="sxs-lookup"><span data-stu-id="4e03e-122">false</span></span>|<span data-ttu-id="4e03e-123">使用預設堆疊大小。</span><span class="sxs-lookup"><span data-stu-id="4e03e-123">Use the default stack size.</span></span> <span data-ttu-id="4e03e-124">這是預設值[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4e03e-124">This is the default for the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4e03e-125">子元素</span><span class="sxs-lookup"><span data-stu-id="4e03e-125">Child Elements</span></span>  
 <span data-ttu-id="4e03e-126">無。</span><span class="sxs-lookup"><span data-stu-id="4e03e-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4e03e-127">父項目</span><span class="sxs-lookup"><span data-stu-id="4e03e-127">Parent Elements</span></span>  
  
|<span data-ttu-id="4e03e-128">項目</span><span class="sxs-lookup"><span data-stu-id="4e03e-128">Element</span></span>|<span data-ttu-id="4e03e-129">描述</span><span class="sxs-lookup"><span data-stu-id="4e03e-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4e03e-130">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="4e03e-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="4e03e-131">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="4e03e-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e03e-132">備註</span><span class="sxs-lookup"><span data-stu-id="4e03e-132">Remarks</span></span>  
 <span data-ttu-id="4e03e-133">這個組態項目用來要求在處理程序，減少的虛擬記憶體使用，因為如果接受要求，則 CLR 會使用其內部執行緒的明確執行緒大小為小於預設大小。</span><span class="sxs-lookup"><span data-stu-id="4e03e-133">This configuration element is used to request reduced virtual memory use in a process, because the explicit thread sizes that the CLR uses for its internal threads, if the request is honored, are smaller than the default size.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4e03e-134">這個組態項目是要求 CLR，而不是絕對必要的需求。</span><span class="sxs-lookup"><span data-stu-id="4e03e-134">This configuration element is a request to the CLR rather than an absolute requirement.</span></span> <span data-ttu-id="4e03e-135">在[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]，要求會被接受只適用於 x86 架構。</span><span class="sxs-lookup"><span data-stu-id="4e03e-135">In the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], the request is honored only for the x86 architecture.</span></span> <span data-ttu-id="4e03e-136">可能在未來版本的 CLR 中完全忽略這個項目，或明確的堆疊大小一定會用於選取的內部執行緒會被取代。</span><span class="sxs-lookup"><span data-stu-id="4e03e-136">This element might be ignored completely in future versions of the CLR, or replaced by explicit stack sizes that are always used for selected internal threads.</span></span>  
  
 <span data-ttu-id="4e03e-137">指定這個組態項目往來的較小的虛擬記憶體使用可靠性是否 CLR 會接受要求，因為較小的堆疊大小可能無法使堆疊可能溢位。</span><span class="sxs-lookup"><span data-stu-id="4e03e-137">Specifying this configuration element trades reliability for smaller virtual memory use if the CLR honors the request, because smaller stack sizes could potentially make stack overflows more likely.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e03e-138">範例</span><span class="sxs-lookup"><span data-stu-id="4e03e-138">Example</span></span>  
 <span data-ttu-id="4e03e-139">下列範例會示範如何要求 CLR 使用明確堆疊調整特定大小的執行緒，它會在內部使用。</span><span class="sxs-lookup"><span data-stu-id="4e03e-139">The following example shows how to request that the CLR use explicit stack sizes for certain threads that it uses internally.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4e03e-140">請參閱</span><span class="sxs-lookup"><span data-stu-id="4e03e-140">See Also</span></span>  
 [<span data-ttu-id="4e03e-141">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="4e03e-141">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="4e03e-142">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="4e03e-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
