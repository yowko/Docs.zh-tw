---
title: 啟用的 &lt;diagnostics&gt;
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: 4e5332eed87ded51cebcd614f45cbc8e80e570fb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltdiagnosticsgt-for-activation"></a><span data-ttu-id="e40a9-102">啟用的 &lt;diagnostics&gt;</span><span class="sxs-lookup"><span data-stu-id="e40a9-102">&lt;diagnostics&gt; for Activation</span></span>
<span data-ttu-id="e40a9-103">設定 Windows Communication Foundation (WCF) 接聽程式的診斷功能。</span><span class="sxs-lookup"><span data-stu-id="e40a9-103">Configures Windows Communication Foundation (WCF) listener's diagnostics functionalities.</span></span>  
  
 <span data-ttu-id="e40a9-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="e40a9-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="e40a9-105">\<診斷 ></span><span class="sxs-lookup"><span data-stu-id="e40a9-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e40a9-106">語法</span><span class="sxs-lookup"><span data-stu-id="e40a9-106">Syntax</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <diagnostics performanceCountersEnabled="Boolean" />  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## <a name="type"></a><span data-ttu-id="e40a9-107">類型</span><span class="sxs-lookup"><span data-stu-id="e40a9-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e40a9-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e40a9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e40a9-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e40a9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e40a9-110">屬性</span><span class="sxs-lookup"><span data-stu-id="e40a9-110">Attributes</span></span>  
  
|<span data-ttu-id="e40a9-111">屬性</span><span class="sxs-lookup"><span data-stu-id="e40a9-111">Attribute</span></span>|<span data-ttu-id="e40a9-112">描述</span><span class="sxs-lookup"><span data-stu-id="e40a9-112">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="e40a9-113">布林值，指出是否啟用效能計數器以供診斷用途。</span><span class="sxs-lookup"><span data-stu-id="e40a9-113">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e40a9-114">子項目</span><span class="sxs-lookup"><span data-stu-id="e40a9-114">Child Elements</span></span>  
 <span data-ttu-id="e40a9-115">無。</span><span class="sxs-lookup"><span data-stu-id="e40a9-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e40a9-116">父項目</span><span class="sxs-lookup"><span data-stu-id="e40a9-116">Parent Elements</span></span>  
  
|<span data-ttu-id="e40a9-117">項目</span><span class="sxs-lookup"><span data-stu-id="e40a9-117">Element</span></span>|<span data-ttu-id="e40a9-118">描述</span><span class="sxs-lookup"><span data-stu-id="e40a9-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e40a9-119">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="e40a9-119">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="e40a9-120">包含 SMSvcHost.exe 接聽程式處理序的組態設定。</span><span class="sxs-lookup"><span data-stu-id="e40a9-120">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e40a9-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e40a9-121">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
