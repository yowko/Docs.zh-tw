---
title: HOW TO：自訂搭配反映提供者 （WCF 資料服務） 使用摘要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, customizing feeds
ms.assetid: 00c23dcf-9bb8-459a-a012-6c4d9bcad7e9
ms.openlocfilehash: 4f7f17e13dce81dfbaecc266b314e6695716f21c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59086828"
---
# <a name="how-to-customize-feeds-with-the-reflection-provider-wcf-data-services"></a>HOW TO：自訂搭配反映提供者 （WCF 資料服務） 使用摘要
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 可讓您自訂資料服務回應中的 Atom 序列化，因此實體的屬性可以對應至在 AtomPub 協定中定義的未使用項目。 本主題說明如何針對資料模型中的實體類型 (經由使用反映提供者定義) 定義對應的屬性。 如需詳細資訊，請參閱 <<c0> [ 摘要自訂](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md)。  
  
 此範例中的資料模型主題中所定義[How to:建立資料服務，使用反映提供者](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)  
  
## <a name="example"></a>範例  
 在下列範例中，`Order` 類型的兩個屬性都對應至現有的元素項目。 `Product` 類型的 `Item` 屬性會對應至不同命名空間中的自訂摘要屬性。  
  
 [!code-csharp[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria custom feeds/cs/orderitems.svc.cs#customiqueryablefeeds)]
 [!code-vb[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria custom feeds/vb/orderitems.svc.vb#customiqueryablefeeds)]  
  
## <a name="example"></a>範例  
 上一個範例會傳回以下 URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items` 的結果。  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResultInline](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/iqueryablefeedresultinline.xml#iqueryablefeedresultinline)]  
  
## <a name="see-also"></a>另請參閱

- [反映提供者](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)
