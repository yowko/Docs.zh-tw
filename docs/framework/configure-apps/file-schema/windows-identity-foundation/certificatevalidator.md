---
title: <certificateValidator>
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: c25f183679f41f51ffee4f482bfe7a64763647d9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941909"
---
# <a name="certificatevalidator"></a>\<certificateValidator>
指定憑證驗證的自訂類型。 只有當`certificateValidationMode` [ \<certificateValidation >](certificatevalidation.md)元素的屬性設定為 "Custom" 時, 才會使用此類型。  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<certificateValidation>  
\<certificateValidator>  
  
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
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|說明|  
|---------------|-----------------|  
|型別|指定衍生<xref:System.IdentityModel.Selectors.X509CertificateValidator>自類別的自訂類型。 將 certificateValidation > 元素的`certificateValidationMode`屬性[設定為 "Custom", 以\<](certificatevalidation.md)使用此類型。 如需如何指定屬性的`type`詳細資訊, 請參閱[自訂類型參考](../windows-workflow-foundation/index.md)。 選擇性。|  
  
### <a name="child-elements"></a>子元素  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<certificateValidation>](certificatevalidation.md)|控制權杖處理常式用來驗證憑證的設定。|  
  
## <a name="example"></a>範例  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />    
</certificateValidation>        
```
