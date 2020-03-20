---
title: <appDomainManagerAssembly> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
ms.openlocfilehash: 4c4ea35bff17a0e5188f26884e93cf77173a7df8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154418"
---
# <a name="appdomainmanagerassembly-element"></a><span data-ttu-id="8c5e1-102">\<應用程式域管理器程式集>元素</span><span class="sxs-lookup"><span data-stu-id="8c5e1-102">\<appDomainManagerAssembly> Element</span></span>
<span data-ttu-id="8c5e1-103">針對處理序中的預設應用程式網域，指定提供應用程式網域管理員的組件。</span><span class="sxs-lookup"><span data-stu-id="8c5e1-103">Specifies the assembly that provides the application domain manager for the default application domain in the process.</span></span>  
  
<span data-ttu-id="8c5e1-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8c5e1-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8c5e1-105">&nbsp;&nbsp;[**\<運行時>**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="8c5e1-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="8c5e1-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<應用程式域管理器組裝>**</span><span class="sxs-lookup"><span data-stu-id="8c5e1-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerAssembly>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c5e1-107">語法</span><span class="sxs-lookup"><span data-stu-id="8c5e1-107">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly
   value="assembly display name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8c5e1-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8c5e1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8c5e1-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="8c5e1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8c5e1-110">屬性</span><span class="sxs-lookup"><span data-stu-id="8c5e1-110">Attributes</span></span>  
  
|<span data-ttu-id="8c5e1-111">屬性</span><span class="sxs-lookup"><span data-stu-id="8c5e1-111">Attribute</span></span>|<span data-ttu-id="8c5e1-112">描述</span><span class="sxs-lookup"><span data-stu-id="8c5e1-112">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="8c5e1-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="8c5e1-113">Required attribute.</span></span> <span data-ttu-id="8c5e1-114">指定在此過程中為預設應用程式域提供應用程式域管理器的程式集的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="8c5e1-114">Specifies the display name of the assembly that provides the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8c5e1-115">子元素</span><span class="sxs-lookup"><span data-stu-id="8c5e1-115">Child Elements</span></span>  
 <span data-ttu-id="8c5e1-116">無。</span><span class="sxs-lookup"><span data-stu-id="8c5e1-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8c5e1-117">父項目</span><span class="sxs-lookup"><span data-stu-id="8c5e1-117">Parent Elements</span></span>  
  
|<span data-ttu-id="8c5e1-118">元素</span><span class="sxs-lookup"><span data-stu-id="8c5e1-118">Element</span></span>|<span data-ttu-id="8c5e1-119">描述</span><span class="sxs-lookup"><span data-stu-id="8c5e1-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8c5e1-120">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="8c5e1-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="8c5e1-121">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="8c5e1-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c5e1-122">備註</span><span class="sxs-lookup"><span data-stu-id="8c5e1-122">Remarks</span></span>  
 <span data-ttu-id="8c5e1-123">要指定應用程式域管理器的類型，必須同時指定此元素和[\<appDomainManagerType>](appdomainmanagertype-element.md)元素。</span><span class="sxs-lookup"><span data-stu-id="8c5e1-123">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerType>](appdomainmanagertype-element.md) element.</span></span> <span data-ttu-id="8c5e1-124">如果未指定其中任一元素，則忽略另一個元素。</span><span class="sxs-lookup"><span data-stu-id="8c5e1-124">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="8c5e1-125">載入預設應用程式域時，<xref:System.TypeLoadException>如果指定的程式集不存在，或者程式集不包含[\<appDomainManagerType 指定的類型>](appdomainmanagertype-element.md)元素，則引發該程式集;進程無法啟動。</span><span class="sxs-lookup"><span data-stu-id="8c5e1-125">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified assembly does not exist or if the assembly does not contain the type specified by the [\<appDomainManagerType>](appdomainmanagertype-element.md) element; and the process fails to start.</span></span> <span data-ttu-id="8c5e1-126">如果找到程式集但版本資訊不匹配，則引發 。 <xref:System.IO.FileLoadException></span><span class="sxs-lookup"><span data-stu-id="8c5e1-126">If the assembly is found but the version information does not match, a <xref:System.IO.FileLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="8c5e1-127">當您為預設應用程式域指定應用程式域管理器類型時，從預設應用程式域創建的其他應用程式域將繼承應用程式域管理器類型。</span><span class="sxs-lookup"><span data-stu-id="8c5e1-127">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="8c5e1-128">使用<xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>和<xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>屬性為新的應用程式域指定不同的應用程式域管理器類型。</span><span class="sxs-lookup"><span data-stu-id="8c5e1-128">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="8c5e1-129">指定應用程式域管理器類型需要應用程式具有完全信任。</span><span class="sxs-lookup"><span data-stu-id="8c5e1-129">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="8c5e1-130">（例如，在桌面上運行的應用程式具有完全信任。如果應用程式沒有完全信任，則引發 。 <xref:System.TypeLoadException></span><span class="sxs-lookup"><span data-stu-id="8c5e1-130">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="8c5e1-131">有關程式集顯示名稱的格式，請參閱 屬性<xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="8c5e1-131">For the format of the assembly display name, see the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="8c5e1-132">此配置元素僅在 .NET 框架 4 和更高版本中可用。</span><span class="sxs-lookup"><span data-stu-id="8c5e1-132">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c5e1-133">範例</span><span class="sxs-lookup"><span data-stu-id="8c5e1-133">Example</span></span>  
 <span data-ttu-id="8c5e1-134">下面的示例演示如何指定進程預設應用程式域的應用程式域管理器是程式集中`MyMgr``AdMgrExample`的類型。</span><span class="sxs-lookup"><span data-stu-id="8c5e1-134">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8c5e1-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c5e1-135">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="8c5e1-136">\<應用域管理器類型>元素</span><span class="sxs-lookup"><span data-stu-id="8c5e1-136">\<appDomainManagerType> Element</span></span>](appdomainmanagertype-element.md)
- [<span data-ttu-id="8c5e1-137">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="8c5e1-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="8c5e1-138">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="8c5e1-138">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="8c5e1-139">SetAppDomainManagerType 方法</span><span class="sxs-lookup"><span data-stu-id="8c5e1-139">SetAppDomainManagerType Method</span></span>](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
