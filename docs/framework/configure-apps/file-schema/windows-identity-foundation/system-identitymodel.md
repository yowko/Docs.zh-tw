---
title: '&lt;system.identityModel&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 210ce7e9-d07b-400c-800f-5f525dcf95e8
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 356dd1531f093282a1a8463b7d697400f8b45862
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltsystemidentitymodelgt"></a>&lt;system.identityModel&gt;
提供用於啟用應用程式中的 Windows Identity Foundation (WIF) 選項的設定。  
  
 \<system.identityModel >  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.identityModel>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無  
  
### <a name="child-elements"></a>子元素  
  
|項目|說明|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|指定服務層級身分識別設定。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`<configuration>`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
  
## <a name="remarks"></a>備註  
 新增`<system.identityModel>`組態檔來設定服務或應用程式使用 Windows Identity Foundation (WIF) 一節。 `<system.identityModel>`項目由<xref:System.IdentityModel.Configuration.SystemIdentityModelSection>類別。  
  
## <a name="example"></a>範例  
 下列範例示範如何將加入`<system.identityModel>`區段的組態檔。 您必須先新增底下的組態區段和命名空間宣告`<configSections>`項目。 接著您可以將新增`<system.IdentityModel>`組態檔來指定一或多個身分識別組態項目。  
  
```xml  
<configuration>  
  <configSections>  
    <!--WIF 4.5 sections -->  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
  </configSections>  
  
  ...  
  
  <system.identityModel>  
    <identityConfiguration>  
      <audienceUris>  
        <add value="http://localhost/WebApplication1/" />  
      </audienceUris>  
      <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089">  
        <trustedIssuers>  
          <add thumbprint="313D3B … 9106A9EC" name="SelfSTS" />  
        </trustedIssuers>  
      </issuerNameRegistry>  
      <certificateValidation certificateValidationMode="None"/>  
    </identityConfiguration>  
  </system.identityModel>  
  
  ...  
  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IdentityModel.Configuration.SystemIdentityModelSection>
