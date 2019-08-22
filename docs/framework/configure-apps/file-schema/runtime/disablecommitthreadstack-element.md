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
ms.openlocfilehash: 4b1f55f056ef1aed4a5eff655650cefe778c97ae
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663788"
---
# <a name="disablecommitthreadstack-element"></a><span data-ttu-id="d984e-102">\<disableCommitThreadStack > 元素</span><span class="sxs-lookup"><span data-stu-id="d984e-102">\<disableCommitThreadStack> Element</span></span>
<span data-ttu-id="d984e-103">指定是否在執行緒啟動時認可完整執行緒堆疊。</span><span class="sxs-lookup"><span data-stu-id="d984e-103">Specifies whether the full thread stack is committed when a thread is started.</span></span>  
  
 <span data-ttu-id="d984e-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="d984e-104">\<configuration></span></span>  
<span data-ttu-id="d984e-105">\<執行時間 ></span><span class="sxs-lookup"><span data-stu-id="d984e-105">\<runtime></span></span>  
<span data-ttu-id="d984e-106">\<disableCommitThreadStack></span><span class="sxs-lookup"><span data-stu-id="d984e-106">\<disableCommitThreadStack></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d984e-107">語法</span><span class="sxs-lookup"><span data-stu-id="d984e-107">Syntax</span></span>  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d984e-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d984e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d984e-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d984e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d984e-110">屬性</span><span class="sxs-lookup"><span data-stu-id="d984e-110">Attributes</span></span>  
  
|<span data-ttu-id="d984e-111">屬性</span><span class="sxs-lookup"><span data-stu-id="d984e-111">Attribute</span></span>|<span data-ttu-id="d984e-112">說明</span><span class="sxs-lookup"><span data-stu-id="d984e-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d984e-113">enabled</span><span class="sxs-lookup"><span data-stu-id="d984e-113">enabled</span></span>|<span data-ttu-id="d984e-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="d984e-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="d984e-115">指定是否停用在執行緒啟動時認可完整執行緒堆疊 (預設行為)。</span><span class="sxs-lookup"><span data-stu-id="d984e-115">Specifies whether committing the full thread stack on thread startup (the default behavior) is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="d984e-116">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="d984e-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="d984e-117">值</span><span class="sxs-lookup"><span data-stu-id="d984e-117">Value</span></span>|<span data-ttu-id="d984e-118">描述</span><span class="sxs-lookup"><span data-stu-id="d984e-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d984e-119">0</span><span class="sxs-lookup"><span data-stu-id="d984e-119">0</span></span>|<span data-ttu-id="d984e-120">不停用 Common Language Runtime 的預設行為，也就是在執行緒啟動時認可完整執行緒堆疊。</span><span class="sxs-lookup"><span data-stu-id="d984e-120">Do not disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
|<span data-ttu-id="d984e-121">1</span><span class="sxs-lookup"><span data-stu-id="d984e-121">1</span></span>|<span data-ttu-id="d984e-122">不停用 Common Language Runtime 的預設行為，也就是在執行緒啟動時認可完整執行緒堆疊。</span><span class="sxs-lookup"><span data-stu-id="d984e-122">Disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d984e-123">子元素</span><span class="sxs-lookup"><span data-stu-id="d984e-123">Child Elements</span></span>  
 <span data-ttu-id="d984e-124">無。</span><span class="sxs-lookup"><span data-stu-id="d984e-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d984e-125">父項目</span><span class="sxs-lookup"><span data-stu-id="d984e-125">Parent Elements</span></span>  
  
|<span data-ttu-id="d984e-126">項目</span><span class="sxs-lookup"><span data-stu-id="d984e-126">Element</span></span>|<span data-ttu-id="d984e-127">說明</span><span class="sxs-lookup"><span data-stu-id="d984e-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d984e-128">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="d984e-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d984e-129">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="d984e-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d984e-130">備註</span><span class="sxs-lookup"><span data-stu-id="d984e-130">Remarks</span></span>  
 <span data-ttu-id="d984e-131">Common Language Runtime 的預設行為是在執行緒啟動時認可完整執行緒堆疊。</span><span class="sxs-lookup"><span data-stu-id="d984e-131">The default behavior of the common language runtime is to commit the full thread stack when a thread is started.</span></span> <span data-ttu-id="d984e-132">如果必須在具有有限記憶體的伺服器上建立大量執行緒，而且大部分的執行緒都會使用極小的堆疊空間，則 Common Language Runtime 不要在執行緒啟動時立即認可完整執行緒堆疊，伺服器的效能可能會較好。</span><span class="sxs-lookup"><span data-stu-id="d984e-132">If a large number of threads must be created on a server that has limited memory, and most of those threads will use very little stack space, the server might perform better if the common language runtime does not commit the full thread stack immediately when a thread is started.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d984e-133">未受管理的主機可以在 `STARTUP_DISABLE_COMMITTHREADSTACK` STARTUP_FLAGS [列舉中使用](../../../unmanaged-api/hosting/startup-flags-enumeration.md) 啟動旗標，來達到相同的結果。</span><span class="sxs-lookup"><span data-stu-id="d984e-133">Unmanaged hosts can use the `STARTUP_DISABLE_COMMITTHREADSTACK` startup flag in the [STARTUP_FLAGS](../../../unmanaged-api/hosting/startup-flags-enumeration.md) enumeration to accomplish the same result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d984e-134">範例</span><span class="sxs-lookup"><span data-stu-id="d984e-134">Example</span></span>  
 <span data-ttu-id="d984e-135">下列範例示範如何停用 Common Language Runtime 的預設行為，也就是在執行緒啟動時認可完整執行緒堆疊。</span><span class="sxs-lookup"><span data-stu-id="d984e-135">The following example shows how to disable the default behavior of the common language runtime, which is to commit the full thread stack on thread startup.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d984e-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d984e-136">See also</span></span>

- [<span data-ttu-id="d984e-137">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="d984e-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d984e-138">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="d984e-138">Configuration File Schema</span></span>](../index.md)
