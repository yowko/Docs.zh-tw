---
title: 作法：新增、修改和刪除實體（WCF Data Services）
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: a00f8933-b232-4445-95ba-adc634f055d8
ms.openlocfilehash: 13c59bee9fc58dbe8c5b8c768fe9ff8b31d72e76
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780253"
---
# <a name="how-to-add-modify-and-delete-entities-wcf-data-services"></a>HOW TO：新增、修改和刪除實體（WCF Data Services）
透過用戶端程式庫，您可以在中的<xref:System.Data.Services.Client.DataServiceContext>物件上執行對等的動作，以建立、更新和刪除資料服務中的實體資料。 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 如需詳細資訊，請參閱[更新資料服務](updating-the-data-service-wcf-data-services.md)。  
  
 本主題中的範例使用 Northwind 範例資料服務和自動產生的用戶端資料服務類別。 當您完成[WCF Data Services 快速入門](quickstart-wcf-data-services.md)時，會建立此服務和用戶端資料類別。  
  
## <a name="example"></a>範例  
 下列範例會建立新的物件執行個體，然後呼叫 <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> 的 <xref:System.Data.Services.Client.DataServiceContext> 方法，在內容中建立項目。 呼叫 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> 方法時，會將 HTTP POST 訊息傳送至資料服務。  
  
 [!code-csharp[Astoria Northwind Client#AddProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addproduct)]
 [!code-vb[Astoria Northwind Client#AddProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addproduct)]  
  
## <a name="example"></a>範例  
 下列範例會擷取並修改現有的物件，然後呼叫 <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> 的 <xref:System.Data.Services.Client.DataServiceContext> 方法，將內容中的項目標記為已更新。 呼叫 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> 方法時，會將 HTTP MERGE 訊息傳送至資料服務。  
  
 [!code-csharp[Astoria Northwind Client#ModifyCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#modifycustomer)]
 [!code-vb[Astoria Northwind Client#ModifyCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#modifycustomer)]  
  
## <a name="example"></a>範例  
 下列範例會在 <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> 呼叫 <xref:System.Data.Services.Client.DataServiceContext> 方法，將內容中的項目標記為已刪除。 呼叫 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> 方法時，會將 HTTP DELETE 訊息傳送至資料服務。  
  
 [!code-csharp[Astoria Northwind Client#DeleteProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#deleteproduct)]
 [!code-vb[Astoria Northwind Client#DeleteProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#deleteproduct)]  
  
## <a name="example"></a>範例  
 下列範例會建立一個新的物件執行個體，然後呼叫 <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> 的 <xref:System.Data.Services.Client.DataServiceContext> 方法，在內容中建立項目與相關訂單的連結。 呼叫 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> 方法時，會將 HTTP POST 訊息傳送至資料服務。  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorderauto)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorderauto)]  
  
## <a name="see-also"></a>另請參閱

- [WCF Data Services 用戶端程式庫](wcf-data-services-client-library.md)
- [如何：將現有的實體附加至 DataServiceCoNtext](attach-an-existing-entity-to-dc-wcf-data.md)
- [如何：定義實體關聯性](how-to-define-entity-relationships-wcf-data-services.md)
- [批次處理作業](batching-operations-wcf-data-services.md)
