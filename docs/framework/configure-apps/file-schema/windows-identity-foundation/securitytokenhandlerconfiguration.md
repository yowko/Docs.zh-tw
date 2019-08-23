---
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: 0aefaa808dfc32085a208420fcd582b1671acc64
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942450"
---
# <a name="securitytokenhandlerconfiguration"></a>\<securityTokenHandlerConfiguration>
提供權杖處理常式集合的設定。  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<securityTokenHandlerConfiguration>  
  
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
|saveBootstrapContext|指定啟動程式權杖是否應包含在會話權杖中。 您也可以在`saveBootstrapContext` [ \<identityConfiguration >](identityconfiguration.md)專案上設定屬性, 以在權杖處理常式集合上設定此值。 在權杖處理常式集合上設定的值會覆寫服務上設定的值。|  
|maximumClockSkew|<xref:System.TimeSpan> , 指定允許的最大時鐘誤差。 控制執行時間緊迫作業時允許的時鐘誤差上限, 例如驗證登入會話的到期時間。 預設值為5分鐘, "00:05:00"。 如需如何指定<xref:System.TimeSpan>值的詳細資訊, 請參閱[Timespan 值](../windows-workflow-foundation/index.md)。 您也可以在`maximumClockSkew` [ \<identityConfiguration >](identityconfiguration.md)專案上設定屬性, 以在服務層級設定最大時鐘誤差。 在權杖處理常式集合上設定的值會覆寫服務上設定的值。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|說明|  
|-------------|-----------------|  
|[\<audienceUris>](audienceuris.md)|指定 Uri 的集合, 這是此信賴憑證者可接受的識別碼。 選擇性。|  
|[\<caches>](caches.md)|註冊用於會話權杖和權杖重新執行偵測的快取。 可以在服務層級或安全性權杖處理常式集合中指定。 選擇性。|  
|[\<certificateValidation>](certificatevalidation.md)|控制權杖處理常式用來驗證憑證的設定。 可以在服務層級或安全性權杖處理常式集合中指定。 如果特定處理常式已設定自己的驗證器, 則會覆寫這些設定。 選擇性。|  
|[\<issuerNameRegistry>](issuernameregistry.md)|設定權杖處理常式集合中處理常式所使用的簽發者名稱登錄。 選擇性。|  
|[\<issuerTokenResolver>](issuertokenresolver.md)|註冊權杖處理常式集合中處理常式所使用的簽發者 token 解析程式。 簽發者權杖解析程式是用來解析傳入權杖和訊息上的簽署權杖。 選擇性。|  
|[\<serviceTokenResolver>](servicetokenresolver.md)|註冊權杖處理常式集合中處理常式所使用的服務 token 解析程式。 服務權杖解析程式是用來解析傳入權杖和訊息上的加密權杖。 選擇性。|  
|[\<tokenReplayDetection>](tokenreplaydetection.md)|啟用權杖重新執行偵測, 並指定權杖的到期時間。 可以在服務層級或安全性權杖處理常式集合中指定。 選擇性。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|指定已向端點註冊的安全性權杖處理常式集合。|  
  
## <a name="remarks"></a>備註  
 本節提供<xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration>物件的屬性值。 在此區段中設定的設定會覆寫在服務上設定的設定。 其中有些設定可以覆寫為將處理常式加入至安全性權杖處理常式集合時所指定的設定。  
  
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
