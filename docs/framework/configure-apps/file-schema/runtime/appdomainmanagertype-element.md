---
title: <appDomainManagerType> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
ms.openlocfilehash: 8eb6129b3fafaeb81a94d5a4078e41a16583a226
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154419"
---
# <a name="appdomainmanagertype-element"></a><span data-ttu-id="d03a5-102">\<appDomainManagerType> 項目</span><span class="sxs-lookup"><span data-stu-id="d03a5-102">\<appDomainManagerType> Element</span></span>
<span data-ttu-id="d03a5-103">針對預設應用程式網域，指定做為應用程式網域管理員的類型。</span><span class="sxs-lookup"><span data-stu-id="d03a5-103">Specifies the type that serves as the application domain manager for the default application domain.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerType>**  
  
## <a name="syntax"></a><span data-ttu-id="d03a5-104">語法</span><span class="sxs-lookup"><span data-stu-id="d03a5-104">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly
   value="type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d03a5-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d03a5-105">Attributes and Elements</span></span>  
 <span data-ttu-id="d03a5-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d03a5-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d03a5-107">屬性</span><span class="sxs-lookup"><span data-stu-id="d03a5-107">Attributes</span></span>  
  
|<span data-ttu-id="d03a5-108">屬性</span><span class="sxs-lookup"><span data-stu-id="d03a5-108">Attribute</span></span>|<span data-ttu-id="d03a5-109">描述</span><span class="sxs-lookup"><span data-stu-id="d03a5-109">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="d03a5-110">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="d03a5-110">Required attribute.</span></span> <span data-ttu-id="d03a5-111">指定類型的名稱，包括命名空間，做為進程中預設應用程式域的應用程式域管理員。</span><span class="sxs-lookup"><span data-stu-id="d03a5-111">Specifies the name of the type, including the namespace, that serves as the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d03a5-112">子元素</span><span class="sxs-lookup"><span data-stu-id="d03a5-112">Child Elements</span></span>  
 <span data-ttu-id="d03a5-113">無。</span><span class="sxs-lookup"><span data-stu-id="d03a5-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d03a5-114">父項目</span><span class="sxs-lookup"><span data-stu-id="d03a5-114">Parent Elements</span></span>  
  
|<span data-ttu-id="d03a5-115">元素</span><span class="sxs-lookup"><span data-stu-id="d03a5-115">Element</span></span>|<span data-ttu-id="d03a5-116">描述</span><span class="sxs-lookup"><span data-stu-id="d03a5-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d03a5-117">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="d03a5-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d03a5-118">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="d03a5-118">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d03a5-119">備註</span><span class="sxs-lookup"><span data-stu-id="d03a5-119">Remarks</span></span>  
 <span data-ttu-id="d03a5-120">若要指定應用程式域管理員的類型，您必須同時指定這個元素和專案 [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) 。</span><span class="sxs-lookup"><span data-stu-id="d03a5-120">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element.</span></span> <span data-ttu-id="d03a5-121">如果未指定任何一個專案，則會忽略另一個元素。</span><span class="sxs-lookup"><span data-stu-id="d03a5-121">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="d03a5-122">載入預設應用程式域時， <xref:System.TypeLoadException> 如果指定的型別不存在於元素所指定的元件中，就會擲回， [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) 而且進程無法啟動。</span><span class="sxs-lookup"><span data-stu-id="d03a5-122">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified type does not exist in the assembly that is specified by the [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element; and the process fails to start.</span></span>  
  
 <span data-ttu-id="d03a5-123">當您針對預設應用程式域指定應用程式域管理員類型時，從預設應用程式域建立的其他應用程式域會繼承應用程式域管理員類型。</span><span class="sxs-lookup"><span data-stu-id="d03a5-123">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="d03a5-124">使用 <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> 和 <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> 屬性，為新的應用程式域指定不同的應用程式域管理員類型。</span><span class="sxs-lookup"><span data-stu-id="d03a5-124">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="d03a5-125">指定應用程式域管理員類型時，應用程式必須具有完全信任。</span><span class="sxs-lookup"><span data-stu-id="d03a5-125">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="d03a5-126">（例如，在桌面上執行的應用程式會有完全信任）。如果應用程式沒有完全信任， <xref:System.TypeLoadException> 則會擲回。</span><span class="sxs-lookup"><span data-stu-id="d03a5-126">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="d03a5-127">類型和命名空間的格式與用於屬性的格式相同 <xref:System.Type.FullName%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="d03a5-127">The format of the type and namespace is the same format that is used for the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="d03a5-128">此 configuration 元素僅適用于 .NET Framework 4 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="d03a5-128">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d03a5-129">範例</span><span class="sxs-lookup"><span data-stu-id="d03a5-129">Example</span></span>  
 <span data-ttu-id="d03a5-130">下列範例示範如何指定進程的預設應用程式域的應用程式域管理員是 `MyMgr` 元件中的類型 `AdMgrExample` 。</span><span class="sxs-lookup"><span data-stu-id="d03a5-130">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d03a5-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d03a5-131">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="d03a5-132">\<appDomainManagerAssembly>元素</span><span class="sxs-lookup"><span data-stu-id="d03a5-132">\<appDomainManagerAssembly> Element</span></span>](appdomainmanagerassembly-element.md)
- [<span data-ttu-id="d03a5-133">執行時間設定架構</span><span class="sxs-lookup"><span data-stu-id="d03a5-133">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d03a5-134">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="d03a5-134">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="d03a5-135">SetAppDomainManagerType 方法</span><span class="sxs-lookup"><span data-stu-id="d03a5-135">SetAppDomainManagerType Method</span></span>](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
