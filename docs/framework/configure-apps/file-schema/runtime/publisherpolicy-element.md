---
title: "&lt;p&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#publisherPolicy
helpviewer_keywords:
- publisherPolicy element
- container tags, <publisherPolicy> element
- <publisherPolicy> element
ms.assetid: 4613407e-d0a8-4ef2-9f81-a6acb9fdc7d4
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 654887c870a7f620c52fa402d6324de39fdb2feb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltpublisherpolicygt-element"></a><span data-ttu-id="fecd1-102">&lt;p&gt;項目</span><span class="sxs-lookup"><span data-stu-id="fecd1-102">&lt;publisherPolicy&gt; Element</span></span>
<span data-ttu-id="fecd1-103">指定執行階段是否套用發行者原則。</span><span class="sxs-lookup"><span data-stu-id="fecd1-103">Specifies whether the runtime applies publisher policy.</span></span>  
  
 <span data-ttu-id="fecd1-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="fecd1-104">\<configuration></span></span>  
<span data-ttu-id="fecd1-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="fecd1-105">\<runtime></span></span>  
<span data-ttu-id="fecd1-106">\<assemblyBinding ></span><span class="sxs-lookup"><span data-stu-id="fecd1-106">\<assemblyBinding></span></span>  
<span data-ttu-id="fecd1-107">\<y ></span><span class="sxs-lookup"><span data-stu-id="fecd1-107">\<dependentAssembly></span></span>  
<span data-ttu-id="fecd1-108">\<p ></span><span class="sxs-lookup"><span data-stu-id="fecd1-108">\<publisherPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fecd1-109">語法</span><span class="sxs-lookup"><span data-stu-id="fecd1-109">Syntax</span></span>  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fecd1-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="fecd1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="fecd1-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="fecd1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fecd1-112">屬性</span><span class="sxs-lookup"><span data-stu-id="fecd1-112">Attributes</span></span>  
  
|<span data-ttu-id="fecd1-113">屬性</span><span class="sxs-lookup"><span data-stu-id="fecd1-113">Attribute</span></span>|<span data-ttu-id="fecd1-114">說明</span><span class="sxs-lookup"><span data-stu-id="fecd1-114">Description</span></span>|  
|---------------|-----------------|  
|`apply`|<span data-ttu-id="fecd1-115">指定是否套用發行者原則。</span><span class="sxs-lookup"><span data-stu-id="fecd1-115">Specifies whether to apply publisher policy.</span></span>|  
  
## <a name="apply-attribute"></a><span data-ttu-id="fecd1-116">套用屬性</span><span class="sxs-lookup"><span data-stu-id="fecd1-116">apply Attribute</span></span>  
  
|<span data-ttu-id="fecd1-117">值</span><span class="sxs-lookup"><span data-stu-id="fecd1-117">Value</span></span>|<span data-ttu-id="fecd1-118">說明</span><span class="sxs-lookup"><span data-stu-id="fecd1-118">Description</span></span>|  
|-----------|-----------------|  
|`yes`|<span data-ttu-id="fecd1-119">套用發行者原則。</span><span class="sxs-lookup"><span data-stu-id="fecd1-119">Applies publisher policy.</span></span> <span data-ttu-id="fecd1-120">這是預設設定。</span><span class="sxs-lookup"><span data-stu-id="fecd1-120">This is the default setting.</span></span>|  
|`no`|<span data-ttu-id="fecd1-121">不套用發行者原則。</span><span class="sxs-lookup"><span data-stu-id="fecd1-121">Does not apply publisher policy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fecd1-122">子元素</span><span class="sxs-lookup"><span data-stu-id="fecd1-122">Child Elements</span></span>  
 <span data-ttu-id="fecd1-123">無。</span><span class="sxs-lookup"><span data-stu-id="fecd1-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fecd1-124">父項目</span><span class="sxs-lookup"><span data-stu-id="fecd1-124">Parent Elements</span></span>  
  
|<span data-ttu-id="fecd1-125">項目</span><span class="sxs-lookup"><span data-stu-id="fecd1-125">Element</span></span>|<span data-ttu-id="fecd1-126">描述</span><span class="sxs-lookup"><span data-stu-id="fecd1-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="fecd1-127">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="fecd1-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="fecd1-128">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="fecd1-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fecd1-129">備註</span><span class="sxs-lookup"><span data-stu-id="fecd1-129">Remarks</span></span>  
 <span data-ttu-id="fecd1-130">當元件廠商發行新版的組件時，廠商可以包含發行者原則，因此現在使用舊版本的應用程式使用新的版本。</span><span class="sxs-lookup"><span data-stu-id="fecd1-130">When a component vendor releases a new version of an assembly, the vendor can include a publisher policy so applications that use the old version now use the new version.</span></span> <span data-ttu-id="fecd1-131">若要指定是否要針對特定的組件套用發行者原則，請將 **\<p >**中的項目 **\<dependentAssembly >**項目。</span><span class="sxs-lookup"><span data-stu-id="fecd1-131">To specify whether to apply publisher policy for a particular assembly, put the **\<publisherPolicy>** element in the **\<dependentAssembly>** element.</span></span>  
  
 <span data-ttu-id="fecd1-132">預設設定**套用**屬性是**是**。</span><span class="sxs-lookup"><span data-stu-id="fecd1-132">The default setting for the **apply** attribute is **yes**.</span></span> <span data-ttu-id="fecd1-133">設定**套用**屬性**沒有**覆寫任何先前**是**組件的設定。</span><span class="sxs-lookup"><span data-stu-id="fecd1-133">Setting the **apply** attribute to **no** overrides any previous **yes** settings for an assembly.</span></span>  
  
 <span data-ttu-id="fecd1-134">若要明確地略過發行者原則使用的應用程式需要的權限[ \<p 套用 ="no"/ >](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)應用程式組態檔中的項目。</span><span class="sxs-lookup"><span data-stu-id="fecd1-134">Permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) element in the application configuration file.</span></span> <span data-ttu-id="fecd1-135">藉由設定授與權<xref:System.Security.Permissions.SecurityPermissionFlag>加上旗標上<xref:System.Security.Permissions.SecurityPermission>。</span><span class="sxs-lookup"><span data-stu-id="fecd1-135">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="fecd1-136">如需詳細資訊，請參閱[組件繫結重新導向安全性權限](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md)。</span><span class="sxs-lookup"><span data-stu-id="fecd1-136">For more information, see [Assembly Binding Redirection Security Permission](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fecd1-137">範例</span><span class="sxs-lookup"><span data-stu-id="fecd1-137">Example</span></span>  
 <span data-ttu-id="fecd1-138">下列範例會關閉發行者原則組件， `myAssembly`。</span><span class="sxs-lookup"><span data-stu-id="fecd1-138">The following example turns off publisher policy for the assembly, `myAssembly`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fecd1-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fecd1-139">See Also</span></span>  
 [<span data-ttu-id="fecd1-140">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="fecd1-140">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="fecd1-141">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="fecd1-141">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="fecd1-142">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="fecd1-142">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="fecd1-143">重新導向組件版本</span><span class="sxs-lookup"><span data-stu-id="fecd1-143">Redirecting Assembly Versions</span></span>](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
