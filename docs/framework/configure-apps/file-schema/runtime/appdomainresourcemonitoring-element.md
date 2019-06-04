---
title: <appDomainResourceMonitoring> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad0ae023215eeb1f42f9351369ee77d41d537b88
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487724"
---
# <a name="appdomainresourcemonitoring-element"></a><span data-ttu-id="98b1c-102">\<appDomainResourceMonitoring > 項目</span><span class="sxs-lookup"><span data-stu-id="98b1c-102">\<appDomainResourceMonitoring> Element</span></span>
<span data-ttu-id="98b1c-103">針對處理序存留期間，指示執行階段收集處理序中所有應用程式網域的統計資料。</span><span class="sxs-lookup"><span data-stu-id="98b1c-103">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="98b1c-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="98b1c-104">\<configuration></span></span>  
<span data-ttu-id="98b1c-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="98b1c-105">\<runtime></span></span>  
<span data-ttu-id="98b1c-106">\<appDomainResourceMonitoring></span><span class="sxs-lookup"><span data-stu-id="98b1c-106">\<appDomainResourceMonitoring></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98b1c-107">語法</span><span class="sxs-lookup"><span data-stu-id="98b1c-107">Syntax</span></span>  
  
```xml  
<appDomainResourceMonitoring    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="98b1c-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="98b1c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="98b1c-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="98b1c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="98b1c-110">屬性</span><span class="sxs-lookup"><span data-stu-id="98b1c-110">Attributes</span></span>  
  
|<span data-ttu-id="98b1c-111">屬性</span><span class="sxs-lookup"><span data-stu-id="98b1c-111">Attribute</span></span>|<span data-ttu-id="98b1c-112">描述</span><span class="sxs-lookup"><span data-stu-id="98b1c-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="98b1c-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="98b1c-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="98b1c-114">指定是否執行階段會收集應用程式定義域資源監視的統計資料。</span><span class="sxs-lookup"><span data-stu-id="98b1c-114">Specifies whether the runtime collects statistics for application domain resource monitoring.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="98b1c-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="98b1c-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="98b1c-116">值</span><span class="sxs-lookup"><span data-stu-id="98b1c-116">Value</span></span>|<span data-ttu-id="98b1c-117">描述</span><span class="sxs-lookup"><span data-stu-id="98b1c-117">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="98b1c-118">會收集統計資料的應用程式定義域資源監視。</span><span class="sxs-lookup"><span data-stu-id="98b1c-118">Statistics for application domain resource monitoring are collected.</span></span>|  
|`false`|<span data-ttu-id="98b1c-119">不會收集應用程式定義域資源監視的統計資料。</span><span class="sxs-lookup"><span data-stu-id="98b1c-119">Statistics for application domain resource monitoring are not collected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="98b1c-120">子元素</span><span class="sxs-lookup"><span data-stu-id="98b1c-120">Child Elements</span></span>  
 <span data-ttu-id="98b1c-121">無。</span><span class="sxs-lookup"><span data-stu-id="98b1c-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="98b1c-122">父項目</span><span class="sxs-lookup"><span data-stu-id="98b1c-122">Parent Elements</span></span>  
  
|<span data-ttu-id="98b1c-123">項目</span><span class="sxs-lookup"><span data-stu-id="98b1c-123">Element</span></span>|<span data-ttu-id="98b1c-124">描述</span><span class="sxs-lookup"><span data-stu-id="98b1c-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="98b1c-125">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="98b1c-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="98b1c-126">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="98b1c-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98b1c-127">備註</span><span class="sxs-lookup"><span data-stu-id="98b1c-127">Remarks</span></span>  
 <span data-ttu-id="98b1c-128">應用程式定義域資源監視是透過受控應用程式網域類別，裝載[ICLRAppDomainResourceMonitor](../../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)介面和事件追蹤的 Windows (ETW)。</span><span class="sxs-lookup"><span data-stu-id="98b1c-128">Application domain resource monitoring is available through the managed application domain class, the hosting [ICLRAppDomainResourceMonitor](../../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface, and event tracing for Windows (ETW).</span></span> <span data-ttu-id="98b1c-129">啟用監視時，會收集統計資料的生命週期的處理程序的程序中的所有應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="98b1c-129">When monitoring is enabled, statistics are collected for all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="98b1c-130">若要啟用監視從 managed 程式碼，請使用<xref:System.AppDomain.MonitoringIsEnabled%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="98b1c-130">To enable monitoring from managed code, use the <xref:System.AppDomain.MonitoringIsEnabled%2A> property.</span></span>  
  
 <span data-ttu-id="98b1c-131">這個組態項目是僅適用於.NET Framework 4 及更新版本。</span><span class="sxs-lookup"><span data-stu-id="98b1c-131">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98b1c-132">範例</span><span class="sxs-lookup"><span data-stu-id="98b1c-132">Example</span></span>  
 <span data-ttu-id="98b1c-133">下列範例示範如何啟用應用程式定義域資源監視。</span><span class="sxs-lookup"><span data-stu-id="98b1c-133">The following example shows how to enable application domain resource monitoring.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="98b1c-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98b1c-134">See also</span></span>

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="98b1c-135">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="98b1c-135">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="98b1c-136">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="98b1c-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
