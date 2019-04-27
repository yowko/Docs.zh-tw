---
title: HOW TO：載入相關的實體 (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: 6f143d30-d997-4e6b-bcf0-d5c394ecb108
ms.openlocfilehash: 75e1d583d2a4d519619a440800cdeb1403fedac2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61936491"
---
# <a name="how-to-load-related-entities-wcf-data-services"></a>HOW TO：載入相關的實體 (WCF Data Services)
當您需要在 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 中載入相關的實體時，可以在 <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> 類別上使用 <xref:System.Data.Services.Client.DataServiceContext> 方法。 您也可以使用<xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A>方法<xref:System.Data.Services.Client.DataServiceQuery%601>要求相同的查詢回應中，提早載入相關的實體。  
  
 本主題中的範例使用 Northwind 範例資料服務和自動產生的用戶端資料服務類別。 當您完成建立這項服務和用戶端資料類別[WCF Data Services 快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何明確地載入與所傳回之每個 `Customer` 執行個體相關的 `Orders`。  
  
 [!code-csharp[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadrelatedordercustomer)]
 [!code-vb[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadrelatedordercustomer)]  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> 方法傳回屬於查詢所傳回之 `Order Details` 的 `Orders` 方法。  
  
 [!code-csharp[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#expandorderdetails)]
 [!code-vb[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#expandorderdetails)]  
  
## <a name="see-also"></a>另請參閱

- [查詢資料服務](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
