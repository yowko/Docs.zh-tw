---
title: "&lt;disableCommitThreadStack&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCommitThreadStack
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCommitThreadStack
helpviewer_keywords:
- <disableCommitThreadStack> element
- disableCommitThreadStack element
ms.assetid: 3559d46a-7640-4c72-9a11-7e980768929e
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4a7961c62d46a10767b119c4c55a4b620e1ad782
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltdisablecommitthreadstackgt-element"></a><span data-ttu-id="73261-102">&lt;disableCommitThreadStack&gt;項目</span><span class="sxs-lookup"><span data-stu-id="73261-102">&lt;disableCommitThreadStack&gt; Element</span></span>
<span data-ttu-id="73261-103">指定是否在執行緒啟動時認可完整執行緒堆疊。</span><span class="sxs-lookup"><span data-stu-id="73261-103">Specifies whether the full thread stack is committed when a thread is started.</span></span>  
  
 <span data-ttu-id="73261-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="73261-104">\<configuration></span></span>  
<span data-ttu-id="73261-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="73261-105">\<runtime></span></span>  
<span data-ttu-id="73261-106">\<disableCommitThreadStack ></span><span class="sxs-lookup"><span data-stu-id="73261-106">\<disableCommitThreadStack></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73261-107">語法</span><span class="sxs-lookup"><span data-stu-id="73261-107">Syntax</span></span>  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73261-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="73261-108">Attributes and Elements</span></span>  
 <span data-ttu-id="73261-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="73261-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73261-110">屬性</span><span class="sxs-lookup"><span data-stu-id="73261-110">Attributes</span></span>  
  
|<span data-ttu-id="73261-111">屬性</span><span class="sxs-lookup"><span data-stu-id="73261-111">Attribute</span></span>|<span data-ttu-id="73261-112">描述</span><span class="sxs-lookup"><span data-stu-id="73261-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="73261-113">enabled</span><span class="sxs-lookup"><span data-stu-id="73261-113">enabled</span></span>|<span data-ttu-id="73261-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="73261-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="73261-115">指定是否停用在執行緒啟動時認可完整執行緒堆疊 (預設行為)。</span><span class="sxs-lookup"><span data-stu-id="73261-115">Specifies whether committing the full thread stack on thread startup (the default behavior) is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="73261-116">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="73261-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="73261-117">值</span><span class="sxs-lookup"><span data-stu-id="73261-117">Value</span></span>|<span data-ttu-id="73261-118">描述</span><span class="sxs-lookup"><span data-stu-id="73261-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="73261-119">0</span><span class="sxs-lookup"><span data-stu-id="73261-119">0</span></span>|<span data-ttu-id="73261-120">不停用 Common Language Runtime 的預設行為，也就是在執行緒啟動時認可完整執行緒堆疊。</span><span class="sxs-lookup"><span data-stu-id="73261-120">Do not disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
|<span data-ttu-id="73261-121">1</span><span class="sxs-lookup"><span data-stu-id="73261-121">1</span></span>|<span data-ttu-id="73261-122">不停用 Common Language Runtime 的預設行為，也就是在執行緒啟動時認可完整執行緒堆疊。</span><span class="sxs-lookup"><span data-stu-id="73261-122">Disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="73261-123">子元素</span><span class="sxs-lookup"><span data-stu-id="73261-123">Child Elements</span></span>  
 <span data-ttu-id="73261-124">無。</span><span class="sxs-lookup"><span data-stu-id="73261-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="73261-125">父項目</span><span class="sxs-lookup"><span data-stu-id="73261-125">Parent Elements</span></span>  
  
|<span data-ttu-id="73261-126">項目</span><span class="sxs-lookup"><span data-stu-id="73261-126">Element</span></span>|<span data-ttu-id="73261-127">描述</span><span class="sxs-lookup"><span data-stu-id="73261-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="73261-128">Common Language Runtime 和 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 應用程式所使用之所有組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="73261-128">The root element in every configuration file used by the common language runtime and [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] applications.</span></span>|  
|`runtime`|<span data-ttu-id="73261-129">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="73261-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73261-130">備註</span><span class="sxs-lookup"><span data-stu-id="73261-130">Remarks</span></span>  
 <span data-ttu-id="73261-131">Common Language Runtime 的預設行為是在執行緒啟動時認可完整執行緒堆疊。</span><span class="sxs-lookup"><span data-stu-id="73261-131">The default behavior of the common language runtime is to commit the full thread stack when a thread is started.</span></span> <span data-ttu-id="73261-132">如果必須在具有有限記憶體的伺服器上建立大量執行緒，而且大部分的執行緒都會使用極小的堆疊空間，則 Common Language Runtime 不要在執行緒啟動時立即認可完整執行緒堆疊，伺服器的效能可能會較好。</span><span class="sxs-lookup"><span data-stu-id="73261-132">If a large number of threads must be created on a server that has limited memory, and most of those threads will use very little stack space, the server might perform better if the common language runtime does not commit the full thread stack immediately when a thread is started.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="73261-133">未受管理的主機可以在 `STARTUP_DISABLE_COMMITTHREADSTACK` STARTUP_FLAGS [列舉中使用](../../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) 啟動旗標，來達到相同的結果。</span><span class="sxs-lookup"><span data-stu-id="73261-133">Unmanaged hosts can use the `STARTUP_DISABLE_COMMITTHREADSTACK` startup flag in the [STARTUP_FLAGS](../../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration to accomplish the same result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73261-134">範例</span><span class="sxs-lookup"><span data-stu-id="73261-134">Example</span></span>  
 <span data-ttu-id="73261-135">下列範例示範如何停用 Common Language Runtime 的預設行為，也就是在執行緒啟動時認可完整執行緒堆疊。</span><span class="sxs-lookup"><span data-stu-id="73261-135">The following example shows how to disable the default behavior of the common language runtime, which is to commit the full thread stack on thread startup.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="73261-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="73261-136">See Also</span></span>  
 [<span data-ttu-id="73261-137">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="73261-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="73261-138">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="73261-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
