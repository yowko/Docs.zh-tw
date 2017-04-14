---
title: "&lt;basicHttpBinding&gt; 的 &lt;transport&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4c5ba293-3d7e-47a6-b84e-e9022857b7e5
caps.latest.revision: 18
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 18
---
# &lt;basicHttpBinding&gt; 的 &lt;transport&gt;
定義可控制 HTTP 傳輸之驗證參數的屬性。  
  
## 語法  
  
```  
<basicHttpBinding>  
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
</basicHttpBinding>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|clientCredentialType|-   指定當使用 HTTP 驗證執行用戶端驗證時，要使用的認證類型。  預設為 `None`。  此屬性的型別為 <xref:System.ServiceModel.HttpClientCredentialType>。|  
|proxyCredentialType|-   指定當使用 Proxy over HTTP 從網域內執行用戶端驗證時，要使用的認證類型。  這個屬性僅適用於父 `security` 項目的 `mode` 屬性是 `Transport` 或 `TransportCredentialsOnly` 時。  此屬性的型別為 <xref:System.ServiceModel.HttpProxyCredentialType>。|  
|realm|字串，指定摘要式驗證或基本驗證的 HTTP 驗證配置所使用的領域。  預設為空字串。|  
|policyEnforcement|此列舉指定了應該強制執行 <xref:System.Security.Authentication.ExtendedProtectionPolicy> 的時間。<br /><br /> 1.  Never：絕不強制執行此原則 \(延伸保護已停用\)。<br />2.  WhenSupported：只有當用戶端支援延伸保護時，才強制執行此原則。<br />3.  Always：一律強制執行此原則。  不支援延伸保護的用戶端將無法驗證。|  
|protectionScenario|此列舉會指定原則強制執行的保護案例。|  
  
## clientCredentialType 屬性  
  
|值|描述|  
|-------|--------|  
|無|傳輸期間不會保護訊息的安全。|  
|基本|指定基本驗證。|  
|摘要|指定摘要式驗證。|  
|Ntlm|指定可能的情況下以及 Windows 驗證失敗時的 NTLM 驗證。|  
|Windows|指定 Windows 整合式驗證。|  
  
## proxyCredentialType 屬性  
  
|值|描述|  
|-------|--------|  
|無|-   傳輸期間不會保護訊息的安全。|  
|基本|指定依照 RFC 2617 – HTTP Authentication: Basic and Digest Authentication 所定義的基本驗證。|  
|摘要|指定依照 RFC 2617 – HTTP Authentication: Basic and Digest Authentication 所定義的摘要式驗證。|  
|Ntlm|指定可能的情況下以及 Windows 驗證失敗時的 NTLM 驗證。|  
|Windows|指定 Windows 整合式驗證。|  
|憑證|使用憑證執行用戶端驗證。  這個選項只有在父 `security` 項目的 `Mode` 屬性設為 Transport 時才能使用，如果該屬性設為 TransportCredentialOnly，則無法使用。|  
  
### 子項目  
 無  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<安全性\>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|定義 [\<basicHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) 的安全性功能。|  
  
## 範例  
 下列範例示範透過基本繫結來使用 SSL 傳輸安全性。  根據預設，基本繫結支援 HTTP 通訊。  
  
```  
<system.serviceModel>  
   <services>  
      <service   
          type="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
         <endpoint address=""  
               binding="basicHttpBinding"  
               bindingConfiguration="Binding1"   
               contract="Microsoft.ServiceModel.Samples.ICalculator" />  
      </service>  
   </services>  
    <bindings>  
        <basicHttpBinding>  
        <!-- Configure basicHttpBinding with Transport security -- >  
        <!-- mode and clientCredentialType set to None.-->  
           <binding name="Binding1">  
               <security mode="Transport">  
                   <transport clientCredentialType="None"  
                              proxyCredentialType="None">  
                       <extendedProtectionPolicy  
                          policyEnforcement="WhenSupported"  
                          protectionScenario="TransportSelected">  
                    <customServiceNames></customServiceNames>  
                       </extendedProtectionPolicy>  
               </security>  
           </binding>  
        </basicHttpBinding>  
    </bindings>  
</system.serviceModel>  
```  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>   
 <xref:System.ServiceModel.BasicHttpSecurity.Transport%2A>   
 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>   
 <xref:System.ServiceModel.HttpTransportSecurity>   
 [確保服務與用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [繫結](../../../../../docs/framework/wcf/bindings.md)   
 [設定系統提供的繫結](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/zh-tw/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<繫結\>](../../../../../docs/framework/misc/binding.md)