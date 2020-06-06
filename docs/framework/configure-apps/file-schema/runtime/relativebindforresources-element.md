---
title: <relativeBindForResources> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
ms.openlocfilehash: cd49d424019a4e8422fee0ae16217d49cfc456b1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153902"
---
# <a name="relativebindforresources-element"></a><span data-ttu-id="aba2a-102">\<relativeBindForResources> 項目</span><span class="sxs-lookup"><span data-stu-id="aba2a-102">\<relativeBindForResources> Element</span></span>
<span data-ttu-id="aba2a-103">最佳化附屬組件的探查。</span><span class="sxs-lookup"><span data-stu-id="aba2a-103">Optimizes the probe for satellite assemblies.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<relativeBindForResources>**  
  
## <a name="syntax"></a><span data-ttu-id="aba2a-104">語法</span><span class="sxs-lookup"><span data-stu-id="aba2a-104">Syntax</span></span>  
  
```xml
<relativeBindForResources
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aba2a-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="aba2a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="aba2a-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="aba2a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aba2a-107">屬性</span><span class="sxs-lookup"><span data-stu-id="aba2a-107">Attributes</span></span>  
  
|<span data-ttu-id="aba2a-108">屬性</span><span class="sxs-lookup"><span data-stu-id="aba2a-108">Attribute</span></span>|<span data-ttu-id="aba2a-109">描述</span><span class="sxs-lookup"><span data-stu-id="aba2a-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="aba2a-110">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="aba2a-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="aba2a-111">指定通用語言執行時間是否要優化附屬元件的探查。</span><span class="sxs-lookup"><span data-stu-id="aba2a-111">Specifies whether the common language runtime optimizes the probe for satellite assemblies.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="aba2a-112">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="aba2a-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="aba2a-113">值</span><span class="sxs-lookup"><span data-stu-id="aba2a-113">Value</span></span>|<span data-ttu-id="aba2a-114">描述</span><span class="sxs-lookup"><span data-stu-id="aba2a-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="aba2a-115">執行時間不會優化附屬元件的探查。</span><span class="sxs-lookup"><span data-stu-id="aba2a-115">The runtime does not optimize the probe for satellite assemblies.</span></span> <span data-ttu-id="aba2a-116">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="aba2a-116">This is the default value.</span></span>|  
|`true`|<span data-ttu-id="aba2a-117">執行時間會優化附屬元件的探查。</span><span class="sxs-lookup"><span data-stu-id="aba2a-117">The runtime optimizes the probe for satellite assemblies.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aba2a-118">子元素</span><span class="sxs-lookup"><span data-stu-id="aba2a-118">Child Elements</span></span>  
 <span data-ttu-id="aba2a-119">無。</span><span class="sxs-lookup"><span data-stu-id="aba2a-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aba2a-120">父項目</span><span class="sxs-lookup"><span data-stu-id="aba2a-120">Parent Elements</span></span>  
  
|<span data-ttu-id="aba2a-121">元素</span><span class="sxs-lookup"><span data-stu-id="aba2a-121">Element</span></span>|<span data-ttu-id="aba2a-122">描述</span><span class="sxs-lookup"><span data-stu-id="aba2a-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="aba2a-123">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="aba2a-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="aba2a-124">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="aba2a-124">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aba2a-125">備註</span><span class="sxs-lookup"><span data-stu-id="aba2a-125">Remarks</span></span>  
 <span data-ttu-id="aba2a-126">一般來說，Resource Manager 會探查資源，如[封裝和部署資源](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)主題中所述。</span><span class="sxs-lookup"><span data-stu-id="aba2a-126">In general, Resource Manager probes for resources, as documented in the [Packaging and Deploying Resources](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) topic.</span></span> <span data-ttu-id="aba2a-127">這表示當 Resource Manager 探查特定當地語系化版本的資源時，它可能會查看全域組件快取、在應用程式的程式碼基底中尋找特定文化特性的資料夾、針對附屬元件查詢 Windows Installer，以及引發 <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> 事件。</span><span class="sxs-lookup"><span data-stu-id="aba2a-127">This means that when Resource Manager probes for a particular localized version of a resource, it may look in the global assembly cache, look in a culture-specific folder in the application's code base, query Windows Installer for satellite assemblies, and raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="aba2a-128">`<relativeBindForResources>`元素會將 Resource Manager 探查附屬元件的方式優化。</span><span class="sxs-lookup"><span data-stu-id="aba2a-128">The `<relativeBindForResources>` element optimizes the way in which Resource Manager probes for satellite assemblies.</span></span> <span data-ttu-id="aba2a-129">在下列情況下探查資源時，它可以改善效能：</span><span class="sxs-lookup"><span data-stu-id="aba2a-129">It can improve performance when probing for resources under the following conditions:</span></span>  
  
- <span data-ttu-id="aba2a-130">當附屬元件部署在與程式碼元件相同的位置時。</span><span class="sxs-lookup"><span data-stu-id="aba2a-130">When the satellite assembly is deployed in the same location as the code assembly.</span></span> <span data-ttu-id="aba2a-131">換句話說，如果程式碼元件安裝在全域組件快取中，則也必須在該處安裝附屬元件。</span><span class="sxs-lookup"><span data-stu-id="aba2a-131">In other words, if the code assembly is installed in the global assembly cache, the satellite assemblies must also be installed there.</span></span> <span data-ttu-id="aba2a-132">如果程式碼元件安裝在應用程式的程式碼基底中，則附屬元件也必須安裝在程式碼基底中的文化特性特定資料夾內。</span><span class="sxs-lookup"><span data-stu-id="aba2a-132">If the code assembly is installed in the application's code base, the satellite assemblies must also be installed in a culture-specific folder in the code base.</span></span>  
  
- <span data-ttu-id="aba2a-133">未使用 Windows Installer，或只是很少用來視需要安裝附屬元件。</span><span class="sxs-lookup"><span data-stu-id="aba2a-133">When Windows Installer is not used or is used only rarely for on-demand installation of satellite assemblies.</span></span>  
  
- <span data-ttu-id="aba2a-134">當應用程式代碼未處理 <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> 事件時。</span><span class="sxs-lookup"><span data-stu-id="aba2a-134">When application code does not handle the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
 <span data-ttu-id="aba2a-135">設定專案的 `enabled` 屬性 `<relativeBindForResources>` ，以將 `true` Resource Manager 的附屬元件探查優化，如下所示：</span><span class="sxs-lookup"><span data-stu-id="aba2a-135">Setting the `enabled` attribute of the `<relativeBindForResources>` element to `true` optimizes Resource Manager's probe for satellite assemblies as follows:</span></span>  
  
- <span data-ttu-id="aba2a-136">它會使用父程式碼元件的位置來探查附屬元件。</span><span class="sxs-lookup"><span data-stu-id="aba2a-136">It uses the location of the parent code assembly to probe for the satellite assembly.</span></span>  
  
- <span data-ttu-id="aba2a-137">它不會查詢附屬元件 Windows Installer。</span><span class="sxs-lookup"><span data-stu-id="aba2a-137">It does not query Windows Installer for satellite assemblies.</span></span>  
  
- <span data-ttu-id="aba2a-138">它不會引發 <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> 事件。</span><span class="sxs-lookup"><span data-stu-id="aba2a-138">It does not raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aba2a-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aba2a-139">See also</span></span>

- [<span data-ttu-id="aba2a-140">封裝和部署資源</span><span class="sxs-lookup"><span data-stu-id="aba2a-140">Packaging and Deploying Resources</span></span>](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [<span data-ttu-id="aba2a-141">執行時間設定架構</span><span class="sxs-lookup"><span data-stu-id="aba2a-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="aba2a-142">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="aba2a-142">Configuration File Schema</span></span>](../index.md)
