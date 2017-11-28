---
title: "WCF 新聞訂閱概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af6d4c39-e5e8-4099-aee6-5261feff9107
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 629ec17ea01ec29480f15f5921d09e7497e9f8c8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="wcf-syndication-overview"></a>WCF 新聞訂閱概觀
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 會針對公開來自 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務的新聞訂閱摘要提供支援。 新聞訂閱是一種應用程式整合機制，可讓伺服器透過稱為摘要的互通格式來公開一些應用程式資料。 摘要是一種應用程式資料的集合，內含一些摘要層級的中繼資料 (標題、作者、URL 與其他中繼資料) 以及一系列的摘要項目。 摘要中的項目通常會依照時間順序，從距今最近的時間往回排列。 摘要項目包含一組標準的項目層級中繼資料 (標題、URL、建立日期、分類，與其他項目層級的中繼資料) 以及任意數量的特定應用程式資料。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 同時支援 Really Simple Syndication (RSS) 2.0 和 Atom 1.0 這兩種最常見的新聞訂閱摘要類型。  
  
## <a name="object-model"></a>物件模型  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會定義一組特定的新聞訂閱類別，讓您在不受格式影響的情況下使用摘要、摘要項目與相關的中繼資料：<xref:System.ServiceModel.Syndication.SyndicationFeed>、<xref:System.ServiceModel.Syndication.SyndicationItem>、<xref:System.ServiceModel.Syndication.SyndicationPerson>、<xref:System.ServiceModel.Syndication.SyndicationLink> 和其他特定的新聞訂閱類別。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]也會定義在 WCF REST 程式設計模型提供新聞訂閱支援包括建置的基礎結構類別： <xref:System.ServiceModel.Syndication.Atom10FeedFormatter>，和<!--zz <xref:System.ServiceModel.Syndication.RSS20FeedFormatter>--> `RSS20FeedFormatter`。 摘要格式器類別支援在 RSS 2.0 和 Atom 1.0 格式之間來回序列化物件模型。  
  
## <a name="scenarios"></a>案例  
 今日最常見的新聞訂閱應用就是網誌，也就是網誌作者會定期發行一些資訊。 這些內容可以是文字、影像、聲音，或其他類型的資訊。 許多報紙與雜誌也會透過新聞訂閱方式來發行新聞報導或文章。 只要訂閱這類摘要，使用者就可以隨時取得這些網站的最新資訊。 儘管新聞訂閱最常與網誌和出版社產生關聯，它還可以和其他用來公開大量資訊的應用程式搭配使用，例如，使用新聞訂閱摘要來公開 Bug 資料庫。 您可以建立 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務來公開稱為 `CodeDefects` 的作業。 這項作業所採用的參數能夠針對您要擷取 Bug 的人員指定其電子郵件地址。 用戶端可以使用下列 URL 來呼叫作業：http://someserver/bugDatabase/CodeDefects?user=johndoe。  
  
## <a name="syndication-formats"></a>新聞訂閱格式  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 新聞訂閱平台支援 RSS 2.0 和 Atom 1.0。  
  
## <a name="see-also"></a>另請參閱  
 [WCF Web HTTP 程式設計模型](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
