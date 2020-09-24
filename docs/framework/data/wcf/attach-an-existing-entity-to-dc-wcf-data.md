---
title: 如何：將現有實體附加至 DataServiceContext (WCF 資料服務)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: e3f2d71d-434c-4e98-91c3-95adae4702b6
ms.openlocfilehash: 69ca64f4ab3470c1a4f58c582b31c06aed9cadd5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166127"
---
# <a name="how-to-attach-an-existing-entity-to-the-dataservicecontext-wcf-data-services"></a>如何：將現有實體附加至 DataServiceContext (WCF 資料服務)

當實體已經存在於資料服務中時，WCF Data Services 用戶端程式庫可讓您將代表實體的物件直接附加至， <xref:System.Data.Services.Client.DataServiceContext> 而不需要先執行查詢。 如需詳細資訊，請參閱 [更新資料服務](updating-the-data-service-wcf-data-services.md)。  
  
 本主題中的範例使用 Northwind 範例資料服務和自動產生的用戶端資料服務類別。 此服務和用戶端資料類別會在您完成 [WCF Data Services 快速入門](quickstart-wcf-data-services.md)時建立。  
  
## <a name="example"></a>範例  

 下列範例示範如何建立現有的 `Customer` 物件，此物件包含要儲存至資料服務的變更。 系統會將物件附加至內容，並呼叫 <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> 方法，將附加物件標記為 <xref:System.Data.Services.Client.EntityStates.Modified>，然後再呼叫 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> 方法。  
  
 [!code-csharp[Astoria Northwind Client#AttachObject](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#attachobject)]
 [!code-vb[Astoria Northwind Client#AttachObject](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#attachobject)]  
  
## <a name="see-also"></a>另請參閱

- [WCF 資料服務用戶端程式庫](wcf-data-services-client-library.md)
