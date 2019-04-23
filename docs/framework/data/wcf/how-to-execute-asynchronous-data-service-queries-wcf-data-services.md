---
title: HOW TO：執行非同步資料服務查詢 (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, asynchronous operations
- asynchronous operations [WCF Data Services]
ms.assetid: 902a2dc1-d0e9-4b00-90a8-becc4cb1f6a7
ms.openlocfilehash: f89a5004afeffe5aa9a28cb2d43374aede8a935e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59518158"
---
# <a name="how-to-execute-asynchronous-data-service-queries-wcf-data-services"></a>HOW TO：執行非同步資料服務查詢 (WCF Data Services)
透過使用 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 用戶端程式庫，您可以透過非同步的方式執行用戶端伺服器作業，例如執行查詢和儲存變更。 如需詳細資訊，請參閱 <<c0> [ 非同步作業](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)。  
  
> [!NOTE]
>  在必須於特定執行緒上叫用回呼的應用程式中，您必須明確地封送處理 <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> 方法的執行。 如需詳細資訊，請參閱 <<c0> [ 非同步作業](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)。  
  
 本主題中的範例使用 Northwind 範例資料服務和自動產生的用戶端資料服務類別。 當您完成建立這項服務和用戶端資料類別[WCF Data Services 快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何透過呼叫 <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> 方法啟動查詢來執行非同步查詢。 內嵌委派會呼叫 <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> 方法以顯示查詢結果。  
  
 [!code-csharp[Astoria Northwind Client#ExecuteQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#executequeryasync)]
 [!code-vb[Astoria Northwind Client#ExecuteQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#executequeryasync)]  
  
## <a name="see-also"></a>另請參閱

- [WCF Data Services 用戶端程式庫](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
