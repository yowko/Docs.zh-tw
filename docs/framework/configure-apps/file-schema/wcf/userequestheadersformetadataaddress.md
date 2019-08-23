---
title: <useRequestHeadersForMetadataAddress>
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: 84310d4ae5e04e76e4484f4fc606c9896239c776
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940556"
---
# <a name="userequestheadersformetadataaddress"></a><span data-ttu-id="4aacc-101">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="4aacc-101">\<useRequestHeadersForMetadataAddress></span></span>
<span data-ttu-id="4aacc-102">允許從要求訊息標題擷取中繼資料位址資訊。</span><span class="sxs-lookup"><span data-stu-id="4aacc-102">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="4aacc-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4aacc-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="4aacc-104">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="4aacc-104">\<behaviors></span></span>  
<span data-ttu-id="4aacc-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="4aacc-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="4aacc-106">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="4aacc-106">\<behavior></span></span>  
<span data-ttu-id="4aacc-107">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="4aacc-107">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4aacc-108">語法</span><span class="sxs-lookup"><span data-stu-id="4aacc-108">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4aacc-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4aacc-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4aacc-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="4aacc-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4aacc-111">屬性</span><span class="sxs-lookup"><span data-stu-id="4aacc-111">Attributes</span></span>  
 <span data-ttu-id="4aacc-112">無。</span><span class="sxs-lookup"><span data-stu-id="4aacc-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4aacc-113">子元素</span><span class="sxs-lookup"><span data-stu-id="4aacc-113">Child Elements</span></span>  
  
|<span data-ttu-id="4aacc-114">項目</span><span class="sxs-lookup"><span data-stu-id="4aacc-114">Element</span></span>|<span data-ttu-id="4aacc-115">描述</span><span class="sxs-lookup"><span data-stu-id="4aacc-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4aacc-116">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="4aacc-116">\<defaultPorts></span></span>](defaultports.md)|<span data-ttu-id="4aacc-117">預設連接埠的集合，這些連接埠會接聽用戶端應用程式所接聽的預設通訊端點。</span><span class="sxs-lookup"><span data-stu-id="4aacc-117">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4aacc-118">父項目</span><span class="sxs-lookup"><span data-stu-id="4aacc-118">Parent Elements</span></span>  
  
|<span data-ttu-id="4aacc-119">項目</span><span class="sxs-lookup"><span data-stu-id="4aacc-119">Element</span></span>|<span data-ttu-id="4aacc-120">描述</span><span class="sxs-lookup"><span data-stu-id="4aacc-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4aacc-121">\<behavior></span><span class="sxs-lookup"><span data-stu-id="4aacc-121">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="4aacc-122">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="4aacc-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4aacc-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4aacc-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
