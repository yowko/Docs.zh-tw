---
title: <certificateValidator>
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: 3f3d79d3567c1714a79423b7767ce3f454b9d52d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152784"
---
# <a name="certificatevalidator"></a>\<證書驗證器>
指定證書驗證的自訂類型。 `certificateValidationMode`[僅當\<證書驗證>](certificatevalidation.md)元素的屬性設置為"自訂"時，才使用此類型。  
  
[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<系統.身份模型>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<身份配置>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<證書驗證>**](certificatevalidation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<證書驗證器>**  
  
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
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|type|指定派生自類的<xref:System.IdentityModel.Selectors.X509CertificateValidator>自訂類型。 `certificateValidationMode`[將\<證書驗證>](certificatevalidation.md)元素的屬性設置為"自訂"以使用此類型。 有關如何指定屬性的詳細資訊，`type`請參閱[自訂類型引用](../windows-workflow-foundation/index.md)。 選擇性。|  
  
### <a name="child-elements"></a>子元素  
 None  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<證書驗證>](certificatevalidation.md)|控制權杖處理常式用於驗證憑證的設置。|  
  
## <a name="example"></a>範例  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />
</certificateValidation>
```
