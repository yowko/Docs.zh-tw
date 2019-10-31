---
title: <qualifyAssembly> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#qualifyAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/qualifyAssembly
helpviewer_keywords:
- container tags, <qualifyAssembly> element
- <qualifyAssembly> element
- qualifyAssembly element
ms.assetid: ad6442f6-1a9d-43b6-b733-04ac1b7f9b82
ms.openlocfilehash: 17cfe9fc39d65f146beef5d02c701f5e3e2fbbe1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115776"
---
# <a name="qualifyassembly-element"></a><span data-ttu-id="40cc8-102">\<qualifyAssembly > 元素</span><span class="sxs-lookup"><span data-stu-id="40cc8-102">\<qualifyAssembly> Element</span></span>
<span data-ttu-id="40cc8-103">指定應該在使用部分名稱時以動態方式載入的組件的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="40cc8-103">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>  
  
<span data-ttu-id="40cc8-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="40cc8-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="40cc8-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="40cc8-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="40cc8-106">&nbsp; &nbsp; &nbsp; &nbsp;[ **\<assemblyBinding**](assemblybinding-element-for-runtime.md) > </span><span class="sxs-lookup"><span data-stu-id="40cc8-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="40cc8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<qualifyAssembly >**</span><span class="sxs-lookup"><span data-stu-id="40cc8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<qualifyAssembly>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40cc8-108">語法</span><span class="sxs-lookup"><span data-stu-id="40cc8-108">Syntax</span></span>  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="40cc8-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="40cc8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="40cc8-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="40cc8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="40cc8-111">屬性</span><span class="sxs-lookup"><span data-stu-id="40cc8-111">Attributes</span></span>  
  
|<span data-ttu-id="40cc8-112">屬性</span><span class="sxs-lookup"><span data-stu-id="40cc8-112">Attribute</span></span>|<span data-ttu-id="40cc8-113">描述</span><span class="sxs-lookup"><span data-stu-id="40cc8-113">Description</span></span>|  
|---------------|-----------------|  
|`partialName`|<span data-ttu-id="40cc8-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="40cc8-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="40cc8-115">指定元件出現在程式碼中的部分名稱。</span><span class="sxs-lookup"><span data-stu-id="40cc8-115">Specifies the partial name of the assembly as it appears in the code.</span></span>|  
|`fullName`|<span data-ttu-id="40cc8-116">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="40cc8-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="40cc8-117">指定元件出現在全域組件快取中的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="40cc8-117">Specifies the full name of the assembly as it appears in the global assembly cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="40cc8-118">子項目</span><span class="sxs-lookup"><span data-stu-id="40cc8-118">Child Elements</span></span>  
 <span data-ttu-id="40cc8-119">無。</span><span class="sxs-lookup"><span data-stu-id="40cc8-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="40cc8-120">父項目</span><span class="sxs-lookup"><span data-stu-id="40cc8-120">Parent Elements</span></span>  
  
|<span data-ttu-id="40cc8-121">項目</span><span class="sxs-lookup"><span data-stu-id="40cc8-121">Element</span></span>|<span data-ttu-id="40cc8-122">描述</span><span class="sxs-lookup"><span data-stu-id="40cc8-122">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="40cc8-123">包含有關組件版本重新導向和組件位置的資訊。</span><span class="sxs-lookup"><span data-stu-id="40cc8-123">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="40cc8-124">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="40cc8-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="40cc8-125">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="40cc8-125">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40cc8-126">備註</span><span class="sxs-lookup"><span data-stu-id="40cc8-126">Remarks</span></span>  
 <span data-ttu-id="40cc8-127">使用部分元件名稱呼叫 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> 方法，會導致 common language runtime 只在應用程式基底目錄中尋找元件。</span><span class="sxs-lookup"><span data-stu-id="40cc8-127">Calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method using partial assembly names causes the common language runtime to look for the assembly only in the application base directory.</span></span> <span data-ttu-id="40cc8-128">使用應用程式佈建檔中的 **\<qualifyAssembly >** 元素，以提供完整的元件資訊（名稱、版本、公開金鑰標記和文化特性），並導致 common language runtime 在全域中搜尋元件組件快取。</span><span class="sxs-lookup"><span data-stu-id="40cc8-128">Use the **\<qualifyAssembly>** element in your application configuration file to provide the full assembly information (name, version, public key token, and culture) and cause the common language runtime to search for the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="40cc8-129">**FullName**屬性必須包含元件識別的四個欄位：名稱、版本、公開金鑰標記和文化特性。</span><span class="sxs-lookup"><span data-stu-id="40cc8-129">The **fullName** attribute must include the four fields of assembly identity: name, version, public key token, and culture.</span></span> <span data-ttu-id="40cc8-130">**PartialName**屬性必須部分參考元件。</span><span class="sxs-lookup"><span data-stu-id="40cc8-130">The **partialName** attribute must partially reference an assembly.</span></span> <span data-ttu-id="40cc8-131">您至少必須指定元件的文字名稱（最常見的情況），但您也可以包含版本、公開金鑰標記或文化特性（或四個（但不是全部四個）的任何組合。</span><span class="sxs-lookup"><span data-stu-id="40cc8-131">You must specify at least the assembly's text name (the most common case), but you can also include version, public key token, or culture (or any combination of the four, but not all four).</span></span> <span data-ttu-id="40cc8-132">**PartialName**必須符合您的呼叫中所指定的名稱。</span><span class="sxs-lookup"><span data-stu-id="40cc8-132">The **partialName** must match the name specified in your call.</span></span> <span data-ttu-id="40cc8-133">例如，您無法將 `"math"` 指定為設定檔中的**partialName**屬性，並在您的程式碼中呼叫 `Assembly.Load("math, Version=3.3.3.3")`。</span><span class="sxs-lookup"><span data-stu-id="40cc8-133">For example, you cannot specify `"math"` as the **partialName** attribute in your configuration file and call `Assembly.Load("math, Version=3.3.3.3")` in your code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40cc8-134">範例</span><span class="sxs-lookup"><span data-stu-id="40cc8-134">Example</span></span>  
 <span data-ttu-id="40cc8-135">下列範例會以邏輯方式將呼叫 `Assembly.Load("math")` 變成 `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`。</span><span class="sxs-lookup"><span data-stu-id="40cc8-135">The following example logically turns the call `Assembly.Load("math")` into `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="40cc8-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="40cc8-136">See also</span></span>

- [<span data-ttu-id="40cc8-137">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="40cc8-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="40cc8-138">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="40cc8-138">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- <span data-ttu-id="40cc8-139">[部分元件參考](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="40cc8-139">[Partial Assembly References](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span></span>
