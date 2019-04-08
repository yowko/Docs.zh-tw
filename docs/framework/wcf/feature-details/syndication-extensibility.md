---
title: 新聞訂閱擴充性
ms.date: 03/30/2017
ms.assetid: 4d941175-74a2-4b15-81b3-086e8a95d25f
ms.openlocfilehash: 226ea682d8b17a818e6d5be2097a19315d106bda
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170796"
---
# <a name="syndication-extensibility"></a>新聞訂閱擴充性
新聞訂閱 API 主要是提供格式中性的程式設計模型，以允許以各種格式將新聞訂閱內容寫入網路中。 抽象資料模型包含下列類別：  
  
-   <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 這些類別可緊密地對應至 Atom 1.0 規格中所定義的建構 (儘管其中有些名稱不同)。  
  
 擴充性是新聞訂閱通訊協定的一項重要功能。 Atom 1.0 和 RSS 2.0 兩者都會將屬性和項目新增到規格中未定義的新聞訂閱摘要中。 Windows Communication Foundation (WCF) 的新聞訂閱程式設計模型提供下列方式使用自訂屬性與延伸及鬆散型別存取和衍生新類別。  
  
## <a name="loosely-typed-access"></a>鬆散型別存取  
 您需要撰寫額外的程式碼，才能藉由衍生新類別來新增延伸。 另一種方式則是透過鬆散型別方式來存取延伸。 在新聞訂閱抽象資料模型中定義的所有型別都包含名為 `AttributeExtensions` 和 `ElementExtensions` 的屬性，唯一的例外是，<xref:System.ServiceModel.Syndication.SyndicationContent> 具有 `AttributeExtensions` 屬性，但不包含 `ElementExtensions` 屬性。 這些屬性是分別是 `TryParseAttribute` 和 `TryParseElement` 方法無法處理之延伸的集合。 您可以呼叫 <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection.ReadElementExtensions%2A?displayProperty=nameWithType> 屬性 (屬於 `ElementExtensions`、<xref:System.ServiceModel.Syndication.SyndicationFeed>、<xref:System.ServiceModel.Syndication.SyndicationItem>、<xref:System.ServiceModel.Syndication.SyndicationLink> 和 <xref:System.ServiceModel.Syndication.SyndicationPerson>) 上的 <xref:System.ServiceModel.Syndication.SyndicationCategory> 存取這些未處理的延伸。 這群方法集合會先找到所有包含指定名稱和命名空間的延伸、加以個別還原序列化為 `TExtension` 的執行個體，然後將它們當成 `TExtension` 物件的集合傳回。  
  
## <a name="deriving-a-new-class"></a>衍生新的類別  
 您可以從任何一個現有的抽象資料模型類別中衍生新的類別。 在您實作應用程式時，如果所使用的大部分摘要都包含特定延伸時，就可以這麼做。 在本主題中，程式使用的大部分摘要都包含 `MyExtension` 延伸。 若要提供更好的程式設計體驗，請執行下列步驟：  
  
-   建立可保留延伸資料的類別。 在此案例中，建立名為 MyExtension 的類別。  
  
-   從 <xref:System.ServiceModel.Syndication.SyndicationItem> 衍生名為 MyExtensionItem 的類別並公開型別 MyExtension 的屬性以供程式設計之用。  
  
-   讀入 MyExtension 時，覆寫 MyExtensionItem 類別中的 <xref:System.ServiceModel.Syndication.SyndicationItem.TryParseElement%28System.Xml.XmlReader%2CSystem.String%29> 以產生新的 MyExtension 執行個體。  
  
-   覆寫 MyExtensionItem 類別中的 <xref:System.ServiceModel.Syndication.SyndicationItem.WriteElementExtensions%28System.Xml.XmlWriter%2CSystem.String%29> 以將 MyExtension 屬性內容寫入 XML 寫入器。  
  
-   從 <xref:System.ServiceModel.Syndication.SyndicationFeed> 衍生稱為 MyExtensionFeed 的類別。  
  
-   覆寫 MyExtensionFeed 類別中的 <xref:System.ServiceModel.Syndication.SyndicationFeed.CreateItem> 以產生 MyExtensionItem，而不是預設的 <xref:System.ServiceModel.Syndication.SyndicationItem>。 <xref:System.ServiceModel.Syndication.SyndicationFeed> 和 <xref:System.ServiceModel.Syndication.SyndicationItem> 中定義了一系列的方法，可建立 <xref:System.ServiceModel.Syndication.SyndicationLink>、<xref:System.ServiceModel.Syndication.SyndicationCategory> 和 <xref:System.ServiceModel.Syndication.SyndicationPerson> 物件 (例如，<xref:System.ServiceModel.Syndication.SyndicationFeed.CreateLink>、<xref:System.ServiceModel.Syndication.SyndicationFeed.CreateCategory> 和 <xref:System.ServiceModel.Syndication.SyndicationFeed.CreatePerson>)。 這些全部都可加以覆寫，以建立自訂的衍生類別。  
  
## <a name="see-also"></a>另請參閱

- [WCF 新聞訂閱概觀](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md)
- [新聞訂閱架構](../../../../docs/framework/wcf/feature-details/architecture-of-syndication.md)
