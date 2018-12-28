---
title: '&lt;gcServer&gt;項目'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcServer
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcServer
helpviewer_keywords:
- gcServer element
- <gcServer> element
ms.assetid: 8d25b80e-2581-4803-bd87-a59528e3cb03
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 80421a66a3ace4970324fb295e167b7d4875063f
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610673"
---
# <a name="ltgcservergt-element"></a><span data-ttu-id="52bd1-102">&lt;gcServer&gt;項目</span><span class="sxs-lookup"><span data-stu-id="52bd1-102">&lt;gcServer&gt; Element</span></span>
<span data-ttu-id="52bd1-103">指定 Common Language Runtime 是否執行伺服器記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="52bd1-103">Specifies whether the common language runtime runs server garbage collection.</span></span>  
  
 <span data-ttu-id="52bd1-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="52bd1-104">\<configuration></span></span>  
<span data-ttu-id="52bd1-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="52bd1-105">\<runtime></span></span>  
<span data-ttu-id="52bd1-106">\<gcServer></span><span class="sxs-lookup"><span data-stu-id="52bd1-106">\<gcServer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52bd1-107">語法</span><span class="sxs-lookup"><span data-stu-id="52bd1-107">Syntax</span></span>  
  
```xml  
<gcServer    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="52bd1-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="52bd1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="52bd1-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="52bd1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="52bd1-110">屬性</span><span class="sxs-lookup"><span data-stu-id="52bd1-110">Attributes</span></span>  
  
|<span data-ttu-id="52bd1-111">屬性</span><span class="sxs-lookup"><span data-stu-id="52bd1-111">Attribute</span></span>|<span data-ttu-id="52bd1-112">描述</span><span class="sxs-lookup"><span data-stu-id="52bd1-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="52bd1-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="52bd1-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="52bd1-114">指定執行階段是否執行伺服器記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="52bd1-114">Specifies whether the runtime runs server garbage collection.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="52bd1-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="52bd1-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="52bd1-116">值</span><span class="sxs-lookup"><span data-stu-id="52bd1-116">Value</span></span>|<span data-ttu-id="52bd1-117">描述</span><span class="sxs-lookup"><span data-stu-id="52bd1-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="52bd1-118">不執行伺服器記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="52bd1-118">Does not run server garbage collection.</span></span> <span data-ttu-id="52bd1-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="52bd1-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="52bd1-120">執行伺服器記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="52bd1-120">Runs server garbage collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="52bd1-121">子元素</span><span class="sxs-lookup"><span data-stu-id="52bd1-121">Child Elements</span></span>  
 <span data-ttu-id="52bd1-122">無。</span><span class="sxs-lookup"><span data-stu-id="52bd1-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="52bd1-123">父項目</span><span class="sxs-lookup"><span data-stu-id="52bd1-123">Parent Elements</span></span>  
  
|<span data-ttu-id="52bd1-124">項目</span><span class="sxs-lookup"><span data-stu-id="52bd1-124">Element</span></span>|<span data-ttu-id="52bd1-125">描述</span><span class="sxs-lookup"><span data-stu-id="52bd1-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="52bd1-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="52bd1-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="52bd1-127">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="52bd1-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52bd1-128">備註</span><span class="sxs-lookup"><span data-stu-id="52bd1-128">Remarks</span></span>  
 <span data-ttu-id="52bd1-129">Common Language Runtime (CLR) 支援兩種類型的記憶體回收：工作站記憶體回收 (可用於所有系統)，以及伺服器記憶體回收 (可用於多處理器系統)。</span><span class="sxs-lookup"><span data-stu-id="52bd1-129">The common language runtime (CLR) supports two types of garbage collection: workstation garbage collection, which is available on all systems, and server garbage collection, which is available on multiprocessor systems.</span></span> <span data-ttu-id="52bd1-130">您可以使用 `<gcServer>` 項目來控制 CLR 執行的記憶體回收類型。</span><span class="sxs-lookup"><span data-stu-id="52bd1-130">You use the `<gcServer>` element to control the type of garbage collection the CLR performs.</span></span> <span data-ttu-id="52bd1-131">使用 <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> 屬性來決定是否啟用伺服器記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="52bd1-131">Use the <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> property to determine if server garbage collection is enabled.</span></span>  
  
 <span data-ttu-id="52bd1-132">針對單一處理器電腦，預設的工作站記憶體回收應該是最快的選項。</span><span class="sxs-lookup"><span data-stu-id="52bd1-132">For single-processor computers, the default workstation garbage collection should be the fastest option.</span></span> <span data-ttu-id="52bd1-133">無論是工作站或伺服器，都可以用於兩個處理器的電腦。</span><span class="sxs-lookup"><span data-stu-id="52bd1-133">Either workstation or server can be used for two-processor computers.</span></span> <span data-ttu-id="52bd1-134">針對兩個以上的處理器，伺服器記憶體回收應該是最快的選項。</span><span class="sxs-lookup"><span data-stu-id="52bd1-134">Server garbage collection should be the fastest option for more than two processors.</span></span>  
  
 <span data-ttu-id="52bd1-135">此項目只能用在應用程式組態檔中；如果是在或電腦組態檔中，就會忽略此項目。</span><span class="sxs-lookup"><span data-stu-id="52bd1-135">This element can be used only in the application configuration file; it is ignored if it is in the machine configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52bd1-136">在 .NET Framework 4 (含) 以前版本中，當伺服器記憶體回收啟用時，無法使用並行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="52bd1-136">In the .NET Framework 4 and earlier versions, concurrent garbage collection is not available when server garbage collection is enabled.</span></span> <span data-ttu-id="52bd1-137">從 [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)] 開始，伺服器記憶體回收為並行。</span><span class="sxs-lookup"><span data-stu-id="52bd1-137">Starting with the [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], server garbage collection is concurrent.</span></span> <span data-ttu-id="52bd1-138">若要使用非並行伺服器記憶體回收，將`<gcServer>`項目`true`並[ \<gcConcurrent > 項目](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)來`false`。</span><span class="sxs-lookup"><span data-stu-id="52bd1-138">To use non-concurrent server garbage collection, set the `<gcServer>` element to `true` and the [\<gcConcurrent> element](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52bd1-139">範例</span><span class="sxs-lookup"><span data-stu-id="52bd1-139">Example</span></span>  
 <span data-ttu-id="52bd1-140">下列範例會啟用伺服器記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="52bd1-140">The following example enables server garbage collection.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="52bd1-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52bd1-141">See Also</span></span>  
- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="52bd1-142">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="52bd1-142">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [<span data-ttu-id="52bd1-143">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="52bd1-143">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [<span data-ttu-id="52bd1-144">如何：停用並行記憶體回收</span><span class="sxs-lookup"><span data-stu-id="52bd1-144">How to: Disable Concurrent Garbage Collection</span></span>](https://msdn.microsoft.com/library/ba2c6c67-5778-497c-9fac-5f793b5500c7)
