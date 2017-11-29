---
title: "&lt;PreferComInsteadOfManagedRemoting&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7aed6baa227b2bdf90c26f02d38ee67c1ffbbda1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltprefercominsteadofmanagedremotinggt-element"></a><span data-ttu-id="72f77-102">&lt;PreferComInsteadOfManagedRemoting&gt;項目</span><span class="sxs-lookup"><span data-stu-id="72f77-102">&lt;PreferComInsteadOfManagedRemoting&gt; Element</span></span>
<span data-ttu-id="72f77-103">指定是否執行階段會使用 COM interop 而不是遠端執行功能的所有呼叫跨越應用程式定義域界限。</span><span class="sxs-lookup"><span data-stu-id="72f77-103">Specifies whether the runtime will use COM interop instead of remoting for all calls across application domain boundaries.</span></span>  
  
 <span data-ttu-id="72f77-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="72f77-104">\<configuration></span></span>  
<span data-ttu-id="72f77-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="72f77-105">\<runtime></span></span>  
<span data-ttu-id="72f77-106">\<PreferComInsteadOfManagedRemoting ></span><span class="sxs-lookup"><span data-stu-id="72f77-106">\<PreferComInsteadOfManagedRemoting></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72f77-107">語法</span><span class="sxs-lookup"><span data-stu-id="72f77-107">Syntax</span></span>  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="72f77-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="72f77-108">Attributes and Elements</span></span>  
 <span data-ttu-id="72f77-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="72f77-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="72f77-110">屬性</span><span class="sxs-lookup"><span data-stu-id="72f77-110">Attributes</span></span>  
  
|<span data-ttu-id="72f77-111">屬性</span><span class="sxs-lookup"><span data-stu-id="72f77-111">Attribute</span></span>|<span data-ttu-id="72f77-112">描述</span><span class="sxs-lookup"><span data-stu-id="72f77-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="72f77-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="72f77-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="72f77-114">指出是否執行階段會使用 COM interop 而不是遠端處理跨應用程式定義域界限。</span><span class="sxs-lookup"><span data-stu-id="72f77-114">Indicates whether the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="72f77-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="72f77-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="72f77-116">值</span><span class="sxs-lookup"><span data-stu-id="72f77-116">Value</span></span>|<span data-ttu-id="72f77-117">說明</span><span class="sxs-lookup"><span data-stu-id="72f77-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="72f77-118">執行階段會使用遠端處理跨應用程式定義域界限。</span><span class="sxs-lookup"><span data-stu-id="72f77-118">The runtime will use remoting across application domain boundaries.</span></span> <span data-ttu-id="72f77-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="72f77-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="72f77-120">執行階段會跨應用程式定義域界限使用 COM interop。</span><span class="sxs-lookup"><span data-stu-id="72f77-120">The runtime will use COM interop across application domain boundaries.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="72f77-121">子元素</span><span class="sxs-lookup"><span data-stu-id="72f77-121">Child Elements</span></span>  
 <span data-ttu-id="72f77-122">無。</span><span class="sxs-lookup"><span data-stu-id="72f77-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="72f77-123">父項目</span><span class="sxs-lookup"><span data-stu-id="72f77-123">Parent Elements</span></span>  
  
|<span data-ttu-id="72f77-124">項目</span><span class="sxs-lookup"><span data-stu-id="72f77-124">Element</span></span>|<span data-ttu-id="72f77-125">描述</span><span class="sxs-lookup"><span data-stu-id="72f77-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="72f77-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="72f77-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="72f77-127">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="72f77-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72f77-128">備註</span><span class="sxs-lookup"><span data-stu-id="72f77-128">Remarks</span></span>  
 <span data-ttu-id="72f77-129">當您將`enabled`屬性`true`，執行階段行為，如下所示：</span><span class="sxs-lookup"><span data-stu-id="72f77-129">When you set the `enabled` attribute to `true`, the runtime behaves as follows:</span></span>  
  
-   <span data-ttu-id="72f77-130">執行階段不會呼叫[iunknown:: Queryinterface](http://go.microsoft.com/fwlink/?LinkID=144867)如[IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)介面[IUnknown](http://go.microsoft.com/fwlink/?LinkId=148003)介面進入透過 COM 介面的網域。</span><span class="sxs-lookup"><span data-stu-id="72f77-130">The runtime does not call [IUnknown::QueryInterface](http://go.microsoft.com/fwlink/?LinkID=144867) for an [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface when an [IUnknown](http://go.microsoft.com/fwlink/?LinkId=148003) interface enters the domain through a COM interface.</span></span> <span data-ttu-id="72f77-131">相反地，它是由建構[執行階段可呼叫包裝函式](../../../../../docs/framework/interop/runtime-callable-wrapper.md)(RCW) 的物件周圍。</span><span class="sxs-lookup"><span data-stu-id="72f77-131">Instead, it constructs a [Runtime Callable Wrapper](../../../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) around the object.</span></span>  
  
-   <span data-ttu-id="72f77-132">執行階段收到時，它會傳回 E_NOINTERFACE`QueryInterface`呼叫[IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)任何介面[COM 可呼叫包裝函式](../../../../../docs/framework/interop/com-callable-wrapper.md)(CCW)，已在這個網域中建立。</span><span class="sxs-lookup"><span data-stu-id="72f77-132">The runtime returns E_NOINTERFACE when it receives a `QueryInterface` call for an [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface for any [COM Callable Wrapper](../../../../../docs/framework/interop/com-callable-wrapper.md) (CCW) that has been created in this domain.</span></span>  
  
 <span data-ttu-id="72f77-133">這些兩種行為可確保所有的呼叫，透過 COM 介面之間受管理的物件，跨應用程式定義域界限使用 COM 和 COM interop，而不是遠端執行功能。</span><span class="sxs-lookup"><span data-stu-id="72f77-133">These two behaviors ensure that all calls over COM interfaces between managed objects across application domain boundaries use COM and COM interop instead of remoting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72f77-134">範例</span><span class="sxs-lookup"><span data-stu-id="72f77-134">Example</span></span>  
 <span data-ttu-id="72f77-135">下列範例示範如何指定執行階段應該使用 COM interop 跨隔離界限：</span><span class="sxs-lookup"><span data-stu-id="72f77-135">The following example shows how to specify that the runtime should use COM interop across isolation boundaries:</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="72f77-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72f77-136">See Also</span></span>  
 [<span data-ttu-id="72f77-137">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="72f77-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="72f77-138">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="72f77-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
