---
title: <transportConfigurationTypes>
ms.date: 03/30/2017
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
ms.openlocfilehash: 6545e1f1be2695d165b89a38c7218e0acdc88bfc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162019"
---
# \<transportConfigurationTypes>

<span data-ttu-id="f15bf-101">代表組態項目的集合，這些項目會識別特定傳輸的類型。</span><span class="sxs-lookup"><span data-stu-id="f15bf-101">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="f15bf-102">這可以用來加入自訂 WAS 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="f15bf-102">This can be used to add custom WAS protocols.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transportConfigurationTypes>**  
  
## <a name="syntax"></a><span data-ttu-id="f15bf-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="f15bf-103">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f15bf-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f15bf-104">Attributes and Elements</span></span>  

 <span data-ttu-id="f15bf-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f15bf-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f15bf-106">屬性</span><span class="sxs-lookup"><span data-stu-id="f15bf-106">Attributes</span></span>  
  
|<span data-ttu-id="f15bf-107">屬性</span><span class="sxs-lookup"><span data-stu-id="f15bf-107">Attribute</span></span>|<span data-ttu-id="f15bf-108">描述</span><span class="sxs-lookup"><span data-stu-id="f15bf-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f15bf-109">NAME</span><span class="sxs-lookup"><span data-stu-id="f15bf-109">name</span></span>|<span data-ttu-id="f15bf-110">傳輸的名稱</span><span class="sxs-lookup"><span data-stu-id="f15bf-110">The name of the transport</span></span>|  
|<span data-ttu-id="f15bf-111">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="f15bf-111">transportConfigurationType</span></span>|<span data-ttu-id="f15bf-112">實作傳輸的型別</span><span class="sxs-lookup"><span data-stu-id="f15bf-112">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f15bf-113">子元素</span><span class="sxs-lookup"><span data-stu-id="f15bf-113">Child Elements</span></span>  
  
|<span data-ttu-id="f15bf-114">項目</span><span class="sxs-lookup"><span data-stu-id="f15bf-114">Element</span></span>|<span data-ttu-id="f15bf-115">描述</span><span class="sxs-lookup"><span data-stu-id="f15bf-115">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-transportconfigurationtype.md)|<span data-ttu-id="f15bf-116">新增組態項目，此項目會識別特定傳輸的類型。</span><span class="sxs-lookup"><span data-stu-id="f15bf-116">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f15bf-117">父項目</span><span class="sxs-lookup"><span data-stu-id="f15bf-117">Parent Elements</span></span>  
  
|<span data-ttu-id="f15bf-118">項目</span><span class="sxs-lookup"><span data-stu-id="f15bf-118">Element</span></span>|<span data-ttu-id="f15bf-119">描述</span><span class="sxs-lookup"><span data-stu-id="f15bf-119">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="f15bf-120">定義服務裝載環境為特定傳輸產生的類型。</span><span class="sxs-lookup"><span data-stu-id="f15bf-120">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f15bf-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f15bf-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>
- [<span data-ttu-id="f15bf-122">Hosting</span><span class="sxs-lookup"><span data-stu-id="f15bf-122">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
