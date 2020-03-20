---
title: <appDomainResourceMonitoring> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
ms.openlocfilehash: 3c6092b6c34bb13c0ad0e66df2d3b7e65ac3de7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154372"
---
# <a name="appdomainresourcemonitoring-element"></a><span data-ttu-id="7462c-102">\<appDomain資源監視>元素</span><span class="sxs-lookup"><span data-stu-id="7462c-102">\<appDomainResourceMonitoring> Element</span></span>
<span data-ttu-id="7462c-103">針對處理序存留期間，指示執行階段收集處理序中所有應用程式網域的統計資料。</span><span class="sxs-lookup"><span data-stu-id="7462c-103">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>  
  
<span data-ttu-id="7462c-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7462c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7462c-105">&nbsp;&nbsp;[**\<運行時>**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="7462c-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="7462c-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<應用程式域資源監視>**</span><span class="sxs-lookup"><span data-stu-id="7462c-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainResourceMonitoring>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7462c-107">語法</span><span class="sxs-lookup"><span data-stu-id="7462c-107">Syntax</span></span>  
  
```xml  
<appDomainResourceMonitoring
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7462c-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7462c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7462c-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="7462c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7462c-110">屬性</span><span class="sxs-lookup"><span data-stu-id="7462c-110">Attributes</span></span>  
  
|<span data-ttu-id="7462c-111">屬性</span><span class="sxs-lookup"><span data-stu-id="7462c-111">Attribute</span></span>|<span data-ttu-id="7462c-112">描述</span><span class="sxs-lookup"><span data-stu-id="7462c-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="7462c-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="7462c-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="7462c-114">指定運行時是否收集應用程式域資源監視的統計資訊。</span><span class="sxs-lookup"><span data-stu-id="7462c-114">Specifies whether the runtime collects statistics for application domain resource monitoring.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="7462c-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="7462c-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="7462c-116">值</span><span class="sxs-lookup"><span data-stu-id="7462c-116">Value</span></span>|<span data-ttu-id="7462c-117">描述</span><span class="sxs-lookup"><span data-stu-id="7462c-117">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="7462c-118">收集應用程式域資源監視的統計資訊。</span><span class="sxs-lookup"><span data-stu-id="7462c-118">Statistics for application domain resource monitoring are collected.</span></span>|  
|`false`|<span data-ttu-id="7462c-119">不會收集應用程式域資源監視的統計資訊。</span><span class="sxs-lookup"><span data-stu-id="7462c-119">Statistics for application domain resource monitoring are not collected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7462c-120">子元素</span><span class="sxs-lookup"><span data-stu-id="7462c-120">Child Elements</span></span>  
 <span data-ttu-id="7462c-121">無。</span><span class="sxs-lookup"><span data-stu-id="7462c-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7462c-122">父項目</span><span class="sxs-lookup"><span data-stu-id="7462c-122">Parent Elements</span></span>  
  
|<span data-ttu-id="7462c-123">元素</span><span class="sxs-lookup"><span data-stu-id="7462c-123">Element</span></span>|<span data-ttu-id="7462c-124">描述</span><span class="sxs-lookup"><span data-stu-id="7462c-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7462c-125">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="7462c-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="7462c-126">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="7462c-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7462c-127">備註</span><span class="sxs-lookup"><span data-stu-id="7462c-127">Remarks</span></span>  
 <span data-ttu-id="7462c-128">應用程式域資源監視可通過託管應用程式域類、託管[ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)介面和 Windows （ETW） 的事件跟蹤進行。</span><span class="sxs-lookup"><span data-stu-id="7462c-128">Application domain resource monitoring is available through the managed application domain class, the hosting [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface, and event tracing for Windows (ETW).</span></span> <span data-ttu-id="7462c-129">啟用監視後，將收集流程中所有應用程式域的統計資訊，以進行此過程的生命週期。</span><span class="sxs-lookup"><span data-stu-id="7462c-129">When monitoring is enabled, statistics are collected for all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="7462c-130">要啟用從託管代碼進行監視，請使用<xref:System.AppDomain.MonitoringIsEnabled%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="7462c-130">To enable monitoring from managed code, use the <xref:System.AppDomain.MonitoringIsEnabled%2A> property.</span></span>  
  
 <span data-ttu-id="7462c-131">此配置元素僅在 .NET 框架 4 和更高版本中可用。</span><span class="sxs-lookup"><span data-stu-id="7462c-131">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7462c-132">範例</span><span class="sxs-lookup"><span data-stu-id="7462c-132">Example</span></span>  
 <span data-ttu-id="7462c-133">下面的示例演示如何啟用應用程式域資源監視。</span><span class="sxs-lookup"><span data-stu-id="7462c-133">The following example shows how to enable application domain resource monitoring.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7462c-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7462c-134">See also</span></span>

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="7462c-135">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="7462c-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="7462c-136">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="7462c-136">Configuration File Schema</span></span>](../index.md)
