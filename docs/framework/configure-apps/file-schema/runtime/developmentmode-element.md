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
ms.openlocfilehash: 4a062da31740edb8f0c7a4f4db8b09800c687587
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117624"
---
# <a name="developmentmode-element"></a><span data-ttu-id="6f645-102">\<developmentMode> 項目</span><span class="sxs-lookup"><span data-stu-id="6f645-102">\<developmentMode> Element</span></span>
<span data-ttu-id="6f645-103">指定執行階段是否要在 DEVPATH 環境變數所指定的目錄中搜尋組件。</span><span class="sxs-lookup"><span data-stu-id="6f645-103">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<developmentMode>**  
  
## <a name="syntax"></a><span data-ttu-id="6f645-104">語法</span><span class="sxs-lookup"><span data-stu-id="6f645-104">Syntax</span></span>  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f645-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6f645-105">Attributes and Elements</span></span>  
 <span data-ttu-id="6f645-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6f645-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f645-107">屬性</span><span class="sxs-lookup"><span data-stu-id="6f645-107">Attributes</span></span>  
  
|<span data-ttu-id="6f645-108">屬性</span><span class="sxs-lookup"><span data-stu-id="6f645-108">Attribute</span></span>|<span data-ttu-id="6f645-109">描述</span><span class="sxs-lookup"><span data-stu-id="6f645-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6f645-110">**developerInstallation**</span><span class="sxs-lookup"><span data-stu-id="6f645-110">**developerInstallation**</span></span>|<span data-ttu-id="6f645-111">指定執行階段是否要在 DEVPATH 環境變數所指定的目錄中搜尋組件。</span><span class="sxs-lookup"><span data-stu-id="6f645-111">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
  
## <a name="developerinstallation-attribute"></a><span data-ttu-id="6f645-112">developerInstallation 屬性</span><span class="sxs-lookup"><span data-stu-id="6f645-112">developerInstallation Attribute</span></span>  
  
|<span data-ttu-id="6f645-113">值</span><span class="sxs-lookup"><span data-stu-id="6f645-113">Value</span></span>|<span data-ttu-id="6f645-114">描述</span><span class="sxs-lookup"><span data-stu-id="6f645-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6f645-115">**true**</span><span class="sxs-lookup"><span data-stu-id="6f645-115">**true**</span></span>|<span data-ttu-id="6f645-116">在 DEVPATH 環境變數所指定的目錄中搜尋元件。</span><span class="sxs-lookup"><span data-stu-id="6f645-116">Searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
|<span data-ttu-id="6f645-117">**false**</span><span class="sxs-lookup"><span data-stu-id="6f645-117">**false**</span></span>|<span data-ttu-id="6f645-118">不會在 DEVPATH 環境變數所指定的目錄中搜尋元件。</span><span class="sxs-lookup"><span data-stu-id="6f645-118">Does not search for assemblies in directories specified by the DEVPATH environment variable.</span></span> <span data-ttu-id="6f645-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="6f645-119">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6f645-120">子元素</span><span class="sxs-lookup"><span data-stu-id="6f645-120">Child Elements</span></span>  
 <span data-ttu-id="6f645-121">無。</span><span class="sxs-lookup"><span data-stu-id="6f645-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6f645-122">父項目</span><span class="sxs-lookup"><span data-stu-id="6f645-122">Parent Elements</span></span>  
  
|<span data-ttu-id="6f645-123">元素</span><span class="sxs-lookup"><span data-stu-id="6f645-123">Element</span></span>|<span data-ttu-id="6f645-124">描述</span><span class="sxs-lookup"><span data-stu-id="6f645-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6f645-125">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="6f645-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="6f645-126">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="6f645-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f645-127">備註</span><span class="sxs-lookup"><span data-stu-id="6f645-127">Remarks</span></span>  
 <span data-ttu-id="6f645-128">請只在開發階段使用此設定。</span><span class="sxs-lookup"><span data-stu-id="6f645-128">Use this setting only at development time.</span></span> <span data-ttu-id="6f645-129">執行時間不會檢查在 DEVPATH 中找到的強式名稱元件上的版本。</span><span class="sxs-lookup"><span data-stu-id="6f645-129">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="6f645-130">它只會使用所找到的第一個元件。</span><span class="sxs-lookup"><span data-stu-id="6f645-130">It simply uses the first assembly it finds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f645-131">範例</span><span class="sxs-lookup"><span data-stu-id="6f645-131">Example</span></span>  
 <span data-ttu-id="6f645-132">下列範例顯示如何讓執行時間在 DEVPATH 環境變數所指定的目錄中搜尋元件。</span><span class="sxs-lookup"><span data-stu-id="6f645-132">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6f645-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f645-133">See also</span></span>

- [<span data-ttu-id="6f645-134">執行時間設定架構</span><span class="sxs-lookup"><span data-stu-id="6f645-134">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6f645-135">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="6f645-135">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="6f645-136">作法：使用 DEVPATH 找出組件</span><span class="sxs-lookup"><span data-stu-id="6f645-136">How to: Locate Assemblies by Using DEVPATH</span></span>](../../how-to-locate-assemblies-by-using-devpath.md)
