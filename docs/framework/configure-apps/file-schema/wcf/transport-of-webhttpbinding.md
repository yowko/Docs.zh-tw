---
title: "&lt;webHttpBinding&gt; 的 &lt;transport&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 44397edf2d2c5e2f99a255789452b08d91484b81
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="lttransportgt-of-ltwebhttpbindinggt"></a>&lt;webHttpBinding&gt; 的 &lt;transport&gt;
定義服務端點 (此服務端點是設定來接收 HTTP 要求的) 之傳輸層級安全性設定。  
  
 \<系統。ServiceModel >  
\<繫結 >  
\<w >  
\<繫結 >  
\<安全性 >  
\<傳輸 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<webHttpBinding>  
    <binding>  
        <security  
        mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">  
            <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"  
             proxyCredentialType="None|Basic|Digest|Ntlm|Windows" realm="string" >  
                <extendedProtectionPolicy  
                     policyEnforcement="Never|WhenSupported|Always"  
                     protectionScenario="TransportSelected|TrustedProxy">  
                    <customServiceNames></customServiceNames>  
                        </extendedProtectionPolicy>  
            </transport>  
        </security>  
    </binding>  
</WebHttpBinding>  
```  
  
## <a name="type"></a>類型  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`clientCredentialType`|指定用來對服務驗證用戶端的認證。 此屬性的型別為 <xref:System.ServiceModel.HttpClientCredentialType>。|  
|`proxyCredentialType`|指定用來對網域 Proxy 驗證用戶端的認證。 此屬性的型別為 <xref:System.ServiceModel.HttpProxyCredentialType>。|  
|`realm`|指定摘要式驗證或基本驗證之驗證領域的字串。 預設為空字串。<br /><br /> 驗證領域至少會指定負責執行驗證之主機的名稱， 也可以指定具有存取權之使用者的集合。 使用者可以查詢驗證領域，以確定可以使用的其中一組使用者名稱和密碼。|  
|`policyEnforcement`|此列舉指定了應該強制執行 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> 的時間。<br /><br /> 1.Never：絕不強制執行此原則 (延伸保護已停用)。<br />2.WhenSupported：只有當用戶端支援延伸保護時，才強制執行此原則。<br />3.Always：一律強制執行此原則。 不支援延伸保護的用戶端將無法驗證。|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType 屬性  
  
|值|描述|  
|-----------|-----------------|  
|`None`|停用安全性。|  
|`Basic`|使用基本驗證。|  
|`Certificate`|使用 X.509 憑證來驗證用戶端。|  
|`Digest`|使用摘要式驗證。|  
|`Ntlm`|使用 NTLM 驗證做為 Windows 網域的後援。|  
|`Windows`|使用整合式 Windows 驗證。|  
  
## <a name="proxycredentialtype-attribute"></a>proxyCredentialType 屬性  
  
|值|描述|  
|-----------|-----------------|  
|`None`|停用安全性。|  
|`Basic`|使用基本驗證。|  
|`Digest`|使用摘要式驗證。|  
|`Ntlm`|使用 NTLM 做為 Windows 網域的後援。|  
|`Windows`|使用整合式 Windows 驗證。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<安全性 >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-webhttpbinding.md)|代表的安全性功能[ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)項目。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>  
 [保護服務和用戶端](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [繫結](../../../../../docs/framework/wcf/bindings.md)  
 [設定系統提供繫結](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [使用繫結來設定 Windows Communication Foundation 服務和用戶端](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<繫結 >](../../../../../docs/framework/misc/binding.md)  
 [WCF Web HTTP 程式設計模型](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
