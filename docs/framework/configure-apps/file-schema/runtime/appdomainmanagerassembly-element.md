---
title: <appDomainManagerAssembly> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4fe1dfbd62a6967ae51031fa12f80e9c5563dc44
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182347"
---
# <a name="appdomainmanagerassembly-element"></a><span data-ttu-id="1d077-102">\<appDomainManagerAssembly > 項目</span><span class="sxs-lookup"><span data-stu-id="1d077-102">\<appDomainManagerAssembly> Element</span></span>
<span data-ttu-id="1d077-103">針對處理序中的預設應用程式網域，指定提供應用程式網域管理員的組件。</span><span class="sxs-lookup"><span data-stu-id="1d077-103">Specifies the assembly that provides the application domain manager for the default application domain in the process.</span></span>  
  
 <span data-ttu-id="1d077-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="1d077-104">\<configuration></span></span>  
<span data-ttu-id="1d077-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="1d077-105">\<runtime></span></span>  
<span data-ttu-id="1d077-106">\<appDomainManagerAssembly></span><span class="sxs-lookup"><span data-stu-id="1d077-106">\<appDomainManagerAssembly></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d077-107">語法</span><span class="sxs-lookup"><span data-stu-id="1d077-107">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly   
   value="assembly display name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d077-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1d077-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1d077-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="1d077-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d077-110">屬性</span><span class="sxs-lookup"><span data-stu-id="1d077-110">Attributes</span></span>  
  
|<span data-ttu-id="1d077-111">屬性</span><span class="sxs-lookup"><span data-stu-id="1d077-111">Attribute</span></span>|<span data-ttu-id="1d077-112">描述</span><span class="sxs-lookup"><span data-stu-id="1d077-112">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="1d077-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="1d077-113">Required attribute.</span></span> <span data-ttu-id="1d077-114">指定提供應用程式定義域管理員程序中的預設應用程式定義域的組件的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="1d077-114">Specifies the display name of the assembly that provides the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1d077-115">子元素</span><span class="sxs-lookup"><span data-stu-id="1d077-115">Child Elements</span></span>  
 <span data-ttu-id="1d077-116">無。</span><span class="sxs-lookup"><span data-stu-id="1d077-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1d077-117">父項目</span><span class="sxs-lookup"><span data-stu-id="1d077-117">Parent Elements</span></span>  
  
|<span data-ttu-id="1d077-118">項目</span><span class="sxs-lookup"><span data-stu-id="1d077-118">Element</span></span>|<span data-ttu-id="1d077-119">描述</span><span class="sxs-lookup"><span data-stu-id="1d077-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1d077-120">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="1d077-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="1d077-121">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="1d077-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d077-122">備註</span><span class="sxs-lookup"><span data-stu-id="1d077-122">Remarks</span></span>  
 <span data-ttu-id="1d077-123">若要指定的應用程式定義域管理員類型，您必須指定這個項目和[ \<appDomainManagerType >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)項目。</span><span class="sxs-lookup"><span data-stu-id="1d077-123">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerType>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md) element.</span></span> <span data-ttu-id="1d077-124">如果未指定這些項目，則會忽略其他。</span><span class="sxs-lookup"><span data-stu-id="1d077-124">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="1d077-125">載入預設應用程式定義域時，<xref:System.TypeLoadException>如果指定的組件不存在，或者組件不包含所指定的型別，會擲回[ \<appDomainManagerType >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)項目; 和此程序無法啟動。</span><span class="sxs-lookup"><span data-stu-id="1d077-125">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified assembly does not exist or if the assembly does not contain the type specified by the [\<appDomainManagerType>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md) element; and the process fails to start.</span></span> <span data-ttu-id="1d077-126">如果找到組件，但不是符合的版本資訊，<xref:System.IO.FileLoadException>就會擲回。</span><span class="sxs-lookup"><span data-stu-id="1d077-126">If the assembly is found but the version information does not match, a <xref:System.IO.FileLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="1d077-127">當您指定預設應用程式定義域的應用程式定義域管理員類型時，從預設應用程式定義域建立其他應用程式定義域繼承應用程式定義域管理員類型。</span><span class="sxs-lookup"><span data-stu-id="1d077-127">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="1d077-128">使用<xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>和<xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>屬性來指定新的應用程式定義域的不同的應用程式定義域管理員類型。</span><span class="sxs-lookup"><span data-stu-id="1d077-128">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="1d077-129">指定應用程式定義域管理員類型需要有完全信任應用程式。</span><span class="sxs-lookup"><span data-stu-id="1d077-129">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="1d077-130">（例如，在桌面上執行的應用程式有完全信任）。如果應用程式並沒有完全信任，<xref:System.TypeLoadException>就會擲回。</span><span class="sxs-lookup"><span data-stu-id="1d077-130">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="1d077-131">如需組件的顯示名稱的格式，請參閱<xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="1d077-131">For the format of the assembly display name, see the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="1d077-132">這個組態項目是僅適用於[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]和更新版本。</span><span class="sxs-lookup"><span data-stu-id="1d077-132">This configuration element is available only in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d077-133">範例</span><span class="sxs-lookup"><span data-stu-id="1d077-133">Example</span></span>  
 <span data-ttu-id="1d077-134">下列範例示範如何指定應用程式定義域管理員，預設應用程式定義域的處理程序會`MyMgr`輸入`AdMgrExample`組件。</span><span class="sxs-lookup"><span data-stu-id="1d077-134">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly   
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1d077-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d077-135">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="1d077-136">\<appDomainManagerType > 項目</span><span class="sxs-lookup"><span data-stu-id="1d077-136">\<appDomainManagerType> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)
- [<span data-ttu-id="1d077-137">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="1d077-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="1d077-138">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="1d077-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="1d077-139">SetAppDomainManagerType 方法</span><span class="sxs-lookup"><span data-stu-id="1d077-139">SetAppDomainManagerType Method</span></span>](../../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
