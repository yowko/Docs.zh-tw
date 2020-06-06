---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: 67d7e0aa5b6b05bfe8b17a1b1efebb1fbddbb0eb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152667"
---
# \<issuerTokenResolver>
註冊權杖處理常式集合中處理常式所使用的簽發者 token 解析程式。 簽發者權杖解析程式是用來解析傳入權杖和訊息上的簽署權杖。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerTokenResolver>**  
  
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
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|type|指定簽發者 token 解析程式的類型。 必須是 <xref:System.IdentityModel.Tokens.IssuerTokenResolver> 類別或衍生自類別的類型 <xref:System.IdentityModel.Tokens.IssuerTokenResolver> 。 必要。|  
  
### <a name="child-elements"></a>子元素  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|提供安全性權杖處理常式集合的設定。|  
  
## <a name="remarks"></a>備註  
 簽發者權杖解析程式是用來解析傳入權杖和訊息上的簽署權杖。 它是用來抓取用於檢查簽章的密碼編譯內容。 您必須指定 `type` 屬性。 指定的型別可以是 <xref:System.IdentityModel.Tokens.IssuerTokenResolver> 或衍生自類別的自訂型別 <xref:System.IdentityModel.Tokens.IssuerTokenResolver> 。  
  
 某些權杖處理常式可讓您在設定中指定簽發者權杖解析程式設定。 個別權杖處理常式上的設定會覆寫安全性權杖處理常式集合上指定的設定。  
  
> [!NOTE]
> 將專案指定為專案的 `<issuerTokenResolver>` 子項目 [\<identityConfiguration>](identityconfiguration.md) 已被取代，但仍支援回溯相容性。 元素上的設定會覆寫專案上的專案 `<securityTokenHandlerConfiguration>` `<identityConfiguration>` 。  
  
## <a name="example"></a>範例  
 下列 XML 會根據衍生自的自訂類別，顯示簽發者 token 解析程式的設定 <xref:System.IdentityModel.Tokens.IssuerTokenResolver> 。 權杖解析程式會維護一組物件-金鑰組的字典，這些是從為類別定義的自訂設定元素（）初始化的 `<AddAudienceKeyPair>` 。 類別會覆寫 <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> 方法來處理這個元素。 此覆寫如下列範例所示：不過，為了簡潔起見，不會顯示其所呼叫的方法。 如需完整範例，請參閱 `CustomToken` 範例。  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a>範例
  
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
  
## <a name="see-also"></a>另請參閱

- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
