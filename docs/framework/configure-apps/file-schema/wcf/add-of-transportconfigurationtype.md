---
title: <add> 的 <transportConfigurationType>
ms.date: 03/30/2017
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
ms.openlocfilehash: 84ad745e7789fc2de8dcc23f3607b63702af05a1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55263444"
---
# <a name="add-of-transportconfigurationtype"></a><span data-ttu-id="6cc94-102">\<add> of \<transportConfigurationType></span><span class="sxs-lookup"><span data-stu-id="6cc94-102">\<add> of \<transportConfigurationType></span></span>
<span data-ttu-id="6cc94-103">此項目是索引鍵/值組，可用來識別特定傳輸的型別。</span><span class="sxs-lookup"><span data-stu-id="6cc94-103">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
 <span data-ttu-id="6cc94-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6cc94-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6cc94-105">\<ServiceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="6cc94-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="6cc94-106">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="6cc94-106">\<transportConfigurationTypes></span></span>  
<span data-ttu-id="6cc94-107">\<add></span><span class="sxs-lookup"><span data-stu-id="6cc94-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cc94-108">語法</span><span class="sxs-lookup"><span data-stu-id="6cc94-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6cc94-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6cc94-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6cc94-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="6cc94-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6cc94-111">屬性</span><span class="sxs-lookup"><span data-stu-id="6cc94-111">Attributes</span></span>  
  
|<span data-ttu-id="6cc94-112">屬性</span><span class="sxs-lookup"><span data-stu-id="6cc94-112">Attribute</span></span>|<span data-ttu-id="6cc94-113">描述</span><span class="sxs-lookup"><span data-stu-id="6cc94-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6cc94-114">name</span><span class="sxs-lookup"><span data-stu-id="6cc94-114">name</span></span>|<span data-ttu-id="6cc94-115">必要的 String 屬性。</span><span class="sxs-lookup"><span data-stu-id="6cc94-115">Required String attribute.</span></span><br /><br /> <span data-ttu-id="6cc94-116">包含唯一識別傳輸型別的使用者定義索引鍵。</span><span class="sxs-lookup"><span data-stu-id="6cc94-116">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="6cc94-117">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="6cc94-117">transportConfigurationType</span></span>|<span data-ttu-id="6cc94-118">字串，包含可實作特定傳輸的型別。</span><span class="sxs-lookup"><span data-stu-id="6cc94-118">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6cc94-119">子元素</span><span class="sxs-lookup"><span data-stu-id="6cc94-119">Child Elements</span></span>  
 <span data-ttu-id="6cc94-120">無</span><span class="sxs-lookup"><span data-stu-id="6cc94-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6cc94-121">父項目</span><span class="sxs-lookup"><span data-stu-id="6cc94-121">Parent Elements</span></span>  
  
|<span data-ttu-id="6cc94-122">項目</span><span class="sxs-lookup"><span data-stu-id="6cc94-122">Element</span></span>|<span data-ttu-id="6cc94-123">描述</span><span class="sxs-lookup"><span data-stu-id="6cc94-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6cc94-124">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="6cc94-124">\<transportConfigurationTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transportconfigurationtypes.md)|<span data-ttu-id="6cc94-125">實作特定傳輸之型別的集合。</span><span class="sxs-lookup"><span data-stu-id="6cc94-125">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6cc94-126">範例</span><span class="sxs-lookup"><span data-stu-id="6cc94-126">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="net.udp"
         transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="see-also"></a><span data-ttu-id="6cc94-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6cc94-127">See also</span></span>
- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="6cc94-128">裝載</span><span class="sxs-lookup"><span data-stu-id="6cc94-128">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
