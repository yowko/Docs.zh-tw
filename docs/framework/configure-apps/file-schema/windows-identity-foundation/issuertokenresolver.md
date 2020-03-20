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
# <a name="issuertokenresolver"></a>\<頒發者權杖解析器>
註冊權杖處理常式集合中處理常式使用的頒發者權杖解析器。 頒發者權杖解析器用於解析傳入權杖和消息上的簽名權杖。  
  
[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<系統.身份模型>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<身份配置>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<安全權杖處理常式>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<安全權杖處理常式配置>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<頒發者權杖解析器>**  
  
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
|type|指定頒發者權杖解析器的類型。 必須是類<xref:System.IdentityModel.Tokens.IssuerTokenResolver>或從<xref:System.IdentityModel.Tokens.IssuerTokenResolver>類派生的類型。 必要。|  
  
### <a name="child-elements"></a>子元素  
 None  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<安全權杖處理常式配置>](securitytokenhandlerconfiguration.md)|為安全權杖處理常式的集合提供配置。|  
  
## <a name="remarks"></a>備註  
 頒發者權杖解析器用於解析傳入權杖和消息上的簽名權杖。 它用於檢索用於檢查簽名的加密材料。 必須指定該`type`屬性。 指定的類型可以是 或<xref:System.IdentityModel.Tokens.IssuerTokenResolver>派生自類的<xref:System.IdentityModel.Tokens.IssuerTokenResolver>自訂類型。  
  
 某些權杖處理常式允許您在配置中指定頒發者權杖解析器設置。 各個權杖處理常式上的設置將覆蓋在安全權杖處理常式集合上指定的設置。  
  
> [!NOTE]
> 將`<issuerTokenResolver>`元素指定為[\<標識配置>](identityconfiguration.md)元素的子項目已被棄用，但仍支援向後相容性。 元素上的`<securityTokenHandlerConfiguration>`設置將覆蓋元素上的`<identityConfiguration>`設置。  
  
## <a name="example"></a>範例  
 以下 XML 顯示基於 派生的<xref:System.IdentityModel.Tokens.IssuerTokenResolver>自訂類的頒發者權杖解析器的配置。 權杖解析器維護從為類定義的自訂配置元素 （`<AddAudienceKeyPair>`） 初始化的便捷鍵對字典。 類重寫處理<xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A>此元素的方法。 重寫顯示在以下示例中;如下例中所示。但是，它調用的方法不顯示為簡潔。 有關完整示例，請參閱示例`CustomToken`。  
  
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
