---
title: <bindingRedirect> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/bindingRedirect
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bindingRedirect
helpviewer_keywords:
- <bindingRedirect> element
- container tags, <bindingRedirect> element
- bindingRedirect element
ms.assetid: 67784ecd-9663-434e-bd6a-26975e447ac0
ms.openlocfilehash: 7667f78d2c341990585526fd153c0b230658a2ee
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167245"
---
# <a name="bindingredirect-element"></a><span data-ttu-id="e328e-102">\<bindingRedirect> 項目</span><span class="sxs-lookup"><span data-stu-id="e328e-102">\<bindingRedirect> Element</span></span>

<span data-ttu-id="e328e-103">將一個組件版本重新導向至另一個版本。</span><span class="sxs-lookup"><span data-stu-id="e328e-103">Redirects one assembly version to another.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bindingRedirect>**  
  
## <a name="syntax"></a><span data-ttu-id="e328e-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="e328e-104">Syntax</span></span>  
  
```xml  
   <bindingRedirect
oldVersion="existing assembly version"  
newVersion="new assembly version"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e328e-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e328e-105">Attributes and Elements</span></span>  

 <span data-ttu-id="e328e-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e328e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e328e-107">屬性</span><span class="sxs-lookup"><span data-stu-id="e328e-107">Attributes</span></span>  
  
|<span data-ttu-id="e328e-108">屬性</span><span class="sxs-lookup"><span data-stu-id="e328e-108">Attribute</span></span>|<span data-ttu-id="e328e-109">描述</span><span class="sxs-lookup"><span data-stu-id="e328e-109">Description</span></span>|  
|---------------|-----------------|  
|`oldVersion`|<span data-ttu-id="e328e-110">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="e328e-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="e328e-111">指定原本要求的組件版本。</span><span class="sxs-lookup"><span data-stu-id="e328e-111">Specifies the version of the assembly that was originally requested.</span></span> <span data-ttu-id="e328e-112">元件版本號碼的格式為 *主要.*... a............。</span><span class="sxs-lookup"><span data-stu-id="e328e-112">The format of an assembly version number is *major.minor.build.revision*.</span></span> <span data-ttu-id="e328e-113">這個版本號碼每個部分的有效值為 0 至 65535。</span><span class="sxs-lookup"><span data-stu-id="e328e-113">Valid values for each part of this version number are 0 to 65535.</span></span><br /><br /> <span data-ttu-id="e328e-114">您也可以使用下列格式指定版本範圍：</span><span class="sxs-lookup"><span data-stu-id="e328e-114">You can also specify a range of versions in the following format:</span></span><br /><br /> <span data-ttu-id="e328e-115">*n. n. n. n n n n. n n*</span><span class="sxs-lookup"><span data-stu-id="e328e-115">*n.n.n.n - n.n.n.n*</span></span>|  
|`newVersion`|<span data-ttu-id="e328e-116">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="e328e-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="e328e-117">指定要使用的元件版本，而不是原始要求的版本，格式為： *n-1* . n. n</span><span class="sxs-lookup"><span data-stu-id="e328e-117">Specifies the version of the assembly to use instead of the originally requested version in the format: *n.n.n.n*</span></span><br /><br /> <span data-ttu-id="e328e-118">這個值可以指定 `oldVersion` 以前的版本。</span><span class="sxs-lookup"><span data-stu-id="e328e-118">This value can specify an earlier version than `oldVersion`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e328e-119">子元素</span><span class="sxs-lookup"><span data-stu-id="e328e-119">Child Elements</span></span>  
  
|<span data-ttu-id="e328e-120">項目</span><span class="sxs-lookup"><span data-stu-id="e328e-120">Element</span></span>|<span data-ttu-id="e328e-121">描述</span><span class="sxs-lookup"><span data-stu-id="e328e-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e328e-122">無</span><span class="sxs-lookup"><span data-stu-id="e328e-122">None</span></span>||  
  
### <a name="parent-elements"></a><span data-ttu-id="e328e-123">父項目</span><span class="sxs-lookup"><span data-stu-id="e328e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e328e-124">項目</span><span class="sxs-lookup"><span data-stu-id="e328e-124">Element</span></span>|<span data-ttu-id="e328e-125">描述</span><span class="sxs-lookup"><span data-stu-id="e328e-125">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="e328e-126">包含有關組件版本重新導向和組件位置的資訊。</span><span class="sxs-lookup"><span data-stu-id="e328e-126">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="e328e-127">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="e328e-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="e328e-128">封裝每一個組件的繫結原則和組件位置。</span><span class="sxs-lookup"><span data-stu-id="e328e-128">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="e328e-129">針對每個組件使用一個 dependentAssembly 項目。</span><span class="sxs-lookup"><span data-stu-id="e328e-129">Use one dependentAssembly element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="e328e-130">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="e328e-130">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e328e-131">備註</span><span class="sxs-lookup"><span data-stu-id="e328e-131">Remarks</span></span>  

 <span data-ttu-id="e328e-132">當您對照強式名稱的組件建置 .NET Framework 應用程式時，即使有可用的新版本，應用程式仍會預設為在執行階段使用該組件版本。</span><span class="sxs-lookup"><span data-stu-id="e328e-132">When you build a .NET Framework application against a strong-named assembly, the application uses that version of the assembly at run time by default, even if a new version is available.</span></span> <span data-ttu-id="e328e-133">不過，您可以設定應用程式以較新的組件版本執行。</span><span class="sxs-lookup"><span data-stu-id="e328e-133">However, you can configure the application to run against a newer version of the assembly.</span></span> <span data-ttu-id="e328e-134">如需執行時間如何使用這些檔案來判斷要使用哪個元件版本的詳細資訊，請參閱 [執行時間如何找出元件](../../../deployment/how-the-runtime-locates-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="e328e-134">For details on how the runtime uses these files to determine which assembly version to use, see [How the Runtime Locates Assemblies](../../../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="e328e-135">您可以在 `bindingRedirect` 項目中包含多個 `dependentAssembly` 項目，藉此重新導向多個組件版本。</span><span class="sxs-lookup"><span data-stu-id="e328e-135">You can redirect more than one assembly version by including multiple `bindingRedirect` elements in a `dependentAssembly` element.</span></span> <span data-ttu-id="e328e-136">您也可以將組件從較新版本重新導向至較舊版本。</span><span class="sxs-lookup"><span data-stu-id="e328e-136">You can also redirect from a newer version to an older version of the assembly.</span></span>  
  
 <span data-ttu-id="e328e-137">在應用程式組態檔中進行明確的組件繫結重新導向必須擁有安全性權限。</span><span class="sxs-lookup"><span data-stu-id="e328e-137">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="e328e-138">這適用於 .NET Framework 組件和協力廠商組件的重新導向。</span><span class="sxs-lookup"><span data-stu-id="e328e-138">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="e328e-139">藉由在上設定旗標來授與許可權 <xref:System.Security.Permissions.SecurityPermissionFlag> <xref:System.Security.Permissions.SecurityPermission> 。</span><span class="sxs-lookup"><span data-stu-id="e328e-139">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="e328e-140">如需詳細資訊，請參閱元件系結重新導向 [安全性許可權](../../assembly-binding-redirection-security-permission.md)。</span><span class="sxs-lookup"><span data-stu-id="e328e-140">For more information, see [Assembly Binding Redirection Security Permission](../../assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e328e-141">範例</span><span class="sxs-lookup"><span data-stu-id="e328e-141">Example</span></span>  

 <span data-ttu-id="e328e-142">下列範例將示範如何將某一個組件版本重新導向至另一個版本。</span><span class="sxs-lookup"><span data-stu-id="e328e-142">The following example shows how to redirect one assembly version to another.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e328e-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e328e-143">See also</span></span>

- [<span data-ttu-id="e328e-144">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="e328e-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e328e-145">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="e328e-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="e328e-146">重新導向組件版本</span><span class="sxs-lookup"><span data-stu-id="e328e-146">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
