---
title: <transportConfigurationTypes>
ms.date: 03/30/2017
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
ms.openlocfilehash: 4be08f780c1095b0016bd130b5719a2a7307d019
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854935"
---
# <a name="transportconfigurationtypes"></a><span data-ttu-id="8cea0-101">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="8cea0-101">\<transportConfigurationTypes></span></span>
<span data-ttu-id="8cea0-102">代表組態項目的集合，這些項目會識別特定傳輸的類型。</span><span class="sxs-lookup"><span data-stu-id="8cea0-102">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="8cea0-103">這可以用來加入自訂 WAS 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="8cea0-103">This can be used to add custom WAS protocols.</span></span>  
  
<span data-ttu-id="8cea0-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8cea0-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8cea0-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="8cea0-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="8cea0-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceHostingEnvironment >** ](servicehostingenvironment.md)</span><span class="sxs-lookup"><span data-stu-id="8cea0-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)</span></span>\
<span data-ttu-id="8cea0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<transportConfigurationTypes >**</span><span class="sxs-lookup"><span data-stu-id="8cea0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transportConfigurationTypes>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cea0-108">語法</span><span class="sxs-lookup"><span data-stu-id="8cea0-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8cea0-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8cea0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8cea0-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="8cea0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8cea0-111">屬性</span><span class="sxs-lookup"><span data-stu-id="8cea0-111">Attributes</span></span>  
  
|<span data-ttu-id="8cea0-112">屬性</span><span class="sxs-lookup"><span data-stu-id="8cea0-112">Attribute</span></span>|<span data-ttu-id="8cea0-113">描述</span><span class="sxs-lookup"><span data-stu-id="8cea0-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8cea0-114">NAME</span><span class="sxs-lookup"><span data-stu-id="8cea0-114">name</span></span>|<span data-ttu-id="8cea0-115">傳輸的名稱</span><span class="sxs-lookup"><span data-stu-id="8cea0-115">The name of the transport</span></span>|  
|<span data-ttu-id="8cea0-116">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="8cea0-116">transportConfigurationType</span></span>|<span data-ttu-id="8cea0-117">實作傳輸的型別</span><span class="sxs-lookup"><span data-stu-id="8cea0-117">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8cea0-118">子元素</span><span class="sxs-lookup"><span data-stu-id="8cea0-118">Child Elements</span></span>  
  
|<span data-ttu-id="8cea0-119">項目</span><span class="sxs-lookup"><span data-stu-id="8cea0-119">Element</span></span>|<span data-ttu-id="8cea0-120">描述</span><span class="sxs-lookup"><span data-stu-id="8cea0-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8cea0-121">\<add></span><span class="sxs-lookup"><span data-stu-id="8cea0-121">\<add></span></span>](add-of-transportconfigurationtype.md)|<span data-ttu-id="8cea0-122">新增組態項目，此項目會識別特定傳輸的類型。</span><span class="sxs-lookup"><span data-stu-id="8cea0-122">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8cea0-123">父項目</span><span class="sxs-lookup"><span data-stu-id="8cea0-123">Parent Elements</span></span>  
  
|<span data-ttu-id="8cea0-124">項目</span><span class="sxs-lookup"><span data-stu-id="8cea0-124">Element</span></span>|<span data-ttu-id="8cea0-125">描述</span><span class="sxs-lookup"><span data-stu-id="8cea0-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8cea0-126">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="8cea0-126">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="8cea0-127">定義服務裝載環境為特定傳輸產生的類型。</span><span class="sxs-lookup"><span data-stu-id="8cea0-127">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8cea0-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8cea0-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>
- [<span data-ttu-id="8cea0-129">裝載</span><span class="sxs-lookup"><span data-stu-id="8cea0-129">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
