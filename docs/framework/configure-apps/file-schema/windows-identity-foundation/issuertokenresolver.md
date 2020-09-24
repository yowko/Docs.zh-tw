---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: 946ae8601e1e4563becd0b346b6c792724405a45
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91165035"
---
# \<issuerTokenResolver>

<span data-ttu-id="07846-101">註冊權杖處理常式集合中處理常式所使用的簽發者權杖解析程式。</span><span class="sxs-lookup"><span data-stu-id="07846-101">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="07846-102">簽發者權杖解析程式是用來解析傳入權杖和訊息上的簽署權杖。</span><span class="sxs-lookup"><span data-stu-id="07846-102">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerTokenResolver>**  
  
## <a name="syntax"></a><span data-ttu-id="07846-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="07846-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="07846-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="07846-104">Attributes and Elements</span></span>  

 <span data-ttu-id="07846-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="07846-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="07846-106">屬性</span><span class="sxs-lookup"><span data-stu-id="07846-106">Attributes</span></span>  
  
|<span data-ttu-id="07846-107">屬性</span><span class="sxs-lookup"><span data-stu-id="07846-107">Attribute</span></span>|<span data-ttu-id="07846-108">描述</span><span class="sxs-lookup"><span data-stu-id="07846-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="07846-109">type</span><span class="sxs-lookup"><span data-stu-id="07846-109">type</span></span>|<span data-ttu-id="07846-110">指定簽發者權杖解析程式的類型。</span><span class="sxs-lookup"><span data-stu-id="07846-110">Specifies the type of the issuer token resolver.</span></span> <span data-ttu-id="07846-111">必須是 <xref:System.IdentityModel.Tokens.IssuerTokenResolver> 類別或衍生自類別的型別 <xref:System.IdentityModel.Tokens.IssuerTokenResolver> 。</span><span class="sxs-lookup"><span data-stu-id="07846-111">Must be either the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class or a type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span> <span data-ttu-id="07846-112">必要。</span><span class="sxs-lookup"><span data-stu-id="07846-112">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="07846-113">子元素</span><span class="sxs-lookup"><span data-stu-id="07846-113">Child Elements</span></span>  

 <span data-ttu-id="07846-114">無</span><span class="sxs-lookup"><span data-stu-id="07846-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="07846-115">父項目</span><span class="sxs-lookup"><span data-stu-id="07846-115">Parent Elements</span></span>  
  
|<span data-ttu-id="07846-116">項目</span><span class="sxs-lookup"><span data-stu-id="07846-116">Element</span></span>|<span data-ttu-id="07846-117">描述</span><span class="sxs-lookup"><span data-stu-id="07846-117">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="07846-118">提供安全性權杖處理常式集合的設定。</span><span class="sxs-lookup"><span data-stu-id="07846-118">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07846-119">備註</span><span class="sxs-lookup"><span data-stu-id="07846-119">Remarks</span></span>  

 <span data-ttu-id="07846-120">簽發者權杖解析程式是用來解析傳入權杖和訊息上的簽署權杖。</span><span class="sxs-lookup"><span data-stu-id="07846-120">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="07846-121">它是用來取出用來檢查簽章的密碼編譯內容。</span><span class="sxs-lookup"><span data-stu-id="07846-121">It is used to retrieve the cryptographic material that is used for checking the signature.</span></span> <span data-ttu-id="07846-122">您必須指定 `type` 屬性。</span><span class="sxs-lookup"><span data-stu-id="07846-122">You must specify the `type` attribute.</span></span> <span data-ttu-id="07846-123">指定的型別可以是 <xref:System.IdentityModel.Tokens.IssuerTokenResolver> 或衍生自類別的自訂型別 <xref:System.IdentityModel.Tokens.IssuerTokenResolver> 。</span><span class="sxs-lookup"><span data-stu-id="07846-123">The type specified can be either <xref:System.IdentityModel.Tokens.IssuerTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span>  
  
 <span data-ttu-id="07846-124">某些權杖處理常式可讓您在設定中指定簽發者權杖解析程式設定。</span><span class="sxs-lookup"><span data-stu-id="07846-124">Some token handlers allow you to specify issuer token resolver settings in configuration.</span></span> <span data-ttu-id="07846-125">個別標記處理常式上的設定會覆寫安全性權杖處理常式集合上指定的設定。</span><span class="sxs-lookup"><span data-stu-id="07846-125">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="07846-126">將 `<issuerTokenResolver>` 元素指定為專案的子項目 [\<identityConfiguration>](identityconfiguration.md) 已被取代，但仍支援回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="07846-126">Specifying the `<issuerTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="07846-127">元素上的設定會覆 `<securityTokenHandlerConfiguration>` 寫元素上的設定 `<identityConfiguration>` 。</span><span class="sxs-lookup"><span data-stu-id="07846-127">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07846-128">範例</span><span class="sxs-lookup"><span data-stu-id="07846-128">Example</span></span>  

 <span data-ttu-id="07846-129">下列 XML 會根據衍生自的自訂類別，顯示簽發者權杖解析程式的設定 <xref:System.IdentityModel.Tokens.IssuerTokenResolver> 。</span><span class="sxs-lookup"><span data-stu-id="07846-129">The following XML shows configuration for an issuer token resolver that is based on a custom class that derives from <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span></span> <span data-ttu-id="07846-130">權杖解析程式會維護從自訂設定專案初始化的物件-金鑰組字典， (`<AddAudienceKeyPair>`) 為類別定義。</span><span class="sxs-lookup"><span data-stu-id="07846-130">The token resolver maintains a dictionary of audience-key pairs that is initialized from a custom configuration element (`<AddAudienceKeyPair>`) defined for the class.</span></span> <span data-ttu-id="07846-131">類別會覆寫 <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> 方法以處理此元素。</span><span class="sxs-lookup"><span data-stu-id="07846-131">The class overrides the <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> method to process this element.</span></span> <span data-ttu-id="07846-132">覆寫會顯示在下列範例中：但為了簡潔起見，並不會顯示其所呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="07846-132">The override is shown in the following example; however, the methods it calls are not shown for brevity.</span></span> <span data-ttu-id="07846-133">如需完整範例，請參閱 `CustomToken` 範例。</span><span class="sxs-lookup"><span data-stu-id="07846-133">For the complete example, see the `CustomToken` sample.</span></span>  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a><span data-ttu-id="07846-134">範例</span><span class="sxs-lookup"><span data-stu-id="07846-134">Example</span></span>
  
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
  
## <a name="see-also"></a><span data-ttu-id="07846-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07846-135">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
