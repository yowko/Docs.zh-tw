---
title: HOW TO：執行資料服務查詢（WCF Data Services）
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- querying the data service [WCF Data Services]
- WCF Data Services, querying
- WCF Data Services, accessing data
ms.assetid: 62997821-e0c6-4c4d-9fb7-1273fb5e5d18
ms.openlocfilehash: 984bba9f31ddaee68c6997ba6da09a511e42b4ce
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780072"
---
# <a name="how-to-execute-data-service-queries-wcf-data-services"></a>HOW TO：執行資料服務查詢（WCF Data Services）
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 可讓您使用所產生的用戶端資料服務類別，從以 .NET Framework 為基礎的用戶端應用程式查詢資料服務。 您可以使用下列其中一種方法執行查詢：  
  
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
  
## <a name="see-also"></a>另請參閱

- [如何：將查詢選項加入至資料服務查詢](how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)
