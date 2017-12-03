---
title: "如何：載入相關實體 (WCF 資料服務)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: 6f143d30-d997-4e6b-bcf0-d5c394ecb108
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fce222a07ad57820af6165b456fe4e2033900aee
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-load-related-entities-wcf-data-services"></a>如何：載入相關實體 (WCF 資料服務)
當您需要在 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 中載入相關的實體時，可以在 <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> 類別上使用 <xref:System.Data.Services.Client.DataServiceContext> 方法。 您也可以使用<xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A>方法<xref:System.Data.Services.Client.DataServiceQuery%601>要求，在相同的查詢回應中立即載入相關的實體。  
  
 本主題中的範例使用 Northwind 範例資料服務和自動產生的用戶端資料服務類別。 當您完成建立此服務和用戶端資料類別[WCF Data Services 快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何明確地載入與所傳回之每個 `Customer` 執行個體相關的 `Orders`。  
  
 [!code-csharp[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#loadrelatedordercustomer)]
 [!code-vb[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#loadrelatedordercustomer)]  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> 方法傳回屬於查詢所傳回之 `Order Details` 的 `Orders` 方法。  
  
 [!code-csharp[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#expandorderdetails)]
 [!code-vb[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#expandorderdetails)]  
  
## <a name="see-also"></a>另請參閱  
 [查詢資料服務](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
