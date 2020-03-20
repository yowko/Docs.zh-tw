---
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: e3e65820fa4dc341371d4f67689a288cd3f63951
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152563"
---
# <a name="securitytokenhandlerconfiguration"></a>\<安全權杖處理常式配置>
提供權杖處理常式集合的配置。  
  
[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<系統.身份模型>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<身份配置>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<安全權杖處理常式>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<安全權杖處理常式配置>**  
  
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
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|保存引導上下文|指定是否應在會話權杖中包括引導標記。 還可以通過在`saveBootstrapContext`[\<標識配置>](identityconfiguration.md)元素上設置屬性，在權杖處理常式集合上設置該值。 權杖處理常式集合上設置的值將覆蓋服務上設置的值。|  
|最大時鐘|指定<xref:System.TimeSpan>允許的最大時鐘偏斜的 。 控制執行時間敏感操作（如驗證登錄會話的過期時間）時允許的最大時鐘偏差。 預設值為 5 分鐘，"00：05：00"。 有關如何指定<xref:System.TimeSpan>值的詳細資訊，請參閱[時間跨度值](../windows-workflow-foundation/index.md)。 還可以通過在`maximumClockSkew`[\<標識配置>](identityconfiguration.md)元素上設置屬性，在服務等級設置最大時鐘偏斜。 權杖處理常式集合上設置的值將覆蓋服務上設置的值。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<觀眾尤裡斯·>](audienceuris.md)|指定此依賴方可接受的識別碼的 URI 集。 選擇性。|  
|[\<緩存>](caches.md)|註冊用於會話權杖和權杖重播檢測的緩存。 可以在服務等級或安全權杖處理常式集合上指定。 選擇性。|  
|[\<證書驗證>](certificatevalidation.md)|控制權杖處理常式用於驗證憑證的設置。 可以在服務等級或安全權杖處理常式集合上指定。 如果特定處理常式配置了自己的驗證器，則這些設置將被覆蓋。 選擇性。|  
|[\<發行人名稱註冊>](issuernameregistry.md)|配置權杖處理常式集合中處理常式使用的頒發者名稱註冊表。 選擇性。|  
|[\<頒發者權杖解析器>](issuertokenresolver.md)|註冊權杖處理常式集合中處理常式使用的頒發者權杖解析器。 頒發者權杖解析器用於解析傳入權杖和消息上的簽名權杖。 選擇性。|  
|[\<服務權杖解析器>](servicetokenresolver.md)|註冊權杖處理常式集合中處理常式使用的服務權杖解析器。 服務權杖解析器用於解析傳入權杖和消息上的加密權杖。 選擇性。|  
|[\<權杖重播檢測>](tokenreplaydetection.md)|啟用權杖重播檢測並指定權杖的過期時間。 可以在服務等級或安全權杖處理常式集合上指定。 選擇性。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<安全權杖處理常式>](securitytokenhandlers.md)|指定向終結點註冊的安全權杖處理常式的集合。|  
  
## <a name="remarks"></a>備註  
 本節提供<xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration>物件的屬性值。 本節中配置的設置將覆蓋服務上配置的設置。 反過來，其中一些設置可以被在將處理常式添加到安全權杖處理常式集合時指定的設置覆蓋。  
  
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
