---
title: '&lt;PreferComInsteadOfManagedRemoting&gt;項目'
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c05e27226a58086c806e8977ba50a55873d1167e
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46002069"
---
# <a name="ltprefercominsteadofmanagedremotinggt-element"></a><span data-ttu-id="a906f-102">&lt;PreferComInsteadOfManagedRemoting&gt;項目</span><span class="sxs-lookup"><span data-stu-id="a906f-102">&lt;PreferComInsteadOfManagedRemoting&gt; Element</span></span>
<span data-ttu-id="a906f-103">指定是否執行階段會使用 COM interop 而不是遠端處理的所有呼叫跨越應用程式定義域界限。</span><span class="sxs-lookup"><span data-stu-id="a906f-103">Specifies whether the runtime will use COM interop instead of remoting for all calls across application domain boundaries.</span></span>  
  
 <span data-ttu-id="a906f-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="a906f-104">\<configuration></span></span>  
<span data-ttu-id="a906f-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="a906f-105">\<runtime></span></span>  
<span data-ttu-id="a906f-106">\<PreferComInsteadOfManagedRemoting ></span><span class="sxs-lookup"><span data-stu-id="a906f-106">\<PreferComInsteadOfManagedRemoting></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a906f-107">語法</span><span class="sxs-lookup"><span data-stu-id="a906f-107">Syntax</span></span>  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a906f-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a906f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a906f-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a906f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a906f-110">屬性</span><span class="sxs-lookup"><span data-stu-id="a906f-110">Attributes</span></span>  
  
|<span data-ttu-id="a906f-111">屬性</span><span class="sxs-lookup"><span data-stu-id="a906f-111">Attribute</span></span>|<span data-ttu-id="a906f-112">描述</span><span class="sxs-lookup"><span data-stu-id="a906f-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="a906f-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="a906f-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="a906f-114">指出是否執行階段會使用 COM interop 而不是遠端處理跨應用程式定義域界限。</span><span class="sxs-lookup"><span data-stu-id="a906f-114">Indicates whether the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="a906f-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="a906f-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="a906f-116">值</span><span class="sxs-lookup"><span data-stu-id="a906f-116">Value</span></span>|<span data-ttu-id="a906f-117">描述</span><span class="sxs-lookup"><span data-stu-id="a906f-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="a906f-118">執行階段會使用遠端處理跨應用程式定義域界限。</span><span class="sxs-lookup"><span data-stu-id="a906f-118">The runtime will use remoting across application domain boundaries.</span></span> <span data-ttu-id="a906f-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="a906f-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="a906f-120">執行階段會跨應用程式定義域界限使用 COM interop。</span><span class="sxs-lookup"><span data-stu-id="a906f-120">The runtime will use COM interop across application domain boundaries.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a906f-121">子元素</span><span class="sxs-lookup"><span data-stu-id="a906f-121">Child Elements</span></span>  
 <span data-ttu-id="a906f-122">無。</span><span class="sxs-lookup"><span data-stu-id="a906f-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a906f-123">父項目</span><span class="sxs-lookup"><span data-stu-id="a906f-123">Parent Elements</span></span>  
  
|<span data-ttu-id="a906f-124">項目</span><span class="sxs-lookup"><span data-stu-id="a906f-124">Element</span></span>|<span data-ttu-id="a906f-125">描述</span><span class="sxs-lookup"><span data-stu-id="a906f-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a906f-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="a906f-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="a906f-127">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="a906f-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a906f-128">備註</span><span class="sxs-lookup"><span data-stu-id="a906f-128">Remarks</span></span>  
 <span data-ttu-id="a906f-129">當您設定`enabled`屬性設定為`true`，執行階段行為，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a906f-129">When you set the `enabled` attribute to `true`, the runtime behaves as follows:</span></span>  
  
-   <span data-ttu-id="a906f-130">執行階段不會呼叫[iunknown:: Queryinterface](https://go.microsoft.com/fwlink/?LinkID=144867) for [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)介面[IUnknown](https://go.microsoft.com/fwlink/?LinkId=148003)介面進入網域透過 COM 介面。</span><span class="sxs-lookup"><span data-stu-id="a906f-130">The runtime does not call [IUnknown::QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) for an [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface when an [IUnknown](https://go.microsoft.com/fwlink/?LinkId=148003) interface enters the domain through a COM interface.</span></span> <span data-ttu-id="a906f-131">相反地，它會建構[執行階段可呼叫包裝函式](../../../../../docs/framework/interop/runtime-callable-wrapper.md)(RCW) 物件周圍。</span><span class="sxs-lookup"><span data-stu-id="a906f-131">Instead, it constructs a [Runtime Callable Wrapper](../../../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) around the object.</span></span>  
  
-   <span data-ttu-id="a906f-132">執行階段會接收時，會傳回 E_NOINTERFACE`QueryInterface`呼叫[IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)介面的任何[COM 可呼叫包裝函式](../../../../../docs/framework/interop/com-callable-wrapper.md)(CCW)，已建立在這個網域中。</span><span class="sxs-lookup"><span data-stu-id="a906f-132">The runtime returns E_NOINTERFACE when it receives a `QueryInterface` call for an [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface for any [COM Callable Wrapper](../../../../../docs/framework/interop/com-callable-wrapper.md) (CCW) that has been created in this domain.</span></span>  
  
 <span data-ttu-id="a906f-133">這些兩種行為可確保所有呼叫 com 都介面之間受管理的物件，在應用程式定義域界限使用 COM 和 COM interop，而不是遠端執行功能。</span><span class="sxs-lookup"><span data-stu-id="a906f-133">These two behaviors ensure that all calls over COM interfaces between managed objects across application domain boundaries use COM and COM interop instead of remoting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a906f-134">範例</span><span class="sxs-lookup"><span data-stu-id="a906f-134">Example</span></span>  
 <span data-ttu-id="a906f-135">下列範例示範如何指定執行階段應該使用 COM interop 跨越隔離界限：</span><span class="sxs-lookup"><span data-stu-id="a906f-135">The following example shows how to specify that the runtime should use COM interop across isolation boundaries:</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a906f-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a906f-136">See Also</span></span>  
 [<span data-ttu-id="a906f-137">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="a906f-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="a906f-138">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="a906f-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
