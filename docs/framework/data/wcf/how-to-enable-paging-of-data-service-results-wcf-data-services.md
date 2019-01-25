---
title: HOW TO：啟用分頁功能，為資料服務結果 (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- paging output [WCF Data Services]
ms.assetid: 9a316cbd-9612-4482-a541-a10bc78b2635
ms.openlocfilehash: be5bd41494c27724a360b785b8706b618447e7de
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54523451"
---
# <a name="how-to-enable-paging-of-data-service-results-wcf-data-services"></a>HOW TO：啟用分頁功能，為資料服務結果 (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 可讓您限制資料服務查詢所傳回的實體數目。 當服務已初始化且可針對每個實體集分別設定服務時，分頁限制會定義於所呼叫的方法中。  
  
 啟用分頁時，摘要中的最後一個項目會包含下一頁資料的連結。 如需詳細資訊，請參閱 <<c0> [ 設定資料服務](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)。  
  
 本主題顯示如何修改資料服務以啟用傳回之 `Customers` 和 `Orders` 實體集之分頁。 本主題中的範例使用 Northwind 範例資料服務。 當您完成時，此服務會建立[WCF Data Services 快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)。  
  
### <a name="how-to-enable-paging-of-returned-customers-and-orders-entity-sets"></a>如何啟用傳回之 Customers 和 Orders 實體集之分頁  
  
-   在資料服務的程式碼中，以下列程式碼取代 `InitializeService` 函數中的預留位置程式碼：  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## <a name="see-also"></a>另請參閱
- [載入延後內容](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)
- [如何：載入分頁結果](../../../../docs/framework/data/wcf/how-to-load-paged-results-wcf-data-services.md)
