---
title: '&lt;developmentMode&gt;項目'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/developmentMode
- http://schemas.microsoft.com/.NetConfiguration/v2.0#developmentMode
helpviewer_keywords:
- developmentMode element
- container tags, <developmentMode> element
- <developmentMode> element
ms.assetid: 60e79a8c-415a-497d-be29-b9d0fd9bdee3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 982bc04e362f82760226b1cd2b8b3febe9cc7107
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612045"
---
# <a name="ltdevelopmentmodegt-element"></a><span data-ttu-id="93fa5-102">&lt;developmentMode&gt;項目</span><span class="sxs-lookup"><span data-stu-id="93fa5-102">&lt;developmentMode&gt; Element</span></span>
<span data-ttu-id="93fa5-103">指定執行階段是否要在 DEVPATH 環境變數所指定的目錄中搜尋組件。</span><span class="sxs-lookup"><span data-stu-id="93fa5-103">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
 <span data-ttu-id="93fa5-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="93fa5-104">\<configuration></span></span>  
<span data-ttu-id="93fa5-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="93fa5-105">\<runtime></span></span>  
<span data-ttu-id="93fa5-106">\<developmentMode ></span><span class="sxs-lookup"><span data-stu-id="93fa5-106">\<developmentMode></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93fa5-107">語法</span><span class="sxs-lookup"><span data-stu-id="93fa5-107">Syntax</span></span>  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="93fa5-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="93fa5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="93fa5-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="93fa5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="93fa5-110">屬性</span><span class="sxs-lookup"><span data-stu-id="93fa5-110">Attributes</span></span>  
  
|<span data-ttu-id="93fa5-111">屬性</span><span class="sxs-lookup"><span data-stu-id="93fa5-111">Attribute</span></span>|<span data-ttu-id="93fa5-112">描述</span><span class="sxs-lookup"><span data-stu-id="93fa5-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="93fa5-113">**developerInstallation**</span><span class="sxs-lookup"><span data-stu-id="93fa5-113">**developerInstallation**</span></span>|<span data-ttu-id="93fa5-114">指定執行階段是否要在 DEVPATH 環境變數所指定的目錄中搜尋組件。</span><span class="sxs-lookup"><span data-stu-id="93fa5-114">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
  
## <a name="developerinstallation-attribute"></a><span data-ttu-id="93fa5-115">developerInstallation 屬性</span><span class="sxs-lookup"><span data-stu-id="93fa5-115">developerInstallation Attribute</span></span>  
  
|<span data-ttu-id="93fa5-116">值</span><span class="sxs-lookup"><span data-stu-id="93fa5-116">Value</span></span>|<span data-ttu-id="93fa5-117">描述</span><span class="sxs-lookup"><span data-stu-id="93fa5-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="93fa5-118">**true**</span><span class="sxs-lookup"><span data-stu-id="93fa5-118">**true**</span></span>|<span data-ttu-id="93fa5-119">DEVPATH 環境變數所指定的目錄中的組件的搜尋。</span><span class="sxs-lookup"><span data-stu-id="93fa5-119">Searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
|<span data-ttu-id="93fa5-120">**false**</span><span class="sxs-lookup"><span data-stu-id="93fa5-120">**false**</span></span>|<span data-ttu-id="93fa5-121">不會搜尋 DEVPATH 環境變數所指定的目錄中的組件。</span><span class="sxs-lookup"><span data-stu-id="93fa5-121">Does not search for assemblies in directories specified by the DEVPATH environment variable.</span></span> <span data-ttu-id="93fa5-122">這是預設值</span><span class="sxs-lookup"><span data-stu-id="93fa5-122">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="93fa5-123">子元素</span><span class="sxs-lookup"><span data-stu-id="93fa5-123">Child Elements</span></span>  
 <span data-ttu-id="93fa5-124">無。</span><span class="sxs-lookup"><span data-stu-id="93fa5-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="93fa5-125">父項目</span><span class="sxs-lookup"><span data-stu-id="93fa5-125">Parent Elements</span></span>  
  
|<span data-ttu-id="93fa5-126">項目</span><span class="sxs-lookup"><span data-stu-id="93fa5-126">Element</span></span>|<span data-ttu-id="93fa5-127">描述</span><span class="sxs-lookup"><span data-stu-id="93fa5-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="93fa5-128">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="93fa5-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="93fa5-129">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="93fa5-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93fa5-130">備註</span><span class="sxs-lookup"><span data-stu-id="93fa5-130">Remarks</span></span>  
 <span data-ttu-id="93fa5-131">使用此設定只在開發階段。</span><span class="sxs-lookup"><span data-stu-id="93fa5-131">Use this setting only at development time.</span></span> <span data-ttu-id="93fa5-132">執行階段不會檢查在 DEVPATH 中找到的強式名稱組件的版本。</span><span class="sxs-lookup"><span data-stu-id="93fa5-132">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="93fa5-133">它會直接使用第一個找到的組件。</span><span class="sxs-lookup"><span data-stu-id="93fa5-133">It simply uses the first assembly it finds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93fa5-134">範例</span><span class="sxs-lookup"><span data-stu-id="93fa5-134">Example</span></span>  
 <span data-ttu-id="93fa5-135">下列範例示範如何讓執行階段搜尋 DEVPATH 環境變數所指定的目錄中的組件。</span><span class="sxs-lookup"><span data-stu-id="93fa5-135">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="93fa5-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93fa5-136">See Also</span></span>  
- [<span data-ttu-id="93fa5-137">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="93fa5-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [<span data-ttu-id="93fa5-138">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="93fa5-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [<span data-ttu-id="93fa5-139">如何：使用 DEVPATH 找出組件</span><span class="sxs-lookup"><span data-stu-id="93fa5-139">How to: Locate Assemblies by Using DEVPATH</span></span>](../../../../../docs/framework/configure-apps/how-to-locate-assemblies-by-using-devpath.md)
