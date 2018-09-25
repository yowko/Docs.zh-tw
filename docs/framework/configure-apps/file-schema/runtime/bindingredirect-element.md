---
title: '&lt;bindingRedirect&gt;項目'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/bindingRedirect
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bindingRedirect
helpviewer_keywords:
- <bindingRedirect> element
- container tags, <bindingRedirect> element
- bindingRedirect element
ms.assetid: 67784ecd-9663-434e-bd6a-26975e447ac0
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 535519c65aba7ce13703bb33a16b09cde84c3f03
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47085540"
---
# <a name="ltbindingredirectgt-element"></a><span data-ttu-id="e6f06-102">&lt;bindingRedirect&gt;項目</span><span class="sxs-lookup"><span data-stu-id="e6f06-102">&lt;bindingRedirect&gt; Element</span></span>
<span data-ttu-id="e6f06-103">將一個組件版本重新導向至另一個版本。</span><span class="sxs-lookup"><span data-stu-id="e6f06-103">Redirects one assembly version to another.</span></span>  
  
 <span data-ttu-id="e6f06-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="e6f06-104">\<configuration></span></span>  
<span data-ttu-id="e6f06-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="e6f06-105">\<runtime></span></span>  
<span data-ttu-id="e6f06-106">\<assemblyBinding></span><span class="sxs-lookup"><span data-stu-id="e6f06-106">\<assemblyBinding></span></span>  
<span data-ttu-id="e6f06-107">\<dependentAssembly></span><span class="sxs-lookup"><span data-stu-id="e6f06-107">\<dependentAssembly></span></span>  
<span data-ttu-id="e6f06-108">\<bindingRedirect ></span><span class="sxs-lookup"><span data-stu-id="e6f06-108">\<bindingRedirect></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6f06-109">語法</span><span class="sxs-lookup"><span data-stu-id="e6f06-109">Syntax</span></span>  
  
```xml  
   <bindingRedirect    
oldVersion="existing assembly version"  
newVersion="new assembly version"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6f06-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e6f06-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e6f06-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e6f06-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6f06-112">屬性</span><span class="sxs-lookup"><span data-stu-id="e6f06-112">Attributes</span></span>  
  
|<span data-ttu-id="e6f06-113">屬性</span><span class="sxs-lookup"><span data-stu-id="e6f06-113">Attribute</span></span>|<span data-ttu-id="e6f06-114">描述</span><span class="sxs-lookup"><span data-stu-id="e6f06-114">Description</span></span>|  
|---------------|-----------------|  
|`oldVersion`|<span data-ttu-id="e6f06-115">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="e6f06-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="e6f06-116">指定原本要求的組件版本。</span><span class="sxs-lookup"><span data-stu-id="e6f06-116">Specifies the version of the assembly that was originally requested.</span></span> <span data-ttu-id="e6f06-117">組件版本號碼的格式*major.minor.build.revision*。</span><span class="sxs-lookup"><span data-stu-id="e6f06-117">The format of an assembly version number is *major.minor.build.revision*.</span></span> <span data-ttu-id="e6f06-118">這個版本號碼每個部分的有效值為 0 至 65535。</span><span class="sxs-lookup"><span data-stu-id="e6f06-118">Valid values for each part of this version number are 0 to 65535.</span></span><br /><br /> <span data-ttu-id="e6f06-119">您也可以使用下列格式指定版本範圍：</span><span class="sxs-lookup"><span data-stu-id="e6f06-119">You can also specify a range of versions in the following format:</span></span><br /><br /> <span data-ttu-id="e6f06-120">*n.n.n.n-n.n.n.n*</span><span class="sxs-lookup"><span data-stu-id="e6f06-120">*n.n.n.n - n.n.n.n*</span></span>|  
|`newVersion`|<span data-ttu-id="e6f06-121">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="e6f06-121">Required attribute.</span></span><br /><br /> <span data-ttu-id="e6f06-122">指定要使用，而非原本要求的版本格式的組件版本： *n.n.n.n*</span><span class="sxs-lookup"><span data-stu-id="e6f06-122">Specifies the version of the assembly to use instead of the originally requested version in the format: *n.n.n.n*</span></span><br /><br /> <span data-ttu-id="e6f06-123">這個值可以指定 `oldVersion` 以前的版本。</span><span class="sxs-lookup"><span data-stu-id="e6f06-123">This value can specify an earlier version than `oldVersion`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e6f06-124">子元素</span><span class="sxs-lookup"><span data-stu-id="e6f06-124">Child Elements</span></span>  
  
|<span data-ttu-id="e6f06-125">項目</span><span class="sxs-lookup"><span data-stu-id="e6f06-125">Element</span></span>|<span data-ttu-id="e6f06-126">描述</span><span class="sxs-lookup"><span data-stu-id="e6f06-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e6f06-127">無</span><span class="sxs-lookup"><span data-stu-id="e6f06-127">None</span></span>||  
  
### <a name="parent-elements"></a><span data-ttu-id="e6f06-128">父項目</span><span class="sxs-lookup"><span data-stu-id="e6f06-128">Parent Elements</span></span>  
  
|<span data-ttu-id="e6f06-129">項目</span><span class="sxs-lookup"><span data-stu-id="e6f06-129">Element</span></span>|<span data-ttu-id="e6f06-130">描述</span><span class="sxs-lookup"><span data-stu-id="e6f06-130">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="e6f06-131">包含有關組件版本重新導向和組件位置的資訊。</span><span class="sxs-lookup"><span data-stu-id="e6f06-131">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="e6f06-132">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="e6f06-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="e6f06-133">封裝每一個組件的繫結原則和組件位置。</span><span class="sxs-lookup"><span data-stu-id="e6f06-133">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="e6f06-134">針對每個組件使用一個 dependentAssembly 項目。</span><span class="sxs-lookup"><span data-stu-id="e6f06-134">Use one dependentAssembly element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="e6f06-135">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="e6f06-135">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6f06-136">備註</span><span class="sxs-lookup"><span data-stu-id="e6f06-136">Remarks</span></span>  
 <span data-ttu-id="e6f06-137">當您對照強式名稱的組件建置 .NET Framework 應用程式時，即使有可用的新版本，應用程式仍會預設為在執行階段使用該組件版本。</span><span class="sxs-lookup"><span data-stu-id="e6f06-137">When you build a .NET Framework application against a strong-named assembly, the application uses that version of the assembly at run time by default, even if a new version is available.</span></span> <span data-ttu-id="e6f06-138">不過，您可以設定應用程式以較新的組件版本執行。</span><span class="sxs-lookup"><span data-stu-id="e6f06-138">However, you can configure the application to run against a newer version of the assembly.</span></span> <span data-ttu-id="e6f06-139">如需如何執行階段會使用這些檔案來判斷要使用的組件版本的詳細資訊，請參閱[執行階段如何找出組件](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="e6f06-139">For details on how the runtime uses these files to determine which assembly version to use, see [How the Runtime Locates Assemblies](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="e6f06-140">您可以在 `bindingRedirect` 項目中包含多個 `dependentAssembly` 項目，藉此重新導向多個組件版本。</span><span class="sxs-lookup"><span data-stu-id="e6f06-140">You can redirect more than one assembly version by including multiple `bindingRedirect` elements in a `dependentAssembly` element.</span></span> <span data-ttu-id="e6f06-141">您也可以將組件從較新版本重新導向至較舊版本。</span><span class="sxs-lookup"><span data-stu-id="e6f06-141">You can also redirect from a newer version to an older version of the assembly.</span></span>  
  
 <span data-ttu-id="e6f06-142">在應用程式組態檔中進行明確的組件繫結重新導向必須擁有安全性權限。</span><span class="sxs-lookup"><span data-stu-id="e6f06-142">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="e6f06-143">這適用於 .NET Framework 組件和協力廠商組件的重新導向。</span><span class="sxs-lookup"><span data-stu-id="e6f06-143">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="e6f06-144">藉由設定授與權限<xref:System.Security.Permissions.SecurityPermissionFlag>加上旗標上<xref:System.Security.Permissions.SecurityPermission>。</span><span class="sxs-lookup"><span data-stu-id="e6f06-144">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="e6f06-145">如需詳細資訊，請參閱 <<c0> [ 組件繫結重新導向安全性使用權限](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md)。</span><span class="sxs-lookup"><span data-stu-id="e6f06-145">For more information, see [Assembly Binding Redirection Security Permission](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6f06-146">範例</span><span class="sxs-lookup"><span data-stu-id="e6f06-146">Example</span></span>  
 <span data-ttu-id="e6f06-147">下列範例將示範如何將某一個組件版本重新導向至另一個版本。</span><span class="sxs-lookup"><span data-stu-id="e6f06-147">The following example shows how to redirect one assembly version to another.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e6f06-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6f06-148">See Also</span></span>  
 [<span data-ttu-id="e6f06-149">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="e6f06-149">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="e6f06-150">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="e6f06-150">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="e6f06-151">重新導向組件版本</span><span class="sxs-lookup"><span data-stu-id="e6f06-151">Redirecting Assembly Versions</span></span>](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
