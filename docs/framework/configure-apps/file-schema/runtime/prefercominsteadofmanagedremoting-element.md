---
title: <PreferComInsteadOfManagedRemoting> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c79c76717acf7ff309375313b30534dd0aff9399
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920701"
---
# <a name="prefercominsteadofmanagedremoting-element"></a><span data-ttu-id="c0061-102">\<PreferComInsteadOfManagedRemoting > 元素</span><span class="sxs-lookup"><span data-stu-id="c0061-102">\<PreferComInsteadOfManagedRemoting> Element</span></span>
<span data-ttu-id="c0061-103">指定執行時間是否會針對跨應用程式域界限的所有呼叫, 使用 COM Interop 而不是遠端處理。</span><span class="sxs-lookup"><span data-stu-id="c0061-103">Specifies whether the runtime will use COM interop instead of remoting for all calls across application domain boundaries.</span></span>  
  
 <span data-ttu-id="c0061-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="c0061-104">\<configuration></span></span>  
<span data-ttu-id="c0061-105">\<執行時間 ></span><span class="sxs-lookup"><span data-stu-id="c0061-105">\<runtime></span></span>  
<span data-ttu-id="c0061-106">\<PreferComInsteadOfManagedRemoting></span><span class="sxs-lookup"><span data-stu-id="c0061-106">\<PreferComInsteadOfManagedRemoting></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0061-107">語法</span><span class="sxs-lookup"><span data-stu-id="c0061-107">Syntax</span></span>  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0061-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c0061-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c0061-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c0061-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0061-110">屬性</span><span class="sxs-lookup"><span data-stu-id="c0061-110">Attributes</span></span>  
  
|<span data-ttu-id="c0061-111">屬性</span><span class="sxs-lookup"><span data-stu-id="c0061-111">Attribute</span></span>|<span data-ttu-id="c0061-112">說明</span><span class="sxs-lookup"><span data-stu-id="c0061-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="c0061-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="c0061-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="c0061-114">指出執行時間是否會使用 COM Interop, 而不是跨應用程式域界限進行遠端處理。</span><span class="sxs-lookup"><span data-stu-id="c0061-114">Indicates whether the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="c0061-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="c0061-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="c0061-116">值</span><span class="sxs-lookup"><span data-stu-id="c0061-116">Value</span></span>|<span data-ttu-id="c0061-117">描述</span><span class="sxs-lookup"><span data-stu-id="c0061-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="c0061-118">執行時間會跨應用程式域界限使用遠端功能。</span><span class="sxs-lookup"><span data-stu-id="c0061-118">The runtime will use remoting across application domain boundaries.</span></span> <span data-ttu-id="c0061-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="c0061-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="c0061-120">執行時間會跨應用程式域界限使用 COM Interop。</span><span class="sxs-lookup"><span data-stu-id="c0061-120">The runtime will use COM interop across application domain boundaries.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c0061-121">子元素</span><span class="sxs-lookup"><span data-stu-id="c0061-121">Child Elements</span></span>  
 <span data-ttu-id="c0061-122">無。</span><span class="sxs-lookup"><span data-stu-id="c0061-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c0061-123">父項目</span><span class="sxs-lookup"><span data-stu-id="c0061-123">Parent Elements</span></span>  
  
|<span data-ttu-id="c0061-124">項目</span><span class="sxs-lookup"><span data-stu-id="c0061-124">Element</span></span>|<span data-ttu-id="c0061-125">描述</span><span class="sxs-lookup"><span data-stu-id="c0061-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c0061-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="c0061-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="c0061-127">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="c0061-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0061-128">備註</span><span class="sxs-lookup"><span data-stu-id="c0061-128">Remarks</span></span>  
 <span data-ttu-id="c0061-129">當您將`enabled`屬性設定為`true`時, 執行時間的行為會如下所示:</span><span class="sxs-lookup"><span data-stu-id="c0061-129">When you set the `enabled` attribute to `true`, the runtime behaves as follows:</span></span>  
  
- <span data-ttu-id="c0061-130">當[iunknown](https://go.microsoft.com/fwlink/?LinkId=148003)介面透過 COM 介面進入網域時, 執行時間不會針對[IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md)介面呼叫[IUnknown:: QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) 。</span><span class="sxs-lookup"><span data-stu-id="c0061-130">The runtime does not call [IUnknown::QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) for an [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) interface when an [IUnknown](https://go.microsoft.com/fwlink/?LinkId=148003) interface enters the domain through a COM interface.</span></span> <span data-ttu-id="c0061-131">相反地, 它會在物件周圍建立執行時間可呼叫[包裝](../../../../standard/native-interop/runtime-callable-wrapper.md)函式 (RCW)。</span><span class="sxs-lookup"><span data-stu-id="c0061-131">Instead, it constructs a [Runtime Callable Wrapper](../../../../standard/native-interop/runtime-callable-wrapper.md) (RCW) around the object.</span></span>  
  
- <span data-ttu-id="c0061-132">執行時間會在收到`QueryInterface`此網域中已建立之任何 COM 可呼叫[包裝](../../../../standard/native-interop/com-callable-wrapper.md)函式 (CCW) 的[IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md)介面呼叫時傳回 E_NOINTERFACE。</span><span class="sxs-lookup"><span data-stu-id="c0061-132">The runtime returns E_NOINTERFACE when it receives a `QueryInterface` call for an [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) interface for any [COM Callable Wrapper](../../../../standard/native-interop/com-callable-wrapper.md) (CCW) that has been created in this domain.</span></span>  
  
 <span data-ttu-id="c0061-133">這兩種行為可確保跨應用程式域界限的 managed 物件之間的所有呼叫都是使用 COM 和 COM Interop, 而不是遠端處理。</span><span class="sxs-lookup"><span data-stu-id="c0061-133">These two behaviors ensure that all calls over COM interfaces between managed objects across application domain boundaries use COM and COM interop instead of remoting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0061-134">範例</span><span class="sxs-lookup"><span data-stu-id="c0061-134">Example</span></span>  
 <span data-ttu-id="c0061-135">下列範例顯示如何指定執行時間應該跨隔離界限使用 COM Interop:</span><span class="sxs-lookup"><span data-stu-id="c0061-135">The following example shows how to specify that the runtime should use COM interop across isolation boundaries:</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c0061-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0061-136">See also</span></span>

- [<span data-ttu-id="c0061-137">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="c0061-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c0061-138">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="c0061-138">Configuration File Schema</span></span>](../index.md)
