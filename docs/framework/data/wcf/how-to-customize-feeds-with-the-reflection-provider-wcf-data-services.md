---
title: 如何：自訂搭配反映提供者使用的摘要 (WCF 資料服務)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, customizing feeds
ms.assetid: 00c23dcf-9bb8-459a-a012-6c4d9bcad7e9
ms.openlocfilehash: fb22e87569a8e243813b3186232b6989abeb2a5e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161304"
---
# <a name="how-to-customize-feeds-with-the-reflection-provider-wcf-data-services"></a><span data-ttu-id="1d4be-102">如何：自訂搭配反映提供者使用的摘要 (WCF 資料服務)</span><span class="sxs-lookup"><span data-stu-id="1d4be-102">How to: Customize Feeds with the Reflection Provider (WCF Data Services)</span></span>

<span data-ttu-id="1d4be-103">WCF Data Services 可讓您自訂資料服務回應中的 Atom 序列化，讓實體的屬性可以對應至 AtomPub 通訊協定中定義的未使用元素。</span><span class="sxs-lookup"><span data-stu-id="1d4be-103">WCF Data Services enables you to customize the Atom serialization in a data service response so that properties of an entity may be mapped to unused elements that are defined in the AtomPub protocol.</span></span> <span data-ttu-id="1d4be-104">本主題說明如何針對資料模型中的實體類型 (經由使用反映提供者定義) 定義對應的屬性。</span><span class="sxs-lookup"><span data-stu-id="1d4be-104">This topic shows how to define mapping attributes for the entity types in a data model that is defined by using the reflection provider.</span></span> <span data-ttu-id="1d4be-105">如需詳細資訊，請參閱摘要 [自訂](feed-customization-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="1d4be-105">For more information, see [Feed Customization](feed-customization-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="1d4be-106">此範例的資料模型定義于 how [to：使用反映提供者建立資料服務](create-a-data-service-using-rp-wcf-data-services.md)中的主題。</span><span class="sxs-lookup"><span data-stu-id="1d4be-106">The data model for this example is defined in the topic [How to: Create a Data Service Using the Reflection Provider](create-a-data-service-using-rp-wcf-data-services.md)</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d4be-107">範例</span><span class="sxs-lookup"><span data-stu-id="1d4be-107">Example</span></span>  

 <span data-ttu-id="1d4be-108">在下列範例中，`Order` 類型的兩個屬性都對應至現有的元素項目。</span><span class="sxs-lookup"><span data-stu-id="1d4be-108">In the following example, both properties of the `Order` type are mapped to existing Atom elements.</span></span> <span data-ttu-id="1d4be-109">`Product` 類型的 `Item` 屬性會對應至不同命名空間中的自訂摘要屬性。</span><span class="sxs-lookup"><span data-stu-id="1d4be-109">The `Product` property of the `Item` type is mapped to a custom feed attribute in a separate namespace.</span></span>  
  
 [!code-csharp[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_custom_feeds/cs/orderitems.svc.cs#customiqueryablefeeds)]
 [!code-vb[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_custom_feeds/vb/orderitems.svc.vb#customiqueryablefeeds)]  
  
## <a name="example"></a><span data-ttu-id="1d4be-110">範例</span><span class="sxs-lookup"><span data-stu-id="1d4be-110">Example</span></span>  

 <span data-ttu-id="1d4be-111">上一個範例會傳回以下 URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items` 的結果。</span><span class="sxs-lookup"><span data-stu-id="1d4be-111">The previous example returns the following result for the URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items`.</span></span>  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResultInline](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/iqueryablefeedresultinline.xml#iqueryablefeedresultinline)]  
  
## <a name="see-also"></a><span data-ttu-id="1d4be-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d4be-112">See also</span></span>

- [<span data-ttu-id="1d4be-113">反映提供者</span><span class="sxs-lookup"><span data-stu-id="1d4be-113">Reflection Provider</span></span>](reflection-provider-wcf-data-services.md)
