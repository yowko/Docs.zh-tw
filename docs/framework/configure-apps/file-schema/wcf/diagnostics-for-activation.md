---
title: 啟動的 <diagnostics>
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: c16f32357d40b9b69d52c525ce8a395a3de8fdb1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192317"
---
# <a name="diagnostics-for-activation"></a><span data-ttu-id="159af-102">啟動的 \<diagnostics></span><span class="sxs-lookup"><span data-stu-id="159af-102">\<diagnostics> for Activation</span></span>

<span data-ttu-id="159af-103">設定 Windows Communication Foundation (WCF) 接聽程式的診斷功能。</span><span class="sxs-lookup"><span data-stu-id="159af-103">Configures Windows Communication Foundation (WCF) listener's diagnostics functionalities.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<diagnostics>**  
  
## <a name="syntax"></a><span data-ttu-id="159af-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="159af-104">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <diagnostics performanceCountersEnabled="Boolean" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="159af-105">類型</span><span class="sxs-lookup"><span data-stu-id="159af-105">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="159af-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="159af-106">Attributes and Elements</span></span>  

 <span data-ttu-id="159af-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="159af-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="159af-108">屬性</span><span class="sxs-lookup"><span data-stu-id="159af-108">Attributes</span></span>  
  
|<span data-ttu-id="159af-109">屬性</span><span class="sxs-lookup"><span data-stu-id="159af-109">Attribute</span></span>|<span data-ttu-id="159af-110">描述</span><span class="sxs-lookup"><span data-stu-id="159af-110">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="159af-111">布林值，指出是否啟用效能計數器以供診斷用途。</span><span class="sxs-lookup"><span data-stu-id="159af-111">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="159af-112">子元素</span><span class="sxs-lookup"><span data-stu-id="159af-112">Child Elements</span></span>  

 <span data-ttu-id="159af-113">無。</span><span class="sxs-lookup"><span data-stu-id="159af-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="159af-114">父項目</span><span class="sxs-lookup"><span data-stu-id="159af-114">Parent Elements</span></span>  
  
|<span data-ttu-id="159af-115">項目</span><span class="sxs-lookup"><span data-stu-id="159af-115">Element</span></span>|<span data-ttu-id="159af-116">描述</span><span class="sxs-lookup"><span data-stu-id="159af-116">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](system-servicemodel-activation.md)|<span data-ttu-id="159af-117">包含 SMSvcHost.exe 接聽程式處理序的組態設定。</span><span class="sxs-lookup"><span data-stu-id="159af-117">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="159af-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="159af-118">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
