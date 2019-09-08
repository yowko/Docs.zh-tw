---
title: 作法：將現有實體附加至 DataServiceCoNtext （WCF Data Services）
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: e3f2d71d-434c-4e98-91c3-95adae4702b6
ms.openlocfilehash: 160f0afc2e1baf033557b7114a51145a5c983e29
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791179"
---
# <a name="how-to-attach-an-existing-entity-to-the-dataservicecontext-wcf-data-services"></a>HOW TO：將現有實體附加至 DataServiceCoNtext （WCF Data Services）
當實體已存在於資料服務時， [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]用戶端程式庫可讓您將代表該實體的物件直接附加<xref:System.Data.Services.Client.DataServiceContext>至，而不需要先執行查詢。 如需詳細資訊，請參閱[更新資料服務](updating-the-data-service-wcf-data-services.md)。  
  
 本主題中的範例使用 Northwind 範例資料服務和自動產生的用戶端資料服務類別。 當您完成[WCF Data Services 快速入門](quickstart-wcf-data-services.md)時，會建立此服務和用戶端資料類別。  
  
## <a name="example"></a>範例  
 下列範例示範如何建立現有的 `Customer` 物件，此物件包含要儲存至資料服務的變更。 系統會將物件附加至內容，並呼叫 <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> 方法，將附加物件標記為 <xref:System.Data.Services.Client.EntityStates.Modified>，然後再呼叫 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> 方法。  
  
 [!code-csharp[Astoria Northwind Client#AttachObject](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#attachobject)]
 [!code-vb[Astoria Northwind Client#AttachObject](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#attachobject)]  
  
## <a name="see-also"></a>另請參閱

- [WCF Data Services 用戶端程式庫](wcf-data-services-client-library.md)
