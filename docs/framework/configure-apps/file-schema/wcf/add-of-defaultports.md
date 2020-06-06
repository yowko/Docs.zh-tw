---
title: <add> 的 <defaultPorts>
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: f5de2aa897a3bc37d08932451a2c7b94bc603b9e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400645"
---
# <a name="add-of-defaultports"></a><span data-ttu-id="cadc6-102">\<add> 的 \<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="cadc6-102">\<add> of \<defaultPorts></span></span>
<span data-ttu-id="cadc6-103">預設通訊端點，用戶端應用程式會接聽這個端點。</span><span class="sxs-lookup"><span data-stu-id="cadc6-103">A default communications endpoint that the client application listens to.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<useRequestHeadersForMetadataAddress>**](userequestheadersformetadataaddress.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultPorts>**](defaultports.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="cadc6-104">語法</span><span class="sxs-lookup"><span data-stu-id="cadc6-104">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cadc6-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cadc6-105">Attributes and Elements</span></span>  
 <span data-ttu-id="cadc6-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="cadc6-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cadc6-107">屬性</span><span class="sxs-lookup"><span data-stu-id="cadc6-107">Attributes</span></span>  
  
|<span data-ttu-id="cadc6-108">屬性</span><span class="sxs-lookup"><span data-stu-id="cadc6-108">Attribute</span></span>|<span data-ttu-id="cadc6-109">描述</span><span class="sxs-lookup"><span data-stu-id="cadc6-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cadc6-110">連接埠</span><span class="sxs-lookup"><span data-stu-id="cadc6-110">port</span></span>|<span data-ttu-id="cadc6-111">指定預設通訊埠編號的整數。</span><span class="sxs-lookup"><span data-stu-id="cadc6-111">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="cadc6-112">scheme</span><span class="sxs-lookup"><span data-stu-id="cadc6-112">scheme</span></span>|<span data-ttu-id="cadc6-113">指定與通訊連接埠相關之通訊協定設定群組的字串。</span><span class="sxs-lookup"><span data-stu-id="cadc6-113">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cadc6-114">子元素</span><span class="sxs-lookup"><span data-stu-id="cadc6-114">Child Elements</span></span>  
 <span data-ttu-id="cadc6-115">無。</span><span class="sxs-lookup"><span data-stu-id="cadc6-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cadc6-116">父項目</span><span class="sxs-lookup"><span data-stu-id="cadc6-116">Parent Elements</span></span>  
  
|<span data-ttu-id="cadc6-117">元素</span><span class="sxs-lookup"><span data-stu-id="cadc6-117">Element</span></span>|<span data-ttu-id="cadc6-118">描述</span><span class="sxs-lookup"><span data-stu-id="cadc6-118">Description</span></span>|  
|-------------|-----------------|  
|[\<defaultPorts>](defaultports.md)|<span data-ttu-id="cadc6-119">預設連接埠的集合，這些連接埠會接聽用戶端應用程式所接聽的預設通訊端點。</span><span class="sxs-lookup"><span data-stu-id="cadc6-119">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cadc6-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cadc6-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElement>
