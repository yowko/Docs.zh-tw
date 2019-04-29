---
title: <add> 的 <transportConfigurationType>
ms.date: 03/30/2017
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
ms.openlocfilehash: c71a58b13e89bedb5eed24d784c82fb1525f7625
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701433"
---
# <a name="add-of-transportconfigurationtype"></a><span data-ttu-id="e05b5-102">\<add> of \<transportConfigurationType></span><span class="sxs-lookup"><span data-stu-id="e05b5-102">\<add> of \<transportConfigurationType></span></span>
<span data-ttu-id="e05b5-103">此項目是索引鍵/值組，可用來識別特定傳輸的型別。</span><span class="sxs-lookup"><span data-stu-id="e05b5-103">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
 <span data-ttu-id="e05b5-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e05b5-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e05b5-105">\<ServiceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="e05b5-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="e05b5-106">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="e05b5-106">\<transportConfigurationTypes></span></span>  
<span data-ttu-id="e05b5-107">\<add></span><span class="sxs-lookup"><span data-stu-id="e05b5-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e05b5-108">語法</span><span class="sxs-lookup"><span data-stu-id="e05b5-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e05b5-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e05b5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e05b5-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e05b5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e05b5-111">屬性</span><span class="sxs-lookup"><span data-stu-id="e05b5-111">Attributes</span></span>  
  
|<span data-ttu-id="e05b5-112">屬性</span><span class="sxs-lookup"><span data-stu-id="e05b5-112">Attribute</span></span>|<span data-ttu-id="e05b5-113">描述</span><span class="sxs-lookup"><span data-stu-id="e05b5-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e05b5-114">名稱</span><span class="sxs-lookup"><span data-stu-id="e05b5-114">name</span></span>|<span data-ttu-id="e05b5-115">必要的 String 屬性。</span><span class="sxs-lookup"><span data-stu-id="e05b5-115">Required String attribute.</span></span><br /><br /> <span data-ttu-id="e05b5-116">包含唯一識別傳輸型別的使用者定義索引鍵。</span><span class="sxs-lookup"><span data-stu-id="e05b5-116">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="e05b5-117">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="e05b5-117">transportConfigurationType</span></span>|<span data-ttu-id="e05b5-118">字串，包含可實作特定傳輸的型別。</span><span class="sxs-lookup"><span data-stu-id="e05b5-118">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e05b5-119">子元素</span><span class="sxs-lookup"><span data-stu-id="e05b5-119">Child Elements</span></span>  
 <span data-ttu-id="e05b5-120">None</span><span class="sxs-lookup"><span data-stu-id="e05b5-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e05b5-121">父項目</span><span class="sxs-lookup"><span data-stu-id="e05b5-121">Parent Elements</span></span>  
  
|<span data-ttu-id="e05b5-122">項目</span><span class="sxs-lookup"><span data-stu-id="e05b5-122">Element</span></span>|<span data-ttu-id="e05b5-123">描述</span><span class="sxs-lookup"><span data-stu-id="e05b5-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e05b5-124">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="e05b5-124">\<transportConfigurationTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transportconfigurationtypes.md)|<span data-ttu-id="e05b5-125">實作特定傳輸之型別的集合。</span><span class="sxs-lookup"><span data-stu-id="e05b5-125">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e05b5-126">範例</span><span class="sxs-lookup"><span data-stu-id="e05b5-126">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="net.udp"
         transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="see-also"></a><span data-ttu-id="e05b5-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e05b5-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="e05b5-128">裝載</span><span class="sxs-lookup"><span data-stu-id="e05b5-128">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
