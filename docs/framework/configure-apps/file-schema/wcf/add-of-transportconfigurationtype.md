---
title: <add> 的 <transportConfigurationType>
ms.date: 03/30/2017
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
ms.openlocfilehash: 483ede53df13c896b88171910031dbe9793d66dc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920039"
---
# <a name="add-of-transportconfigurationtype"></a><span data-ttu-id="b8df6-102">\<新增 transportConfigurationType > \<的 ></span><span class="sxs-lookup"><span data-stu-id="b8df6-102">\<add> of \<transportConfigurationType></span></span>
<span data-ttu-id="b8df6-103">此項目是索引鍵/值組，可用來識別特定傳輸的型別。</span><span class="sxs-lookup"><span data-stu-id="b8df6-103">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
 <span data-ttu-id="b8df6-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b8df6-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b8df6-105">\<ServiceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="b8df6-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="b8df6-106">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="b8df6-106">\<transportConfigurationTypes></span></span>  
<span data-ttu-id="b8df6-107">\<add></span><span class="sxs-lookup"><span data-stu-id="b8df6-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8df6-108">語法</span><span class="sxs-lookup"><span data-stu-id="b8df6-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8df6-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b8df6-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b8df6-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="b8df6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8df6-111">屬性</span><span class="sxs-lookup"><span data-stu-id="b8df6-111">Attributes</span></span>  
  
|<span data-ttu-id="b8df6-112">屬性</span><span class="sxs-lookup"><span data-stu-id="b8df6-112">Attribute</span></span>|<span data-ttu-id="b8df6-113">描述</span><span class="sxs-lookup"><span data-stu-id="b8df6-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b8df6-114">NAME</span><span class="sxs-lookup"><span data-stu-id="b8df6-114">name</span></span>|<span data-ttu-id="b8df6-115">必要的 String 屬性。</span><span class="sxs-lookup"><span data-stu-id="b8df6-115">Required String attribute.</span></span><br /><br /> <span data-ttu-id="b8df6-116">包含唯一識別傳輸型別的使用者定義索引鍵。</span><span class="sxs-lookup"><span data-stu-id="b8df6-116">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="b8df6-117">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="b8df6-117">transportConfigurationType</span></span>|<span data-ttu-id="b8df6-118">字串，包含可實作特定傳輸的型別。</span><span class="sxs-lookup"><span data-stu-id="b8df6-118">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b8df6-119">子元素</span><span class="sxs-lookup"><span data-stu-id="b8df6-119">Child Elements</span></span>  
 <span data-ttu-id="b8df6-120">None</span><span class="sxs-lookup"><span data-stu-id="b8df6-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b8df6-121">父項目</span><span class="sxs-lookup"><span data-stu-id="b8df6-121">Parent Elements</span></span>  
  
|<span data-ttu-id="b8df6-122">項目</span><span class="sxs-lookup"><span data-stu-id="b8df6-122">Element</span></span>|<span data-ttu-id="b8df6-123">說明</span><span class="sxs-lookup"><span data-stu-id="b8df6-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b8df6-124">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="b8df6-124">\<transportConfigurationTypes></span></span>](transportconfigurationtypes.md)|<span data-ttu-id="b8df6-125">實作特定傳輸之型別的集合。</span><span class="sxs-lookup"><span data-stu-id="b8df6-125">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b8df6-126">範例</span><span class="sxs-lookup"><span data-stu-id="b8df6-126">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="net.udp"
         transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="see-also"></a><span data-ttu-id="b8df6-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8df6-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="b8df6-128">裝載</span><span class="sxs-lookup"><span data-stu-id="b8df6-128">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
