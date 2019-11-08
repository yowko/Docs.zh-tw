---
title: <security> 的 <wsDualHttpBinding>
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
ms.openlocfilehash: 4969c041678bbf3490975bc0ec53507b6cf762bb
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738614"
---
# <a name="security-of-wsdualhttpbinding"></a><span data-ttu-id="2f72d-102">\<wsDualHttpBinding 的 \<安全性 > ></span><span class="sxs-lookup"><span data-stu-id="2f72d-102">\<security> of \<wsDualHttpBinding></span></span>
<span data-ttu-id="2f72d-103">定義[\<wsDualHttpBinding >](wsdualhttpbinding.md)的安全性功能。</span><span class="sxs-lookup"><span data-stu-id="2f72d-103">Defines the security capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>  
  
<span data-ttu-id="2f72d-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2f72d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2f72d-105">&nbsp; &nbsp;[ **\<system system.servicemodel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="2f72d-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="2f72d-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](bindings.md)系結 ></span><span class="sxs-lookup"><span data-stu-id="2f72d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="2f72d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsDualHttpBinding >** ](wsdualhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="2f72d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsDualHttpBinding>**](wsdualhttpbinding.md)</span></span>\
<span data-ttu-id="2f72d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<** 系結 ></span><span class="sxs-lookup"><span data-stu-id="2f72d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="2f72d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<安全性 >**</span><span class="sxs-lookup"><span data-stu-id="2f72d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f72d-110">語法</span><span class="sxs-lookup"><span data-stu-id="2f72d-110">Syntax</span></span>  
  
```xml  
<security mode="Message/None">
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           negotiateServiceCredential="Boolean"/>
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2f72d-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2f72d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2f72d-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2f72d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2f72d-113">屬性</span><span class="sxs-lookup"><span data-stu-id="2f72d-113">Attributes</span></span>  
  
|<span data-ttu-id="2f72d-114">屬性</span><span class="sxs-lookup"><span data-stu-id="2f72d-114">Attribute</span></span>|<span data-ttu-id="2f72d-115">描述</span><span class="sxs-lookup"><span data-stu-id="2f72d-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2f72d-116">模式</span><span class="sxs-lookup"><span data-stu-id="2f72d-116">mode</span></span>|<span data-ttu-id="2f72d-117">選擇性.</span><span class="sxs-lookup"><span data-stu-id="2f72d-117">-   Optional.</span></span> <span data-ttu-id="2f72d-118">指定套用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="2f72d-118">Specifies the type of security that is applied.</span></span> <span data-ttu-id="2f72d-119">預設值是 `Message`。</span><span class="sxs-lookup"><span data-stu-id="2f72d-119">The default value is `Message`.</span></span> <span data-ttu-id="2f72d-120">此屬性的型別為 <xref:System.ServiceModel.WSDualHttpSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="2f72d-120">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="2f72d-121">Mode 屬性</span><span class="sxs-lookup"><span data-stu-id="2f72d-121">Mode Attribute</span></span>  
  
|<span data-ttu-id="2f72d-122">值</span><span class="sxs-lookup"><span data-stu-id="2f72d-122">Value</span></span>|<span data-ttu-id="2f72d-123">描述</span><span class="sxs-lookup"><span data-stu-id="2f72d-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2f72d-124">None</span><span class="sxs-lookup"><span data-stu-id="2f72d-124">None</span></span>|<span data-ttu-id="2f72d-125">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="2f72d-125">Security is disabled.</span></span>|  
|<span data-ttu-id="2f72d-126">訊息</span><span class="sxs-lookup"><span data-stu-id="2f72d-126">Message</span></span>|<span data-ttu-id="2f72d-127">系統會使用 SOAP 訊息安全性來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="2f72d-127">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2f72d-128">子項目</span><span class="sxs-lookup"><span data-stu-id="2f72d-128">Child Elements</span></span>  
  
|<span data-ttu-id="2f72d-129">項目</span><span class="sxs-lookup"><span data-stu-id="2f72d-129">Element</span></span>|<span data-ttu-id="2f72d-130">描述</span><span class="sxs-lookup"><span data-stu-id="2f72d-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2f72d-131">\<message ></span><span class="sxs-lookup"><span data-stu-id="2f72d-131">\<message></span></span>](message-of-wsdualhttpbinding.md)|<span data-ttu-id="2f72d-132">定義訊息層級安全性的設定。</span><span class="sxs-lookup"><span data-stu-id="2f72d-132">Defines the settings for the message-level security.</span></span> <span data-ttu-id="2f72d-133">此項目的型別為 <xref:System.ServiceModel.MessageSecurityOverHttp>。</span><span class="sxs-lookup"><span data-stu-id="2f72d-133">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2f72d-134">父項目</span><span class="sxs-lookup"><span data-stu-id="2f72d-134">Parent Elements</span></span>  
  
|<span data-ttu-id="2f72d-135">項目</span><span class="sxs-lookup"><span data-stu-id="2f72d-135">Element</span></span>|<span data-ttu-id="2f72d-136">描述</span><span class="sxs-lookup"><span data-stu-id="2f72d-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2f72d-137">\<binding ></span><span class="sxs-lookup"><span data-stu-id="2f72d-137">\<binding></span></span>](bindings.md)|<span data-ttu-id="2f72d-138">定義[\<wsDualHttpBinding >](wsdualhttpbinding.md)的所有系結功能。</span><span class="sxs-lookup"><span data-stu-id="2f72d-138">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f72d-139">備註</span><span class="sxs-lookup"><span data-stu-id="2f72d-139">Remarks</span></span>  
 <span data-ttu-id="2f72d-140">雙重繫結會向服務公開用戶端的 IP 位址，</span><span class="sxs-lookup"><span data-stu-id="2f72d-140">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="2f72d-141">用戶端應該使用安全性確保本身只連接其信任的服務。</span><span class="sxs-lookup"><span data-stu-id="2f72d-141">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f72d-142">請參閱</span><span class="sxs-lookup"><span data-stu-id="2f72d-142">See also</span></span>

- <xref:System.ServiceModel.WSDualHttpSecurity>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="2f72d-143">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="2f72d-143">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="2f72d-144">繫結</span><span class="sxs-lookup"><span data-stu-id="2f72d-144">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="2f72d-145">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="2f72d-145">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="2f72d-146">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="2f72d-146">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="2f72d-147">\<binding ></span><span class="sxs-lookup"><span data-stu-id="2f72d-147">\<binding></span></span>](bindings.md)
