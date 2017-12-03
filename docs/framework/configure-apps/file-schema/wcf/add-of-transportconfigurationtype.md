---
title: "&lt;transportConfigurationType&gt; 的 &lt;add&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0b27994cae77ec012e0b432e702c9c2ccb1933b8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-lttransportconfigurationtypegt"></a><span data-ttu-id="2ef85-102">&lt;transportConfigurationType&gt; 的 &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="2ef85-102">&lt;add&gt; of &lt;transportConfigurationType&gt;</span></span>
<span data-ttu-id="2ef85-103">此項目是索引鍵/值組，可用來識別特定傳輸的型別。</span><span class="sxs-lookup"><span data-stu-id="2ef85-103">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
 <span data-ttu-id="2ef85-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="2ef85-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2ef85-105">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="2ef85-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="2ef85-106">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="2ef85-106">\<transportConfigurationTypes></span></span>  
<span data-ttu-id="2ef85-107">\<add></span><span class="sxs-lookup"><span data-stu-id="2ef85-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ef85-108">語法</span><span class="sxs-lookup"><span data-stu-id="2ef85-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <transportConfigurationTypes>  
      <add name="String"  
               transportConfigurationType="String"/>   
   </transportConfigurationTypes>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2ef85-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2ef85-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2ef85-110">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2ef85-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2ef85-111">屬性</span><span class="sxs-lookup"><span data-stu-id="2ef85-111">Attributes</span></span>  
  
|<span data-ttu-id="2ef85-112">屬性</span><span class="sxs-lookup"><span data-stu-id="2ef85-112">Attribute</span></span>|<span data-ttu-id="2ef85-113">描述</span><span class="sxs-lookup"><span data-stu-id="2ef85-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2ef85-114">name</span><span class="sxs-lookup"><span data-stu-id="2ef85-114">name</span></span>|<span data-ttu-id="2ef85-115">必要的 String 屬性。</span><span class="sxs-lookup"><span data-stu-id="2ef85-115">Required String attribute.</span></span><br /><br /> <span data-ttu-id="2ef85-116">包含唯一識別傳輸型別的使用者定義索引鍵。</span><span class="sxs-lookup"><span data-stu-id="2ef85-116">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="2ef85-117">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="2ef85-117">transportConfigurationType</span></span>|<span data-ttu-id="2ef85-118">字串，包含可實作特定傳輸的型別。</span><span class="sxs-lookup"><span data-stu-id="2ef85-118">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2ef85-119">子元素</span><span class="sxs-lookup"><span data-stu-id="2ef85-119">Child Elements</span></span>  
 <span data-ttu-id="2ef85-120">無</span><span class="sxs-lookup"><span data-stu-id="2ef85-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2ef85-121">父項目</span><span class="sxs-lookup"><span data-stu-id="2ef85-121">Parent Elements</span></span>  
  
|<span data-ttu-id="2ef85-122">項目</span><span class="sxs-lookup"><span data-stu-id="2ef85-122">Element</span></span>|<span data-ttu-id="2ef85-123">說明</span><span class="sxs-lookup"><span data-stu-id="2ef85-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2ef85-124">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="2ef85-124">\<transportConfigurationTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transportconfigurationtypes.md)|<span data-ttu-id="2ef85-125">實作特定傳輸之型別的集合。</span><span class="sxs-lookup"><span data-stu-id="2ef85-125">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2ef85-126">範例</span><span class="sxs-lookup"><span data-stu-id="2ef85-126">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <transportConfigurationTypes>  
      <add name="net.udp"  
      transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />   
   </transportConfigurationTypes>  
</serviceHostingEnvironment>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2ef85-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ef85-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [<span data-ttu-id="2ef85-128">裝載</span><span class="sxs-lookup"><span data-stu-id="2ef85-128">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
