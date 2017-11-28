---
title: "&lt;qualifyAssembly&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#qualifyAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/qualifyAssembly
helpviewer_keywords:
- container tags, <qualifyAssembly> element
- <qualifyAssembly> element
- qualifyAssembly element
ms.assetid: ad6442f6-1a9d-43b6-b733-04ac1b7f9b82
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 521bbccd83f224cc824dae41309715d65472454e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltqualifyassemblygt-element"></a><span data-ttu-id="ff18a-102">&lt;qualifyAssembly&gt;項目</span><span class="sxs-lookup"><span data-stu-id="ff18a-102">&lt;qualifyAssembly&gt; Element</span></span>
<span data-ttu-id="ff18a-103">指定應該在使用部分名稱時以動態方式載入的組件的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="ff18a-103">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>  
  
 <span data-ttu-id="ff18a-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="ff18a-104">\<configuration></span></span>  
<span data-ttu-id="ff18a-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="ff18a-105">\<runtime></span></span>  
<span data-ttu-id="ff18a-106">\<assemblyBinding ></span><span class="sxs-lookup"><span data-stu-id="ff18a-106">\<assemblyBinding></span></span>  
<span data-ttu-id="ff18a-107">\<qualifyAssembly ></span><span class="sxs-lookup"><span data-stu-id="ff18a-107">\<qualifyAssembly></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff18a-108">語法</span><span class="sxs-lookup"><span data-stu-id="ff18a-108">Syntax</span></span>  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff18a-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ff18a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ff18a-110">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ff18a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff18a-111">屬性</span><span class="sxs-lookup"><span data-stu-id="ff18a-111">Attributes</span></span>  
  
|<span data-ttu-id="ff18a-112">屬性</span><span class="sxs-lookup"><span data-stu-id="ff18a-112">Attribute</span></span>|<span data-ttu-id="ff18a-113">描述</span><span class="sxs-lookup"><span data-stu-id="ff18a-113">Description</span></span>|  
|---------------|-----------------|  
|`partialName`|<span data-ttu-id="ff18a-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="ff18a-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="ff18a-115">指定出現在程式碼中的組件部分的名稱。</span><span class="sxs-lookup"><span data-stu-id="ff18a-115">Specifies the partial name of the assembly as it appears in the code.</span></span>|  
|`fullName`|<span data-ttu-id="ff18a-116">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="ff18a-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="ff18a-117">指定出現在全域組件快取中的組件的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="ff18a-117">Specifies the full name of the assembly as it appears in the global assembly cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ff18a-118">子元素</span><span class="sxs-lookup"><span data-stu-id="ff18a-118">Child Elements</span></span>  
 <span data-ttu-id="ff18a-119">無。</span><span class="sxs-lookup"><span data-stu-id="ff18a-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ff18a-120">父項目</span><span class="sxs-lookup"><span data-stu-id="ff18a-120">Parent Elements</span></span>  
  
|<span data-ttu-id="ff18a-121">項目</span><span class="sxs-lookup"><span data-stu-id="ff18a-121">Element</span></span>|<span data-ttu-id="ff18a-122">說明</span><span class="sxs-lookup"><span data-stu-id="ff18a-122">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="ff18a-123">包含有關組件版本重新導向和組件位置的資訊。</span><span class="sxs-lookup"><span data-stu-id="ff18a-123">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="ff18a-124">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="ff18a-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ff18a-125">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="ff18a-125">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff18a-126">備註</span><span class="sxs-lookup"><span data-stu-id="ff18a-126">Remarks</span></span>  
 <span data-ttu-id="ff18a-127">呼叫<xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>使用部分的組件名稱的方法會導致 common language runtime 的組件只能在應用程式基底目錄中尋找。</span><span class="sxs-lookup"><span data-stu-id="ff18a-127">Calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method using partial assembly names causes the common language runtime to look for the assembly only in the application base directory.</span></span> <span data-ttu-id="ff18a-128">使用 **\<qualifyAssembly >**應用程式組態檔中提供完整的組件資訊 （名稱、 版本、 公開金鑰語彙基元和文化特性），而造成 common language runtime 来搜尋的項目全域組件快取中的組件。</span><span class="sxs-lookup"><span data-stu-id="ff18a-128">Use the **\<qualifyAssembly>** element in your application configuration file to provide the full assembly information (name, version, public key token, and culture) and cause the common language runtime to search for the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="ff18a-129">**FullName**屬性必須包含組件識別四個欄位： 名稱、 版本、 公開金鑰語彙基元和文化特性。</span><span class="sxs-lookup"><span data-stu-id="ff18a-129">The **fullName** attribute must include the four fields of assembly identity: name, version, public key token, and culture.</span></span> <span data-ttu-id="ff18a-130">**PartialName**屬性部分必須參考的組件。</span><span class="sxs-lookup"><span data-stu-id="ff18a-130">The **partialName** attribute must partially reference an assembly.</span></span> <span data-ttu-id="ff18a-131">您至少必須指定組件的文字名稱 （最常見的情況），但您也可以包含版本、 公開金鑰語彙基元或文化特性 （或任何組合的四個，但是並非所有的四個欄位）。</span><span class="sxs-lookup"><span data-stu-id="ff18a-131">You must specify at least the assembly's text name (the most common case), but you can also include version, public key token, or culture (or any combination of the four, but not all four).</span></span> <span data-ttu-id="ff18a-132">**PartialName**必須符合您的呼叫中指定的名稱。</span><span class="sxs-lookup"><span data-stu-id="ff18a-132">The **partialName** must match the name specified in your call.</span></span> <span data-ttu-id="ff18a-133">例如，您無法指定`"math"`為**partialName**屬性在組態檔，並呼叫`Assembly.Load("math, Version=3.3.3.3")`程式碼中。</span><span class="sxs-lookup"><span data-stu-id="ff18a-133">For example, you cannot specify `"math"` as the **partialName** attribute in your configuration file and call `Assembly.Load("math, Version=3.3.3.3")` in your code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff18a-134">範例</span><span class="sxs-lookup"><span data-stu-id="ff18a-134">Example</span></span>  
 <span data-ttu-id="ff18a-135">下列範例邏輯上會呼叫`Assembly.Load("math")`到`Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`。</span><span class="sxs-lookup"><span data-stu-id="ff18a-135">The following example logically turns the call `Assembly.Load("math")` into `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <qualifyAssembly partialName="math"   
                         fullName=  
"math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ff18a-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff18a-136">See Also</span></span>  
 [<span data-ttu-id="ff18a-137">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="ff18a-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="ff18a-138">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="ff18a-138">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="ff18a-139">NIB： 部分組件參考</span><span class="sxs-lookup"><span data-stu-id="ff18a-139">NIB: Partial Assembly References</span></span>](http://msdn.microsoft.com/en-us/ec90f07a-398c-4306-9401-0fc5ff9cb59f)
