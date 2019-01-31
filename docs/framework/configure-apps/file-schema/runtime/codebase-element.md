---
title: <codeBase> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#codeBase
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/codeBase
helpviewer_keywords:
- <codeBase> element
- container tags, <codeBase> element
- codeBase element
ms.assetid: d48a3983-2297-43ff-a14d-1f29d3995822
ms.openlocfilehash: ebf7e2624cc36fb6a758afef38e2054669061dff
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269649"
---
# <a name="codebase-element"></a><span data-ttu-id="83ad6-102">\<程式碼基底 > 項目</span><span class="sxs-lookup"><span data-stu-id="83ad6-102">\<codeBase> Element</span></span>
<span data-ttu-id="83ad6-103">指定 common language runtime 可以找到組件的位置。</span><span class="sxs-lookup"><span data-stu-id="83ad6-103">Specifies where the common language runtime can find an assembly.</span></span>  
  
 <span data-ttu-id="83ad6-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="83ad6-104">\<configuration></span></span>  
<span data-ttu-id="83ad6-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="83ad6-105">\<runtime></span></span>  
<span data-ttu-id="83ad6-106">\<assemblyBinding></span><span class="sxs-lookup"><span data-stu-id="83ad6-106">\<assemblyBinding></span></span>  
<span data-ttu-id="83ad6-107">\<dependentAssembly></span><span class="sxs-lookup"><span data-stu-id="83ad6-107">\<dependentAssembly></span></span>  
<span data-ttu-id="83ad6-108">\<codeBase></span><span class="sxs-lookup"><span data-stu-id="83ad6-108">\<codeBase></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83ad6-109">語法</span><span class="sxs-lookup"><span data-stu-id="83ad6-109">Syntax</span></span>  
  
```xml  
   <codeBase    
version="Assembly version"  
href="URL of assembly"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="83ad6-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="83ad6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="83ad6-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="83ad6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="83ad6-112">屬性</span><span class="sxs-lookup"><span data-stu-id="83ad6-112">Attributes</span></span>  
  
|<span data-ttu-id="83ad6-113">屬性</span><span class="sxs-lookup"><span data-stu-id="83ad6-113">Attribute</span></span>|<span data-ttu-id="83ad6-114">描述</span><span class="sxs-lookup"><span data-stu-id="83ad6-114">Description</span></span>|  
|---------------|-----------------|  
|`href`|<span data-ttu-id="83ad6-115">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="83ad6-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="83ad6-116">指定執行階段可以在哪裡找到指定的版本的組件的 URL。</span><span class="sxs-lookup"><span data-stu-id="83ad6-116">Specifies the URL where the runtime can find the specified version of the assembly.</span></span>|  
|`version`|<span data-ttu-id="83ad6-117">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="83ad6-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="83ad6-118">指定程式碼基底適用於組件的版本。</span><span class="sxs-lookup"><span data-stu-id="83ad6-118">Specifies the version of the assembly the codebase applies to.</span></span> <span data-ttu-id="83ad6-119">組件版本號碼的格式*major.minor.build.revision*。</span><span class="sxs-lookup"><span data-stu-id="83ad6-119">The format of an assembly version number is *major.minor.build.revision*.</span></span>|  
  
## <a name="version-attribute"></a><span data-ttu-id="83ad6-120">版本屬性</span><span class="sxs-lookup"><span data-stu-id="83ad6-120">version Attribute</span></span>  
  
|<span data-ttu-id="83ad6-121">值</span><span class="sxs-lookup"><span data-stu-id="83ad6-121">Value</span></span>|<span data-ttu-id="83ad6-122">描述</span><span class="sxs-lookup"><span data-stu-id="83ad6-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="83ad6-123">每個部分的版本號碼的有效值為 0 到 65535 之間。</span><span class="sxs-lookup"><span data-stu-id="83ad6-123">Valid values for each part of the version number are 0 to 65535.</span></span>|<span data-ttu-id="83ad6-124">不適用。</span><span class="sxs-lookup"><span data-stu-id="83ad6-124">Not applicable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="83ad6-125">子元素</span><span class="sxs-lookup"><span data-stu-id="83ad6-125">Child Elements</span></span>  
 <span data-ttu-id="83ad6-126">無。</span><span class="sxs-lookup"><span data-stu-id="83ad6-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="83ad6-127">父項目</span><span class="sxs-lookup"><span data-stu-id="83ad6-127">Parent Elements</span></span>  
  
|<span data-ttu-id="83ad6-128">項目</span><span class="sxs-lookup"><span data-stu-id="83ad6-128">Element</span></span>|<span data-ttu-id="83ad6-129">描述</span><span class="sxs-lookup"><span data-stu-id="83ad6-129">Description</span></span>|  
|-------------|-----------------|  
|`buildproviders`|<span data-ttu-id="83ad6-130">定義用來編譯自訂資源檔的組建提供者集合。</span><span class="sxs-lookup"><span data-stu-id="83ad6-130">Defines a collection of build providers used to compile custom resource files.</span></span> <span data-ttu-id="83ad6-131">組建提供者的數量不限。</span><span class="sxs-lookup"><span data-stu-id="83ad6-131">You can have any number of build providers.</span></span>|  
|`compilation`|<span data-ttu-id="83ad6-132">設定 ASP.NET 使用的所有編譯設定。</span><span class="sxs-lookup"><span data-stu-id="83ad6-132">Configures all the compilation settings that ASP.NET uses.</span></span>|  
|`configuration`|<span data-ttu-id="83ad6-133">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="83ad6-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.web`|<span data-ttu-id="83ad6-134">指定 ASP.NET 組態區段的根項目。</span><span class="sxs-lookup"><span data-stu-id="83ad6-134">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83ad6-135">備註</span><span class="sxs-lookup"><span data-stu-id="83ad6-135">Remarks</span></span>  
 <span data-ttu-id="83ad6-136">若要使用執行階段 **\<程式碼基底>** 設定在電腦組態檔或發行者原則檔中，檔案也必須重新導向組件版本。</span><span class="sxs-lookup"><span data-stu-id="83ad6-136">For the runtime to use the **\<codeBase>** setting in a machine configuration file or publisher policy file, the file must also redirect the assembly version.</span></span> <span data-ttu-id="83ad6-137">應用程式組態檔可以有程式碼基底設定，不需要重新導向組件版本。</span><span class="sxs-lookup"><span data-stu-id="83ad6-137">Application configuration files can have a codebase setting without redirecting the assembly version.</span></span> <span data-ttu-id="83ad6-138">決定要使用的組件版本之後，執行階段適用於決定版本的檔案中的程式碼基底設定。</span><span class="sxs-lookup"><span data-stu-id="83ad6-138">After determining which assembly version to use, the runtime applies the codebase setting from the file that determines the version.</span></span> <span data-ttu-id="83ad6-139">如果沒有程式碼基底指示，執行階段會以一般方式探查組件。</span><span class="sxs-lookup"><span data-stu-id="83ad6-139">If no codebase is indicated, the runtime probes for the assembly in the usual way.</span></span>  
  
 <span data-ttu-id="83ad6-140">如果組件具有強式名稱，可以任何地方的程式碼基底設定是近端內部網路或網際網路上。</span><span class="sxs-lookup"><span data-stu-id="83ad6-140">If the assembly has a strong name, the codebase setting can be anywhere on the local intranet or the Internet.</span></span> <span data-ttu-id="83ad6-141">如果組件私用組件，程式碼基底設定必須是相對於應用程式的目錄路徑。</span><span class="sxs-lookup"><span data-stu-id="83ad6-141">If the assembly is a private assembly, the codebase setting must be a path relative to the application's directory.</span></span>  
  
 <span data-ttu-id="83ad6-142">針對沒有強式名稱的組件，則會忽略版本和載入器會使用的第一個出現\<程式碼基底 > 內\<dependentAssembly >。</span><span class="sxs-lookup"><span data-stu-id="83ad6-142">For assemblies without a strong name, version is ignored and the loader uses the first appearance of \<codebase> inside \<dependentAssembly>.</span></span> <span data-ttu-id="83ad6-143">如果應用程式組態檔，將繫結重新導向至另一個組件中沒有項目，重新導向將會優先，即使組件版本不符合繫結要求。</span><span class="sxs-lookup"><span data-stu-id="83ad6-143">If there is an entry in the application configuration file that redirects binding to another assembly, the redirection will take precedence even if the assembly version doesnt match the binding request.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83ad6-144">範例</span><span class="sxs-lookup"><span data-stu-id="83ad6-144">Example</span></span>  
 <span data-ttu-id="83ad6-145">下列範例示範如何指定執行階段可以在哪裡找到組件。</span><span class="sxs-lookup"><span data-stu-id="83ad6-145">The following example shows how to specify where the runtime can find an assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <codeBase version="2.0.0.0"  
                      href="http://www.litwareinc.com/myAssembly.dll"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="83ad6-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83ad6-146">See also</span></span>
- [<span data-ttu-id="83ad6-147">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="83ad6-147">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="83ad6-148">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="83ad6-148">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="83ad6-149">指定組件的位置</span><span class="sxs-lookup"><span data-stu-id="83ad6-149">Specifying an Assembly's Location</span></span>](../../../../../docs/framework/configure-apps/specify-assembly-location.md)
- [<span data-ttu-id="83ad6-150">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="83ad6-150">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
