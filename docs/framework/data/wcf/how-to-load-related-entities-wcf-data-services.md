---
title: 如何：載入相關實體 (WCF 資料服務)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: 6f143d30-d997-4e6b-bcf0-d5c394ecb108
ms.openlocfilehash: 1ef7fa93b5afdf664f22bd69d3fe3a3b17e98f18
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91180708"
---
# <a name="how-to-load-related-entities-wcf-data-services"></a>如何：載入相關實體 (WCF 資料服務)

當您需要在 WCF Data Services 中載入相關聯的實體時，您可以 <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> 在類別上使用方法 <xref:System.Data.Services.Client.DataServiceContext> 。 您也可以 <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> 在上使用方法， <xref:System.Data.Services.Client.DataServiceQuery%601> 要求將相關實體立即載入相同的查詢回應中。  
  
 本主題中的範例使用 Northwind 範例資料服務和自動產生的用戶端資料服務類別。 此服務和用戶端資料類別會在您完成 [WCF Data Services 快速入門](quickstart-wcf-data-services.md)時建立。  
  
## <a name="example"></a>範例  

 下列範例示範如何明確地載入與所傳回之每個 `Customer` 執行個體相關的 `Orders`。  
  
 [!code-csharp[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadrelatedordercustomer)]
 [!code-vb[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadrelatedordercustomer)]  
  
## <a name="example"></a>範例  

 下列範例示範如何使用 <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> 方法傳回屬於查詢所傳回之 `Order Details` 的 `Orders` 方法。  
  
 [!code-csharp[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#expandorderdetails)]
 [!code-vb[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#expandorderdetails)]  
  
## <a name="see-also"></a>另請參閱

- [查詢資料服務](querying-the-data-service-wcf-data-services.md)
