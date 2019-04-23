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
# <a name="issuertokenresolver"></a>\<issuerTokenResolver>
註冊由權杖處理常式集合中的處理常式的簽發者權杖解析程式。 簽發者權杖解析程式用來解析簽署的權杖上傳入的權杖和訊息。  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<securityTokenHandlerConfiguration>  
\<issuerTokenResolver>  
  
## <a name="syntax"></a>語法  
  
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
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|類型|指定簽發者權杖解析程式類型。 必須是<xref:System.IdentityModel.Tokens.IssuerTokenResolver>類別或衍生自類型<xref:System.IdentityModel.Tokens.IssuerTokenResolver>類別。 必要項。|  
  
### <a name="child-elements"></a>子元素  
 None  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|提供組態集合的安全性權杖處理常式。|  
  
## <a name="remarks"></a>備註  
 簽發者權杖解析程式用來解析簽署的權杖上傳入的權杖和訊息。 它用來擷取用來檢查簽章的加密編譯內容。 您必須指定`type`屬性。 指定的型別可以是<xref:System.IdentityModel.Tokens.IssuerTokenResolver>或自訂的型別衍生自<xref:System.IdentityModel.Tokens.IssuerTokenResolver>類別。  
  
 某些權杖處理常式可讓您在組態中指定簽發者權杖解析程式設定。 在個別的權杖處理常式上的設定會覆寫所指定的安全性權杖處理常式集合。  
  
> [!NOTE]
>  指定`<issuerTokenResolver>`元素的子元素當做[ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)項目已被取代，但仍支援回溯相容性。 上的設定`<securityTokenHandlerConfiguration>`項目會覆寫上`<identityConfiguration>`項目。  
  
## <a name="example"></a>範例  
 下列 XML 顯示組態的簽發者權杖解析程式為基礎的自訂類別衍生自<xref:System.IdentityModel.Tokens.IssuerTokenResolver>。 權杖解析程式會維護對象索引鍵組的字典，初始化從自訂的組態項目 (`<AddAudienceKeyPair>`) 定義的類別。 類別會覆寫<xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A>方法來處理這個項目。 覆寫會顯示在下列範例中，不過，它會呼叫的方法不會顯示為求簡單明瞭。 完整的範例，請參閱`CustomToken`範例。  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a>範例  
  
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
  
## <a name="see-also"></a>另請參閱

- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
