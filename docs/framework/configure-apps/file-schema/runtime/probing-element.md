---
title: <probing> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/probing
- http://schemas.microsoft.com/.NetConfiguration/v2.0#probing
helpviewer_keywords:
- <probing> element
- container tags, <probing> element
- probing element
ms.assetid: 09c80fc9-1ba5-4192-89f7-3a79b2e4b024
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 05634cb319ac69bd76e16e592ba59490b30c9c9d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252391"
---
# <a name="probing-element"></a><span data-ttu-id="f4d73-102">\<探查 > 元素</span><span class="sxs-lookup"><span data-stu-id="f4d73-102">\<probing> Element</span></span>
<span data-ttu-id="f4d73-103">指定載入元件時，common language runtime 要搜尋的應用程式基底子目錄。</span><span class="sxs-lookup"><span data-stu-id="f4d73-103">Specifies application base subdirectories for the common language runtime to search when loading assemblies.</span></span>  
  
<span data-ttu-id="f4d73-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f4d73-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f4d73-105">&nbsp;&nbsp;[ **\<執行時間 >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="f4d73-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="f4d73-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<assemblyBinding >** ](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="f4d73-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="f4d73-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<探查 >**</span><span class="sxs-lookup"><span data-stu-id="f4d73-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<probing>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4d73-108">語法</span><span class="sxs-lookup"><span data-stu-id="f4d73-108">Syntax</span></span>  
  
```xml  
<probing privatePath="paths"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f4d73-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f4d73-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f4d73-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f4d73-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f4d73-111">屬性</span><span class="sxs-lookup"><span data-stu-id="f4d73-111">Attributes</span></span>  
  
|<span data-ttu-id="f4d73-112">屬性</span><span class="sxs-lookup"><span data-stu-id="f4d73-112">Attribute</span></span>|<span data-ttu-id="f4d73-113">描述</span><span class="sxs-lookup"><span data-stu-id="f4d73-113">Description</span></span>|  
|---------------|-----------------|  
|`privatePath`|<span data-ttu-id="f4d73-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="f4d73-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="f4d73-115">指定可能包含元件之應用程式基底目錄的子目錄。</span><span class="sxs-lookup"><span data-stu-id="f4d73-115">Specifies subdirectories of the application's base directory that might contain assemblies.</span></span> <span data-ttu-id="f4d73-116">以分號分隔每個子目錄。</span><span class="sxs-lookup"><span data-stu-id="f4d73-116">Delimit each subdirectory with a semicolon.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f4d73-117">子元素</span><span class="sxs-lookup"><span data-stu-id="f4d73-117">Child Elements</span></span>  

<span data-ttu-id="f4d73-118">無。</span><span class="sxs-lookup"><span data-stu-id="f4d73-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f4d73-119">父項目</span><span class="sxs-lookup"><span data-stu-id="f4d73-119">Parent Elements</span></span>  
  
|<span data-ttu-id="f4d73-120">項目</span><span class="sxs-lookup"><span data-stu-id="f4d73-120">Element</span></span>|<span data-ttu-id="f4d73-121">說明</span><span class="sxs-lookup"><span data-stu-id="f4d73-121">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="f4d73-122">包含有關組件版本重新導向和組件位置的資訊。</span><span class="sxs-lookup"><span data-stu-id="f4d73-122">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="f4d73-123">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="f4d73-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="f4d73-124">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="f4d73-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f4d73-125">範例</span><span class="sxs-lookup"><span data-stu-id="f4d73-125">Example</span></span>  
 <span data-ttu-id="f4d73-126">下列範例顯示如何指定執行時間應該搜尋元件的應用程式基底子目錄。</span><span class="sxs-lookup"><span data-stu-id="f4d73-126">The following example shows how to specify application base subdirectories the runtime should search for assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f4d73-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4d73-127">See also</span></span>

- [<span data-ttu-id="f4d73-128">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="f4d73-128">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="f4d73-129">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="f4d73-129">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="f4d73-130">指定組件的位置</span><span class="sxs-lookup"><span data-stu-id="f4d73-130">Specifying an Assembly's Location</span></span>](../../specify-assembly-location.md)
- [<span data-ttu-id="f4d73-131">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="f4d73-131">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
