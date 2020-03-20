---
title: <appDomainManagerType> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
ms.openlocfilehash: 8eb6129b3fafaeb81a94d5a4078e41a16583a226
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154419"
---
# <a name="appdomainmanagertype-element"></a><span data-ttu-id="a12e6-102">\<應用域管理器類型>元素</span><span class="sxs-lookup"><span data-stu-id="a12e6-102">\<appDomainManagerType> Element</span></span>
<span data-ttu-id="a12e6-103">針對預設應用程式網域，指定做為應用程式網域管理員的類型。</span><span class="sxs-lookup"><span data-stu-id="a12e6-103">Specifies the type that serves as the application domain manager for the default application domain.</span></span>  
  
<span data-ttu-id="a12e6-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a12e6-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a12e6-105">&nbsp;&nbsp;[**\<運行時>**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="a12e6-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="a12e6-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<應用域管理器類型>**</span><span class="sxs-lookup"><span data-stu-id="a12e6-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerType>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a12e6-107">語法</span><span class="sxs-lookup"><span data-stu-id="a12e6-107">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly
   value="type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a12e6-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a12e6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a12e6-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a12e6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a12e6-110">屬性</span><span class="sxs-lookup"><span data-stu-id="a12e6-110">Attributes</span></span>  
  
|<span data-ttu-id="a12e6-111">屬性</span><span class="sxs-lookup"><span data-stu-id="a12e6-111">Attribute</span></span>|<span data-ttu-id="a12e6-112">描述</span><span class="sxs-lookup"><span data-stu-id="a12e6-112">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="a12e6-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="a12e6-113">Required attribute.</span></span> <span data-ttu-id="a12e6-114">指定作為進程中預設應用程式域的應用程式域管理器的類型的名稱（包括命名空間）。</span><span class="sxs-lookup"><span data-stu-id="a12e6-114">Specifies the name of the type, including the namespace, that serves as the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a12e6-115">子元素</span><span class="sxs-lookup"><span data-stu-id="a12e6-115">Child Elements</span></span>  
 <span data-ttu-id="a12e6-116">無。</span><span class="sxs-lookup"><span data-stu-id="a12e6-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a12e6-117">父項目</span><span class="sxs-lookup"><span data-stu-id="a12e6-117">Parent Elements</span></span>  
  
|<span data-ttu-id="a12e6-118">元素</span><span class="sxs-lookup"><span data-stu-id="a12e6-118">Element</span></span>|<span data-ttu-id="a12e6-119">描述</span><span class="sxs-lookup"><span data-stu-id="a12e6-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a12e6-120">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="a12e6-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="a12e6-121">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="a12e6-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a12e6-122">備註</span><span class="sxs-lookup"><span data-stu-id="a12e6-122">Remarks</span></span>  
 <span data-ttu-id="a12e6-123">要指定應用程式域管理器的類型，必須同時指定此元素和[\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md)元素。</span><span class="sxs-lookup"><span data-stu-id="a12e6-123">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element.</span></span> <span data-ttu-id="a12e6-124">如果未指定其中任一元素，則忽略另一個元素。</span><span class="sxs-lookup"><span data-stu-id="a12e6-124">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="a12e6-125">載入預設應用程式域時，<xref:System.TypeLoadException>如果[\<應用域管理器元件>](appdomainmanagerassembly-element.md)元素指定的程式集中不存在指定的類型，則引發該類型;進程無法啟動。</span><span class="sxs-lookup"><span data-stu-id="a12e6-125">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified type does not exist in the assembly that is specified by the [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element; and the process fails to start.</span></span>  
  
 <span data-ttu-id="a12e6-126">當您為預設應用程式域指定應用程式域管理器類型時，從預設應用程式域創建的其他應用程式域將繼承應用程式域管理器類型。</span><span class="sxs-lookup"><span data-stu-id="a12e6-126">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="a12e6-127">使用<xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>和<xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>屬性為新的應用程式域指定不同的應用程式域管理器類型。</span><span class="sxs-lookup"><span data-stu-id="a12e6-127">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="a12e6-128">指定應用程式域管理器類型需要應用程式具有完全信任。</span><span class="sxs-lookup"><span data-stu-id="a12e6-128">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="a12e6-129">（例如，在桌面上運行的應用程式具有完全信任。如果應用程式沒有完全信任，則引發 。 <xref:System.TypeLoadException></span><span class="sxs-lookup"><span data-stu-id="a12e6-129">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="a12e6-130">類型和命名空間的格式與用於屬性的<xref:System.Type.FullName%2A?displayProperty=nameWithType>格式相同。</span><span class="sxs-lookup"><span data-stu-id="a12e6-130">The format of the type and namespace is the same format that is used for the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="a12e6-131">此配置元素僅在 .NET 框架 4 和更高版本中可用。</span><span class="sxs-lookup"><span data-stu-id="a12e6-131">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a12e6-132">範例</span><span class="sxs-lookup"><span data-stu-id="a12e6-132">Example</span></span>  
 <span data-ttu-id="a12e6-133">下面的示例演示如何指定進程預設應用程式域的應用程式域管理器是程式集中`MyMgr``AdMgrExample`的類型。</span><span class="sxs-lookup"><span data-stu-id="a12e6-133">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a12e6-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a12e6-134">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="a12e6-135">\<應用程式域管理器程式集>元素</span><span class="sxs-lookup"><span data-stu-id="a12e6-135">\<appDomainManagerAssembly> Element</span></span>](appdomainmanagerassembly-element.md)
- [<span data-ttu-id="a12e6-136">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="a12e6-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a12e6-137">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="a12e6-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="a12e6-138">SetAppDomainManagerType 方法</span><span class="sxs-lookup"><span data-stu-id="a12e6-138">SetAppDomainManagerType Method</span></span>](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
