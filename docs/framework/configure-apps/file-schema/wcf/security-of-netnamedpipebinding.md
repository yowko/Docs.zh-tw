---
title: <security> 的 <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
ms.openlocfilehash: 31ea31ce6880a770c966350cd931e487396c4d63
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736445"
---
# <a name="security-of-netnamedpipebinding"></a><span data-ttu-id="bd02b-102">\<security> 的 \<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="bd02b-102">\<security> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="bd02b-103">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="bd02b-103">Defines the security settings for a binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netNamedPipeBinding>**](netnamedpipebinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="bd02b-104">語法</span><span class="sxs-lookup"><span data-stu-id="bd02b-104">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bd02b-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="bd02b-105">Attributes and Elements</span></span>  
 <span data-ttu-id="bd02b-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="bd02b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bd02b-107">屬性</span><span class="sxs-lookup"><span data-stu-id="bd02b-107">Attributes</span></span>  
  
|<span data-ttu-id="bd02b-108">屬性</span><span class="sxs-lookup"><span data-stu-id="bd02b-108">Attribute</span></span>|<span data-ttu-id="bd02b-109">描述</span><span class="sxs-lookup"><span data-stu-id="bd02b-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bd02b-110">mode</span><span class="sxs-lookup"><span data-stu-id="bd02b-110">mode</span></span>|<span data-ttu-id="bd02b-111">指定套用至這個繫結的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="bd02b-111">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="bd02b-112">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="bd02b-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="bd02b-113">-None：這會停用安全性。</span><span class="sxs-lookup"><span data-stu-id="bd02b-113">-   None: This disables security.</span></span><br /><span data-ttu-id="bd02b-114">-Transport：安全性是以基礎傳輸為基礎的安全性來提供。</span><span class="sxs-lookup"><span data-stu-id="bd02b-114">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="bd02b-115">您可以使用此模式來控制保護等級。</span><span class="sxs-lookup"><span data-stu-id="bd02b-115">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="bd02b-116">-預設值是 Transport。</span><span class="sxs-lookup"><span data-stu-id="bd02b-116">-   The default value is Transport.</span></span> <span data-ttu-id="bd02b-117">此屬性的型別為 <xref:System.ServiceModel.NetNamedPipeSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="bd02b-117">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bd02b-118">子元素</span><span class="sxs-lookup"><span data-stu-id="bd02b-118">Child Elements</span></span>  
  
|<span data-ttu-id="bd02b-119">元素</span><span class="sxs-lookup"><span data-stu-id="bd02b-119">Element</span></span>|<span data-ttu-id="bd02b-120">描述</span><span class="sxs-lookup"><span data-stu-id="bd02b-120">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bd02b-121">傳輸</span><span class="sxs-lookup"><span data-stu-id="bd02b-121">transport</span></span>|<span data-ttu-id="bd02b-122">定義傳輸的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="bd02b-122">Defines the security settings for the transport.</span></span> <span data-ttu-id="bd02b-123">此項目的型別為 <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="bd02b-123">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bd02b-124">父項目</span><span class="sxs-lookup"><span data-stu-id="bd02b-124">Parent Elements</span></span>  
  
|<span data-ttu-id="bd02b-125">元素</span><span class="sxs-lookup"><span data-stu-id="bd02b-125">Element</span></span>|<span data-ttu-id="bd02b-126">描述</span><span class="sxs-lookup"><span data-stu-id="bd02b-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bd02b-127">繫結</span><span class="sxs-lookup"><span data-stu-id="bd02b-127">binding</span></span>|<span data-ttu-id="bd02b-128">的繫結項目 [\<netNamedPipeBinding>](netnamedpipebinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="bd02b-128">The binding element of the [\<netNamedPipeBinding>](netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bd02b-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd02b-129">See also</span></span>

- <xref:System.ServiceModel.NetNamedPipeSecurity>
- <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>
- [<span data-ttu-id="bd02b-130">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="bd02b-130">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="bd02b-131">選取認證類型</span><span class="sxs-lookup"><span data-stu-id="bd02b-131">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="bd02b-132">繫結</span><span class="sxs-lookup"><span data-stu-id="bd02b-132">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="bd02b-133">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="bd02b-133">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="bd02b-134">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="bd02b-134">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
