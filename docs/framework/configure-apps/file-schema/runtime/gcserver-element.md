---
title: <gcServer> 項目
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
ms.openlocfilehash: 61b4076a72dbc17ffc800a1a8d37a22d1435e02b
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663688"
---
# <a name="gcserver-element"></a><span data-ttu-id="4e458-102">\<gcServer > 元素</span><span class="sxs-lookup"><span data-stu-id="4e458-102">\<gcServer> Element</span></span>
<span data-ttu-id="4e458-103">指定 Common Language Runtime 是否執行伺服器記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="4e458-103">Specifies whether the common language runtime runs server garbage collection.</span></span>  
  
 <span data-ttu-id="4e458-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="4e458-104">\<configuration></span></span>  
<span data-ttu-id="4e458-105">\<執行時間 ></span><span class="sxs-lookup"><span data-stu-id="4e458-105">\<runtime></span></span>  
<span data-ttu-id="4e458-106">\<gcServer></span><span class="sxs-lookup"><span data-stu-id="4e458-106">\<gcServer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e458-107">語法</span><span class="sxs-lookup"><span data-stu-id="4e458-107">Syntax</span></span>  
  
```xml  
<gcServer    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4e458-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4e458-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4e458-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="4e458-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4e458-110">屬性</span><span class="sxs-lookup"><span data-stu-id="4e458-110">Attributes</span></span>  
  
|<span data-ttu-id="4e458-111">屬性</span><span class="sxs-lookup"><span data-stu-id="4e458-111">Attribute</span></span>|<span data-ttu-id="4e458-112">描述</span><span class="sxs-lookup"><span data-stu-id="4e458-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="4e458-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="4e458-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="4e458-114">指定執行階段是否執行伺服器記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="4e458-114">Specifies whether the runtime runs server garbage collection.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="4e458-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="4e458-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="4e458-116">值</span><span class="sxs-lookup"><span data-stu-id="4e458-116">Value</span></span>|<span data-ttu-id="4e458-117">描述</span><span class="sxs-lookup"><span data-stu-id="4e458-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="4e458-118">不執行伺服器記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="4e458-118">Does not run server garbage collection.</span></span> <span data-ttu-id="4e458-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="4e458-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="4e458-120">執行伺服器記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="4e458-120">Runs server garbage collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4e458-121">子元素</span><span class="sxs-lookup"><span data-stu-id="4e458-121">Child Elements</span></span>  
 <span data-ttu-id="4e458-122">無。</span><span class="sxs-lookup"><span data-stu-id="4e458-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4e458-123">父項目</span><span class="sxs-lookup"><span data-stu-id="4e458-123">Parent Elements</span></span>  
  
|<span data-ttu-id="4e458-124">項目</span><span class="sxs-lookup"><span data-stu-id="4e458-124">Element</span></span>|<span data-ttu-id="4e458-125">說明</span><span class="sxs-lookup"><span data-stu-id="4e458-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4e458-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="4e458-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="4e458-127">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="4e458-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e458-128">備註</span><span class="sxs-lookup"><span data-stu-id="4e458-128">Remarks</span></span>  
 <span data-ttu-id="4e458-129">Common Language Runtime (CLR) 支援兩種類型的記憶體回收：工作站記憶體回收 (可用於所有系統)，以及伺服器記憶體回收 (可用於多處理器系統)。</span><span class="sxs-lookup"><span data-stu-id="4e458-129">The common language runtime (CLR) supports two types of garbage collection: workstation garbage collection, which is available on all systems, and server garbage collection, which is available on multiprocessor systems.</span></span> <span data-ttu-id="4e458-130">您可以使用 `<gcServer>` 項目來控制 CLR 執行的記憶體回收類型。</span><span class="sxs-lookup"><span data-stu-id="4e458-130">You use the `<gcServer>` element to control the type of garbage collection the CLR performs.</span></span> <span data-ttu-id="4e458-131">使用 <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> 屬性來決定是否啟用伺服器記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="4e458-131">Use the <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> property to determine if server garbage collection is enabled.</span></span>  
  
 <span data-ttu-id="4e458-132">針對單一處理器電腦，預設的工作站記憶體回收應該是最快的選項。</span><span class="sxs-lookup"><span data-stu-id="4e458-132">For single-processor computers, the default workstation garbage collection should be the fastest option.</span></span> <span data-ttu-id="4e458-133">無論是工作站或伺服器，都可以用於兩個處理器的電腦。</span><span class="sxs-lookup"><span data-stu-id="4e458-133">Either workstation or server can be used for two-processor computers.</span></span> <span data-ttu-id="4e458-134">針對兩個以上的處理器，伺服器記憶體回收應該是最快的選項。</span><span class="sxs-lookup"><span data-stu-id="4e458-134">Server garbage collection should be the fastest option for more than two processors.</span></span>  
  
 <span data-ttu-id="4e458-135">此項目只能用在應用程式組態檔中；如果是在或電腦組態檔中，就會忽略此項目。</span><span class="sxs-lookup"><span data-stu-id="4e458-135">This element can be used only in the application configuration file; it is ignored if it is in the machine configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e458-136">在 .NET Framework 4 (含) 以前版本中，當伺服器記憶體回收啟用時，無法使用並行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="4e458-136">In the .NET Framework 4 and earlier versions, concurrent garbage collection is not available when server garbage collection is enabled.</span></span> <span data-ttu-id="4e458-137">從 .NET Framework 4.5 開始，伺服器記憶體回收為並行。</span><span class="sxs-lookup"><span data-stu-id="4e458-137">Starting with the .NET Framework 4.5, server garbage collection is concurrent.</span></span> <span data-ttu-id="4e458-138">若要使用非並行伺服器垃圾收集, 請將`<gcServer>`元素設`true`為, 並[ \<將 gcConcurrent >](gcconcurrent-element.md)專案設定為。 `false`</span><span class="sxs-lookup"><span data-stu-id="4e458-138">To use non-concurrent server garbage collection, set the `<gcServer>` element to `true` and the [\<gcConcurrent> element](gcconcurrent-element.md) to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e458-139">範例</span><span class="sxs-lookup"><span data-stu-id="4e458-139">Example</span></span>  
 <span data-ttu-id="4e458-140">下列範例會啟用伺服器記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="4e458-140">The following example enables server garbage collection.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4e458-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e458-141">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="4e458-142">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="4e458-142">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="4e458-143">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="4e458-143">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="4e458-144">停用並行垃圾收集</span><span class="sxs-lookup"><span data-stu-id="4e458-144">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
