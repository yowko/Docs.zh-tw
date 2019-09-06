---
title: <serviceCertificate>
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
ms.openlocfilehash: 653dd9cfadbfd33f5371b77172199b946321bc8c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251862"
---
# <a name="servicecertificate"></a>\<serviceCertificate>
設定用來加密和解密權杖的 x.509 憑證。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<Microsoft.identitymodel >** ](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<federationConfiguration >** ](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceCertificate >**  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 None  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<certificateReference>](certificatereference.md)|指定用來在憑證存放區中尋找和驗證 x.509 憑證的設定。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|包含設定<xref:System.IdentityModel.Services.WSFederationAuthenticationModule> （WSFAM） <xref:System.IdentityModel.Services.SessionAuthenticationModule>和（SAM）的設定。|  
  
## <a name="example"></a>範例  
 下列 XML 顯示\<serviceCertificate > 元素的用法。 XML 取自`CustomToken`範例。  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
