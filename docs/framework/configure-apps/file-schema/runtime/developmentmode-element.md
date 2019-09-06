---
title: <developmentMode> 項目
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
ms.openlocfilehash: 0253c3ced52b575097fe5d18abb8ce188c0164fb
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252688"
---
# <a name="developmentmode-element"></a><span data-ttu-id="64408-102">\<developmentMode > 元素</span><span class="sxs-lookup"><span data-stu-id="64408-102">\<developmentMode> Element</span></span>
<span data-ttu-id="64408-103">指定執行階段是否要在 DEVPATH 環境變數所指定的目錄中搜尋組件。</span><span class="sxs-lookup"><span data-stu-id="64408-103">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
<span data-ttu-id="64408-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="64408-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="64408-105">&nbsp;&nbsp;[ **\<執行時間 >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="64408-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="64408-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<developmentMode>**</span><span class="sxs-lookup"><span data-stu-id="64408-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<developmentMode>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64408-107">語法</span><span class="sxs-lookup"><span data-stu-id="64408-107">Syntax</span></span>  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="64408-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="64408-108">Attributes and Elements</span></span>  
 <span data-ttu-id="64408-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="64408-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="64408-110">屬性</span><span class="sxs-lookup"><span data-stu-id="64408-110">Attributes</span></span>  
  
|<span data-ttu-id="64408-111">屬性</span><span class="sxs-lookup"><span data-stu-id="64408-111">Attribute</span></span>|<span data-ttu-id="64408-112">描述</span><span class="sxs-lookup"><span data-stu-id="64408-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="64408-113">**developerInstallation**</span><span class="sxs-lookup"><span data-stu-id="64408-113">**developerInstallation**</span></span>|<span data-ttu-id="64408-114">指定執行階段是否要在 DEVPATH 環境變數所指定的目錄中搜尋組件。</span><span class="sxs-lookup"><span data-stu-id="64408-114">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
  
## <a name="developerinstallation-attribute"></a><span data-ttu-id="64408-115">developerInstallation 屬性</span><span class="sxs-lookup"><span data-stu-id="64408-115">developerInstallation Attribute</span></span>  
  
|<span data-ttu-id="64408-116">值</span><span class="sxs-lookup"><span data-stu-id="64408-116">Value</span></span>|<span data-ttu-id="64408-117">描述</span><span class="sxs-lookup"><span data-stu-id="64408-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="64408-118">**true**</span><span class="sxs-lookup"><span data-stu-id="64408-118">**true**</span></span>|<span data-ttu-id="64408-119">在 DEVPATH 環境變數所指定的目錄中搜尋元件。</span><span class="sxs-lookup"><span data-stu-id="64408-119">Searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
|<span data-ttu-id="64408-120">**false**</span><span class="sxs-lookup"><span data-stu-id="64408-120">**false**</span></span>|<span data-ttu-id="64408-121">不會在 DEVPATH 環境變數所指定的目錄中搜尋元件。</span><span class="sxs-lookup"><span data-stu-id="64408-121">Does not search for assemblies in directories specified by the DEVPATH environment variable.</span></span> <span data-ttu-id="64408-122">這是預設值</span><span class="sxs-lookup"><span data-stu-id="64408-122">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="64408-123">子元素</span><span class="sxs-lookup"><span data-stu-id="64408-123">Child Elements</span></span>  
 <span data-ttu-id="64408-124">無。</span><span class="sxs-lookup"><span data-stu-id="64408-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="64408-125">父項目</span><span class="sxs-lookup"><span data-stu-id="64408-125">Parent Elements</span></span>  
  
|<span data-ttu-id="64408-126">項目</span><span class="sxs-lookup"><span data-stu-id="64408-126">Element</span></span>|<span data-ttu-id="64408-127">說明</span><span class="sxs-lookup"><span data-stu-id="64408-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="64408-128">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="64408-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="64408-129">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="64408-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64408-130">備註</span><span class="sxs-lookup"><span data-stu-id="64408-130">Remarks</span></span>  
 <span data-ttu-id="64408-131">請只在開發階段使用此設定。</span><span class="sxs-lookup"><span data-stu-id="64408-131">Use this setting only at development time.</span></span> <span data-ttu-id="64408-132">執行時間不會檢查在 DEVPATH 中找到的強式名稱元件上的版本。</span><span class="sxs-lookup"><span data-stu-id="64408-132">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="64408-133">它只會使用所找到的第一個元件。</span><span class="sxs-lookup"><span data-stu-id="64408-133">It simply uses the first assembly it finds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64408-134">範例</span><span class="sxs-lookup"><span data-stu-id="64408-134">Example</span></span>  
 <span data-ttu-id="64408-135">下列範例顯示如何讓執行時間在 DEVPATH 環境變數所指定的目錄中搜尋元件。</span><span class="sxs-lookup"><span data-stu-id="64408-135">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="64408-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64408-136">See also</span></span>

- [<span data-ttu-id="64408-137">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="64408-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="64408-138">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="64408-138">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="64408-139">如何：使用 DEVPATH 找出元件</span><span class="sxs-lookup"><span data-stu-id="64408-139">How to: Locate Assemblies by Using DEVPATH</span></span>](../../how-to-locate-assemblies-by-using-devpath.md)
