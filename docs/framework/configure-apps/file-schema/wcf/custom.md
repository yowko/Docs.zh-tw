---
title: "&lt;自訂&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# &lt;自訂&gt;
指定自訂對等解析程式服務的設定。  
  
## 語法  
  
```  
  
<custom address="Uri"  
   resolverType="String">  
      <headers/>  
   <identity/>  
</peerResolver>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`address`|URI，這個 URI 會指定裝載自訂解析程式服務之對等節點的端點位址。|  
|`resolverType`|字串，這個字串會指定自訂對等解析服務之型別。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<識別\>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|指定使用這個項目設定的自訂對等解析程式的身分識別。  此項目的型別為 <xref:System.ServiceModel.Configuration.IdentityElement>。|  
|[\<頁首\>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|位址標頭的集合，用於自訂對等解析程式所處理的 SOAP 訊息。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<resolver\>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|對等解析程式，這個程式可用於將對等網狀結構 ID 解析成一組對等節點位址，這組位址可表示參與網狀結構的數個節點。|  
  
## 備註  
 這個項目定義自訂對等解析程式服務的基本設定，包括裝載服務之對等的端點位址以及任何特定繫結設定。  如需建立自訂解析程式的詳細資訊，請參閱[Adding a Custom Resolver to a PeerChannel Application](http://msdn.microsoft.com/zh-tw/12aa3787-2962-439c-ad27-46523c8b0419)。  
  
## 請參閱  
 <xref:System.Servicemodel.PeerResolvers.CustomPeerResolverService>   
 <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>   
 <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>   
 <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>   
 [對等解析程式](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)   
 [Adding a Custom Resolver to a PeerChannel Application](http://msdn.microsoft.com/zh-tw/12aa3787-2962-439c-ad27-46523c8b0419)