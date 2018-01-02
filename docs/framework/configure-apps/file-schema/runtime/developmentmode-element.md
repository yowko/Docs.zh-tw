---
title: "&lt;developmentMode&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/developmentMode
- http://schemas.microsoft.com/.NetConfiguration/v2.0#developmentMode
helpviewer_keywords:
- developmentMode element
- container tags, <developmentMode> element
- <developmentMode> element
ms.assetid: 60e79a8c-415a-497d-be29-b9d0fd9bdee3
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a77f93a0dff198821509c2c26f67caa137073ced
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltdevelopmentmodegt-element"></a><span data-ttu-id="c4472-102">&lt;developmentMode&gt;項目</span><span class="sxs-lookup"><span data-stu-id="c4472-102">&lt;developmentMode&gt; Element</span></span>
<span data-ttu-id="c4472-103">指定執行階段是否要在 DEVPATH 環境變數所指定的目錄中搜尋組件。</span><span class="sxs-lookup"><span data-stu-id="c4472-103">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
 <span data-ttu-id="c4472-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="c4472-104">\<configuration></span></span>  
<span data-ttu-id="c4472-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="c4472-105">\<runtime></span></span>  
<span data-ttu-id="c4472-106">\<developmentMode ></span><span class="sxs-lookup"><span data-stu-id="c4472-106">\<developmentMode></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4472-107">語法</span><span class="sxs-lookup"><span data-stu-id="c4472-107">Syntax</span></span>  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c4472-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c4472-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c4472-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c4472-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c4472-110">屬性</span><span class="sxs-lookup"><span data-stu-id="c4472-110">Attributes</span></span>  
  
|<span data-ttu-id="c4472-111">屬性</span><span class="sxs-lookup"><span data-stu-id="c4472-111">Attribute</span></span>|<span data-ttu-id="c4472-112">描述</span><span class="sxs-lookup"><span data-stu-id="c4472-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c4472-113">**developerInstallation**</span><span class="sxs-lookup"><span data-stu-id="c4472-113">**developerInstallation**</span></span>|<span data-ttu-id="c4472-114">指定執行階段是否要在 DEVPATH 環境變數所指定的目錄中搜尋組件。</span><span class="sxs-lookup"><span data-stu-id="c4472-114">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
  
## <a name="developerinstallation-attribute"></a><span data-ttu-id="c4472-115">developerInstallation 屬性</span><span class="sxs-lookup"><span data-stu-id="c4472-115">developerInstallation Attribute</span></span>  
  
|<span data-ttu-id="c4472-116">值</span><span class="sxs-lookup"><span data-stu-id="c4472-116">Value</span></span>|<span data-ttu-id="c4472-117">描述</span><span class="sxs-lookup"><span data-stu-id="c4472-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c4472-118">**true**</span><span class="sxs-lookup"><span data-stu-id="c4472-118">**true**</span></span>|<span data-ttu-id="c4472-119">搜尋 DEVPATH 環境變數所指定的目錄中的組件。</span><span class="sxs-lookup"><span data-stu-id="c4472-119">Searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
|<span data-ttu-id="c4472-120">**false**</span><span class="sxs-lookup"><span data-stu-id="c4472-120">**false**</span></span>|<span data-ttu-id="c4472-121">不會搜尋 DEVPATH 環境變數所指定的目錄中的組件。</span><span class="sxs-lookup"><span data-stu-id="c4472-121">Does not search for assemblies in directories specified by the DEVPATH environment variable.</span></span> <span data-ttu-id="c4472-122">這是預設值</span><span class="sxs-lookup"><span data-stu-id="c4472-122">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c4472-123">子元素</span><span class="sxs-lookup"><span data-stu-id="c4472-123">Child Elements</span></span>  
 <span data-ttu-id="c4472-124">無。</span><span class="sxs-lookup"><span data-stu-id="c4472-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c4472-125">父項目</span><span class="sxs-lookup"><span data-stu-id="c4472-125">Parent Elements</span></span>  
  
|<span data-ttu-id="c4472-126">項目</span><span class="sxs-lookup"><span data-stu-id="c4472-126">Element</span></span>|<span data-ttu-id="c4472-127">描述</span><span class="sxs-lookup"><span data-stu-id="c4472-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c4472-128">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="c4472-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="c4472-129">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="c4472-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4472-130">備註</span><span class="sxs-lookup"><span data-stu-id="c4472-130">Remarks</span></span>  
 <span data-ttu-id="c4472-131">使用此設定只在開發階段。</span><span class="sxs-lookup"><span data-stu-id="c4472-131">Use this setting only at development time.</span></span> <span data-ttu-id="c4472-132">執行階段不會檢查 DEVPATH 中找到的強式名稱組件上的版本。</span><span class="sxs-lookup"><span data-stu-id="c4472-132">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="c4472-133">它只會使用第一個找到的組件。</span><span class="sxs-lookup"><span data-stu-id="c4472-133">It simply uses the first assembly it finds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4472-134">範例</span><span class="sxs-lookup"><span data-stu-id="c4472-134">Example</span></span>  
 <span data-ttu-id="c4472-135">下列範例會示範如何使執行階段 DEVPATH 環境變數所指定的目錄中搜尋組件。</span><span class="sxs-lookup"><span data-stu-id="c4472-135">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c4472-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="c4472-136">See Also</span></span>  
 [<span data-ttu-id="c4472-137">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="c4472-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="c4472-138">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="c4472-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="c4472-139">如何：使用 DEVPATH 找出組件</span><span class="sxs-lookup"><span data-stu-id="c4472-139">How to: Locate Assemblies by Using DEVPATH</span></span>](../../../../../docs/framework/configure-apps/how-to-locate-assemblies-by-using-devpath.md)
