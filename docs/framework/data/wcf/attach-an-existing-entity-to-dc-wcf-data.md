---
title: 如何：將現有實體附加至 DataServiceContext (WCF 資料服務)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: e3f2d71d-434c-4e98-91c3-95adae4702b6
ms.openlocfilehash: 7c8355ea9e9823e7cab6f43c0f3f901948d1d539
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569384"
---
# <a name="how-to-attach-an-existing-entity-to-the-dataservicecontext-wcf-data-services"></a>如何：將現有實體附加至 DataServiceContext (WCF 資料服務)
當實體已存在於資料服務時，WCF Data Services 用戶端程式庫可讓您將代表該實體的物件直接附加至 <xref:System.Data.Services.Client.DataServiceContext>，而不需要先執行查詢。 如需詳細資訊，請參閱[更新資料服務](updating-the-data-service-wcf-data-services.md)。  
  
 本主題中的範例使用 Northwind 範例資料服務和自動產生的用戶端資料服務類別。 當您完成[WCF Data Services 快速入門](quickstart-wcf-data-services.md)時，會建立此服務和用戶端資料類別。  
  
## <a name="example"></a>範例  
 下列範例示範如何建立現有的 `Customer` 物件，此物件包含要儲存至資料服務的變更。 系統會將物件附加至內容，並呼叫 <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> 方法，將附加物件標記為 <xref:System.Data.Services.Client.EntityStates.Modified>，然後再呼叫 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> 方法。  
  
 [!code-csharp[Astoria Northwind Client#AttachObject](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#attachobject)]
 [!code-vb[Astoria Northwind Client#AttachObject](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#attachobject)]  
  
## <a name="see-also"></a>請參閱

- [WCF Data Services 用戶端程式庫](wcf-data-services-client-library.md)
