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
ms.openlocfilehash: 29932eb27bcd13876ea6982982e67341edb8e0de
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076285"
---
# <a name="publisherpolicy-element"></a><span data-ttu-id="8dbcf-102">\<publisherPolicy > 項目</span><span class="sxs-lookup"><span data-stu-id="8dbcf-102">\<publisherPolicy> Element</span></span>
<span data-ttu-id="8dbcf-103">指定執行階段是否套用發行者原則。</span><span class="sxs-lookup"><span data-stu-id="8dbcf-103">Specifies whether the runtime applies publisher policy.</span></span>  
  
 <span data-ttu-id="8dbcf-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="8dbcf-104">\<configuration></span></span>  
<span data-ttu-id="8dbcf-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="8dbcf-105">\<runtime></span></span>  
<span data-ttu-id="8dbcf-106">\<assemblyBinding></span><span class="sxs-lookup"><span data-stu-id="8dbcf-106">\<assemblyBinding></span></span>  
<span data-ttu-id="8dbcf-107">\<dependentAssembly></span><span class="sxs-lookup"><span data-stu-id="8dbcf-107">\<dependentAssembly></span></span>  
<span data-ttu-id="8dbcf-108">\<publisherPolicy></span><span class="sxs-lookup"><span data-stu-id="8dbcf-108">\<publisherPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dbcf-109">語法</span><span class="sxs-lookup"><span data-stu-id="8dbcf-109">Syntax</span></span>  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8dbcf-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8dbcf-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8dbcf-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="8dbcf-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8dbcf-112">屬性</span><span class="sxs-lookup"><span data-stu-id="8dbcf-112">Attributes</span></span>  
  
|<span data-ttu-id="8dbcf-113">屬性</span><span class="sxs-lookup"><span data-stu-id="8dbcf-113">Attribute</span></span>|<span data-ttu-id="8dbcf-114">描述</span><span class="sxs-lookup"><span data-stu-id="8dbcf-114">Description</span></span>|  
|---------------|-----------------|  
|`apply`|<span data-ttu-id="8dbcf-115">指定是否要將發行者原則套用。</span><span class="sxs-lookup"><span data-stu-id="8dbcf-115">Specifies whether to apply publisher policy.</span></span>|  
  
## <a name="apply-attribute"></a><span data-ttu-id="8dbcf-116">套用屬性</span><span class="sxs-lookup"><span data-stu-id="8dbcf-116">apply Attribute</span></span>  
  
|<span data-ttu-id="8dbcf-117">值</span><span class="sxs-lookup"><span data-stu-id="8dbcf-117">Value</span></span>|<span data-ttu-id="8dbcf-118">描述</span><span class="sxs-lookup"><span data-stu-id="8dbcf-118">Description</span></span>|  
|-----------|-----------------|  
|`yes`|<span data-ttu-id="8dbcf-119">發行者原則套用。</span><span class="sxs-lookup"><span data-stu-id="8dbcf-119">Applies publisher policy.</span></span> <span data-ttu-id="8dbcf-120">這是預設設定。</span><span class="sxs-lookup"><span data-stu-id="8dbcf-120">This is the default setting.</span></span>|  
|`no`|<span data-ttu-id="8dbcf-121">不適用於發行者原則。</span><span class="sxs-lookup"><span data-stu-id="8dbcf-121">Does not apply publisher policy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8dbcf-122">子元素</span><span class="sxs-lookup"><span data-stu-id="8dbcf-122">Child Elements</span></span>  
 <span data-ttu-id="8dbcf-123">無。</span><span class="sxs-lookup"><span data-stu-id="8dbcf-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8dbcf-124">父項目</span><span class="sxs-lookup"><span data-stu-id="8dbcf-124">Parent Elements</span></span>  
  
|<span data-ttu-id="8dbcf-125">項目</span><span class="sxs-lookup"><span data-stu-id="8dbcf-125">Element</span></span>|<span data-ttu-id="8dbcf-126">描述</span><span class="sxs-lookup"><span data-stu-id="8dbcf-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8dbcf-127">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="8dbcf-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="8dbcf-128">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="8dbcf-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8dbcf-129">備註</span><span class="sxs-lookup"><span data-stu-id="8dbcf-129">Remarks</span></span>  
 <span data-ttu-id="8dbcf-130">當元件廠商發行新版本的組件時，廠商可以加入發行者原則，因此現在使用的舊版本的應用程式使用新的版本。</span><span class="sxs-lookup"><span data-stu-id="8dbcf-130">When a component vendor releases a new version of an assembly, the vendor can include a publisher policy so applications that use the old version now use the new version.</span></span> <span data-ttu-id="8dbcf-131">若要指定是否為特定組件套用發行者原則，請將放 **\<publisherPolicy >** 中的項目 **\<dependentAssembly >** 項目。</span><span class="sxs-lookup"><span data-stu-id="8dbcf-131">To specify whether to apply publisher policy for a particular assembly, put the **\<publisherPolicy>** element in the **\<dependentAssembly>** element.</span></span>  
  
 <span data-ttu-id="8dbcf-132">預設值**套用**屬性是**是**。</span><span class="sxs-lookup"><span data-stu-id="8dbcf-132">The default setting for the **apply** attribute is **yes**.</span></span> <span data-ttu-id="8dbcf-133">設定**套用**屬性設定為**沒有**覆寫任何先前**是**組件的設定。</span><span class="sxs-lookup"><span data-stu-id="8dbcf-133">Setting the **apply** attribute to **no** overrides any previous **yes** settings for an assembly.</span></span>  
  
 <span data-ttu-id="8dbcf-134">需要明確地略過發行者原則使用的應用程式的權限[ \<apply ="no"/ >](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)應用程式組態檔中的項目。</span><span class="sxs-lookup"><span data-stu-id="8dbcf-134">Permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) element in the application configuration file.</span></span> <span data-ttu-id="8dbcf-135">藉由設定授與權限<xref:System.Security.Permissions.SecurityPermissionFlag>加上旗標上<xref:System.Security.Permissions.SecurityPermission>。</span><span class="sxs-lookup"><span data-stu-id="8dbcf-135">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="8dbcf-136">如需詳細資訊，請參閱 <<c0> [ 組件繫結重新導向安全性使用權限](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md)。</span><span class="sxs-lookup"><span data-stu-id="8dbcf-136">For more information, see [Assembly Binding Redirection Security Permission](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8dbcf-137">範例</span><span class="sxs-lookup"><span data-stu-id="8dbcf-137">Example</span></span>  
 <span data-ttu-id="8dbcf-138">下列範例會關閉發行者原則組件， `myAssembly`。</span><span class="sxs-lookup"><span data-stu-id="8dbcf-138">The following example turns off publisher policy for the assembly, `myAssembly`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8dbcf-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8dbcf-139">See also</span></span>

- [<span data-ttu-id="8dbcf-140">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="8dbcf-140">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="8dbcf-141">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="8dbcf-141">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="8dbcf-142">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="8dbcf-142">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="8dbcf-143">重新導向組件版本</span><span class="sxs-lookup"><span data-stu-id="8dbcf-143">Redirecting Assembly Versions</span></span>](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
