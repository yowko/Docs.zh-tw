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
ms.openlocfilehash: 26b265996a059d8e52901557603bcf5e7636e596
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195216"
---
# <a name="qualifyassembly-element"></a><span data-ttu-id="87f2d-102">\<qualifyAssembly> 項目</span><span class="sxs-lookup"><span data-stu-id="87f2d-102">\<qualifyAssembly> Element</span></span>

<span data-ttu-id="87f2d-103">指定應該在使用部分名稱時以動態方式載入的組件的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="87f2d-103">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<qualifyAssembly>**  
  
## <a name="syntax"></a><span data-ttu-id="87f2d-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="87f2d-104">Syntax</span></span>  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87f2d-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="87f2d-105">Attributes and Elements</span></span>  

 <span data-ttu-id="87f2d-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="87f2d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87f2d-107">屬性</span><span class="sxs-lookup"><span data-stu-id="87f2d-107">Attributes</span></span>  
  
|<span data-ttu-id="87f2d-108">屬性</span><span class="sxs-lookup"><span data-stu-id="87f2d-108">Attribute</span></span>|<span data-ttu-id="87f2d-109">描述</span><span class="sxs-lookup"><span data-stu-id="87f2d-109">Description</span></span>|  
|---------------|-----------------|  
|`partialName`|<span data-ttu-id="87f2d-110">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="87f2d-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="87f2d-111">指定元件在程式碼中顯示的部分名稱。</span><span class="sxs-lookup"><span data-stu-id="87f2d-111">Specifies the partial name of the assembly as it appears in the code.</span></span>|  
|`fullName`|<span data-ttu-id="87f2d-112">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="87f2d-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="87f2d-113">指定元件在全域組件快取中所顯示的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="87f2d-113">Specifies the full name of the assembly as it appears in the global assembly cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="87f2d-114">子元素</span><span class="sxs-lookup"><span data-stu-id="87f2d-114">Child Elements</span></span>  

 <span data-ttu-id="87f2d-115">無。</span><span class="sxs-lookup"><span data-stu-id="87f2d-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="87f2d-116">父項目</span><span class="sxs-lookup"><span data-stu-id="87f2d-116">Parent Elements</span></span>  
  
|<span data-ttu-id="87f2d-117">項目</span><span class="sxs-lookup"><span data-stu-id="87f2d-117">Element</span></span>|<span data-ttu-id="87f2d-118">描述</span><span class="sxs-lookup"><span data-stu-id="87f2d-118">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="87f2d-119">包含有關組件版本重新導向和組件位置的資訊。</span><span class="sxs-lookup"><span data-stu-id="87f2d-119">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="87f2d-120">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="87f2d-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="87f2d-121">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="87f2d-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87f2d-122">備註</span><span class="sxs-lookup"><span data-stu-id="87f2d-122">Remarks</span></span>  

 <span data-ttu-id="87f2d-123"><xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>使用部分元件名稱呼叫方法會導致 common language runtime 只在應用程式基底目錄中尋找元件。</span><span class="sxs-lookup"><span data-stu-id="87f2d-123">Calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method using partial assembly names causes the common language runtime to look for the assembly only in the application base directory.</span></span> <span data-ttu-id="87f2d-124">**\<qualifyAssembly>** 您可以使用應用程式佈建檔中的專案，提供完整的元件資訊 (名稱、版本、公開金鑰 token 和文化特性) ，並導致 common language runtime 搜尋全域組件快取中的元件。</span><span class="sxs-lookup"><span data-stu-id="87f2d-124">Use the **\<qualifyAssembly>** element in your application configuration file to provide the full assembly information (name, version, public key token, and culture) and cause the common language runtime to search for the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="87f2d-125">**FullName**屬性必須包含元件身分識別的四個欄位：名稱、版本、公開金鑰 token 和文化特性。</span><span class="sxs-lookup"><span data-stu-id="87f2d-125">The **fullName** attribute must include the four fields of assembly identity: name, version, public key token, and culture.</span></span> <span data-ttu-id="87f2d-126">**PartialName**屬性必須部分參考元件。</span><span class="sxs-lookup"><span data-stu-id="87f2d-126">The **partialName** attribute must partially reference an assembly.</span></span> <span data-ttu-id="87f2d-127">您必須至少指定元件的文字名稱 (最常見的案例) ，但您也可以包含版本、公開金鑰 token 或文化特性 (或四個的任意組合，而不是全部四個) 。</span><span class="sxs-lookup"><span data-stu-id="87f2d-127">You must specify at least the assembly's text name (the most common case), but you can also include version, public key token, or culture (or any combination of the four, but not all four).</span></span> <span data-ttu-id="87f2d-128">**PartialName**必須符合您在呼叫中指定的名稱。</span><span class="sxs-lookup"><span data-stu-id="87f2d-128">The **partialName** must match the name specified in your call.</span></span> <span data-ttu-id="87f2d-129">例如，您不能在 `"math"` 設定檔中指定作為 **partialName** 屬性，然後 `Assembly.Load("math, Version=3.3.3.3")` 在程式碼中呼叫。</span><span class="sxs-lookup"><span data-stu-id="87f2d-129">For example, you cannot specify `"math"` as the **partialName** attribute in your configuration file and call `Assembly.Load("math, Version=3.3.3.3")` in your code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87f2d-130">範例</span><span class="sxs-lookup"><span data-stu-id="87f2d-130">Example</span></span>  

 <span data-ttu-id="87f2d-131">下列範例會以邏輯方式開啟的呼叫 `Assembly.Load("math")` `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")` 。</span><span class="sxs-lookup"><span data-stu-id="87f2d-131">The following example logically turns the call `Assembly.Load("math")` into `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="87f2d-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87f2d-132">See also</span></span>

- [<span data-ttu-id="87f2d-133">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="87f2d-133">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="87f2d-134">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="87f2d-134">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- <span data-ttu-id="87f2d-135">[部分組件參考](/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="87f2d-135">[Partial Assembly References](/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span></span>
