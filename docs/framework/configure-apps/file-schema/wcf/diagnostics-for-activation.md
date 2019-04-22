---
title: 啟動的 <diagnostics>
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: 30456963a7d74a93e39bb1fddc0910daae97f039
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59203804"
---
# <a name="diagnostics-for-activation"></a><span data-ttu-id="30b84-102">\<診斷 > 啟用</span><span class="sxs-lookup"><span data-stu-id="30b84-102">\<diagnostics> for Activation</span></span>
<span data-ttu-id="30b84-103">設定 Windows Communication Foundation (WCF) 接聽程式的診斷功能。</span><span class="sxs-lookup"><span data-stu-id="30b84-103">Configures Windows Communication Foundation (WCF) listener's diagnostics functionalities.</span></span>  
  
 <span data-ttu-id="30b84-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="30b84-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="30b84-105">\<diagnostics></span><span class="sxs-lookup"><span data-stu-id="30b84-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30b84-106">語法</span><span class="sxs-lookup"><span data-stu-id="30b84-106">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <diagnostics performanceCountersEnabled="Boolean" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="30b84-107">類型</span><span class="sxs-lookup"><span data-stu-id="30b84-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="30b84-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="30b84-108">Attributes and Elements</span></span>  
 <span data-ttu-id="30b84-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="30b84-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30b84-110">屬性</span><span class="sxs-lookup"><span data-stu-id="30b84-110">Attributes</span></span>  
  
|<span data-ttu-id="30b84-111">屬性</span><span class="sxs-lookup"><span data-stu-id="30b84-111">Attribute</span></span>|<span data-ttu-id="30b84-112">描述</span><span class="sxs-lookup"><span data-stu-id="30b84-112">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="30b84-113">布林值，指出是否啟用效能計數器以供診斷用途。</span><span class="sxs-lookup"><span data-stu-id="30b84-113">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="30b84-114">子元素</span><span class="sxs-lookup"><span data-stu-id="30b84-114">Child Elements</span></span>  
 <span data-ttu-id="30b84-115">無。</span><span class="sxs-lookup"><span data-stu-id="30b84-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="30b84-116">父項目</span><span class="sxs-lookup"><span data-stu-id="30b84-116">Parent Elements</span></span>  
  
|<span data-ttu-id="30b84-117">項目</span><span class="sxs-lookup"><span data-stu-id="30b84-117">Element</span></span>|<span data-ttu-id="30b84-118">描述</span><span class="sxs-lookup"><span data-stu-id="30b84-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="30b84-119">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="30b84-119">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="30b84-120">包含 SMSvcHost.exe 接聽程式處理序的組態設定。</span><span class="sxs-lookup"><span data-stu-id="30b84-120">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="30b84-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30b84-121">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
