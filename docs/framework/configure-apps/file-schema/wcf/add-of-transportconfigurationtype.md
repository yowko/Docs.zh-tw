---
title: <add> 的 <transportConfigurationType>
ms.date: 03/30/2017
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
ms.openlocfilehash: adf4cd7f02db6535c5950443d09476a9a5ff63fb
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850314"
---
# <a name="add-of-transportconfigurationtype"></a><span data-ttu-id="c0a02-102">\<新增 transportConfigurationType > \<的 ></span><span class="sxs-lookup"><span data-stu-id="c0a02-102">\<add> of \<transportConfigurationType></span></span>
<span data-ttu-id="c0a02-103">此項目是索引鍵/值組，可用來識別特定傳輸的型別。</span><span class="sxs-lookup"><span data-stu-id="c0a02-103">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
<span data-ttu-id="c0a02-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c0a02-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c0a02-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c0a02-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c0a02-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceHostingEnvironment >** ](servicehostingenvironment.md)</span><span class="sxs-lookup"><span data-stu-id="c0a02-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)</span></span>\
<span data-ttu-id="c0a02-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<transportConfigurationTypes >** ](transportconfigurationtypes.md)</span><span class="sxs-lookup"><span data-stu-id="c0a02-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<transportConfigurationTypes>**](transportconfigurationtypes.md)</span></span>\
<span data-ttu-id="c0a02-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<新增 >**</span><span class="sxs-lookup"><span data-stu-id="c0a02-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0a02-109">語法</span><span class="sxs-lookup"><span data-stu-id="c0a02-109">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0a02-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c0a02-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c0a02-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c0a02-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0a02-112">屬性</span><span class="sxs-lookup"><span data-stu-id="c0a02-112">Attributes</span></span>  
  
|<span data-ttu-id="c0a02-113">屬性</span><span class="sxs-lookup"><span data-stu-id="c0a02-113">Attribute</span></span>|<span data-ttu-id="c0a02-114">描述</span><span class="sxs-lookup"><span data-stu-id="c0a02-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c0a02-115">NAME</span><span class="sxs-lookup"><span data-stu-id="c0a02-115">name</span></span>|<span data-ttu-id="c0a02-116">必要的 String 屬性。</span><span class="sxs-lookup"><span data-stu-id="c0a02-116">Required String attribute.</span></span><br /><br /> <span data-ttu-id="c0a02-117">包含唯一識別傳輸型別的使用者定義索引鍵。</span><span class="sxs-lookup"><span data-stu-id="c0a02-117">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="c0a02-118">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="c0a02-118">transportConfigurationType</span></span>|<span data-ttu-id="c0a02-119">字串，包含可實作特定傳輸的型別。</span><span class="sxs-lookup"><span data-stu-id="c0a02-119">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c0a02-120">子元素</span><span class="sxs-lookup"><span data-stu-id="c0a02-120">Child Elements</span></span>  
 <span data-ttu-id="c0a02-121">None</span><span class="sxs-lookup"><span data-stu-id="c0a02-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c0a02-122">父項目</span><span class="sxs-lookup"><span data-stu-id="c0a02-122">Parent Elements</span></span>  
  
|<span data-ttu-id="c0a02-123">項目</span><span class="sxs-lookup"><span data-stu-id="c0a02-123">Element</span></span>|<span data-ttu-id="c0a02-124">描述</span><span class="sxs-lookup"><span data-stu-id="c0a02-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c0a02-125">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="c0a02-125">\<transportConfigurationTypes></span></span>](transportconfigurationtypes.md)|<span data-ttu-id="c0a02-126">實作特定傳輸之型別的集合。</span><span class="sxs-lookup"><span data-stu-id="c0a02-126">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c0a02-127">範例</span><span class="sxs-lookup"><span data-stu-id="c0a02-127">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="net.udp"
         transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="see-also"></a><span data-ttu-id="c0a02-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0a02-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="c0a02-129">裝載</span><span class="sxs-lookup"><span data-stu-id="c0a02-129">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
