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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cc206e584440778858e61fc0bab51fc8ffa2009a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252385"
---
# <a name="publisherpolicy-element"></a><span data-ttu-id="2b069-102">\<publisherPolicy > 元素</span><span class="sxs-lookup"><span data-stu-id="2b069-102">\<publisherPolicy> Element</span></span>
<span data-ttu-id="2b069-103">指定執行階段是否套用發行者原則。</span><span class="sxs-lookup"><span data-stu-id="2b069-103">Specifies whether the runtime applies publisher policy.</span></span>  
  
<span data-ttu-id="2b069-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2b069-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2b069-105">&nbsp;&nbsp;[ **\<執行時間 >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="2b069-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="2b069-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<assemblyBinding >** ](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="2b069-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="2b069-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dependentAssembly >** ](dependentassembly-element.md)</span><span class="sxs-lookup"><span data-stu-id="2b069-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)</span></span>\
<span data-ttu-id="2b069-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<publisherPolicy >**</span><span class="sxs-lookup"><span data-stu-id="2b069-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<publisherPolicy>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b069-109">語法</span><span class="sxs-lookup"><span data-stu-id="2b069-109">Syntax</span></span>  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b069-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2b069-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2b069-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2b069-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b069-112">屬性</span><span class="sxs-lookup"><span data-stu-id="2b069-112">Attributes</span></span>  
  
|<span data-ttu-id="2b069-113">屬性</span><span class="sxs-lookup"><span data-stu-id="2b069-113">Attribute</span></span>|<span data-ttu-id="2b069-114">說明</span><span class="sxs-lookup"><span data-stu-id="2b069-114">Description</span></span>|  
|---------------|-----------------|  
|`apply`|<span data-ttu-id="2b069-115">指定是否要套用發行者原則。</span><span class="sxs-lookup"><span data-stu-id="2b069-115">Specifies whether to apply publisher policy.</span></span>|  
  
## <a name="apply-attribute"></a><span data-ttu-id="2b069-116">apply 屬性</span><span class="sxs-lookup"><span data-stu-id="2b069-116">apply Attribute</span></span>  
  
|<span data-ttu-id="2b069-117">值</span><span class="sxs-lookup"><span data-stu-id="2b069-117">Value</span></span>|<span data-ttu-id="2b069-118">說明</span><span class="sxs-lookup"><span data-stu-id="2b069-118">Description</span></span>|  
|-----------|-----------------|  
|`yes`|<span data-ttu-id="2b069-119">套用發行者原則。</span><span class="sxs-lookup"><span data-stu-id="2b069-119">Applies publisher policy.</span></span> <span data-ttu-id="2b069-120">這是預設設定。</span><span class="sxs-lookup"><span data-stu-id="2b069-120">This is the default setting.</span></span>|  
|`no`|<span data-ttu-id="2b069-121">不會套用發行者原則。</span><span class="sxs-lookup"><span data-stu-id="2b069-121">Does not apply publisher policy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2b069-122">子元素</span><span class="sxs-lookup"><span data-stu-id="2b069-122">Child Elements</span></span>  

<span data-ttu-id="2b069-123">無。</span><span class="sxs-lookup"><span data-stu-id="2b069-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2b069-124">父項目</span><span class="sxs-lookup"><span data-stu-id="2b069-124">Parent Elements</span></span>  
  
|<span data-ttu-id="2b069-125">項目</span><span class="sxs-lookup"><span data-stu-id="2b069-125">Element</span></span>|<span data-ttu-id="2b069-126">描述</span><span class="sxs-lookup"><span data-stu-id="2b069-126">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="2b069-127">包含有關組件版本重新導向和組件位置的資訊。</span><span class="sxs-lookup"><span data-stu-id="2b069-127">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="2b069-128">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="2b069-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="2b069-129">封裝每一個組件的繫結原則和組件位置。</span><span class="sxs-lookup"><span data-stu-id="2b069-129">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="2b069-130">針對每`<dependentAssembly>`個元件使用一個元素。</span><span class="sxs-lookup"><span data-stu-id="2b069-130">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="2b069-131">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="2b069-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b069-132">備註</span><span class="sxs-lookup"><span data-stu-id="2b069-132">Remarks</span></span>  
 <span data-ttu-id="2b069-133">當元件廠商發行新版本的元件時, 廠商可以包含發行者原則, 因此使用舊版本的應用程式現在會使用新的版本。</span><span class="sxs-lookup"><span data-stu-id="2b069-133">When a component vendor releases a new version of an assembly, the vendor can include a publisher policy so applications that use the old version now use the new version.</span></span> <span data-ttu-id="2b069-134">若要指定是否要針對特定元件套用發行者原則, 請將 **\<publisherPolicy >** 元素放在 **\<dependentAssembly >** 元素中。</span><span class="sxs-lookup"><span data-stu-id="2b069-134">To specify whether to apply publisher policy for a particular assembly, put the **\<publisherPolicy>** element in the **\<dependentAssembly>** element.</span></span>  
  
 <span data-ttu-id="2b069-135">**Apply**屬性的預設設定為 **[是]** 。</span><span class="sxs-lookup"><span data-stu-id="2b069-135">The default setting for the **apply** attribute is **yes**.</span></span> <span data-ttu-id="2b069-136">將 [套用屬性] 設定為 [**否**] 會覆寫元件的任何先前的 **[是]** 設定。</span><span class="sxs-lookup"><span data-stu-id="2b069-136">Setting the **apply** attribute to **no** overrides any previous **yes** settings for an assembly.</span></span>  
  
 <span data-ttu-id="2b069-137">應用程式必須具備許可權, 才能使用應用程式佈建檔中的[ \<publisherPolicy apply = "no"/>](publisherpolicy-element.md)元素明確忽略發行者原則。</span><span class="sxs-lookup"><span data-stu-id="2b069-137">Permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](publisherpolicy-element.md) element in the application configuration file.</span></span> <span data-ttu-id="2b069-138">許可權是藉由<xref:System.Security.Permissions.SecurityPermissionFlag> <xref:System.Security.Permissions.SecurityPermission>在上設定旗標來授與。</span><span class="sxs-lookup"><span data-stu-id="2b069-138">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="2b069-139">如需詳細資訊, 請參閱元件系結重新導向[安全性許可權](../../assembly-binding-redirection-security-permission.md)。</span><span class="sxs-lookup"><span data-stu-id="2b069-139">For more information, see [Assembly Binding Redirection Security Permission](../../assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b069-140">範例</span><span class="sxs-lookup"><span data-stu-id="2b069-140">Example</span></span>  
 <span data-ttu-id="2b069-141">下列範例會關閉元件`myAssembly`的發行者原則。</span><span class="sxs-lookup"><span data-stu-id="2b069-141">The following example turns off publisher policy for the assembly, `myAssembly`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2b069-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b069-142">See also</span></span>

- [<span data-ttu-id="2b069-143">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="2b069-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="2b069-144">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="2b069-144">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="2b069-145">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="2b069-145">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="2b069-146">重新導向組件版本</span><span class="sxs-lookup"><span data-stu-id="2b069-146">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
