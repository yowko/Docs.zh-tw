---
title: '&lt;issuerTokenResolver&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 02e2beb285cb0c4d88f98c3155ab5a3ff5e31e0b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltissuertokenresolvergt"></a><span data-ttu-id="6d8dc-102">&lt;issuerTokenResolver&gt;</span><span class="sxs-lookup"><span data-stu-id="6d8dc-102">&lt;issuerTokenResolver&gt;</span></span>
<span data-ttu-id="6d8dc-103">註冊由權杖處理常式集合中的處理常式的簽發者權杖解析程式。</span><span class="sxs-lookup"><span data-stu-id="6d8dc-103">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="6d8dc-104">簽發者的語彙基元解析程式用來解析內送的語彙基元和訊息簽署權杖。</span><span class="sxs-lookup"><span data-stu-id="6d8dc-104">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span>  
  
 <span data-ttu-id="6d8dc-105">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="6d8dc-105">\<system.identityModel></span></span>  
<span data-ttu-id="6d8dc-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="6d8dc-106">\<identityConfiguration></span></span>  
<span data-ttu-id="6d8dc-107">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="6d8dc-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="6d8dc-108">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="6d8dc-108">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="6d8dc-109">\<issuerTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="6d8dc-109">\<issuerTokenResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d8dc-110">語法</span><span class="sxs-lookup"><span data-stu-id="6d8dc-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6d8dc-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6d8dc-111">Attributes and Elements</span></span>  
 <span data-ttu-id="6d8dc-112">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="6d8dc-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6d8dc-113">屬性</span><span class="sxs-lookup"><span data-stu-id="6d8dc-113">Attributes</span></span>  
  
|<span data-ttu-id="6d8dc-114">屬性</span><span class="sxs-lookup"><span data-stu-id="6d8dc-114">Attribute</span></span>|<span data-ttu-id="6d8dc-115">描述</span><span class="sxs-lookup"><span data-stu-id="6d8dc-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6d8dc-116">類型</span><span class="sxs-lookup"><span data-stu-id="6d8dc-116">type</span></span>|<span data-ttu-id="6d8dc-117">指定簽發者的語彙基元解析程式類型。</span><span class="sxs-lookup"><span data-stu-id="6d8dc-117">Specifies the type of the issuer token resolver.</span></span> <span data-ttu-id="6d8dc-118">必須是<xref:System.IdentityModel.Tokens.IssuerTokenResolver>類別或衍生自型別<xref:System.IdentityModel.Tokens.IssuerTokenResolver>類別。</span><span class="sxs-lookup"><span data-stu-id="6d8dc-118">Must be either the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class or a type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span> <span data-ttu-id="6d8dc-119">必要項。</span><span class="sxs-lookup"><span data-stu-id="6d8dc-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6d8dc-120">子元素</span><span class="sxs-lookup"><span data-stu-id="6d8dc-120">Child Elements</span></span>  
 <span data-ttu-id="6d8dc-121">無</span><span class="sxs-lookup"><span data-stu-id="6d8dc-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6d8dc-122">父項目</span><span class="sxs-lookup"><span data-stu-id="6d8dc-122">Parent Elements</span></span>  
  
|<span data-ttu-id="6d8dc-123">項目</span><span class="sxs-lookup"><span data-stu-id="6d8dc-123">Element</span></span>|<span data-ttu-id="6d8dc-124">說明</span><span class="sxs-lookup"><span data-stu-id="6d8dc-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6d8dc-125">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="6d8dc-125">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="6d8dc-126">提供組態集合的安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="6d8dc-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d8dc-127">備註</span><span class="sxs-lookup"><span data-stu-id="6d8dc-127">Remarks</span></span>  
 <span data-ttu-id="6d8dc-128">簽發者的語彙基元解析程式用來解析內送的語彙基元和訊息簽署權杖。</span><span class="sxs-lookup"><span data-stu-id="6d8dc-128">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="6d8dc-129">它用來擷取用來檢查簽章的加密編譯內容。</span><span class="sxs-lookup"><span data-stu-id="6d8dc-129">It is used to retrieve the cryptographic material that is used for checking the signature.</span></span> <span data-ttu-id="6d8dc-130">您必須指定`type`屬性。</span><span class="sxs-lookup"><span data-stu-id="6d8dc-130">You must specify the `type` attribute.</span></span> <span data-ttu-id="6d8dc-131">指定的型別可以是<xref:System.IdentityModel.Tokens.IssuerTokenResolver>或自訂型別衍生自<xref:System.IdentityModel.Tokens.IssuerTokenResolver>類別。</span><span class="sxs-lookup"><span data-stu-id="6d8dc-131">The type specified can be either <xref:System.IdentityModel.Tokens.IssuerTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span>  
  
 <span data-ttu-id="6d8dc-132">某些權杖處理常式可讓您在組態中指定簽發者權杖解析程式設定。</span><span class="sxs-lookup"><span data-stu-id="6d8dc-132">Some token handlers allow you to specify issuer token resolver settings in configuration.</span></span> <span data-ttu-id="6d8dc-133">在個別的語彙基元處理常式上的設定會覆寫安全性權杖處理常式集合上指定。</span><span class="sxs-lookup"><span data-stu-id="6d8dc-133">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6d8dc-134">指定`<issuerTokenResolver>`為的子元素的項目[ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)項目已被取代，但仍支援回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="6d8dc-134">Specifying the `<issuerTokenResolver>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="6d8dc-135">設定`<securityTokenHandlerConfiguration>`元素會覆寫上`<identityConfiguration>`項目。</span><span class="sxs-lookup"><span data-stu-id="6d8dc-135">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d8dc-136">範例</span><span class="sxs-lookup"><span data-stu-id="6d8dc-136">Example</span></span>  
 <span data-ttu-id="6d8dc-137">下列 XML 顯示設定簽發者權杖解析程式為基礎的自訂類別衍生自<xref:System.IdentityModel.Tokens.IssuerTokenResolver>。</span><span class="sxs-lookup"><span data-stu-id="6d8dc-137">The following XML shows configuration for an issuer token resolver that is based on a custom class that derives from <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span></span> <span data-ttu-id="6d8dc-138">語彙基元解析程式會維護初始化自自訂組態項目之對象金鑰組的字典 (`<AddAudienceKeyPair>`) 為類別定義。</span><span class="sxs-lookup"><span data-stu-id="6d8dc-138">The token resolver maintains a dictionary of audience-key pairs that is initialized from a custom configuration element (`<AddAudienceKeyPair>`) defined for the class.</span></span> <span data-ttu-id="6d8dc-139">類別會覆寫<xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A>方法來處理這個項目。</span><span class="sxs-lookup"><span data-stu-id="6d8dc-139">The class overrides the <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> method to process this element.</span></span> <span data-ttu-id="6d8dc-140">覆寫會顯示在下列範例中。不過，它會呼叫的方法不會顯示為求簡單明瞭。</span><span class="sxs-lookup"><span data-stu-id="6d8dc-140">The override is shown in the following example; however, the methods it calls are not shown for brevity.</span></span> <span data-ttu-id="6d8dc-141">完整的範例，請參閱`CustomToken`範例。</span><span class="sxs-lookup"><span data-stu-id="6d8dc-141">For the complete example, see the `CustomToken` sample.</span></span>  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a><span data-ttu-id="6d8dc-142">範例</span><span class="sxs-lookup"><span data-stu-id="6d8dc-142">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6d8dc-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d8dc-143">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
