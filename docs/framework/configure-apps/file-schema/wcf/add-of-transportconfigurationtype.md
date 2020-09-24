---
title: <add> 的 <transportConfigurationType>
ms.date: 03/30/2017
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
ms.openlocfilehash: 9bef44ed39ee892080342058206f779b38fb460d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151151"
---
# <a name="add-of-transportconfigurationtype"></a><span data-ttu-id="16f6b-102">\<add> 的 \<transportConfigurationType></span><span class="sxs-lookup"><span data-stu-id="16f6b-102">\<add> of \<transportConfigurationType></span></span>

<span data-ttu-id="16f6b-103">此項目是索引鍵/值組，可用來識別特定傳輸的型別。</span><span class="sxs-lookup"><span data-stu-id="16f6b-103">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<transportConfigurationTypes>**](transportconfigurationtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="16f6b-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="16f6b-104">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="16f6b-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="16f6b-105">Attributes and Elements</span></span>  

 <span data-ttu-id="16f6b-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="16f6b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="16f6b-107">屬性</span><span class="sxs-lookup"><span data-stu-id="16f6b-107">Attributes</span></span>  
  
|<span data-ttu-id="16f6b-108">屬性</span><span class="sxs-lookup"><span data-stu-id="16f6b-108">Attribute</span></span>|<span data-ttu-id="16f6b-109">描述</span><span class="sxs-lookup"><span data-stu-id="16f6b-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="16f6b-110">NAME</span><span class="sxs-lookup"><span data-stu-id="16f6b-110">name</span></span>|<span data-ttu-id="16f6b-111">必要的 String 屬性。</span><span class="sxs-lookup"><span data-stu-id="16f6b-111">Required String attribute.</span></span><br /><br /> <span data-ttu-id="16f6b-112">包含唯一識別傳輸型別的使用者定義索引鍵。</span><span class="sxs-lookup"><span data-stu-id="16f6b-112">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="16f6b-113">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="16f6b-113">transportConfigurationType</span></span>|<span data-ttu-id="16f6b-114">字串，包含可實作特定傳輸的型別。</span><span class="sxs-lookup"><span data-stu-id="16f6b-114">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="16f6b-115">子元素</span><span class="sxs-lookup"><span data-stu-id="16f6b-115">Child Elements</span></span>  

 <span data-ttu-id="16f6b-116">無</span><span class="sxs-lookup"><span data-stu-id="16f6b-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="16f6b-117">父項目</span><span class="sxs-lookup"><span data-stu-id="16f6b-117">Parent Elements</span></span>  
  
|<span data-ttu-id="16f6b-118">項目</span><span class="sxs-lookup"><span data-stu-id="16f6b-118">Element</span></span>|<span data-ttu-id="16f6b-119">描述</span><span class="sxs-lookup"><span data-stu-id="16f6b-119">Description</span></span>|  
|-------------|-----------------|  
|[\<transportConfigurationTypes>](transportconfigurationtypes.md)|<span data-ttu-id="16f6b-120">實作特定傳輸之型別的集合。</span><span class="sxs-lookup"><span data-stu-id="16f6b-120">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="16f6b-121">範例</span><span class="sxs-lookup"><span data-stu-id="16f6b-121">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="net.udp"
         transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="see-also"></a><span data-ttu-id="16f6b-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16f6b-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="16f6b-123">Hosting</span><span class="sxs-lookup"><span data-stu-id="16f6b-123">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
