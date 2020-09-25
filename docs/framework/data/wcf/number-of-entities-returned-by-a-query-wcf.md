---
title: 如何：判斷查詢傳回的實體數目 (WCF 資料服務)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, row count
ms.assetid: 03d41a82-df95-40ac-8439-a6c327d37ba8
ms.openlocfilehash: 0513d7cdb3ab8de8cd8a73528f7e6038a0e4faed
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194280"
---
# <a name="how-to-determine-the-number-of-entities-returned-by-a-query-wcf-data-services"></a>如何：判斷查詢傳回的實體數目 (WCF 資料服務)

使用 WCF Data Services，您可以判斷查詢 URI 所指定之實體集中的實體數目。 這個計劃可能包含在查詢結果中或包含為整數值。 如需詳細資訊，請參閱 [查詢資料服務](querying-the-data-service-wcf-data-services.md)。  
  
 本主題中的範例使用 Northwind 範例資料服務和自動產生的用戶端資料服務類別。 此服務和用戶端資料類別會在您完成 [WCF Data Services 快速入門](quickstart-wcf-data-services.md)時建立。  
  
## <a name="example"></a>範例  

 這個範例會在呼叫 <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> 方法之後執行查詢。 <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> 屬性會傳回 `Customers` 實體集中的實體數目。  
  
 [!code-csharp[Astoria Northwind Client#CountAllCustomers](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#countallcustomers)]
 [!code-vb[Astoria Northwind Client#CountAllCustomers](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#countallcustomers)]  
  
## <a name="example"></a>範例  

 這個範例會呼叫 <xref:System.Linq.Enumerable.Count%2A> 方法，以便僅傳回代表 `Customers` 實體集中之實體數目的整數值。  
  
 [!code-csharp[Astoria Northwind Client#CountAllCustomersValueOnly](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#countallcustomersvalueonly)]
 [!code-vb[Astoria Northwind Client#CountAllCustomersValueOnly](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#countallcustomersvalueonly)]  
  
## <a name="see-also"></a>另請參閱

- [查詢資料服務](querying-the-data-service-wcf-data-services.md)
