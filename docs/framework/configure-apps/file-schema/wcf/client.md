---
title: <client>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: 2e0352efdd5b709984338fe4484b120bddb7d545
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164355"
---
# <a name="client"></a><span data-ttu-id="d0493-101">\<client></span><span class="sxs-lookup"><span data-stu-id="d0493-101">\<client></span></span>
<span data-ttu-id="d0493-102">`client` 項目會定義用戶端可連線的端點清單。</span><span class="sxs-lookup"><span data-stu-id="d0493-102">The `client` element defines a list of endpoints that a client can connect to.</span></span>  
  
 <span data-ttu-id="d0493-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d0493-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="d0493-104">\<client></span><span class="sxs-lookup"><span data-stu-id="d0493-104">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0493-105">語法</span><span class="sxs-lookup"><span data-stu-id="d0493-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <client>
    <endpoint>
    </endpoint>
    <metadata>
    </metadata>
  </client>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d0493-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d0493-106">Attributes and Elements</span></span>  
 <span data-ttu-id="d0493-107">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d0493-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d0493-108">屬性</span><span class="sxs-lookup"><span data-stu-id="d0493-108">Attributes</span></span>  
 <span data-ttu-id="d0493-109">None</span><span class="sxs-lookup"><span data-stu-id="d0493-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d0493-110">子元素</span><span class="sxs-lookup"><span data-stu-id="d0493-110">Child Elements</span></span>  
  
|<span data-ttu-id="d0493-111">項目</span><span class="sxs-lookup"><span data-stu-id="d0493-111">Element</span></span>|<span data-ttu-id="d0493-112">描述</span><span class="sxs-lookup"><span data-stu-id="d0493-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d0493-113">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="d0493-113">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|<span data-ttu-id="d0493-114">包含端點項目的清單，其中的端點項目指定這個用戶端可連線的端點。</span><span class="sxs-lookup"><span data-stu-id="d0493-114">Contains a collection of endpoint elements, that specify the endpoints that this client can connect to.</span></span>|  
|[<span data-ttu-id="d0493-115">\<metadata></span><span class="sxs-lookup"><span data-stu-id="d0493-115">\<metadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md)|<span data-ttu-id="d0493-116">包含處理中繼資料的設定。</span><span class="sxs-lookup"><span data-stu-id="d0493-116">Contains settings for processing metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d0493-117">父項目</span><span class="sxs-lookup"><span data-stu-id="d0493-117">Parent Elements</span></span>  
  
|<span data-ttu-id="d0493-118">項目</span><span class="sxs-lookup"><span data-stu-id="d0493-118">Element</span></span>|<span data-ttu-id="d0493-119">描述</span><span class="sxs-lookup"><span data-stu-id="d0493-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d0493-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d0493-120">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="d0493-121">所有 Windows Communication Foundation (WCF) 組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="d0493-121">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0493-122">備註</span><span class="sxs-lookup"><span data-stu-id="d0493-122">Remarks</span></span>  
 <span data-ttu-id="d0493-123">`client` 區段會定義用戶端可連線的端點清單。</span><span class="sxs-lookup"><span data-stu-id="d0493-123">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="d0493-124">在用戶端區段中定義的每個端點會定義它自己的繫結、行為和合約。</span><span class="sxs-lookup"><span data-stu-id="d0493-124">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="d0493-125">它是以 `name` 和 `contract` 屬性的組合唯一識別的。</span><span class="sxs-lookup"><span data-stu-id="d0493-125">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="d0493-126">用戶端程式碼指定 `name` 以連線至用戶端所實作服務的端點。</span><span class="sxs-lookup"><span data-stu-id="d0493-126">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="d0493-127">如果省略 `name` 屬性，則端點會做為它所實作合約的預設端點。</span><span class="sxs-lookup"><span data-stu-id="d0493-127">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>  
  
 <span data-ttu-id="d0493-128">此外，本區段也會指定處理中繼資料的設定。</span><span class="sxs-lookup"><span data-stu-id="d0493-128">In addition, this section also specifies settings for processing metadata.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0493-129">範例</span><span class="sxs-lookup"><span data-stu-id="d0493-129">Example</span></span>  
  
```xml  
<client>
  <endpoint address="/HelloWorld/"
            bindingConfiguration="usingDefaults"
            name="MyBinding"
            binding="customBinding"
            contract="HelloWorld">
    <addressProperties actingAs="http://www.microsoft.com/TestActor"
                       identityData="BasicReadWrite"
                       identityType="Spn"
                       isAddressPrivate="false">
  </endpoint>
</client>
```  
  
## <a name="see-also"></a><span data-ttu-id="d0493-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0493-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- [<span data-ttu-id="d0493-131">WCF 用戶端組態</span><span class="sxs-lookup"><span data-stu-id="d0493-131">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="d0493-132">用戶端</span><span class="sxs-lookup"><span data-stu-id="d0493-132">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
