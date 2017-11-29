---
title: '&lt;certificateValidator&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 74dd0827ee073d57c82729ec1e6a9a672aa1f404
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltcertificatevalidatorgt"></a>&lt;certificateValidator&gt;
指定自訂憑證驗證類型。 此類型只使用`certificateValidationMode`屬性[ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)元素設定為"Custom"。  
  
 \<system.identityModel >  
\<identityConfiguration >  
\<certificateValidation >  
\<certificateValidator >  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <certificateValidation>  
      <certificateValidator type=xs:string>  
      </certificateValidator>  
    </certificateValidation>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|類型|指定自訂型別衍生自<xref:System.IdentityModel.Selectors.X509CertificateValidator>類別。 設定`certificateValidationMode`屬性[ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)為"Custom"，使用此類型的項目。 如需有關如何指定`type`屬性，請參閱[自訂型別參考](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md)。 選擇項。|  
  
### <a name="child-elements"></a>子元素  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|控制權杖處理常式用來驗證憑證的設定。|  
  
## <a name="example"></a>範例  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />    
</certificateValidation>        
```
