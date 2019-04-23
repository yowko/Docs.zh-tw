---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: 08082d2e6647f07f33df72ab79dac00c15a1cd1b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59200814"
---
# <a name="issuertokenresolver"></a><span data-ttu-id="5e1e4-101">\<issuerTokenResolver></span><span class="sxs-lookup"><span data-stu-id="5e1e4-101">\<issuerTokenResolver></span></span>
<span data-ttu-id="5e1e4-102">註冊由權杖處理常式集合中的處理常式的簽發者權杖解析程式。</span><span class="sxs-lookup"><span data-stu-id="5e1e4-102">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="5e1e4-103">簽發者權杖解析程式用來解析簽署的權杖上傳入的權杖和訊息。</span><span class="sxs-lookup"><span data-stu-id="5e1e4-103">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span>  
  
 <span data-ttu-id="5e1e4-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="5e1e4-104">\<system.identityModel></span></span>  
<span data-ttu-id="5e1e4-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="5e1e4-105">\<identityConfiguration></span></span>  
<span data-ttu-id="5e1e4-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="5e1e4-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="5e1e4-107">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="5e1e4-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="5e1e4-108">\<issuerTokenResolver></span><span class="sxs-lookup"><span data-stu-id="5e1e4-108">\<issuerTokenResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e1e4-109">語法</span><span class="sxs-lookup"><span data-stu-id="5e1e4-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5e1e4-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5e1e4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5e1e4-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="5e1e4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5e1e4-112">屬性</span><span class="sxs-lookup"><span data-stu-id="5e1e4-112">Attributes</span></span>  
  
|<span data-ttu-id="5e1e4-113">屬性</span><span class="sxs-lookup"><span data-stu-id="5e1e4-113">Attribute</span></span>|<span data-ttu-id="5e1e4-114">描述</span><span class="sxs-lookup"><span data-stu-id="5e1e4-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5e1e4-115">類型</span><span class="sxs-lookup"><span data-stu-id="5e1e4-115">type</span></span>|<span data-ttu-id="5e1e4-116">指定簽發者權杖解析程式類型。</span><span class="sxs-lookup"><span data-stu-id="5e1e4-116">Specifies the type of the issuer token resolver.</span></span> <span data-ttu-id="5e1e4-117">必須是<xref:System.IdentityModel.Tokens.IssuerTokenResolver>類別或衍生自類型<xref:System.IdentityModel.Tokens.IssuerTokenResolver>類別。</span><span class="sxs-lookup"><span data-stu-id="5e1e4-117">Must be either the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class or a type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span> <span data-ttu-id="5e1e4-118">必要項。</span><span class="sxs-lookup"><span data-stu-id="5e1e4-118">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5e1e4-119">子元素</span><span class="sxs-lookup"><span data-stu-id="5e1e4-119">Child Elements</span></span>  
 <span data-ttu-id="5e1e4-120">None</span><span class="sxs-lookup"><span data-stu-id="5e1e4-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5e1e4-121">父項目</span><span class="sxs-lookup"><span data-stu-id="5e1e4-121">Parent Elements</span></span>  
  
|<span data-ttu-id="5e1e4-122">項目</span><span class="sxs-lookup"><span data-stu-id="5e1e4-122">Element</span></span>|<span data-ttu-id="5e1e4-123">描述</span><span class="sxs-lookup"><span data-stu-id="5e1e4-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5e1e4-124">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="5e1e4-124">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="5e1e4-125">提供組態集合的安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="5e1e4-125">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e1e4-126">備註</span><span class="sxs-lookup"><span data-stu-id="5e1e4-126">Remarks</span></span>  
 <span data-ttu-id="5e1e4-127">簽發者權杖解析程式用來解析簽署的權杖上傳入的權杖和訊息。</span><span class="sxs-lookup"><span data-stu-id="5e1e4-127">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="5e1e4-128">它用來擷取用來檢查簽章的加密編譯內容。</span><span class="sxs-lookup"><span data-stu-id="5e1e4-128">It is used to retrieve the cryptographic material that is used for checking the signature.</span></span> <span data-ttu-id="5e1e4-129">您必須指定`type`屬性。</span><span class="sxs-lookup"><span data-stu-id="5e1e4-129">You must specify the `type` attribute.</span></span> <span data-ttu-id="5e1e4-130">指定的型別可以是<xref:System.IdentityModel.Tokens.IssuerTokenResolver>或自訂的型別衍生自<xref:System.IdentityModel.Tokens.IssuerTokenResolver>類別。</span><span class="sxs-lookup"><span data-stu-id="5e1e4-130">The type specified can be either <xref:System.IdentityModel.Tokens.IssuerTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span>  
  
 <span data-ttu-id="5e1e4-131">某些權杖處理常式可讓您在組態中指定簽發者權杖解析程式設定。</span><span class="sxs-lookup"><span data-stu-id="5e1e4-131">Some token handlers allow you to specify issuer token resolver settings in configuration.</span></span> <span data-ttu-id="5e1e4-132">在個別的權杖處理常式上的設定會覆寫所指定的安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="5e1e4-132">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e1e4-133">指定`<issuerTokenResolver>`元素的子元素當做[ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)項目已被取代，但仍支援回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="5e1e4-133">Specifying the `<issuerTokenResolver>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="5e1e4-134">上的設定`<securityTokenHandlerConfiguration>`項目會覆寫上`<identityConfiguration>`項目。</span><span class="sxs-lookup"><span data-stu-id="5e1e4-134">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e1e4-135">範例</span><span class="sxs-lookup"><span data-stu-id="5e1e4-135">Example</span></span>  
 <span data-ttu-id="5e1e4-136">下列 XML 顯示組態的簽發者權杖解析程式為基礎的自訂類別衍生自<xref:System.IdentityModel.Tokens.IssuerTokenResolver>。</span><span class="sxs-lookup"><span data-stu-id="5e1e4-136">The following XML shows configuration for an issuer token resolver that is based on a custom class that derives from <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span></span> <span data-ttu-id="5e1e4-137">權杖解析程式會維護對象索引鍵組的字典，初始化從自訂的組態項目 (`<AddAudienceKeyPair>`) 定義的類別。</span><span class="sxs-lookup"><span data-stu-id="5e1e4-137">The token resolver maintains a dictionary of audience-key pairs that is initialized from a custom configuration element (`<AddAudienceKeyPair>`) defined for the class.</span></span> <span data-ttu-id="5e1e4-138">類別會覆寫<xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A>方法來處理這個項目。</span><span class="sxs-lookup"><span data-stu-id="5e1e4-138">The class overrides the <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> method to process this element.</span></span> <span data-ttu-id="5e1e4-139">覆寫會顯示在下列範例中，不過，它會呼叫的方法不會顯示為求簡單明瞭。</span><span class="sxs-lookup"><span data-stu-id="5e1e4-139">The override is shown in the following example; however, the methods it calls are not shown for brevity.</span></span> <span data-ttu-id="5e1e4-140">完整的範例，請參閱`CustomToken`範例。</span><span class="sxs-lookup"><span data-stu-id="5e1e4-140">For the complete example, see the `CustomToken` sample.</span></span>  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a><span data-ttu-id="5e1e4-141">範例</span><span class="sxs-lookup"><span data-stu-id="5e1e4-141">Example</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="5e1e4-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e1e4-142">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
