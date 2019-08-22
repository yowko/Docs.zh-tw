---
title: <appDomainManagerType> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b535ba67ab05dabd7e0a23e79692bbf69e25b55
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663914"
---
# <a name="appdomainmanagertype-element"></a><span data-ttu-id="74cf4-102">\<appDomainManagerType > 元素</span><span class="sxs-lookup"><span data-stu-id="74cf4-102">\<appDomainManagerType> Element</span></span>
<span data-ttu-id="74cf4-103">針對預設應用程式網域，指定做為應用程式網域管理員的類型。</span><span class="sxs-lookup"><span data-stu-id="74cf4-103">Specifies the type that serves as the application domain manager for the default application domain.</span></span>  
  
 <span data-ttu-id="74cf4-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="74cf4-104">\<configuration></span></span>  
<span data-ttu-id="74cf4-105">\<執行時間 ></span><span class="sxs-lookup"><span data-stu-id="74cf4-105">\<runtime></span></span>  
<span data-ttu-id="74cf4-106">\<appDomainManagerType></span><span class="sxs-lookup"><span data-stu-id="74cf4-106">\<appDomainManagerType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74cf4-107">語法</span><span class="sxs-lookup"><span data-stu-id="74cf4-107">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly   
   value="type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="74cf4-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="74cf4-108">Attributes and Elements</span></span>  
 <span data-ttu-id="74cf4-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="74cf4-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="74cf4-110">屬性</span><span class="sxs-lookup"><span data-stu-id="74cf4-110">Attributes</span></span>  
  
|<span data-ttu-id="74cf4-111">屬性</span><span class="sxs-lookup"><span data-stu-id="74cf4-111">Attribute</span></span>|<span data-ttu-id="74cf4-112">說明</span><span class="sxs-lookup"><span data-stu-id="74cf4-112">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="74cf4-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="74cf4-113">Required attribute.</span></span> <span data-ttu-id="74cf4-114">指定類型的名稱, 包括命名空間, 做為進程中預設應用程式域的應用程式域管理員。</span><span class="sxs-lookup"><span data-stu-id="74cf4-114">Specifies the name of the type, including the namespace, that serves as the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="74cf4-115">子元素</span><span class="sxs-lookup"><span data-stu-id="74cf4-115">Child Elements</span></span>  
 <span data-ttu-id="74cf4-116">無。</span><span class="sxs-lookup"><span data-stu-id="74cf4-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="74cf4-117">父項目</span><span class="sxs-lookup"><span data-stu-id="74cf4-117">Parent Elements</span></span>  
  
|<span data-ttu-id="74cf4-118">項目</span><span class="sxs-lookup"><span data-stu-id="74cf4-118">Element</span></span>|<span data-ttu-id="74cf4-119">說明</span><span class="sxs-lookup"><span data-stu-id="74cf4-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="74cf4-120">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="74cf4-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="74cf4-121">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="74cf4-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74cf4-122">備註</span><span class="sxs-lookup"><span data-stu-id="74cf4-122">Remarks</span></span>  
 <span data-ttu-id="74cf4-123">若要指定應用程式域管理員的類型, 您必須同時指定此元素和[ \<appDomainManagerAssembly >](appdomainmanagerassembly-element.md)元素。</span><span class="sxs-lookup"><span data-stu-id="74cf4-123">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element.</span></span> <span data-ttu-id="74cf4-124">如果未指定任何一個專案, 則會忽略另一個元素。</span><span class="sxs-lookup"><span data-stu-id="74cf4-124">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="74cf4-125">載入預設應用程式域時, 如果<xref:System.TypeLoadException>指定的型別不存在於[ \<appDomainManagerAssembly >](appdomainmanagerassembly-element.md)專案所指定的元件中, 就會擲回, 而且進程無法啟動。</span><span class="sxs-lookup"><span data-stu-id="74cf4-125">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified type does not exist in the assembly that is specified by the [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element; and the process fails to start.</span></span>  
  
 <span data-ttu-id="74cf4-126">當您針對預設應用程式域指定應用程式域管理員類型時, 從預設應用程式域建立的其他應用程式域會繼承應用程式域管理員類型。</span><span class="sxs-lookup"><span data-stu-id="74cf4-126">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="74cf4-127"><xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>使用和<xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>屬性, 為新的應用程式域指定不同的應用程式域管理員類型。</span><span class="sxs-lookup"><span data-stu-id="74cf4-127">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="74cf4-128">指定應用程式域管理員類型時, 應用程式必須具有完全信任。</span><span class="sxs-lookup"><span data-stu-id="74cf4-128">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="74cf4-129">(例如, 在桌面上執行的應用程式會有完全信任)。如果應用程式沒有完全信任, <xref:System.TypeLoadException>則會擲回。</span><span class="sxs-lookup"><span data-stu-id="74cf4-129">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="74cf4-130">類型和命名空間的格式與用於<xref:System.Type.FullName%2A?displayProperty=nameWithType>屬性的格式相同。</span><span class="sxs-lookup"><span data-stu-id="74cf4-130">The format of the type and namespace is the same format that is used for the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="74cf4-131">此 configuration 元素僅適用于 .NET Framework 4 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="74cf4-131">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74cf4-132">範例</span><span class="sxs-lookup"><span data-stu-id="74cf4-132">Example</span></span>  
 <span data-ttu-id="74cf4-133">下列範例示範如何指定進程的預設應用程式域的應用程式域管理員是`MyMgr` `AdMgrExample`元件中的類型。</span><span class="sxs-lookup"><span data-stu-id="74cf4-133">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly   
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="74cf4-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74cf4-134">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="74cf4-135">\<appDomainManagerAssembly > 元素</span><span class="sxs-lookup"><span data-stu-id="74cf4-135">\<appDomainManagerAssembly> Element</span></span>](appdomainmanagerassembly-element.md)
- [<span data-ttu-id="74cf4-136">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="74cf4-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="74cf4-137">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="74cf4-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="74cf4-138">SetAppDomainManagerType 方法</span><span class="sxs-lookup"><span data-stu-id="74cf4-138">SetAppDomainManagerType Method</span></span>](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
