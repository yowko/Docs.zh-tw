---
title: "HOW TO：透過反映提供者自訂摘要 (WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF Data Services, 自訂"
  - "WCF Data Services, 自訂摘要"
ms.assetid: 00c23dcf-9bb8-459a-a012-6c4d9bcad7e9
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# HOW TO：透過反映提供者自訂摘要 (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 可讓您自訂資料服務回應中的 Atom 序列化，因此可以將實體的屬性對應至在 AtomPub 通訊協定中定義的未使用項目。  本主題說明如何針對資料模型中的實體類型 \(經由使用反映提供者定義\) 定義對應的屬性。  如需詳細資訊，請參閱[摘要自訂](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md)。  
  
 此範例的資料模型定義於 [HOW TO：使用反映提供者建立資料服務](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)主題中。  
  
## 範例  
 在下列範例中，`Order` 類型的兩個屬性都對應至現有的元素項目。  `Item` 類型的 `Product` 屬性會對應至不同命名空間中的自訂摘要屬性。  
  
 [!code-csharp[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria custom feeds/cs/orderitems.svc.cs#customiqueryablefeeds)]
 [!code-vb[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria custom feeds/vb/orderitems.svc.vb#customiqueryablefeeds)]  
  
## 範例  
 上一個範例會傳回以下 URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items` 的結果。  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResultInline](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/iqueryablefeedresultinline.xml#iqueryablefeedresultinline)]  
  
## 請參閱  
 [反映提供者](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)