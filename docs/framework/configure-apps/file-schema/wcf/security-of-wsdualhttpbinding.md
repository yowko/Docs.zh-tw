---
title: <security> 的 <wsDualHttpBinding>
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
ms.openlocfilehash: 4969c041678bbf3490975bc0ec53507b6cf762bb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738614"
---
# <a name="security-of-wsdualhttpbinding"></a><span data-ttu-id="0fc89-102">\<security> 的 \<wsDualHttpBinding></span><span class="sxs-lookup"><span data-stu-id="0fc89-102">\<security> of \<wsDualHttpBinding></span></span>
<span data-ttu-id="0fc89-103">定義的安全性功能 [\<wsDualHttpBinding>](wsdualhttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="0fc89-103">Defines the security capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsDualHttpBinding>**](wsdualhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="0fc89-104">語法</span><span class="sxs-lookup"><span data-stu-id="0fc89-104">Syntax</span></span>  
  
```xml  
<security mode="Message/None">
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           negotiateServiceCredential="Boolean"/>
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0fc89-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0fc89-105">Attributes and Elements</span></span>  
 <span data-ttu-id="0fc89-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="0fc89-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0fc89-107">屬性</span><span class="sxs-lookup"><span data-stu-id="0fc89-107">Attributes</span></span>  
  
|<span data-ttu-id="0fc89-108">屬性</span><span class="sxs-lookup"><span data-stu-id="0fc89-108">Attribute</span></span>|<span data-ttu-id="0fc89-109">描述</span><span class="sxs-lookup"><span data-stu-id="0fc89-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0fc89-110">mode</span><span class="sxs-lookup"><span data-stu-id="0fc89-110">mode</span></span>|<span data-ttu-id="0fc89-111">選擇性.</span><span class="sxs-lookup"><span data-stu-id="0fc89-111">-   Optional.</span></span> <span data-ttu-id="0fc89-112">指定套用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="0fc89-112">Specifies the type of security that is applied.</span></span> <span data-ttu-id="0fc89-113">預設值是 `Message`。</span><span class="sxs-lookup"><span data-stu-id="0fc89-113">The default value is `Message`.</span></span> <span data-ttu-id="0fc89-114">此屬性的型別為 <xref:System.ServiceModel.WSDualHttpSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="0fc89-114">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="0fc89-115">Mode 屬性</span><span class="sxs-lookup"><span data-stu-id="0fc89-115">Mode Attribute</span></span>  
  
|<span data-ttu-id="0fc89-116">值</span><span class="sxs-lookup"><span data-stu-id="0fc89-116">Value</span></span>|<span data-ttu-id="0fc89-117">描述</span><span class="sxs-lookup"><span data-stu-id="0fc89-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0fc89-118">None</span><span class="sxs-lookup"><span data-stu-id="0fc89-118">None</span></span>|<span data-ttu-id="0fc89-119">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="0fc89-119">Security is disabled.</span></span>|  
|<span data-ttu-id="0fc89-120">訊息</span><span class="sxs-lookup"><span data-stu-id="0fc89-120">Message</span></span>|<span data-ttu-id="0fc89-121">系統會使用 SOAP 訊息安全性來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="0fc89-121">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0fc89-122">子元素</span><span class="sxs-lookup"><span data-stu-id="0fc89-122">Child Elements</span></span>  
  
|<span data-ttu-id="0fc89-123">元素</span><span class="sxs-lookup"><span data-stu-id="0fc89-123">Element</span></span>|<span data-ttu-id="0fc89-124">描述</span><span class="sxs-lookup"><span data-stu-id="0fc89-124">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-of-wsdualhttpbinding.md)|<span data-ttu-id="0fc89-125">定義訊息層級安全性的設定。</span><span class="sxs-lookup"><span data-stu-id="0fc89-125">Defines the settings for the message-level security.</span></span> <span data-ttu-id="0fc89-126">此項目的型別為 <xref:System.ServiceModel.MessageSecurityOverHttp>。</span><span class="sxs-lookup"><span data-stu-id="0fc89-126">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0fc89-127">父項目</span><span class="sxs-lookup"><span data-stu-id="0fc89-127">Parent Elements</span></span>  
  
|<span data-ttu-id="0fc89-128">元素</span><span class="sxs-lookup"><span data-stu-id="0fc89-128">Element</span></span>|<span data-ttu-id="0fc89-129">描述</span><span class="sxs-lookup"><span data-stu-id="0fc89-129">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="0fc89-130">定義的所有系結功能 [\<wsDualHttpBinding>](wsdualhttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="0fc89-130">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0fc89-131">備註</span><span class="sxs-lookup"><span data-stu-id="0fc89-131">Remarks</span></span>  
 <span data-ttu-id="0fc89-132">雙重繫結會向服務公開用戶端的 IP 位址，</span><span class="sxs-lookup"><span data-stu-id="0fc89-132">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="0fc89-133">用戶端應該使用安全性確保本身只連接其信任的服務。</span><span class="sxs-lookup"><span data-stu-id="0fc89-133">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fc89-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0fc89-134">See also</span></span>

- <xref:System.ServiceModel.WSDualHttpSecurity>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="0fc89-135">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="0fc89-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="0fc89-136">繫結</span><span class="sxs-lookup"><span data-stu-id="0fc89-136">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0fc89-137">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="0fc89-137">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="0fc89-138">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="0fc89-138">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
