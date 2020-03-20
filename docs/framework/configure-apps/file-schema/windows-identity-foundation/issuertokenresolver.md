---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: 67d7e0aa5b6b05bfe8b17a1b1efebb1fbddbb0eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152667"
---
# <a name="issuertokenresolver"></a><span data-ttu-id="00aec-101">\<頒發者權杖解析器></span><span class="sxs-lookup"><span data-stu-id="00aec-101">\<issuerTokenResolver></span></span>
<span data-ttu-id="00aec-102">註冊權杖處理常式集合中處理常式使用的頒發者權杖解析器。</span><span class="sxs-lookup"><span data-stu-id="00aec-102">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="00aec-103">頒發者權杖解析器用於解析傳入權杖和消息上的簽名權杖。</span><span class="sxs-lookup"><span data-stu-id="00aec-103">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span>  
  
<span data-ttu-id="00aec-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="00aec-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="00aec-105">&nbsp;&nbsp;[**\<系統.身份模型>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="00aec-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="00aec-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<身份配置>**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="00aec-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="00aec-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<安全權杖處理常式>**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="00aec-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="00aec-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<安全權杖處理常式配置>**](securitytokenhandlerconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="00aec-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)</span></span>\
<span data-ttu-id="00aec-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<頒發者權杖解析器>**</span><span class="sxs-lookup"><span data-stu-id="00aec-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerTokenResolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00aec-110">語法</span><span class="sxs-lookup"><span data-stu-id="00aec-110">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerTokenResolver type=xs:string>  
        </issuerTokenResolver>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="00aec-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="00aec-111">Attributes and Elements</span></span>  
 <span data-ttu-id="00aec-112">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="00aec-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="00aec-113">屬性</span><span class="sxs-lookup"><span data-stu-id="00aec-113">Attributes</span></span>  
  
|<span data-ttu-id="00aec-114">屬性</span><span class="sxs-lookup"><span data-stu-id="00aec-114">Attribute</span></span>|<span data-ttu-id="00aec-115">描述</span><span class="sxs-lookup"><span data-stu-id="00aec-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="00aec-116">type</span><span class="sxs-lookup"><span data-stu-id="00aec-116">type</span></span>|<span data-ttu-id="00aec-117">指定頒發者權杖解析器的類型。</span><span class="sxs-lookup"><span data-stu-id="00aec-117">Specifies the type of the issuer token resolver.</span></span> <span data-ttu-id="00aec-118">必須是類<xref:System.IdentityModel.Tokens.IssuerTokenResolver>或從<xref:System.IdentityModel.Tokens.IssuerTokenResolver>類派生的類型。</span><span class="sxs-lookup"><span data-stu-id="00aec-118">Must be either the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class or a type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span> <span data-ttu-id="00aec-119">必要。</span><span class="sxs-lookup"><span data-stu-id="00aec-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="00aec-120">子元素</span><span class="sxs-lookup"><span data-stu-id="00aec-120">Child Elements</span></span>  
 <span data-ttu-id="00aec-121">None</span><span class="sxs-lookup"><span data-stu-id="00aec-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="00aec-122">父項目</span><span class="sxs-lookup"><span data-stu-id="00aec-122">Parent Elements</span></span>  
  
|<span data-ttu-id="00aec-123">元素</span><span class="sxs-lookup"><span data-stu-id="00aec-123">Element</span></span>|<span data-ttu-id="00aec-124">描述</span><span class="sxs-lookup"><span data-stu-id="00aec-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="00aec-125">\<安全權杖處理常式配置></span><span class="sxs-lookup"><span data-stu-id="00aec-125">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="00aec-126">為安全權杖處理常式的集合提供配置。</span><span class="sxs-lookup"><span data-stu-id="00aec-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00aec-127">備註</span><span class="sxs-lookup"><span data-stu-id="00aec-127">Remarks</span></span>  
 <span data-ttu-id="00aec-128">頒發者權杖解析器用於解析傳入權杖和消息上的簽名權杖。</span><span class="sxs-lookup"><span data-stu-id="00aec-128">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="00aec-129">它用於檢索用於檢查簽名的加密材料。</span><span class="sxs-lookup"><span data-stu-id="00aec-129">It is used to retrieve the cryptographic material that is used for checking the signature.</span></span> <span data-ttu-id="00aec-130">必須指定該`type`屬性。</span><span class="sxs-lookup"><span data-stu-id="00aec-130">You must specify the `type` attribute.</span></span> <span data-ttu-id="00aec-131">指定的類型可以是 或<xref:System.IdentityModel.Tokens.IssuerTokenResolver>派生自類的<xref:System.IdentityModel.Tokens.IssuerTokenResolver>自訂類型。</span><span class="sxs-lookup"><span data-stu-id="00aec-131">The type specified can be either <xref:System.IdentityModel.Tokens.IssuerTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span>  
  
 <span data-ttu-id="00aec-132">某些權杖處理常式允許您在配置中指定頒發者權杖解析器設置。</span><span class="sxs-lookup"><span data-stu-id="00aec-132">Some token handlers allow you to specify issuer token resolver settings in configuration.</span></span> <span data-ttu-id="00aec-133">各個權杖處理常式上的設置將覆蓋在安全權杖處理常式集合上指定的設置。</span><span class="sxs-lookup"><span data-stu-id="00aec-133">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="00aec-134">將`<issuerTokenResolver>`元素指定為[\<標識配置>](identityconfiguration.md)元素的子項目已被棄用，但仍支援向後相容性。</span><span class="sxs-lookup"><span data-stu-id="00aec-134">Specifying the `<issuerTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="00aec-135">元素上的`<securityTokenHandlerConfiguration>`設置將覆蓋元素上的`<identityConfiguration>`設置。</span><span class="sxs-lookup"><span data-stu-id="00aec-135">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00aec-136">範例</span><span class="sxs-lookup"><span data-stu-id="00aec-136">Example</span></span>  
 <span data-ttu-id="00aec-137">以下 XML 顯示基於 派生的<xref:System.IdentityModel.Tokens.IssuerTokenResolver>自訂類的頒發者權杖解析器的配置。</span><span class="sxs-lookup"><span data-stu-id="00aec-137">The following XML shows configuration for an issuer token resolver that is based on a custom class that derives from <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span></span> <span data-ttu-id="00aec-138">權杖解析器維護從為類定義的自訂配置元素 （`<AddAudienceKeyPair>`） 初始化的便捷鍵對字典。</span><span class="sxs-lookup"><span data-stu-id="00aec-138">The token resolver maintains a dictionary of audience-key pairs that is initialized from a custom configuration element (`<AddAudienceKeyPair>`) defined for the class.</span></span> <span data-ttu-id="00aec-139">類重寫處理<xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A>此元素的方法。</span><span class="sxs-lookup"><span data-stu-id="00aec-139">The class overrides the <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> method to process this element.</span></span> <span data-ttu-id="00aec-140">重寫顯示在以下示例中;如下例中所示。但是，它調用的方法不顯示為簡潔。</span><span class="sxs-lookup"><span data-stu-id="00aec-140">The override is shown in the following example; however, the methods it calls are not shown for brevity.</span></span> <span data-ttu-id="00aec-141">有關完整示例，請參閱示例`CustomToken`。</span><span class="sxs-lookup"><span data-stu-id="00aec-141">For the complete example, see the `CustomToken` sample.</span></span>  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a><span data-ttu-id="00aec-142">範例</span><span class="sxs-lookup"><span data-stu-id="00aec-142">Example</span></span>
  
```csharp
public override void LoadCustomConfiguration(System.Xml.XmlNodeList nodelist)  
{  
    foreach (XmlNode node in nodelist)  
    {  
        XmlDictionaryReader rdr = XmlDictionaryReader.CreateDictionaryReader(new XmlTextReader(new StringReader(node.OuterXml)));  
        rdr.MoveToContent();  
  
        string symmetricKey = rdr.GetAttribute("symmetricKey");  
        string audience = rdr.GetAttribute("audience");  
  
        this.AddAudienceKeyPair(audience, symmetricKey);  
    }  
}  
```
  
## <a name="see-also"></a><span data-ttu-id="00aec-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00aec-143">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
