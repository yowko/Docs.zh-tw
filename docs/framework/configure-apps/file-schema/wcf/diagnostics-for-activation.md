---
title: "啟用的 &lt;diagnostics&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 29f2e56dd18da9dc3ce3206f5c3c80f4a47a7ff0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltdiagnosticsgt-for-activation"></a><span data-ttu-id="7a02c-102">啟用的 &lt;diagnostics&gt;</span><span class="sxs-lookup"><span data-stu-id="7a02c-102">&lt;diagnostics&gt; for Activation</span></span>
<span data-ttu-id="7a02c-103">設定 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 接聽程式的診斷功能。</span><span class="sxs-lookup"><span data-stu-id="7a02c-103">Configures [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] listener's diagnostics functionalities.</span></span>  
  
 <span data-ttu-id="7a02c-104">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="7a02c-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="7a02c-105">\<診斷 ></span><span class="sxs-lookup"><span data-stu-id="7a02c-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a02c-106">語法</span><span class="sxs-lookup"><span data-stu-id="7a02c-106">Syntax</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <diagnostics performanceCountersEnabled="Boolean" />  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## <a name="type"></a><span data-ttu-id="7a02c-107">類型</span><span class="sxs-lookup"><span data-stu-id="7a02c-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7a02c-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7a02c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7a02c-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7a02c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7a02c-110">屬性</span><span class="sxs-lookup"><span data-stu-id="7a02c-110">Attributes</span></span>  
  
|<span data-ttu-id="7a02c-111">屬性</span><span class="sxs-lookup"><span data-stu-id="7a02c-111">Attribute</span></span>|<span data-ttu-id="7a02c-112">描述</span><span class="sxs-lookup"><span data-stu-id="7a02c-112">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="7a02c-113">布林值，指出是否啟用效能計數器以供診斷用途。</span><span class="sxs-lookup"><span data-stu-id="7a02c-113">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7a02c-114">子元素</span><span class="sxs-lookup"><span data-stu-id="7a02c-114">Child Elements</span></span>  
 <span data-ttu-id="7a02c-115">無。</span><span class="sxs-lookup"><span data-stu-id="7a02c-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7a02c-116">父項目</span><span class="sxs-lookup"><span data-stu-id="7a02c-116">Parent Elements</span></span>  
  
|<span data-ttu-id="7a02c-117">項目</span><span class="sxs-lookup"><span data-stu-id="7a02c-117">Element</span></span>|<span data-ttu-id="7a02c-118">說明</span><span class="sxs-lookup"><span data-stu-id="7a02c-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7a02c-119">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="7a02c-119">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="7a02c-120">包含 SMSvcHost.exe 接聽程式處理序的組態設定。</span><span class="sxs-lookup"><span data-stu-id="7a02c-120">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7a02c-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a02c-121">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
