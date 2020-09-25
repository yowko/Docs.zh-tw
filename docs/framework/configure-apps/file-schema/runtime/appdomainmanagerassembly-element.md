---
title: <appDomainManagerAssembly> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
ms.openlocfilehash: 1716b11106775bed2c0d6ccb62e8d5b032b6e8be
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176132"
---
# <a name="appdomainmanagerassembly-element"></a><span data-ttu-id="aaf70-102">\<appDomainManagerAssembly> 項目</span><span class="sxs-lookup"><span data-stu-id="aaf70-102">\<appDomainManagerAssembly> Element</span></span>

<span data-ttu-id="aaf70-103">針對處理序中的預設應用程式網域，指定提供應用程式網域管理員的組件。</span><span class="sxs-lookup"><span data-stu-id="aaf70-103">Specifies the assembly that provides the application domain manager for the default application domain in the process.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerAssembly>**  
  
## <a name="syntax"></a><span data-ttu-id="aaf70-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="aaf70-104">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly
   value="assembly display name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aaf70-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="aaf70-105">Attributes and Elements</span></span>  

 <span data-ttu-id="aaf70-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="aaf70-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aaf70-107">屬性</span><span class="sxs-lookup"><span data-stu-id="aaf70-107">Attributes</span></span>  
  
|<span data-ttu-id="aaf70-108">屬性</span><span class="sxs-lookup"><span data-stu-id="aaf70-108">Attribute</span></span>|<span data-ttu-id="aaf70-109">描述</span><span class="sxs-lookup"><span data-stu-id="aaf70-109">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="aaf70-110">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="aaf70-110">Required attribute.</span></span> <span data-ttu-id="aaf70-111">指定元件的顯示名稱，這個元件會提供進程中預設應用程式域的應用程式域管理員。</span><span class="sxs-lookup"><span data-stu-id="aaf70-111">Specifies the display name of the assembly that provides the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aaf70-112">子元素</span><span class="sxs-lookup"><span data-stu-id="aaf70-112">Child Elements</span></span>  

 <span data-ttu-id="aaf70-113">無。</span><span class="sxs-lookup"><span data-stu-id="aaf70-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aaf70-114">父項目</span><span class="sxs-lookup"><span data-stu-id="aaf70-114">Parent Elements</span></span>  
  
|<span data-ttu-id="aaf70-115">項目</span><span class="sxs-lookup"><span data-stu-id="aaf70-115">Element</span></span>|<span data-ttu-id="aaf70-116">描述</span><span class="sxs-lookup"><span data-stu-id="aaf70-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="aaf70-117">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="aaf70-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="aaf70-118">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="aaf70-118">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aaf70-119">備註</span><span class="sxs-lookup"><span data-stu-id="aaf70-119">Remarks</span></span>  

 <span data-ttu-id="aaf70-120">若要指定應用程式域管理員的類型，您必須同時指定這個元素和 [\<appDomainManagerType>](appdomainmanagertype-element.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="aaf70-120">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerType>](appdomainmanagertype-element.md) element.</span></span> <span data-ttu-id="aaf70-121">如果未指定任何一個專案，則會忽略另一個元素。</span><span class="sxs-lookup"><span data-stu-id="aaf70-121">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="aaf70-122">當載入預設應用程式域時， <xref:System.TypeLoadException> 如果指定的元件不存在或元件不包含元素所指定的型別，則會擲回， [\<appDomainManagerType>](appdomainmanagertype-element.md) 且進程無法啟動。</span><span class="sxs-lookup"><span data-stu-id="aaf70-122">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified assembly does not exist or if the assembly does not contain the type specified by the [\<appDomainManagerType>](appdomainmanagertype-element.md) element; and the process fails to start.</span></span> <span data-ttu-id="aaf70-123">如果找到元件，但版本資訊不相符，就會擲回 <xref:System.IO.FileLoadException> 。</span><span class="sxs-lookup"><span data-stu-id="aaf70-123">If the assembly is found but the version information does not match, a <xref:System.IO.FileLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="aaf70-124">當您針對預設應用程式域指定應用程式域管理員類型時，從預設應用程式域建立的其他應用程式域會繼承應用程式域管理員類型。</span><span class="sxs-lookup"><span data-stu-id="aaf70-124">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="aaf70-125">使用 <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> 和 <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> 屬性為新的應用程式域指定不同的應用程式域管理員類型。</span><span class="sxs-lookup"><span data-stu-id="aaf70-125">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="aaf70-126">指定應用程式域管理員類型需要應用程式具有完全信任。</span><span class="sxs-lookup"><span data-stu-id="aaf70-126">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="aaf70-127"> (例如，在桌上型電腦上執行的應用程式具有完全信任。 ) 如果應用程式沒有完全信任， <xref:System.TypeLoadException> 則會擲回。</span><span class="sxs-lookup"><span data-stu-id="aaf70-127">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="aaf70-128">如需元件顯示名稱的格式，請參閱 <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="aaf70-128">For the format of the assembly display name, see the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="aaf70-129">只有 .NET Framework 4 和更新版本才提供此設定元素。</span><span class="sxs-lookup"><span data-stu-id="aaf70-129">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aaf70-130">範例</span><span class="sxs-lookup"><span data-stu-id="aaf70-130">Example</span></span>  

 <span data-ttu-id="aaf70-131">下列範例示範如何指定進程之預設應用程式域的應用程式域管理員是 `MyMgr` 元件中的型別 `AdMgrExample` 。</span><span class="sxs-lookup"><span data-stu-id="aaf70-131">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="aaf70-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aaf70-132">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="aaf70-133">\<appDomainManagerType> 元素</span><span class="sxs-lookup"><span data-stu-id="aaf70-133">\<appDomainManagerType> Element</span></span>](appdomainmanagertype-element.md)
- [<span data-ttu-id="aaf70-134">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="aaf70-134">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="aaf70-135">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="aaf70-135">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="aaf70-136">SetAppDomainManagerType 方法</span><span class="sxs-lookup"><span data-stu-id="aaf70-136">SetAppDomainManagerType Method</span></span>](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
