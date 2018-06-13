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
ms.openlocfilehash: 984a4aac43689be0ec80e7f6c289e8d5229e9e1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358004"
---
# <a name="how-to-customize-feeds-with-the-reflection-provider-wcf-data-services"></a><span data-ttu-id="3eced-102">如何：自訂搭配反映提供者使用的摘要 (WCF 資料服務)</span><span class="sxs-lookup"><span data-stu-id="3eced-102">How to: Customize Feeds with the Reflection Provider (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="3eced-103"> 可讓您自訂資料服務回應中的 Atom 序列化，因此可以將實體的屬性對應至在 AtomPub 通訊協定中定義的未使用項目。</span><span class="sxs-lookup"><span data-stu-id="3eced-103"> enables you to customize the Atom serialization in a data service response so that properties of an entity may be mapped to unused elements that are defined in the AtomPub protocol.</span></span> <span data-ttu-id="3eced-104">本主題說明如何針對資料模型中的實體類型 (經由使用反映提供者定義) 定義對應的屬性。</span><span class="sxs-lookup"><span data-stu-id="3eced-104">This topic shows how to define mapping attributes for the entity types in a data model that is defined by using the reflection provider.</span></span> <span data-ttu-id="3eced-105">如需詳細資訊，請參閱[摘要自訂](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="3eced-105">For more information, see [Feed Customization](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="3eced-106">本主題中定義此範例中的資料模型[How to： 建立資料服務，使用反映提供者](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)</span><span class="sxs-lookup"><span data-stu-id="3eced-106">The data model for this example is defined in the topic [How to: Create a Data Service Using the Reflection Provider](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)</span></span>  
  
## <a name="example"></a><span data-ttu-id="3eced-107">範例</span><span class="sxs-lookup"><span data-stu-id="3eced-107">Example</span></span>  
 <span data-ttu-id="3eced-108">在下列範例中，`Order` 類型的兩個屬性都對應至現有的元素項目。</span><span class="sxs-lookup"><span data-stu-id="3eced-108">In the following example, both properties of the `Order` type are mapped to existing Atom elements.</span></span> <span data-ttu-id="3eced-109">`Product` 類型的 `Item` 屬性會對應至不同命名空間中的自訂摘要屬性。</span><span class="sxs-lookup"><span data-stu-id="3eced-109">The `Product` property of the `Item` type is mapped to a custom feed attribute in a separate namespace.</span></span>  
  
 [!code-csharp[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria custom feeds/cs/orderitems.svc.cs#customiqueryablefeeds)]
 [!code-vb[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria custom feeds/vb/orderitems.svc.vb#customiqueryablefeeds)]  
  
## <a name="example"></a><span data-ttu-id="3eced-110">範例</span><span class="sxs-lookup"><span data-stu-id="3eced-110">Example</span></span>  
 <span data-ttu-id="3eced-111">上一個範例會傳回以下 URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items` 的結果。</span><span class="sxs-lookup"><span data-stu-id="3eced-111">The previous example returns the following result for the URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items`.</span></span>  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResultInline](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/iqueryablefeedresultinline.xml#iqueryablefeedresultinline)]  
  
## <a name="see-also"></a><span data-ttu-id="3eced-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3eced-112">See Also</span></span>  
 [<span data-ttu-id="3eced-113">反映提供者</span><span class="sxs-lookup"><span data-stu-id="3eced-113">Reflection Provider</span></span>](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)
