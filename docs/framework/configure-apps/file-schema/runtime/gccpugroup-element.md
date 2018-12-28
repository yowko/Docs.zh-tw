---
title: '&lt;GCCpuGroup&gt;項目'
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25d083b730117a791fb8ab550b36f7b2e6c5f5be
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613709"
---
# <a name="ltgccpugroupgt-element"></a><span data-ttu-id="1035f-102">&lt;GCCpuGroup&gt;項目</span><span class="sxs-lookup"><span data-stu-id="1035f-102">&lt;GCCpuGroup&gt; Element</span></span>
<span data-ttu-id="1035f-103">指定記憶體回收是否支援多個 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="1035f-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>  
  
 <span data-ttu-id="1035f-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="1035f-104">\<configuration></span></span>  
<span data-ttu-id="1035f-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="1035f-105">\<runtime></span></span>  
<span data-ttu-id="1035f-106">\<GCCpuGroup></span><span class="sxs-lookup"><span data-stu-id="1035f-106">\<GCCpuGroup></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1035f-107">語法</span><span class="sxs-lookup"><span data-stu-id="1035f-107">Syntax</span></span>  
  
```xml  
<GCCpuGroup    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1035f-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1035f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1035f-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="1035f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1035f-110">屬性</span><span class="sxs-lookup"><span data-stu-id="1035f-110">Attributes</span></span>  
  
|<span data-ttu-id="1035f-111">屬性</span><span class="sxs-lookup"><span data-stu-id="1035f-111">Attribute</span></span>|<span data-ttu-id="1035f-112">描述</span><span class="sxs-lookup"><span data-stu-id="1035f-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="1035f-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="1035f-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="1035f-114">指定記憶體回收是否支援多個 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="1035f-114">Specifies whether garbage collection supports multiple CPU groups.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="1035f-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="1035f-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="1035f-116">值</span><span class="sxs-lookup"><span data-stu-id="1035f-116">Value</span></span>|<span data-ttu-id="1035f-117">描述</span><span class="sxs-lookup"><span data-stu-id="1035f-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="1035f-118">記憶體回收不支援多個 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="1035f-118">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="1035f-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="1035f-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="1035f-120">記憶體回收會支援多個 CPU 群組，如果已啟用伺服器記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="1035f-120">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1035f-121">子元素</span><span class="sxs-lookup"><span data-stu-id="1035f-121">Child Elements</span></span>  
 <span data-ttu-id="1035f-122">無。</span><span class="sxs-lookup"><span data-stu-id="1035f-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1035f-123">父項目</span><span class="sxs-lookup"><span data-stu-id="1035f-123">Parent Elements</span></span>  
  
|<span data-ttu-id="1035f-124">項目</span><span class="sxs-lookup"><span data-stu-id="1035f-124">Element</span></span>|<span data-ttu-id="1035f-125">描述</span><span class="sxs-lookup"><span data-stu-id="1035f-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1035f-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="1035f-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="1035f-127">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="1035f-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1035f-128">備註</span><span class="sxs-lookup"><span data-stu-id="1035f-128">Remarks</span></span>  
 <span data-ttu-id="1035f-129">當電腦具有多個 CPU 群組，而且啟用伺服器記憶體回收之後 (請參閱[ \<Gcserver> >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)項目)，啟用這個項目延伸到所有 CPU 群組的記憶體回收和採用到的所有核心帳戶建立和平衡堆積時。</span><span class="sxs-lookup"><span data-stu-id="1035f-129">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1035f-130">這個項目僅適用於記憶體回收執行緒。</span><span class="sxs-lookup"><span data-stu-id="1035f-130">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="1035f-131">若要啟用使用者執行緒分散到所有 CPU 群組的執行階段，您也必須啟用[< Thread_UseAllCpuGroups >](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)項目。</span><span class="sxs-lookup"><span data-stu-id="1035f-131">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [<Thread_UseAllCpuGroups>](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1035f-132">範例</span><span class="sxs-lookup"><span data-stu-id="1035f-132">Example</span></span>  
 <span data-ttu-id="1035f-133">下列範例示範如何啟用多個 CPU 群組記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="1035f-133">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1035f-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1035f-134">See Also</span></span>  
- [<span data-ttu-id="1035f-135">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="1035f-135">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [<span data-ttu-id="1035f-136">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="1035f-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [<span data-ttu-id="1035f-137">如何：停用並行記憶體回收</span><span class="sxs-lookup"><span data-stu-id="1035f-137">How to: Disable Concurrent Garbage Collection</span></span>](https://msdn.microsoft.com/library/ba2c6c67-5778-497c-9fac-5f793b5500c7)  
- [<span data-ttu-id="1035f-138">工作站和伺服器記憶體回收</span><span class="sxs-lookup"><span data-stu-id="1035f-138">Workstation and server garbage collection</span></span>](../../../../../docs/standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)
