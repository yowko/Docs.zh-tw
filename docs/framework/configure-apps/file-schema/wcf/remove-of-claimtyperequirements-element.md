---
title: "&lt;claimTypeRequirements&gt; 項目的 &lt;remove&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8ef05bc4-1950-4ee4-95c5-1c6a394eff7e
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# &lt;claimTypeRequirements&gt; 項目的 &lt;remove&gt;
指定聯合認證中要移除的宣告型別。  
  
## 語法  
  
```  
  
<claimTypeRequirements>  
      <remove claimType="URI" />  
</claimTypeRequirements>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|claimType|定義要移除之宣告型別的 URI。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<claimTypeRequirements\>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|指定必要宣告型別的集合。  每個項目的型別為 <xref:System.ServiceModel.Configuration.ClaimTypeElement>。<br /><br /> 在聯合案例中，服務會聲明對傳入認證的需求。  例如，傳入認證必須處理特定的一組宣告型別。  這個集合中的每一個項目都會指定要顯示在聯合認證中的必要和選擇性宣告型別。|  
  
## 請參閱  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>   
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>   
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>   
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>   
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>