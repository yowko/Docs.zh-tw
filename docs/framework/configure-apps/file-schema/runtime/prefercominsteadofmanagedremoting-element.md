---
title: <PreferComInsteadOfManagedRemoting> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
ms.openlocfilehash: 2fb0d94f91d28f9d9d4f247411d273f786f7b63b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195281"
---
# <a name="prefercominsteadofmanagedremoting-element"></a><span data-ttu-id="1ec69-102">\<PreferComInsteadOfManagedRemoting> 項目</span><span class="sxs-lookup"><span data-stu-id="1ec69-102">\<PreferComInsteadOfManagedRemoting> Element</span></span>

<span data-ttu-id="1ec69-103">指定執行時間是否會在跨應用程式域界限的所有呼叫中使用 COM interop，而不是遠端處理。</span><span class="sxs-lookup"><span data-stu-id="1ec69-103">Specifies whether the runtime will use COM interop instead of remoting for all calls across application domain boundaries.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<PreferComInsteadOfManagedRemoting>**  
  
## <a name="syntax"></a><span data-ttu-id="1ec69-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="1ec69-104">Syntax</span></span>  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1ec69-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1ec69-105">Attributes and Elements</span></span>  

 <span data-ttu-id="1ec69-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="1ec69-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1ec69-107">屬性</span><span class="sxs-lookup"><span data-stu-id="1ec69-107">Attributes</span></span>  
  
|<span data-ttu-id="1ec69-108">屬性</span><span class="sxs-lookup"><span data-stu-id="1ec69-108">Attribute</span></span>|<span data-ttu-id="1ec69-109">描述</span><span class="sxs-lookup"><span data-stu-id="1ec69-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="1ec69-110">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="1ec69-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="1ec69-111">指出執行時間是否會使用 COM interop，而不是跨應用程式域界限進行遠端處理。</span><span class="sxs-lookup"><span data-stu-id="1ec69-111">Indicates whether the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="1ec69-112">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="1ec69-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="1ec69-113">值</span><span class="sxs-lookup"><span data-stu-id="1ec69-113">Value</span></span>|<span data-ttu-id="1ec69-114">描述</span><span class="sxs-lookup"><span data-stu-id="1ec69-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="1ec69-115">執行時間會跨應用程式域界限使用遠端功能。</span><span class="sxs-lookup"><span data-stu-id="1ec69-115">The runtime will use remoting across application domain boundaries.</span></span> <span data-ttu-id="1ec69-116">此為預設值。</span><span class="sxs-lookup"><span data-stu-id="1ec69-116">This is the default.</span></span>|  
|`true`|<span data-ttu-id="1ec69-117">執行時間會跨應用程式域界限使用 COM interop。</span><span class="sxs-lookup"><span data-stu-id="1ec69-117">The runtime will use COM interop across application domain boundaries.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1ec69-118">子元素</span><span class="sxs-lookup"><span data-stu-id="1ec69-118">Child Elements</span></span>  

 <span data-ttu-id="1ec69-119">無。</span><span class="sxs-lookup"><span data-stu-id="1ec69-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1ec69-120">父項目</span><span class="sxs-lookup"><span data-stu-id="1ec69-120">Parent Elements</span></span>  
  
|<span data-ttu-id="1ec69-121">項目</span><span class="sxs-lookup"><span data-stu-id="1ec69-121">Element</span></span>|<span data-ttu-id="1ec69-122">描述</span><span class="sxs-lookup"><span data-stu-id="1ec69-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1ec69-123">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="1ec69-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="1ec69-124">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="1ec69-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ec69-125">備註</span><span class="sxs-lookup"><span data-stu-id="1ec69-125">Remarks</span></span>  

 <span data-ttu-id="1ec69-126">當您將 `enabled` 屬性設定為時 `true` ，執行時間的行為會如下所示：</span><span class="sxs-lookup"><span data-stu-id="1ec69-126">When you set the `enabled` attribute to `true`, the runtime behaves as follows:</span></span>  
  
- <span data-ttu-id="1ec69-127">當[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)介面透過 COM 介面進入網域時，執行時間不會為[IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md)介面呼叫[IUnknown：： QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) 。</span><span class="sxs-lookup"><span data-stu-id="1ec69-127">The runtime does not call [IUnknown::QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) for an [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) interface when an [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) interface enters the domain through a COM interface.</span></span> <span data-ttu-id="1ec69-128">相反地，它會將執行時間可呼叫 [包裝](../../../../standard/native-interop/runtime-callable-wrapper.md) 函式 (RCW) 在物件周圍。</span><span class="sxs-lookup"><span data-stu-id="1ec69-128">Instead, it constructs a [Runtime Callable Wrapper](../../../../standard/native-interop/runtime-callable-wrapper.md) (RCW) around the object.</span></span>  
  
- <span data-ttu-id="1ec69-129">當執行時間接收到 `QueryInterface` 任何 COM 可呼叫[包裝](../../../../standard/native-interop/com-callable-wrapper.md)函式之[IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md)介面的呼叫時，此執行時間會傳回 E_NOINTERFACE， (在此網域中建立的 CCW) 。</span><span class="sxs-lookup"><span data-stu-id="1ec69-129">The runtime returns E_NOINTERFACE when it receives a `QueryInterface` call for an [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) interface for any [COM Callable Wrapper](../../../../standard/native-interop/com-callable-wrapper.md) (CCW) that has been created in this domain.</span></span>  
  
 <span data-ttu-id="1ec69-130">這兩種行為可確保跨應用程式域界限之 managed 物件之間的 COM 介面呼叫都使用 COM 和 COM interop，而不是遠端處理。</span><span class="sxs-lookup"><span data-stu-id="1ec69-130">These two behaviors ensure that all calls over COM interfaces between managed objects across application domain boundaries use COM and COM interop instead of remoting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ec69-131">範例</span><span class="sxs-lookup"><span data-stu-id="1ec69-131">Example</span></span>  

 <span data-ttu-id="1ec69-132">下列範例示範如何指定執行時間應該跨隔離界限使用 COM interop：</span><span class="sxs-lookup"><span data-stu-id="1ec69-132">The following example shows how to specify that the runtime should use COM interop across isolation boundaries:</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1ec69-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ec69-133">See also</span></span>

- [<span data-ttu-id="1ec69-134">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="1ec69-134">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="1ec69-135">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="1ec69-135">Configuration File Schema</span></span>](../index.md)
