---
title: <client>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: b3234bfa60cd1e3c88778951fc27301c615c84ba
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148954"
---
# \<client>

<span data-ttu-id="2e3ea-101">`client` 項目會定義用戶端可連線的端點清單。</span><span class="sxs-lookup"><span data-stu-id="2e3ea-101">The `client` element defines a list of endpoints that a client can connect to.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<client>**

## <a name="syntax"></a><span data-ttu-id="2e3ea-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="2e3ea-102">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="2e3ea-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2e3ea-103">Attributes and Elements</span></span>

 <span data-ttu-id="2e3ea-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="2e3ea-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="2e3ea-105">屬性</span><span class="sxs-lookup"><span data-stu-id="2e3ea-105">Attributes</span></span>

 <span data-ttu-id="2e3ea-106">無</span><span class="sxs-lookup"><span data-stu-id="2e3ea-106">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="2e3ea-107">子元素</span><span class="sxs-lookup"><span data-stu-id="2e3ea-107">Child Elements</span></span>

|<span data-ttu-id="2e3ea-108">項目</span><span class="sxs-lookup"><span data-stu-id="2e3ea-108">Element</span></span>|<span data-ttu-id="2e3ea-109">描述</span><span class="sxs-lookup"><span data-stu-id="2e3ea-109">Description</span></span>|
|-------------|-----------------|
|[\<endpoint>](endpoint-of-client.md)|<span data-ttu-id="2e3ea-110">包含端點專案的集合，這些專案會指定此用戶端可以連接的端點。</span><span class="sxs-lookup"><span data-stu-id="2e3ea-110">Contains a collection of endpoint elements that specify the endpoints that this client can connect to.</span></span>|
|[\<metadata>](metadata.md)|<span data-ttu-id="2e3ea-111">包含處理中繼資料的設定。</span><span class="sxs-lookup"><span data-stu-id="2e3ea-111">Contains settings for processing metadata.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2e3ea-112">父項目</span><span class="sxs-lookup"><span data-stu-id="2e3ea-112">Parent Elements</span></span>

|<span data-ttu-id="2e3ea-113">項目</span><span class="sxs-lookup"><span data-stu-id="2e3ea-113">Element</span></span>|<span data-ttu-id="2e3ea-114">描述</span><span class="sxs-lookup"><span data-stu-id="2e3ea-114">Description</span></span>|
|-------------|-----------------|
|[\<system.serviceModel>](system-servicemodel.md)|<span data-ttu-id="2e3ea-115">所有 Windows Communication Foundation (WCF) 組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="2e3ea-115">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2e3ea-116">備註</span><span class="sxs-lookup"><span data-stu-id="2e3ea-116">Remarks</span></span>

 <span data-ttu-id="2e3ea-117">`client` 區段會定義用戶端可連線的端點清單。</span><span class="sxs-lookup"><span data-stu-id="2e3ea-117">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="2e3ea-118">在用戶端區段中定義的每個端點會定義它自己的繫結、行為和合約。</span><span class="sxs-lookup"><span data-stu-id="2e3ea-118">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="2e3ea-119">它是以 `name` 和 `contract` 屬性的組合唯一識別的。</span><span class="sxs-lookup"><span data-stu-id="2e3ea-119">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="2e3ea-120">用戶端程式碼指定 `name` 以連線至用戶端所實作服務的端點。</span><span class="sxs-lookup"><span data-stu-id="2e3ea-120">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="2e3ea-121">如果省略 `name` 屬性，則端點會做為它所實作合約的預設端點。</span><span class="sxs-lookup"><span data-stu-id="2e3ea-121">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>

 <span data-ttu-id="2e3ea-122">此外，本區段也會指定處理中繼資料的設定。</span><span class="sxs-lookup"><span data-stu-id="2e3ea-122">In addition, this section also specifies settings for processing metadata.</span></span>

## <a name="example"></a><span data-ttu-id="2e3ea-123">範例</span><span class="sxs-lookup"><span data-stu-id="2e3ea-123">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2e3ea-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e3ea-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- [<span data-ttu-id="2e3ea-125">WCF 用戶端組態</span><span class="sxs-lookup"><span data-stu-id="2e3ea-125">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="2e3ea-126">用戶端</span><span class="sxs-lookup"><span data-stu-id="2e3ea-126">Clients</span></span>](../../../wcf/feature-details/clients.md)
