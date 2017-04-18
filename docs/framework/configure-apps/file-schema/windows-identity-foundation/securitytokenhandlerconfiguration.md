---
title: "&lt;securityTokenHandlerConfiguration&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 8
---
# &lt;securityTokenHandlerConfiguration&gt;
提供集合的語彙基元的處理常式的組態。  
  
## 語法  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration saveBootstrapContext=xs:boolean  
          maximumClockSkew=TimeSpan>  
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
|saveBootstrapContext|指定啟動程序載入的語彙基元是否應該包含在工作階段權杖。  可能也設定值對語彙基元的處理常式的集合物件藉由設定`saveBootstrapContext`在[\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)項目。  在語彙基元的處理常式集合上所設定的值會覆寫服務上所設定的值。|  
|maximumClockSkew|A <xref:System.TimeSpan> ，指定允許的最大時鐘扭曲。  執行即時作業，例如驗證登入工作階段的到期時間時，控制允許的最大時鐘扭曲。  預設值是 5 分鐘，"00: 05: 00"。  如需有關如何指定<xref:System.TimeSpan>的值，請參閱[Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md#BKMK_TimespanValues)。  最大時鐘扭曲可能也設定在服務層級藉由設定`maximumClockSkew`在[\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)項目。  在語彙基元的處理常式集合上所設定的值會覆寫服務上所設定的值。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<audienceUris\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)|指定為可接受的識別項，此信賴憑證者的合作對象的 Uri 集合。  選擇項。|  
|[\<caches\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|註冊快取使用的工作階段權杖和語彙基元重新執行偵測。  可以指定在服務層級，或在安全性語彙基元的處理常式集合。  選擇項。|  
|[\<certificateValidation\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|控制的設定，用來驗證憑證的語彙基元的處理常式。  可以指定在服務層級，或在安全性語彙基元的處理常式集合。  如果以它自己的驗證程式設定特定的處理常式，則會覆寫這些設定。  選擇項。|  
|[\<issuerNameRegistry\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|設定發行者名稱登錄所使用的語彙基元的處理常式集合中的處理常式。  選擇項。|  
|[\<issuerTokenResolver\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)|註冊發照者權杖解析程式所使用的語彙基元的處理常式集合中的處理常式。  發照者的權杖解析程式用來解析上連入的語彙基元和訊息的簽章的語彙基元。  選擇項。|  
|[\<serviceTokenResolver\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)|註冊服務權杖解析程式所使用的語彙基元的處理常式集合中的處理常式。  權杖解析程式服務用來解析加密上的語彙基元連入的語彙基元和訊息。  選擇項。|  
|[\<tokenReplayDetection\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|啟用語彙基元重新執行偵測，並指定語彙基元的到期時間。  可以指定在服務層級，或在安全性語彙基元的處理常式集合。  選擇項。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<securityTokenHandlers\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|指定登錄與端點的安全性語彙基元處理常式的集合。|  
  
## 備註  
 本章節提供的屬性值的<xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration>物件。  這一節中所設定的設定會覆寫該服務上設定的。  其中某些設定，這反而設定覆寫處理常式加入至安全性語彙基元的處理常式集合時所指定。  
  
## 範例  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>   
      <securityTokenHandlerConfiguration>  
  
        <audienceUris>  
          <clear/>  
          <add value="http://www.example.com/myapp/" />  
        </audienceUris>  
  
        <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel">  
          <trustedIssuers>  
            <add thumbprint="97249e1a … 4c9158de" name="contoso.com" />  
          </trustedIssuers>  
        </issuerNameRegistry>  
  
        <issuerTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
        <serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```