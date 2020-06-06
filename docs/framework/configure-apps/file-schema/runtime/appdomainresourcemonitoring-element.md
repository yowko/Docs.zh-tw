---
title: <appDomainResourceMonitoring> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
ms.openlocfilehash: 3c6092b6c34bb13c0ad0e66df2d3b7e65ac3de7e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154372"
---
# <a name="appdomainresourcemonitoring-element"></a><span data-ttu-id="a6fcc-102">\<appDomainResourceMonitoring> 項目</span><span class="sxs-lookup"><span data-stu-id="a6fcc-102">\<appDomainResourceMonitoring> Element</span></span>
<span data-ttu-id="a6fcc-103">針對處理序存留期間，指示執行階段收集處理序中所有應用程式網域的統計資料。</span><span class="sxs-lookup"><span data-stu-id="a6fcc-103">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainResourceMonitoring>**  
  
## <a name="syntax"></a><span data-ttu-id="a6fcc-104">語法</span><span class="sxs-lookup"><span data-stu-id="a6fcc-104">Syntax</span></span>  
  
```xml  
<appDomainResourceMonitoring
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6fcc-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a6fcc-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a6fcc-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a6fcc-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6fcc-107">屬性</span><span class="sxs-lookup"><span data-stu-id="a6fcc-107">Attributes</span></span>  
  
|<span data-ttu-id="a6fcc-108">屬性</span><span class="sxs-lookup"><span data-stu-id="a6fcc-108">Attribute</span></span>|<span data-ttu-id="a6fcc-109">描述</span><span class="sxs-lookup"><span data-stu-id="a6fcc-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="a6fcc-110">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="a6fcc-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="a6fcc-111">指定執行時間是否收集應用程式域資源監視的統計資料。</span><span class="sxs-lookup"><span data-stu-id="a6fcc-111">Specifies whether the runtime collects statistics for application domain resource monitoring.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="a6fcc-112">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="a6fcc-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="a6fcc-113">值</span><span class="sxs-lookup"><span data-stu-id="a6fcc-113">Value</span></span>|<span data-ttu-id="a6fcc-114">描述</span><span class="sxs-lookup"><span data-stu-id="a6fcc-114">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="a6fcc-115">系統會收集應用程式域資源監視的統計資料。</span><span class="sxs-lookup"><span data-stu-id="a6fcc-115">Statistics for application domain resource monitoring are collected.</span></span>|  
|`false`|<span data-ttu-id="a6fcc-116">不會收集應用程式域資源監視的統計資料。</span><span class="sxs-lookup"><span data-stu-id="a6fcc-116">Statistics for application domain resource monitoring are not collected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a6fcc-117">子元素</span><span class="sxs-lookup"><span data-stu-id="a6fcc-117">Child Elements</span></span>  
 <span data-ttu-id="a6fcc-118">無。</span><span class="sxs-lookup"><span data-stu-id="a6fcc-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a6fcc-119">父項目</span><span class="sxs-lookup"><span data-stu-id="a6fcc-119">Parent Elements</span></span>  
  
|<span data-ttu-id="a6fcc-120">元素</span><span class="sxs-lookup"><span data-stu-id="a6fcc-120">Element</span></span>|<span data-ttu-id="a6fcc-121">描述</span><span class="sxs-lookup"><span data-stu-id="a6fcc-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a6fcc-122">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="a6fcc-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="a6fcc-123">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="a6fcc-123">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6fcc-124">備註</span><span class="sxs-lookup"><span data-stu-id="a6fcc-124">Remarks</span></span>  
 <span data-ttu-id="a6fcc-125">應用程式域資源監視可透過受控應用程式域類別、裝載[ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)介面和 Windows 事件追蹤（ETW）來取得。</span><span class="sxs-lookup"><span data-stu-id="a6fcc-125">Application domain resource monitoring is available through the managed application domain class, the hosting [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface, and event tracing for Windows (ETW).</span></span> <span data-ttu-id="a6fcc-126">啟用監視時，會針對進程中的所有應用程式域收集統計資料。</span><span class="sxs-lookup"><span data-stu-id="a6fcc-126">When monitoring is enabled, statistics are collected for all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="a6fcc-127">若要從 managed 程式碼啟用監視，請使用 <xref:System.AppDomain.MonitoringIsEnabled%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="a6fcc-127">To enable monitoring from managed code, use the <xref:System.AppDomain.MonitoringIsEnabled%2A> property.</span></span>  
  
 <span data-ttu-id="a6fcc-128">此 configuration 元素僅適用于 .NET Framework 4 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="a6fcc-128">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6fcc-129">範例</span><span class="sxs-lookup"><span data-stu-id="a6fcc-129">Example</span></span>  
 <span data-ttu-id="a6fcc-130">下列範例顯示如何啟用應用程式域資源監視。</span><span class="sxs-lookup"><span data-stu-id="a6fcc-130">The following example shows how to enable application domain resource monitoring.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a6fcc-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6fcc-131">See also</span></span>

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="a6fcc-132">執行時間設定架構</span><span class="sxs-lookup"><span data-stu-id="a6fcc-132">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a6fcc-133">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="a6fcc-133">Configuration File Schema</span></span>](../index.md)
