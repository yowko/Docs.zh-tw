---
title: <disableCommitThreadStack> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCommitThreadStack
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCommitThreadStack
helpviewer_keywords:
- <disableCommitThreadStack> element
- disableCommitThreadStack element
ms.assetid: 3559d46a-7640-4c72-9a11-7e980768929e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08ffd6ffcb9a8fa356d486f6d2ae1113de0fa682
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59106505"
---
# <a name="disablecommitthreadstack-element"></a><span data-ttu-id="f259d-102">\<disableCommitThreadStack > 項目</span><span class="sxs-lookup"><span data-stu-id="f259d-102">\<disableCommitThreadStack> Element</span></span>
<span data-ttu-id="f259d-103">指定是否在執行緒啟動時認可完整執行緒堆疊。</span><span class="sxs-lookup"><span data-stu-id="f259d-103">Specifies whether the full thread stack is committed when a thread is started.</span></span>  
  
 <span data-ttu-id="f259d-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="f259d-104">\<configuration></span></span>  
<span data-ttu-id="f259d-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="f259d-105">\<runtime></span></span>  
<span data-ttu-id="f259d-106">\<disableCommitThreadStack></span><span class="sxs-lookup"><span data-stu-id="f259d-106">\<disableCommitThreadStack></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f259d-107">語法</span><span class="sxs-lookup"><span data-stu-id="f259d-107">Syntax</span></span>  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f259d-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f259d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f259d-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f259d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f259d-110">屬性</span><span class="sxs-lookup"><span data-stu-id="f259d-110">Attributes</span></span>  
  
|<span data-ttu-id="f259d-111">屬性</span><span class="sxs-lookup"><span data-stu-id="f259d-111">Attribute</span></span>|<span data-ttu-id="f259d-112">描述</span><span class="sxs-lookup"><span data-stu-id="f259d-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f259d-113">enabled</span><span class="sxs-lookup"><span data-stu-id="f259d-113">enabled</span></span>|<span data-ttu-id="f259d-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="f259d-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="f259d-115">指定是否停用在執行緒啟動時認可完整執行緒堆疊 (預設行為)。</span><span class="sxs-lookup"><span data-stu-id="f259d-115">Specifies whether committing the full thread stack on thread startup (the default behavior) is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="f259d-116">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="f259d-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="f259d-117">值</span><span class="sxs-lookup"><span data-stu-id="f259d-117">Value</span></span>|<span data-ttu-id="f259d-118">描述</span><span class="sxs-lookup"><span data-stu-id="f259d-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f259d-119">0</span><span class="sxs-lookup"><span data-stu-id="f259d-119">0</span></span>|<span data-ttu-id="f259d-120">不停用 Common Language Runtime 的預設行為，也就是在執行緒啟動時認可完整執行緒堆疊。</span><span class="sxs-lookup"><span data-stu-id="f259d-120">Do not disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
|<span data-ttu-id="f259d-121">1</span><span class="sxs-lookup"><span data-stu-id="f259d-121">1</span></span>|<span data-ttu-id="f259d-122">不停用 Common Language Runtime 的預設行為，也就是在執行緒啟動時認可完整執行緒堆疊。</span><span class="sxs-lookup"><span data-stu-id="f259d-122">Disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f259d-123">子元素</span><span class="sxs-lookup"><span data-stu-id="f259d-123">Child Elements</span></span>  
 <span data-ttu-id="f259d-124">無。</span><span class="sxs-lookup"><span data-stu-id="f259d-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f259d-125">父項目</span><span class="sxs-lookup"><span data-stu-id="f259d-125">Parent Elements</span></span>  
  
|<span data-ttu-id="f259d-126">項目</span><span class="sxs-lookup"><span data-stu-id="f259d-126">Element</span></span>|<span data-ttu-id="f259d-127">描述</span><span class="sxs-lookup"><span data-stu-id="f259d-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f259d-128">Common Language Runtime 和 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 應用程式所使用之所有組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="f259d-128">The root element in every configuration file used by the common language runtime and [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] applications.</span></span>|  
|`runtime`|<span data-ttu-id="f259d-129">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="f259d-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f259d-130">備註</span><span class="sxs-lookup"><span data-stu-id="f259d-130">Remarks</span></span>  
 <span data-ttu-id="f259d-131">Common Language Runtime 的預設行為是在執行緒啟動時認可完整執行緒堆疊。</span><span class="sxs-lookup"><span data-stu-id="f259d-131">The default behavior of the common language runtime is to commit the full thread stack when a thread is started.</span></span> <span data-ttu-id="f259d-132">如果必須在具有有限記憶體的伺服器上建立大量執行緒，而且大部分的執行緒都會使用極小的堆疊空間，則 Common Language Runtime 不要在執行緒啟動時立即認可完整執行緒堆疊，伺服器的效能可能會較好。</span><span class="sxs-lookup"><span data-stu-id="f259d-132">If a large number of threads must be created on a server that has limited memory, and most of those threads will use very little stack space, the server might perform better if the common language runtime does not commit the full thread stack immediately when a thread is started.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f259d-133">未受管理的主機可以在 `STARTUP_DISABLE_COMMITTHREADSTACK` STARTUP_FLAGS [列舉中使用](../../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) 啟動旗標，來達到相同的結果。</span><span class="sxs-lookup"><span data-stu-id="f259d-133">Unmanaged hosts can use the `STARTUP_DISABLE_COMMITTHREADSTACK` startup flag in the [STARTUP_FLAGS](../../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration to accomplish the same result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f259d-134">範例</span><span class="sxs-lookup"><span data-stu-id="f259d-134">Example</span></span>  
 <span data-ttu-id="f259d-135">下列範例示範如何停用 Common Language Runtime 的預設行為，也就是在執行緒啟動時認可完整執行緒堆疊。</span><span class="sxs-lookup"><span data-stu-id="f259d-135">The following example shows how to disable the default behavior of the common language runtime, which is to commit the full thread stack on thread startup.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f259d-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f259d-136">See also</span></span>

- [<span data-ttu-id="f259d-137">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="f259d-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="f259d-138">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="f259d-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
