---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: 8775e3044e58886cfa53a9fd9fc8b4b8ed2105b5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251945"
---
# <a name="issuertokenresolver"></a><span data-ttu-id="ecf57-101">\<issuerTokenResolver></span><span class="sxs-lookup"><span data-stu-id="ecf57-101">\<issuerTokenResolver></span></span>
<span data-ttu-id="ecf57-102">註冊權杖處理常式集合中處理常式所使用的簽發者 token 解析程式。</span><span class="sxs-lookup"><span data-stu-id="ecf57-102">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="ecf57-103">簽發者權杖解析程式是用來解析傳入權杖和訊息上的簽署權杖。</span><span class="sxs-lookup"><span data-stu-id="ecf57-103">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span>  
  
<span data-ttu-id="ecf57-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ecf57-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ecf57-105">&nbsp;&nbsp;[ **\<Microsoft.identitymodel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="ecf57-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="ecf57-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="ecf57-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="ecf57-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="ecf57-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="ecf57-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlerConfiguration >** ](securitytokenhandlerconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="ecf57-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)</span></span>\
<span data-ttu-id="ecf57-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<issuerTokenResolver >**</span><span class="sxs-lookup"><span data-stu-id="ecf57-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerTokenResolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecf57-110">語法</span><span class="sxs-lookup"><span data-stu-id="ecf57-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ecf57-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ecf57-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ecf57-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ecf57-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ecf57-113">屬性</span><span class="sxs-lookup"><span data-stu-id="ecf57-113">Attributes</span></span>  
  
|<span data-ttu-id="ecf57-114">屬性</span><span class="sxs-lookup"><span data-stu-id="ecf57-114">Attribute</span></span>|<span data-ttu-id="ecf57-115">描述</span><span class="sxs-lookup"><span data-stu-id="ecf57-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ecf57-116">型別</span><span class="sxs-lookup"><span data-stu-id="ecf57-116">type</span></span>|<span data-ttu-id="ecf57-117">指定簽發者 token 解析程式的類型。</span><span class="sxs-lookup"><span data-stu-id="ecf57-117">Specifies the type of the issuer token resolver.</span></span> <span data-ttu-id="ecf57-118">必須是<xref:System.IdentityModel.Tokens.IssuerTokenResolver>類別或衍生<xref:System.IdentityModel.Tokens.IssuerTokenResolver>自類別的類型。</span><span class="sxs-lookup"><span data-stu-id="ecf57-118">Must be either the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class or a type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span> <span data-ttu-id="ecf57-119">必要項。</span><span class="sxs-lookup"><span data-stu-id="ecf57-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ecf57-120">子元素</span><span class="sxs-lookup"><span data-stu-id="ecf57-120">Child Elements</span></span>  
 <span data-ttu-id="ecf57-121">None</span><span class="sxs-lookup"><span data-stu-id="ecf57-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ecf57-122">父項目</span><span class="sxs-lookup"><span data-stu-id="ecf57-122">Parent Elements</span></span>  
  
|<span data-ttu-id="ecf57-123">項目</span><span class="sxs-lookup"><span data-stu-id="ecf57-123">Element</span></span>|<span data-ttu-id="ecf57-124">描述</span><span class="sxs-lookup"><span data-stu-id="ecf57-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ecf57-125">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="ecf57-125">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="ecf57-126">提供安全性權杖處理常式集合的設定。</span><span class="sxs-lookup"><span data-stu-id="ecf57-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ecf57-127">備註</span><span class="sxs-lookup"><span data-stu-id="ecf57-127">Remarks</span></span>  
 <span data-ttu-id="ecf57-128">簽發者權杖解析程式是用來解析傳入權杖和訊息上的簽署權杖。</span><span class="sxs-lookup"><span data-stu-id="ecf57-128">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="ecf57-129">它是用來抓取用於檢查簽章的密碼編譯內容。</span><span class="sxs-lookup"><span data-stu-id="ecf57-129">It is used to retrieve the cryptographic material that is used for checking the signature.</span></span> <span data-ttu-id="ecf57-130">您必須指定`type`屬性。</span><span class="sxs-lookup"><span data-stu-id="ecf57-130">You must specify the `type` attribute.</span></span> <span data-ttu-id="ecf57-131">指定的型別可以是<xref:System.IdentityModel.Tokens.IssuerTokenResolver>或衍生<xref:System.IdentityModel.Tokens.IssuerTokenResolver>自類別的自訂型別。</span><span class="sxs-lookup"><span data-stu-id="ecf57-131">The type specified can be either <xref:System.IdentityModel.Tokens.IssuerTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span>  
  
 <span data-ttu-id="ecf57-132">某些權杖處理常式可讓您在設定中指定簽發者權杖解析程式設定。</span><span class="sxs-lookup"><span data-stu-id="ecf57-132">Some token handlers allow you to specify issuer token resolver settings in configuration.</span></span> <span data-ttu-id="ecf57-133">個別權杖處理常式上的設定會覆寫安全性權杖處理常式集合上指定的設定。</span><span class="sxs-lookup"><span data-stu-id="ecf57-133">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ecf57-134">將專案指定為[ \<identityConfiguration >](identityconfiguration.md)專案的子項目已被取代, 但仍支援回溯相容性。 `<issuerTokenResolver>`</span><span class="sxs-lookup"><span data-stu-id="ecf57-134">Specifying the `<issuerTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="ecf57-135">元素上的`<securityTokenHandlerConfiguration>`設定會覆寫專案`<identityConfiguration>`上的專案。</span><span class="sxs-lookup"><span data-stu-id="ecf57-135">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ecf57-136">範例</span><span class="sxs-lookup"><span data-stu-id="ecf57-136">Example</span></span>  
 <span data-ttu-id="ecf57-137">下列 XML 會根據衍生<xref:System.IdentityModel.Tokens.IssuerTokenResolver>自的自訂類別, 顯示簽發者 token 解析程式的設定。</span><span class="sxs-lookup"><span data-stu-id="ecf57-137">The following XML shows configuration for an issuer token resolver that is based on a custom class that derives from <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span></span> <span data-ttu-id="ecf57-138">權杖解析程式會維護一組物件-金鑰組的字典, 這些是從為類別定義`<AddAudienceKeyPair>`的自訂設定元素 () 初始化的。</span><span class="sxs-lookup"><span data-stu-id="ecf57-138">The token resolver maintains a dictionary of audience-key pairs that is initialized from a custom configuration element (`<AddAudienceKeyPair>`) defined for the class.</span></span> <span data-ttu-id="ecf57-139">類別會覆寫<xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A>方法來處理這個元素。</span><span class="sxs-lookup"><span data-stu-id="ecf57-139">The class overrides the <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> method to process this element.</span></span> <span data-ttu-id="ecf57-140">此覆寫如下列範例所示:不過, 為了簡潔起見, 不會顯示其所呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="ecf57-140">The override is shown in the following example; however, the methods it calls are not shown for brevity.</span></span> <span data-ttu-id="ecf57-141">如需完整範例, 請參閱`CustomToken`範例。</span><span class="sxs-lookup"><span data-stu-id="ecf57-141">For the complete example, see the `CustomToken` sample.</span></span>  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a><span data-ttu-id="ecf57-142">範例</span><span class="sxs-lookup"><span data-stu-id="ecf57-142">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ecf57-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ecf57-143">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
