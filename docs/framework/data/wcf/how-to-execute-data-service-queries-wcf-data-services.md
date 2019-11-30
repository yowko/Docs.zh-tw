---
title: 如何：執行資料服務查詢 (WCF 資料服務)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- querying the data service [WCF Data Services]
- WCF Data Services, querying
- WCF Data Services, accessing data
ms.assetid: 62997821-e0c6-4c4d-9fb7-1273fb5e5d18
ms.openlocfilehash: b06a21a45dcf6e67c41287c4cd59cdda4aa7b447
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569073"
---
# <a name="how-to-execute-data-service-queries-wcf-data-services"></a>如何：執行資料服務查詢 (WCF 資料服務)
WCF Data Services 可讓您使用所產生的用戶端資料服務類別，從以 .NET Framework 為基礎的用戶端應用程式查詢資料服務。 您可以使用下列其中一種方法執行查詢：  
  
- 針對您從 <xref:System.Data.Services.Client.DataServiceQuery%601> 工具所產生之 <xref:System.Data.Services.Client.DataServiceContext> 取得的具名 `Add Data Service Reference` 執行 LINQ 查詢。  
  
- 以隱含的方式列舉您從 <xref:System.Data.Services.Client.DataServiceQuery%601> 工具所產生之 <xref:System.Data.Services.Client.DataServiceContext> 取得的具名 `Add Data Service Reference`。  
  
- 透過在 <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> 呼叫 <xref:System.Data.Services.Client.DataServiceQuery%601> 方法或 <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> 方法，明確地進行非同步執行。  
  
 如需詳細資訊，請參閱[查詢資料服務](querying-the-data-service-wcf-data-services.md)。  
  
 本主題中的範例使用 Northwind 範例資料服務和自動產生的用戶端資料服務類別。 當您完成[WCF Data Services 快速入門](quickstart-wcf-data-services.md)時，會建立此服務和用戶端資料類別。  
  
## <a name="example"></a>範例  
 下列範例示範如何定義與執行針對 Northwind 資料服務傳回所有 `Customers` 的 LINQ 查詢。  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersLinq](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getallcustomerslinq)]
 [!code-vb[Astoria Northwind Client#GetAllCustomersLinq](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getallcustomerslinq)]  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 `Add Data Service Reference` 工具所產生的內容，隱含地執行會針對 Northwind 資料服務傳回所有 `Customers` 的查詢。 內容會自動判斷所要求之 `Customers` 實體集的 URI。 發生列舉時會隱含執行查詢。  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomers](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getallcustomers)]
 [!code-vb[Astoria Northwind Client#GetAllCustomers](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getallcustomers)]  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 <xref:System.Data.Services.Client.DataServiceContext> 明確地執行針對 Northwind 資料服務傳回所有 `Customers` 的查詢。  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersExplicit](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getallcustomersexplicit)]
 [!code-vb[Astoria Northwind Client#GetAllCustomersExplicit](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getallcustomersexplicit)]  
  
## <a name="see-also"></a>請參閱

- [如何：將查詢選項新增至資料服務查詢](how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)
