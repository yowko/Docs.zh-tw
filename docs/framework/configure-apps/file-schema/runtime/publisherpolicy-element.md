---
title: <publisherPolicy> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#publisherPolicy
helpviewer_keywords:
- publisherPolicy element
- container tags, <publisherPolicy> element
- <publisherPolicy> element
ms.assetid: 4613407e-d0a8-4ef2-9f81-a6acb9fdc7d4
ms.openlocfilehash: 89fa8a991cc7d0352eb0a13cdfd3a6063ea468e7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73115852"
---
# <a name="publisherpolicy-element"></a><span data-ttu-id="a8621-102">\<publisherPolicy> 項目</span><span class="sxs-lookup"><span data-stu-id="a8621-102">\<publisherPolicy> Element</span></span>
<span data-ttu-id="a8621-103">指定執行階段是否套用發行者原則。</span><span class="sxs-lookup"><span data-stu-id="a8621-103">Specifies whether the runtime applies publisher policy.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<publisherPolicy>**  
  
## <a name="syntax"></a><span data-ttu-id="a8621-104">語法</span><span class="sxs-lookup"><span data-stu-id="a8621-104">Syntax</span></span>  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a8621-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a8621-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a8621-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a8621-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a8621-107">屬性</span><span class="sxs-lookup"><span data-stu-id="a8621-107">Attributes</span></span>  
  
|<span data-ttu-id="a8621-108">屬性</span><span class="sxs-lookup"><span data-stu-id="a8621-108">Attribute</span></span>|<span data-ttu-id="a8621-109">描述</span><span class="sxs-lookup"><span data-stu-id="a8621-109">Description</span></span>|  
|---------------|-----------------|  
|`apply`|<span data-ttu-id="a8621-110">指定是否要套用發行者原則。</span><span class="sxs-lookup"><span data-stu-id="a8621-110">Specifies whether to apply publisher policy.</span></span>|  
  
## <a name="apply-attribute"></a><span data-ttu-id="a8621-111">apply 屬性</span><span class="sxs-lookup"><span data-stu-id="a8621-111">apply Attribute</span></span>  
  
|<span data-ttu-id="a8621-112">值</span><span class="sxs-lookup"><span data-stu-id="a8621-112">Value</span></span>|<span data-ttu-id="a8621-113">描述</span><span class="sxs-lookup"><span data-stu-id="a8621-113">Description</span></span>|  
|-----------|-----------------|  
|`yes`|<span data-ttu-id="a8621-114">套用發行者原則。</span><span class="sxs-lookup"><span data-stu-id="a8621-114">Applies publisher policy.</span></span> <span data-ttu-id="a8621-115">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="a8621-115">This is the default setting.</span></span>|  
|`no`|<span data-ttu-id="a8621-116">不會套用發行者原則。</span><span class="sxs-lookup"><span data-stu-id="a8621-116">Does not apply publisher policy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a8621-117">子元素</span><span class="sxs-lookup"><span data-stu-id="a8621-117">Child Elements</span></span>  

<span data-ttu-id="a8621-118">無。</span><span class="sxs-lookup"><span data-stu-id="a8621-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a8621-119">父項目</span><span class="sxs-lookup"><span data-stu-id="a8621-119">Parent Elements</span></span>  
  
|<span data-ttu-id="a8621-120">元素</span><span class="sxs-lookup"><span data-stu-id="a8621-120">Element</span></span>|<span data-ttu-id="a8621-121">描述</span><span class="sxs-lookup"><span data-stu-id="a8621-121">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="a8621-122">包含有關組件版本重新導向和組件位置的資訊。</span><span class="sxs-lookup"><span data-stu-id="a8621-122">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="a8621-123">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="a8621-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="a8621-124">封裝每一個組件的繫結原則和組件位置。</span><span class="sxs-lookup"><span data-stu-id="a8621-124">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="a8621-125">`<dependentAssembly>`針對每個元件使用一個元素。</span><span class="sxs-lookup"><span data-stu-id="a8621-125">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="a8621-126">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="a8621-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8621-127">備註</span><span class="sxs-lookup"><span data-stu-id="a8621-127">Remarks</span></span>  
 <span data-ttu-id="a8621-128">當元件廠商發行新版本的元件時，廠商可以包含發行者原則，因此使用舊版本的應用程式現在會使用新的版本。</span><span class="sxs-lookup"><span data-stu-id="a8621-128">When a component vendor releases a new version of an assembly, the vendor can include a publisher policy so applications that use the old version now use the new version.</span></span> <span data-ttu-id="a8621-129">若要指定是否要針對特定元件套用發行者原則，請將 **\<publisherPolicy>** 元素放在 **\<dependentAssembly>** 元素中。</span><span class="sxs-lookup"><span data-stu-id="a8621-129">To specify whether to apply publisher policy for a particular assembly, put the **\<publisherPolicy>** element in the **\<dependentAssembly>** element.</span></span>  
  
 <span data-ttu-id="a8621-130">**Apply**屬性的預設設定為 **[是]**。</span><span class="sxs-lookup"><span data-stu-id="a8621-130">The default setting for the **apply** attribute is **yes**.</span></span> <span data-ttu-id="a8621-131">**將 [套用**屬性] 設定為 [**否**] 會覆寫元件的任何先前的 **[是]** 設定。</span><span class="sxs-lookup"><span data-stu-id="a8621-131">Setting the **apply** attribute to **no** overrides any previous **yes** settings for an assembly.</span></span>  
  
 <span data-ttu-id="a8621-132">需要有許可權，應用程式才能使用 [\<publisherPolicy apply="no"/>](publisherpolicy-element.md) 應用程式佈建檔中的專案明確略過發行者原則。</span><span class="sxs-lookup"><span data-stu-id="a8621-132">Permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](publisherpolicy-element.md) element in the application configuration file.</span></span> <span data-ttu-id="a8621-133">許可權是藉由在上設定旗標來授與 <xref:System.Security.Permissions.SecurityPermissionFlag> <xref:System.Security.Permissions.SecurityPermission> 。</span><span class="sxs-lookup"><span data-stu-id="a8621-133">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="a8621-134">如需詳細資訊，請參閱元件系結重新導向[安全性許可權](../../assembly-binding-redirection-security-permission.md)。</span><span class="sxs-lookup"><span data-stu-id="a8621-134">For more information, see [Assembly Binding Redirection Security Permission](../../assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8621-135">範例</span><span class="sxs-lookup"><span data-stu-id="a8621-135">Example</span></span>  
 <span data-ttu-id="a8621-136">下列範例會關閉元件的發行者原則 `myAssembly` 。</span><span class="sxs-lookup"><span data-stu-id="a8621-136">The following example turns off publisher policy for the assembly, `myAssembly`.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                                    publicKeyToken="32ab4ba45e0a69a1"  
                                    culture="neutral" />  
            <publisherPolicy apply="no"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a8621-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8621-137">See also</span></span>

- [<span data-ttu-id="a8621-138">執行時間設定架構</span><span class="sxs-lookup"><span data-stu-id="a8621-138">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a8621-139">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="a8621-139">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="a8621-140">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="a8621-140">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="a8621-141">重新導向組件版本</span><span class="sxs-lookup"><span data-stu-id="a8621-141">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
