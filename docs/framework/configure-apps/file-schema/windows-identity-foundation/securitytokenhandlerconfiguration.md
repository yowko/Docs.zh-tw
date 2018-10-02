---
title: '&lt;Securitytokenhandlerconfiguration>&gt;'
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: d66771ec7ed52ace52df6bb3bfafdcf9cce989b5
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48029320"
---
# <a name="ltsecuritytokenhandlerconfigurationgt"></a>&lt;Securitytokenhandlerconfiguration>&gt;
提供的權杖處理常式集合的組態。  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<Securitytokenhandlerconfiguration> >  
  
## <a name="syntax"></a>語法  
  
```xml  
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
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|saveBootstrapContext|指定是否應包含啟動程序權杖中的工作階段權杖。 值可能也會在集合上設定權杖處理常式設定`saveBootstrapContext`屬性[ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)項目。 權杖處理常式集合上所設定的值會覆寫在服務上設定的值。|  
|maximumClockSkew|A <xref:System.TimeSpan> ，指定最大允許的時鐘誤差。 執行時間緊迫的作業，例如驗證登入工作階段的到期時間時，控制最大允許的時鐘誤差。 預設值為 5 分鐘，"00: 05:00"。 如需有關如何指定<xref:System.TimeSpan>值，請參閱[Timespan 值](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md)。 最大時鐘誤差可能也會設定服務層級設定`maximumClockSkew`屬性[ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)項目。 權杖處理常式集合上所設定的值會覆寫在服務上設定的值。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<audienceUris >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)|指定是可接受的識別項，此信賴憑證者的合作對象的 Uri 的集合。 選擇性。|  
|[\<快取 >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|註冊用於工作階段權杖和權杖重新執行偵測快取。 可以在服務層級或上指定的安全性權杖處理常式集合。 選擇性。|  
|[\<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|控制權杖處理常式用來驗證憑證的設定。 可以在服務層級或上指定的安全性權杖處理常式集合。 如果特定的處理常式設定為使用自己的驗證程式，則會覆寫這些設定。 選擇性。|  
|[\<issuerNameRegistry >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|設定簽發者名稱登錄，可由權杖處理常式集合中的處理常式。 選擇性。|  
|[\<issuerTokenResolver >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)|註冊由權杖處理常式集合中的處理常式的簽發者權杖解析程式。 簽發者權杖解析程式用來解析簽署的權杖上傳入的權杖和訊息。 選擇性。|  
|[\<serviceTokenResolver >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)|註冊的服務權杖解析程式由權杖處理常式集合中的處理常式。 服務權杖解析程式用來解析上傳入的權杖和訊息的加密語彙基元。 選擇性。|  
|[\<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|啟用權杖重新執行偵測，並指定權杖的到期時間。 可以在服務層級或上指定的安全性權杖處理常式集合。 選擇性。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|指定登錄與端點的安全性權杖處理常式的集合。|  
  
## <a name="remarks"></a>備註  
 本節提供的屬性值的<xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration>物件。 在本節中的設定會覆寫服務上設定。 其中某些設定可以依次覆寫時的處理常式加入至安全性權杖處理常式集合中指定的設定。  
  
## <a name="example"></a>範例  
  
```xml  
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
