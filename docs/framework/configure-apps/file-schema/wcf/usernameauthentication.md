---
title: "&lt;userNameAuthentication&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# &lt;userNameAuthentication&gt;
根據使用者名稱和密碼來指定服務的認證。  
  
## 語法  
  
```  
  
<userNameAuthentication  
   cacheLogonTokenLifetime="TimeSpan"  
   cacheLogonTokens="Boolean"   
   customUserNamePasswordValidatorType="String"  
   includeWindowsGroups="Boolean"   
   maxCacheLogonTokens="Integer"  
   membershipProviderName="String"  
   userNamePasswordValidationMode="Windows/MembershipProvider/Custom" />  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`cacheLogonTokenLifetime`|<xref:System.Timespan>，指定快取權杖的最大時間長度。  預設為 00:15:00。|  
|`cacheLogonTokens`|布林值，指定是否要快取登入權杖。  預設為 `false`。|  
|`customUserNamePasswordValidatorType`|字串，指定所使用的自訂使用者名稱密碼驗證程式的型別。  預設為空字串。|  
|`includeWindowsGroups`|布林值，指定 Windows 群組是否包含在安全性內容中。  預設為 `true`。<br /><br /> 將這個屬性設定為 `true` 會有效能方面的影響，因為它會造成完整的群組擴充。  如果您不需要建立使用者所屬之群組的清單，請將此屬性設定為 `false`。|  
|`maxCacheLogonTokens`|整數，指定快取登入權杖的數目上限。  這個值應大於零。  預設值為 128。|  
|`membershipProviderName`|當繫結的 `clientCredentialType` 屬性設為 `username` 時，使用者名稱會對應至 Windows 帳戶。  您可以使用這個屬性來覆寫這個行為，該屬性是一個字串，其中包含 <xref:System.Web.Security.MembershipProvider> 值的名稱，可提供相關的密碼驗證機制。|  
|`userNamePasswordValidationMode`|指定驗證使用者名稱密碼的方法。  有效值為：<br /><br /> -   Windows<br />-   MembershipProvider<br />-   自訂<br /><br /> 預設為 Windows。  此屬性的型別為 <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<serviceCredentials\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|指定要用於驗證 \(Authenticate\) 服務的認證，以及用戶端認證的驗證 \(Validation\) 相關設定。|  
  
## 備註  
 如果服務使用的繫結中沒有任何一個是針對使用者名稱\/密碼驗證設定的，就會忽略這個項目的屬性。  其中包括 `customUserNamePasswordValidatorType`、`includeWindowsGroups`、`membershipProviderName` 和 `userNamePasswordValidationMode`。  
  
 如果服務使用的繫結中沒有任何一個是設定成針對使用者名稱\/密碼使用 Windows 驗證，就會忽略與登錄權杖快取相關的設定。  其中包括 `cacheLogonTokenLifetime`、`cacheLogonTokens` 和 `maxCacheLogonTokens`。  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.UserNameServiceElement>   
 <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>   
 <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>   
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>