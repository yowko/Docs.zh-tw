---
title: <security> 的 <wsDualHttpBinding>
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
ms.openlocfilehash: 7398cd538bb240e78413575f7c28abe7f797d05c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162201"
---
# <a name="security-of-wsdualhttpbinding"></a><span data-ttu-id="a0c91-102">\<security> 的 \<wsDualHttpBinding></span><span class="sxs-lookup"><span data-stu-id="a0c91-102">\<security> of \<wsDualHttpBinding></span></span>

<span data-ttu-id="a0c91-103">定義的安全性功能 [\<wsDualHttpBinding>](wsdualhttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="a0c91-103">Defines the security capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsDualHttpBinding>**](wsdualhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="a0c91-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="a0c91-104">Syntax</span></span>  
  
```xml  
<security mode="Message/None">
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           negotiateServiceCredential="Boolean"/>
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a0c91-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a0c91-105">Attributes and Elements</span></span>  

 <span data-ttu-id="a0c91-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a0c91-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a0c91-107">屬性</span><span class="sxs-lookup"><span data-stu-id="a0c91-107">Attributes</span></span>  
  
|<span data-ttu-id="a0c91-108">屬性</span><span class="sxs-lookup"><span data-stu-id="a0c91-108">Attribute</span></span>|<span data-ttu-id="a0c91-109">描述</span><span class="sxs-lookup"><span data-stu-id="a0c91-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a0c91-110">mode</span><span class="sxs-lookup"><span data-stu-id="a0c91-110">mode</span></span>|<span data-ttu-id="a0c91-111">參數.</span><span class="sxs-lookup"><span data-stu-id="a0c91-111">-   Optional.</span></span> <span data-ttu-id="a0c91-112">指定套用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="a0c91-112">Specifies the type of security that is applied.</span></span> <span data-ttu-id="a0c91-113">預設值是 `Message`。</span><span class="sxs-lookup"><span data-stu-id="a0c91-113">The default value is `Message`.</span></span> <span data-ttu-id="a0c91-114">此屬性的型別為 <xref:System.ServiceModel.WSDualHttpSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="a0c91-114">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="a0c91-115">Mode 屬性</span><span class="sxs-lookup"><span data-stu-id="a0c91-115">Mode Attribute</span></span>  
  
|<span data-ttu-id="a0c91-116">值</span><span class="sxs-lookup"><span data-stu-id="a0c91-116">Value</span></span>|<span data-ttu-id="a0c91-117">描述</span><span class="sxs-lookup"><span data-stu-id="a0c91-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a0c91-118">無</span><span class="sxs-lookup"><span data-stu-id="a0c91-118">None</span></span>|<span data-ttu-id="a0c91-119">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="a0c91-119">Security is disabled.</span></span>|  
|<span data-ttu-id="a0c91-120">訊息</span><span class="sxs-lookup"><span data-stu-id="a0c91-120">Message</span></span>|<span data-ttu-id="a0c91-121">系統會使用 SOAP 訊息安全性來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="a0c91-121">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a0c91-122">子元素</span><span class="sxs-lookup"><span data-stu-id="a0c91-122">Child Elements</span></span>  
  
|<span data-ttu-id="a0c91-123">項目</span><span class="sxs-lookup"><span data-stu-id="a0c91-123">Element</span></span>|<span data-ttu-id="a0c91-124">描述</span><span class="sxs-lookup"><span data-stu-id="a0c91-124">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-of-wsdualhttpbinding.md)|<span data-ttu-id="a0c91-125">定義訊息層級安全性的設定。</span><span class="sxs-lookup"><span data-stu-id="a0c91-125">Defines the settings for the message-level security.</span></span> <span data-ttu-id="a0c91-126">此項目的型別為 <xref:System.ServiceModel.MessageSecurityOverHttp>。</span><span class="sxs-lookup"><span data-stu-id="a0c91-126">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a0c91-127">父項目</span><span class="sxs-lookup"><span data-stu-id="a0c91-127">Parent Elements</span></span>  
  
|<span data-ttu-id="a0c91-128">項目</span><span class="sxs-lookup"><span data-stu-id="a0c91-128">Element</span></span>|<span data-ttu-id="a0c91-129">描述</span><span class="sxs-lookup"><span data-stu-id="a0c91-129">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="a0c91-130">定義的所有系結功能 [\<wsDualHttpBinding>](wsdualhttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="a0c91-130">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0c91-131">備註</span><span class="sxs-lookup"><span data-stu-id="a0c91-131">Remarks</span></span>  

 <span data-ttu-id="a0c91-132">雙重繫結會向服務公開用戶端的 IP 位址，</span><span class="sxs-lookup"><span data-stu-id="a0c91-132">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="a0c91-133">用戶端應該使用安全性確保本身只連接其信任的服務。</span><span class="sxs-lookup"><span data-stu-id="a0c91-133">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0c91-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0c91-134">See also</span></span>

- <xref:System.ServiceModel.WSDualHttpSecurity>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="a0c91-135">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="a0c91-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="a0c91-136">繫結</span><span class="sxs-lookup"><span data-stu-id="a0c91-136">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a0c91-137">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="a0c91-137">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a0c91-138">使用繫結來設定服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="a0c91-138">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
