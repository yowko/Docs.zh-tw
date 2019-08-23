---
title: 啟動的 <diagnostics>
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: 543c41936921eda39017e07f1c97294b268a9141
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919212"
---
# <a name="diagnostics-for-activation"></a><span data-ttu-id="1a537-102">\<啟用的診斷 ></span><span class="sxs-lookup"><span data-stu-id="1a537-102">\<diagnostics> for Activation</span></span>
<span data-ttu-id="1a537-103">設定 Windows Communication Foundation (WCF) 接聽程式的診斷功能。</span><span class="sxs-lookup"><span data-stu-id="1a537-103">Configures Windows Communication Foundation (WCF) listener's diagnostics functionalities.</span></span>  
  
 <span data-ttu-id="1a537-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="1a537-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="1a537-105">\<diagnostics></span><span class="sxs-lookup"><span data-stu-id="1a537-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a537-106">語法</span><span class="sxs-lookup"><span data-stu-id="1a537-106">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <diagnostics performanceCountersEnabled="Boolean" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="1a537-107">類型</span><span class="sxs-lookup"><span data-stu-id="1a537-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1a537-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1a537-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1a537-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="1a537-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1a537-110">屬性</span><span class="sxs-lookup"><span data-stu-id="1a537-110">Attributes</span></span>  
  
|<span data-ttu-id="1a537-111">屬性</span><span class="sxs-lookup"><span data-stu-id="1a537-111">Attribute</span></span>|<span data-ttu-id="1a537-112">說明</span><span class="sxs-lookup"><span data-stu-id="1a537-112">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="1a537-113">布林值，指出是否啟用效能計數器以供診斷用途。</span><span class="sxs-lookup"><span data-stu-id="1a537-113">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1a537-114">子元素</span><span class="sxs-lookup"><span data-stu-id="1a537-114">Child Elements</span></span>  
 <span data-ttu-id="1a537-115">無。</span><span class="sxs-lookup"><span data-stu-id="1a537-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1a537-116">父項目</span><span class="sxs-lookup"><span data-stu-id="1a537-116">Parent Elements</span></span>  
  
|<span data-ttu-id="1a537-117">項目</span><span class="sxs-lookup"><span data-stu-id="1a537-117">Element</span></span>|<span data-ttu-id="1a537-118">描述</span><span class="sxs-lookup"><span data-stu-id="1a537-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1a537-119">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="1a537-119">\<system.serviceModel.activation></span></span>](system-servicemodel-activation.md)|<span data-ttu-id="1a537-120">包含 SMSvcHost.exe 接聽程式處理序的組態設定。</span><span class="sxs-lookup"><span data-stu-id="1a537-120">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1a537-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a537-121">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
