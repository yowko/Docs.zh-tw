---
title: '&lt;dns&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f2e3dbd0781485336a441c8eacb536ad008ff7a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltdnsgt"></a>&lt;dns&gt;
指定伺服器的預期身分識別。 如果伺服器的憑證包含具有相同值的 DNS，這個身分識別對於 X509 憑證驗證模式是有效的。 如果 SPN 具有相同的值，則對於 Windows 驗證模式也是有效的。  
  
 如需有關設定項目值的詳細資訊，請參閱[服務識別和驗證](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)。  
  
 \<身分識別 >  
\<dns >  
  
## <a name="syntax"></a>語法  
  
```xml  
<dns value = "String" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|value|憑證的 DNS。 DNS 是業界標準通訊協定，用來尋找 IP 網路上的電腦。 使用者可記住顯示名稱，例如[http://go.microsoft.com/fwlink/?prd=10929](http://go.microsoft.com/fwlink/?prd=10929)或[http://go.microsoft.com/fwlink/?LinkID=96165](http://go.microsoft.com/fwlink/?LinkID=96165)、 數字為基礎的位址，例如 207.46.131.137 比更容易。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<身分識別 >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|指定要由用戶端驗證之服務的身分識別。|  
  
## <a name="example"></a>範例  
 下列組態程式碼會指定用來驗證伺服器之 X.509 憑證的 DNS。  
  
```xml  
<identity>  
  <dns value = "www.cohowinery.com" />  
</identity>  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.DnsEndpointIdentity>  
 [服務身分識別和驗證](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [\<身分識別 >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
