---
title: "&lt;authorizationPolicies&gt; 的 &lt;add&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# &lt;authorizationPolicies&gt; 的 &lt;add&gt;
指定用於宣告轉換的驗證原則。  
  
## 語法  
  
```  
  
<authorizationPolicies>  
   <add policyType="String" />  
</authorizationPolicies>  
```  
  
## 類型  
 `Type`  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`policyType`|必要的字串屬性。<br /><br /> [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 存取控制模型支援提供一組授權原則做為型別。  此屬性會指定授權原則，可將一組輸入宣告轉換為另一組宣告。  它可以做為授與或拒絕存取控制 \(Access Control\) 的基礎。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<authorizationPolicies\>](../../../../../docs/framework/configure-apps/file-schema/wcf/authorizationpolicies.md)|指定授權原則型別的集合。|  
  
## 備註  
 每個授權原則包含一個必要的 `policyType` 屬性字串。  該屬性會指定授權原則，可讓一組輸入宣告轉換成另一組宣告。  它可以做為授與或拒絕存取控制 \(Access Control\) 的基礎。  如需授權原則運作方式的詳細資訊，請參閱 <xref:System.IdentityModel.Policy.IAuthorizationPolicy> 和[授權原則](../../../../../docs/framework/wcf/samples/authorization-policy.md)。  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>   
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>   
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>   
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>   
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>   
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>   
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>   
 [授權存取服務作業](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)   
 [HOW TO：為服務建立自訂授權管理員](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)   
 [\<add\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-authorizationpolicies.md)   
 [授權原則](../../../../../docs/framework/wcf/samples/authorization-policy.md)