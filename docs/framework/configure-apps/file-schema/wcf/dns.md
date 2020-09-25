---
title: <dns>
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: adfd94365ceb0ddc3164a6baef838c16027b4bc3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190134"
---
# \<dns>

指定伺服器的預期身分識別。 如果伺服器的憑證包含具有相同值的 DNS，這個身分識別對於 X509 憑證驗證模式是有效的。 如果 SPN 具有相同的值，則對於 Windows 驗證模式也是有效的。  
  
如需設定元素值的詳細資訊，請參閱 [服務身分識別和驗證](../../../wcf/feature-details/service-identity-and-authentication.md)。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dns>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<dns value = "String" />
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|value|憑證的 DNS。 DNS 是業界標準通訊協定，用來尋找 IP 網路上的電腦。 使用者可以記住顯示名稱，例如 `https://go.microsoft.com/fwlink/?prd=10929` 或 `https://go.microsoft.com/fwlink/?LinkID=96165` ，比以數位為基礎的位址（例如 207.46.131.137) 簡單）更容易。|  
  
### <a name="child-elements"></a>子元素  

 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<identity>](identity.md)|指定要由用戶端驗證之服務的身分識別。|  
  
## <a name="example"></a>範例  

 下列組態程式碼會指定用來驗證伺服器之 X.509 憑證的 DNS。  
  
```xml  
<identity>
  <dns value = "www.cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.DnsEndpointIdentity>
- [服務身分識別和驗證](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
