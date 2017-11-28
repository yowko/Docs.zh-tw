---
title: "&lt;探查&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/probing
- http://schemas.microsoft.com/.NetConfiguration/v2.0#probing
helpviewer_keywords:
- <probing> element
- container tags, <probing> element
- probing element
ms.assetid: 09c80fc9-1ba5-4192-89f7-3a79b2e4b024
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7dd829fbbfbaa6f26b59e26d5a8b1d2b36593f57
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltprobinggt-element"></a><span data-ttu-id="0258a-102">&lt;探查&gt;項目</span><span class="sxs-lookup"><span data-stu-id="0258a-102">&lt;probing&gt; Element</span></span>
<span data-ttu-id="0258a-103">指定 common language runtime 載入組件時所要搜尋的應用程式基底的子目錄。</span><span class="sxs-lookup"><span data-stu-id="0258a-103">Specifies application base subdirectories for the common language runtime to search when loading assemblies.</span></span>  
  
 <span data-ttu-id="0258a-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="0258a-104">\<configuration></span></span>  
<span data-ttu-id="0258a-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="0258a-105">\<runtime></span></span>  
<span data-ttu-id="0258a-106">\<assemblyBinding ></span><span class="sxs-lookup"><span data-stu-id="0258a-106">\<assemblyBinding></span></span>  
<span data-ttu-id="0258a-107">\<探查 ></span><span class="sxs-lookup"><span data-stu-id="0258a-107">\<probing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0258a-108">語法</span><span class="sxs-lookup"><span data-stu-id="0258a-108">Syntax</span></span>  
  
```xml  
<probing privatePath="paths"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0258a-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0258a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0258a-110">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0258a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0258a-111">屬性</span><span class="sxs-lookup"><span data-stu-id="0258a-111">Attributes</span></span>  
  
|<span data-ttu-id="0258a-112">屬性</span><span class="sxs-lookup"><span data-stu-id="0258a-112">Attribute</span></span>|<span data-ttu-id="0258a-113">描述</span><span class="sxs-lookup"><span data-stu-id="0258a-113">Description</span></span>|  
|---------------|-----------------|  
|`privatePath`|<span data-ttu-id="0258a-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="0258a-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="0258a-115">指定的應用程式可能包含組件的基底目錄的子目錄。</span><span class="sxs-lookup"><span data-stu-id="0258a-115">Specifies subdirectories of the application's base directory that might contain assemblies.</span></span> <span data-ttu-id="0258a-116">分隔每個以分號的子目錄。</span><span class="sxs-lookup"><span data-stu-id="0258a-116">Delimit each subdirectory with a semicolon.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0258a-117">子元素</span><span class="sxs-lookup"><span data-stu-id="0258a-117">Child Elements</span></span>  
 <span data-ttu-id="0258a-118">無。</span><span class="sxs-lookup"><span data-stu-id="0258a-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0258a-119">父項目</span><span class="sxs-lookup"><span data-stu-id="0258a-119">Parent Elements</span></span>  
  
|<span data-ttu-id="0258a-120">項目</span><span class="sxs-lookup"><span data-stu-id="0258a-120">Element</span></span>|<span data-ttu-id="0258a-121">說明</span><span class="sxs-lookup"><span data-stu-id="0258a-121">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="0258a-122">包含有關組件版本重新導向和組件位置的資訊。</span><span class="sxs-lookup"><span data-stu-id="0258a-122">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="0258a-123">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="0258a-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="0258a-124">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="0258a-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0258a-125">範例</span><span class="sxs-lookup"><span data-stu-id="0258a-125">Example</span></span>  
 <span data-ttu-id="0258a-126">下列範例會示範如何指定執行階段應該搜尋組件的應用程式基底子目錄。</span><span class="sxs-lookup"><span data-stu-id="0258a-126">The following example shows how to specify application base subdirectories the runtime should search for assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0258a-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0258a-127">See Also</span></span>  
 [<span data-ttu-id="0258a-128">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="0258a-128">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="0258a-129">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="0258a-129">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="0258a-130">指定組件的位置</span><span class="sxs-lookup"><span data-stu-id="0258a-130">Specifying an Assembly's Location</span></span>](../../../../../docs/framework/configure-apps/specify-assembly-location.md)  
 [<span data-ttu-id="0258a-131">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="0258a-131">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
