---
title: <x509SecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: 30ce69a35cfdd34e0dfea5c682347eb9187e04ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152446"
---
# <a name="x509securitytokenhandlerrequirement"></a>\<x509 安全權杖處理常式要求>
為<xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>類或派生類提供可選配置。  
  
[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<系統.身份模型>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<身份配置>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<安全權杖處理常式>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<添加>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<x509 安全權杖處理常式要求>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
        <x509SecurityTokenHandlerRequirement>  
          mapToWindows=xs:boolean  
          certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
          certificateValidator="Namespace.Class, Assembly"  
          revocationMode="NoCheck||Offline||Online"  
          trustedStoreLocation="CurrentUser||LocalMachine"  
        </x509SecurityTokenHandlerRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|certificateValidationMode|指定<xref:System.ServiceModel.Security.X509CertificateValidationMode>要用於 X.509 憑證的驗證模式的值。 預設值為"對等或鏈信任"。|  
|地圖到視窗|指定權杖處理常式是否應通過使用傳入的 UPN 聲明將驗證權杖映射到 Windows 帳戶。 預設值為 "false"。|  
|revocationMode|指定<xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>要用於 X.509 憑證的吊銷模式的值。 預設值為"連線"。|  
|trustedStoreLocation|指定<xref:System.Security.Cryptography.X509Certificates.StoreLocation>X.509 憑證存儲的值。 預設值為"本地電腦"。|  
|證書驗證器|派生自<xref:System.IdentityModel.Selectors.X509CertificateValidator>的自訂類型。 如果`certificateValidationMode`屬性為"自訂"，則此類型的實例用於頒發者證書驗證。|  
  
### <a name="child-elements"></a>子元素  
 None  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<添加>](add.md)|將指定的安全權杖處理常式添加到權杖處理常式集合。|  
  
## <a name="example"></a>範例  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"
                                         certificateValidationMode="PeerOrChainTrust"
                                         revocationMode="Online"
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
