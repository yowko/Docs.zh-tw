---
title: '&lt;appDomainResourceMonitoring&gt;項目'
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 11e892d8ab9001d3670c801b43ba444aa24b2e41
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743572"
---
# <a name="ltappdomainresourcemonitoringgt-element"></a><span data-ttu-id="2c191-102">&lt;appDomainResourceMonitoring&gt;項目</span><span class="sxs-lookup"><span data-stu-id="2c191-102">&lt;appDomainResourceMonitoring&gt; Element</span></span>
<span data-ttu-id="2c191-103">針對處理序存留期間，指示執行階段收集處理序中所有應用程式網域的統計資料。</span><span class="sxs-lookup"><span data-stu-id="2c191-103">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="2c191-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="2c191-104">\<configuration></span></span>  
<span data-ttu-id="2c191-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="2c191-105">\<runtime></span></span>  
<span data-ttu-id="2c191-106">\<appDomainResourceMonitoring ></span><span class="sxs-lookup"><span data-stu-id="2c191-106">\<appDomainResourceMonitoring></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c191-107">語法</span><span class="sxs-lookup"><span data-stu-id="2c191-107">Syntax</span></span>  
  
```xml  
<appDomainResourceMonitoring    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2c191-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2c191-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2c191-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2c191-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2c191-110">屬性</span><span class="sxs-lookup"><span data-stu-id="2c191-110">Attributes</span></span>  
  
|<span data-ttu-id="2c191-111">屬性</span><span class="sxs-lookup"><span data-stu-id="2c191-111">Attribute</span></span>|<span data-ttu-id="2c191-112">描述</span><span class="sxs-lookup"><span data-stu-id="2c191-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="2c191-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="2c191-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="2c191-114">指定是否執行階段會收集應用程式定義域資源監視的統計資料。</span><span class="sxs-lookup"><span data-stu-id="2c191-114">Specifies whether the runtime collects statistics for application domain resource monitoring.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="2c191-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="2c191-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="2c191-116">值</span><span class="sxs-lookup"><span data-stu-id="2c191-116">Value</span></span>|<span data-ttu-id="2c191-117">描述</span><span class="sxs-lookup"><span data-stu-id="2c191-117">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="2c191-118">會收集應用程式定義域資源監視的統計資料。</span><span class="sxs-lookup"><span data-stu-id="2c191-118">Statistics for application domain resource monitoring are collected.</span></span>|  
|`false`|<span data-ttu-id="2c191-119">不會收集應用程式定義域資源監視的統計資料。</span><span class="sxs-lookup"><span data-stu-id="2c191-119">Statistics for application domain resource monitoring are not collected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2c191-120">子項目</span><span class="sxs-lookup"><span data-stu-id="2c191-120">Child Elements</span></span>  
 <span data-ttu-id="2c191-121">無。</span><span class="sxs-lookup"><span data-stu-id="2c191-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2c191-122">父項目</span><span class="sxs-lookup"><span data-stu-id="2c191-122">Parent Elements</span></span>  
  
|<span data-ttu-id="2c191-123">項目</span><span class="sxs-lookup"><span data-stu-id="2c191-123">Element</span></span>|<span data-ttu-id="2c191-124">描述</span><span class="sxs-lookup"><span data-stu-id="2c191-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2c191-125">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="2c191-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="2c191-126">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="2c191-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c191-127">備註</span><span class="sxs-lookup"><span data-stu-id="2c191-127">Remarks</span></span>  
 <span data-ttu-id="2c191-128">應用程式定義域資源監視是透過 managed 應用程式網域類別裝載[ICLRAppDomainResourceMonitor](../../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)介面和事件追蹤 Windows (ETW)。</span><span class="sxs-lookup"><span data-stu-id="2c191-128">Application domain resource monitoring is available through the managed application domain class, the hosting [ICLRAppDomainResourceMonitor](../../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface, and event tracing for Windows (ETW).</span></span> <span data-ttu-id="2c191-129">啟用監視，收集統計資料的程序的存留期的程序中的所有應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="2c191-129">When monitoring is enabled, statistics are collected for all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="2c191-130">若要啟用監視，從 managed 程式碼，請使用<xref:System.AppDomain.MonitoringIsEnabled%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="2c191-130">To enable monitoring from managed code, use the <xref:System.AppDomain.MonitoringIsEnabled%2A> property.</span></span>  
  
 <span data-ttu-id="2c191-131">這個組態項目是僅適用於[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]和更新版本。</span><span class="sxs-lookup"><span data-stu-id="2c191-131">This configuration element is available only in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c191-132">範例</span><span class="sxs-lookup"><span data-stu-id="2c191-132">Example</span></span>  
 <span data-ttu-id="2c191-133">下列範例會示範如何啟用應用程式定義域資源監視。</span><span class="sxs-lookup"><span data-stu-id="2c191-133">The following example shows how to enable application domain resource monitoring.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2c191-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c191-134">See Also</span></span>  
 <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="2c191-135">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="2c191-135">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="2c191-136">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="2c191-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
