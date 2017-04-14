---
title: "&lt;issuerTokenResolver&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
caps.latest.revision: 9
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 8
---
# &lt;issuerTokenResolver&gt;
註冊發照者權杖解析程式所使用的語彙基元的處理常式集合中的處理常式。  發照者的權杖解析程式用來解析上連入的語彙基元和訊息的簽章的語彙基元。  
  
## 語法  
  
```  
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
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|type|指定簽發者的權杖解析的型別。  必須是<xref:System.IdentityModel.Tokens.IssuerTokenResolver>類別或衍生自型別<xref:System.IdentityModel.Tokens.IssuerTokenResolver>類別。  如需有關如何指定`type`屬性，請參閱[Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md#BKMK_CustomTypeReferences)。  必要項。|  
  
### 子項目  
 None  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<securityTokenHandlerConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|提供組態集合的安全性語彙基元的處理常式。|  
  
## 備註  
 發照者的權杖解析程式用來解析上連入的語彙基元和訊息的簽章的語彙基元。  它用來擷取用來檢查簽章的密碼編譯內容。  您必須指定`type`屬性。  指定的型別可以是<xref:System.IdentityModel.Tokens.IssuerTokenResolver>或自訂的型別衍生自<xref:System.IdentityModel.Tokens.IssuerTokenResolver>類別。  
  
 某些語彙基元的處理常式可讓您在組態中指定發行者的語彙基元的解析程式設定。  在個別的語彙基元處理常式的設定會覆寫安全性語彙基元的處理常式集合上指定。  
  
> [!NOTE]
>  指定`<issuerTokenResolver>`項目做為子項目， [\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)項目已被取代，但仍然支援回溯相容性。  設定在`<securityTokenHandlerConfiguration>`項目會覆寫那些在`<identityConfiguration>`項目。  
  
## 範例  
 下列 XML 程式碼顯示設定發照者權杖解析為基礎的自訂類別衍生自<xref:System.IdentityModel.Tokens.IssuerTokenResolver>。  權杖解析會維護對象金鑰組的字典，會從自訂組態項目 \(`<AddAudienceKeyPair>`\) 為類別定義。  類別覆寫<xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A>方法來處理這個項目。  覆寫會顯示下列的範例 ； 不過，它會呼叫這些方法不會顯示因簡要考量。  完整的範例，請參閱`CustomToken`範例。  
  
```  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## 範例  
  
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
  
## 請參閱  
 <xref:System.IdentityModel.Tokens.IssuerTokenResolver>