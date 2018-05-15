---
title: '&lt;appDomainManagerType&gt;項目'
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8fb771d58a99e42ad53a465008e8848cff0a87fd
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltappdomainmanagertypegt-element"></a><span data-ttu-id="47da1-102">&lt;appDomainManagerType&gt;項目</span><span class="sxs-lookup"><span data-stu-id="47da1-102">&lt;appDomainManagerType&gt; Element</span></span>
<span data-ttu-id="47da1-103">針對預設應用程式網域，指定做為應用程式網域管理員的類型。</span><span class="sxs-lookup"><span data-stu-id="47da1-103">Specifies the type that serves as the application domain manager for the default application domain.</span></span>  
  
 <span data-ttu-id="47da1-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="47da1-104">\<configuration></span></span>  
<span data-ttu-id="47da1-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="47da1-105">\<runtime></span></span>  
<span data-ttu-id="47da1-106">\<appDomainManagerType ></span><span class="sxs-lookup"><span data-stu-id="47da1-106">\<appDomainManagerType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47da1-107">語法</span><span class="sxs-lookup"><span data-stu-id="47da1-107">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly   
   value="type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="47da1-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="47da1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="47da1-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="47da1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="47da1-110">屬性</span><span class="sxs-lookup"><span data-stu-id="47da1-110">Attributes</span></span>  
  
|<span data-ttu-id="47da1-111">屬性</span><span class="sxs-lookup"><span data-stu-id="47da1-111">Attribute</span></span>|<span data-ttu-id="47da1-112">描述</span><span class="sxs-lookup"><span data-stu-id="47da1-112">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="47da1-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="47da1-113">Required attribute.</span></span> <span data-ttu-id="47da1-114">指定類型，包括命名空間，做為預設應用程式定義域中的程序的應用程式定義域管理員的名稱。</span><span class="sxs-lookup"><span data-stu-id="47da1-114">Specifies the name of the type, including the namespace, that serves as the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="47da1-115">子項目</span><span class="sxs-lookup"><span data-stu-id="47da1-115">Child Elements</span></span>  
 <span data-ttu-id="47da1-116">無。</span><span class="sxs-lookup"><span data-stu-id="47da1-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="47da1-117">父項目</span><span class="sxs-lookup"><span data-stu-id="47da1-117">Parent Elements</span></span>  
  
|<span data-ttu-id="47da1-118">項目</span><span class="sxs-lookup"><span data-stu-id="47da1-118">Element</span></span>|<span data-ttu-id="47da1-119">描述</span><span class="sxs-lookup"><span data-stu-id="47da1-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="47da1-120">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="47da1-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="47da1-121">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="47da1-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47da1-122">備註</span><span class="sxs-lookup"><span data-stu-id="47da1-122">Remarks</span></span>  
 <span data-ttu-id="47da1-123">若要指定應用程式定義域管理員類型，您必須指定這個項目和[ \<appDomainManagerAssembly >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md)項目。</span><span class="sxs-lookup"><span data-stu-id="47da1-123">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md) element.</span></span> <span data-ttu-id="47da1-124">如果未指定這些項目，則會忽略其他。</span><span class="sxs-lookup"><span data-stu-id="47da1-124">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="47da1-125">載入預設應用程式定義域時，<xref:System.TypeLoadException>如果所指定的組件中沒有指定的型別會擲回[ \<appDomainManagerAssembly >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md)項目; 和處理程序無法啟動。</span><span class="sxs-lookup"><span data-stu-id="47da1-125">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified type does not exist in the assembly that is specified by the [\<appDomainManagerAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md) element; and the process fails to start.</span></span>  
  
 <span data-ttu-id="47da1-126">當您指定的應用程式網域管理員類型的預設應用程式定義域時，從預設應用程式定義域建立其他應用程式定義域繼承應用程式定義域管理員類型。</span><span class="sxs-lookup"><span data-stu-id="47da1-126">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="47da1-127">使用<xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>和<xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>屬性，以指定新的應用程式定義域的不同的應用程式定義域管理員類型。</span><span class="sxs-lookup"><span data-stu-id="47da1-127">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="47da1-128">指定應用程式定義域管理員類型需要有完全信任應用程式。</span><span class="sxs-lookup"><span data-stu-id="47da1-128">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="47da1-129">（例如，在桌面上執行的應用程式有完全信任）。如果應用程式並沒有完全信任，<xref:System.TypeLoadException>就會擲回。</span><span class="sxs-lookup"><span data-stu-id="47da1-129">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="47da1-130">型別和命名空間的格式是相同的格式用於<xref:System.Type.FullName%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="47da1-130">The format of the type and namespace is the same format that is used for the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="47da1-131">這個組態項目是僅適用於[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]和更新版本。</span><span class="sxs-lookup"><span data-stu-id="47da1-131">This configuration element is available only in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47da1-132">範例</span><span class="sxs-lookup"><span data-stu-id="47da1-132">Example</span></span>  
 <span data-ttu-id="47da1-133">下列範例示範如何指定預設應用程式定義域的程序的應用程式定義域管理員為`MyMgr`輸入`AdMgrExample`組件。</span><span class="sxs-lookup"><span data-stu-id="47da1-133">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly   
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="47da1-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47da1-134">See Also</span></span>  
 <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>  
 <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="47da1-135">\<appDomainManagerAssembly > 項目</span><span class="sxs-lookup"><span data-stu-id="47da1-135">\<appDomainManagerAssembly> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md)  
 [<span data-ttu-id="47da1-136">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="47da1-136">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="47da1-137">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="47da1-137">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="47da1-138">SetAppDomainManagerType 方法</span><span class="sxs-lookup"><span data-stu-id="47da1-138">SetAppDomainManagerType Method</span></span>](../../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
