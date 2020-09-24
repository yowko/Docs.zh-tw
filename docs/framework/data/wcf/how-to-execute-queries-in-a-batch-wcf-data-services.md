---
title: 如何：批次執行查詢 (WCF 資料服務)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, batch requests
ms.assetid: 3b4db7df-bd33-43a1-8ea4-63a18e131f97
ms.openlocfilehash: b9b18aabc8321d2f77c3781b836eeb6a0d320229
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150592"
---
# <a name="how-to-execute-queries-in-a-batch-wcf-data-services"></a>如何：批次執行查詢 (WCF 資料服務)

藉由使用 WCF Data Services 用戶端程式庫，您可以在單一批次中針對資料服務執行一個以上的查詢。 如需詳細資訊，請參閱 [批次處理作業](batching-operations-wcf-data-services.md)。  
  
 本主題中的範例使用 Northwind 範例資料服務和自動產生的用戶端資料服務類別。 此服務和用戶端資料類別會在您完成 [WCF Data Services 快速入門](quickstart-wcf-data-services.md)時建立。  
  
## <a name="example"></a>範例  

 下列範例顯示如何呼叫 <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> 方法，執行 <xref:System.Data.Services.Client.DataServiceRequest%601> 物件的陣列，其中包含從 Northwind 資料服務同時傳回 `Customers` 和 `Products` 物件的查詢。 在傳回的 <xref:System.Data.Services.Client.QueryOperationResponse%601>中，會列舉 <xref:System.Data.Services.Client.DataServiceResponse> 物件集合以及包含在每一個 <xref:System.Data.Services.Client.QueryOperationResponse%601> 中的物件集合。  
  
 [!code-csharp[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#batchquery)]
 [!code-vb[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#batchquery)]  
  
## <a name="see-also"></a>另請參閱

- [WCF 資料服務用戶端程式庫](wcf-data-services-client-library.md)
