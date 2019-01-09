---
title: '&lt;transportConfigurationType&gt; 的 &lt;add&gt;'
ms.date: 03/30/2017
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
ms.openlocfilehash: 1079b25ce137dc89fc31f46a11f3720486462021
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149133"
---
# <a name="ltaddgt-of-lttransportconfigurationtypegt"></a><span data-ttu-id="3b4e8-102">&lt;transportConfigurationType&gt; 的 &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="3b4e8-102">&lt;add&gt; of &lt;transportConfigurationType&gt;</span></span>
<span data-ttu-id="3b4e8-103">此項目是索引鍵/值組，可用來識別特定傳輸的型別。</span><span class="sxs-lookup"><span data-stu-id="3b4e8-103">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
 <span data-ttu-id="3b4e8-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3b4e8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3b4e8-105">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="3b4e8-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="3b4e8-106">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="3b4e8-106">\<transportConfigurationTypes></span></span>  
<span data-ttu-id="3b4e8-107">\<add></span><span class="sxs-lookup"><span data-stu-id="3b4e8-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b4e8-108">語法</span><span class="sxs-lookup"><span data-stu-id="3b4e8-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3b4e8-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3b4e8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3b4e8-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="3b4e8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3b4e8-111">屬性</span><span class="sxs-lookup"><span data-stu-id="3b4e8-111">Attributes</span></span>  
  
|<span data-ttu-id="3b4e8-112">屬性</span><span class="sxs-lookup"><span data-stu-id="3b4e8-112">Attribute</span></span>|<span data-ttu-id="3b4e8-113">描述</span><span class="sxs-lookup"><span data-stu-id="3b4e8-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3b4e8-114">name</span><span class="sxs-lookup"><span data-stu-id="3b4e8-114">name</span></span>|<span data-ttu-id="3b4e8-115">必要的 String 屬性。</span><span class="sxs-lookup"><span data-stu-id="3b4e8-115">Required String attribute.</span></span><br /><br /> <span data-ttu-id="3b4e8-116">包含唯一識別傳輸型別的使用者定義索引鍵。</span><span class="sxs-lookup"><span data-stu-id="3b4e8-116">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="3b4e8-117">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="3b4e8-117">transportConfigurationType</span></span>|<span data-ttu-id="3b4e8-118">字串，包含可實作特定傳輸的型別。</span><span class="sxs-lookup"><span data-stu-id="3b4e8-118">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3b4e8-119">子元素</span><span class="sxs-lookup"><span data-stu-id="3b4e8-119">Child Elements</span></span>  
 <span data-ttu-id="3b4e8-120">無</span><span class="sxs-lookup"><span data-stu-id="3b4e8-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3b4e8-121">父項目</span><span class="sxs-lookup"><span data-stu-id="3b4e8-121">Parent Elements</span></span>  
  
|<span data-ttu-id="3b4e8-122">項目</span><span class="sxs-lookup"><span data-stu-id="3b4e8-122">Element</span></span>|<span data-ttu-id="3b4e8-123">描述</span><span class="sxs-lookup"><span data-stu-id="3b4e8-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3b4e8-124">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="3b4e8-124">\<transportConfigurationTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transportconfigurationtypes.md)|<span data-ttu-id="3b4e8-125">實作特定傳輸之型別的集合。</span><span class="sxs-lookup"><span data-stu-id="3b4e8-125">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3b4e8-126">範例</span><span class="sxs-lookup"><span data-stu-id="3b4e8-126">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="net.udp"
         transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="see-also"></a><span data-ttu-id="3b4e8-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b4e8-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [<span data-ttu-id="3b4e8-128">裝載</span><span class="sxs-lookup"><span data-stu-id="3b4e8-128">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
