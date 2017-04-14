---
title: "&lt;resolver&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# &lt;resolver&gt;
指定對等解析程式，用於將對等網狀結構 ID 解析成一組對等節點位址，這組位址可表示參與網狀結構的數個節點。  
  
## 語法  
  
```  
  
<resolver mode="Auto/Custom/Pnrp"  
   referralPolicy="DoNotShare/Service/Share">  
</resolver>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`mode`|字串，指定與此服務相關聯的對等解析程式執行個體是 PNRP 專用、自訂解析程式或自動判定。  此屬性的型別為 <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>。|  
|`referralPolicy`|字串，指定在對等之間共用轉介的方法。  此屬性的型別為 <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<頁首\>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|指定自訂對等解析程式服務的設定。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<繫結\>](../../../../../docs/framework/misc/binding.md)|定義 [\<netPeerTcpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md) 的所有繫結功能。|  
  
## 備註  
 對等名稱解析程式是對等通道用來尋找參與對等網狀結構之對等節點的探索服務。  您也可以使用這個解析程式將節點「註冊」到對等網狀結構，透過這樣的機制使得對等節點成為已知的，並且可從對等網狀結構中取得。  如需對等解析程式的詳細資訊，請參閱[對等解析程式](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)。  
  
## 請參閱  
 <xref:System.ServiceModel.PeerResolver>   
 <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>   
 <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>   
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>   
 <xref:System.ServiceModel.Configuration.PeerResolverElement>   
 [對等解析程式](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)   
 [Adding a Custom Resolver to a PeerChannel Application](http://msdn.microsoft.com/zh-tw/12aa3787-2962-439c-ad27-46523c8b0419)