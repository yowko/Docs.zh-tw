---
title: "&lt;serviceCredentials&gt; 的 &lt;windowsAuthentication&gt;  | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# &lt;serviceCredentials&gt; 的 &lt;windowsAuthentication&gt; 
指定 Windows 服務認證的設定。  
  
## 語法  
  
```  
  
<windowsAuthentication  
      allowAnonymousLogons="Boolean"  
      includeWindowsGroups="Boolean" />  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`includeWindowsGroups`|選擇性的布林值屬性，指定系統是否在安全性內容中包含 Windows 群組。  預設為 `true`。<br /><br /> 將這個屬性設定為 `true` 會有效能方面的影響，因為它會造成完整的群組擴充。  如果您不需要建立使用者所屬之群組的清單，請將此屬性設定為 `false`。|  
|`allowAnonymousLogons`|選擇性的布林值屬性，指定是否允許匿名、未經驗證的呼叫端。  預設為 `false`。<br /><br /> 當繫結的 `clientCredentialType` 屬性設定為 `Windows` 時，系統不允許匿名呼叫端。  這表示只有經過網域或工作群組驗證的呼叫端才可以存取系統。  您可以使用這個屬性覆寫這個行為。<br /><br /> 使用這個設定時需具備高度警覺。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<serviceCredentials\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|指定要用於驗證 \(Authenticate\) 服務的認證，以及用戶端認證的驗證 \(Validation\) 相關設定。|  
  
## 備註  
 使用此項目並藉由設定 `allowAnonymousLogons` 屬性，指定是否允許匿名 Windows 使用者存取。  您也可以藉由設定 `includeWindowsGroups` 屬性，指定是否要在 AuthorizationContext 中包含使用者所屬群組的資訊。  如果該屬性設為 `true` \(預設值\)，服務就可以判斷用戶端屬於哪個 Windows 群組。  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.WindowsServiceElement>   
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>   
 <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>   
 <xref:System.ServiceModel.Security.WindowsServiceCredential>