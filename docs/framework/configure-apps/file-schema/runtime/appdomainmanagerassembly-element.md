---
title: <appDomainManagerAssembly> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
ms.openlocfilehash: 4c4ea35bff17a0e5188f26884e93cf77173a7df8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154418"
---
# <a name="appdomainmanagerassembly-element"></a><span data-ttu-id="f5469-102">\<appDomainManagerAssembly> 項目</span><span class="sxs-lookup"><span data-stu-id="f5469-102">\<appDomainManagerAssembly> Element</span></span>
<span data-ttu-id="f5469-103">針對處理序中的預設應用程式網域，指定提供應用程式網域管理員的組件。</span><span class="sxs-lookup"><span data-stu-id="f5469-103">Specifies the assembly that provides the application domain manager for the default application domain in the process.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerAssembly>**  
  
## <a name="syntax"></a><span data-ttu-id="f5469-104">語法</span><span class="sxs-lookup"><span data-stu-id="f5469-104">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly
   value="assembly display name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f5469-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f5469-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f5469-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f5469-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f5469-107">屬性</span><span class="sxs-lookup"><span data-stu-id="f5469-107">Attributes</span></span>  
  
|<span data-ttu-id="f5469-108">屬性</span><span class="sxs-lookup"><span data-stu-id="f5469-108">Attribute</span></span>|<span data-ttu-id="f5469-109">描述</span><span class="sxs-lookup"><span data-stu-id="f5469-109">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="f5469-110">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="f5469-110">Required attribute.</span></span> <span data-ttu-id="f5469-111">針對進程中的預設應用程式域，指定提供應用程式域管理員之元件的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="f5469-111">Specifies the display name of the assembly that provides the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f5469-112">子元素</span><span class="sxs-lookup"><span data-stu-id="f5469-112">Child Elements</span></span>  
 <span data-ttu-id="f5469-113">無。</span><span class="sxs-lookup"><span data-stu-id="f5469-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f5469-114">父項目</span><span class="sxs-lookup"><span data-stu-id="f5469-114">Parent Elements</span></span>  
  
|<span data-ttu-id="f5469-115">元素</span><span class="sxs-lookup"><span data-stu-id="f5469-115">Element</span></span>|<span data-ttu-id="f5469-116">描述</span><span class="sxs-lookup"><span data-stu-id="f5469-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f5469-117">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="f5469-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="f5469-118">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="f5469-118">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5469-119">備註</span><span class="sxs-lookup"><span data-stu-id="f5469-119">Remarks</span></span>  
 <span data-ttu-id="f5469-120">若要指定應用程式域管理員的類型，您必須同時指定這個元素和專案 [\<appDomainManagerType>](appdomainmanagertype-element.md) 。</span><span class="sxs-lookup"><span data-stu-id="f5469-120">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerType>](appdomainmanagertype-element.md) element.</span></span> <span data-ttu-id="f5469-121">如果未指定任何一個專案，則會忽略另一個元素。</span><span class="sxs-lookup"><span data-stu-id="f5469-121">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="f5469-122">載入預設應用程式域時， <xref:System.TypeLoadException> 如果指定的元件不存在，或是元件不包含專案所指定的類型，就會擲回， [\<appDomainManagerType>](appdomainmanagertype-element.md) 而且進程無法啟動。</span><span class="sxs-lookup"><span data-stu-id="f5469-122">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified assembly does not exist or if the assembly does not contain the type specified by the [\<appDomainManagerType>](appdomainmanagertype-element.md) element; and the process fails to start.</span></span> <span data-ttu-id="f5469-123">如果找到元件，但版本資訊不相符，則會擲回 <xref:System.IO.FileLoadException> 。</span><span class="sxs-lookup"><span data-stu-id="f5469-123">If the assembly is found but the version information does not match, a <xref:System.IO.FileLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="f5469-124">當您針對預設應用程式域指定應用程式域管理員類型時，從預設應用程式域建立的其他應用程式域會繼承應用程式域管理員類型。</span><span class="sxs-lookup"><span data-stu-id="f5469-124">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="f5469-125">使用 <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> 和 <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> 屬性，為新的應用程式域指定不同的應用程式域管理員類型。</span><span class="sxs-lookup"><span data-stu-id="f5469-125">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="f5469-126">指定應用程式域管理員類型時，應用程式必須具有完全信任。</span><span class="sxs-lookup"><span data-stu-id="f5469-126">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="f5469-127">（例如，在桌面上執行的應用程式會有完全信任）。如果應用程式沒有完全信任， <xref:System.TypeLoadException> 則會擲回。</span><span class="sxs-lookup"><span data-stu-id="f5469-127">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="f5469-128">如需元件顯示名稱的格式，請參閱 <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="f5469-128">For the format of the assembly display name, see the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="f5469-129">此 configuration 元素僅適用于 .NET Framework 4 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="f5469-129">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5469-130">範例</span><span class="sxs-lookup"><span data-stu-id="f5469-130">Example</span></span>  
 <span data-ttu-id="f5469-131">下列範例示範如何指定進程的預設應用程式域的應用程式域管理員是 `MyMgr` 元件中的類型 `AdMgrExample` 。</span><span class="sxs-lookup"><span data-stu-id="f5469-131">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f5469-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5469-132">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="f5469-133">\<appDomainManagerType>元素</span><span class="sxs-lookup"><span data-stu-id="f5469-133">\<appDomainManagerType> Element</span></span>](appdomainmanagertype-element.md)
- [<span data-ttu-id="f5469-134">執行時間設定架構</span><span class="sxs-lookup"><span data-stu-id="f5469-134">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="f5469-135">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="f5469-135">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="f5469-136">SetAppDomainManagerType 方法</span><span class="sxs-lookup"><span data-stu-id="f5469-136">SetAppDomainManagerType Method</span></span>](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
