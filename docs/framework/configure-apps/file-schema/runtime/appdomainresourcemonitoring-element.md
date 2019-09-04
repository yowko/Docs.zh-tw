---
title: <appDomainResourceMonitoring> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1395ee64d94e33693344b678c7a949665f994079
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252828"
---
# <a name="appdomainresourcemonitoring-element"></a><span data-ttu-id="e4135-102">\<appDomainResourceMonitoring > 元素</span><span class="sxs-lookup"><span data-stu-id="e4135-102">\<appDomainResourceMonitoring> Element</span></span>
<span data-ttu-id="e4135-103">針對處理序存留期間，指示執行階段收集處理序中所有應用程式網域的統計資料。</span><span class="sxs-lookup"><span data-stu-id="e4135-103">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>  
  
<span data-ttu-id="e4135-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e4135-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e4135-105">&nbsp;&nbsp;[ **\<執行時間 >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="e4135-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="e4135-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<appDomainResourceMonitoring>**</span><span class="sxs-lookup"><span data-stu-id="e4135-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainResourceMonitoring>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4135-107">語法</span><span class="sxs-lookup"><span data-stu-id="e4135-107">Syntax</span></span>  
  
```xml  
<appDomainResourceMonitoring    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4135-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e4135-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e4135-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e4135-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4135-110">屬性</span><span class="sxs-lookup"><span data-stu-id="e4135-110">Attributes</span></span>  
  
|<span data-ttu-id="e4135-111">屬性</span><span class="sxs-lookup"><span data-stu-id="e4135-111">Attribute</span></span>|<span data-ttu-id="e4135-112">描述</span><span class="sxs-lookup"><span data-stu-id="e4135-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="e4135-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="e4135-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="e4135-114">指定執行時間是否收集應用程式域資源監視的統計資料。</span><span class="sxs-lookup"><span data-stu-id="e4135-114">Specifies whether the runtime collects statistics for application domain resource monitoring.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="e4135-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="e4135-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="e4135-116">值</span><span class="sxs-lookup"><span data-stu-id="e4135-116">Value</span></span>|<span data-ttu-id="e4135-117">描述</span><span class="sxs-lookup"><span data-stu-id="e4135-117">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="e4135-118">系統會收集應用程式域資源監視的統計資料。</span><span class="sxs-lookup"><span data-stu-id="e4135-118">Statistics for application domain resource monitoring are collected.</span></span>|  
|`false`|<span data-ttu-id="e4135-119">不會收集應用程式域資源監視的統計資料。</span><span class="sxs-lookup"><span data-stu-id="e4135-119">Statistics for application domain resource monitoring are not collected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e4135-120">子元素</span><span class="sxs-lookup"><span data-stu-id="e4135-120">Child Elements</span></span>  
 <span data-ttu-id="e4135-121">無。</span><span class="sxs-lookup"><span data-stu-id="e4135-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e4135-122">父項目</span><span class="sxs-lookup"><span data-stu-id="e4135-122">Parent Elements</span></span>  
  
|<span data-ttu-id="e4135-123">項目</span><span class="sxs-lookup"><span data-stu-id="e4135-123">Element</span></span>|<span data-ttu-id="e4135-124">描述</span><span class="sxs-lookup"><span data-stu-id="e4135-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e4135-125">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="e4135-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e4135-126">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="e4135-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4135-127">備註</span><span class="sxs-lookup"><span data-stu-id="e4135-127">Remarks</span></span>  
 <span data-ttu-id="e4135-128">應用程式域資源監視可透過受控應用程式域類別、裝載[ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)介面和 Windows 事件追蹤 (ETW) 來取得。</span><span class="sxs-lookup"><span data-stu-id="e4135-128">Application domain resource monitoring is available through the managed application domain class, the hosting [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface, and event tracing for Windows (ETW).</span></span> <span data-ttu-id="e4135-129">啟用監視時, 會針對進程中的所有應用程式域收集統計資料。</span><span class="sxs-lookup"><span data-stu-id="e4135-129">When monitoring is enabled, statistics are collected for all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="e4135-130">若要從 managed 程式碼啟用監視, <xref:System.AppDomain.MonitoringIsEnabled%2A>請使用屬性。</span><span class="sxs-lookup"><span data-stu-id="e4135-130">To enable monitoring from managed code, use the <xref:System.AppDomain.MonitoringIsEnabled%2A> property.</span></span>  
  
 <span data-ttu-id="e4135-131">此 configuration 元素僅適用于 .NET Framework 4 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="e4135-131">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4135-132">範例</span><span class="sxs-lookup"><span data-stu-id="e4135-132">Example</span></span>  
 <span data-ttu-id="e4135-133">下列範例顯示如何啟用應用程式域資源監視。</span><span class="sxs-lookup"><span data-stu-id="e4135-133">The following example shows how to enable application domain resource monitoring.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e4135-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4135-134">See also</span></span>

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e4135-135">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="e4135-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e4135-136">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="e4135-136">Configuration File Schema</span></span>](../index.md)
