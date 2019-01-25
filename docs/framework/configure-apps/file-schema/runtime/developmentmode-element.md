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
ms.openlocfilehash: 2f6a48a055d98a2f0b379df612da4e8fd49f3987
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54669090"
---
# <a name="ltdevelopmentmodegt-element"></a><span data-ttu-id="79e88-102">&lt;developmentMode&gt;項目</span><span class="sxs-lookup"><span data-stu-id="79e88-102">&lt;developmentMode&gt; Element</span></span>
<span data-ttu-id="79e88-103">指定執行階段是否要在 DEVPATH 環境變數所指定的目錄中搜尋組件。</span><span class="sxs-lookup"><span data-stu-id="79e88-103">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
 <span data-ttu-id="79e88-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="79e88-104">\<configuration></span></span>  
<span data-ttu-id="79e88-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="79e88-105">\<runtime></span></span>  
<span data-ttu-id="79e88-106">\<developmentMode></span><span class="sxs-lookup"><span data-stu-id="79e88-106">\<developmentMode></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79e88-107">語法</span><span class="sxs-lookup"><span data-stu-id="79e88-107">Syntax</span></span>  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="79e88-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="79e88-108">Attributes and Elements</span></span>  
 <span data-ttu-id="79e88-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="79e88-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="79e88-110">屬性</span><span class="sxs-lookup"><span data-stu-id="79e88-110">Attributes</span></span>  
  
|<span data-ttu-id="79e88-111">屬性</span><span class="sxs-lookup"><span data-stu-id="79e88-111">Attribute</span></span>|<span data-ttu-id="79e88-112">描述</span><span class="sxs-lookup"><span data-stu-id="79e88-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="79e88-113">**developerInstallation**</span><span class="sxs-lookup"><span data-stu-id="79e88-113">**developerInstallation**</span></span>|<span data-ttu-id="79e88-114">指定執行階段是否要在 DEVPATH 環境變數所指定的目錄中搜尋組件。</span><span class="sxs-lookup"><span data-stu-id="79e88-114">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
  
## <a name="developerinstallation-attribute"></a><span data-ttu-id="79e88-115">developerInstallation 屬性</span><span class="sxs-lookup"><span data-stu-id="79e88-115">developerInstallation Attribute</span></span>  
  
|<span data-ttu-id="79e88-116">值</span><span class="sxs-lookup"><span data-stu-id="79e88-116">Value</span></span>|<span data-ttu-id="79e88-117">描述</span><span class="sxs-lookup"><span data-stu-id="79e88-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="79e88-118">**true**</span><span class="sxs-lookup"><span data-stu-id="79e88-118">**true**</span></span>|<span data-ttu-id="79e88-119">DEVPATH 環境變數所指定的目錄中的組件的搜尋。</span><span class="sxs-lookup"><span data-stu-id="79e88-119">Searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
|<span data-ttu-id="79e88-120">**false**</span><span class="sxs-lookup"><span data-stu-id="79e88-120">**false**</span></span>|<span data-ttu-id="79e88-121">不會搜尋 DEVPATH 環境變數所指定的目錄中的組件。</span><span class="sxs-lookup"><span data-stu-id="79e88-121">Does not search for assemblies in directories specified by the DEVPATH environment variable.</span></span> <span data-ttu-id="79e88-122">這是預設值</span><span class="sxs-lookup"><span data-stu-id="79e88-122">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="79e88-123">子元素</span><span class="sxs-lookup"><span data-stu-id="79e88-123">Child Elements</span></span>  
 <span data-ttu-id="79e88-124">無。</span><span class="sxs-lookup"><span data-stu-id="79e88-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="79e88-125">父項目</span><span class="sxs-lookup"><span data-stu-id="79e88-125">Parent Elements</span></span>  
  
|<span data-ttu-id="79e88-126">項目</span><span class="sxs-lookup"><span data-stu-id="79e88-126">Element</span></span>|<span data-ttu-id="79e88-127">描述</span><span class="sxs-lookup"><span data-stu-id="79e88-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="79e88-128">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="79e88-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="79e88-129">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="79e88-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79e88-130">備註</span><span class="sxs-lookup"><span data-stu-id="79e88-130">Remarks</span></span>  
 <span data-ttu-id="79e88-131">使用此設定只在開發階段。</span><span class="sxs-lookup"><span data-stu-id="79e88-131">Use this setting only at development time.</span></span> <span data-ttu-id="79e88-132">執行階段不會檢查在 DEVPATH 中找到的強式名稱組件的版本。</span><span class="sxs-lookup"><span data-stu-id="79e88-132">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="79e88-133">它會直接使用第一個找到的組件。</span><span class="sxs-lookup"><span data-stu-id="79e88-133">It simply uses the first assembly it finds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79e88-134">範例</span><span class="sxs-lookup"><span data-stu-id="79e88-134">Example</span></span>  
 <span data-ttu-id="79e88-135">下列範例示範如何讓執行階段搜尋 DEVPATH 環境變數所指定的目錄中的組件。</span><span class="sxs-lookup"><span data-stu-id="79e88-135">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="79e88-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79e88-136">See also</span></span>
- [<span data-ttu-id="79e88-137">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="79e88-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="79e88-138">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="79e88-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="79e88-139">如何：使用 DEVPATH 找出組件</span><span class="sxs-lookup"><span data-stu-id="79e88-139">How to: Locate Assemblies by Using DEVPATH</span></span>](../../../../../docs/framework/configure-apps/how-to-locate-assemblies-by-using-devpath.md)
