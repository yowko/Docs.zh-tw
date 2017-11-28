---
title: "&lt;用戶端&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 67f91f4462fc8c11b1769d5805a4ad1407385a50
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltclientgt"></a><span data-ttu-id="787e9-102">&lt;用戶端&gt;</span><span class="sxs-lookup"><span data-stu-id="787e9-102">&lt;client&gt;</span></span>
<span data-ttu-id="787e9-103">`client` 項目會定義用戶端可連線的端點清單。</span><span class="sxs-lookup"><span data-stu-id="787e9-103">The `client` element defines a list of endpoints that a client can connect to.</span></span>  
  
 <span data-ttu-id="787e9-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="787e9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="787e9-105">\<用戶端 ></span><span class="sxs-lookup"><span data-stu-id="787e9-105">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="787e9-106">語法</span><span class="sxs-lookup"><span data-stu-id="787e9-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="787e9-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="787e9-107">Attributes and Elements</span></span>  
 <span data-ttu-id="787e9-108">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="787e9-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="787e9-109">屬性</span><span class="sxs-lookup"><span data-stu-id="787e9-109">Attributes</span></span>  
 <span data-ttu-id="787e9-110">無</span><span class="sxs-lookup"><span data-stu-id="787e9-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="787e9-111">子元素</span><span class="sxs-lookup"><span data-stu-id="787e9-111">Child Elements</span></span>  
  
|<span data-ttu-id="787e9-112">項目</span><span class="sxs-lookup"><span data-stu-id="787e9-112">Element</span></span>|<span data-ttu-id="787e9-113">說明</span><span class="sxs-lookup"><span data-stu-id="787e9-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="787e9-114">\<端點 ></span><span class="sxs-lookup"><span data-stu-id="787e9-114">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|<span data-ttu-id="787e9-115">包含端點項目的清單，其中的端點項目指定這個用戶端可連線的端點。</span><span class="sxs-lookup"><span data-stu-id="787e9-115">Contains a collection of endpoint elements, that specify the endpoints that this client can connect to.</span></span>|  
|[<span data-ttu-id="787e9-116">\<中繼資料 ></span><span class="sxs-lookup"><span data-stu-id="787e9-116">\<metadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md)|<span data-ttu-id="787e9-117">包含處理中繼資料的設定。</span><span class="sxs-lookup"><span data-stu-id="787e9-117">Contains settings for processing metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="787e9-118">父項目</span><span class="sxs-lookup"><span data-stu-id="787e9-118">Parent Elements</span></span>  
  
|<span data-ttu-id="787e9-119">項目</span><span class="sxs-lookup"><span data-stu-id="787e9-119">Element</span></span>|<span data-ttu-id="787e9-120">說明</span><span class="sxs-lookup"><span data-stu-id="787e9-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="787e9-121">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="787e9-121">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="787e9-122">所有 Windows Communication Foundation (WCF) 組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="787e9-122">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="787e9-123">備註</span><span class="sxs-lookup"><span data-stu-id="787e9-123">Remarks</span></span>  
 <span data-ttu-id="787e9-124">`client` 區段會定義用戶端可連線的端點清單。</span><span class="sxs-lookup"><span data-stu-id="787e9-124">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="787e9-125">在用戶端區段中定義的每個端點會定義它自己的繫結、行為和合約。</span><span class="sxs-lookup"><span data-stu-id="787e9-125">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="787e9-126">它是以 `name` 和 `contract` 屬性的組合唯一識別的。</span><span class="sxs-lookup"><span data-stu-id="787e9-126">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="787e9-127">用戶端程式碼指定 `name` 以連線至用戶端所實作服務的端點。</span><span class="sxs-lookup"><span data-stu-id="787e9-127">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="787e9-128">如果省略 `name` 屬性，則端點會做為它所實作合約的預設端點。</span><span class="sxs-lookup"><span data-stu-id="787e9-128">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>  
  
 <span data-ttu-id="787e9-129">此外，本區段也會指定處理中繼資料的設定。</span><span class="sxs-lookup"><span data-stu-id="787e9-129">In addition, this section also specifies settings for processing metadata.</span></span>  
  
## <a name="example"></a><span data-ttu-id="787e9-130">範例</span><span class="sxs-lookup"><span data-stu-id="787e9-130">Example</span></span>  
  
```xml  
<client>  
    <endpoint address="/HelloWorld/"  
              bindingConfiguration="usingDefaults"  
              name="MyBinding"  
              binding="customBinding"  
              contract="HelloWorld">  
    <addressProperties actingAs="http://www.microsoft.com/TestActor"  
             identityData="BasicReadWrite" identityType="Spn" isAddressPrivate="false">  
    </endpoint>  
</client>  
```  
  
## <a name="see-also"></a><span data-ttu-id="787e9-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="787e9-131">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientSection>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 [<span data-ttu-id="787e9-132">WCF 用戶端組態</span><span class="sxs-lookup"><span data-stu-id="787e9-132">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="787e9-133">用戶端</span><span class="sxs-lookup"><span data-stu-id="787e9-133">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
