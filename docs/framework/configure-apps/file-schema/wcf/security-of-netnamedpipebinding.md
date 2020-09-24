---
title: <security> 的 <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
ms.openlocfilehash: 1a231a60d29cc6a4460de69a98753c23c0386027
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170034"
---
# <a name="security-of-netnamedpipebinding"></a><span data-ttu-id="83b74-102">\<security> 的 \<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="83b74-102">\<security> of \<netNamedPipeBinding></span></span>

<span data-ttu-id="83b74-103">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="83b74-103">Defines the security settings for a binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netNamedPipeBinding>**](netnamedpipebinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="83b74-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="83b74-104">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="83b74-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="83b74-105">Attributes and Elements</span></span>  

 <span data-ttu-id="83b74-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="83b74-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="83b74-107">屬性</span><span class="sxs-lookup"><span data-stu-id="83b74-107">Attributes</span></span>  
  
|<span data-ttu-id="83b74-108">屬性</span><span class="sxs-lookup"><span data-stu-id="83b74-108">Attribute</span></span>|<span data-ttu-id="83b74-109">描述</span><span class="sxs-lookup"><span data-stu-id="83b74-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="83b74-110">mode</span><span class="sxs-lookup"><span data-stu-id="83b74-110">mode</span></span>|<span data-ttu-id="83b74-111">指定套用至這個繫結的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="83b74-111">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="83b74-112">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="83b74-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="83b74-113">-None：這會停用安全性。</span><span class="sxs-lookup"><span data-stu-id="83b74-113">-   None: This disables security.</span></span><br /><span data-ttu-id="83b74-114">-Transport：使用基礎傳輸型安全性來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="83b74-114">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="83b74-115">您可以使用此模式來控制保護等級。</span><span class="sxs-lookup"><span data-stu-id="83b74-115">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="83b74-116">-預設值為 Transport。</span><span class="sxs-lookup"><span data-stu-id="83b74-116">-   The default value is Transport.</span></span> <span data-ttu-id="83b74-117">此屬性的型別為 <xref:System.ServiceModel.NetNamedPipeSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="83b74-117">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="83b74-118">子元素</span><span class="sxs-lookup"><span data-stu-id="83b74-118">Child Elements</span></span>  
  
|<span data-ttu-id="83b74-119">項目</span><span class="sxs-lookup"><span data-stu-id="83b74-119">Element</span></span>|<span data-ttu-id="83b74-120">描述</span><span class="sxs-lookup"><span data-stu-id="83b74-120">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="83b74-121">傳輸</span><span class="sxs-lookup"><span data-stu-id="83b74-121">transport</span></span>|<span data-ttu-id="83b74-122">定義傳輸的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="83b74-122">Defines the security settings for the transport.</span></span> <span data-ttu-id="83b74-123">此項目的型別為 <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="83b74-123">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="83b74-124">父項目</span><span class="sxs-lookup"><span data-stu-id="83b74-124">Parent Elements</span></span>  
  
|<span data-ttu-id="83b74-125">項目</span><span class="sxs-lookup"><span data-stu-id="83b74-125">Element</span></span>|<span data-ttu-id="83b74-126">描述</span><span class="sxs-lookup"><span data-stu-id="83b74-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="83b74-127">繫結</span><span class="sxs-lookup"><span data-stu-id="83b74-127">binding</span></span>|<span data-ttu-id="83b74-128">的繫結項目 [\<netNamedPipeBinding>](netnamedpipebinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="83b74-128">The binding element of the [\<netNamedPipeBinding>](netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="83b74-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83b74-129">See also</span></span>

- <xref:System.ServiceModel.NetNamedPipeSecurity>
- <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>
- [<span data-ttu-id="83b74-130">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="83b74-130">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="83b74-131">選取認證類型</span><span class="sxs-lookup"><span data-stu-id="83b74-131">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="83b74-132">繫結</span><span class="sxs-lookup"><span data-stu-id="83b74-132">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="83b74-133">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="83b74-133">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="83b74-134">使用繫結來設定服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="83b74-134">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
