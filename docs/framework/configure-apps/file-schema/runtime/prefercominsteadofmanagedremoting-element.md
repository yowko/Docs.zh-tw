---
title: <PreferComInsteadOfManagedRemoting> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d793c8d84a15f554ada78f3c0dd1f0e936893fd4
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252400"
---
# <a name="prefercominsteadofmanagedremoting-element"></a><span data-ttu-id="574ae-102">\<PreferComInsteadOfManagedRemoting > 元素</span><span class="sxs-lookup"><span data-stu-id="574ae-102">\<PreferComInsteadOfManagedRemoting> Element</span></span>
<span data-ttu-id="574ae-103">指定執行時間是否會針對跨應用程式域界限的所有呼叫，使用 COM Interop 而不是遠端處理。</span><span class="sxs-lookup"><span data-stu-id="574ae-103">Specifies whether the runtime will use COM interop instead of remoting for all calls across application domain boundaries.</span></span>  
  
<span data-ttu-id="574ae-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="574ae-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="574ae-105">&nbsp;&nbsp;[ **\<執行時間 >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="574ae-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="574ae-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<PreferComInsteadOfManagedRemoting>**</span><span class="sxs-lookup"><span data-stu-id="574ae-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<PreferComInsteadOfManagedRemoting>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="574ae-107">語法</span><span class="sxs-lookup"><span data-stu-id="574ae-107">Syntax</span></span>  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="574ae-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="574ae-108">Attributes and Elements</span></span>  
 <span data-ttu-id="574ae-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="574ae-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="574ae-110">屬性</span><span class="sxs-lookup"><span data-stu-id="574ae-110">Attributes</span></span>  
  
|<span data-ttu-id="574ae-111">屬性</span><span class="sxs-lookup"><span data-stu-id="574ae-111">Attribute</span></span>|<span data-ttu-id="574ae-112">說明</span><span class="sxs-lookup"><span data-stu-id="574ae-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="574ae-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="574ae-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="574ae-114">指出執行時間是否會使用 COM Interop，而不是跨應用程式域界限進行遠端處理。</span><span class="sxs-lookup"><span data-stu-id="574ae-114">Indicates whether the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="574ae-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="574ae-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="574ae-116">值</span><span class="sxs-lookup"><span data-stu-id="574ae-116">Value</span></span>|<span data-ttu-id="574ae-117">說明</span><span class="sxs-lookup"><span data-stu-id="574ae-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="574ae-118">執行時間會跨應用程式域界限使用遠端功能。</span><span class="sxs-lookup"><span data-stu-id="574ae-118">The runtime will use remoting across application domain boundaries.</span></span> <span data-ttu-id="574ae-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="574ae-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="574ae-120">執行時間會跨應用程式域界限使用 COM Interop。</span><span class="sxs-lookup"><span data-stu-id="574ae-120">The runtime will use COM interop across application domain boundaries.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="574ae-121">子元素</span><span class="sxs-lookup"><span data-stu-id="574ae-121">Child Elements</span></span>  
 <span data-ttu-id="574ae-122">無。</span><span class="sxs-lookup"><span data-stu-id="574ae-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="574ae-123">父項目</span><span class="sxs-lookup"><span data-stu-id="574ae-123">Parent Elements</span></span>  
  
|<span data-ttu-id="574ae-124">項目</span><span class="sxs-lookup"><span data-stu-id="574ae-124">Element</span></span>|<span data-ttu-id="574ae-125">描述</span><span class="sxs-lookup"><span data-stu-id="574ae-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="574ae-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="574ae-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="574ae-127">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="574ae-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="574ae-128">備註</span><span class="sxs-lookup"><span data-stu-id="574ae-128">Remarks</span></span>  
 <span data-ttu-id="574ae-129">當您將`enabled`屬性設定為`true`時，執行時間的行為會如下所示：</span><span class="sxs-lookup"><span data-stu-id="574ae-129">When you set the `enabled` attribute to `true`, the runtime behaves as follows:</span></span>  
  
- <span data-ttu-id="574ae-130">當[iunknown](https://go.microsoft.com/fwlink/?LinkId=148003)介面透過 COM 介面進入網域時，執行時間不會針對[IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md)介面呼叫[IUnknown：： QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) 。</span><span class="sxs-lookup"><span data-stu-id="574ae-130">The runtime does not call [IUnknown::QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) for an [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) interface when an [IUnknown](https://go.microsoft.com/fwlink/?LinkId=148003) interface enters the domain through a COM interface.</span></span> <span data-ttu-id="574ae-131">相反地，它會在物件周圍建立執行時間可呼叫[包裝](../../../../standard/native-interop/runtime-callable-wrapper.md)函式（RCW）。</span><span class="sxs-lookup"><span data-stu-id="574ae-131">Instead, it constructs a [Runtime Callable Wrapper](../../../../standard/native-interop/runtime-callable-wrapper.md) (RCW) around the object.</span></span>  
  
- <span data-ttu-id="574ae-132">執行時間會在收到`QueryInterface`此網域中已建立之任何 COM 可呼叫[包裝](../../../../standard/native-interop/com-callable-wrapper.md)函式（CCW）的[IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md)介面呼叫時傳回 E_NOINTERFACE。</span><span class="sxs-lookup"><span data-stu-id="574ae-132">The runtime returns E_NOINTERFACE when it receives a `QueryInterface` call for an [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) interface for any [COM Callable Wrapper](../../../../standard/native-interop/com-callable-wrapper.md) (CCW) that has been created in this domain.</span></span>  
  
 <span data-ttu-id="574ae-133">這兩種行為可確保跨應用程式域界限的 managed 物件之間的所有呼叫都是使用 COM 和 COM Interop，而不是遠端處理。</span><span class="sxs-lookup"><span data-stu-id="574ae-133">These two behaviors ensure that all calls over COM interfaces between managed objects across application domain boundaries use COM and COM interop instead of remoting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="574ae-134">範例</span><span class="sxs-lookup"><span data-stu-id="574ae-134">Example</span></span>  
 <span data-ttu-id="574ae-135">下列範例顯示如何指定執行時間應該跨隔離界限使用 COM Interop：</span><span class="sxs-lookup"><span data-stu-id="574ae-135">The following example shows how to specify that the runtime should use COM interop across isolation boundaries:</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="574ae-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="574ae-136">See also</span></span>

- [<span data-ttu-id="574ae-137">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="574ae-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="574ae-138">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="574ae-138">Configuration File Schema</span></span>](../index.md)
