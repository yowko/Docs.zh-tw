---
title: 啟動的 <diagnostics>
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: 33b2cd4c5ae1b4076892a61aa7e2b927efa1ddc1
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400415"
---
# <a name="diagnostics-for-activation"></a><span data-ttu-id="2aa86-102">\<啟用的診斷 ></span><span class="sxs-lookup"><span data-stu-id="2aa86-102">\<diagnostics> for Activation</span></span>
<span data-ttu-id="2aa86-103">設定 Windows Communication Foundation （WCF）接聽程式的診斷功能。</span><span class="sxs-lookup"><span data-stu-id="2aa86-103">Configures Windows Communication Foundation (WCF) listener's diagnostics functionalities.</span></span>  
  
<span data-ttu-id="2aa86-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2aa86-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2aa86-105">&nbsp;&nbsp;[ **\<System.servicemodel. 啟用 >** ](system-servicemodel-activation.md)</span><span class="sxs-lookup"><span data-stu-id="2aa86-105">&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)</span></span>\
<span data-ttu-id="2aa86-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<診斷 >**</span><span class="sxs-lookup"><span data-stu-id="2aa86-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<diagnostics>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2aa86-107">語法</span><span class="sxs-lookup"><span data-stu-id="2aa86-107">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <diagnostics performanceCountersEnabled="Boolean" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="2aa86-108">類型</span><span class="sxs-lookup"><span data-stu-id="2aa86-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2aa86-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2aa86-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2aa86-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2aa86-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2aa86-111">屬性</span><span class="sxs-lookup"><span data-stu-id="2aa86-111">Attributes</span></span>  
  
|<span data-ttu-id="2aa86-112">屬性</span><span class="sxs-lookup"><span data-stu-id="2aa86-112">Attribute</span></span>|<span data-ttu-id="2aa86-113">描述</span><span class="sxs-lookup"><span data-stu-id="2aa86-113">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="2aa86-114">布林值，指出是否啟用效能計數器以供診斷用途。</span><span class="sxs-lookup"><span data-stu-id="2aa86-114">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2aa86-115">子元素</span><span class="sxs-lookup"><span data-stu-id="2aa86-115">Child Elements</span></span>  
 <span data-ttu-id="2aa86-116">無。</span><span class="sxs-lookup"><span data-stu-id="2aa86-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2aa86-117">父項目</span><span class="sxs-lookup"><span data-stu-id="2aa86-117">Parent Elements</span></span>  
  
|<span data-ttu-id="2aa86-118">項目</span><span class="sxs-lookup"><span data-stu-id="2aa86-118">Element</span></span>|<span data-ttu-id="2aa86-119">說明</span><span class="sxs-lookup"><span data-stu-id="2aa86-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2aa86-120">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="2aa86-120">\<system.serviceModel.activation></span></span>](system-servicemodel-activation.md)|<span data-ttu-id="2aa86-121">包含 SMSvcHost.exe 接聽程式處理序的組態設定。</span><span class="sxs-lookup"><span data-stu-id="2aa86-121">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2aa86-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2aa86-122">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
