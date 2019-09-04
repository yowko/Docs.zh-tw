---
title: <appDomainManagerAssembly> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 083e3ba21dcd196eacfe3d9fd649c211da9dc125
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252842"
---
# <a name="appdomainmanagerassembly-element"></a><span data-ttu-id="5a147-102">\<appDomainManagerAssembly > 元素</span><span class="sxs-lookup"><span data-stu-id="5a147-102">\<appDomainManagerAssembly> Element</span></span>
<span data-ttu-id="5a147-103">針對處理序中的預設應用程式網域，指定提供應用程式網域管理員的組件。</span><span class="sxs-lookup"><span data-stu-id="5a147-103">Specifies the assembly that provides the application domain manager for the default application domain in the process.</span></span>  
  
<span data-ttu-id="5a147-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5a147-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5a147-105">&nbsp;&nbsp;[ **\<執行時間 >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="5a147-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="5a147-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<appDomainManagerAssembly>**</span><span class="sxs-lookup"><span data-stu-id="5a147-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerAssembly>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a147-107">語法</span><span class="sxs-lookup"><span data-stu-id="5a147-107">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly   
   value="assembly display name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a147-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5a147-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5a147-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="5a147-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a147-110">屬性</span><span class="sxs-lookup"><span data-stu-id="5a147-110">Attributes</span></span>  
  
|<span data-ttu-id="5a147-111">屬性</span><span class="sxs-lookup"><span data-stu-id="5a147-111">Attribute</span></span>|<span data-ttu-id="5a147-112">說明</span><span class="sxs-lookup"><span data-stu-id="5a147-112">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="5a147-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="5a147-113">Required attribute.</span></span> <span data-ttu-id="5a147-114">針對進程中的預設應用程式域, 指定提供應用程式域管理員之元件的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="5a147-114">Specifies the display name of the assembly that provides the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5a147-115">子元素</span><span class="sxs-lookup"><span data-stu-id="5a147-115">Child Elements</span></span>  
 <span data-ttu-id="5a147-116">無。</span><span class="sxs-lookup"><span data-stu-id="5a147-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5a147-117">父項目</span><span class="sxs-lookup"><span data-stu-id="5a147-117">Parent Elements</span></span>  
  
|<span data-ttu-id="5a147-118">項目</span><span class="sxs-lookup"><span data-stu-id="5a147-118">Element</span></span>|<span data-ttu-id="5a147-119">描述</span><span class="sxs-lookup"><span data-stu-id="5a147-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5a147-120">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="5a147-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="5a147-121">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="5a147-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a147-122">備註</span><span class="sxs-lookup"><span data-stu-id="5a147-122">Remarks</span></span>  
 <span data-ttu-id="5a147-123">若要指定應用程式域管理員的類型, 您必須同時指定此元素和[ \<appDomainManagerType >](appdomainmanagertype-element.md)元素。</span><span class="sxs-lookup"><span data-stu-id="5a147-123">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerType>](appdomainmanagertype-element.md) element.</span></span> <span data-ttu-id="5a147-124">如果未指定任何一個專案, 則會忽略另一個元素。</span><span class="sxs-lookup"><span data-stu-id="5a147-124">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="5a147-125">載入預設的應用程式域時, <xref:System.TypeLoadException>如果指定的元件不存在, 或是元件不包含[ \<appDomainManagerType >](appdomainmanagertype-element.md)專案所指定的類型, 則會擲回, 而且進程無法「.</span><span class="sxs-lookup"><span data-stu-id="5a147-125">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified assembly does not exist or if the assembly does not contain the type specified by the [\<appDomainManagerType>](appdomainmanagertype-element.md) element; and the process fails to start.</span></span> <span data-ttu-id="5a147-126">如果找到元件, 但版本資訊不相符, <xref:System.IO.FileLoadException>則會擲回。</span><span class="sxs-lookup"><span data-stu-id="5a147-126">If the assembly is found but the version information does not match, a <xref:System.IO.FileLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="5a147-127">當您針對預設應用程式域指定應用程式域管理員類型時, 從預設應用程式域建立的其他應用程式域會繼承應用程式域管理員類型。</span><span class="sxs-lookup"><span data-stu-id="5a147-127">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="5a147-128"><xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>使用和<xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>屬性, 為新的應用程式域指定不同的應用程式域管理員類型。</span><span class="sxs-lookup"><span data-stu-id="5a147-128">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="5a147-129">指定應用程式域管理員類型時, 應用程式必須具有完全信任。</span><span class="sxs-lookup"><span data-stu-id="5a147-129">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="5a147-130">(例如, 在桌面上執行的應用程式會有完全信任)。如果應用程式沒有完全信任, <xref:System.TypeLoadException>則會擲回。</span><span class="sxs-lookup"><span data-stu-id="5a147-130">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="5a147-131">如需元件顯示名稱的格式, 請參閱<xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="5a147-131">For the format of the assembly display name, see the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="5a147-132">此 configuration 元素僅適用于 .NET Framework 4 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="5a147-132">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a147-133">範例</span><span class="sxs-lookup"><span data-stu-id="5a147-133">Example</span></span>  
 <span data-ttu-id="5a147-134">下列範例示範如何指定進程的預設應用程式域的應用程式域管理員是`MyMgr` `AdMgrExample`元件中的類型。</span><span class="sxs-lookup"><span data-stu-id="5a147-134">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly   
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5a147-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a147-135">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="5a147-136">\<appDomainManagerType > 元素</span><span class="sxs-lookup"><span data-stu-id="5a147-136">\<appDomainManagerType> Element</span></span>](appdomainmanagertype-element.md)
- [<span data-ttu-id="5a147-137">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="5a147-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="5a147-138">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="5a147-138">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="5a147-139">SetAppDomainManagerType 方法</span><span class="sxs-lookup"><span data-stu-id="5a147-139">SetAppDomainManagerType Method</span></span>](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
