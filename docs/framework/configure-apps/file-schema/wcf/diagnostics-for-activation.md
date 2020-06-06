---
title: 啟動的 <diagnostics>
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: 33b2cd4c5ae1b4076892a61aa7e2b927efa1ddc1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400415"
---
# <a name="diagnostics-for-activation"></a><span data-ttu-id="389f1-102">啟動的 \<diagnostics></span><span class="sxs-lookup"><span data-stu-id="389f1-102">\<diagnostics> for Activation</span></span>
<span data-ttu-id="389f1-103">設定 Windows Communication Foundation （WCF）接聽程式的診斷功能。</span><span class="sxs-lookup"><span data-stu-id="389f1-103">Configures Windows Communication Foundation (WCF) listener's diagnostics functionalities.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<diagnostics>**  
  
## <a name="syntax"></a><span data-ttu-id="389f1-104">語法</span><span class="sxs-lookup"><span data-stu-id="389f1-104">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <diagnostics performanceCountersEnabled="Boolean" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="389f1-105">類型</span><span class="sxs-lookup"><span data-stu-id="389f1-105">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="389f1-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="389f1-106">Attributes and Elements</span></span>  
 <span data-ttu-id="389f1-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="389f1-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="389f1-108">屬性</span><span class="sxs-lookup"><span data-stu-id="389f1-108">Attributes</span></span>  
  
|<span data-ttu-id="389f1-109">屬性</span><span class="sxs-lookup"><span data-stu-id="389f1-109">Attribute</span></span>|<span data-ttu-id="389f1-110">描述</span><span class="sxs-lookup"><span data-stu-id="389f1-110">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="389f1-111">布林值，指出是否啟用效能計數器以供診斷用途。</span><span class="sxs-lookup"><span data-stu-id="389f1-111">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="389f1-112">子元素</span><span class="sxs-lookup"><span data-stu-id="389f1-112">Child Elements</span></span>  
 <span data-ttu-id="389f1-113">無。</span><span class="sxs-lookup"><span data-stu-id="389f1-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="389f1-114">父項目</span><span class="sxs-lookup"><span data-stu-id="389f1-114">Parent Elements</span></span>  
  
|<span data-ttu-id="389f1-115">元素</span><span class="sxs-lookup"><span data-stu-id="389f1-115">Element</span></span>|<span data-ttu-id="389f1-116">描述</span><span class="sxs-lookup"><span data-stu-id="389f1-116">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](system-servicemodel-activation.md)|<span data-ttu-id="389f1-117">包含 SMSvcHost.exe 接聽程式處理序的組態設定。</span><span class="sxs-lookup"><span data-stu-id="389f1-117">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="389f1-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="389f1-118">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
