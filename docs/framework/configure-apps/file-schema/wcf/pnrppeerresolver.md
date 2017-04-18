---
title: "&lt;pnrpPeerResolver&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# &lt;pnrpPeerResolver&gt;
指定對等名稱解析通訊協定 \(Peer Name Resolution Protocol，PNRP\) 解析程式做為解析程式使用。  這是一個選擇性的項目，因為 PNRP 是預設的解析程式。  
  
## 語法  
  
```  
  
<pnrpResolver resolverType="String" />  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|resolverType|字串，指定要使用的解析程式。  這是一個選擇性的屬性。  如果未設定，或如果設定為空字串，則使用 PNRP。|  
  
### 子項目  
 無  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<繫結\>](../../../../../docs/framework/misc/binding.md)|定義自訂繫結的所有繫結功能。|  
  
## 範例  
  
```  
<pnrpResolver resolverType="" />  
```  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>   
 <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>   
 <xref:System.ServiceModel.Channels.CustomBinding>   
 [繫結](../../../../../docs/framework/wcf/bindings.md)   
 [擴充繫結](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
 [自訂繫結](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
 [\<customBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)   
 [對等解析程式](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)